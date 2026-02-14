# 🖥️ Azure Windows-to-Windows Networking Lab  
A beginner-friendly cloud networking project built on Microsoft Azure.

This lab demonstrates how to deploy two Windows 11 virtual machines, place them on the same virtual network, and observe network traffic using Wireshark.  
Completed on a **Mac Mini** using Microsoft Remote Desktop.

---

# 🚀 Goals
- Deploy two Windows 11 VMs  
- Connect from macOS  
- Use Wireshark to capture traffic  
- Test ICMP, DNS, DHCP, SSH, and RDP  
- Modify NSG firewall rules  
- Troubleshoot Windows Firewall blocking ping  

---

# 🧱 Part 1 — Build the Azure Environment

## **1. Create a Resource Group**
- Name: `Lab-RG`

 
<img width="1319" height="367" alt="Image 2-4-26 at 9 12 PM readme" src="https://github.com/user-attachments/assets/09039ab5-8ea7-4103-b3fc-7962139593cd" />


---

## **2. Create Windows 11 VM #1**
- Name: `Win11-VM1`
- Image: Windows 11 Pro
- Networking: Create new VNet + Subnet

---

## **3. Create Windows 11 VM #2**
- Name: `Win11-VM2`
- Networking: Use the **same VNet + Subnet** as VM1

<img width="1317" height="711" alt="Image 2-4-26 at 9 13 PM" src="https://github.com/user-attachments/assets/f76ecd3f-e9ef-49c0-b191-f0b05d200e67" />


---

## **4. Confirm Network Settings**
Both VMs should show the same:
- Virtual Network  
- Subnet  


---

# 🖥️ Part 2 — Connect to VM1 (from macOS)

## **1. Install Microsoft Remote Desktop**
From the Mac App Store.

![Image 2-1-26 at 10 04 AM](https://github.com/user-attachments/assets/44ac90c7-35df-4e5e-a2ed-8ed98fa545e7)


---

## **2. Connect to VM1**
Use VM1’s **Public IP**.


---

# 🔍 Part 3 — Wireshark Traffic Capture

## **1. Install Wireshark inside VM1**
Download from https://www.wireshark.org/

![Image 2-1-26 at 10 15 AM](https://github.com/user-attachments/assets/ed0b5e93-28b9-433c-8c50-a2ac62fe927c)


---

## **2. Start a capture**
Double‑click the Ethernet adapter.


---

## **3. Filter for ICMP**

![Image 2-1-26 at 10 26 AM](https://github.com/user-attachments/assets/7b865b4f-2bcb-4977-9240-0bdee24ca649)


---

## **4. Ping VM2**


<img width="1793" height="787" alt="Screenshot 2026-02-14 at 12 21 50 AM" src="https://github.com/user-attachments/assets/4758610a-b903-43de-a734-fe4f1c74a617" />


---

## **5. Ping Google**

<img width="1983" height="737" alt="Screenshot 2026-02-14 at 12 24 40 AM" src="https://github.com/user-attachments/assets/8a62892a-867c-42d5-b57b-eb9d1b6dbd0a" />


# 🔥 Part 4 — Firewall (NSG) Testing

## **1. Start nonstop ping**

<img width="1968" height="722" alt="Screenshot 2026-02-14 at 12 29 24 AM" src="https://github.com/user-attachments/assets/fadc32ca-6e37-4399-aefa-ffdb69585eb3" />

