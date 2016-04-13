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
Denial Of Service attacks is when you send a lot of requests to a server using a bot network to either deny 'real' traffic access or to crash the server. Threats using a NoSQL database: There is not something directly similar to SQL injection with a NoSQL database, but there are other security issues - e.g. with MongoDB you dont have a admin password thereby having the database 'exposed' if the communicationport 27017 and 28017 is open on the server.

###3. Explain, at a fundamental level, the technologies involved, and the steps required in initializing a SSL connection between a browser and a server and how to use SSL in a secure way.

- 1: A browser requests a secure page, most commonly known as https://.
- 2: The web server sends back its public key along with its certificate.
- 3: The browser ensures that the certificate is issued by a trusted party, that the certificate is still valid and that the certificate is related to the site contacted.
- 4: The browser uses the public key, to encrypt a random symmetric encryption key and then sends it to the server with the encrypted URL required.
- 5: The web server decrypts the symmetric encryption key using its private key and uses the symmetric key to decrypt the URL and http data.
- 6: The web server sends back the requested html document and http data encrypted with the symmetric key.
- 7: The browser decrypts the http data and html document using the symmetric key and displays the information.

