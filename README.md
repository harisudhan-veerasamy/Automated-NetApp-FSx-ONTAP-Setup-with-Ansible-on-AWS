# 🚀 Automated NetApp FSx for ONTAP Setup with Ansible on AWS

A real-world automation project to provision **FSx for NetApp ONTAP** using **Ansible** and **AWS CLI**, developed as part of my DevOps interview preparation with **NetApp**. This project demonstrates best practices in **cloud automation**, **infrastructure as code**, and **enterprise storage provisioning**.

---

## 📌 Project Overview

This project automates:
- Provisioning of **FSx for NetApp ONTAP** file systems
- Creating **Security Groups**, **Storage Virtual Machines (SVMs)**, and **Volumes**
- Mounting FSx volumes to **EC2 Linux instances** using **NFS**
- Real-time validation and troubleshooting using CLI automation

---

## 🛠 Tech Stack

- **AWS** – FSx for ONTAP, EC2, CLI
- **Ansible** – Infrastructure automation
- **Python** – For Ansible execution environment
- **NFS** – Linux-based persistent mounts
- **Bash/Command Line** – Volume testing & SSH automation

---

## 📂 File Structure

fsx-ontap-ansible/
│
├── createfsx.yaml # Ansible playbook for end-to-end automation
├── extract_ids.sh # Script to extract FSx & SVM IDs (if used)
├── mount_instructions.txt # Manual EC2 mount guidance
├── screenshots/ # Optional visuals
└── README.md

yaml
Copy
Edit

---

## 🔧 Prerequisites

- ✅ AWS account with FSx, VPC, and EC2 permissions
- ✅ AWS CLI installed and configured (`aws configure`)
- ✅ Python + pip installed
- ✅ Ansible installed (`sudo apt install ansible`)
- ✅ Ansible AWS Collection:
  ```bash
  ansible-galaxy collection install amazon.aws
📝 How It Works
Step 1: Create FSx File System
Automatically fetches default VPC & subnet

Creates security group with NFS & SMB rules

Provisions FSx with SSD storage and ONTAP configuration

Step 2: Create SVM
Configures storage virtual machine on FSx

Security style: UNIX

Step 3: Create Volume
Creates ONTAP volume (vol1) with NFS export

Enables snapshot policy and storage efficiency

Step 4: Mount Volume to EC2
Manual command (or automate via SSH):

bash
Copy
Edit
sudo mkdir /fsx
sudo mount -t nfs <SVM DNS>:/vol1 /fsx
🚀 Running the Project
bash
Copy
Edit
ansible-playbook createfsx.yaml
Verify in the AWS Console under FSx → File systems.

🖥️ EC2 Mount Example
Launch a Linux EC2 instance in the same VPC

SSH into the instance and run:

bash
Copy
Edit
sudo apt update && sudo apt install -y nfs-common
sudo mkdir /fsx
sudo mount -t nfs <SVM-DNS>:/vol1 /fsx
Test by creating a file in /fsx and confirming it's accessible from other instances.

✅ Outcome
🔁 Fully automated storage provisioning workflow

🔒 Secure setup with IAM roles & SGs

📈 Real-world readiness for hybrid storage environments

🧠 Reinforced practical DevOps skills in automation, cloud storage, and networking

🙏 Special Thanks
Huge thanks to Camille Naulet and the NetApp HR Team for the interview opportunity. This project reflects my passion for cloud automation, hybrid storage, and innovative engineering.

📬 Connect
If you’re working in the Cloud, DevOps, or Storage space — I’d love to connect!
