# Manual-WebApp-Azure
This is a guide on how to deploy a basic PHP app on Azure using App Service.

## 1. Setup Azure Resources
* Setup a Resource Group named "task1" in the "East US" location.
* Then, set up an App Service. Choose the "Web App + Database" category as this option creates a linked database via a private link to the App Service and also a VNet. Create a MySQL Flexible Server, which is highly managed by Azure.
    * **Azure Web App + Database Service Details:**
        * Resource Group: "task1"
        * Name: "app1-task1"
        * Runtime Stack: "php 8.2"
        * DB Engine: "MySQL Flexible server"
        * Server: "app1-server"
        * Database Name: "app1-database"
        * DB Username: (Your chosen username)
        * DB Password: (Your chosen password)
        * Location: "Canada Central"
        * SKU: "Basic Tier"

## 2. Network Configuration
* **Configuring NSG (Network Security Group):**
    * Name: "nsg-task1"
    * Location: "East US"
    * **Rules:**
        * Except for the inbound and outbound default rules:
            * **Inbound:** Allow HTTP at Port 80, HTTPS at Port 443, and SQL at Port 3306.
            * **Outbound:** Allow SQL at Port 3306.

## 3. App Creation and Deployment
* Fork the basic PHP "Hello World" code in the repository and deploy it on App Service.
* Insert a database connection code into the PHP application and deploy it again.
* Resolve all issues encountered during deployment.
* Install MySQL Workbench to connect to the database to edit records.
* Use SSL Certificates, enforcing SSL, and other credentials to access Azure DB through MySQL Workbench.
* Allow public access to the DB Server at port 3306 for connecting to MySQL Workbench through SSL/TLS (Add the client IP (your own IP) to allowed connections).
* After the database connection to Workbench, add records to the database.
* Edit the code to fetch records and display them on the web app.
* Resolve any bugs and other issues.
* The app should now successfully fetch records and display them on the web app.

## 4. Load Balancing/Scaling
* The scaling option is disabled for the Basic Tier. However, scaling can be done via the "Scale out" tab in the left pane, where you can choose conditions for scaling out up to desired specifications.

## 5. Monitoring and Diagnostics
* Enable Azure monitoring with the option to get metrics in the "Metrics" tab (left pane).
* Create an Action Group resource which sends an email to your email address upon alert triggering.
* Create an alert rule to trigger an alert on 70% CPU consumption metric and link it to the action group.

## 6. Backup and Recovery
* MySQL Flexible Server automatically backs up the database once daily. You can also perform on-demand backups in the "Recovery" tab in the left pane of the DB server.

## 7. Other Resources
* Resources that are automatically created besides the above-mentioned are:
    * Action Groups
    * Managed Identity
    * App Service Plans
    * Private DNS
