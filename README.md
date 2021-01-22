# Communication/Transport

KBV Core RESTful API:
- use secure HTTP (HTTPS) as transport layer
- reqeust/response message format is JSON
- the services are addressed via URI
- the request method is POST
- use token based stateless authentication


HTTP Request Header
|Attribute	|Value |Mandatory  |Decsription
| --- | -----------  | --------- | ---------
|Authorization | JSON Web Token (JWT) | true | Authetication token
|Content-Type | application/json | true | Media type of KBV API is JSON
|Accept-Encoding | gzip | false | If the attribute is present and is set to GZIp, KBV 


HTTP compression, otherwise known as content encoding, is a publicly defined way to compress textual content transferred from web servers to browsers. HTTP compression uses public domain compression algorithms, like gzip and compress, to compress XHTML, JavaScript, CSS, and other text files at the server.Sep 
HTTP Request 
Mehtod: POST
Header attributes
