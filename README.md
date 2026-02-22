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


# Part 4 — Firewall (NSG) Testing

## **1. Start nonstop ping**

<img width="1968" height="722" alt="Screenshot 2026-02-14 at 12 29 24 AM" src="https://github.com/user-attachments/assets/fadc32ca-6e37-4399-aefa-ffdb69585eb3" />


## **2. Block ICMP in VM2’s NSG**
Add inbound rule:
- Deny  
- ICMP  
- Priority 280  

<img width="1330" height="1217" alt="Image 2-22-26 at 9 22 AM" src="https://github.com/user-attachments/assets/0318f879-a87c-4dd2-a126-b9986289dbbb" />

<img width="1563" height="875" alt="Image 2-22-26 at 9 29 AM" src="https://github.com/user-attachments/assets/852b2ee1-5479-4c14-8e91-7993ffd0a64e" />

# **3. Re-enable ICMP**
Delete or disable the deny rule.

<img width="1451" height="1084" alt="Image 2-22-26 at 9 33 AM" src="https://github.com/user-attachments/assets/dfeec656-8789-4219-91ae-1fbd0c880906" />

<img width="1577" height="761" alt="Image 2-22-26 at 9 37 AM" src="https://github.com/user-attachments/assets/4c55f585-bc5e-4e37-bb2c-a3b7ac1a1ea2" />

 # ** Filter for SSH**

<img width="1391" height="1052" alt="Image 2-22-26 at 12 07 PM" src="https://github.com/user-attachments/assets/52e7ca39-36ee-4abc-b97a-b4bab98727ce" />

<img width="1664" height="898" alt="Image 2-22-26 at 1 23 PM" src="https://github.com/user-attachments/assets/7c7a901f-b880-491b-94db-caa6006b6e63" />

 # ** Filter for DNS**
Use nslookup
<img width="1650" height="814" alt="Image 2-22-26 at 1 39 PM" src="https://github.com/user-attachments/assets/1d3c50f4-c5de-4439-a17e-7fc2476388a2" />

 # ** DHCP Traffic**
 Filter for DHCP
 
 Renew IP

 <img width="1643" height="706" alt="Image 2-22-26 at 1 49 PM" src="https://github.com/user-attachments/assets/6543b3c3-d275-4b7f-aa21-1e986d0dff5d" />

# ** DHCP Traffic**
RDP Traffic

tcp.port == 3389

<img width="1682" height="912" alt="Image 2-22-26 at 1 55 PM" src="https://github.com/user-attachments/assets/1580311b-4068-41c5-a5f0-7fda6eaebcc5" />

# What I Learned
VM deployment

VNet/Subnet configuration

NSG firewall rules

Wireshark protocol analysis

Troubleshooting Windows Firewall

Understanding ICMP, DNS, DHCP, SSH, RDP

