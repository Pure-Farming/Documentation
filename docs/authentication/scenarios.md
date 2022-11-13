---

title: Scenarios
menu_order: 1
post_status: draft
post_excerpt: Authentication - Scenarios
taxonomy:
    category:
        - root
    post_tag:
        - root

---
# Scenarios
- [Applications authenticated with Pure Farming](#authenticated)
- [Applications not authenticated with Pure Farming](#NotAuthenticated)

---

## Applications authenticated with Pure Farming
**Prerequisite-** Third-party businesses/Third-party application developers need to send an email to info@purefarming.com to get the client ID and client secret. 

!(OAuth_Scenarios_ClientSecret.svg)

The Pure Farming OAuth 2.0 endpoints supports any language or run-time that can make HTTP requests, for example Java, PHP, Python, and ASP.NET. 

Pure Farming APIs use proof key for code exchange (PKCE) authorisation code flow. In order to make Pure Farming API requests, users will need to obtain an access token and refresh token. The application needs to redirect the user to the authorisation endpoint https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/auth with the client ID and code challenge.  

If the user is logged in, they will be redirected to the application with the authorisation code. If they are not logged in, they would need to log in. Once they log in, they will be redirected to the application with the authorisation code. The application needs to return this code in exchange for the access token and refresh token, but while doing so it also needs to send the code value it initially sent when the application submitted an authorisation request to the token endpoint. 

Once the access token and refresh token are received, the application needs to store the access and refresh token and associated configuration securely. Finally, the application can call the Pure Farming APIs using the Authorisation header as follows:
```
{
    Authorization: Bearer <token>
}
```

!(OAuth_Scenarios_App_endpoints.svg)

**Note:** The Pure Farming OAuth 2.0 endpoint also supports applications that are installed on devices like smartphones, tablets, and computers as well as JavaScript applications that run in a browser. The same process mentioned above can be used by installed applications and JavaScript applications for accessing Pure Farming APIs.  

---

## Applications not authenticated with Pure Farming
Pre-requisite– Third-party businesses need to send an email to developer-support@purefarming.com to get the client ID and client secret. 

!(OAuth_Scenarios_NotAuth.svg)

The Pure Farming OAuth 2.0 endpoint also supports applications that are not authenticated with Pure Farming. For instance, if Application X is authenticated with Pure Farming and it is allowing Application Y to access Pure Farming’s APIs on its behalf, Application Y can do so.  

In this case, the user needs to be pre-authenticated with the client ID and secret that the application is going to use to access the data because the refresh token has to be issued to that client. You can either do it manually using Postman or Insomnia or you can create a dummy application that is authenticated with the client ID and secret. 

In order to make Pure Farming API requests, users will need to obtain an access token and refresh token by submitting an authorisation request, which includes the client ID, client secret and a code to the authorisation endpoint with standard OAuth 2.0 parameters and the offline_access scope.  

Once the application makes a request to the authorisation endpoint, it will get a code in return. The application needs to return this code in exchange for the access token and refresh token, but while doing so it also needs to send the code value it initially sent when the application submitted an authorisation request to the authorisation endpoint.  

Once the access token and refresh token are received, the application needs to store the access and refresh token and associated configuration securely. Finally, the application can call the Pure Farming APIs using the Authorisation header as follows:

```
{
    Authorization: Bearer <token>
}
```

!(OAuth_Scenarios_App_endpoints.svg)

The application can use the refresh token to get a new access token by making a request to: https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token 

!(OAuth_Scenarios_NotAuth.svg)

