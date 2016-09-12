# spring-rest-api
Web Service which exposes an interface for client integration. It would query a database that submits a response on SMS URL

# Introduction

The example uses OAuth2 Authorization framework to control access to a resource brookside-server when accessed by a client application.

[OAuth2](https://tools.ietf.org/html/draft-ietf-oauth-v2-31) is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Facebook, GitHub, and Twitter.
It works by delegating user authentication to the service that hosts the user account, and authorizing third-party applications to access the user account.
OAuth 2 provides authorization flows for web and desktop applications, and mobile devices.

# Overview

# Resource Server
Resource Server hosts the resources [our REST API] the client is interested in. Resources are located on /user/.

# Authorization Server
Authorization server is the one responsible for verifying credentials and if credentials are OK, providing the tokens[refresh-token as well as access-token].
It also contains information about registered clients and possible access scopes and grant types.

# Security Configuration
Gluing everything together. Endpoint /oauth/token is used to request a token [access or refresh].
Resource owners [mou,bob] are configured here itself.

# Endpoints and their purpose
Attempt to access resources [REST API] without any authorization [will fail of-course].
GET http://localhost:8080/brookside-spring-example/user/
Ask for tokens[access+refresh] using HTTP POST on /oauth/token, with grant_type=password,and resource owners credentials as req-params.
Additionally, send client credentials in Authorization header.
POST http://localhost:8080/brookside-spring-example/oauth/token?grant_type=password&username=mou&password=mou123

This database example is comprised of the following classes.

* The `UserServiceImpl` illustrates using the [SQL Object Queries](http://jdbi.org/sql_object_api_queries/) and string template
features in JDBI.

* All the SQL statements for use in the `UserService` are located the .....

* `migrations.xml` ....

# Running the Application

* Clone the application into your local repository by running the following git command..

```javascript
$ git clone https://github.com/WilliamMoU/secure-spring-rest-api.git
```

* Navigate into your application by
```javascript
$ cd/secure-spring-rest-api
```

* To package the application run.
```javascript
$  mvn package
```

* You can also recompile and clean the application after making changes by running run.
```javascript
$  mvn clean install
```
* Test the brookside-resource-server application by running the test/java/SpringRestClient.java application.


* To setup the oracle database run......(will look at it later on)

## Running the application
Run it and test it using two different clients.

### Client 1: Postman
Try to access a resource without any auth info, you will get a 401.

### Client 2: RestTemplate based java application
Method sendTokenRequest is used to actually get the tokens. The access-token we got in response is then used with each request.
If required, You can implement the refresh-token flow easily in below SpringRestClient.java has been used as a minimal GUI client
that demonstrates security and role based authorization.


* To hit this url to access the server example.

	http://localhost:8080/brookside-spring-example/user/

* To post data into the application you have use your login credentials in example.

       http://localhost:8080/brookside-spring-example/oauth/token?grant_type=password&username=bill&password=abc123

   Postman screen is shwon below

    ![Alt text](https://github.com/WilliamMoU/secure-spring-rest-api/blob/master/Capture.PNG?raw=true "Optional Title")
