# SQL Temporary Access
Customer request was to have a mechanism to provide Azure AD users temporary access to databases, in the case of support requests, application development, etc. The following solution uses a Logic App that is triggered by a new Microsoft Form response, where the user to request access. The Logic App connects to two Azure Automation runbooks to give access to the requested user, then remove access after the specified length of time.



# Deployment Steps
1. Create a Microsoft Form to gather request information
![image](https://user-images.githubusercontent.com/76528226/118903878-a5e26a80-b8e6-11eb-8deb-d18281d6d9aa.png)

2. Create an Azure Automation account with Run As account (service principal)
3. Give Service Principal Azure AD Admin permissions to SQL Server
4. Add runbooks from this repo to Azure Automation account <br />
  [Provide access](https://github.com/Get-AZanushka/SQL-Temp-Roles/blob/main/New-SQLAzureUser.ps1) <br />
  [Remove access](https://github.com/Get-AZanushka/SQL-Temp-Roles/blob/main/Remove-SQLAzureUser.ps1) <br />
6. Create Logic App
### Overview
![image](https://user-images.githubusercontent.com/76528226/118903642-32d8f400-b8e6-11eb-8822-f59a0f8d9dbc.png)
### Trigger using Form
![image](https://user-images.githubusercontent.com/76528226/118905177-391c9f80-b8e9-11eb-9d60-c9276f803029.png)
### Run Azure Automation runbook to provide access
![image](https://user-images.githubusercontent.com/76528226/118905745-5140ee80-b8ea-11eb-9812-14535abf65ad.png)
### Run Azure Automation runbook with specified delay to remove access
![image](https://user-images.githubusercontent.com/76528226/118905654-23f44080-b8ea-11eb-9225-0274c94df619.png)

