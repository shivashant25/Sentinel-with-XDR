## Lab 07 - Ingest Logs from Microsoft Defender for Endpoint

### Task 1: Explore defender for ingest data

In this task, you will explore ingesting logs from Microsoft Defender for Cloud.

1. In the Search bar of the Azure portal, type *Defender*, then select **Microsoft Defender for Cloud**.

1. From Defender for Cloud's menu, select Environment settings and select the subscription with the Linux machines that you want to receive Defender for Endpoint.

![Picture 1](../media/Subscription_Select.png)

1. In the Monitoring coverage column of the Defender for Server plan, select Settings.

1. In the status of the Endpoint protection component, select On to enable the integration with Microsoft Defender for Endpoint.

![Picture 1](../media/Endpoint_Protection_1.png)

Automatically onboard your Windows and Linux machines to Defender for Endpoint, Detect any previous installations of Defender for Endpoint and reconfigure them to integrate with Defender for Cloud.Onboarding might take up to 1 hour.

1. Select Continue and Save to save your settings.


### Task 2: verify installation of Defender for Endpoint on a machine

**Linux**:

```
sudo mdatp health --get
```

**Windows**:

```
Get-MpComputerStatus
```


