## Part:1 Lab03 - Create a Microsoft Sentinel

## Lab scenario
In this lab you will walk through the process of creating an  Microsoft Sentinel instance.  You will also set up the permissions to ensure access to the resources that will get deployed to support  Microsoft Sentinel.  Once this basic setup is done you will walk through the steps for connecting Microsoft Sentinel to your data sources, set up a workbook, and do a brief walk-through of some of key capabilities available in Microsoft Sentinel. 

## Lab objectives

In this lab, you will complete the following tasks:

+ Task 1: Create a Microsoft Sentinel instance
+ Task 2: Built-in Microsoft Sentinel roles
+ Task 3: Data connector to your instance of Microsoft Sentinel
+ Task 4: Explore on capabilities available in Sentinel

## Estimated timing: 60 minutes

## Architecture diagram

![](../media/sc900lab7-(1).png)

## Task 1:  Create a Microsoft Sentinel instance

1. In the Azure portal, in the **Search Bar** search for **Microsoft Sentinel** then select **Microsoft Sentinel** from the search results. 

   ![Picture 1](../media/image_7.png)

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

   ![Picture 1](../media/image_8.png)
   
   ![Picture 1](../media/image_9.png)

1. Keep this page open, as you will use it in the next task.
