# Subscribing your team to Kiro - IDE - Docs - Kiro

Source: https://kiro.dev/docs/enterprise/subscribe/

---

Prerequisites
Before you begin, make sure you have the following:
An AWS account - You can create an AWS account if you do not have one already.
AWS permissions - As a Kiro admin, you must have the permissions to access the Kiro console in AWS in order to subscribe and manage Kiro users. The minimum permissions you'll need are described in Policy: Allow administrators to configure Kiro and subscribe users.
AWS IAM Identity Center - You must have an instance of IAM Identity Center set up in your AWS account, with the identities of the users you want to subscribe to Kiro. Your IAM Identity Center instance must be in a supported AWS Region.
Users and groups - You can add users and groups to IAM Identity Center's built-in directory, or to an external identity provider (IdP) that is connected to IAM Identity Center. For more information, see Getting started with IAM Identity Center.
Create the Kiro profile
Sign in to the AWS Management Console.
Switch to the Kiro console.
Make sure you are in your preferred supported AWS Region to create the Kiro profile and store user data.
Choose the Sign up for Kiro button.
Review the contents of the Create Kiro profile dialog box then choose Enable. The Kiro profile is created.
(Optional) Edit the profile with a different name or description as needed in the Settings page.
Subscribe your team to Kiro
Switch to the Kiro console if you're not there yet.
Make sure you're in the AWS Region where you created the Kiro profile.
In the Users & Groups page, choose the Users or Groups tab.
Choose the Add user or Add group button. A dialog box appears where you can select the Kiro subscription tier (Pro, Pro+, Power) with details about each tier.
Choose the desired subscription tier and choose Continue.
In the search bar, search for a group or a user you want to subscribe to the selected tier, or select one from the drop down.
The group or user will auto-populate with what is available in the IAM Identity Center.
Select them and choose Assign. Users or groups are now subscribed.
Have users check their email
If users are not already registered with the AWS IAM Identity Center instance, they will receive an invitation email, where they need to choose a user name and password and supply an multi-factor authentication (MFA) method.
If they are already registered, they will receive an activation email containing the Start URL and Region of your IAM Identity Center instance. They will need to use the Start URL and Region provided in the email to sign in to the Kiro IDE or Kiro CLI.
They may be asked to provide password and MFA for authentication purposes, and if authentication is successful, they will be signed in and instructed to go back to the Kiro IDE or CLI.Page updated: November 16, 2025Onboarding quickstartManage subscriptions