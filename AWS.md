# 🧩 项目一：在 AWS 创建 EC2 实例并配置 Security Group

## 🎯 项目目标
- 在 AWS 上启动一台 Amazon Linux 2 实例  
- 配置安全组，允许 SSH (22) 访问  
- 使用本地终端连接实例  
- 记录命令与截图  

---

## 🧱 步骤一：登录 AWS 控制台
1. 打开 [AWS EC2 控制台](https://console.aws.amazon.com/ec2)
2. 确认右上角的 Region（区域）为 **us-west-2 (Oregon)**。


---

## 🚀 步骤二：创建 EC2 实例
1. 选择左侧菜单 **Instances → Launch instances**
2. 配置：
   - **Name:** `web1`
   - **AMI:** Amazon Linux 2 (Free tier eligible)
   - **Instance Type:** `t2.micro`
   - **Key Pair:** 创建新的密钥对（下载 `aws-key.pem`）
   - **Network settings:**
     - 编辑安全组，勾选  
       ✅ Allow SSH traffic from anywhere (0.0.0.0/0)

3. 点击 **Launch instance**

---

## 🧩 步骤三：验证实例状态
1. 打开左侧菜单 **Instances → Instances**
2. 检查：
   - Instance state: **running**
   - Public IPv4 address: **显示的公网 IP**
   - Private IPv4: 172.x.x.x（内部地址）


---

## 🧠 步骤四：配置 SSH 登录
1. 在终端中进入密钥所在目录  
2. 修改密钥权限：
   ```
   chmod 400 aws-key.pem
   ```
3. 使用 SSH 登录：
   ```
   ssh -i aws-key.pem ec2-user@<Public-IP>
   ```
4. 登录成功后终端会显示：
   ```
   [ec2-user@ip-172-31-xx-xx ~]$
   ```

---

## 🌐 步骤五：查看网络配置
登录后查看 IP 信息：
```
ip addr
```
输出中可见：
- eth0 的 私有 IP 地址 (172.x.x.x)
- 公网 IP（由 AWS 分配）

---

## 🔐 步骤六：验证 Security Group
在 AWS 控制台 → Security Groups 中确认：
- Inbound rules 包含：
  - Type: SSH
  - Port: 22
  - Source: 0.0.0.0/0
 
---

# 🧩 Project 2: Deploy Nginx + Static Website + Enable CloudTrail on AWS

## 🎯 Objective
- Deploy an Nginx web server on your AWS EC2 instance  
- Replace the default Nginx page with your own static website  
- Enable AWS CloudTrail to log all account actions  
- Record commands and screenshots for each stage  

---

## 🧱 Step 1: Verify EC2 Instance Status
1. Log in to your [AWS EC2 Console](https://console.aws.amazon.com/ec2)
2. Check:
   - **Instance state:** Running  
   - **Public IPv4 address:** Assigned  
3. If stopped → click **Instance state → Start instance**


---

## 🔑 Step 2: Connect to the Instance
Open your terminal and run:
```
chmod 400 my-ec2-key.pem
ssh -i my-ec2-key.pem ec2-user@<Public-IP>
```
When prompted:
Are you sure you want to continue connecting (yes/no/[fingerprint])?
Type `yes`.

---

## 🌐 Step 3: Install and Start Nginx
Once connected to your instance, run the following commands:
```
sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```
Expected output:
```
Active: active (running)
```
---

## 🧾 Step 4: Test the Default Nginx Page
Open a browser and go to:
```
http://<Your-Public-IP>
```
✅ You should see the “Welcome to Nginx” page.

---

## 🧱 Step 5: Deploy a Static Website
1. Navigate to the Nginx web root:
```
cd /usr/share/nginx/html
```
2. Replace the default page:
```
sudo nano index.html
```
3. Add your own HTML:
```
<html>
<head><title>My AWS Static Site</title></head>
<body><h1>Hello from AWS EC2 + Nginx!</h1></body>
</html>
```
4. Save and exit (Ctrl + O, Enter, Ctrl + X)
5. Refresh your browser to see the custom page.

---

## ☁️ Step 6: Enable AWS CloudTrail
1. Go to the AWS Console → search for CloudTrail
2. Click Create trail
3. Set the options:
  - Apply trail to all regions
  - Log read and write events
  - Create a new S3 bucket for logs
4. Click Create trail

---

## 🧠 Step 7: Verify CloudTrail Logging
You can check CloudTrail logs:
- Go to the **Event history** tab
- You’ll see entries for actions like:
  - StartInstances
  - RunInstances
  - DescribeSecurityGroups
