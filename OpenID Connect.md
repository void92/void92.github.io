# OpenID Connect
--
### OAuth
```
Problem: How can I delegate limited authorisation for sharing a resource on one app without sharing my 
credentials to a another third party application ?
Solution : The OAuth 2.0 Authorization Framework [RFC 6749]
```
<img src=/Users/rajeev/Downloads/temp/1.png width=100% hieght=100%>



### OAuth flows

1. **Authorization Code Flow:**
	
	<img src=/Users/rajeev/Downloads/temp/7.png width=100% hieght=80%>
> **Use case:** If the Client is a regular web app executing on a server, then the Authorization Code Flow is the flow you should use
	
2. **Implicit Flow:**	

	<img src=/Users/rajeev/Downloads/temp/8.png width=100% hieght=80%>
> **Use case:** If your SPA doesn't need an Access Token, you can use the Implicit Flow with Form Post.
	
3. **Resource Owner Password Credentials Flow:**
	
	<img src=/Users/rajeev/Downloads/temp/9.png width=100% hieght=80%>
> **Use case:** If the client is absolutely trustworthy  

4. **Client Credentials Flow:**

	<img src=/Users/rajeev/Downloads/temp/11.png width=100% hieght=80%>
> **Use case:** If the party that requires access to resources is a machine. In the case of machine-to-machine authorization, the Client is also the Resource Owner, so no end-user authorization is needed

5. **Refresh Token Flow:**

	<img src=/Users/rajeev/Downloads/temp/10.png width=100% hieght=80%>
> **Use cases:** 
> 
>1. If the Client is a regular web app executing on a server, then the Authorization Code Flow is the flow you should use. Using this the Client can retrieve an Access Token and, optionally, a **Refresh Token**.  
>2. If the Client is a Single-Page App (SPA) and if the Authorization Code Flow with PKCE is used, this flow can return **Refresh Tokens**.
 
	
**Important Note:** You can find request and response structures of authorisation and token endpoints(with required and optional parameters) [here](https://darutk.medium.com/diagrams-and-movies-of-all-the-oauth-2-0-flows-194f3c3ade85)

***Eg:*** <img src=/Users/rajeev/Downloads/temp/12.png width=100% hieght=80%>

**Note:** RFC 6749 (OAuth 2.0) includes the definition of a Web API called “authorization endpoint”. The API requires ***response_type*** as a mandatory request parameter.




Open ID
---
```
Issue: OAuth is specifically designed for authorisation (permissions and scope of permissions not for 
user info validation), but web applications adopted it widely for authentication by implementing few 
custom criterias on top of oAuth. There is no interoperability (No standard way to get the user info). 
Solution: OpenID Connect - a simple identity layer on top of the OAuth 2.0 protocol
```

<img src=/Users/rajeev/Downloads/temp/2.png width=70% hieght=50%>  
<img src=/Users/rajeev/Downloads/temp/5.png width=70% hieght=50%>
***
<img src=/Users/rajeev/Downloads/temp/3.png width=70% hieght=50%>

***
<img src=/Users/rajeev/Downloads/temp/4.png width=100% hieght=50%>
<img src=/Users/rajeev/Downloads/temp/6.png width=70% hieght=50%>

### OpenID Connect Flows
```
In RFC 6749, the value of response_type is either code or token. OpenID Connect has added a new value, 
id_token, and allowed any combination of code, token and id_token. A special value, none, has been 
added, too. As a result, now *response_type* can take any one of the following values:

1. code
2. token
3. id_token
4. id_token token
5. code id_token
6. code token
7. code id_token token
8. none

Note that a request for an ID token has to include openid in the scope request parameter. Especially, 
if openid is not included in scope, the case of response_type=code is regarded as the original 
authorization code flow defined in RFC 6749 and an ID token won't be issued. The same is true 
of the case of response_type=code token, too.
```
**Eg: If response_type=code:**  
 When the value of response_type is code, but if openid is not included in the scope request parameter, the request is just an ***authorization code flow (OAuth flow)*** which is defined in RFC 6749. On the other hand, if openid is included in the scope request parameter, an ID token is issued from the token endpoint in addition to an access token.

if openid is included,

<img src=/Users/rajeev/Downloads/temp/13.webp width=100% hieght=50%>

<img src=/Users/rajeev/Downloads/temp/14.webp width=100% hieght=50%>

**Important Note:** You can find OpenID Connect flows for different OAuth flows [here](https://darutk.medium.com/diagrams-of-all-the-openid-connect-flows-6968e3990660)
