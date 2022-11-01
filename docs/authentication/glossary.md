---

title: Glossary
menu_order: 1
post_status: draft
post_excerpt: Glossary
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# Glossary

| **Authorisation Grant** | Gives the app permission to retrieve an access token on behalf of the end user. OAuth 2.0 defines four specific grant types namely, authorisation code, implicit, resource owner password credentials and client credentials. |
| **Access Token** | An access token is a long string of characters that serves as a credential used to access protected resources. |
| **Protected Resource** | It is the data owned by the resource owner. For example, the user’s contact list, account information or other sensitive data. |
| **Client** | The client is the system that requires access to the protected resources. To access resources, the client must hold the appropriate Access Token. |
| **Resource Owner** | The resource owner is the user who authorizes an application to access their account. The app’s access to the user’s account is limited to the scope of the authorisation granted (e.g. read or write access). |
| **Refresh Token** | A refresh token is a string that is used to get a new access token when an access token expires. |
| **Authorisation Server** | This server receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner. |
| **Resource Server** | A server that protects the user’s resources and receives access requests from the Client. It accepts and validates an Access Token from the Client and returns the appropriate resources to it. |
| **Multi tenant Application** | Multi tenancy is an architecture wherein a single occurrence of a software application serves numerous clients. Furthermore, every client is known as a tenant. Tenants might be enabled to modify a few pieces of the application, for instance, user interface, yet they can’t alter the application’s code. |
| **Proof Key for Code Exchange** | Proof key for code exchange is a security extension to OAuth 2.0 for public clients on mobile devices, specifically designed to prevent interception of the authorisation code by a malicious application that has sneaked into the same device. |