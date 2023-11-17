## Lab 03 - Create a Microsoft Sentinel


## Task 1:  Create a Microsoft Sentinel instance

1. In the Azure portal, in the **Search resources, services, and docs** search for **Microsoft Sentinel** then select **Microsoft Sentinel** from the search results.  

1. From the Microsoft Sentinel page, select **+ Create**.

1. From Add Microsoft Sentinel to a workspace, select **+ Create a new workspace**.

1. From the basics tab of the Create Log Analytics workspace, enter the following

    | Setting | Action |
    | -- | -- |
    | Subscription |  **Select the given subscription (1)**  |
    | Resource group | select ResourceGroup |
    | Name | LogAnalytics-workspace-<inject key="DeploymentID" enableCopy="false"/>** |
    | Region | leave this default |
    |||

    ![Picture 1](../media/image1-lab7.png)

1. click **Review + Create**.   

1. Verify the information you entered then select **Create**.

1. If you don’t see the new workspace listed, select **Refresh**, then select newly created workspace **LogAnalytics-workspace-<inject key="DeploymentID" enableCopy="false"/> (1)** and click on **Add (2)**.

   ![Picture 1](../media/image2-lab(7).png)

1. Once the new workspace is added, the Microsoft Sentinel | News & guides page will display., including that the Microsoft Sentinel free trial is activated. Select **OK**  Note the three steps listed on the Get started page.

1. Keep this page open, as you will use it in the next task.
