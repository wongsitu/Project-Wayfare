# React: JWT Authentication

## Learning Objectives (5 min / 0:05)
- Describe JSON web tokens (JWTs)
- Identify parts of JWTs
- Add JWT authentication with Passport to a MERN app

## Framing (10 min / 0:10)
(https://auth0.com/learn/json-web-tokens/)
(https://jwt.io/introduction/)

###What is a JSON Web Token?

[Official definition](https://tools.ietf.org/html/rfc7519): compact, URL-safe means of representing claims to be transferred between two parties. 

In other words: A JSON web token is JSON-formatted data sent between the server and the browser via HTTP requests.

**How JWTs work/are used for authentication**
(compare to session cookies - https://medium.com/@rajaraodv/securing-react-redux-apps-with-jwt-tokens-fcfe81356ea0)
> Diagram: https://cdn-images-1.medium.com/max/1600/1*d6YcPvq7TeU0DTamj629xw.png

1. Client browser makes a request sending user login credentials and password (only has to do this once)
2. Server validates the credentials and sends a JSON response to the client that encodes user login data
3. Client stores this JSON token
4. When the client sends a request to a route that requires authentication, it will send this token to the API to authenticate its authorization for access

With every request sent to the server, we sent the JWT

**Advantages of using JWTs:**
- after inital request from browser, server doesn't need to interact with DB to know who the user is (stored in tokens)
- using JWTs allows you to limit database lookups

**What does a JWT look like?** A string with three parts, each separated by dots (`.`):

    - header
    - payload
    - signature

**Header** is a JSON object consisting of two parts: the type of token (typ) and the hashing algorithm being used on the token (alg).

```
Header example:
{
  "alg": "HS256",
  "typ": "JWT"
}
```
**Payload** is a JSON object containing claims. Claims refer to statements about an entity (e.g. user). There are three different types of claims: public claims, private claims, and registered claims.

```
Payload example:
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
}
```
**Signature** is encoded header and payload signed with a secret. The sender and receiveder are able to decrypt it, but no one else can.

JWTs are self-contained - you have all the information you need to decrypt the token.

**Using JWTs with Passport**
- Passport allows you to store the user object in request instead of in sessions

-Upon the log in request, the server will create a token and pass it to the browser in the HTTP response.

### Additional Resources on JWTs:
- https://medium.com/vandium-software/5-easy-steps-to-understanding-json-web-tokens-jwt-1164c0adfcec
- https://jwt.io/introduction/

## Getting Started (20 min / 0:20)

Outline where JWT will be implemented in front-end/back-end before beginning

**Build out dog walking app ('Walk It Out') with pictures of dogs: React with Express

Then code along: Add in JWT functionality for auth
    - first in back-end (Express)
    - then in front-end (React)

- **Give starter code with Express and Passport in**
- **Give extensive front-end starter code (including sign in and sign)**
- **Give time for students to explore starter code at beginning**: 10 min to explore, 5 min to ask q's
- Think about exploring back-end first using Postman to test paths, then bring front-end in

Back End Code Along
- npm install: passport, passport-jwt, passport-local, json-web-token, bcrypt

### Additional Resources on using JWTs in React apps

- https://medium.com/@rajaraodv/securing-react-redux-apps-with-jwt-tokens-fcfe81356ea0
- https://hptechblogs.com/using-json-web-token-react/
- https://blog.jscrambler.com/implementing-jwt-using-passport/

## Bonus Materials

- [FAQs: Authentication with tokens (vs cookies)](https://auth0.com/blog/ten-things-you-should-know-about-tokens-and-cookies/#token-oauth)
- 