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
 First of all BDRE setup should be installed in your system.Suppose, you had added a new feature in you system.How should give plugin structure of the newly added feature? Let me tell you with an example.
 
 We had developed a plugin named hive data gen for generating bulk data.For this development, we required  data-gen (Plugin Specific dir),rest api, jsp for ui, shell script for deployment and execution, pom.xml(since it is a maven project),
 settings.xml for softwares versions on which this plugin is dependent,plugin.json which stores all the metadata for creating the plugin.
 
 Let me discuss the structure of plugin.json in detail.
 
### Plugin Contains
 - [Plugin Specific dir](###Plugin Specific dir)
 - [md-rest-api](###md-rest-api)
 - [md-ui](###md-ui)
 - [scripts](###Scripts)
 - [workflow-generator](###workflow-generator)
 - [plugin.json](###Plugin Json)
 - [pom.xml](POM)
 - [settings.xml](Settings)
