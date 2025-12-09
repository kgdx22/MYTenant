# MYTenant — Azure Identity & Cybersecurity Architecture Lab

This repository documents the full build-out of my Azure tenant focusing **Identity & Access Management (IAM)** and **Cybersecurity Architecture**.  
It includes Entra ID configuration, Conditional Access, PIM, Defender XDR, Sentinel integration, Intune onboarding, and Zero Trust controls.  
All screenshots and workflows are organized into collapsible sections for clarity.


# 🔐 Identity & Access Management (IAM)

## Overview
This section captures my work configuring foundational and advanced IAM capabilities:

- Tenant initialization and admin roles  
- User lifecycle provisioning  
- Conditional Access policies  
- MFA/SSPR enforcement  
- Custom security controls  
- Identity Protection  
- Access reviews  
- Enterprise application integration  
- Cross-tenant collaboration settings  
- Zero Trust identity alignment  

---

## **IAM Configuration — Screenshots & Steps**

<details>
  <summary><strong>IAM Setup (Screens 1–5)</strong></summary><br>

### **1. Tenant Initialization**
![IAM6](https://github.com/user-attachments/assets/3efec3ae-0a6c-4caa-a9c8-966d2224cf9c)


**Steps:**
- Created Azure AD tenant  
- Configured initial global admin  
- Applied security defaults → later upgraded to custom CA policies  

---

### **2. User Creation & Groups**
![IAM9](https://github.com/user-attachments/assets/7e4ec5f1-413e-4713-896f-fe057d1423ba)
![IAM8](https://github.com/user-attachments/assets/f8e2e639-5070-462d-9ab1-3a7bb2ae4a13)

**Steps:**
- Added cloud-only and hybrid-simulated users  
- Created role-based access groups  
- Prepared security groups for PIM and Conditional Access targeting  

---

### **3. Conditional Access Baseline**
![IAM3](https://github.com/user-attachments/assets/15ceee70-6af1-4048-b57f-bf435dd0afe8)
![IAM5](https://github.com/user-attachments/assets/4228c80c-99c4-4b3e-a25b-7603bbf37b12)

**Configured policies:**
- Require MFA for all users  
- Block legacy authentication  
- Require compliant or hybrid-joined device  
- High-risk sign-ins → require password reset  

---

### **4. MFA + SSPR Integration**
![IAM10](https://github.com/user-attachments/assets/8249ad04-5d99-4686-9077-89ff7594f01b)
![IAM7](https://github.com/user-attachments/assets/e69e9f9c-7d93-4dc1-9ffc-79d96e20d590)


**Steps:**
- Enabled combined registration  
- Enforced authentication methods policy  
- Required MFA + SSPR for administrators  

---

### **5. Identity Protection**
![IAM4](https://github.com/user-attachments/assets/fb1e3126-9b59-4893-8bc2-7f0f9dde113c)

**Configured:**
- User Risk Policy  
- Sign-in Risk Policy  
- Risk detection review  

</details>

---

<details>
  <summary><strong>Join Azure VM to Azure AD (Screens 6–10)</strong></summary><br>

### **6. Creating an Azure VM**
![IAM13](https://github.com/user-attachments/assets/1da097fd-2c74-4cb9-99b1-6f21a57a3224)

**Steps:**
- Selected Windows 11 image and configured size, region, and admin settings
- Chose VNet + subnet and enabled RDP access through NSG
- Enabled Entra ID login 

---

### **7. RBAC for VM Access**
![IAM14](https://github.com/user-attachments/assets/ebeec6ab-599f-4719-9d17-b235768a7f34)

**Configured:** 
- Selected the newly created Virtual Machine 
- Selected Access control (IAM).
- Select + Add, then Add role assignment to open the Add role assignment page
- Assigned VM Admin Login role to appropriate user 

---

### **8. Connecting to Azure VM**
![IAM15](https://github.com/user-attachments/assets/a79b33f2-468e-4b7c-8d0d-5cc26730cc98)

**Connected:**
- Downloaded the VM’s auto-generated RDP file from Azure
- Entered the assigned local admin credentials to establish the session

---

### **9. Allowing RDP**
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/bd37476d-9728-45bf-ac0d-6e40e3168149" />


**Allowed:**
- Type Control Panel and launch the control panel app.
- Select System and Security from the list of settings.
- From the System setting, select the Allow remote access option.
- At the bottom of the dialog box that opens you will see a Remote Desktop section.
- Uncheck the box labeled Allow connections only from computers running Remote Desktop with Network Level Authentication.

Select Apply and then OK.

---

### **10. Entra Join Device**
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/447c43ce-be9d-44eb-a363-a47a90b9ed97" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/83f9b4c3-5e00-4542-944c-49573a7491ac" />


Configured:
- Opened Settings → Accounts → Access work or school and selected Connect → Join this device to Microsoft Entra ID
- Signed in with the Entra user to complete the Azure AD Join
- Ran PowerShell as admin and added the user to Remote Desktop Users: net localgroup "Remote Desktop Users" /add "AzureAD\MonicaT"

 

---

### **Confirm User Login**
<img width="1918" height="1198" alt="image" src="https://github.com/user-attachments/assets/54ac746f-1371-4d06-982b-0ce566130bbc" />
<img width="1918" height="1209" alt="image" src="https://github.com/user-attachments/assets/c2488d76-bfbb-419e-8650-7e2ef5b26be6" />



</details>

---

# 🛡 Cybersecurity Architecture 

## Overview
This section documents my security architecture design work:

- Zero Trust architecture  
- Workspace and environment segmentation  
- Defender for Cloud deployment  
- MDE onboarding  
- Sentinel integration  
- Threat modeling & governance alignment  
- Secure network design  
- CSPM + CWPP controls  

---

## **Cybersecurity Architecture — Screenshots & Steps**

<details>
  <summary><strong> MDE Onboarding (Screens 1–5)</strong></summary><br>

### **1. Zero Trust Overview**
![SC1](https://github.com/user-attachments/assets/045347a5-f449-4977-ab5d-090c029331cf)

Built full Zero Trust alignment:
- Identity  
- Devices  
- Apps  
- Infrastructure  
- Data  
- Networks  

---

### **2. Enterprise Application Settings**
<img width="1918" height="999" alt="image" src="https://github.com/user-attachments/assets/71dca6b0-2ede-4b8c-9e4c-043b5bcdb7b8" />
<img width="1903" height="990" alt="image" src="https://github.com/user-attachments/assets/5702501d-d9a7-4b9c-b8ec-07c32f53c274" />
<img width="1917" height="999" alt="image" src="https://github.com/user-attachments/assets/2e6cd180-8470-4cb3-996f-c0fabc65158d" />


**Configured:**

- Restrictions on guest invitations
- B2B cross-tenant collaboration policies
- Registered enterprise apps and assigned required API permissions (Graph, Directory, User.Read, etc.)
- Granted admin consent to authorize delegated/app permissions for tenant-wide use
- Configured authentication settings (redirect URI, supported account types, implicit/OAuth settings) to enable secure sign-in via Microsoft Entra ID

---

### **3. Sentinel - Log Analytics Workspace Integration**
<img width="1918" height="991" alt="image" src="https://github.com/user-attachments/assets/33867555-62de-44f0-91ef-d37834b97e6b" />
<img width="1918" height="934" alt="image" src="https://github.com/user-attachments/assets/850111e0-3552-4ae9-baa9-b434d80dc738" />
<img width="1918" height="997" alt="image" src="https://github.com/user-attachments/assets/8beb34d2-de96-4ce3-a296-920781157f45" />

**Enabled:**
- Created a new Azure Storage account + Log Analytics Workspace (LAW) to act as the main log lake/telemetry store 
- Enabled Sentinel on the LAW — converting it into a Sentinel workspace to ingest security logs and events 
- Configured data connectors (e.g. Azure Activity logs, Azure AD sign-ins, resource logs) to feed cloud data into Sentinel for monitoring and detection
---

### **4. Defender for Endpoint Onboarding**
<img width="1918" height="994" alt="image" src="https://github.com/user-attachments/assets/72bd2f9b-ac96-4854-89c6-06ed72637d59" />
<img width="1918" height="994" alt="image" src="https://github.com/user-attachments/assets/bdcc91ca-7c73-46fc-a4af-ca8f6dbaee67" />
<img width="1918" height="991" alt="image" src="https://github.com/user-attachments/assets/cf7e5cec-ddf8-4f42-879e-02b3535a2a04" />
<img width="1885" height="1189" alt="image" src="https://github.com/user-attachments/assets/4b97cc12-6985-4f07-959f-c11dfea312d2" />


**Steps taken:**
- Enabled MDE integration  
- Configured Intune connector  
- Onboarded VM via policy  
- Verified advanced hunting signals  

---

### **5. EDR Policy**
<img width="1918" height="996" alt="image" src="https://github.com/user-attachments/assets/e1dc3f3f-df94-403a-b9ff-9a4c9939888c" />
<img width="1918" height="999" alt="image" src="https://github.com/user-attachments/assets/42db3740-eaed-418c-bad5-4c84aed17bd9" />
<img width="1918" height="991" alt="image" src="https://github.com/user-attachments/assets/d500a841-3f9b-4f56-96e5-f9aa531e3407" />

**Steps Taken:**
- Enabled the Defender for Endpoint → Intune connector to allow device risk reporting & automatic onboarding
- Created an MDE “Endpoint Detection & Response” (EDR) policy in Intune and assigned it to my lab device group
- Downloaded / applied the onboarding package (auto-inserted via connector) so the VM registers with MDE
- Synced the device in Intune, verified compliance, and confirmed the VM shows Onboarded in Microsoft Defender for Endpoint

</details>

---

<details>
  <summary><strong> Zero Trust & Purview Governance (Screens 5–20)</strong></summary><br>



![SC21](https://github.com/user-attachments/assets/e2fd94b4-869d-440a-8d20-b8ed99ef5f90)
![SC22](https://github.com/user-attachments/assets/a3844e53-06db-4a52-aa2a-717390a775b0)
![SC23](https://github.com/user-attachments/assets/0ece9270-2f0c-4cd4-a8f6-9ed398228593)
![SC24](https://github.com/user-attachments/assets/8664bf0e-fdcb-4e62-9fe5-7907601e6f4c)
![SC25](https://github.com/user-attachments/assets/fee3681d-65ef-4fc9-8260-1abcd7efc5bb)
![SC26](https://github.com/user-attachments/assets/ed73f582-451d-4990-8784-f15e5c2a6740)
![SC27](https://github.com/user-attachments/assets/76ee4f9f-c366-4715-8640-95f250f49b4b)
![SC28](https://github.com/user-attachments/assets/222f7e8b-ec97-4cbe-8ab3-b0c14b6e9669)
![SC29](https://github.com/user-attachments/assets/3c533935-d2a0-4c54-9559-e781f0475620)
![SC30](https://github.com/user-attachments/assets/541faccd-68b5-49c0-83a9-dca6b8f72fd5)
![SC31](https://github.com/user-attachments/assets/f5ee2d79-5485-4378-bb31-b42149022e02)
![SC32](https://github.com/user-attachments/assets/1c3e2358-2803-4b63-b2f7-3357156d7d38)
![SC33](https://github.com/user-attachments/assets/1b16e9c1-ac29-4ead-bcb9-48bf599a84ef)
![SC34](https://github.com/user-attachments/assets/e9aaac31-8be9-4065-a432-bb7a7ef145c0)
![SC35](https://github.com/user-attachments/assets/a78b7048-7d50-4497-87ea-7561352ba41d)

</details>






