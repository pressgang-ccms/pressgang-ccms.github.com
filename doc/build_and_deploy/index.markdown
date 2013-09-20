---
layout: page
title: "Build and Deploy PressGang CCMS"
date: 2012-09-19 12:04
categories: build deploy docs 
author: Darrin Mison
page_type: doc
---

The PressGangCCMS is made up of two deployable components (the UI and the REST service) and depends on a relational database.  

UI -> Rest -> Database server

Both the UI and RESTful service are deployed as WARs to an application server.  

The database server must already be setup with a database schema with some preloaded configuration data.  A script is provided to do this.

### Preflight Checklist

* Java 6 JDK is installed
* Maven 3 is installed.
* Red Hat JBoss EAP 6 or JBoss AS 7 is installed and setup.
* MySQL5 is installed and setup.


Building and installing PressGangCCMS has the following steps:

* Install application server and database server.
* Add a user for the database, run the database creation script, and grant the user access.
* Configure system properties and a datasource on the application server.
* add Maven repositories 
* Download and build the UI and REST service WARs using Maven.
* Deploy the two WARs built in step 1.



* The `oss.sonatype.org` and `jboss.org` Maven repository have been add to your configuration. added (probably in settings.xml)


---

### Sample `Settings.xml`

{% highlight xml %}
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <profiles>
        <profile>
            <id>oss-public</id>
            <activation>
                <property>
                    <name>!oss.public.off</name>
                </property>
            </activation>
            <repositories>
                <repository>
                    <id>oss-public</id>
                    <name>oss-public</name>
                    <url>https://oss.sonatype.org/content/groups/public/</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>oss-public</id>
                    <name>oss-public</name>
                    <url>https://oss.sonatype.org/content/groups/public/</url>
                    <releases>
                        <enabled>true</enabled>
                    </releases>
                    <snapshots>
                        <enabled>true</enabled>
                    </snapshots>
                </pluginRepository>
            </pluginRepositories>
        </profile>
        <profile>
            <id>jboss-public</id>
            <activation>
                <property>
                    <name>!jboss.public.off</name>
                </property>
            </activation>
            <repositories>
                <repository>
                    <id>jboss-public-repository-group</id>
                    <name>JBoss Public Maven Repository Group</name>
                    <url>https://repository.jboss.org/nexus/content/groups/public/</url>
                    <layout>default</layout>
                    <releases>
                        <updatePolicy>never</updatePolicy>
                    </releases>
                    <snapshots>
                        <updatePolicy>never</updatePolicy>
                    </snapshots>
                </repository>
            </repositories>
            <pluginRepositories>
                <pluginRepository>
                    <id>jboss-public-repository-group</id>
                    <name>JBoss Public Maven Repository Group</name>
                    <url>https://repository.jboss.org/nexus/content/groups/public/</url>
                    <layout>default</layout>
                    <releases>
                        <updatePolicy>never</updatePolicy>
                    </releases>
                    <snapshots>
                        <updatePolicy>never</updatePolicy>
                    </snapshots>
                </pluginRepository>
            </pluginRepositories>
        </profile>
    </profiles>
</settings>
{% endhighlight %}