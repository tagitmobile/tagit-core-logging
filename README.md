# tagit-core-logging

The repository for sharing the default logging and samples for each version.


# Introduction

As of Mobeix 7.4 onwards, TagitCore is bundled with the Mobeix Logger library. For more information on how the TagitCore Logging System works with the Mobeix Logger, please refer to [Application Logging Configuration - Partner - Product - Development Guidelines - Confluence (tagitmobile.com)](https://edocs1.tagitmobile.com/confluence/pages/viewpage.action?spaceKey=PPDG&title=Application+Logging+Configuration).

# Mobeix Logging Properties

Here is a reference sample properties for configuring the Mobeix Logger. 

```
### Mobeix Logging ###
mxlogger.debug=true
mxlogger.enabled=true
mxlogger.mode=CONSOLEFILE
mxlogger.level=INFO
mxlogger.packagelevel={org.springframework.beans=DEBUG, org.springframework.context=DEBUG, org.springframework.web.servlet.mvc=DEBUG, org.hibernate.id=DEBUG, org.hibernate.SQL=DEBUG, org.hibernate.type.descriptor.sql.BasicBinder=TRACE, com.tagit=DEBUG, com.tagit.commons.core.web.rest.filter=TRACE, com.tagit.commons.core.boot.autoconfigure.env=TRACE, com.mobeix=DEBUG, com.mib.util=INFO, org.hibernate.orm.jdbc.bind=TRACE, org.hibernate.stat=TRACE, org.hibernate.SQL_SLOW=TRACE, org.hibernate.cache=TRACE}
mxlogger.fileconfig=[{packagename=*, filename=<application-name>, logrolltime=DAILY, loglevel=INFO, filesize=100, maxfiles=100}]
mxlogger.location=/layers/mobeix/logs/<application-name>
```

> **Note**
>
> For more information, please refer to [tagitmobile/tagit-core-properties: The repository for sharing the default application properties and samples for each version (github.com)](https://github.com/tagitmobile/tagit-core-properties) and switch to the branch that matches your Mobeix version.


# Logging Files

#### [log4j2-test.xml](/log4j2-test.xml)

The **ONLY** Log4J configuration file that must be present in the classpath for the Tagit Core Logging System to work. Delete all other log4j2 configuration files in the classpath.

> **Shared Tomcat Deployment**
>
> When deploying an application using TagitCore Logging System and Mobeix Logger in a shared Tomcat (more than one WAR in the Tomcat webapps folder), the other WARs must NOT have `log4j-spring-boot.jar` library. Otherwise, there will be a class loading conflict in the way the applications override the Log4J and Spring Logging System.

> **Technology Upgrade Story**
>
> [[DBP-18871] <COMPONENT API/ADM> Mobeix 7.5 Technology Upgrade Template: Ensure mxlogger is working and configurable - JIRA (tagitmobile.com)](https://jira.tagitmobile.com/browse/DBP-18871)

