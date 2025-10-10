# 1. Architecture
## 1.1 Circuit vs Packet Switching
| Aspect |	Circuit Switching (telephone/PSTN) |	Packet Switching (Internet/cellular core) |
|:------:| :--------------------------------: | :----------------------------------------: |
| How it works |	Reserve a **fixed path** (a circuit) for the whole call |	Split data into packets that share links on demand |
| Congestion symptom | **Blocking**: new calls refused when all circuits busy |	**Queueing** then **packet loss** if buffers overflow |
| Delay pattern |	Stable after setup | Variable (depends on queue length) |
| Typical math |	**M/M/n/n** Erlang–B (no waiting) |	**M/M/1, M/M/1/K, M/G/1** (waiting allowed) |

When to use which?
- Real-time with strict guarantees → circuits/admission control.
- Bursty elastic data (web, video streaming with buffers) → packets.

---

## 1.2 Common Network Topologies
- **Telephone**: hierarchical switches; **trunk groups** sized so blocking ≤ target (use Erlang-B).
- **Internet**:
  - **AS-level**: ISPs (Autonomous Systems) connected by BGP.
  - **Router-level**: POPs and backbone links; last-mile access (fiber, cable, DSL, cellular).
- **Cellular**: cells (BTS/eNodeB/gNodeB) → packet core (EPC/5GC); **handoff** between cells; radio channels scarce.
- **Cable (HFC/DOCSIS)**: shared coax upstream, CMTS/CCAP schedules transmissions; IP over everything.
- **Technology convergence**: voice/video/data all ride over **IP** across these access types.

---

## 1.3 Internet Parts & Protocol Stack
- **Application**: HTTP(S), DNS, SMTP, RTP/RTCP, QUIC.
- **Transport**: TCP (reliable, congestion control), UDP (datagrams), QUIC (reliable in user space).
- **Network**: IP (IPv4/IPv6), ICMP; routing: BGP (inter-domain), OSPF/IS-IS (intra-domain).
- **Link**: Ethernet, Wi-Fi, LTE/5G MAC, DOCSIS.
- **Physical**: fiber, copper, radio.
Cross-cutting: NAT, firewall, VPN/tunnels, CDNs, load balancers, middleboxes.

---

## 1.4 Delay Components & Bandwidth–Delay Product (BDP)
For a packet of **L bits** on a link **R bps**, distance **d**, propagation speed **v**, queue ahead **Q**:
  - **Processing**: router examines headers.
  - **Transmission**: `L / R` seconds (push bits onto the link).
  - **Propagation**: `d / v` seconds (travel).
  - **Queueing**: wait behind others (depends on model).

**Total per-hop delay**
```ini
d_total = d_proc + d_queue + (L/R) + (d/v)
```
**BDP(bits in flight)**
```ini
BDP = R * RTT
```
- Need ≈ **BDP bytes** in flight to fully utilize a path.
- Too-big buffers ⇒ **bufferbloat** (huge queueing delay).
- Too-small buffers ⇒ under-utilization on long-RTT paths.

---

## 1.5 Technology Convergence & QoS
- Past: different networks for calls, email/files, TV, cellular voice.
- Now: all of these apps (web, email, **streaming**, video chat, gaming, VoIP) run **over all networks.**
- **Different QoS needs**: e.g., voice/video favor low jitter and loss; file transfer favors throughput.

---

## 1.6 Performance Metrics (E2E view)
End-to-end performance depends on **multiple hops**, and on **links** (rates, lengths), **nodes** (CPU, buffer), **topology**, and **active hosts**.

Core metrics:
  - **Delay** (esp. queueing)
  - **Loss** (drops/blocking)
  - **Throughput** (bits/s over user-visible windows)
  - **Efficiency** (useful data / total resource used; includes overhead, idle time, losses)
  Metrics **interact**: if you allow larger delay, you can often push loss probability closer to zero; strict latency requires tighter control (and sometimes accepting a bit more loss/marking).

---

## 1.7 Delay Math — Tiny Examples
Assume **Packet = 512 B, Link = 10 Mb/s, Hop = 100 km, Propagation ≈ 3×10⁸ m/s**
  - Propagation:
    `d_prop = 100 km / (3e8 m/s) ≈ 0.000333 s = 333 μs`
  - Transmission:
    `d_trans = (512 * 8 bits) / (10^7 b/s) = 409.6 μs`

Observations:
- On slow links, `d_trans` can dominate.
- On long fiber, `d_prop` can dominate (esp. for small packets).

---

## 1.8 Congestion, Throughput (Fluid View), Efficiency
- Congestion happens when instantaneous demand > capacity → queues form; if buffers fill, loss occurs.
- Throughput over a multi-second window is limited by the minimum rate along the path.

**Simple fluid examples from slides**
1. **Single path** (server → client):
  Throughput ≈ `min(Rs, Rc)` where `Rs/Rc` are server/client-side link rates.
2. **Bottleneck sharing** (3 flows share one link of rate `R`):
   If fair share is `R/3`, per-flow throughput ≈ `min(Rs, R/3, Rc)`.

**Efficiency** = (delivered useful data) / (total resources spent)
→ accounts for headers, idle time, collisions/contests, retransmissions, and drops.

---

# 2. Probability Foundations (Really Simple)

## 2.1 Exponential Distribution (time until next event)
**Definition**
```
X ~ Exponential(λ)   (λ > 0)
```
This notation means: 

- “The random variable X follows an exponential distribution with rate λ.”

`λ`(lambda) is the **rate parameter**, measured in events per second.

The higher λ is, the **faster** events happen → the **shorter** the waiting time.

**Probability Desity Function(PDF)**
```
f(x) = λ e^(−λx)   for x > 0
f(x) = 0           for x ≤ 0
```
- The exponential PDF is **always positive** for x > 0 and **decays exponentially** as x grows.
  
- It represents a “waiting-time” curve:
  high probability for short waits, smaller probability for long waits.
  
Think of it like a curve starting high at x = 0 and dropping rapidly.

🔹 “Density” ≠ probability itself.

> For a continuous variable, the probability of a single exact value (e.g., X = 1.0000) is 0.
> 
> We compute probability over intervals by integrating the area under the curve:
> 
> **P(a ≤ X ≤ b) = ∫ₐᵇ λ e^(−λx) dx**

- **Mean**
  `E[X] = ∫₀^∞ xλe^(−λx) dx = 1/λ`

  Interpretation:

  - Mean wait time = 1 / λ
    
  - Larger λ → shorter expected waiting time.
    
  | λ | Average wait `𝐸[𝑋]` | Example meaning |
  |:--:|:----------------:| :-------------:|
  | 0.5 /s |	2 s |	On average, one event every 2 s |
  | 1 /s	 | 1 s |	One event per second |
  | 5 /s |	0.2 s |	Five events per second |

- **Variance** `Var(X) = 1/λ²`
  
  It shows the **spread** (uncertainty) of the waiting time.
  
  So if λ = 5, the variance is (1/25), and the standard deviation (√Var) = 0.2 s — the same as the mean!
  
  ➡️ This is a unique property of exponential distributions.

**Memoryless property**
```
P(X > s + t | X > s) = P(X > t)
```

Reading: “if it hasn’t happened by time s, the remaining wait looks brand new.”

It **forgets the past** — that’s why it’s called “memoryless.”

Simple example

Imagine waiting for a bus:

- The average wait is 10 minutes (λ = 1/10 min⁻¹).

- You’ve already waited 5 min, and no bus yet.

You might think: “Since I already waited 5 minutes, it should arrive soon.”

❌ Not true for exponential waiting. The remaining wait is still exponential(λ),

so your expected extra wait is still 10 minutes.

Formally:

P(X > 5 + 5 | X > 5) = e^(-λ(5)) = e^(-0.1×5) = e^(-0.5)

which equals P(X > 5) — same curve, just shifted.

**Why it appears in queues**
  - Service times or inter-arrival times often approximated as exponential → neat, closed-form delay formulas.

---

## 2.2 Poisson Distribution & Poisson Process (counting events)
**Poisson(k; m)**

Probability of exactly **k** events when the **mean** is **m**:

```mathematica
P(N = k) = (m^k / k!) * e^(−m)
```
**Poisson process N(t) with rate λ (events/second)**
  - `N(0)=0`
  - **Stationary increments**: only window length matters.
  - **Independent increments**: disjoint time windows are independent.
  - `N(t) ~ Poisson(λ t)` (mean arrivals in time t is λt)
  - Inter-arrival times are **Exponential(λ)**.

**Rule of thumb links**
  - “Time until next arrival” ~ Exponential(λ).
  - “# arrivals in t seconds” ~ Poisson(λt).

---

# 3. Queueing Models
## 3.1 Notation & Universal Laws
**Kendall’s notation** `A/S/c/K`
  - `A`: arrival process (M=Poisson, D=deterministic, G=general)
  - `S`: service-time distribution (M, D, G)
  - `c`: number of parallel servers
  - `K`: total system capacity (queue + in service); omit = infinite
  - Discipline default: **FIFO**

**Traffic intensity (utilization)**
```r
ρ = λ / (c μ)      (μ = service rate per server)
```

**Little’s Law (very general)**
```perl
L  = λ W      (average items in system)
Lq = λ Wq     (average items waiting)
```

---

## 3.2 M/M/1
  - Poisson arrivals (rate λ), exponential service (rate μ), 1 server, **infinite buffer**.
  - Stability: `ρ = λ/μ < 1`.

**Key formulas**
```pgsql
L   = ρ / (1 − ρ)                 (avg in system)
W   = 1 / (μ − λ)                 (avg time in system)

Lq  = ρ^2 / (1 − ρ)               (avg in queue)
Wq  = ρ / (μ − λ)                 (avg waiting time)

Distribution of sojourn time is exponential with rate (μ − λ).
```

**Intuition**
As 'ρ → 1', waiting time **blows up** sharply → keep utilization reasonable (often < 0.7–0.8 for low latency).

---

## 3.3 M/M/1/K (finite buffer → drops)
  - Same as M/M/1 but **capacity** `K` (including the job in service).
  - If an arrival finds `K` items already in the system ⇒ **drop**.

**Stationary probabilities** (truncated geometric)
```mathematica
π_n = (1−ρ) ρ^n / (1 − ρ^(K+1)),   n = 0..K
Drop probability = π_K
Throughput (carried load) = λ * (1 − π_K)
```

**Use**: Router output queues (drop-tail).
  - Big K ⇒ low loss but large delay (bufferbloat).
  - Small K ⇒ higher loss but lower latency; AQM/ECN try to balance.

---

## 3.4 M/M/n/n (Erlang loss; no waiting)
  - **n servers, no queue**. Arrivals when all n are busy are **blocked** (lost call).
  - Offered load in **Erlangs**: `a = λ/μ`.

**Blocking (Erlang-B)**
```java
B(n, a) = (a^n / n!) / Σ_{k=0..n} (a^k / k!)
Carried traffic = a * (1 − B)
```

**Use**: Telephone trunk groups; radio channels per cell; often give **handoff calls** priority (advanced variants).

---

## 3.5 M/G/1 (general service, heavy tails)
  - Poisson arrivals; **general** service time S with mean `E[S]=1/μ`, variance `Var(S)`, second moment `E[S²]`.

**Pollaczek–Khinchine (average waiting)**
```ini
Wq = [ λ E[S²] ] / [ 2 (1 − ρ) ],   ρ = λ E[S]
W  = Wq + E[S]

```
**Service-time variability matters**
Let `C_S² = Var(S) / (E[S])²`. Then:
```ini
Wq = (ρ / (1−ρ)) * ((1 + C_S²)/2) * E[S]
```
  - **Heavy-tailed** sizes (large 'C_S²') → much larger queues than M/M/1 even with same mean service!

---

## 3.6 Networks of Queues (tandems)
  - **Burke’s theorem**: in steady state, **departures** from M/M/1 are **Poisson(λ)**.
  - Consequence: a **tandem** of M/M/1 nodes can be analyzed per-node (Jackson networks under mild assumptions).
  - Use to approximate multi-hop paths: access → aggregation → core.

---

## 3.7 Fluid Models & Throughput
  - Treat queues as fluid with rate dynamics:
```perl
dq/dt = λ(t) − μ(t),   q(t) ≥ 0
```
  - Good for control-loop reasoning (TCP + AQM).
  - Rough TCP Reno throughput law: `rate ∝ 1 / (RTT * sqrt(p))` (connects BDP, RTT, and drop prob. `p`).

---

# 4. Mapping Topics ⇄ Models
  - **Packet switching models & metrics** → M/M/1, M/M/1/K, M/G/1; delay/loss/throughput formulas.
  - **Circuit switching models & metrics** → M/M/n/n (Erlang-B); **call blocking**.
  - **Queueing networks** → tandems/Jackson; **Burke** for Poisson departures.
  - **Heavy-tailed packet lengths** → M/G/1 with large `C_S²`→ big delays.
  - **Fluid flow, throughput** → §3.7.
  - **Bandwidth–delay product** → §1.4.
  - **Multiple cells, handoff** → loss systems with priority/guard channels.

---

# 5. Worked Micro-Examples
**(A) Exponential “clock” sense check**
Rate `λ = 5 / s` ⇒ average wait `E[X]=0.2 s`. Probability you wait **more than **`0.5 s`:
```
P(X > 0.5) = e^(−λ*0.5) = e^(−2.5) ≈ 0.0821
```

**(B) Router output buffer (M/M/1/K)**
Link 10 Gbps, 1500-B packets ⇒ `μ ≈ 10^10 / (1500*8) ≈ 833,333 pkts/s`.
If `λ = 700,000 pkts/s` ⇒ `ρ ≈ 0.84`. With `K=200`, loss is tiny but `Wq` rises because `ρ` is high.
→ Lesson: latency explodes as `ρ → 1` even if drops are near zero.

**(C) Trunk group sizing (Erlang-B)**
Offered `a = 120 `Erlangs; choose `n` with `B(n,a) ≤ 1%`. Using the formula (or a small script/table), `n ≈ 137–139` circuits.

**(D) Heavy tails hurt (M/G/1)**
Same mean `E[S]=1 ms`, arrival `λ = 0.8/ms` (ρ=0.8).
  - Exp service (`C_S²=1`):
    `Wq = (ρ/(1−ρ)) * (1+1)/2 * E[S] = 4 * 1 ms = 4 ms`.
  - Heavy-tailed (`C_S²=10`):
    `Wq = 4 * (11/2) * 1 ms = 22 ms`.
    Same mean service, **>5×** wait due to variability.































