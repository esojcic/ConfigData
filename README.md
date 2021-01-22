# Communication/Transport

## KBV Core RESTful API
- uses HTTP as transport layer
- reqeust/response message format is JSON
- the services are addressed via URIs
- the request method is POST
- use token based stateless authentication

## External accessibility of the KBV Services
For external service consumers, the KBV services are protected via secured HTTP (HTTPS). However, HTTPS is not a part of the KBV Core API implementation and takes place in the Cloud, when the internal resources are mapped to the external URLs and exposed. 
External consumers access the KBV services using basic authentication. The transition from basic authentication to the KBV token authetication is perfomed in the cloud and ist not a part of the KBV Core API. (TODO: What is the exact name of this mechanism? Are there documentation for this mechanism? Refer here to the documentation).


## KBV Service Request
Structure of HTTP request:

|Part | Attribute	|Value |Mandatory  |Decsription
| --- | --- | -----------  | --------- | ---------
|Header |Authorization | JSON Web Token (JWT) | true | Authetication token
|Header |Content-Type | application/json | true | Media type of KBV API is JSON
|Header |Accept-Encoding | gzip | false | If the attribute is present and is set to GZIp, the response will be compressed
|Body |--- |JSON | Request message in JSON format

HTTP compression, otherwise known as content encoding, is a publicly defined way to compress textual content transferred from web servers to browsers. HTTP compression uses public domain compression algorithms, like gzip and compress, to compress XHTML, JavaScript, CSS, and other text files at the server.Sep 
HTTP Request 
Mehtod: POST
Header attributes
