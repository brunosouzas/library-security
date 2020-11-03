# Overview
Security is an essential element of any application, especially in regards to APIs, where you have hundreds or thousands of applications making calls on a daily basis. Every day, new threats and vulnerabilities are created, and every day, companies find themselves racing against the clock to patch them. It's very important to protect your APIs from attacks. Thankfully, while an API manager doesn’t eliminate all threats, it can help protect you against some of the most common ones. And when used as a proxy, it can prevent malicious attacks from hitting your architecture.

Early on, API security consisted of basic authorization, or asking the user for their username and password, which was then forwarded to the API by the software consuming it. This, however, created a huge security risk.

Today Open Authorization (OAUTH) - a token authorization system - is the most common API security measure. Unlike basic authorization, OAuth does not allow API client from accessing the users’ information. Instead it relays the user to a page on the destination server where they can enter their credentials, and then returns to the API client an access token for that user.

The benefit of token-based access is that it may be deleted at any time for any reason - a security breach, misuse or even if the user decides they no longer want that service to have access to their account. Access tokens can also be used to restrict permissions, letting the user decide what the application should be able to do with their information or account.

[API security best practices](https://www.mulesoft.com/webinars/api/security-best-practices) are well defined, no matter how complex or simple the API. Developers need to make sure that their APIs keep users’ data (usernames and passwords) secure, which means creating a layer of separation between their information and the client. Developers should never request login credentials through public APIs, as doing so makes the user’s information vulnerable.

Download a copy of [Undisturbed REST: A Guide to Designing the Perfect API](https://www.mulesoft.com/lp/ebook/api/restbook) to learn about OAuth systems and guidelines for implementing these and other [API security](https://www.mulesoft.com/platform/api) measures into an API project.

### Basic Authentication
Is simple and most widely used authentication mechanism in HTTP based services or APIs. The client sends HTTP requests with the Authorization HTTP header that contains the word Basic word followed by a space and a base64-encoded string username:password .

For example, to authorize as username/password the client would send below HTTP header

```
Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=
```

### Token
The Client ID Enforcement policy restricts access to a protected resource by allowing requests only from registered client applications. The policy ensures that the client credentials sent on each request have been approved to consume the API.

When a client application is registered in Anypoint Platform, a pair of credentials consisting of a client ID and client secret is generated. When the client application requests access to an API, a contract is created between the application and that API. An API that is protected with a Client ID Enforcement policy is accessible only to applications that have an approved contract.

When you apply a Client ID Enforcement policy, access to your API is tracked by reporting the client ID along with the analytics events. You can configure Mule runtime engine (Mule) to encrypt all sensitive information that pertains to policies, contracts, and initialization data.

## How to use
Import the fragment in your API and add in main raml file or in a library:

```
uses:
  security: exchange_modules/[YOUR ORGANIZATION]/library-security/[FRAGMENT VERSION]/security.raml

/resource:
  securedBy: security.token

/resource:
  securedBy: security.basicAuthentication
```