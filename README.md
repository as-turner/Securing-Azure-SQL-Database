# Securing Azure SQL Database

![Securing Azure SQL Database](https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/c6e5d63e-2509-4e17-a715-48c4b3518d4b)

## Introduction
In this lesson, you will learn how to implement various security features for an Azure SQL Database. The exercise consists of four tasks: deploying an Azure SQL Database, configuring advanced data protection, configuring data classification, and configuring auditing. These tasks will help you enhance the security of your SQL Database and protect sensitive data.

#### Prerequisites:

- An Azure subscription with Owner or Contributor role access.
- Basic understanding of Azure portal navigation.

Lesson Steps:

<details> 
  
  <summary> 
    
### Step 1: Deploy an Azure SQL Database
    
  </summary>

- Sign in to the Azure portal using your Azure account.
- Open the Azure portal at `https://portal.azure.com/`.
 -In the search bar at the top of the portal, type "Deploy a custom template" and press Enter.
- On the Custom deployment blade, select "Build your own template in the editor."
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/58399f1c-d8dc-4c6a-a4f6-31de7def8839" height="60%" width="60%" alt="build a template"/>
  
- On the Edit template blade, click "Load file" and locate the file [JSON file](). Click Open.
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/c30a506d-449d-4dff-90c6-e7842fb9a837" height="60%" width="60%" alt="load json template"/>
  
- Review the template content that describes the deployment of an Azure SQL Database.
- Click Save on the Edit template blade.
- On the Custom deployment blade, configure the following settings:
- Subscription: Select the Azure subscription you will use for this lab.
- Resource group: Click "Create new" and type the name "AZ500LAB11".
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/301c45aa-af6d-462e-b306-e06436a9a0e5" height="60%" width="60%" alt="create resource group for custom deployement"/>
  
- Location: Select "(US) South Central US" or your preferred location that is nearest to you. This has to match the location that is in the template. 
- Click "Review + Create" and then click Create.
- Wait for the deployment to complete.

  </details>
  
  #
  
  <details>
  
<summary>
  
### Step 2: Configure Advanced Data Protection
    
</summary>

In the Azure portal, search for "Resource groups" and select it from the results.

- On the Resource groups blade, locate and click on the "AZ500LAB11" entry.
- On the AZ500LAB11 blade, click the entry representing the newly created SQL Server.
- On the SQL server blade, go to the Security section and click "Microsoft Defender for Cloud".
- Select "Enable Microsoft Defender for SQL" and wait for the notification indicating that Azure Defender for SQL has been successfully enabled.
  
  ![Enable Defender for SQL under Microsoft Defender for Cloud](https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/6ce425de-106f-4972-b95e-da50e46c6aff)

  
- On the SQL server blade, in the Security section, click on the "Microsoft Defender for Cloud" page.
- In the "Microsoft Defender for SQL: Enabled at the subscription-level (Configure)" parameter, click "(configure)". Refresh the browser if it's not displaying.
  
  <img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/9e5c9532-68ec-432a-a5b2-c04114643c57" height="50%" width="50%" alt="Confirm Microsoft Defender for SQL has been Enabled"/>
  
- On the Server Settings blade, review the information about pricing, trial period, vulnerability assessment settings, and advanced threat protection settings.
- Go back to the Microsoft Defender for Cloud blade and review recommendations and security alerts.
  
  >**Note**: Recommendations may take some time to appear. You can proceed to the next task while waiting.
  
  </details>
  
  #
  
  <details>
  
<summary> 
  
### Step 3: Configure Data Classification

</summary>

On the SQL server blade, in the Settings section, click "SQL Databases".
  
- Select the "AZ500LabDb" entry from the list of databases.
- On the AZ500LabDb SQL database blade, in the Security section, click "Data Discovery & Classification".
- On the Data Discovery & Classification blade, click the "Classification" tab.
  
  >**Note**: The classification engine scans your database for columns containing potentially sensitive data and provides recommended column classifications.

- Click the text message "We have found 15 columns with classification recommendations" displayed on the blue bar at the top of the blade.
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/de0bf138-0f31-43e8-a22e-47635d757cea" height="80%" width="80%" alt="Data and Discovery Classification"/>

  
- Review the listed columns and the recommended sensitivity labels.
- Enable the "Select all" checkbox and then click "Accept Selected Recommendations".
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/4ffe51af-6f56-49b7-9a51-cefd168d2460" height="80%" width="80%" alt="Classification Select All"/>
  
  >**Note**: Alternatively, you can select specific columns and dismiss others.

  >**Note**: You can also change the information type and sensitivity label.
Once you have completed your review, click "Save".
  
 <img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/a78a99de-8a0b-41a9-a47d-8ef9f66de381" height="80%" width="80%" alt=" Save Selected Data Classifications"/>


  >**Note**: This will complete the classification and persistently label the database columns with the new classification metadata.

- Back on the Data Discovery & Classification blade, go to the "Overview" tab and note the updated classification information.

</details> 

#

<details> 
  
<summary>

### Step 4: Configure Auditing

</summary> 
    
In the Azure portal, navigate back to the SQL Server blade.

- In the Security section, click "Auditing".
  
  >**Note**: This is server-level auditing, and the default settings include auditing queries, stored procedures, successful and failed logins.

- Set the "Enable Azure SQL Auditing" switch to "ON" to enable auditing.
- Select the Storage checkbox, and the entry boxes for Subscription and Storage Account will appear.
- Choose your Subscription from the dropdown list.
- Click "Storage account" and choose "Create new".
- On the Create storage account blade, enter a globally unique name consisting of between 3 and 24 lowercase letters and digits. Click OK.
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/6fec4962-b6f2-44d7-b4ec-05040b06d919" height="80%" width="80%" alt="Create Storage Account"/>


  >**Note**: Refresh the browser if the storage account doesn't immediately become available.
  
- Back on the Auditing blade, under Advanced properties, set "Retention (days)" to 5.
- Click "Save" to save the auditing settings.
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/cdee1525-cdd5-483d-ab40-5d6008167f71" height="80%" width="80%" alt="Enable Azure SQL Auditing"/>

  >**Note**: If you receive an error message regarding an invalid storage container path, wait a few minutes and click "Storage account". On the Choose storage account blade, select the newly created storage account, and then click "Save".

- On the SQL Server blade, go to the Settings section and click "SQL Databases".
- Select the "AZ500LabDb" entry from the list of databases.
- On the AZ500LabDb SQL database blade, in the Security section, click "Auditing".
  
  >**Note**: This is database-level auditing, and server-level auditing is already enabled.
  
  >**Note**: Audits can be written to an Azure storage account, Log Analytics workspace, or Event Hub.
  
- Click "View Audit Logs".
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/73dfd98c-be65-4623-ba61-1c6874232757" height="80%" width="80%" alt="View Audit Logs for SQL Database"/>

  
- On the Audit records blade, you can switch between Server audit and Database audit.
  
<img src="https://github.com/0xbythesecond/Securing-Azure-SQL-Database/assets/23303634/41545846-17e7-4d9b-ad10-15165c376eeb" height="80%" width="80%" alt="Audit Records"/>
  
  >**Note**: Since the SQL server and database were created recently, there may not be any events available at this point.
  
## Conclusion
Congratulations! You have successfully completed the exercise on implementing SQL Database security features. In this lesson, you learned how to deploy an Azure SQL Database, configure advanced data protection, configure data classification, and configure auditing. These security measures will help you protect your SQL Database and sensitive data. Remember to clean up your resources to avoid unexpected costs.

Clean Up Resources:

Open the Azure Cloud Shell by clicking the first icon in the top right of the Azure portal.
If prompted, select PowerShell and Create storage.
In the PowerShell session within the Cloud Shell pane, run the following command to remove the resource group created in this lab:

```powershell
Remove-AzResourceGroup -Name "AZ500LAB11" -Force -AsJob
```
  
Close the Cloud Shell pane.
Now you can confidently implement SQL Database security features and ensure the protection of your valuable data.

</details> 
