# kitchensink-jsp: Kitchensink with a JSP (JavaServer Pages) Front End
Author: Elvadas Nono  
Level: Intermediate  
Technologies: JSP, JSTL, CDI, JPA, EJB, JAX-RS, BV  
Summary: The `kitchensink-jsp` quickstart demonstrates how to use JSP, JSTL, CDI, EJB, JPA, and Bean Validation in JBoss EAP.  
Target Product: JBoss EAP  
Source: <https://github.com/jbossas/eap-quickstarts/>  

## What is it?

The `kitchensink-jsp` quickstart is a deployable Maven 3 project and demonstrates how to create a compliant Java EE 7 application using JSP 2.0, EL 2.0, JSTL 1.2, CDI, EJB, JPA, and Bean Validation in Red Hat JBoss Enterprise Application Platform.

This example is based on the [kitchensink](../kitchensink/README.md) quickstart, but recreates the presentation tier using JSP and JSTL instead of JSF features. It reuses all other components from the Member Registration template. It also reuses the persistence unit and some sample persistence and transaction code to help you with database access in enterprise Java.

_Note: This quickstart uses the H2 database included with Red Hat JBoss Enterprise Application Platform 7.1. It is a lightweight, relational example datasource that is used for examples only. It is not robust or scalable, is not supported, and should NOT be used in a production environment!_

_Note: This quickstart uses a `*-ds.xml` datasource configuration file for convenience and ease of database configuration. These files are deprecated in JBoss EAP and should not be used in a production environment. Instead, you should configure the datasource using the Management CLI or Management Console. Datasource configuration is documented in the [Configuration Guide](https://access.redhat.com/documentation/en/red-hat-jboss-enterprise-application-platform/) for Red Hat JBoss Enterprise Application Platform._


## System Requirements

The application this project produces is designed to be run on Red Hat JBoss Enterprise Application Platform 7.1 or later.

All you need to build this project is Java 8.0 (Java SDK 1.8) or later and Maven 3.3.1 or later. See [Configure Maven for JBoss EAP 7.1](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN_JBOSS_EAP7.md#configure-maven-to-build-and-deploy-the-quickstarts) to make sure you are configured correctly for testing the quickstarts.


## Use of EAP7_HOME

In the following instructions, replace `EAP7_HOME` with the actual path to your JBoss EAP installation. The installation path is described in detail here: [Use of EAP7_HOME and JBOSS_HOME Variables](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_OF_EAP7_HOME.md#use-of-eap_home-and-jboss_home-variables).


## Start the Server

1. Open a command prompt and navigate to the root of the JBoss EAP directory.
2. The following shows the command line to start the server:

        For Linux:   EAP7_HOME/bin/standalone.sh
        For Windows: EAP7_HOME\bin\standalone.bat


## Build and Deploy the Quickstart

1. Make sure you have started the JBoss EAP server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        mvn clean install wildfly:deploy

4. This will deploy `target/kitchensink-jsp.war` to the running instance of the server.

## Access the application

The application will be running at the following URL: <http://localhost:8080/kitchensink-jsp/>.


## Server Log: Expected Warnings and Errors

_Note:_ You will see the following warnings in the server log. You can ignore these warnings.

    WFLYJCA0091: -ds.xml file deployments are deprecated. Support may be removed in a future version.

    HHH000431: Unable to determine H2 database version, certain features may not work

## Undeploy the Archive

1. Make sure you have started the JBoss EAP server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn wildfly:undeploy


## Run the Arquillian Tests

This quickstart provides Arquillian tests. By default, these tests are configured to be skipped as Arquillian tests require the use of a container.

1. Make sure you have started the JBoss EAP server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. Type the following command to run the test goal with the following profile activated:

        mvn clean verify -Parq-remote

You can also let Arquillian manage the JBoss EAP server by using the `arq-managed` profile. For more information about how to run the Arquillian tests, see [Run the Arquillian Tests](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/RUN_ARQUILLIAN_TESTS.md#run-the-arquillian-tests).


## Run the Quickstart in Red Hat JBoss Developer Studio or Eclipse

You can also start the server and deploy the quickstarts or run the Arquillian tests from Eclipse using JBoss tools. For general information about how to import a quickstart, add a JBoss EAP server, and build and deploy a quickstart, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_JBDS.md#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts).

You may see the following warnings for the `index.jsp` file when you import this quickstart into JBoss Developer Studio.

        The tag handler class for "c:forEach" (org.apache.taglibs.standard.tag.rt.core.ForEachTag) was not found on the Java Build Path
        The tag handler class for "c:out" (org.apache.taglibs.standard.tag.rt.core.OutTag) was not found on the Java Build Path

You can ignore this warning as it does not impact building or deploying the quickstart in JBoss Developer Studio. See [JBIDE-22175](https://issues.jboss.org/browse/JBIDE-22175) for the latest updates on this issue.


## Debug the Application

If you want to debug the source code of any library in the project, run the following command to pull the source into your local repository. The IDE should then detect it.

        mvn dependency:sources
