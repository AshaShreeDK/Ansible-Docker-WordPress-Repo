# 🚀 WordPress Deployment using Docker & Ansible on Amazon Linux 2023

This project demonstrates how to **automate the deployment of a Dockerized WordPress site** on an Amazon EC2 instance using **Ansible and Docker Compose**.  
The setup was implemented and tested on **Amazon Linux 2023**.

---

## 🌐 Tech Stack

- Amazon EC2 (Amazon Linux 2023)
- Docker Engine & Docker Compose
- Ansible (with `localhost` as inventory)
- WordPress + MySQL Containers
- GitHub for version control

---

## 🚀 Project Structure

Ansible-Docker-WordPress-Repo/
├── Ansible+Docker_WordPress.jpg   
├── docker-compose.yml             
├── inventory                      
├── playbook.yml                   
└── README.md                      

---

## ⚙️ Setup Summary

1. ✅ Installed Docker and Ansible on Amazon Linux 2023.
2. ✅ Created `docker-compose.yml` to define WordPress and MySQL containers.
3. ✅ Wrote an Ansible playbook to automate:
   - Docker installation
   - Docker Compose download
   - Compose up for the stack
4. ✅ Hosted a sample WordPress blog via EC2 public IP.

---

## ✅ Output

Once the Ansible playbook completes successfully, you can access WordPress in your browser using the public IP of your EC2 instance.

http://<EC2-PUBLIC-IP>

🟢 If you're using port `80`, there's **no need to add `:80`** in the URL.  
Example:  
http://18.212.188.121


---

## 🧪 Live Demo Screenshot

📸 Screenshot of deployed WordPress:

![WordPress Screenshot](Ansible+Docker_WordPress.jpg)

---

## 📁 GitHub Repository

🔗 [View This Project on GitHub](https://github.com/AshaShreeDK/Ansible-Docker-WordPress-Repo)

---

## 👩‍💻 Author

**Asha**  
🔗 [LinkedIn Profile](https://www.linkedin.com/in/ashashree-d-k-3666012a6)    
📂 [Explore My DevOps Portfolio](https://github.com/AshaShreeDK)


