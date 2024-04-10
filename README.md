# Entra ID-Activity-and-Resource Logs

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/2966b17b-7307-4c6b-bada-ed34c6f73c8a)

## Intro - Entra ID Logs

In this step, I will continue forwarded logs into the Log Analytics Workspace. 

First, I will start with the Entra ID logs formerly known as the Azure Active Directory.

This is also called the Azure Tenant layer.  

It contains the history of the actions that occured in Entra ID:
- Someone signs in the portal
- When someone creates a user account
- When someone assigns a role
- When there is a failed login

I will be focusing on bringing the audit and sign-in logs into the central log repository.

To begin, I will do the following steps:
- Go to the Azure portal
- Search Entra ID
- Scroll down to "Diagnostic Settings" and click it
- Then click 'Add Diagnostic Settings"

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/6a9e22d2-345d-42c8-88a3-3fbc2675674c)
![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/1e2ce5ea-ea92-4672-a772-074e7ecefb7e)

- I gave the name "ds-audit-signin"
- I selected the categories "AuditLogs" and "SignInLogs"
- Under Destination Details, I clicked "Send to Log Analytics Workspace"
  *The specific workspace is "LAW-Cyber-Lab-Ver1"
- And clicked Save
- Now the Aduit Logs and Sing-In Logs will be forwarded to the Log Analytics Workspace

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/3f79dffc-b0b1-4f38-b797-b8cfbe4719ed)

## Activity Log

The Activity Log (Subscription level logging) is the in the Azure Subscription layer.   

It is also know as the "Management Plane",

This layer contains:
- Basically anyhting I do in the Azure portal
  * Create a virtual machine, resource group, storage account
  * Delete a virtual machine, resource group, storage account
  * Changing Network Security Group configurations and etc
 
To forward these logs in the Log Analytics Workspace:
- I went to the Azure portal.
- Typed in "Monitor"
- Clicked on "Activity Log"
- Clicked on "Export Activity Log"
- Clicked "Add Diagnostic Setting"

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/3d5c2e02-deca-4a2c-929b-68e9900cb54b)
![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/a3192083-69bb-45df-a68b-3b6bb51c307f)
![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/9285867f-75de-40ef-bd66-86fe35eeee5f)

- I named the Diagnostic setting "ds-azure-activity"
- Selected all of the categoires
- Then clicked "Send to Log Analytics Workspace" under Destination Details
  * Selected "LAW-Cyber-Lab-Ver1" as the Log Analytics Workspace

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/0c6fbba5-e1c5-4d3f-9e4a-4a38fe58d564)

## Resources Log - Storage Account

Now I will focus on forwarding the Resource Logs into the Log Analytics Workspace.

These logs are from the Azure Resources layer.  

Also known as the "Data Plane".  This layer gives me insight of all the operations performed withing the Azure resources.
Example: The logs in the Linux and Windows Virutal machine.

I will be enabling logging for two things to be sent to the repository:
- The Storage account I created
- The Key Vault that I will also create in this section.
  * A Key Vault is like a password manager.

To begin this process:
- I will go to the Azure portal.
- Type in Storage account and search for "syberlab009"
- Scroll down to "Diagnostic Settings" and click it
- Enable the "blob" 

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/aeefc7cb-f85a-4a2b-b32c-3e4afea574b0)

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/ec62b494-f4f4-49dc-b8a1-736399956743)

- By doing that, actions will be logged into the "Blod" which is the data plane for the Storage account.
- Click "Add diagnostic setting"

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/0e6bb319-c471-4f3e-9488-d21c0a436e02)

- After that, I named the diagnostic setting "ds-storage-account"
- I selected "audit" under category groups
- Under Destination Details, I selected Log Analytics Workspace
  * I selected "LAW-Cyber-Lab-Ver1" as the specific workspace
- And clicked Save
  
![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/43586f49-2330-4d63-b4c6-0dd9941060ae)

Now the Logs from the Storage account will be forwarded to the Log Analytics Workspace

## Resource Log - Key Vault

Now I will focus on creating the Key vault and make sure the logs from the Key Vault are sent to the Log Analytics Workspace

To do this:
- I went to the Azure portal
- Searced Key Vault
- Clicked "Create"
  
![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/96b42880-a220-4a91-828c-3162e404c358)

- I picked the same Resource Group: RG-Cyber-Lab
- Picked the Key Vault name: akv-cyber-lab-365
- Picked the same reigon
- Clicked Next
- Clicked "Vault Access Policy"
- Clciked 'Review and Create"
- The Key Vault has been created

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/c58f1844-4ac7-45ee-a7f3-5dd1f88c81f4)
![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/9568ff54-2589-46e1-bd4b-457042874c0d)

- Now I have make sure the audit logs are forwarded to the Log Analytics Workspace
- I went to Key Vault
- Scrolled down to Diagnostic Settings
- Click "Add Diagnostic Setting"

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/40a42ccc-9a90-433f-989f-482733fe3eaa)

- I named the diagnostic setting: ds-akv
- Checked aduit box
- Clicked "Send to Log Analytics Workspace"
- Selected "LAW-Cyber-Lab-Ver1" as the workspace
- Clicked Save
- Now the Logs will be forwarded to the Central Repository

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/fabc4569-34e5-4092-a107-8b7e691c673a)


## Step 6 is done
- I enabled the logs from Entra ID to be forwarded to the Log Analytics Workspace
- I enabled the logs from the Subscription layer to be forwarded to the Log Analytics Workspace
- I enabled the logs of the Storage account from the resource layer to be forwarded to the Log Analytics Workspace
- I created a Key Vault which is like a password manager
- I enabled the logs from the key vault of the resource layer to be forwarded to the Log Analytics Workspace

![image](https://github.com/Ashrafs-Tech/EntraID-Activity-and-Resource/assets/166546026/7b45f17f-bd6b-44ff-a90d-d957e806fabf)












  



