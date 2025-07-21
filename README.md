# 🐳 WordPress Deployment using Docker & Ansible on Amazon Linux 2023

This project demonstrates how to **automate the deployment of a Dockerized WordPress site** on an Amazon EC2 instance using **Ansible and Docker Compose**. The setup was implemented and tested on **Amazon Linux 2023**.

---

## 📦 Tech Stack

- Amazon EC2 (Amazon Linux 2023)
- Docker Engine & Docker Compose
- Ansible (using `localhost` as inventory)
- WordPress + MySQL Containers
- GitHub for version control

---

## 🚀 Project Structure

📁 ansible-wordpress-setup/
├── 🖼️  Ansible+Docker_WordPress.jpg   - Screenshot of the deployed WordPress site
├── 📄 docker-compose.yml              - Defines multi-container setup for WordPress & MySQL
├── 📄 inventory                       - Ansible inventory file (localhost-based)
├── 📄 playbook.yml                    - Ansible playbook to automate Dockerized WordPress deployment
└── 📘 README.md                       - Complete project documentation

---

## ⚙️ EC2 Instance Setup (Amazon Linux 2023)

```bash
# Connect to EC2
ssh -i "asha.pem" ec2-user@<your-ec2-public-ip>

# Update & install Docker
sudo yum update -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
sudo usermod -aG docker ec2-user
newgrp docker

# Install Python & pip
sudo yum install python3 -y
curl -O https://bootstrap.pypa.io/get-pip.py
python3 get-pip.py --user
export PATH=$PATH:/home/ec2-user/.local/bin
📥 Install Ansible
# Ensure pip is available
python3 -m pip install --user ansible
🛠 Ansible Inventory File (localhost)
[local]
localhost ansible_connection=local
📜 Ansible Playbook
- name: WordPress Docker Deployment
  hosts: local
  become: true
  tasks:
    - name: Install Docker Compose
      get_url:
        url: https://github.com/docker/compose/releases/latest/download/docker-compose-Linux-x86_64
        dest: /usr/local/bin/docker-compose
        mode: '0755'

    - name: Copy Docker Compose file
      copy:
        src: docker-compose.yml
        dest: /home/ec2-user/docker-compose.yml
        mode: '0644'

    - name: Run Docker Compose
      shell: docker-compose -f /home/ec2-user/docker-compose.yml up -d
🧱 Docker Compose File
version: '3.8'
services:
  wordpress:
    image: wordpress:latest
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
      WORDPRESS_DB_NAME: wordpress
    depends_on:
      - db

  db:
    image: mysql:5.7
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
      MYSQL_ROOT_PASSWORD: rootpassword
▶️ Run the Ansible Playbook
ansible-playbook -i inventory playbook.yml
🔍 Verify the Deployment
Open in browser:

http://<your-ec2-public-ip>:8080
✅ You should see the WordPress installation screen.

### 📸 Screenshot

Here’s a glimpse of the running WordPress site deployed using **Ansible + Docker** on an EC2 instance:

![Docker + Ansible WordPress Screenshot](Ansible%2BDocker_WordPress.jpg)
📂 Git Commands Used
git init
git remote add origin https://github.com/AshaShreeDK/Ansible-Docker-WordPress-Repo.git
git branch -M master
git add .
git commit -m "Initial commit: Automated WordPress deployment using Ansible and Docker"
git push -u origin master
👩‍💻 Author
AshaShree D K
🔗 LinkedIn
📁 GitHub Portfolio
