# Base POM

[![Build Status](https://travis-ci.org/myunusov/maxur-base.svg?branch=master)](https://travis-ci.org/myunusov/maxur-base)

[![Dependency Status](https://www.versioneye.com/user/projects/5626986c36d0ab0016001030/badge.svg?style=flat)](https://www.versioneye.com/user/projects/5626986c36d0ab0016001030)

[![Issue Stats](http://issuestats.com/github/myunusov/maxur-base/badge/pr)](http://issuestats.com/github/myunusov/maxur-base)

[![Issue Stats](http://issuestats.com/github/myunusov/maxur-base/badge/issue)](http://issuestats.com/github/myunusov/maxur-base)

[![DevOps By Rultor.com](http://www.rultor.com/b/myunusov/maxur-base)](http://www.rultor.com/p/myunusov/maxur-base)

## Overview

Base Maven projects on this artifact and you will get many pre-configuration benefits, 
including up-to-date dependencies, plugins, build extensions, repositories, and more. 

All that you need to do is to define our artifact as a parent of your project:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <parent>
    <groupId>org.maxur</groupId>
    <artifactId>maxur-base</artifactId>
    <version>0.6</version>
  </parent>
  <groupId>your-group-id</groupId>
  <artifactId>your-artifact-id</artifactId>
  <version>1.2.3-SNAPSHOT</version>
  [...]
</project>
```

##Profiles

###gh-pages
            
This profile can be activated manually: 

```
$ mvn clean install -Pgh-pages
```

It configures site deployment to github pages. See http://pages.github.com/
            

**settings.xml**
```xml
<server>
    <id>github</id>
    <password>OAuthToken</password>
</server>
```
            

###gpg

Sign artifacts before installation with GPG. To enable this profile you should have "gpg.keyname" property defined.

[maven-gpg-plugin] (https://maven.apache.org/plugins/maven-gpg-plugin/) used to GPG-sign the artifact before deployment to foreign
repository. GPG keys have to be provided in CI environment, and published beforehand.  
http://www.sonatype.com/people/2010/01/how-to-generate-pgp-signatures-with-maven/

###inspect

This profile can be activated manually:

```
$ mvn clean install -Pinspect
```

It runs a number of checks to make sure the quality of the build is acceptable. 

These plugins are used at the moment to control quality and prevent errors

[maven-duplicate-finder-plugin] (https://github.com/basepom/duplicate-finder-maven-plugin) is a filter of duplicate classes and resources in classpath. 
It helps to identify dependencies that are not used, or the ones that are used but not defined.


[qulice-maven-plugin] (http://www.qulice.com/qulice-maven-plugin/) is a compound static analysis tools that aggregates
 
  * Checkstyle 
  * PMD 
  * FindBugs 
  * CodeNarc (for Groovy code) 
  * a few other plugins in one bucket. 
  
It is expected by default that your **LICENSE.txt** is located in a root directory of every module.

All plugins are bound to the *verify* Maven phase. 
All executions are named *maxur-check*.

###site

The profile builds site for production environment.           

###sonar

The profile is activated automatically when you have a **sonar.properties** file in a root directory.

For example
```
#Sonar

sonar.sourceEncoding = UTF-8
sonar.language = java

sonar.host.url = http://192.168.1.1:9000
sonar.jdbc.url = jdbc:postgresql://192.168.1.1:5432/sonar
sonar.jdbc.driverClassName = org.postgresql.Driver
sonar.jdbc.username = sonar
sonar.jdbc.password = sonar

sonar.forceAnalysis = true

sonar.artifact.path=
```

It configures [sonar-maven-plugin] (http://docs.sonarqube.org/display/SONAR/Analyzing+with+Maven).

###sonatype
            
The profile deploys all artifacts to oss.sonatype.org repository .
It also skips default deployment plugin.
            
##Implicit Profiles

###clover
The profile is activated automatically when you have a **clover.license** file in a root directory.

It configures [maven-clover2-plugin] (https://docs.atlassian.com/maven-clover2-plugin/2.3.1/) for check and report tasks.


###dep-junit
            
Enable unit testing. The profile is activated when you have **src/test/java directory** in the project.
These artifacts are automatically added to the list of dependencies (in test scope, of course):

 * [junit:junit] (http://junit.org/): unit testing framework
 * [org.assertj:assertj-core] (http://joel-costigliola.github.io/assertj/): assertion framework
 * [org.jmockit:jmockit] (http://jmockit.org/): mocking framework
            
###dep-log4j
          
Enable [LOG4J] (http://logging.apache.org/log4j/) for logging and [SLF4J] (http://www.slf4j.org/) binding. The profile is activated when you have **src/test/resources/log4j.properties**.
            
###dep-logback

Enable [logback] (http://logback.qos.ch/) for logging and [SLF4J] (http://www.slf4j.org/) binding. The profile is activated when you have **src/test/resources/logback.xml**.

## Development documentation 

http://myunusov.github.io/maxur-base/