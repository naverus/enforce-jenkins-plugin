# EnForce Jenkins Plugin

This plugin allows you to capture code coverage information from [EnForce gradle plugin](https://github.com/fundacionjala/enforce-gradle-plugin).

The plugin will generate:

* Code coverage percentage.

* A pie chart with amount of test classes whose code coverage percentage is in the ranges defined as: 

  * Danger (0% - 74%)
  * Risk (75% - 79%)
  * Acceptable (80% - 94%)
  * Safe(95% - 100%)

The EnForce jenkins plugin can be downloaded [here](https://bintray.com/artifact/download/fundacionjala/enforce/enforce-jenkins-plugin.hpi).

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
    * The plugin is hosted on the [Bintray repository](https://bintray.com/artifact/download/fundacionjala/enforce/enforce-jenkins-plugin.hpi)
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


