---
layout: default
title: Groovy
tagline: Building Groovy Projects
---

The following Groovy versions are available to your build:

 * Groovy 2.0
 * Groovy 2.1

## Java Version

The groovy Virtual Machines are configured to use OpenJDK6. If you would
prefer OpenJDK7 you can add the following command to your build script:

```
sudo update-java-alternatives -s java-1.7.0-openjdk-amd64
```

### Gradle

Gradle 1.3 is installed and available for your build. Most groovy projects
will use the following standard command in their build script:

```
gradle build
```

To support better using the [Gradle Wrapper](http://www.gradle.org/docs/current/userguide/gradle_wrapper.html), some versions of Gradle are pre-installed in the location expected by the wrapper.  The following Gradle versions are available for use from the wrapper:

* Gradle 1.3

Maven and Ant are also installed and available for use in your build script.
