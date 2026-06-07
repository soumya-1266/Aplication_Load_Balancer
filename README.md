# Multi-App Hosting with AWS Application Load Balancer (ALB)

# Project Overview
This project demonstrates hosting two web applications on separate EC2 instances and routing requests using AWS Application Load Balancer (ALB) path-based routing.

# Architecture
- `/google` → EC2 Instance 1 (Google Clone)
- `/drive` → EC2 Instance 2 (Drive Clone)

# AWS Services Used
- Two Amazon EC2
- Application Load Balancer (ALB)
- Target Groups
- Security Groups
- Apache HTTP Server

## Execution Steps

# Step 1: Launch Two EC2 Instances
Create:
- google-server (1st EC2)
- drive-server  (2nd EC2)

# Step 2: Install Apache in both EC2 Instance
```bash
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

# Step 3: Deploy Applications

# Google Server
```bash
cd /var/www/html
git clone https://github.com/JacobGrisham/Google-Homepage-HTML-and-CSS
mv Google-Homepage-HTML-and-CSS/* .
```

# Drive Server
```bash
cd /var/www/html
git clone https://github.com/akshay-mudda/Google-Drive-Clone
mv Google-Drive-Clone drive
```

# Step 4: Create Target Groups
- tg-google
- tg-drive

Health Check Path:
```
/
```

# Step 5: Create Application Load Balancer
- Internet Facing
- HTTP Port 80
- Select two Availability Zones

# Step 6: Configure Path-Based Routing

| Path | Target Group |
|------|-------------|
| /google* | tg-google |
| /drive* | tg-drive |

# Step 7: Test
```
http://ALB-DNS/google/
http://ALB-DNS/drive/
```

# Outcome
Successfully hosted two applications on separate EC2 instances and routed traffic using AWS ALB path-based routing.
