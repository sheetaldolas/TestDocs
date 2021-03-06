[Index](./index.md)
/
**Install Apache Oozie**

------

Install Apache Oozie
=====

Apache Oozie is workflow scheduler.

* [Install Oozie RPMs](#install-oozie-rpms)
* [Set Directories and Permissions](#set-directories-and-permissions)
* [Modify Configuration Files](#modify-configuration-files)
* [Copy Configuration Files](#copy-configuration-files)
* [Validate Installation](#validate-installation)


Install Oozie RPMs
----

On Oozie server, install the necessary RPMs.

    yum -y install oozie

Set Directories and Permissions
----

### Create Log Directories

Execute these commands on your Oozie server.

    mkdir -p $OOZIE_LOG_DIR;
    chown -R $OOZIE_USER:$HADOOP_GROUP $OOZIE_LOG_DIR;
    chmod -R 755 $OOZIE_LOG_DIR;

    mkdir -p $OOZIE_PID_DIR;
    chown -R $OOZIE_USER:$HADOOP_GROUP $OOZIE_PID_DIR;
    chmod -R 755 $OOZIE_PID_DIR;

Modify Configuration Files
----

1. Download the Hadoop configuration files from [here](./conf/oozie) to a temporary directory.

2. Modify the following parameters per your environment. Search for **TODO** in the configuration files for the properties to replace.

#### oozie-site.xml

| Parameter         | Example        | Description            |
|-------------------|----------------|-------------------- 
| oozie.base.url    | <code>http://{oozie.full.hostname}:11000/oozie</code> | Enter your Oozie server hostname
| oozie.service.StoreService.jdbc.url | <code>jdbc:derby:/var/db/oozie/${oozie.db.schema.name}-db;create=true</code> | Use value from <code>$OOZIE_DATA_DIR</code>


#### oozie-env.sh

| Parameter         | Example        | Description            |
|-------------------|----------------|---------------------------|
| OOZIE_LOG_DIR     | <code>/var/log/oozie</code> | Use value from <code>$OOZIE_LOG_DIR</code>
| OOZIE_PID_DIR     | <code>/var/run/oozie</code> | Use value from <code>$OOZIE_PID_DIR</code>
| OOZIE_DATA_DIR    | <code>/var/db/oozie</code> | Use value from <Code>$OOZIE_DATA_DIR</code>

Copy Configuration Files
----

On your Oozie server, create the config directory, copy the config files and set the permissions:

    mkdir -p $OOZIE_CONF_DIR ;

    <copy the config files to $OOZIE_CONF_DIR > 

    chown -R $OOZIE_USER:$HADOOP_GROUP $OOZIE_CONF_DIR ;
    chmod -R 755 $OOZIE_CONF_DIR ;


Validate Installation
----

### Start Oozie

1. Run the following command to start the Oozie server.

        /usr/lib/oozie/bin/oozie-start.sh

### Smoke Test Oozie

1. Confirm you can browse to the Oozie server.

        http://{oozie.full.hostname}:11000/oozie

------

[Index](./index.md)
|
Next: [Install Apache Hive and Apache HCatalog](./apache-hive-hcatalog.md)
|
**Install Apache Oozie**
|
Next: [Install Apache HBase and Apache Zookeeper](./apache-hbase-zookeeper.md)