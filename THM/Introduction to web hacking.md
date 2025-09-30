Introduction web hacking
# 1 Walking an Application — TryHackMe (Browser-based recon)

## Overview
This room teaches how to manually review a web application using built-in **browser developer tools** rather than automated scanners.  
Key tools: **View Source**, **Inspector (Elements)**, **Debugger (Sources/Pretty Print)**, **Network**.

---

## Quick access (common shortcuts)
- Open DevTools: `Ctrl+Shift+I` (Windows) / `Cmd+Option+I` (macOS)  
- Console: `Ctrl+Shift+J` / `Cmd+Option+J`  
- View page source: right-click → **View Page Source**, or `view-source:` URL

---

## Step 1 — Map the site (manual reconnaissance)
1. Browse the site and note pages/features (login, signup, contact, dashboard, etc.).  
2. Create a simple feature table while exploring:

| Feature | URL | Notes |
|---|---:|---|
| Home | `/` | Company summary, public. |
| Latest News | `/news` | List of articles, links like `/news/article?id=1`. |
| News article | `/news/article?id=1` | One article is paywalled. |
| Contact | `/contact` | Contact form (name, email, message, send). |
| Customers (redirects) | `/customers` → `/customers/login` | Customer area + login/signup. |
| Customer signup | `/customers/signup` | username / email / password fields. |
| Password reset | `/customers/reset` | email input for reset. |
| Create ticket | `/customers/ticket/new` | form + file upload. |
| Account settings | `/customers/account` | edit username/email/password. |
| Logout | `/customers/logout` | logs user out. |

> **Why map?** Finding interactive pages (forms, file upload, login) reveals high-value targets for further testing.

---

## Step 2 — View Page Source
- What it shows: the HTML delivered by server (HTML, CSS links, script tags).  
- Useful items to look for:
  - HTML comments (`<!-- ... -->`) — may contain developer notes or hidden links.
  - Anchor tags `<a href="...">` — reveal internal URLs (private areas).
  - Linked resources (JS/CSS/images) — may expose framework/version info.
  - Directory listings referenced by `href` (exposed directories can reveal files like `flag.txt`, backups, or source).

**Examples & takeaways**
- Hidden link: `href="/secr..."` in source → could be private page.
- Directory listing enabled → may expose backups, config files → risk.

---

## Step 3 — Inspector / Elements
- Use Inspector to view the **live DOM** (what the browser actually shows after JS/CSS).  
- You can **edit HTML/CSS client-side** to reveal content (only local in your browser).

**Common pentester actions**
- Right-click the paywall element → Inspect → find the container `div` (e.g., `.premium-customer-blocker`).
- In Styles panel change `display: block;` → `display: none;` to hide the overlay and reveal content underneath.
  - This is purely local — refreshing reloads original page.
- Edit text or attributes to test client-side controls (note: server still enforces true access).

**Note:** Removing UI obstacles can reveal content or hidden fields but does not bypass server checks.

---

## Step 4 — Debugger / Sources
- Purpose: read and step through JavaScript used by the page.
- Typical workflow:
  1. Open **Sources** (Chrome) / **Debugger** (Firefox).
  2. Locate relevant `.js` files (e.g., `flash.min.js`, `site.js`).
  3. If file is minified/obfuscated, use **Pretty Print** ( `{ }` ) to reformat.
  4. Search for interesting calls (e.g., `flash['remove']()` or `document.location`).
  5. Add **breakpoints** on lines of interest to pause execution and inspect variables/state.
  6. Reload page to catch execution at the breakpoint, then inspect DOM/state.

**Use cases**
- Stop JS before a popup removes content so you can read what it was hiding.
- Inspect JS logic that enforces client-side checks (often a hint to server endpoints).

---

## Step 5 — Network Tab (XHR/AJAX inspection)
- Open **Network** and refresh the page to capture all resource requests.
- Useful filters: `XHR`, `JS`, `CSS`, `Img`, `Doc`.
- Actions:
  - Submit forms (e.g., contact form) and watch the new network entry.
  - Click an XHR entry to view Request / Response payloads.
  - Identify endpoints receiving form data (e.g., `/contact-msg`) and note parameters.
  - Replay/modify requests with tools (or copy as `curl`) for further testing.

**Why this matters**
- AJAX endpoints often process form data and may reveal server-side behavior or endpoints to target.
- Responses can include sensitive data, error messages, or flags in CTFs.

---

## Extra notes (framework & file detection)
- Page resources can reveal which framework is used and version (meta tags, script comments, `vendor` filenames).
- Knowing framework + version can point to **public vulnerabilities** (e.g., known CVEs).
- Look for `robots.txt`, `sitemap.xml`, or `.git/` leakage.

---

## Practical pentest checklist (browser only)
- [ ] Map site pages & features (create feature table).  
- [ ] View source: search comments, hidden links, resource paths.  
- [ ] Use Inspector to find and temporarily remove overlays / paywalls.  
- [ ] Use Debugger to pretty-print JS; set breakpoints on suspicious lines.  
- [ ] Use Network tab to capture XHR requests and responses for forms.  
- [ ] Note framework versions and public vulnerabilities.  
- [ ] Note potential directory listings or exposed files.  
- [ ] Document findings: URL, payloads, request/responses, screenshots.

---

## Warnings & ethics
- Changes made in Inspector/Debugger are **local only** — they do not exploit server vulnerabilities by themselves.  
- Always have permission before testing non-lab systems. In real engagements use proper authorization (scope, rules of engagement).
