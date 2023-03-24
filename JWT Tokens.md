Pronounced as jAwt (though everyone calls it JWT). JWT Web Tokens are open, industry standard (RFC 1759) method for representing claims securely between two parties. It was introduced in 2010 as a part of OAuth 2.0 specifications.

There are two versions of JWT.

1. JWS (JSON Web Signature) : Introduced in 2010. It provides a way to sign and verify JSON data using digital signatures.
2. JWE (JSON Web Encryption) : Introduced in 2011. Added support for encrypting the JSON Data using public-key encryption.

HTTP is a stateless protocol, i.e. every interaction in HTTP needs to contain everything required for that interaction. Nothing is remembered. No state is saved. 

Thus, let's say if you're a dynamic website (eg: Facebook), now to check the profile, the messages, the list of friends you have and all, to check anything that is only visible to you, you gotta provide the URL + Your Own Credentials while making the request, which makes no sense and makes the work slow.

This problem can be solved by: Session Tokens & JSON Web Tokens.

We'll talk about JSON WEB TOKENS only.

Here, after the authentication, a token which is signed by the server is given to the client which is in JSON format, which is used for the verification of the client. This token can be saved as a cookie in the browser too (You choose how to share the token with server everytime). 

When a user logs in to a system, the server creates a JWT token that contains information about the user, such as their username or email address. This token is then sent back to the user and stored on their device. However, the token doesn't look like a JSON. It looks like this:

![[JWTstring-encoded.png]]

The above token is divided into 3 parts:
1. HEADER
2. PAYLOAD
3. VERIFY SIGNATURE

![[JWTstring-decoded.png]]

Header tells that the 

JWT: https://jwt.io/introduction
Java Brains: https://www.youtube.com/watch?v=soGRyl9ztjI