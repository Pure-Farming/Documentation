---

title: How It Works
menu_order: 1
post_status: publish
post_excerpt: Authentication - How It Works
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# How does OAuth 2.0 work?

OAuth 2.0 is an authorisation framework for enabling resource sharing in a secured manner through a sequence of steps where the resource owner permits a client application to a certain protected resource for a limited time. OAuth defines four roles, with a clean separation of their concerns. This, together with the shifting of security-related complexity into a dedicated authorisation server, makes it possible to roll out OAuth 2.0 protected applications and services quickly and with consistent security properties.  

- **Resource owner:** The resource owner is the person who is giving access to some portion of their account. The application’s access to the user’s account is limited to the scope of the authorisation granted (e.g., read or write access) 
- **Client:** The client is the system that requires access to the protected resources. Before it may do so, it must be authorised by the user, and the authorisation must be validated by the API.  
- **Resource server:** This is the server that protects the user’s resources and receives access requests from the client. It accepts and validates an Access Token from the client and returns the appropriate resources to it.  
- **Authorisation server:** The authorisation server is the server that receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner.  

![alt text](/_images/How_OAuth_Works-1.png "How OAuth Works")

The resource owner is a role that can change with different credentials. Furthermore, it can not only be an end-user, but it can also be a company. 

Clients can be either public or confidential. There’s a significant difference between the two in OAuth nomenclature. Furthermore, confidential clients can be trusted to store a secret. They are not running on a desktop or distributed through an app store. People cannot reverse engineer them and get the secret key. Generally, they are running in a protected area where end-users can’t access them.  

Generally, public clients are browsers, and mobile applications.  

![alt text](/_images/OAuth_Roles.png "OAuth Roles")

Now that you have an idea of what the OAuth 2.0 roles are, let’s look at a diagram of how they generally interact with each other:  

Here is a more detailed explanation of the steps in the diagram:

![alt text](/_images/OAuth_Interactions-1.png "OAuth Interactions")

- **Application asks permission:** The API (Application Programming Interface) or the application asks for authorisation from the resource by providing the user’s verified identity as proof.  
- **Application requests Access Token:** Once the authorisation has been authenticated, the resource grants an Access Token to the API, without having to divulge usernames or passwords.  
- **Application accesses resource:** Tokens come with access permission for the API. Furthermore, these permissions are called scopes and each token will have an authorised scope for every API. The application gets access to the resource only to the extent the scope allows. 