# Introduction to AWS Identity and Access Management (IAM)
In many business environments, access involves a single login to a computer or a network of computer systems that provides the user access to all resources on the network. This access includes rights to personal and shared folders on a network server, company intranets, printers, and other network resources and devices. Unauthorized users can quickly exploit these same resources if the access control and associated authentication procedures are not set up properly.

In this lab, you will explore users, user groups, and policies in the AWS Identity and Access Management (IAM) service.

## OBJECTIVES
Inspect the IAM account password policy
Explore pre-created IAM users and user groups
Inspect IAM policies as applied to the pre-created user groups
Add users to user groups with specific capabilities active
Locate and use the IAM sign-in URL
Experiment with the effects of policies on service access


The current environment has the AWS account located at the top with separate IAM Users and IAM Groups. Under IAM Users, you have the following: user-1, user-2, and user-3. Under IAM Groups, you have the following: EC2-Admin, EC2-Support, and S3-Support. Within these groups, they have specific IAM policies attached to them giving each user access. For EC2-Admin, the IAM Policy gives user-3 EC2 View, Start, and Stop access. The EC2-Support IAM policy gives user-2 EC2 Read-Only access. The S3-Support IAM Policy gives user-1 S3 Read-Only access.

AWS service restrictions
During this lab, you might receive error messages when performing actions beyond the steps in this lab. These messages will not impact your ability to complete the lab.

IAM

IAM can be used for the following:

Manage IAM users and their access: You can create users and assign them individual security credentials (access keys, passwords, and multi-factor authentication devices). You can manage permissions to control which operations a user can perform.

Manage IAM roles and their permissions: An IAM role is similar to a user in that a role is an AWS identity with permission policies that determine what the identity can and cannot do in Amazon Web Services (AWS). However, instead of being uniquely associated with one person, a role is intended to be assumable by anyone who needs it.

Manage federated users and their permissions: You can activate identity federation to allow existing users in your enterprise to access the AWS Management Console, to call AWS application programming interfaces (APIs), and to access resources without the need to create an IAM user for each identity.

Duration
This lab requires approximately 60 minutes to complete.

Start lab
To launch the lab, at the top of the page, choose Start lab.
 You must wait for the provisioned AWS services to be ready before you can continue.

To open the lab, choose Open Console.
You are automatically signed in to the AWS Management Console in a new web browser tab.

 Do not change the Region unless instructed.

COMMON SIGN-IN ERRORS
Error: You must first sign out


If you see the message, You must first log out before logging into a different AWS account:

Choose the click here link.
Close your Amazon Web Services Sign In web browser tab and return to your initial lab page.
Choose Open Console again.
Error: Choosing Start Lab has no effect
In some cases, certain pop-up or script blocker web browser extensions might prevent the Start Lab button from working as intended. If you experience an issue starting the lab:

Add the lab domain name to your pop-up or script blocker’s allow list or turn it off.
Refresh the page and try again.
Task 1: Inspecting the IAM account password policy
In this task, you inspect the password policy for your AWS account. This policy affects all the users associated with the account.

First, note the Region that you are in (for example, Oregon). The upper-right corner of the console page displays your Region.

In the AWS Management Console, in the search  box, enter 

IAM
 and select it.

In the left navigation pane, choose Account settings.

Here you can see the default password policy that is currently in effect.

Under Password policy, examine the following configurations:

Password minimum length
Password strength
Other requirements
Note: These options are provided to strengthen the password requirements. Custom password policy lets you update these configurations in a real worl environment.

SUMMARY OF TASK 1
In this task, you inspected the password requirements by obserrving password policy configuration parameters.

Task 2: Exploring users and user groups
In this task, you explore the users and user groups that have already been created for you in IAM.

In the left navigation pane, choose Users.

The following IAM users have been created for you:

user-1
user-2
user-3
Choose user-1.

This option bring you to a Summary page for user-1. The Permissions tab is displayed.

Notice that user-1 does not have any permissions.

Choose the Groups tab.

user-1 is also is not a member of any user groups.

 A user group consists of several users who need access to the same data. Privileges can be distributed to the entire group of users rather than to each individual. This option is much more efficient when applying permissions and provides greater overall control of access to resources than applying permissions to individuals.

Choose the Security credentials tab.

user-1 is assigned a Console password.

In the left navigation pane, choose User groups.

The following user groups have already been created for you:

EC2-Admin
EC2-Support
S3-Support
Choose the EC2-Support group.

This option brings you to the Summary page for the EC2-Support group.

Choose the Permissions tab.

This group has a managed policy associated with it called AmazonEC2ReadOnlyAccess. Managed policies are pre-built policies (built either by AWS or by your administrators) that can be attached to IAM users and user groups. When the policy is updated, the changes to the policy are immediately applied to all users and user groups that are attached to the policy.

Next to the AmazonEC2ReadOnlyAccess policy, select the plus sign to show the policy.

A policy defines what actions are allowed or denied for specific AWS resources. This policy grants permission to list and describe information about Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudWatch, and Amazon EC2 Auto Scaling. This ability to view resources but not modify them is ideal for assigning to a support role.

The following is the basic structure of the statements in an IAM policy:

Effect indicates whether to Allow or Deny the permissions.
Action specifies the API calls that can be made against an AWS service (for example, cloudwatch:ListMetrics).
Resource defines the scope of entities covered by the policy rule (for example, a specific Amazon Simple Storage Service [Amazon S3] bucket, EC2 instance, or * which means any resource).
In the left navigation pane, choose User groups.

Choose the S3-Support group.

Choose the Permissions tab.

The S3-Support group has the AmazonS3ReadOnlyAccess policy attached.

Next to the AmazonS3ReadOnlyAccess policy, select the plus sign to show the policy.

This policy has permissions to get and list resources in Amazon S3.

In the left navigation pane, choose User groups.

Choose the EC2-Admin group.

Choose the Permissions tab.

This group is slightly different from the other two. Instead of a managed policy, it has a Customer inline policy, which is a policy assigned to only one user or group. Inline policies are typically used to apply permissions for one-off situations.

Next to the EC2-Admin-Policy policy, select the plus sign to show the policy.

This policy grants permission to view (Describe) information about Amazon EC2 and also the ability to start and stop instances.

SUMMARY OF TASK 2
In this task, you were able to view pre-created users along with the pre-created user groups. You learned about the attached polices to the user groups and what the differences between the user groups and their permissions are.

Under Actions, choose the Show Policy link.

A policy defines what actions are allowed or denied for specific AWS resources. This policy grants permission to list and describe information about Amazon Elastic Compute Cloud (EC2), Elastic Load Balancing (ELB), Amazon CloudWatch, and Amazon EC2 Auto Scaling. This ability to view resources but not modify them is ideal for assigning to a support role.

The following is the basic structure of the statements in an IAM policy:

Effect indicates whether to Allow or Deny the permissions.
Action specifies the API calls that can be made against an AWS service (for example, cloudwatch:ListMetrics).
Resource defines the scope of entities covered by the policy rule (for example, a specific Amazon Simple Storage Service [Amazon S3] bucket, EC2 instance, or * which means any resource).
To close the Show Policy window, choose the 

In the left navigation pane, choose User groups.

Choose the S3-Support group.

The S3-Support group has the AmazonS3ReadOnlyAccess policy attached.

From the Actions menu, choose the Show Policy link.

This policy has permissions to get and list resources in Amazon S3.

To close the Show Policy window, choose the 

In the left navigation pane, choose User groups.

Choose the EC2-Admin group.

This group is slightly different from the other two. Instead of a managed policy, it has a Customer inline policy, which is a policy assigned to only one user or group. Inline policies are typically used to apply permissions for one-off situations.

Under Actions, choose Show Policy to view the policy.

This policy grants permission to view (Describe) information about Amazon EC2 and also the ability to start and stop instances.

At the bottom of the screen, choose Cancel to close the policy.

SUMMARY OF TASK 2
In this task, you were able to view pre-created users along with the pre-created user groups. You learned about the attached polices to the user groups and the differences between the user groups and their permissions.

Business scenario
For the remainder of this lab, you work with these users and user groups to activate permissions supporting the following business scenario:

Your company is growing its use of AWS and is using many EC2 instances and a great deal of Amazon S3 storage. You want to give access to new staff members depending upon their job function:

User	In Group	Permissions
user-1	S3-Support	Read-only access to Amazon S3
user-2	EC2-Support	Read-only access to Amazon EC2
user-3	EC2-Admin	View, start, and stop EC2 instances
Task 3: Adding users to user groups
You have recently hired user-1 into a role where they will provide support for Amazon S3. You add them to the S3-Support group so that they inherit the necessary permissions via the attached AmazonS3ReadOnlyAccess policy.

 You can ignore any not authorized errors that appear during this task. They are caused by your lab account having limited permissions and should not impact your ability to complete the lab.

ADDING USER-1 TO THE S3-SUPPORT GROUP
In the left navigation pane, choose User groups.

Choose the S3-Support group.

Choose the Users tab.

In the Users tab, choose Add users.

In the Add users to S3-Support window, configure the following options:

Select the check box for user-1.
Choose Add Users.
In the Users tab, you see that user-1 has been added to the group.

ADDING USER-2 TO THE EC2-SUPPORT GROUP
You have hired user-2 into a role where they provide support for Amazon EC2.

Using the previous steps in this task, add user-2 to the EC2-Support group.

user-2 should now be part of the EC2-Support group.

ADDING USER-3 TO THE EC2-ADMIN GROUP
You have hired user-3 as your Amazon EC2 administrator to manage your EC2 instances.

Using the previous steps in this task, add user-3 to the EC2-Admin group.

user-3 should now be part of the EC2-Admin group.

In the left navigation pane, choose User groups.

Each group should have a 1 in the Users column for the number of users in each group.

If there is not a 1 beside each group, revisit the previous instructions in this task to confirm that each user is assigned to a group as shown in the table at the beginning of the Business scenario section.

SUMMARY OF TASK 3
In this task, you added all the associated users to the user groups.

Task 4: Sign-in and testing user permissions
In this task, you test the permissions of each IAM user.

In the left navigation pane, choose Dashboard.
The AWS Account section includes a Sign-in URL for IAM users in this account. This link should look similar to the following: https://123456789012.signin.aws.amazon.com/console

You can use this link to sign in to the AWS account that you are currently using.

Copy the Sign-in URL for IAM users in this account to a text editor.

Open a private window using the following instructions for your web browser:

Mozilla Firefox

Choose the menu bars  at the upper-right of the screen.
Choose New Private Window.
Google Chrome

Choose the ellipsis  at the upper-right of the screen.
Choose New Incognito window.
Microsoft Edge

Choose the ellipsis  at the upper-right of the screen.
Choose New InPrivate window.
Microsoft Internet Explorer

Choose the Tools menu option.
Choose InPrivate Browsing.
Paste the Sign-in URL for IAM users in this account into your private window, and press Enter.

You now sign in as user-1, who has been hired as your Amazon S3 storage support staff.

Sign in using the following credentials:

IAM user name: Enter 

user-1
Password: Enter 

Lab-Password1
Choose Sign in.

If you see a dialog prompting you to switch to the new console home, choose Switch to the new Console Home.

From the Services menu, choose S3.

Choose the name of one of your buckets, and browse the contents.

Because your user is part of the S3-Support group in IAM, they have permission to view a list of S3 buckets and their contents.

Now, test whether they have access to Amazon EC2.

From the Services menu, choose EC2.

In the left navigation pane, choose Instances.

You cannot see any instances. Instead, you see a message that says, You are not authorized to perform this operation. This message appears because your user has not been assigned any permissions to use Amazon EC2.

You now sign in as user-2, who has been hired as your Amazon EC2 support person.

Sign user-1 out of the AWS Management Console by following these steps:

At the top of the screen, choose user-1.

Choose Sign out.

An image of user-1 and the Sign Out option.

user-1 is currently signed in, and they are currently in the top section of the console at the user dropdown list. When the user dropdown is chosen, the Sign Out option is then chosen.

Paste the Sign-in URL for IAM users in this account into your private window, and press Enter.

This link should be in your text editor.

Sign in using the following credentials:

IAM user name: Enter 

user-2
Password: Enter 

Lab-Password2
Choose Sign in.

If you see a dialog prompting you to switch to the new console home, choose Switch to the new Console Home.

From the Services menu, choose EC2.

In the left navigation pane, choose Instances.

You are now able to see an EC2 instance because you have read-only permissions. However, you are not be able to make any changes to Amazon EC2 resources.

 If you cannot see an EC2 instance, then your Region may be incorrect. In the upper-right of the screen, choose the Region menu, and select the Region that you noted at the start of the lab (for example, Oregon).

The Region located at the top of the console.

In the upper-right of the screen, you will be able to see the user that is signed in, the Region, and a support dropdown. You can confirm or choose the Region by choosing the dropdown. In this example, the Oregon Region is chosen.

Your EC2 instance should be selected. If it is not, choose it.

From the Instance state dropdown list, choose Stop instance.

In the Stop instance? window, choose Stop.

An error message for stopping instances.

A message with “Error stopping instances” will appear. It explains that you are not authorized to perform the operation with an encoded message.

You receive an error that says, Failed to stop the instance. You are not authorized to perform this operation. This message demonstrates that the policy gives you permission to only view information and does not give you permission to make changes.

At the Stop Instances window, choose Cancel.

Next, check if user-2 can access Amazon S3.

From the Services menu, choose S3.

You receive an You don’t have permissions to list buckets message because user-2 does not have permission to use Amazon S3.

You now sign in as user-3, who has been hired as your Amazon EC2 administrator.

Sign user-2 out of the AWS Management Console by following these steps:

At the top of the screen, choose user-2.

Choose Sign out.

user-2 signing out of the console.

user-2 is currently signed in, and they are currently in the top section of the console at the user dropdown list. When the user dropdown is chosen, the Sign Out option is then chosen.

Paste the Sign-in URL for IAM users in this account into your private window, and press Enter.

If this link is not in your clipboard, retrieve it from the text editor where you pasted it earlier.

Sign in using the following credentials:

IAM user name: Enter 

user-3
Password: Enter 

Lab-Password3
Choose Sign in.

If you see a dialog prompting you to switch to the new console home, choose Switch to the new Console Home.

From the Services menu, choose EC2.

In the left navigation pane, choose Instances.

As an EC2 administrator, you should now have permissions to stop the EC2 instance.

Your EC2 instance should be selected. If it is not, choose  it.

 If you cannot see an EC2 instance, then your Region may be incorrect. In the upper-right of the screen, choose the Region menu, and select the Region that you noted at the start of the lab (for example, Oregon).

From the Instance state dropdown list, choose Stop instance.

In the Stop instance? window, choose Stop.

The instance should enter the Stopping state and will shut down.

Close your private window.

SUMMARY OF TASK 4
In this task, you were able to sign in as all three users. You verified that user-1 was able to view S3 buckets but unable to view EC2 instances. You then signed in as user-2 and verified that they were able to view EC2 instances but unable to perform the stop instance action. user-2 was also unable to view S3 buckets. After signing in as user-3, you were able to view EC2 instances and perform the stop instance action.

Conclusion
 Congratulations! You now have successfully:

Inspected the IAM account password policy
Explored pre-created IAM users and user groups
Inspected IAM policies as applied to the pre-created user groups
Added users to user groups with specific capabilities active
Located and used the IAM sign-in URL
Experimented with the effects of policies on service access

https://awsrestart.labs.awsevents.com/lab/arn%3Aaws%3Alearningcontent%3Aus-east-1%3A470679935125%3Ablueprintversion%2FCUR-TF-100-RSSECY-3%2F279-lab-SF-IAM%3A3.0.0-63135c01/en-US