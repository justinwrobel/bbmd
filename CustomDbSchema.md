#Custom B2 Database Schemas
Occasionally, B2s need to store data but regular files are not enough. One of the little 
known features of B2s is to create tables in the blackboard database on installation. 

##Prerequisites
* A running Blackboard Developer VM on [http://localhost:9876](http://localhost:9876). This was covered in the 
[BBDeveloperVMSetupTutorial](BBDeveloperVMSetupTutorial.md)

## Tutorial
We will be building on my previous tutorial [BasicMavenB2Tutorial](BasicMavenB2Tutorial).

1. Download [hello-maven-b2.git](https://github.com/justinwrobel/hello-maven-b2)
   ```
      $ git clone https://github.com/justinwrobel/hello-maven-b2.git
      $ find . ! -path "*.git*" -type f -print
      ./pom.xml
      ./README.md
      ./src/main/webapp/hello.jsp
      ./src/main/webapp/WEB-INF/bb-manifest.xml
      ./src/main/webapp/WEB-INF/web.xml
   ```
   
2. Get ${plugin.name} from plugin.name in the bb-manifest.xml. 
3. Insert the following to src/main/webapp/WEB-INF/${plugin.name}/schema.xml: 
   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <schema name="BBLEARN" xmlns="http://www.blackboard.com/bb-schema"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:schemaLocation="http://www.blackboard.com/bb-schema http://fibbba.blackboard.com/xsd/bb-schema.xsd">
      
      <!-- The table prefix must match the vendor.id in bb-manifest.xml -->
      <table name="jw_hello">
         <column name="id" identity="true" data-type="int" nullable="false" />
         <column name="name" data-type="nvarchar(256)" />
      	
         <primary-key name="jw_hello_pk">
              <columnref name="id" />
         </primary-key>
      </table>
   </schema>
```
4. Finally, run `mvn antrun:run`

The new version hello-maven-b2 will be installed and the schema will be created if needed.

[All the ducks](https://blog.alltheducks.com/post/introduction_to_blackboard_schema_xml/) has a much more thorough write up of all the neat things you can do with schema.xml
