---

title: Authentication
menu_order: 1
post_status: publish
post_excerpt: Authentication
taxonomy:
    category:
        - root
    post_tag:
        - root

---

# Authentication  
***Pure Farming*** uses the OAuth 2.0 protocol for authentication. This informational guide provides an overview of OAuth 2.0, OAuth 2.0 roles, and the process of accessing *Pure Farming* APIs using OAuth 2.0. 

OAuth 2.0 is an authorisation protocol that enables applications to obtain limited access to resources on an HTTP service. This authorisation standard protects user data by providing access to the data without revealing the user’s identity or credentials. It uses username and password tokens instead.  

**Note:** If you are a non-technical reader and are just interested in knowing more about OAuth 2.0 and how applications can access *Pure Farming’s* APIs using OAuth 2.0, please check out the sections in the menu on the left.

---

## Intended Audience for this Guide
The following are the intended audience for this document:

- **Non-Technical Users:** This guide provides an overview for people who want to use *Pure Farming* APIs and want to know how their developers could access the APIs using OAuth 2.0. 
- **Application developers:** This guide is useful for application developers who want to integrate *Pure Farming* APIs into their applications. 

---

## Advantages of OAuth 2.0
OAuth 2.0 not only provides strong authentication, but also has the ability to share data for users without having to release personal information. Here are some of the major benefits of OAuth 2.0. 

1. **Flexible protocol**– OAuth 2.0 is a very flexible protocol that relies on SSL/TLS (Secure Sockets Layer that ensures data between the web server and browsers remain private) to save user access tokens.  
2. **Easy to implement and provides strong authentication**– In addition to being a flexible protocol, OAuth 2.0 is also easy to implement due to its well-documented nature and easy availability of supporting libraries.
3. **Allows limited access to the user’s data**– OAuth 2.0 uses JWT’s to share data about the authenticated user – primarily their “subject” and any “scopes” that they have been granted access to. If a user has granted permission, some of the “profile” information may be included such as: email, name, etc.  
4. **Usable in a variety of solutions**– The access to the resources is realized via HTTP/HTTPs with the token indicated in the headers. This allows OAuth usage in almost any solution: in mobile and desktop applications, on various web portals, and even in browser plug-ins. 

---

## Sections to this Guide

- [How it Works](/authentication/how-it-works.md)
- [Basic Steps](/authentication/basic-steps.md)
- [Scenarios](/authentication/scenarios.md)
- [Glossary](/authentication/glossary.md)

## Endpoints
**Authorisation:**  
```
https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/auth
```

**Token:**  
```
https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/token
```

**User Info:**  
```
https://signin.purefarming.com/auth/realms/moa/protocol/openid-connect/userinfo
```
