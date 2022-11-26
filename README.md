# AWS Lightsail Docker Node-RED

## Getting Started
1. Log in to the AWS Console
2. Navigate to Lightsail

## Create a new Lightsail instance
1. On Lightsail, click the "Create instance" button
2. Choose: "Ohio" (us-east-2) for the instance location
3. Select "Linux/Unix" platform
4. Select "OS Only" blueprint
5. Choose: "Amazon Linux 2"
6. Choose: "Change SSH key pair" 
    - Click: "Create New"
    - Click: "Create" button
    - On "Create a new SSH key pair" type: ```Lightsail_SSH-key```
    - Click the "Generate key pair" button
    - Important: Click: "Download private key"
    - Click: "Okay, got it!" button
7. Check the box: "Enable Automatic Snapshots"
8. Choose instance plan: "$5/month - 1GB RAM, 1CPU"
9. Identify your instance: ```lightsail-docker01```
10. Click: "Create instance" button

## Configure Lightsail "Networking"
1. Click the "Networking" tab in Lightsail
2. Click the "Create static IP" button
3. Attach to instance: ```lightsail-docker01```
4. Indentify static IP: ```lightsail-docker01_Static-IP```
5. Click the "Create" button and record the Static IP assigned

## Configure "IPv4 Firewall" for this Lightsail instance
1. Navigate to the main Lightsail page (Ohio)
2. Click on the Lightsail instance: ```lightsail-docker01```
3. Click on the "Networking" tab
4. Under "IPv4 Firewall" click: "Add rule"
    - Application: "HTTPS" (TCP 443)
    - Click: "Create"
5. Under "IPv4 Firewall" click: "Add rule"
    - Custom TCP port: 1880
    - Click: "Create"

## Install Docker
1. Connect to the Lightsail instance using the static IP and SSH key: ```ssh -i /path/to/private-key.pem ec2-user@public-ip```
2. Apply updates: ```sudo yum upgrade -y```
3. Install Docker (on AL2): ```sudo yum install -y docker```
4. Add the "ec2-user" to "docker" group: ```sudo usermod -a -G docker ec2-user```
5. Update the groups: ```newgrp docker```
6. Install docker-compose: ```sudo pip3 install docker-compose```
7. Enable docker start on boot: ```sudo systemctl enable docker.service```
8. Start docker: ```x```
9. Reboot: ```sudo reboot```

## Install Node-RED
1. 

## Secure Node-RED
1. 

## Configure Node-RED for git version control
1. 

