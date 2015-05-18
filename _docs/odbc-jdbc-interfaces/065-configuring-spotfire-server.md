---
title: "Configuring Tibco Spotfire Server with Drill"
parent: "ODBC/JDBC Interfaces"
---
This document describes how to configure Tibco Spotfire Server (TSS) to integrate with Apache Drill and explore multiple data formats instantly on Hadoop. Users can combine these powerful platforms to rapidly gain analytical access to a wide variety of data types. 


----------


### Step 1: Install and Configure the Drill JDBC Driver 


Drill provides standard JDBC connectivity, making it easy to integrate data exploration capabilities on complex, schema-less data sets. Tibco Spotfire Server (TSS) requires Drill 1.0 or later, which incudes the JDBC driver. The JDBC driver is bundled with the Drill configuration files, and it is recommended that you use the JDBC driver that is shipped with the specific Drill version.

   `<TSS-home-directory>/tomcat/lib`  
   `/usr/local/bin/tibco/tss/6.0.3/tomcat/lib`  
   For example, on a Windows server:  
   `C:\Program Files\apache-tomcat\lib`
   For Linux systems, the hosts file is located here: 
   `/etc/hosts`  
   For Windows systems, the hosts file is located here: 
   `%WINDIR%\system32\drivers\etc\hosts`
----------

### Step 2: Configure the Drill Data Source Template in TSS

The Drill Data Source template can now be configured with the TSS Configuration Tool. The Windows-based TSS Configuration Tool is recommended. If TSS is installed on a Linux system, you also need to install TSS on a small Windows-based system so you can utilize the Configuration Tool. In this case, it is also recommended that you install the Drill JDBC driver on the TSS Windows system.

1. Click **Start > All Programs > TIBCO Spotfire Server > Configure TIBCO Spotfire Server**. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-start.png)
2. Enter the Configuration Tool password that was specified when TSS was initially installed.
8. Add a comment to the updated configuration and click **Finish**. 
9. A response window is displayed to state that the configuration was successfully uploaded to TSS. Click **OK**. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-importconfig.png)
10. Restart TSS to enable it to use the Drill data source template.
   
#### XML Template

Make sure that you enter the correct ZooKeeper node name instead of `<zk-node>`, as well as the correct Drill cluster name instead of `<drill-cluster-name>` in the example below. This is just a template that will appear whenever a data source is configured. The hostnames of ZooKeeper nodes and the Drill cluster name can be found in the `$DRILL_HOME/conf/drill-override.conf` file on any of the Drill nodes in the cluster.
     
    <jdbc-type-settings>
    </jdbc-type-settings>
----------

### Step 3: Configure Drill Data Sources with Tibco Spotfire Desktop 

To configure Drill data sources in TSS, you need to use the Tibco Spotfire Desktop client.

1. Open Tibco Spotfire Desktop. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-client.png)
2. Log into TSS. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-tss.png)
3. Select the deployment area in TSS to be used. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-deployment.png)
4. Click **Tools > Information Designer**. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-infodesigner.png)
5. In the Information Designer, click **New > Data Source**. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-infodesigner2.png)
6. In the Data Source window, enter the name for the data source. Select the Drill Data Source template created in Step 2 as the type. Update the connection URL with the correct hostname of the ZooKeeper node(s) and the Drill cluster name. Note: The Zookeeper node(s) hostname(s) and Drill cluster name can be found in the `$DRILL_HOME/conf/drill-override.conf` file on any of the Drill nodes in the cluster. Enter the username and password used to connect to Drill. When completed, click **Save**. ![drill query flow]({{ site.baseurl }}/docs/img/spotfire-server-connectionURL.png)
7. In the Save As window, verify the name and the folder where you want to save the new data source in TSS. Click **Save** when done. TSS will now validate the information and save the new data source in TSS.


----------

### Step 4: Query and Analyze the Data

After the Drill data source has been configured in the Information Designer, the information elements can be defined. 
2.	The SQL syntax to retrieve the data can be validated by clicking the **SQL** button. Many other operations can be performed in Information Link,  including joins, filters, and so on. See the Tibco Spotfire documentation for details.

