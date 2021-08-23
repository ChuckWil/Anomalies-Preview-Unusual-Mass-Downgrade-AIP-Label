The anomaly simulation package is provided by the SOC-ML Anomalies team to enable demo results for a specific anomaly rule named: 
"(Preview) Unusual mass downgrade AIP label" in your Azure Sentinel instance.

This will not impact production workloads and is designed to demonstrate results of positive indicators for the "(Preview) Unusual mass downgrade AIP label" anomaly rule.

The package includes:
1 - PS script with logic to ingest the simulated anomaly data 
2 - A csv file with the corresponding anomoly preview events

# Anomalies preview Configuration Steps

Ensure you have recorded your WorkspaceID, LogAnalytics WorkspaceId and TenantId.   

#Download the .CSV and PowerShell script (text file). Edit the PS with your information as in the following script snippet and save as .PS:

*script snip

$LogAnalyticsWorkspaceId = "Your WorkspaceIDxxxxxxxxx"

$LogAnalyticsPrimaryKey = "Your LogAnalyticsPrimary Keyxxxxxxxxxxxx=="

$TenantId = "TenantIDxxxxxxxxxx" 

end snip

Upload the files to our your Azure storage via the Cloudshell or other methods. 
Note:  Ensure the PS and CSV files are in the same directory.  Additionally,  line 83 of the script identifies the csv data file by name, verify this name matches the actual file or the script will error. 

# Execute the script.

The script will ingest the demo data into your Sentinel instance.  You should see a new custom log named:  "InformationProtectionLogs_CL" as defined in the script.  

Inside the log you will have 62 events marked:        
# "(Preview) Unusual mass downgrade AIP label". 

A prescheduled backend job will move events matchings the rule,                  "(Preview) Unusual mass downgrade AIP label") to the Anomalies table.  Depending on when you run the script it may intially take 12 hours to record in the anomalies table as the job is scheduled to run once daily by region.

When complete your will have a:

- new customer log
- log entries "(Preview) Unusual mass downgrade AIP label")
- Entries in the Anomalies table you can query to show "Unsual mass downgrade AIP Label" events matching the rule

Script execution and data ingestion simulates what would happen in the event the anomaly rule is triggered.

<img src= "/images/AIPRule.PNG" >
  
# Details on ML and Anomalies are outline here: 
https://techcommunity.microsoft.com/t5/azure-sentinel/democratize-machine-learning-with-customizable-ml-anomalies/ba-p/2346338


# Work with anomaly detection analytics rules in Azure Sentinel
https://docs.microsoft.com/en-us/azure/sentinel/work-with-anomaly-rules


