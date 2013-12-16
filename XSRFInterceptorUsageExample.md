# Blackboard's XSRFInterceptor Usage example 

Blackboard's XSRFInterceptor attempts to protect against cross site request forgery (XSRF). 
This is done by using a nonce. The following is a usage example:

1. pom.xml
1. mvc-config.xml
1. UserController.java
1. user.jsp

#pom.xml
```
<dependency>
	<groupId>blackboard.platform</groupId>
	<artifactId>bb-spring-webapi</artifactId>
	<version>9.1.110082.0</version>
</dependency>
```
#mvc-config.xml
```
<mvc:interceptors>
	<bean class="blackboard.platform.spring.web.interceptors.XSRFInterceptor" />
</mvc:interceptors>
```

#UserController.java
```
@Controller
@RequestMapping("/users")
public class UserController {

	@RequestMapping(value = "{userId}", method = RequestMethod.GET)
	@UserAuthorization( "system.plugin.MODIFY" )
	public String get(Model model, @PathVariable String userId){
		model.addAttribute("userId", userId);
		return "user";
	}

	@RequestMapping(value = "{userId}", method = RequestMethod.POST)
	@UserAuthorization( "system.plugin.MODIFY" )
	public String post(Model model, @PathVariable String userId){
		model.addAttribute("userId", userId);
		return "user";
	}
}
```

#user.jsp
```
<%@ page contentType="text/html; charset=utf-8" pageEncoding="utf-8"%>
<%@ taglib prefix="s" uri="http://www.springframework.org/tags" %>
<%@ taglib uri="/bbNG" prefix="bbNG"%>

<s:url var="postUrl" value="/controller/${userId}" />
<!-- 
	nonceId is the value of the method's RequestMapping annotation. 
	e.g., {userId} from @RequestMapping(value = "{userId}", method = RequestMethod.GET)
	
	Otherwise, it will fail the nonce check in XSRFInterceptor
-->
<bbNG:form nonceId="{userId}" 
	method="post" 
	name="authenticationProviderConfig" 
	action="${postUrl}">
	<input type="submit" value="submit" />
</bbNG:form>
```


