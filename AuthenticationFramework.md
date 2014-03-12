# Blackboard Authentication Framework
Currently, there are two authentication frameworks in blackboard:

 1. Legacy jar based (Bad)
 2. B2 based (Good)


The Legacy jar based framework was the only way to customize authentication until BB9. The installation 
procedure was a nightmare and it had to be completely re-installed on updates. Going forward the B2 
based framework is the recommended way to customize authentication. The support model for the an Authentication B2 is 
simliar to other B2s.


## Authentication B2 Requirements: 

 1. A class that extends AbstractAuthenticationProviderHandler
 2. An <extension/> section in bb-manifest.xml with blackboard.platform.authProviderHandler as the point field.
 3. NOTE: getExtensionId() MUST return extension id contactentated to definition namespace in bb-manifest.xml

e.g., 

**bb-manifest.xml**:

```
<extension-defs>
	<definition namespace="com.test">
		<extension id="testAuthProviderId" 
			point="blackboard.platform.authProviderHandler"
			class="com.test.handler.testAuthProviderClass" 
			singleton="true" />
	</definition>
</extension-defs>
```


**testAuthProviderClass.java**:

```
package com.test.handler;
public class testAuthProviderClass extends AbstractAuthenticationProviderHandler
...
private String namespace = "com.test";
private String extensionId = "testAuthProviderId" ;
getExtensionId(){return namespace+"."+extensionId;}
...
```
 
## Sources
 * [help.blackboard.com's Custom Authentication implementation documentation][1]
 * [Authentication provider presentation][2]
 * [Example LDAP implementation][3]
 * [JavaDoc for AuthenticationProvider][4]
 * [Edugarage forum question][5]
 * [Edugarage forum question][6]
 * [Blackboard's intro to B2 Authentication framework][7]
 * [Legacy Custom Auth][8]
 
 
 [1]: http://help.blackboard.com/en-us/Learn/9.1_SP_10_and_SP_11/Administrator/070_Authentication/Implementing_Authentication/Custom_Authentication_Types
 [2]: http://www.slideshare.net/dan2bit/code-your-own-authentication-provider-for-blackboard-learn
 [3]: https://behind.blackboard.com/System-Administrator/Learn/Downloads/download.aspx?d=1602
 [4]: http://library.blackboard.com/ref/598135ae-501e-46f6-9910-190d7ea0a17c/blackboard/platform/authentication/AuthenticationProvider.html 
 [5]: http://forums.edugarage.com/forums/p/2888/9470.aspx#9470
 [6]: http://forums.edugarage.com/forums/t/3189.aspx
 [7]: https://blackboard.secure.force.com/btbb_articleview?id=kAC7000000000AN
 [8]: https://blackboard.secure.force.com/btbb_articleview?id=kAC70000000000Y

 
 
#Installation Examples
## Example Legacy Authentication Framework install process
 1. Create a jar with a class that extends BaseAuthenticationModule 
 2. Put jar and all dependencies in /usr/local/blackboard/systemlib/
 3. Add jar to classpath to /usr/local/blackboard/apps/collab-server/config/wrapper.conf.bb
    * e.g., wrapper.java.classpath.38=@@bbconfig.basedir@@/systemlib/laureate-authentication.jar
 4. Add jar to classpath to /usr/local/blackboard/system/build/bin/launch-tool.sh
    * e.g., THIRD_PARTY_CP=$THIRD_PARTY_CP:../systemlib/authentication.jar
 5. Add jar to classpath to /usr/local/blackboard/apps/snapshot/config/env.sh.bb
    * e.g., CP=$CP:$BBDIR/systemlib/authentication.jar
 6. Add jar to classpath to /usr/local/blackboard/apps/content-exchange/bin/content-exchange.sh.bb
    * e.g., CP=$CP:$BBDIR/systemlib/authentication.jar
 7. There are probably steps more too.
 8. Oh, you didn't want to configure this jar in the web interface did you? 

## Example B2 Authentication Framework install process
 1. Create a B2
 2. Install B2 
 3. Configure
