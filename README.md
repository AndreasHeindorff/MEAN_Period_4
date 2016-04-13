# MEAN Period 4

###1. Explain basic security terms like authentication, authorization, confidentiality, integrity, SSL/TLS and provide examples of how you have used them

- Authentication:
Authentication is a confirmation of identity. In computer science, verifying a person's identity is often required to
access to confidential data or systems.

- Authorization:
Authorization refers to access rights related to information and such.
For example: The admin is authorized to delete user accounts, but user accounts are not authorized to do so.

- Confidentiality:
Involves a set of rules or a promise that limits access or places restrictions on certain types of information.

- Integrity:
Maintaining and assuring the accuracy and completeness of data over its entire life-cycle. This means that data cannot
be modified in an unauthorized or undetected manner.

- SSL/TLS:
SSL is a protocol by which enables services that communicate over the Internet securely.
TLS is newer and more secure than SSL.

###2. Explain basic security threads like: Cross Site Scripting (XSS), SQL Injection and whether something similar to SQL injection is possible with NoSQL databases like MongoDB, and DOS-attacks. Explain/demonstrate ways to cope with these problems

- XSS:
Cross Site scripting is when you write scripts directly in a guestbook or other places on a webpage which is then being run when other people visit the page, this gives a lot of possibilities for the scripter to gain access to user-sensitive data.

- SQL Injection: 
Somewhat the same method as XSS, a page where you can write SQL statements directly in a login or a search field, enables the use of the 1=1 method to gain priviliges to do what ever you want via SQL.

- DDOS:
Denial Of Service attacks is when you send a lot of requests to a server using a bot network to either deny 'real' traffic access or to crash the server. Threats using a NoSQL database: There is not something directly similar to SQL injection with a NoSQL database, but there are other security issues. with MongoDB you dont have a admin password thereby having the database 'exposed' if the communicationport 27017 and 28017 is open on the server.

###3. Explain, at a fundamental level, the technologies involved, and the steps required in initializing a SSL connection between a browser and a server and how to use SSL in a secure way.

- 1: A browser requests a secure page, most commonly known as https://.

- 2: The web server sends back its public key along with its certificate.

- 3: The browser ensures that the certificate is issued by a trusted party, that the certificate is still valid and that the certificate is related to the site contacted.

- 4: The browser uses the public key, to encrypt a random symmetric encryption key and then sends it to the server with the encrypted URL required.

- 5: The web server decrypts the symmetric encryption key using its private key and uses the symmetric key to decrypt the URL and http data.

- 6: The web server sends back the requested html document and http data encrypted with the symmetric key.

- 7: The browser decrypts the http data and html document using the symmetric key and displays the information.

###4. Explain and demonstrate ways to protect user passwords on our backends, and why this is necessary.

The reason why this is nessesary is that in general we only have 1 user with a unique name and a password as the schema for our Database. We also don’t want to store the passwords in clear text, so whenever we want to save a user, we salt the password and store this value to our Database. This also means, we have to add a special compare method to compare those passwords, so we never get our hands on the real value of the user’s password. This way we protect the endpoints.

For example see: https://github.com/AndreasHeindorff/MEAN_Period_4/blob/master/routes/users.js

###5. Explain about password hashing, salts and the difference between bcrypt and older (not recommended) algorithms like sha1, md5 etc.

A Hashing is a way to create a hash value by using an algorithm like SHA or MD5, resulting in getting smaller data value, aswell as encrypting a value. These functions are pretty quick and even though its a one way function, the hashed value will always be the same. A hacker can have a Rainbow Table and the decode the value. By adding a salt you use a slower algorithm to create a salted version, this ensures security because, by todays standard, it would take forever to create a Rainbow Table for the different salt values. BCrypt does a hashing and salting and is an easy tool to use in your express. See models/users.js

####6. Explain about JSON Web Tokens (JWT) and why they are very suited for a REST-based API

- JSON Web Token (JWT) is a JSON-based open standard (RFC 7519) for passing claims between parties in web application environment. The
tokens are designed to be compact, URL-safe and usable especially in web browser single sign-on (SSO) context. JWT claims can be typically used to pass identity of authenticated users between an identity provider and a service provider, or any other type of claims as required by business processes. The tokens can also be authenticated and encrypted.

- JSON Web Tokens (JWT) are a more modern approach to authentication. As the web moves to a greater separation between the client and server, JWT provides a wonderful alternative to traditional cookie based authentication models.
JWTs provide a way for clients to authenticate every request without having to maintain a session or repeatedly pass login credentials to the server. In other words JWT is a fantastic and simple way to communicate trusted information across untrusted channels.

- Example of what a JWT looks like: 
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJPbmx5IE1lYW50IGZvciBhIEpXVCBkZW1vIiwiaXNzIjoibGFtQGNwaGJ1c2luZXNzLmRrIiwiaWF0IjoxNDYwNTUyNTQ1LjIxLCJleHAiOjE0NjA1NTI4NDUuMjEsInN1YiI6ImxhbSIsImFkZGl0aW9uYWwiOnsiYSI6IkhlbGxvIENsYXNzIiwiYiI6IkkgY2FuIGJhc2ljYWxseSBhZGQgJ3doYXRldmVyJyBJIGxpa2UgaW4gYSBKV1QifX0.VcEOwcG9CCjvSwgyFAY-9XHPUdw_aYSGDUJstK9PKR0
