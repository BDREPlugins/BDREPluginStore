# BDRE Plugin Store
This repo contains pre-configured [BDRE(Bigdata Ready Enterprise)](https://github.com/WiproOpenSourcePractice/openbdre/blob/predevelop/README.md) apps that cater to most common industry usecases.
## Available Plugins
 - Generate Bulk Data
 - Hive Table Migration
 - Monitoring Directory and Ingest
 - Data Quality
 - R Action
 - Spark Action
 - Teradata Ingestion
 - Teradata Query Execution

## How to Develop Plugin
 First of all, BDRE setup should be configured in your system. Suppose, you have developed a new feature in BDRE locally in your system. Now, you want this feature to be used as a plugin by other BDRE users too. 
 
 Suppose we have developed a new plugin named "Hive Data Gen" and we want to add this feature to BDRE as a plugin.
 
 The idea of "Hive Data Gen" plugin is to generate bulk data, which can further be used for testing purpose. For this development, we required  data-gen, ReST api, JSP for User Interface (UI), workflow-generator, Shell Script, pom.xml, settings.xml, plugin.json.
 
 Let me discuss the structure of plugin in detail.
 
## Plugin Module Contains

   [Plugin Specific dir](###plugin-specific-dir)
   [md-rest-api](###md-rest-api)
   [md-ui](###md-ui)
   [scripts](###scripts)
   [workflow-generator](###workflow-generator)
   [plugin.json](###plugin-json)
   [pom.xml](###pom.xml)
   [Settings.xml](#settings.xml)

### Plugin Specific dir
- This is a plugin specific directory which contains all the functions and its dependencies required to run the plugin. 

### md-rest-api
- This contains rest api functions which is responsible to communicate between UI and database. In other way, it works as a controller.

### md-ui
- This module contains all the required Java Server Pages (.jsp) specific to that plugin (if any).

### Scripts
- This module contains all shell scripts required for deployment and execution of the processes relevant plugin.

### workflow-generator
- This module contains classes and functions to generate workflow.

### Plugin Json
- This is the most important module of the pluin which contains all the metadata for plugin installation and uninstallation.

### POM.xml
- Since this is a maven project, pom.xml is must to build the plugin successfully.

# Settings.xml
- This .xml file contains the version of the software required for plugin.
