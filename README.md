# Home SOC Lab with Microsoft Sentinel

This project is a practical simulation of a home-based Security Operations Center (SOC) using Microsoft Azure and Microsoft Sentinel. The lab exposes a Windows virtual machine (honeypot) to the internet, captures attack traffic, and visualizes geographic sources of failed login attempts in real time.

---

## 📦 Lab Summary
- Set up a honeypot VM in Azure using a free-tier account
- Opened the system to public access to attract attacks
- Forwarded logs to Azure Log Analytics Workspace
- Integrated with Microsoft Sentinel (SIEM) for real-time visibility
- Applied KQL (Kusto Query Language) to query and analyze logs
- Created a heatmap dashboard of attacker locations

---

## 🛠️ Lab Setup and Execution

### Create a free Azure account using a personal email  
![Step 1](Home%20SOC/1.png)

### Log in to the Azure Portal (portal.azure.com)  
![Step 2](Home%20SOC/2.png)

### Create a new Resource Group (e.g., rg-sock-lab)  
![Step 3](Home%20SOC/3.png)

### Create a Virtual Network (vnet-sock-lab) in the same region  
![Step 4](Home%20SOC/4.png)

### Confirm Resource Group and VNet creation  
![Step 5](Home%20SOC/5.png)

### Begin creation of a new Virtual Machine  
![Step 6](Home%20SOC/6.png)

### Configure VM: name it generically (e.g., corpnet-east1)  
![Step 7](Home%20SOC/7.png)

### Choose Windows 10 image and select an appropriate VM size  
![Step 8](Home%20SOC/8.png)

### Set a strong username and password for the VM  
![Step 9](Home%20SOC/9.png)

### Enable RDP and complete VM basic configuration  
![Step 10](Home%20SOC/10.png)

### Disable boot diagnostics and finalize settings  
![Step 11](Home%20SOC/11.png)

### Deploy the Virtual Machine  
![Step 12](Home%20SOC/12.png)

### Verify VM components: public IP, NIC, NSG, and disk  
![Step 13](Home%20SOC/13.png)

### Edit the Network Security Group (NSG)  
![Step 14](Home%20SOC/14.png)

### Delete default RDP rule and create 'Allow All' inbound rule  
![Step 15](Home%20SOC/15.png)

### Configure NSG: allow all traffic from any source  
![Step 16](Home%20SOC/16.png)

### Open RDP to the VM using Remote Desktop (Windows/macOS)  
![Step 17](Home%20SOC/17.png)

### Log in to the VM using the credentials set earlier  
![Step 18](Home%20SOC/18.png)

### Access Windows Firewall settings on the VM  
![Step 19](Home%20SOC/19.png)

### Disable all firewall profiles inside the VM  
![Step 20](Home%20SOC/20.png)

### Ping the VM from your local machine to verify connectivity  
![Step 21](Home%20SOC/21.png)

### Attempt failed logins (e.g., using fake user 'employee')  
![Step 22](Home%20SOC/22.png)

### Open Event Viewer and navigate to Security logs  
![Step 23](Home%20SOC/23.png)

### Search for failed logon events (ID 4625)  
![Step 24](Home%20SOC/24.png)

### Filter logs to confirm failed login entries  
![Step 25](Home%20SOC/25.png)

### Create a Log Analytics Workspace in the same Resource Group  
![Step 26](Home%20SOC/26.png)

### Deploy Microsoft Sentinel and connect it to the workspace  
![Step 27](Home%20SOC/27.png)

### Access Sentinel and open the Content Hub  
![Step 28](Home%20SOC/28.png)

### Install the Windows Security Events Data Connector  
![Step 29](Home%20SOC/29.png)

### Begin connector configuration and open VM extensions tab  
![Step 30](Home%20SOC/30.png)

### Install Azure Monitor Agent via the data connector  
![Step 31](Home%20SOC/31.png)

### Create a Data Collection Rule (DCR) to send logs from VM  
![Step 32](Home%20SOC/32.png)

### Select the VM in the DCR and finalize creation  
![Step 33](Home%20SOC/33.png)

### Verify Azure Monitor Agent installation status  
![Step 34](Home%20SOC/34.png)

### Open Log Analytics Workspace > Logs and test queries  
![Step 35](Home%20SOC/35.png)

### Run basic query on 'SecurityEvent' to view ingested logs  
![Step 36](Home%20SOC/36.png)

### Wait 20–30 minutes for logs to populate (auto-ingest delay)  
![Step 37](Home%20SOC/37.png)

### Write and run basic KQL queries to filter logs  
![Step 38](Home%20SOC/38.png)

### Project and rename fields like attacker IP and timestamp  
![Step 39](Home%20SOC/39.png)

### Use external IP lookup to geolocate attacker addresses  
![Step 40](Home%20SOC/40.png)

### Prepare a GeoIP watchlist CSV file for upload  
![Step 41](Home%20SOC/41.png)

### Create a Watchlist in Sentinel and upload the CSV  
![Step 42](Home%20SOC/42.png)

### Verify Watchlist upload and item count (e.g., 55k entries)  
![Step 43](Home%20SOC/43.png)

### Query logs joined with GeoIP to enrich logs with locations  
![Step 44](Home%20SOC/44.png)

### Use `project` in KQL to select and rename key columns  
![Step 45](Home%20SOC/45.png)

### Review enriched log results with attacker geolocation  
![Step 46](Home%20SOC/46.png)

### Create a new Workbook in Sentinel to visualize data  
![Step 47](Home%20SOC/47.png)

### Finalize and save the workbook (e.g., 'Windows VM Attack Map')  
![Step 48](Home%20SOC/48.png)

---

## 🧰 Tools Used
- Microsoft Azure (VM, NSG, Resource Groups)
- Log Analytics Workspace
- Microsoft Sentinel
- KQL (Kusto Query Language)
- Workbook with GeoIP Mapping

---
