The anomaly simulation package is provided by the SOC-ML Anomalies team to enable customers to visualize and demo anomalous activity within their Azure Sentinel consoles.

The package includes:
1 - PS script with logic to ingest the simulated anomaly data (marked as demo)
2 - A csv file with the corresponding anomoly events

It is highly recommended to run the scripted data ingestion routine in a demo/test enviroment.  

Ensure you have recorded your WorkspaceID, LogAnalytics WorkspaceId and TenantId.  Update the script with this information as indicated below. 

<script snip>

$LogAnalyticsWorkspaceId = "Your WorkspaceIDxxxxxxxxx"

$LogAnalyticsPrimaryKey = "Your LogAnalyticsPrimary Keyxxxxxxxxxxxx=="

$TenantId = "TenantIDxxxxxxxxxx" 

<end snip>


If necessary configure the monitoring agent on VMs you wish to affect and view results.  See agent configuration steps: 
https://docs.microsoft.com/en-us/services-hub/health/mma-setupactual

Upload the files to our your Azure storage via the Cloudshell or other methods. 
Note:  Ensure the PS and CSV files are in the same directory.  Additionally line 83 of the script identifies the csv data file by name, verify this name matches the actual file or the script will error. 

Execute the script.

You should see a new custom log named:  "InformationProtectionLogs_CL" as defined in the script.  You will have 62 events marked as demo in this log. 

? - a rule can be created to trigger an alert based on criteria "X" from the log entries





