# Introduction

This repository will host a series of labs/demonstrations showcasing a series of features and capabilities provided by **Red Hat Fuse, Spring Boot, Red Hat AMQ and Red Hat Openshift Container Platform.**

The [Additional References](#testdrive-additional-references) section will provide complementary assets for further reading and complementary details about related subjects.

**Contributions/Suggestions/Issues/Forks are always WELCOME!!**

## Environment

- [JDK 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
- [Apache Maven 3.3+](https://maven.apache.org/)
- [Red Hat Fuse 7.1](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.1/)
- [Red Hat AMQ 7.2](https://access.redhat.com/documentation/en-us/red_hat_amq/7.2/)
- [Red Hat Developer Studio](https://access.redhat.com/documentation/en-us/red_hat_developer_studio/12.9/)

## Labs:

0. [Setup Developer Studio 12.9](#testdrive-step-0)
1. [Configure Maven](#testdrive-step-1)
2. [Create your first Fuse Project and explore Red Hat Developer Studio](#testdrive-step-2)
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

* For additional details regarding the installation process, please refer to [Red Hat Developer Studio Installation](https://access.redhat.com/documentation/en-us/red_hat_developer_studio/12.9/html-single/installation_guide/) and [Installing Red Hat Developer Studio Integration Stack](https://access.redhat.com/documentation/en-us/red_hat_developer_studio_integration_stack/12.0/html-single/installation_guide/) documents.

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

* For additional details regarding *Apache Maven* on **Red Hat Fuse**, please refer to the following document: [Preparing Maven for building Red Hat Fuse](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.1/html-single/getting_started/#Build-GenerateMaven)

### Create your first Fuse Project and explore Red Hat Developer Studio <a name="testdrive-step-2"></a>

* Open **Red Hat Developer Studio**

* Click on: *File -> New -> Fuse Integration Project*

  * *Project Name: Lab02*
  * *Path: default value*
  * *Use default Workspace location: checked*
  * *Click on Finish button*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-projectcreation.png "Lab02 Fuse Project")

* Change to **Fuse Integration Perspective:** *Window -> Perspective -> Open Perspective -> Fuse Integration*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-fuseintgperspective.png "Lab02 Fuse Integration Perspective")

* Click on *Lab02* project in order to expand it and explore all generated files specially: **src/main/resources/spring/camel-context.xml, src/main/java/org/mycompany/Application.java and pom.xml**

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-importantfiles.png "Lab02 Fuse Import Files")

* Click on the *Source* tab leave the *Graphical Editor* to review your **Fuse Route**  implementation using *XML*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-routesource.png "Lab02 Fuse Route Source")

* In order to execute the this route, click on **camel-context.xml** file with the *right mouse button*, select *Run As* and finally *Local Camel context (without tests)*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-runas.png "Lab02 Fuse Run As")

* When invoking *Run As* action, the application is going to be built and if everything went fine, a similar output as follows is expected:

```
[INFO] --- spring-boot-maven-plugin:1.5.4.RELEASE:run (default-cli) @ camel-ose-springboot-xml ---

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::       (v1.5.13.RELEASE)

18:24:27.416 [main] INFO  org.mycompany.Application - Starting Application on skylab with PID 88927 (/Users/vmartine/Documents/REDHAT/SALES/FY19/CLIENTS/SANEPAR/td_fis/workspace/Lab02/target/classes started by vmartine in /Users/vmartine/Documents/REDHAT/SALES/FY19/CLIENTS/SANEPAR/td_fis/workspace/Lab02)
18:24:27.418 [main] INFO  org.mycompany.Application - No active profile set, falling back to default profiles: default
18:24:27.462 [main] INFO  o.s.b.c.e.AnnotationConfigEmbeddedWebApplicationContext - Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@874106b: startup date [Sat Nov 17 18:24:27 BRST 2018]; root of context hierarchy
18:24:27.739 [background-preinit] INFO  o.h.validator.internal.util.Version - HV000001: Hibernate Validator 5.3.5.Final-redhat-2
18:24:27.938 [main] INFO  o.s.b.f.xml.XmlBeanDefinitionReader - Loading XML bean definitions from class path resource [spring/camel-context.xml]
18:24:29.805 [main] INFO  o.s.c.s.PostProcessorRegistrationDelegate$BeanPostProcessorChecker - Bean 'org.apache.camel.spring.boot.CamelAutoConfiguration' of type [org.apache.camel.spring.boot.CamelAutoConfiguration$$EnhancerBySpringCGLIB$$60f459f0] is not eligible for getting processed by all BeanPostProcessors (for example: not eligible for auto-proxying)
18:24:30.222 [main] INFO  o.s.b.c.e.t.TomcatEmbeddedServletContainer - Tomcat initialized with port(s): 8080 (http)
18:24:30.256 [main] INFO  o.a.coyote.http11.Http11NioProtocol - Initializing ProtocolHandler ["http-nio-0.0.0.0-8080"]
18:24:30.263 [main] INFO  o.a.catalina.core.StandardService - Starting service Tomcat
18:24:30.263 [main] INFO  o.a.catalina.core.StandardEngine - Starting Servlet Engine: Apache Tomcat/8.0.36
18:24:30.356 [localhost-startStop-1] INFO  o.a.c.c.C.[Tomcat].[localhost].[/] - Initializing Spring embedded WebApplicationContext
18:24:30.357 [localhost-startStop-1] INFO  o.s.web.context.ContextLoader - Root WebApplicationContext: initialization completed in 2896 ms
18:24:30.607 [localhost-startStop-1] INFO  o.s.b.w.s.ServletRegistrationBean - Mapping servlet: 'dispatcherServlet' to [/]
18:24:30.611 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'metricsFilter' to: [/*]
18:24:30.611 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'characterEncodingFilter' to: [/*]
18:24:30.611 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'hiddenHttpMethodFilter' to: [/*]
18:24:30.611 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'httpPutFormContentFilter' to: [/*]
18:24:30.611 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'requestContextFilter' to: [/*]
18:24:30.611 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'webRequestLoggingFilter' to: [/*]
18:24:30.612 [localhost-startStop-1] INFO  o.s.b.w.s.FilterRegistrationBean - Mapping filter: 'applicationContextIdFilter' to: [/*]
18:24:31.187 [main] INFO  o.s.w.s.m.m.a.RequestMappingHandlerAdapter - Looking for @ControllerAdvice: org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@874106b: startup date [Sat Nov 17 18:24:27 BRST 2018]; root of context hierarchy
18:24:31.303 [main] INFO  o.s.w.s.m.m.a.RequestMappingHandlerMapping - Mapped "{[/error]}" onto public org.springframework.http.ResponseEntity<java.util.Map<java.lang.String, java.lang.Object>> org.springframework.boot.autoconfigure.web.BasicErrorController.error(javax.servlet.http.HttpServletRequest)
18:24:31.306 [main] INFO  o.s.w.s.m.m.a.RequestMappingHandlerMapping - Mapped "{[/error],produces=[text/html]}" onto public org.springframework.web.servlet.ModelAndView org.springframework.boot.autoconfigure.web.BasicErrorController.errorHtml(javax.servlet.http.HttpServletRequest,javax.servlet.http.HttpServletResponse)
18:24:31.404 [main] INFO  o.s.w.s.h.SimpleUrlHandlerMapping - Mapped URL path [/webjars/**] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
18:24:31.405 [main] INFO  o.s.w.s.h.SimpleUrlHandlerMapping - Mapped URL path [/**] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
18:24:31.470 [main] INFO  o.s.w.s.h.SimpleUrlHandlerMapping - Mapped URL path [/**/favicon.ico] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
18:24:31.576 [main] INFO  o.a.c.i.c.DefaultTypeConverter - Type converters loaded (core: 194, classpath: 1)
18:24:32.652 [main] INFO  o.s.j.e.a.AnnotationMBeanExporter - Registering beans for JMX exposure on startup
18:24:32.659 [main] INFO  o.s.b.a.e.jmx.EndpointMBeanExporter - Registering beans for JMX exposure on startup
18:24:32.663 [main] INFO  o.s.b.c.e.AnnotationConfigEmbeddedWebApplicationContext - Refreshing org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@6a387353: startup date [Sat Nov 17 18:24:32 BRST 2018]; parent: org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@874106b
18:24:32.703 [main] INFO  o.s.b.f.s.DefaultListableBeanFactory - Overriding bean definition for bean 'handlerExceptionResolver' with a different definition: replacing [Root bean: class [null]; scope=; abstract=false; lazyInit=false; autowireMode=3; dependencyCheck=0; autowireCandidate=true; primary=false; factoryBeanName=org.springframework.web.servlet.config.annotation.DelegatingWebMvcConfiguration; factoryMethodName=handlerExceptionResolver; initMethodName=null; destroyMethodName=(inferred); defined in org.springframework.web.servlet.config.annotation.DelegatingWebMvcConfiguration] with [Root bean: class [null]; scope=; abstract=false; lazyInit=false; autowireMode=3; dependencyCheck=0; autowireCandidate=true; primary=false; factoryBeanName=endpointWebMvcChildContextConfiguration; factoryMethodName=compositeHandlerExceptionResolver; initMethodName=null; destroyMethodName=(inferred); defined in org.springframework.boot.actuate.autoconfigure.EndpointWebMvcChildContextConfiguration]
18:24:32.762 [main] INFO  o.s.b.c.e.t.TomcatEmbeddedServletContainer - Tomcat initialized with port(s): 8081 (http)
18:24:32.763 [main] INFO  o.a.coyote.http11.Http11NioProtocol - Initializing ProtocolHandler ["http-nio-0.0.0.0-8081"]
18:24:32.763 [main] INFO  o.a.catalina.core.StandardService - Starting service Tomcat
18:24:32.763 [main] INFO  o.a.catalina.core.StandardEngine - Starting Servlet Engine: Apache Tomcat/8.0.36
18:24:32.774 [localhost-startStop-1] INFO  o.a.c.c.C.[Tomcat-1].[localhost].[/] - Initializing Spring embedded WebApplicationContext
18:24:32.774 [localhost-startStop-1] INFO  o.s.web.context.ContextLoader - Root WebApplicationContext: initialization completed in 111 ms
18:24:32.778 [localhost-startStop-1] INFO  o.s.b.w.s.ServletRegistrationBean - Mapping servlet: 'dispatcherServlet' to [/]
18:24:32.836 [main] INFO  o.s.b.a.e.mvc.EndpointHandlerMapping - Mapped "{[/health || /health.json],methods=[GET],produces=[application/vnd.spring-boot.actuator.v1+json || application/json]}" onto public java.lang.Object org.springframework.boot.actuate.endpoint.mvc.HealthMvcEndpoint.invoke(javax.servlet.http.HttpServletRequest,java.security.Principal)
18:24:32.852 [main] INFO  o.s.w.s.m.m.a.RequestMappingHandlerMapping - Mapped "{[/error]}" onto public java.util.Map<java.lang.String, java.lang.Object> org.springframework.boot.actuate.endpoint.mvc.ManagementErrorEndpoint.invoke()
18:24:32.860 [main] INFO  o.s.w.s.h.SimpleUrlHandlerMapping - Mapped URL path [/webjars/**] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
18:24:32.860 [main] INFO  o.s.w.s.h.SimpleUrlHandlerMapping - Mapped URL path [/**] onto handler of type [class org.springframework.web.servlet.resource.ResourceHttpRequestHandler]
18:24:32.873 [main] INFO  o.s.w.s.m.m.a.RequestMappingHandlerAdapter - Looking for @ControllerAdvice: org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@6a387353: startup date [Sat Nov 17 18:24:32 BRST 2018]; parent: org.springframework.boot.context.embedded.AnnotationConfigEmbeddedWebApplicationContext@874106b
18:24:32.917 [main] INFO  o.a.c.spring.boot.RoutesCollector - Loading additional Camel XML routes from: classpath:camel/*.xml
18:24:32.918 [main] INFO  o.a.c.spring.boot.RoutesCollector - Loading additional Camel XML rests from: classpath:camel-rest/*.xml
18:24:32.931 [main] INFO  o.a.camel.spring.SpringCamelContext - Apache Camel 2.21.0.fuse-710018-redhat-00001 (CamelContext: MyCamel) is starting
18:24:32.932 [main] INFO  o.a.c.m.ManagedManagementStrategy - JMX is enabled
18:24:32.932 [main] INFO  o.a.c.m.DefaultManagementAgent - ManagementAgent detected JVM system properties: {org.apache.camel.jmx.createRmiConnector=true}
18:24:33.055 [Camel Thread #2 - Camel Thread #1 - JMXConnector: service:jmx:rmi:///jndi/rmi://skylab:1099/jmxrmi/camel] INFO  o.a.c.m.DefaultManagementAgent - JMX Connector thread started and listening at: service:jmx:rmi:///jndi/rmi://skylab:1099/jmxrmi/camel
18:24:33.205 [main] INFO  o.a.camel.spring.SpringCamelContext - StreamCaching is not in use. If using streams then its recommended to enable stream caching. See more details at http://camel.apache.org/stream-caching.html
18:24:33.234 [main] INFO  o.a.camel.spring.SpringCamelContext - Route: simple-route started and consuming from: timer://foo?period=1000
18:24:33.236 [main] INFO  o.a.camel.spring.SpringCamelContext - Total 1 routes, of which 1 are started
18:24:33.237 [main] INFO  o.a.camel.spring.SpringCamelContext - Apache Camel 2.21.0.fuse-710018-redhat-00001 (CamelContext: MyCamel) started in 0.306 seconds
18:24:33.238 [main] INFO  o.a.coyote.http11.Http11NioProtocol - Starting ProtocolHandler ["http-nio-0.0.0.0-8081"]
18:24:33.253 [main] INFO  o.a.tomcat.util.net.NioSelectorPool - Using a shared selector for servlet write/read
18:24:33.264 [main] INFO  o.s.b.c.e.t.TomcatEmbeddedServletContainer - Tomcat started on port(s): 8081 (http)
18:24:33.269 [main] INFO  o.s.c.s.DefaultLifecycleProcessor - Starting beans in phase 0
18:24:33.277 [main] INFO  o.s.b.a.e.jmx.EndpointMBeanExporter - Located managed bean 'healthEndpoint': registering with JMX server as MBean [org.springframework.boot:type=Endpoint,name=healthEndpoint]
18:24:33.303 [main] INFO  o.a.coyote.http11.Http11NioProtocol - Starting ProtocolHandler ["http-nio-0.0.0.0-8080"]
18:24:33.304 [main] INFO  o.a.tomcat.util.net.NioSelectorPool - Using a shared selector for servlet write/read
18:24:33.305 [main] INFO  o.s.b.c.e.t.TomcatEmbeddedServletContainer - Tomcat started on port(s): 8080 (http)
18:24:33.310 [main] INFO  org.mycompany.Application - Started Application in 6.085 seconds (JVM running for 16.658)
18:24:34.249 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World from camel-context.xml
18:24:35.237 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World from camel-context.xml
18:24:36.240 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World from camel-context.xml
```

* Stop the execution of this **Fuse Route** by clicking on the *Red Button* next to the *Console* tab

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-stoproute.png "Lab02 Stop Fuse Route")

* Enable *Properties* tab by clicking on: *Window -> Show View -> Properties*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-propertiestab.png "Lab02 Properties")

* Click on the *Green Box* with the **Timer Component** and take a closer on the *Properties tab*. Try to review and familiarize yourself with the following components:

  * *Details*
  * *Advanced*
  * *Documentation*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-propertiestab.png "Lab02 Properties Details")

* Click on the *Orange Box* with the **Set Body** component and review both *Details* and *Documentation* from *Properties* tab

* Go back to *Details* and change the **Expression** from **Hello World from camel-context.xml** to **Hello World Fuse Test Drive**

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-helloworldfusetd.png "Lab02 HelloWorld")

* Save the Project: *File -> Save*

![Lab02](https://github.com/vinicius-martinez/fuse7-testdrive/blob/master/images/lab02-saveproject.png "Lab02 SaveProject")

* Try to execute this **Fuse Route** and confirm if the updated *Hello World* message is in place

```
19:36:26.444 [main] INFO  o.s.c.s.DefaultLifecycleProcessor - Starting beans in phase 0
19:36:26.453 [main] INFO  o.s.b.a.e.jmx.EndpointMBeanExporter - Located managed bean 'healthEndpoint': registering with JMX server as MBean [org.springframework.boot:type=Endpoint,name=healthEndpoint]
19:36:26.477 [main] INFO  o.a.coyote.http11.Http11NioProtocol - Starting ProtocolHandler ["http-nio-0.0.0.0-8080"]
19:36:26.477 [main] INFO  o.a.tomcat.util.net.NioSelectorPool - Using a shared selector for servlet write/read
19:36:26.478 [main] INFO  o.s.b.c.e.t.TomcatEmbeddedServletContainer - Tomcat started on port(s): 8080 (http)
19:36:26.482 [main] INFO  org.mycompany.Application - Started Application in 5.572 seconds (JVM running for 15.167)
19:36:27.419 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:28.407 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:29.408 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:30.411 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:31.414 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:32.416 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:33.421 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:34.421 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:35.424 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:36.427 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:37.429 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:38.432 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:39.435 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:40.438 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:41.440 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:42.443 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
19:36:43.446 [Camel (MyCamel) thread #3 - timer://foo] INFO  simple-route - >>> Hello World Fuse Test Drive
```

## Additional References <a name="testdrive-additional-references">
