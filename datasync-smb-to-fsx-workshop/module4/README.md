# **AWS DataSync** - Migrate to FSx Windows File Server using AWS DataSync

# Module 4
## Workshop clean-up

To make sure all resources are deleted after this workshop scenario make sure you execute the steps in the order outlined below (you do not need to wait for CloudFormation to finish deleting before moving to the next step):

1. Module 3 - Manual Method
    1. Go to the AWS management console and go to the **DataSync** service.
    2. Select **Tasks** and delete the task you created previously.
    3. Select **Locations** and delete the locations you created previously.
    4. Select **Agents** and delete the agent you activated previously.  Note that this **will not** delete the actual DataSync agent EC2 instance.  That will get deleted when the CloudFormation stack is deleted.

1. Module 3 - CloudFormation
    1. Go to the CloudFormation page and delete the stack named **DMWFSX-DataSync**.

1. Go to the CloudFormation page and delete the stack named **DMWFSX**.
1. (Optional) Delete CloudWatch Log Group (if there is any created manually).
1. Go to **FSx** page > **Backups** and delete all backups created from this workshop.

    > By default, when you delete an Amazon FSx for Windows File Server file system, a final backup is created upon deletion. This final backup isn’t subject to the file system’s retention policy, and must be manually deleted. REF: [awscli doc](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/fsx/delete-file-system.html)

To make sure that all CloudFormation templates have been deleted correctly, confirm that any EC2 instances created in this workshop are in the **terminated** state.
