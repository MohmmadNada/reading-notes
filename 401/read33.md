# Authentication & Production Server

## Introduction to JSON Web Tokens
### What is JSON Web Token (JWT)?
defines a compact and self-contained way for securely transmitting information between parties as a JSON object. Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims from other parties. When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the private key is the one that signed it.

### When should you use JSON Web Tokens?
* Authorization: Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.
* Information Exchange:
### What is the JSON Web Token structure?
consist of three parts separated by dots (.): 
1. Header
   1. type of the token, which is JWT, 
   2. the signing algorithm being used, such as HMAC SHA256 or RSA.
```
   {
  "alg": "HS256",
  "typ": "JWT"
}
```
2. Payload : claims is statements about an entity (typically, the user) and additional data.
   1.  registered 
   2.  public
   3.  private claims. 
3. Signature
   The signature is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.

look like `xxxxx.yyyyy.zzzzz`

### Putting all together
The output is three Base64-URL strings separated by dots that can be easily passed in HTML and HTTP environments, while being more compact when compared to XML-based standards such as SAML.

### How do JSON Web Tokens work?
ypically in the Authorization header using the Bearer schema. The content of the header should look like the following:
`Authorization: Bearer <token>`
This can be, in certain cases, a stateless authorization mechanism. The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources. If the JWT contains the necessary data, the need to query the database for certain operations may be reduced, though this may not always be the case.

### Why should we use JSON Web Tokens?
As JSON is less verbose than XML, when it is encoded its size is also smaller, making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.

Resources: 
* [JSON Web Tokens](https://jwt.io/introduction/)
* [DRF JWT Authentication](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)
* [ Django Runserver Is Not Your Production Server](https://build.vsupalov.com/django-runserver-in-production/)
* [JWT with DRF](https://www.youtube.com/watch?v=Fhcn2qx-4VQ)
* [ Gunicorn](https://gunicorn.org/)
* [Django Migrations Primer](https://realpython.com/django-migrations-a-primer/)