# DevOps Laboratory

## Student Information

* **Name:** Abhyam Mathur
* **Course:** Containerization and DevOps Lab
* **University:** UPES
* **Semester:** 5

---

## 📌 Repository Overview

This repository contains hands-on laboratory experiments for the **Containerization and DevOps** course. The experiments focus on understanding virtualization concepts, containerization using Docker, and practical comparison between **Virtual Machines (VMs)** and **Containers**.

Each experiment includes:

* Aim and objectives
* Tools and technologies used
* Step-by-step procedure with commands
* Observations and results
* Conclusion
* Screenshots for verification

---

## 🧪 List of Experiments

### 🔹 Experiment 1: Compare Virtual Machine with Container

**Objective:**  
To compare traditional Virtual Machines with Containers by deploying the same application (Nginx web server) and analyzing performance, resource usage, and deployment complexity.

**Technologies Used:**

* VirtualBox
* Vagrant
* Ubuntu 22.04 (Jammy)
* Docker
* Nginx

**Key Learnings:**

* Difference between hypervisor-based and container-based virtualization
* VM lifecycle using Vagrant
* Container lifecycle using Docker
* Port mapping and networking in containers

📁 Folder:
```text
Experiment-1-Compare-VM-with-Container/
```

📄 File:
```text
Experiment-1-Compare-VM-with-Container.md
```

---

### 🔹 Experiment 2: Docker Installation, Configuration and Running Images

**Objective:**  
To install and configure Docker on the host system and understand basic Docker operations such as pulling images, running containers, managing container lifecycle, and accessing containerized applications using port mapping.

**Technologies Used:**

* Docker Desktop
* Docker Hub
* WSL (Ubuntu)
* Nginx

**Key Learnings:**

* Docker installation and verification
* Pulling images from Docker Hub
* Running containers in detached mode
* Port mapping between host and container
* Container lifecycle management using Docker CLI

📁 Folder:
```text
Experiment-2-Docker-Installation-and-Running-Images/
```

📄 File:
```text
Experiment-2-Docker-Installation-and-Running-Images.md
```

---

## 🛠 Tools & Technologies

| Tool       | Purpose                      |
| ---------- | ---------------------------- |
| VirtualBox | Type-2 Hypervisor            |
| Vagrant    | VM provisioning & management |
| Docker     | Container platform           |
| Ubuntu     | Guest operating system       |
| Nginx      | Web server for deployment    |

---

## 📂 Repository Structure

```text
DevOps-Lab/
│── README.md
│
│── Experiment-1-Compare-VM-with-Container/
│     ├── Experiment-1-Compare-VM-with-Container.md
│     └── screenshots/
│           ├── vagrant-version.png
│           ├── vagrant-up.png
│           ├── nginx-vm.png
│           ├── docker-nginx-8080.png
│           └── docker-nginx-8081.png
│
│── Experiment-2-Docker-Installation-and-Running-Images/
│     ├── Experiment-2-Docker-Installation-and-Running-Images.md
│     └── screenshots/
│           ├── docker-version.png
│           ├── docker-pull-nginx.png
│           ├── docker-run.png
│           ├── docker-ps.png
│           ├── docker-ps-a.png
│           └── nginx-browser.png
```

---

## 🧠 Key Concepts Covered

* Virtualization vs Containerization
* Host OS vs Guest OS
* Docker Images and Containers
* Port Binding and Networking
* Resource Optimization
* DevOps Deployment Practices
* Container Lifecycle Management

---

## ✅ How to Run the Experiments

### Virtual Machine (Vagrant)

```bash
vagrant init ubuntu/jammy64
vagrant up
vagrant ssh
```

### Container (Docker)

```bash
docker pull nginx
docker run -d -p 8080:80 nginx
```

---

## 📊 Conclusion

This lab provides a strong foundation in DevOps fundamentals by demonstrating real-world differences between Virtual Machines and Containers and by introducing Docker-based containerization. Containers offer faster deployment, lower resource usage, and easier management, while Virtual Machines provide stronger isolation. Understanding both is essential for modern DevOps engineers.

---

## 📌 Notes

* All experiments were performed on a Windows host system.
* Screenshots are included for verification and assessment purposes.
* Commands and outputs may vary slightly depending on system configuration.

---

## ✨ Acknowledgement

This laboratory work was performed as part of the **Containerization and DevOps Lab** curriculum at **UPES**.

---

**End of README**
