## Authentication
When you create your AWS account, you use the combination of an email address and a password to verify your identity. If a user types in the correct email and password, the system assumes the user is allowed to enter and grants them access. This is the process of authentication.

Authentication simply answers the question, “Are you who you say you are?”

## Authorization
Once you’re authenticated and in your AWS account, you might be curious about what actions you can take. This is where authorization comes in

Authorization is the process of giving users permission to access AWS resources and services. Authorization determines whether a user can perform certain actions, such as read, edit, delete, or create resources. 

Authorization answers the question, “What actions can you perform?” 

## AWS root user
When you first create an AWS account, you begin with a single sign-in identity that has complete access to all AWS services and resources in the account. This identity is called the AWS root user and is accessed by signing in with the email address and password that you used to create the account. 

## AWS root user credentials
The AWS root user has two sets of credentials associated with it. One set of credentials is the email address and password used to create the account. This allows you to access the AWS Management Console.

The second set of credentials is called access keys, which allow you to make programmatic requests from the AWS Command Line Interface (AWS CLI) or AWS API.

Access keys consist of **Access key ID** & **Secret access key**.

Similar to a user name and password combination, you need both the access key ID and secret access key to authenticate your requests via the AWS CLI or AWS API.

## Best practices when working with the AWS root user
The root user has complete access to all AWS services and resources in your account, in addition to your billing and personal information. Due to this, you should securely lock away the credentials associated with the root user and do not use the root user for everyday tasks.

To ensure the safety of the root user, follow these best practices:
- Choose a strong password for the root user
- Never share your root user password or access keys with anyone
- Disable or delete the access keys associated with the root user
- Do not use the root user for administrative tasks or everyday tasks

## Multi-factor authentication (MFA)
When you create an AWS account and first log in to the account, you use single-factor authentication.  Single-factor authentication is the simplest and most common form of authentication. It only requires one authentication method.'

MFA requires two or more authentication methods to verify an identity. MFA pulls from the following three categories of information:
- Something you know, such as a user name and password, or pin number
- Something you have, such as a one-time passcode from a hardware device or mobile app
- Something you are, such as fingerprint or face scanning technology

Using a combination of this information enables systems to provide a layered approach to account access. So even if the first method of authenticated is cracked (e.g. username/password), the second method of authentication, such as a fingerprint, provides another level of security.

## MFA on AWS
If you enable MFA on your root user, you must present a piece of identifying information from both the something you know category and the something you have category. 

The first piece of identifying information the user enters is an email and password combination. The second piece of information is a temporary numeric code provided by an MFA device.

_Enabling MFA on the AWS root user account is an AWS best practice._

## Supported MFA devices
![Screenshot 2022-12-10 at 10 06 11 AM](https://user-images.githubusercontent.com/12791515/206823517-f8a6870f-404a-418c-be83-06bf7aa07c22.png)
