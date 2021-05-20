# SQL Temporary Access
Customer request was to have a mechanism to provide Azure AD users temporary access to databases, in the case of support requests, application development, etc. The following solution uses a Logic App that is triggered by a new Microsoft Form response, where the user to request access. The Logic App connects to two Azure Automation runbooks to give access to the requested user, then remove access after the specified length of time.

![image](https://user-images.githubusercontent.com/76528226/118903642-32d8f400-b8e6-11eb-8822-f59a0f8d9dbc.png)

# Deployment Steps
1. Create a Microsoft Form to gather request information
![image](https://user-images.githubusercontent.com/76528226/118903878-a5e26a80-b8e6-11eb-8deb-d18281d6d9aa.png)

2. Create an Azure Automation account with Run As account (service principal)
3. Give Service Principal Azure AD Admin permissions to SQL Server
4. Add runbooks from this repo to Azure Automation account <br />
  [Provide access](https://github.com/Get-AZanushka/SQL-Temp-Roles/blob/main/New-SQLAzureUser.ps1) <br />
  [Remove access](https://github.com/Get-AZanushka/SQL-Temp-Roles/blob/main/Remove-SQLAzureUser.ps1) <br />
6. Create Logic App using code from this repo
