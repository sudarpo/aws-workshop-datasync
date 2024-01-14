# **AWS DataSync** - NFS server migration using AWS DataSync and AWS Storage Gateway

# Module 1
## Deploy resources in the ON-PREM and IN-CLOUD regions

In this module, you will use CloudFormation scripts to deploy resources in two AWS regions: one that represents the on-premises environment, and one for the in-cloud environment.  Once all resources have been deployed, you will mount an export from the NFS server on the Application server and verify existing files.

![](../images/mod1arch.png)

## Module Steps

#### 1. Deploy AWS resources for the ON-PREMISES region

1. Click one of the launch links in the table below to deploy the **ON-PREMISES** resources using CloudFormation.  To avoid errors during deployment, select a region in which you have previously created AWS resources.

  | **Region Code** | **Region Name** | **Launch** |
  | --- | --- | --- |
  | us-west-1 | US West (N. California) | [Launch in us-west-1](https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | us-west-2 | US West (Oregon) | [Launch in us-west-2](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | us-east-1 | US East (N. Virginia) | [Launch in us-east-1](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | us-east-2 | US East (Ohio) | [Launch in us-east-2](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | eu-west-1 | Ireland | [Launch in eu-west-1](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | eu-central-1 | Frankfurt | [Launch in eu-central-1](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | ap-southeast-1 | Singapore | [Launch in ap-southeast-1](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |
  | ap-southeast-2 | Sydney | [Launch in ap-southeast-2](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=DMW-ONPREM&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/01-nfs-data-migration-workshop-on-prem.yaml) |

2. Click **Next** on the Create Stack page.
3. Select desired EC2 **Instance Type** - depending on budget. Click **Next**.
4. Click **Next** on Stack options page.
5. On the Review page, scroll to the bottom and check the box to acknowledge that CloudFormation will create IAM resources, then click  **Create stack**.

**Note:** Instances that are launched as part of this CloudFormation template may be in the initializing state for few minutes.

While the CloudFormation deployment progresses in the ON-PREMISES region, you can proceed to deploy resources for the IN-CLOUD region.

#### 2. Deploy AWS resources for the IN-CLOUD region

1. Click one of the launch links in the table below to deploy the **IN-CLOUD** resources using CloudFormation.  Use a different region from the ON-PREMISES region.  To avoid errors in deployment, select a region in which you have previously created AWS resources.

  | **Region Code** | **Region Name** | **Launch** |
  | --- | --- | --- |
  | us-west-1 | US West (N. California) | [Launch in us-west-1](https://console.aws.amazon.com/cloudformation/home?region=us-west-1#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | us-west-2 | US West (Oregon) | [Launch in us-west-2](https://console.aws.amazon.com/cloudformation/home?region=us-west-2#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | us-east-1 | US East (N. Virginia) | [Launch in us-east-1](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | us-east-2 | US East (Ohio) | [Launch in us-east-2](https://console.aws.amazon.com/cloudformation/home?region=us-east-2#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | eu-west-1 | Ireland | [Launch in eu-west-1](https://console.aws.amazon.com/cloudformation/home?region=eu-west-1#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | eu-central-1 | Frankfurt | [Launch in eu-central-1](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | ap-southeast-1 | Singapore | [Launch in ap-southeast-1](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |
  | ap-southeast-2 | Sydney | [Launch in ap-southeast-2](https://console.aws.amazon.com/cloudformation/home?region=ap-southeast-2#/stacks/new?stackName=DMW-CLOUD&amp;templateURL=https://workshop-cfn-samples.s3.us-west-1.amazonaws.com/datasync-nfs-migration/02-nfs-data-migration-workshop-in-cloud.yaml) |

2. Click  **Next**  on the Create stack page.
3. Click **Next** (there are no stack parameters) **.**
4. Click  **Next**  again. (skipping the Options and Advanced options sections)
5. On the Review page, scroll to the bottom and check the box to acknowledge that CloudFormation will create IAM resources, then click  **Create stack**.

Wait for the CloudFormation stacks in each region to reach the CREATE\_COMPLETE state before proceeding to the next steps.  It should take about 10 minutes for both CloudFormation stacks to complete.

**NOTE:** If a stack fails to deploy because an EC2 instance type is not available in a particular availability zone, delete the stack and retry in the same region or in a different region.

#### 3. Stack Outputs

Upon completion, each CloudFormation stack will have a list of &quot;Outputs&quot;.  These are values such as IP addresses and resource names that will be used throughout the workshop.  You can either copy these values elsewhere or keep the page open in your browser and refer to them as you go through the workshop.

On the CloudFormation page in the **ON-PREMISES** region, click on the **Outputs** tab, as shown in the image below.  You should see four values listed:

- **appServerPrivateIP** – This is the private IP address of the Application Server.  You will use this when creating the File Gateway file share to limit access to the NFS export.
- **dataSyncAgentPublicIP** – This is the public IP address of the EC2 instance running the DataSync agent.  You will use this when activating the DataSync agent.
- **fileGatewayPublicIP** – This is the public IP address of the EC2 instance running the File Gateway.  You will use this when activating the File Gateway.
- **nfsServerPrivateIP** – This is the private IP address of the NFS server.  You will use this both on the Application Server and when creating a location for DataSync.

  ![](../images/mod1output1.png)

On the CloudFormation page in the **IN-CLOUD** region, click on the **Outputs** tab as shown in the image below.  You should see two values listed:

- **bucketName** – This is the name of the S3 bucket where the data will be copied to.  You will use this when creating a file share on the File Gateway.
- **iamRoleForDataSync** – This is the role that will be used by the DataSync agent to write files to the S3 bucket.  You will use this when creating the S3 location for DataSync.

  ![](../images/mod1-output2.jpg)

#### 4. Connect to the Application server

1. From the AWS console in the **ON-PREMISES** region, click  **Services**  and select  **EC2.**
2. Select  **Instances**  from the menu on the left.
3. Right-click on the **ApplicationServer** instance and select  **Connect** from the menu.

Connect to the instanct directly through your browser using either Session Manager:

  ![](../images/mod1-sessionmanager.jpg)

 A new tab will be opened in your browser with a command line interface (CLI) to the Application server. Keep this tab open - you will use the command line on the Application server throughout this workshop.

## Validation Step

In the CLI for the Application server, run the following commands to mount the NFS export and verify the files on the NFS server.  Use the **nfsServerPrivateIP** value from the **ON-PREMISES** CloudFormation stack output.

    $ sudo mount -t nfs <nfs-server-ip-address>:/media/data /mnt/data
    $ ls /mnt/data/images

In the /mnt/data/images folder you should see 200 image files, as shown below.  These image files represent the NFS server data that will be migrated to the S3 bucket in the IN-CLOUD region.

![](../images/mod1cli1.png)

## Module Summary

In this module, you deployed all of the resources necessary to complete this workshop in both the ON-PREMISES region and the IN-CLOUD region.  You have also mounted the NFS export on the Application server and verified your data set.

In the next module, you will create a DataSync task to do an initial copy of files from the NFS server to the S3 bucket.

Go to [Module 2](../module2/).
