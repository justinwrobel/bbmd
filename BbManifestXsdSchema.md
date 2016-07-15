# bb-manifest.xml Schema


##Link directly to it
```
<?xml version="1.0" encoding="UTF-8"?>
<manifest xmlns="http://www.blackboard.com/bb-manifest-plugin"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.blackboard.com/bb-manifest-plugin http://fibbba.blackboard.com/xsd/bb-manifest-plugin.xsd">
```

## or Download schema and link it in bb-manifest.xml (bad)
1. Download the schema to WEB-INF/bb-manifest-plugin.xsd:
   `wget  https://raw.github.com/justinwrobel/mavenized-bbb-project/master/docs/bb-manifest-plugin.xsd -O WEB-INF/bb-manifest-plugin.xsd`
   NOTE: The link above might be out of date but it can also be found at /usr/local/blackboard/config/internal/bb-manifest-plugin.xsd
   

2. Edit bb-manifest.xml:
```
<?xml version="1.0" encoding="UTF-8"?>
<manifest xmlns="http://www.blackboard.com/bb-manifest-plugin"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.blackboard.com/bb-manifest-plugin ./bb-manifest-plugin.xsd">
```

## Sources & Links
 * https://docs.alltheducks.com/blackboard/bb-manifest-ref.html
 * http://www.edugarage.com/download/attachments/58622224/bb-manifest-plugin.xsd 
 * http://www.edugarage.com/display/BBDN/Your+first+Building+Blocks+project+using+Eclipse
