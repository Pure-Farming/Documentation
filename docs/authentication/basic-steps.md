---

title: Basic Steps
menu_order: 1
post_status: draft
post_excerpt: Basic Steps
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# Basic Steps
All applications need to follow a basic pattern when accessing Pure Farming APIs using OAuth 2.0. Here are the steps: 
- [**Step 1:** Obtain Client ID and Client Secret](#step-1:-obtain-client-id-and-client-secret)
- [**Step 2:** Redirect the User’s browser to the Authorisation Endpoint with the Client ID and Code Challenge](#step-2:-redirect-the-user’s-browser-to-the-authorisation-endpoint-with-the-client-id-and-code-challenge)
- [**Step 3:** Send Authorization Code and Code Verifier](#step-3:-send-authorization-code-and-code-verifier)
- [**Step 4:** Send Access Token to get Data](#step-4:-send-access-token-to-get-data)
- [**Step 5:** Refresh the access token](#step-5:-refresh-the-access-token)

---

## Step 1: Obtain Client ID and Client Secret 
To make Pure Farming OAuth API requests, you are required to generate an “Access Token” and “Code Challenge”. For this, you have to get the Client ID and Client Secret (depending on the client type – as described above) by sending an email to developer-support@purefarming.com. 

**Note:** When you email us, please mention in the email whether you want to use the refresh tokens. It is worth noting that this is an interim measure until such a time as we are able to provide self-service tools to developers. 

---

## Step 2: Redirect the User’s browser to the Authorisation Endpoint with the Client ID and Code Challenge
Your application can only access private data using Pure Farming APIs if it has an access token that grants access to the data or endpoints provided by API. For obtaining the Access Token and Refresh Token, the application should redirect the user’s browser to the Authorization endpoint (https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/auth) with the Client ID and Code Challenge to get the Authorization code. If the user is logged in, they will be redirected to the application with the authorization code. If the user is not logged in, they would need to log in. Once they log in, they will be redirected to the application with the authorization code.  

**Your app needs to send the Client ID and Code Challenge to the following URL:**

https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token 

Values that are required to be passed in as parameters: 

**response_type = code**
**client_id:** Issued when you create your app **scope**: Permissions to request (see below)
**redirect_uri:** The URL on your server to redirect back to
**state:** A unique string to be passed back on completion (optional) (see below)
**code_challenge:** The code challenge your app has generated as described below
**code_challenge_method =** The type of code challenge, can be “S256” or “plain” 

**Redirect URIs**
- All redirect URIs must be https (except for localhost). 
- Custom URL schemes are not supported. 
- Mobile Clients may use a custom URL scheme (e.g. oob://), but it is recommended to use the HTTPS Scheme for registered redirect URIs. 

**Scopes**
Scope parameter is a list of OAuth scopes separated by a space. It indicates the data that your app will be able to access. You should request a minimum scopes requirement for whatever the user is doing at a particular time. 

For example, common scopes are: 

- openid 
- profile 
- email 
- offline_access 

**State** 

The state parameter can be used to avoid forgery attacks. You may pass the unique value to the user you are sending through authorisation. The value will be passed back once the authorisation is completed. 

***Note:** *Users can create Code Challenge by performing SHA256 hash on the code verifier and then by Base64url encoding the hash.* 
```
{
  code_challenge = BASE64URL-ENCODE(SHA256(ASCII(code_verifier))) 
}
```

Once a user has been authenticated (entered their username and password) they will be redirected back to the redirect URL, and all subsequent steps will happen via a back-channel – not visible to the user. 

---

## Step 3: Send Authorization Code and Code Verifier
Once you have received the Authorization Code, you are required to send this code back to the token endpoint: https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token 

with the code verifier and standard OAuth 2.0 parameters. 

You are required to send this Authorization Code along with Code Verifier to get the Access Token and Refresh Token. A Code Verifier is a random string between 43 and 128 characters long. It consists of characters A-Z, a-z, 0-9, and punctuation -._~ (hyphen, period, underscore, and tilde). 

The request body is required to contain the grant type (authorization_code), client_id, code, redirect_uri and code verifier. 

**grant_type** = authorization_code
**client_id** = The client ID of your app
**code** = The authorization code you received in the callback
**redirect_uri** = The same redirect URI that was used when requesting the code
**code_verifier** = The code verifier that you have just created 

```
{
    POST https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token 
    
    Content-Type: application/x-www-form-urlencoded 
    
    grant_type=authorization_code 
    &client_id=zzzzzzzz 
    &code=xxxxxx 
    &redirect_uri=https://myapp.com/redirect 
    &code_verifier=yyyyyyy
}
```

The response from the authorisation server will include: 
- **code:** Temporary code that can only be exchanged once and comes with an expiry time of 5 minutes after its issuance. 
- **state:** If the states didn’t match, the request may have been created by a third party. In this case, you should abort the process. 

**Note:** If somehow the error occurs or the user denies the request, you will be redirected back to redirect_uri with an error parameter. 

The generated token will contain the following parameters.

- **access_token:** The token used to call the API. 
- **Id_token:** The token containing user identity details 
- **Expires_in:** The number of seconds until the access token expires. 
- **token_type: Bearer** 
- **Refresh_token:** The token used to refresh the access token once it has expired (only returned if the offline_access scope is requested). 

**Token Expiry** 

All received tokens come with an associated expiry time. Access Tokens & Refresh Tokens can be exchanged prior to expiry. 

Token expiry times: 
- **id_token:** 5 minutes 
- **access_token:** 30 minutes 
- **refresh_token:** 60 days

Here, the Access token is JSON Web Token (JWT). It can be easily decoded to a JSON object containing information about the user as well as the performed authentication. One of the most useful values is authentication_event_id. It can be used to find out whether the user is connected in the current authorisation flow. 
```
{
    { 
    "nbf": 1589363023, 
    "exp": 1589364823, 
    "iss": "https://identity.purefarming.com", 
    "aud": "https://identity.purefarming.com/resources", 
    "client_id": "91E5715B1199038080D6D0296EBC1648", 
    "sub": "a3a4dbafh3495a808ed7a7b964388f53", 
    "auth_time": 1589361892, 
    "global_session_id": "ac2202575e824af3a181c50fcaa65c3c", 
    "jti": "4e7747cec4ce54d6512b4b0775166c5f", 
    "authentication_event_id": "d0ddcf81-f942-4f4d-b3c7-f98045204db4", 
    "scope": [ 
        "email", 
        "profile", 
        "openid", 
        "offline_access" 
    ] 
    } 
}
```

---

## Step 4: Send Access Token to get Data
Once you get the Access Token and Refresh Token you are required to store both along with associated configuration securely. Once done, you can call the Pure Farming APIs using the Authorization header as follows: **Authorization: Bearer <token>** to get data. 

```
{
    Authorization: Bearer <token> 
}
```

---

## Step 5: Refresh the access token
For security purposes, access tokens are generally valid for a short amount of time. If your application needs access to Pure Farming APIs beyond the lifetime of a single access token, it can obtain a refresh token. A refresh token allows your application to obtain a new access token. When an application requests an initial access token from the Pure Farming authorisation endpoint, it will usually come back with an access token, an identity token and a refresh token, if you request with offline_access scope. 

To obtain a new access token, the application can use the refresh token by making a request to the token endpoint:

```
{
    https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token
}
```

**Refreshing Access & Refresh Tokens**

As discussed earlier, an Access Token expires after 30 minutes. You can refresh the Access Token without user interaction. All you need to do is to use a Refresh Token. For this, request the offline_access.  

***Note:** *Please only request a Refresh Token if there is a requirement for it; and it can be stored securely.*  

For getting a new access token, you need to post to your previously issued refresh token to the token endpoint. 

https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token 

The request body should contain the grant type and refresh token 

- **grant_type** = refresh_token 
- **client_id** = Your client id 
- **refresh_token** = Your refresh token 

```
{
    POST https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token 
    
    Content-Type: application/x-www-form-urlencoded 
    
    grant_type=refresh_token 
    &client_id=zzzzzzz 
    &refresh_token=xxxxxx 
}
```
You will receive a new Access Token and possibly a new Refresh Token in the response. 

***Note:** *Both tokens are required to maintain API access.*  