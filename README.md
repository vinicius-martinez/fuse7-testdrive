# Introduction

This repository will host a series of labs/demonstrations showcasing a series of features and capabilities provided by JBoss Fuse.

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
2. [Installing AMQ-7.2 Broker](#testdrive-step-1)

### Setup Developer Studio <a name="testdrive-step-0"></a>

* Create an account or LogIn on [Red Hat Developer](https://developers.redhat.com)
* Download [Red Hat Developer Studio 12.9 Installer](https://developers.redhat.com/download-manager/file/devstudio-12.9.0.GA-installer-standalone.jar) from [Red Hat Developers](https://developers.redhat.com/products/devstudio/overview/);

![Dev Studio Download](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab0-devstudio-download.png "Red Hat Developer Studio 12.9")

* Install **Red Hat Developer Studio** via *java -jar*. Example:

```
java -jar devstudio-12.9.0.GA-installer-standalone.jar
```

* When prompted for **Fuse Tooling**, enable it:

![Fuse Tooling](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab0-enablefusetooling.png "Enable Fuse Tooling")

* After finishing the installation process, open **Red Hat Developer Studio**. If everything goes fine, *lab0* is sucessfully finished.

### Configure Maven <a name="testdrive-step-1"></a>

* In order to explore **Red Hat Fuse**, you need to properly configure *Apache Maven* settings.xml, therefore the following *repositories* should be enabled:

```
Maven central: https://repo1.maven.org/maven2
Red Hat GA repository: https://maven.repository.redhat.com/ga
Red Hat EA repository: https://maven.repository.redhat.com/earlyaccess/all
```

* If you prefer, just create a blank *settings.xml* file and place it properly depending on your platform:

  * **Linux or MacOS: ~/.m2/settings.xml (on Linux or macOS)**
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

## Additional References <a name="demo-additional-references">
