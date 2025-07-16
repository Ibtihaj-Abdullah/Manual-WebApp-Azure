# Manual-WebApp-Azure
This is a guide on how to deploy a basic php app on Azure using App Service

1. Setup Azure Resources <br>
    • Setup Resource-Group named “task1”. Location: “East-US” <br>
    • Than setup an app service. Category Web App + Database as this category creates a linked database via private link to the app service and a vnet as well. Create a MYSQL Flxeible server which is highly managed by Azure. <br>
    • Azure Web App + Database service;  
      • Resource-Group: “task1” 
      • Name: “app1-task1” 
      • Runtime-Stack: “php 8.2” 
      • DB Engine: “MySQL Flexible server” 
      • Server:  ”app1-server” 
      • Database Name: “app1-database” 
      • DB Username: “” 
      • DB Password: “” 
      • Location “Canada Central” 
      • SKU: “Basic Tier” 

2. Network Configuration <br>
    • Configuring NSG: 
    • Name: “nsg-task1 ” 
    • Location: “East-US” 
    • Rules:  <br>
      • Except the inbound and outbound default rules: 
        • Inbound: Allow HTTP at Port 80, HTTPS at Port 443 and SQL at Port 3306   
        • Outbound: Allow SQL at 3306 

3. App Creation and Deployment. <br>
    • Forked the basic php hello world code on github and deployed it on app service.  
    • Inserted a DB connection code in php and deployed it again.  
    • Resolved all the issues.  
    • Installed MySQL Workbench to connect to the DB to edit records. 
    • Used SSL Certificates, enforcing and other credentials to access Azure DB through MySQL WB.  
    • Allowed public access to the DB Server at port 3306 for connecting to the MySQL WB through SSL/TLS (Added the client IP(own IP) to allowed connections).  
    • After DB connection to WB, added records to the DB 
    • Edited the code to fetch records and display them on the web app. 
    • Resolved the bugs and other issues. 
    • The app fetched the records and displayed them on the web app. 
 
4. Load Balancing/Scaling <br>
    • The scaling option was disabled for the basic tier however the scaling can be done via scale out tab in left pane and choose conditions for scaling out up to desired specifications. 

5. Monitoring and Diagnostics <br>
    • Azure monitoring enabled with the option to get metrics in the metrics tab (left pane). 
    • Created an action group resource which sent the email to my email address on alert triggering. 
    • Created the alert rule to trigger alert on 70% CPU consumption metric and linked it to the action group. 

6. Backup and Recovery <br>
    • MySQL Flexible Server allows us to automatically backup database once daily. We can also do backup on demand in recovery tab in left pane in db server. 

7. Other resources
    • Resources which automatically get dreated besides above mentioned are;
      • Action groups, Managed Indentity, App Service Plans, Private DNS 
