# Azure Virtual Network Lab – Windows 11 + Ubuntu

## Goal of the lab

Create two virtual machines in Microsoft Azure:
- One **Windows 11** VM
- One **Ubuntu (Linux)** VM  
Both must be in the **same virtual network and subnet** so they can communicate like computers on the same LAN.

---

## Part 1 – Create the virtual machines in Azure

### 1. Sign in to the Azure portal

1. On your Mac, open a web browser (Safari or Chrome).
2. Go to: https://portal.azure.com
3. Sign in with your Azure account.

---

### 2. Create a Resource Group

A Resource Group is like a folder that holds all the stuff for this lab.

1. In the left menu, click **Resource groups**.
2. Click **+ Create**.
3. Set:
   - **Subscription:** your active subscription.
   - **Resource group name:** `RG-Network-Lab` (or any name you like).
   - **Region:** choose a region (for example, **East US**).
4. Click **Review + create**, then **Create**.

---

### 3. Create the Windows 11 Virtual Machine (VM)

> The checklist says “Windows 10,” but we’ll use **Windows 11**. The steps are the same idea.

#### 3.1 Start creating the VM

1. In the left menu, click **Virtual machines**.
2. Click **+ Create → Azure virtual machine**.

#### 3.2 Basics tab

1. **Subscription:** your active subscription.
2. **Resource group:** select `RG-Network-Lab`.
3. **Virtual machine name:** `Win11-VM`.
4. **Region:** same region as the Resource Group.
5. **Image:** open the dropdown and choose a **Windows 11** image (for example, *Windows 11 Pro* or *Windows 11 Enterprise*).
6. **Size:** pick a small size that is allowed (for example, `Standard_B2s`).
7. **Administrator account:**
   - **Username:** something like `winadmin`.
   - **Password:** create a strong password and remember it.
8. **Inbound port rules:**
   - **Public inbound ports:** choose **Allow selected ports**.
   - **Select inbound ports:** check **RDP (3389)** so you can connect later.

#### 3.3 Networking tab – let it create a new VNet and subnet

1. Click the **Networking** tab.
2. **Virtual network:** leave it on **Create new**.
   - Name it something like `VNET-Lab`.
3. **Subnet:** keep the default subnet name or rename it (for example, `Subnet-Lab`).
4. Leave the other settings as default for this lab.

#### 3.4 Create the VM

1. Click **Review + create**.
2. After validation passes, click **Create**.
3. Wait for the deployment to finish (this can take a few minutes).

---

### 4. Create the Linux (Ubuntu) VM

Now you’ll create an Ubuntu VM in the **same Resource Group and same Virtual Network**.

#### 4.1 Start creating the VM

1. Go back to **Virtual machines**.
2. Click **+ Create → Azure virtual machine**.

#### 4.2 Basics tab

1. **Subscription:** same as before.
2. **Resource group:** select `RG-Network-Lab` (the same one).
3. **Virtual machine name:** `Ubuntu-VM`.
4. **Region:** same region as the Windows VM.
5. **Image:** choose **Ubuntu Server** (for example, *Ubuntu Server 22.04 LTS*).
6. **Size:** pick a similar small size (for example, `Standard_B2s`).

#### 4.3 Authentication type

1. **Authentication type:** select **Password**.
2. **Username:** for example, `ubuntuuser`.
3. **Password:** create and confirm a strong password.
4. **Inbound port rules:**
   - **Public inbound ports:** choose **Allow selected ports**.
   - **Select inbound ports:** check **SSH (22)** so you can connect later if needed.

#### 4.4 Networking tab – use the same VNet and subnet

1. Click the **Networking** tab.
2. **Virtual network:** from the dropdown, select **VNET-Lab** (the same VNet created with the Windows VM).
3. **Subnet:** select the same subnet (for example, `Subnet-Lab`).
4. Leave the rest as default.

#### 4.5 Create the VM

1. Click **Review + create**.
2. After validation, click **Create**.
3. Wait for the deployment to complete.

---

### 5. Verify both VMs are in the same Virtual Network / Subnet

#### 5.1 Check the Windows 11 VM

1. In **Virtual machines**, click `Win11-VM`.
2. In the left menu, under **Settings**, click **Networking**.
3. Note the **Virtual network** and **Subnet** names (for example, `VNET-Lab` and `Subnet-Lab`).

#### 5.2 Check the Ubuntu VM

1. In **Virtual machines**, click `Ubuntu-VM`.
2. Click **Networking**.
3. Confirm that:
   - **Virtual network** is the same (for example, `VNET-Lab`).
   - **Subnet** is the same (for example, `Subnet-Lab`).

