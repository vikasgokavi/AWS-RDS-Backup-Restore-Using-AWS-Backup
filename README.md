# AWS-RDS-Backup-Restore Using AWS-Backup
AWS Backup simplifies data protection by centralizing and automating backups across AWS services. It's great for compliance, data protection policies, and business continuity. This project covers setting up automated backups for Amazon RDS, restoring backups, and resource cleanup to manage costs efficiently.


## Objectives:

1. Create an on-demand backup job for an Amazon RDS database.
   
2. Utilize a backup plan within AWS Backup to automate backups on a schedule.
   
3. Add resources to an existing backup plan using tags for efficient management.
   
4. Learn how to restore a backup to ensure data recovery and continuity.


## Task 1:  Automating Amazon RDS Backup and restore and Configure an on demand AWS Backup job of an Amazon RDS Database


1. Log in to the AWS Management Console, and open the AWS Backup console.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/60c469d8-0949-4a5d-8ac4-e5becfb60322)

2. Configure the services used with AWS Backup

  On the navigation pane on the left side of the AWS Backup console, under My account, choose Settings.

  ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/48b48842-979d-4c73-a9c5-572a6a47bc82)



3. On the Service opt-in page, choose Configure resources.

   <img width="958" alt="image" src="https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/332ce1d3-f991-408a-82c6-0add57271ae6">


 4.  On the Configure resources page, use the toggle switches to enable or disable the services used with AWS Backup. Choose Confirm when our services are configured.
AWS resources that we're backing up should be in the Region we are using for this how-to guide, and resources must all be in the same AWS Region

  ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/8bad9022-67a5-48b1-915a-88eb0787f412)


6.  Create an on-demand backup job of an Amazon RDS database

  Back in the AWS Backup console, under My account on the left navigation pane, select Protected resources.  

<img width="959" alt="image" src="https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/fc29f3da-10e1-420a-bf91-ffec0ac12d61">


6. From the dashboard, select the Create on-demand backup button.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/a4638333-c872-4f28-a291-81db9b7fd010)



7. On the Create on-demand backup page, choose the following options:

Select the resource type that we want to back up; for example, choose RDS for Amazon RDS.
Choosing the database name or ID of the resource that we want to protect; for example, analytics.
Ensure that Create backup now is selected. This initiates our backup job immediately and enables you to see our saved resource sooner on the Protected resources page.
Select the desired retention period. AWS Backup automatically deletes our backups at the end of this period to save storage costs for us.
Choose an existing backup vault. Choosing Create new Backup vault opens a new page to create a vault and then returns us to the Create on-demand backup page when we are finished.
Under IAM role, choose Default role.
Note: If the AWS Backup Default role is not present in our account, then an AWS Backup Default role is created with the correct permissions.
Select the Create on-demand backup button. This takes us to the Jobs page, where you will see a list of jobs.


![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/141e8c41-836b-4452-81b6-91f0ad79ba79)



8. Choose the Backup job ID for the resource that we chose to back up to see the details of that job.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/9327564d-967d-49a5-b177-d45da62451a2)



## Task 2: Configure automatic AWS backup jobs of an Amazon RDS Database

1. Configure the services used with AWS Backup
   
 Back on the left navigation pane in the AWS Backup console, under My account, choose Settings.

  On the Service opt-in page, choose Configure resources.

  ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/3ec2f768-9699-4a16-823c-87632676022e)


2. On the Configure resources page, use the toggle switches to enable or disable the services used with AWS Backup. Choose Confirm when our services are configured.

AWS resources that we're backing up should be in the Region we are using for this tutorial, and resources must all be in the same AWS Region 

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/04d9d199-611e-4c5c-9455-eabf5de809d7)


3. Configure a backup plan for an Amazon RDS database
   
  In the AWS Backup console, select Backup plans on the left navigation pane under My account, and then Create backup plan.

  ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/dc9e0dea-e5d4-4bd4-9380-4aeedcab0864)


4. AWS Backup provides three ways to get started using the AWS Backup console but for this how-to guide, select Build a new plan:

Start with a template — We can create a new backup plan based on a template provided by AWS Backup. Be aware that backup plans created by AWS Backup are based on backup best practices and common backup policy configurations. When we select an existing backup plan to start from, the configurations from that backup plan are automatically populated for our new backup plan. We can then change any of these configurations according to our backup requirements.
Build a new plan — We can create a new backup plan by specifying each of the backup configuration details, as described in the next section. We can choose from the recommended default configurations.

Define a plan using JSON - We can modify the JSON expression of an existing backup plan or create a new expression.


5. Backup plan name - We must provide a unique backup plan name. If we try to create a backup plan that is identical to an existing plan, we get an AlreadyExistsException error. For this how-to guide, enter RDS-webapp.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/1a407858-d6a1-4bf2-8663-25f3d9c6a049)


6. Backup vault - A backup vault is a container to organize our backups in. Backups created by a backup rule are organized in the backup vault that we specify in the backup rule. We can use backup vaults to set the AWS Key Management Service (AWS KMS) encryption key that is used to encrypt backups in the backup vault and to control access to the backups in the backup vault. We can also add tags to backup vaults to help us organize them. If we don't want to use the default vault, we can create our own.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/dd0c1c90-6c52-4e9a-8062-7434558d98d0)


7. Create new backup vault - Instead of using the default backup vault that is automatically created for us in the AWS Backup console, we can create specific backup vaults to save and organize groups of backups in the same vault.
   
i)  To create a backup vault, choose Create new Backup vault.
ii)  Enter a name for our backup vault. We can name our vault to reflect what we will store in it, or to make it easier to search for the backups we need. For example, we can name it FinancialBackups.
iii)  Select an AWS KMS key. We can use either a key that we already created or select the default AWS Backup master key.
iv)  Optionally, add tags that will help us search for and identify your backup vault.
v)  Select Create Backup vault button.  

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/8103571a-c79c-4024-8088-2d9ae41e5a2e)


8. Backup frequency - The backup frequency determines how often a backup is created. We can choose a frequency of every 12 hours, daily, weekly, or monthly. When selecting weekly, we can specify which days of the week we want backups to be taken. When selecting monthly, we can choose a specific day of the month.

9. Enable continuous backups for point-in-time recovery - With continuous backups, we can perform point-in-time restores (PITR) by choosing when to restore, down to the second. The most time that can elapse between the current state of your workload and our most recent point-in-time restore is 5 minutes. We can store continuous backups for up to 35 days. If we do not enable continuous backups, AWS Backup takes snapshot backups for us.

10. Backup window - Backup windows consist of the time that the backup window begins and the duration of the window in hours. The default backup window is set to start at 5 AM UTC (Coordinated Universal Time) and lasts 8 hours.

    ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/d71324e5-df08-4e6e-b6e8-958c4530bd6c)

11. Transition to cold storage - Currently only Amazon EFS file system backups can be transitioned to cold storage. The cold storage expression is ignored for the backups of Amazon Elastic Block Store (Amazon EBS), Amazon Relational Database Service (Amazon RDS), Amazon Aurora, Amazon DynamoDB, and AWS Storage Gateway.


12. Retention period - AWS Backup automatically deletes our backups at the end of this period to save storage costs for us. AWS Backup can retain snapshots between 1 day and 100 years (or indefinitely, if you do not enter a retention period), and continuous backups between 1 and 35 days.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/4792ed03-4b1d-4d0a-995f-171891d7d291)


13. Copy to destination - As part of our backup plan, we can optionally create a backup copy in another AWS Region. Using AWS Backup, we can copy backups to multiple AWS Regions on-demand, or automatically as part of a scheduled backup plan. Cross-Region Replication (CRR) is particularly valuable if we have business continuity or compliance requirements to store backups a minimum distance away from our production data. When we define a backup copy, we configure the following options:
Copy to destination - The destination Region for the backup copy.
Destination backup vault - The destination backup vault for the copy.
(Advanced Settings) Transition to cold storage
(Advanced Settings) Retention period
Note: Cross-Region Copy incurs additional data transfer costs. We can refer to the AWS Backup pricing page for more information.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/0adc69bd-6651-4a6a-821f-ba90cfe286b8)


14. Tags added to recovery points - The tags that you list here are automatically added to backups when they are created.

    Advanced backup settings - Enables application-consistent backups for third-party applications that are running on Amazon EC2 instances. Currently, AWS Backup supports Windows VSS backups. This is only applicable for Windows EC2 Instances running SQL Server or Exchange databases.

    Choose Create plan.



    ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/cdfaf9a9-fdfb-4de0-9a81-5ef8d11fb1c2)


15. Assign resources to the backup plan
When we assign a resource to a backup plan, that resource is backed up automatically according to the backup plan. The backups for that resource are managed according to the backup plan. We can assign resources using tags or resource IDs. Using tags to assign resources is a simple and scalable way to back up multiple resources.
  Select the created backup plan, and select the Assign resources button.

    ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/388df6ab-dbae-4167-b6cd-12c49f52255d)


 16. Resource assignment name - Provide a resource assignment name.
     
  IAM role - When creating a tag-based backup plan, if we choose a role other than Default role, make sure that it has the necessary permissions to back up all tagged resources. AWS Backup tries to process all resources with the selected tags. If it encounters a resource that it doesn't have permission to access, the backup plan fails.


 ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/a50505b8-1634-4cde-84cd-8542fd58cc36)




 17. Define resource selection - we can choose to include all resource types or specific resource types.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/9dbde90a-34a5-4672-a08f-ab3455e3844c)


18. For resource ID-based assignment, select Resource type and the name of the resource.

  To exclude specific resource IDs, select Resource type and the name of the resource

  ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/716b3c22-05af-4921-9063-3b11be97334f)


19. For tags-based resource assignment, provide the key-value pair of the Amazon RDS database.

  Select Assign resources and the backup plan has the resources assigned to it.  


  ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/89f99390-f077-494a-b6ca-1011e6fcd9cd)

20. Navigate to the AWS Backup console and the backup jobs will be seen under Jobs.
  A backup, or recovery point, represents the content of a resource, such as an Amazon Elastic Block Store (Amazon EBS) volume or Amazon RDS database, at a specified time. Recovery point is a term that refers generally to the different backups in AWS services, such as Amazon EBS snapshots and Amazon RDS backups. In AWS Backup, recovery points are saved in backup vaults, which we can organize according to our business needs. Each recovery point has a unique ID.


![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/97061912-44b8-4396-bb69-cb7ddb749923)


## Task 3: Restore of an AWS RDS Database using AWS BAckup


1. Navigate to the backup vault that was selected in the backup plan and select the latest completed backup.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/ffa42437-be08-43ec-955f-04cd374a51f6)


2. To restore the database, click on the recovery point ARN and select Restore.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/aac1cb75-fb29-4d59-b3d9-312a5c065261)


3. The restore of the ARN will bring us to a Restore backup screen that will have Instance specifications and configurations for the Amazon RDS database. Select the DB engine, License Model, and DB instance class.

Multi AZ - Using a Multi-AZ deployment will automatically provision and maintain a synchronous standby replica in a different Availability Zone. Note that we will have to pay for Multi-AZ deployment.

Storage type - Select Provisioned IOPS (SSD).

Provisioned IOPS - The requested number of I/O operations per second that the DB instance can support. Enter 3000.


![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/d7e95182-2c16-4eb5-979c-05c169789733)


4. DB Instance Identifier - Type a name for the DB instance that is unique for our account in the Region that we selected. If we're restoring from a DB instance that we deleted after we made the DB snapshot, we can use the name of that DB instance.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/14ac3f3c-38fd-4841-9a12-588f50534ec6)


5. Select the appropriate network and security settings:

VPC - Select the VPC where the database needs to be restored to.

Subnet group - Select the subnet group in the VPC where the database needs to be restored to.
Public accessibility - We can choose if we need the DB Instances to have a public address or not. If we choose Yes, this will allocate an IP address for our database instance so that we can directly connect to the database from our own device.
Availability zone - Choose No Preference.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/7fb433a6-b494-44de-8d98-5c3c488a5d4e)


6. Select the appropriate database options.

Database port - Leave the default value of 3306.
DB parameter group - Leave the default value.
Option Group - Leave the default value. Amazon RDS uses option groups to enable and configure additional features.
IAM DB Authentication Enabled - We can authenticate to our DB instance using AWS Identity and Access Management (IAM) database authentication. Select Enable IAM DB authentication.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/3e6a01f1-c4d3-48b0-96ca-96ca82784b5c)


7. Copy Tags to Snapshots - Tags can be set on the database instances to be automatically copied to any automated or manual database snapshots that are created from our instances.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/4c650efa-964a-4228-b9a0-5f1ee9f386a9)


8. Encryption - This is the master key that will be used to protect the key that is used to encrypt the database volume. We can choose from master keys in your AWS account or enter the Amazon Resource Name (ARN) of a key from a different account.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/8eaaeda3-3661-4665-a379-7de9162453bb)


9. Log exports - Select the log types to publish to Amazon CloudWatch logs.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/1130a53f-a405-43b0-afdd-4bba1eeef467)

10. Maintenance - Select Yes if the DB instance should receive automatic engine version upgrades.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/3375d4e3-2bcf-4d63-8330-a843c54c8713)

11. Restore role - Select the Default role or Choose an IAM role.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/153cd944-2507-48ed-9aac-e06d2591ba15)


12. Select Restore backup.

•    Our job will then appear under the Jobs section in the Restore jobs tab in the AWS Backup console.

•    Once the restore job is completed, we can navigate to the Amazon RDS console and use the endpoint to connect to the database.


![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/3a4a965b-eab3-49f3-be3b-b6c67fd8940e)

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/1ea398a1-1916-426f-a734-1d8ca144a36d)

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/80908378-b250-4b3b-85f5-9aee9b504110)


## Task 4: Clean up.

1.  Open the Amazon RDS console.
  In the navigation pane, choose Databases.
  Select the restored RDS database, and choose Actions, Delete.

![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/94403c97-b4cc-41fd-827d-99817011b1e1)



2. To confirm deletion, type delete me into the field.

   ![image](https://github.com/vikasgokavi/AWS-RDS-Backup-Restore-Using-AWS-Backup/assets/105034318/792e7ece-9ac4-471f-9f7b-7f5658c8189d)




## Conclusion:

1. On-demand backup jobs for Amazon RDS databases were created, ensuring data protection.

2. Backup plans within AWS Backup were utilized to automate backups on a schedule, improving efficiency.

3. Resources were added to an existing backup plan using tags, enhancing management capabilities.

4. Backup restoration processes were mastered, ensuring data recovery and continuity in case of incidents.


   

   





   





















     
   





 
