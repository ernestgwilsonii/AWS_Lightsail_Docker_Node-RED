# AWS Lightsail Docker Node-RED

## Getting Started
1. Log in to the AWS Console
2. Navigate to Lightsail

## Create a new Lightsail instance
1. On Lightsail, click the "Create instance" button
2. Choose: "Ohio" (us-east-2) for the instance location
3. Select "Linux/Unix" platform
4. Select "OS Only" blueprint
5. Choose: "Debian 11.4"
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
    - Custom TCP port: 81
    - Click: "Create"
5. Under "IPv4 Firewall" click: "Add rule"
    - Application: "HTTPS" (TCP 443)
    - Click: "Create"
6. Under "IPv4 Firewall" click: "Add rule"
    - Custom TCP port: 1880
    - Click: "Create"
7. Under "IPv4 Firewall" click: "Add rule"
    - Custom TCP port: 1883
    - Click: "Create"
8. Under "IPv4 Firewall" click: "Add rule"
    - Custom TCP port: 8883
    - Click: "Create"
9. Under "IPv4 Firewall" click: "Add rule"
    - Custom TCP port: 9001
    - Click: "Create"
10. Under "IPv4 Firewall" click: "Add rule"
    - Custom TCP port: 9883
    - Click: "Create"

# Add a DNS "A Record"
1. Log in to AWS Route 53
2. Select desired hosted domain zone
3. Create DNS "A Record" ```node-red.domain.name n.n.n.n```

## Install Docker
1. Connect to the Lightsail instance using the static IP and SSH key: ```ssh -i /path/to/private-key.pem admin@public-ip```
2. Apply updates: ```sudo apt-get update && sudo apt-get upgrade -y```
3. Install standard kit: ```sudo apt-get install -y git htop jq lsof mc mosquitto-clients nano ntp python3 python3-pip tcpdump vim```
3. Install Docker: ```curl -fsSL https://get.docker.com | sudo sh```
4. Add the "admin" to "docker" group: ```sudo usermod -a -G docker admin```
5. Update the groups: ```newgrp docker```
6. Install docker-compose: ```sudo pip install docker-compose```
7. Docker Swarm initialize: ```sudo docker swarm init```
9. Reboot: ```sudo reboot```

## Launch Node-RED container
```
n
```

## Secure Node-RED
1. 

## Configure Node-RED for git version control
1. 

