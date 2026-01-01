# 🌐 DNS & IIS Web Hosting Configuration on Windows Server

This project demonstrates **step-by-step configuration of a Windows Server as a DNS server and IIS web host**, allowing client machines to access a hosted website using a domain name within the same network.

This setup is commonly used in:
- IT Support roles
- System Administration labs
- Active Directory / DNS practice environments

---

## 🖥️ Lab Environment Overview

This project is implemented using three different machines, each assigned a specific role in the Windows Server network infrastructure.

---

## 🖥️ Machine 1: Host Server (Windows Server)

- Role: Core Infrastructure Server

- Responsibilities:

- Static IP configuration

- DNS Server installation & configuration

- Forward Lookup Zone creation (kurrecomputers.local)

- Host (A) record creation

- Central name resolution for all machines

📌 IP Address: 10.0.0.1<br>
📌 Subnet Mask: 255.0.0.0

---

## 🖥️ Machine 2: Company Server (IIS Web Server)

- Role: Application / Web Hosting Server

- Responsibilities:

- Static IP configuration

- IIS (Internet Information Services) installation

- Website hosting using index.html

- Integration with DNS using A record

📌 IP Address: 10.0.0.2<br>
📌 DNS Server: 10.0.0.1

---

## 🖥️ Machine 3: Client Machine (User System)

- Role: End User / Client System

- Responsibilities:

- Connected to the same network

- Uses DNS server for name resolution

- Accesses hosted website using domain name

- Verifies DNS & IIS functionality

📌 DNS Server: 10.0.0.1

---

## 🔗 Network Architecture Summary

[ Host Server ]
(DNS Server)
IP: 10.0.0.1<br>
        
      
[ Company Server ]
(IIS Web Server)
IP: 10.0.0.2<br>
        
        
[ Client Machine ]
(Web Access via Domain Name)

---

## 🖥️ 1️⃣ Configure IP Address on Host Server

- Press **Windows + R**
- Type `ncpa.cpl` → Press **Enter**
- Right-click the **Ethernet adapter** → **Properties**
- Select **Internet Protocol Version 4 (TCP/IPv4)** → **Properties**
- Configure the IP address as follows:

IP Address : 10.0.0.1 <br>
Subnet Mask : 255.0.0.0

- Click **OK**

---

## 🧠 2️⃣ DNS Server Role Installation

- Open **Server Manager**
- Click **Add Roles and Features**
- Select and install:
  - ✅ **DNS Server**
- Complete the installation and close the wizard

---

## 🧾 3️⃣ DNS Configuration (Forward Lookup Zone)

- Open **Server Manager**
- Go to **Tools → DNS**
- Right-click **Forward Lookup Zones** → **New Zone**
- Select:
  - ☑️ **Primary Zone** (First DNS Server)
- Create a zone name, for example:
kurrecomputers.local
- Click **Next** (2 times)
- Click **Finish**

---

## 🧩 4️⃣ Add Host (A Record) in DNS

- Open **DNS Manager**
- Right-click the zone **kurrecomputers.local**
- Click **New Host (A or AAAA)**

Configuration:
Name : serverA
IP Address : 10.0.0.2

- Click **Add Host**
- Click **OK**

---

## 💻 5️⃣  Client Machine (Machine1) Network Configuration

Configure **Machine1** with the following details:

IP Address : 10.0.0.2<br>
Subnet Mask : 255.0.0.0<br>
DNS Server : 10.0.0.1 <br>

> ⚠️ DNS IP must point to the **Host Server**

---

## 🌍 6️⃣ Install and Configure IIS on Machine1

### Enable IIS
- Go to **Control Panel**
- Open **Programs and Features**
- Click **Turn Windows features on or off**
- Enable:
  - ☑️ **Internet Information Services (IIS)**
- Click **OK**

---

### IIS Website Setup

- Search **IIS** from Windows search and open **Internet Information Services (IIS) Manager**
- Expand the machine name
- Click **Sites**
- Right-click **Default Web Site** → **Remove**

---

## Add Custom Website

 Navigate to:
C:\inetpub\wwwroot

- Paste your website file (e.g. `index.html`)

- Go back to **IIS Manager**
- Right-click **Sites** → **Add Website**

Configuration:<br>
&emsp;&emsp;Site Name : kurrecomputers<br>
&emsp;&emsp;Physical Path : C:\inetpub\wwwroot<br>
&emsp;&emsp;Binding Type : http / https<br>
&emsp;&emsp;IP Address : This Machine(e.g. `10.0.0.2`)

- Click **OK**

---

### Set Default Document

- Select your website (e.g. `kurrecomputers`)
- Click **Default Document**
- Click **Add**
- Enter: web site folder name
 index.html
- Click **OK**

---

## 🌐 7️⃣ Access Website from Client PC

- Ensure client PC is connected to the **same network**
- Open any web browser
- Type the website name:
- kurrecomputers
 
✅ Website should open successfully using DNS name resolution.

---

## ✅ Final Result

✔️ DNS server configured  
✔️ Host (A Record) created  
✔️ IIS web server hosted successfully  
✔️ Website accessible from client PC using domain name  

---

## 🛠️ Requirements

- Windows Server
- DNS Server Role
- IIS (Internet Information Services)
- Client and Server on the same network

---

## 👨‍💻 Author

**Kumlesh Kurre**  
Bachelor of Computer Applications (BCA) – Pursuing  
IT Support & Networking Enthusiast  

---

⭐ If you find this project helpful, please give it a star on GitHub.



