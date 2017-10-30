# MDG-Sparx-EA-UML-JHipster
MDG integration tool between Sparx Systems Enterprise Architect UML tool and JHipster

- guillaume@umlchannel.com
- www.umlchannel.com/jhipster

# Abstract
 EA UML to JHipster Generator MDG produces JDL (JHipster Domain Language) content in a JL file from UML models maintained in Enterprise Architect. This output can be used in **JHipster** to create the application's entities, including properties and relations. This is an alternative the online JDL-Studio tool by using **Sparx Enterprise Architect** UML modelling tool.
 This project has been initiated and used for a software application project carried by VISEO when JHipster version 2 was available.

 ![Enterprise Architect UML to JHipster integration](http://www.umlchannel.com/images/mdg-jhipster-uml-sparx-ea/mdg-sparx-enterprise-architect-uml-jhipster-jdl-generator.png)

# Compatibility
* The current project is compatible with JHipster 2 and its JDL (JHipster Definition Language)
  * if you use the latest JHipster version, this MDG will work but limited to JHipster 2 definitions
* New JHipster versions (e.g. 4) require setting up a new folder with enhanced definitions
  * additional and modified stereotypes to cater for new properties introduced since JHipster 2 (UML profile update)
  * updated script to generate the appropriate JDL content

# Installation process
* Retrieve the XML file located in folder "JHipster 2\02 MDG XML Installation"
  * Note: when new JHipster versions will be supported, you will need to select the JHipster folder matching your installed version
* Open your EA project in Sparx Enterprise Architect 
* Open EA menu PROJECT > MDG Technology Import (EA 12.1 version), or open ribbon PUBLISH > Technology > Publish > Import MDG Technology (EA 13 version)
* Select the JHipster 2 MDG Technology.xml file (folder location: JHipster 2\02 MDG XML Installation)
* Click on OK to confirm
* The installed MDG should be visible in the Resources view

# Using the MDG
* Open your EA project or the example project available from "JHipster 2\EA UML to JHipster 2 example.EAP"
* Open the existing "JHipster 2 diagram", or create a diagram, select Type JHipster 2 \ JHipster 2
* Use the toolbox to create JHipster entities; "JHipster Entity" stereotyped classes are created.
* You can also add attributes to the class using the toolbox; "JHipster" attributes will be created.
* Define your entities and their properties, and provide values in Tagged Values when applicable:
   * "JHipster Entity" Classes
      * jhipsterDto : select mapstruct for the DTO-entity mapping or none
      * jhipsterPaginate : pagination choice for lists (infinite-scroll, pager, pagination) or none
      * jhipsterService : apply serviceClass to the entity or none
   * "JHipster" attributes
      * jhipsterisRequired : set the value to 1 if the attribute is required
      * jhipsterMin: provides the minimum value (declared as minlength for String attributes, or min for Integer, Long, Float, Double, or BigDecimal attributes)
      * jhipsterMax: provides the maximum value (declared as maxlength for String attributes, or max for Integer, Long, Float, Double, or BigDecimal attributes)
      * jhipsterPattern: provide the pattern value for a String attribute
* Once the model is completed, use the script to generate the JDL content
   * In the EA Project Browser, select the package that contains all your entities
   * Display the scripting view with menu TOOLS > Scripting
   * Open the VISEO EA UML to JHipster Generator group
      * Right click on Generate JHipster 2 JDL > Run Script
      * The JDL content is generated in the System Output, available to copy to a JH file:
      * Right click in the System Output > Copy All to Clipboard
      * Paste the content in a text editor and save your jhipster JH file
      * Below is the result from the example (Test1 & Test2 entities)
		> === EA UML to JHipster Entity Export ===	
		> == More information is available from www.umlchannel.com/jhipster ==	
		> INSTRUCTIONS: copy and paste the following content in a text file, and rename it e.g. as dpl.jh =	
		> entity Test1 {
		>	  prop1 Integer required max(10) min(0),
		>	  prop2 String
		>	  }
		> entity Test2 {
		>	  prop1 Integer required max(10) min(0),
		>	  prop2 String
		>	  }				
		> relationship {
		>	  Test1{test2} to Test2
		>	  }				
		>	  paginate Test1, Test2 with pagination	
		>	  dto Test1, Test2 with mapstruct	
		>	  service Test1, Test2 with serviceClass	
					
* Generate the entities in JHipster by copying the file to your JHipster application’s root folder, and running the following: 
  `jhipster import-jdl my_file.jdl or jhipster-uml my_file.jdl`
 *  More information is available from http://www.jhipster.tech/jdl/

# MDG Sources
- Updating the MDG e.g. stereotypes, script, can be achieved via the EA project located in <github folder>\MDG-Sparx-EA-UML-JHipster\JHipster 2\00 MDG EAP
 - This EA project includes the information to generate a new version of the MDG. 
	- Create the XML file for the UML profile: right click on «profile» JHipster 2 > Advanced > Save Package as UML Profile
	   Filename = <github folder>\MDG-Sparx-EA-UML-JHipster\JHipster 2\01 MDG XML Sources\01-JHipster2-UML-Profile.xml
	- Create the XML file for the Diagram profile: right click on «diagram profile» JHipster 2 > Advanced > Save Package as UML Profile
	   Filename = <github folder>\MDG-Sparx-EA-UML-JHipster\JHipster 2\01 MDG XML Sources\02-JHipster2-Diagram-Profile.xml
	- Create the XML file for the Toolbox profile: right click on «toolbox profile» JHipster 2 > Advanced > Save Package as UML Profile
	   Filename = <github folder>\MDG-Sparx-EA-UML-JHipster\JHipster 2\01 MDG XML Sources\03-JHipster2-Toolbox-Profile.xml
- The MDG can be generated using the MTS file located in JHipster 2 root folder
	- Edit the "MDG Jhipster 2.mts" file and replace <replace with your GitHub folder>
	- Open menu TOOLS > Generate MDG Technology File (EA 12.1 version) and select the "MDG Jhipster 2.mts" file and follow the process to generate the MDG file

