## Part:2 Lab 02 Create Detections

## Lab scenario

You are a Security Operations Analyst working at a company that implemented Microsoft Sentinel. You are going to work with Log Analytics KQL queries and from there, you will create custom analytics rules to help discover threats and anomalous behaviors in your environment.

Analytics rules search for specific events or sets of events across your environment, alert you when certain event thresholds or conditions are reached, generate incidents for your SOC to triage and investigate, and respond to threats with automated tracking and reMediation processes.

## Lab objectives
 In this lab, you will Understand following:
- Task 1: Create a Security Operations Center Team in Microsoft Teams
- Task 2: Create a Playbook in Microsoft Sentinel
- Task 3: Update a Playbook in Microsoft Sentinel
- Task 4: Persistence Attack Detection

## Estimated timing: 120 minutes

## Architecture Diagram

  ![Lab overview.](../media/lab02part2.png)

### Task 1: Create a Security Operations Center Team in Microsoft Teams

In this task, you'll create a Microsoft Teams team for use in the lab.

1. In the lab virtual machine, select **microsoft Teams** icon from the desktop and click to open.

1. Close any Teams pop-ups that may appear.

1. If not already selected, select **Teams** on the left menu, then at the top, select the **+** icon.

1. Select the **Create Team** option.

1. Select the **From scratch** button.

1. Select the **Private** button.

1. Give the team the name: type **SOC** and select the **Create** button.

1. In the Add members to SOC screen, select the **Skip** button. 

1. Scroll down the Teams blade to locate the newly created SOC team, select the ellipsis **(...)** on the right side of the name and select **Add channel**.

1. Enter a channel name of *New Alerts* then select the **Add** button.


### Task 2: Create a Playbook in Microsoft Sentinel

In this task, you'll create a Logic App that is used as a Playbook in Microsoft Sentinel.

1. In the Microsoft Edge browser, navigate to [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel).

<!--- the Azure portal at https://portal.azure.com.

1. In the **Sign in** dialog box, copy and paste in the **Tenant Email** account provided by your lab hosting provider and then select **Next**.

1. In the **Enter password** dialog box, copy and paste in the **Tenant Password** provided by your lab hosting provider and then select **Sign in**.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace you created earlier.

1. Select the **Community** page under the *Content management* area on the left side of the page.

1. On the right pane, select the **Onboard community content** link. This opens a new tab in the Microsoft Edge Browser for Microsoft Sentinel GitHub content. **Hint:** You might need to scroll right to see the link. Alternatively, follow this link instead: [Microsoft Sentinel on GitHub](https://github.com/Azure/Azure-Sentinel). --->

1. Scroll down and select the **Solutions** folder.

1. Next select the **SentinelSOARessentials** folder, then the **Playbooks** folder.

1. Select the **Post-Message-Teams** folder.

1. In the readme.md box, scroll down to the *Quick Deployment* section, **Deploy with incident trigger (recommended)** and select the **Deploy to Azure** button.  

1. Make sure your Azure Subscription is selected.

1. For Resource Group, select **Create New**, enter *RG-Playbooks* and select **OK**.

1. Leave **(US) East US** as the default value for *Region*.

1. Rename the *Playbook Name* to "PostMessageTeams-OnIncident" and select **Review + create**.

1. Now select **Create**. 

    >**Note:** Wait for the deployment to finish before proceeding to the next task.

### Task 3: Update a Playbook in Microsoft Sentinel

In this task, you'll update the new playbook you created with the proper connection information.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select your Microsoft Sentinel Workspace.

1. Select **Automation** under the *Configuration* area and then select the **Active Playbooks** tab.

1. Select **Refresh** from the command bar in case you don't see any playbooks. You should see the playbook created from the previous step with the **Microsoft Sentinel Incident** *Trigger kind*.

1. Select the **PostMessageTeams-OnIncident** playbook name.

1. On the Logic App page for *PostMessageTeams-OnIncident*, in the command menu, select **Edit**.

    >**Note:** You may need to refresh the page.

1. Select the *first* block, **Microsoft Sentinel incident (Preview)**.

1. Select the **Change connection** link.

1. Select **Add new** and select **Sign in**. In the new window, select your Azure subscription admin credentials when prompted. The last line of the block should now read "Connected to your-admin-username".

1. Now select the *second* block, **Connections**.

1. Select **Add new** and select your Azure admin credentials when prompted. The last line of the block should now read "Connected to your-admin-username".

1. The block has now been renamed to **Post a message (V3)(Preview)**, at the end of the *Team* field, select the **X** to clear the contents. The field is changed to a drop-down with a listing of the available Teams from Microsoft Teams. Select **SOC**.

1. Do the same for the *Channel* field, select the **X** at the end of the field to clear the contents. The field is changed to a drop-down with a listing of the Channels of the SOC Teams. Select **New Alerts**.

1. Select **Save** on the command bar. The Logic App will be used in a future task.

### Task 4: Persistence Attack Detection

In this task, you will create a detection for the first attack of the previous exercise.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Microsoft Sentinel**.

1. Select the Microsoft Sentinel Workspace you created earlier.

1. Select **Logs** from the *General* section.

1. **Run** the following KQL Statement again to recall the tables where we have this data:

    ```KQL
    search "temp\\startup.bat"
    ```
   ![Lab overview.](../media/sc200ex7temp.png)
    
    >**Note:** A result with the event might take up to 5 minutes to appear. Wait until it does. If it does not appear, make sure you have rebooted WINServer as instructed in the previous exercise and that you have completed Task #3 of the Learning Path 6 Lab, Exercise 2.
     
1. The table *SecurityEvent* looks to have the data already normalized and is easy for us to query. Expand the row to see all the columns related to the record.

1. From the results, we now know that the Threat Actor is using reg.exe to add keys to the Registry key and the program is located in C:\temp. **Run** the following statement to replace the *search* operator with the *where* operator in our query:

    ```KQL
    SecurityEvent 
    | where Activity startswith "4688" 
    ```
   ![Lab overview.](../media/sc200ex7log.png)

1. It is important to help the Security Operations Center Analyst by providing as much context about the alert as you can. This includes projecting Entities for use in the investigation graph. **Run** the following query:

    ```KQL
    SecurityEvent 
    | where Activity startswith "4688" 
    | extend timestamp = TimeGenerated, HostCustomEntity = Computer, AccountCustomEntity = SubjectUserName
    ```

1. Now that you have a good detection rule, in the Logs window, select the **+ New alert rule** in the command bar and then select **Create Microsoft Sentinel alert**. This will create a new Scheduled rule. **Hint:** You might need to select the ellipsis (...) button in the command bar.

1. This starts the "Analytics rule wizard". For the *General* tab type:

    |Setting|Value|
    |---|---|
    |Name|Startup RegKey|
    |Description|Startup RegKey in c:\temp|
    |Tactics|Persistence|
    |Severity|High|

1. Select **Next: Set rule logic >** button.

1. On the *Set rule logic* tab, the *Rule query* should be populated already with you KQL query, as well as the entities under *Alert enrichment - Entity mapping*.

    |Entity|Identifier|Data Field|
    |:----|:----|:----|
    |Account|FullName|AccountCustomEntity|
    |Host|Hostname|HostCustomEntity|

1. If **Hostname** isn't selected for *Host* Entity, select it from the drop-down list.

1. For *Query scheduling* set the following:

    |Setting|Value|
    |---|---|
    |Run Query every|5 minutes|
    |Lookup data from the last|1 Days|

    >**Note:** We are purposely generating many incidents for the same data. This enables the Lab to use these alerts.

1. Leave the rest of the options with the defaults. Select **Next: Incident settings>** button.

1. For the *Incident settings* tab, leave the default values and select **Next: Automated response >** button.

1. On the *Automated response* tab under *Automation rules*, select **Add new**.

1. Use the settings in the table to configure the automation rule.

    |Setting|Value|
    |:----|:----|
    |Automation rule name|Startup RegKey|
    |Trigger|When incident is created|
    |Actions |Run playbook|
    |playbook |PostMessageTeams-OnIncident|

    >**Note:** You have already assigned permissions to the playbook, so it will be available.

1. Select **Apply**

1. Select the **Next: Review >** button.
  
1. On the *Review and create* tab, select the **Create** button to create the new Scheduled Analytics rule.

## Review
 In this lab, you will Understand following:
- Create a Security Operations Center Team in Microsoft Teams
- Create a Playbook in Microsoft Sentinel
- Update a Playbook in Microsoft Sentinel
- Persistence Attack Detection
