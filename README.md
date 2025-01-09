AWS Security Hub is a service that gives aggregated visibility into security and compliance status across multiple AWS accounts. Based on those findings, we start to remediate the issues to make the account compliant with the CIS policies. These findings are then sent as events to the lambda function using an event bridge rule which is configured to take custom actions and that will be taken as the event input for the lambda function.
By creating custom actions mapped to specific finding types and by developing a corresponding Lambda function for that custom action, we can achieve targeted, automated remediation for these findings. And it is repeated for all the findings from the Security hub to resolve all the failed compliance issues.
For example, to resolve the Security Group compliance that allows traffic from all sources to SSH into a service that has this service group attached which is in defiance of the compliance of the AWS CIS policy. After setting triggers, run the lambda function and it gives the response that informs the user that the inbound rule for the security group has been removed. The ingress rule has now been revoked, which then makes the security group compliant. And it will be noticed after 12 hours in Security Hub.
Automation of the lambda function can be done using EventBridge rules. This can be added as a trigger to the lambda function. To apply it for more than a single user a role containing permissions to assume the access needs to be deployed to the user accounts in the organization and it can be done using CloudFormation Stacksets.

Table of Contents:
1. Remediation of IAM Password Policies
2. Remediation of IAM Security Group Policies

1. Remediation of IAM Password Policies
# In cis_password__policy_lambda:
Function to remediate policies related to user account's password. For eg: If they are changed in every 90 days and if the access is not 90 days old.

2. Remediation of IAM Security Group Policies
# In cis_security_group_lambda:
This funtion is used for remediation any violation caused by a security group in terms of inbound and outbound rules.