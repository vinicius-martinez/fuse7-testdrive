# Introduction

This repository will host a series of labs/demonstrations showcasing a series of features and capabilities provided by **Red Hat Fuse, Spring Boot, Red Hat AMQ and Red Hat Openshift Container Platform.**

For additional details, please refer to [Additional References](#testdrive-additional-references) section.

## Environment

- [JDK 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- [Apache Maven 3.3+](https://maven.apache.org/)
- [Red Hat Fuse 7.1](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.1/)
- [Red Hat AMQ 7.2](https://access.redhat.com/documentation/en-us/red_hat_amq/7.2/)
- [Red Hat Developer Studio](https://access.redhat.com/documentation/en-us/red_hat_developer_studio/12.9/)

## Labs:

0. [Setup Developer Studio 12.9](#testdrive-step-0)
1. [Configure Maven](#testdrive-step-1)
2. [Create your first Fuse Project and explore Developer Studio](#testdrive-step-2)
3. [Explore Red Hat Developer Studio](#testdrive-step-3)

### Setup Developer Studio <a name="testdrive-step-0"></a>

* Create an account or LogIn on [Red Hat Developer](https://developers.redhat.com);
* Download [Red Hat Developer Studio 12.9 Installer](https://developers.redhat.com/download-manager/file/devstudio-12.9.0.GA-installer-standalone.jar) from [Red Hat Developers](https://developers.redhat.com/products/devstudio/overview/);

![Dev Studio Download](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab0-devstudio-download.png "Red Hat Developer Studio 12.9")

* Install **Red Hat Developer Studio** via *java -jar*. Example:

```
java -jar devstudio-12.9.0.GA-installer-standalone.jar
```

* When prompted for **Fuse Tooling**, enable it:

![Fuse Tooling](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab0-enablefusetooling.png "Enable Fuse Tooling")

* After finishing the installation process, open **Red Hat Developer Studio**. If everything goes fine, *lab0* is finished.

### Configure Maven <a name="testdrive-step-1"></a>

* In order to explore **Red Hat Fuse**, you need to properly configure *Apache Maven* settings.xml, therefore the following *repositories* should be enabled:

```
Maven central: https://repo1.maven.org/maven2
Red Hat GA repository: https://maven.repository.redhat.com/ga
Red Hat EA repository: https://maven.repository.redhat.com/earlyaccess/all
```

* If you prefer, just create a blank *settings.xml* file and paste the following content within it:

  * **Linux or MacOS: ~/.m2/settings.xml**
  * **Windows: Documents and Settings\\<USER_NAME>\\.m2\\settings.xml**

```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.1.0 http://maven.apache.org/xsd/settings-1.1.0.xsd">
  <profiles>
    <profile>
      <id>default</id>
      <repositories>
        <repository>
          <id>maven-central</id>
          <name>Mave Central Repo</name>
          <url>https://repo1.maven.org/maven2</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </repository>
        <repository>
          <id>redhat-ga</id>
          <name>Red Hat GA</name>
          <url>http://maven.repository.redhat.com/ga/</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </repository>
        <repository>
          <id>redhat-techpreview</id>
          <name>Red Hat TechPreview</name>
          <url>http://maven.repository.redhat.com/techpreview/all/</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </repository>
        <repository>
          <id>redhat-earlyaccess</id>
          <name>Red Hat Early Access</name>
          <url>https://maven.repository.redhat.com/earlyaccess/all</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </repository>
        <repository>
          <id>jboss-ea</id>
          <name>JBoss Early Access Repository</name>
          <url>http://repository.jboss.org/nexus/content/groups/ea</url>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>never</updatePolicy>
          </releases>
        </repository>
      </repositories>
      <pluginRepositories>
        <pluginRepository>
          <id>maven-central</id>
          <name>Mave Central Repo</name>
          <url>https://repo1.maven.org/maven2</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </pluginRepository>
        <pluginRepository>
          <id>redhat-ga</id>
          <name>Red Hat GA</name>
          <url>http://maven.repository.redhat.com/ga/</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </pluginRepository>
        <pluginRepository>
          <id>redhat-techpreview</id>
          <name>Red Hat TechPreview</name>
          <url>http://maven.repository.redhat.com/techpreview/all/</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </pluginRepository>
        <pluginRepository>
          <id>redhat-earlyaccess</id>
          <name>Red Hat Early Access</name>
          <url>https://maven.repository.redhat.com/earlyaccess/all</url>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </releases>
          <snapshots>
            <enabled>true</enabled>
            <updatePolicy>daily</updatePolicy>
          </snapshots>
        </pluginRepository>
        <pluginRepository>
          <id>jboss-ea</id>
          <name>JBoss Early Access Repository</name>
          <url>http://repository.jboss.org/nexus/content/groups/ea</url>
          <snapshots>
            <enabled>false</enabled>
          </snapshots>
          <releases>
            <enabled>true</enabled>
            <updatePolicy>never</updatePolicy>
          </releases>
        </pluginRepository>
      </pluginRepositories>
    </profile>
  </profiles>

  <activeProfiles>
    <activeProfile>default</activeProfile>
  </activeProfiles>

</settings>
```

* In order to double-check if your *maven* settings are properly configured, try to create a **Red Hat Fuse Application** from command-line:

```
mvn org.apache.maven.plugins:maven-archetype-plugin:2.4:generate \
  -DarchetypeCatalog=https://maven.repository.redhat.com/ga/io/fabric8/archetypes/archetypes-catalog/2.2.0.fuse-710017-redhat-00003/archetypes-catalog-2.2.0.fuse-710017-redhat-00003-archetype-catalog.xml \
  -DarchetypeGroupId=org.jboss.fuse.fis.archetypes \
  -DarchetypeArtifactId=spring-boot-camel-xml-archetype \
  -DarchetypeVersion=2.2.0.fuse-710017-redhat-00003
```

* Inform the required attributes to create your *sample project*. Example:

```
Define value for property 'groupId': : com.redhat.fuse
Define value for property 'artifactId': : helloworld
Define value for property 'version':  1.0-SNAPSHOT: : <PRESS ENTER FOR DEFAULT VALUE>
Define value for property 'package':  com.redhat.fuse: : <PRESS ENTER FOR DEFAULT VALUE>
Confirm properties configuration:
groupId: com.redhat.fuse
artifactId: helloworld
version: 1.0-SNAPSHOT
package: com.redhat.fuse
 Y: : Y
```

* Navigate onto *helloworld* project and run *maven clean install*. Example:

```
cd helloworld
mvn clean install
```

* The following output is expected:

```
[INFO] Scanning for projects...
[INFO]
[INFO] ---------------------< com.redhat.fuse:helloworld >---------------------
[INFO] Building Fabric8 :: Quickstarts :: Spring-Boot :: Camel XML 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] --- maven-clean-plugin:2.5:clean (default-clean) @ helloworld ---
...

[INFO] Installing /private/tmp/helloworld/target/helloworld-1.0-SNAPSHOT.jar to /Users/vmartine/.m2/repository/com/redhat/fuse/helloworld/1.0-SNAPSHOT/helloworld-1.0-SNAPSHOT.jar
[INFO] Installing /private/tmp/helloworld/pom.xml to /Users/vmartine/.m2/repository/com/redhat/fuse/helloworld/1.0-SNAPSHOT/helloworld-1.0-SNAPSHOT.pom
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 3.519 s
[INFO] Finished at: 2018-11-16T17:22:05-02:00
[INFO] ------------------------------------------------------------------------
```

### Create your first Fuse Project and explore Developer Studio <a name="testdrive-step-2"></a>

* Open **Red Hat Developer Studio**

* Click on: *File -> New -> Fuse Integration Project*

  * *Project Name: Lab02*
  * *Path: default value*
  * *Use default Workspace location: checked*
  * *Click on Finish button*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-projectcreation.png "Lab02 Fuse Project")

* If needed, change to *Fuse Integration Perspective: Window -> Perspective -> Open Perspective -> Fuse Integration*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-fuseintgperspective.png "Lab02 Fuse Integration Perspective")

* Click on *Lab02* project in order to expand it and explore all generated files specially: **src/main/resources/spring/camel-context.xml and src/main/java/org/mycompany/Application.java**

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-importantfiles.png "Lab02 Fuse Import Files")

* If you prefer, click on *Source* tab leave the *Graphical Editor* to review your **Fuse Route**  implementation using *XML*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-routesource.png "Lab02 Fuse Import Files")

## Additional References <a name="demo-additional-references">
