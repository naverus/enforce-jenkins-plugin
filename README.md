[![Build Status](https://travis-ci.org/rodrigouz/enforce-jenkins-plugin.svg?branch=master)](https://travis-ci.org/rodrigouz/enforce-jenkins-plugin) [![license](http://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat)](https://github.com/fundacionjala/enforce-jenkins-plugin/blob/master/LICENSE)

# EnForce Jenkins Plugin

This plugin allows you to capture code coverage information from [EnForce gradle plugin](https://github.com/fundacionjala/enforce-gradle-plugin).

The plugin will generate:

* Code coverage percentage.

* A pie chart with amount of test classes whose code coverage percentage is in the ranges defined as: 

  * Danger (0% - 74%)
  * Risk (75% - 79%)
  * Acceptable (80% - 94%)
  * Safe(95% - 100%)

The EnForce jenkins plugin can be downloaded [here](https://bintray.com/artifact/download/fundacionjala/enforce/org/fundacionjala/gradle/plugins/enforce/enforce-gradle-plugin/1.0.4/enforce-jenkins-plugin.hpi).

### Code Coverage chart
Displays the code coverage percent and also the coverage status categorized by type(Danger, Risk, Acceptable, Safe)

![Coverage Percent](https://cloud.githubusercontent.com/assets/8682892/9667401/87c2c2f2-5249-11e5-928c-4cb5e922ca10.png)

# Prerequisites

This plugin depends of coverage.json file that is generated by ``` runTest ``` task of [EnForce gradle plugin](https://github.com/fundacionjala/enforce-gradle-plugin).

# Why this plugin?

This plugin is a good fit for generating code coverage information of your Salesforce organization and also you can configure the minimum coverage percentage in your jenkins job.

# Features

* It generates code coverage percentage of your organization.
* It generates a pie chart with amount of test classes whose code coverage percentage is in the ranges that were defined above.
* It changes the build job status to fail according minimum code coverage percentage configured.

# Installation

* Install the plugin in Jenkins.
    * The plugin is hosted on the [Bintray repository](https://bintray.com/artifact/download/fundacionjala/enforce/org/fundacionjala/gradle/plugins/enforce/enforce-gradle-plugin/1.0.4/enforce-jenkins-plugin.hpi)
    * Go to ``Jenkins`` -> ``Manage Plugins`` -> ``Advanced``
    * Search section ``Upload Plugin``
    * Choose ``enforce-jenkins-plugin.hpi`` file   
    * And upload it
    * Ensure you restart Jenkins


# Configuration

* Configure the plugin in Jenkins.
    * Select your job.
    * Go to ``Configure`` -> ``Add post-build action``
    * Search ``Publish EnForce Coverage Report`` option
    * Set ``Coverage JSON file name``   
    * Set ``Minimum coverage percentage``  
  If the code coverage percent is less than the defined ``Minimum coverage percentage`` value, the build is considered unstable.

![Configure the plugin in Jenkins](https://cloud.githubusercontent.com/assets/8682892/9667667/21a97a4a-524b-11e5-9504-873cfc56733d.png)

# Token Macros

The following macros are provided to be integrated to any other plugin(E.G. [Email-ext plugin](https://wiki.jenkins-ci.org/display/JENKINS/Email-ext+plugin) )
that consumes [Token Macro Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Token+Macro+Plugin) infrastructure.

- ENFORCE_COVERAGE_RESULT
- ENFORCE_COVERAGE_STATUS
- ENFORCE_TEST_RESULT

*Usage*

They are able to be used within a expression definition.
E.G. It is a default email content for [Email-ext plugin](https://wiki.jenkins-ci.org/display/JENKINS/Email-ext+plugin)

```java
$PROJECT_NAME - Build # $BUILD_NUMBER - $BUILD_STATUS:

$ENFORCE_COVERAGE_RESULT
$ENFORCE_COVERAGE_STATUS
$ENFORCE_TEST_RESULT

Check console output at $BUILD_URL to view the results.
```
