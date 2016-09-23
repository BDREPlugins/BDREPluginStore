# BDRE Plugin
BDRE is  enhanced and added with new features. BDRE plugin file is module containing all the files that get copied along with a JSON descriptor describing the plugin installer about the target folders and metadata entries etc.
[A sample descriptor is here](https://github.com/WiproOpenSourcePractice/openbdre/wiki/Plugin-Descriptor-JSON)

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

 - [Plugin Specific dir](#plugin-specific-dir)
 - [md-rest-api](#md-rest-api)
 - [md-ui](#md-ui)
 - [Scripts](#scripts)
 - [workflow-generator](#workflow-generator)
 - [Plugin Descriptor Json](#plugin-json)
 - [POM.xml](#pomxml)
 - [Settings.xml](#settingsxml)

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

### Plugin Descriptor Json

- This is the most important module of the pluin which contains all the metadata for plugin installation and uninstallation.
  Plugin descriptor reader takes the path of a Json descriptor as parameter and de-serializes that into a Java data structure. The structure of the JSON is given below.

#### Following is the high level json schema
•	JSON root
 •	plugin-details //for installed_plugin table
   o	plugin-id //Don’t need unique id and add ts as they can be derived
   o	name
   o	description
   o	version
   o	author
   o	plugin-website
   o	uninstallable
 •	plugin-dependencies
  •	[0]
   o	plugin-id
   o	version
   o	version-level //whether exact or greater version of the parent plugin is needed
  •	[1]
   o	plugin-id
   o	version
   o	version-level
  •	[2]
   o	plugin-id
   o	version
   o	version-level
 o	plugin config
  •	[0]
   o	config group 
   o	key
   o	value 
  •	[1]
   o	config group 
   o	key
   o	value 
  •	[2]
   o	config group 
   o	key
   o	value  
 •	install // During installation this part would be read
  •	fs[0]//All actions under FS tag are for file system actions. 
   o	action //0th element is the action name
   o	sourceLocation // Other ordered elements are parameters to the action
   o	destinationLocation
   o	permission
   o	copy
  •	fs[1]
   o	action 
   o	sourceLocation 
   o	destinationLocation
   o	permission
   o	copy
 •	metadata //All DB actions
  •	insert
   o	tableName
   o	data
    	[0] //These are records to be inserted.
    	[1]
    	[2]
    	[3]
  •	delete
   o	tableName
   o	data
    o	[0] //e.g. col1=’12’ will delete all records from < tableName> where col1=’12’
    o	[1]
  •	update
   o	tableName
   o	data
    	[0]
    	[1]
    	[2]
•	uiwar
   o	location
   o	localizationFile
•	restwar
   o	location




### POM.xml

- Since this is a maven project, pom.xml is must to build the plugin successfully.

### Settings.xml

- This .xml file contains the version of the software required for plugin.
