# Communication/Transport

KBV Core RESTful API

| --- | -----------  | --------- | ---------
|Content-Type | application/json | true | Media type of KBV API is JSON
|Accept-Encoding | gzip | false | false | If the attribute present is set to GZIp, KBV 

-  transport layer with secure HTTP (HTTPS) as a transport layer and JSON as message format. 
The KBV API service are addressed via URI:
- Registry URIs: <base-uri>/

 and sopports requests method is POST
 
|Attribute	|Value |Mandatory  |Decsription
| --- | -----------  | --------- | ---------
|Content-Type | application/json | true | Media type of KBV API is JSON
|Accept-Encoding | gzip | false | false | If the attribute present is set to GZIp, KBV 


HTTP compression, otherwise known as content encoding, is a publicly defined way to compress textual content transferred from web servers to browsers. HTTP compression uses public domain compression algorithms, like gzip and compress, to compress XHTML, JavaScript, CSS, and other text files at the server.Sep 
HTTP Request 
Mehtod: POST
Header attributes

|Attribute	| Value |Mandatory  |Decsription
| --- | -----------  | --------- | ---------
|Authorization | JSON Web Token (JWT) | JwtAuthorization deals with rights to access a KBV Service as well as rights with regard to data access based on theJwtAuthorization deals with rights to access a KBV Service as well as rights with regard to data access based on the
|Content-Type | 'application/json' | true | Media type of KBV API is JSON
|Accept-Encoding | 'gzip' | false | false | If the attribute present is and is set 'gzip", KBV compress the response message.

|KbvNoSalesReferenceFoundException	|481
|KbvInvalidPropertyAssignmentException	|482
|KbvInvalidConfigurationException	|483
|KbvTransformationException	|484
|KbvInvalidApiVersionException	|470
|KbvIllegalArgumentException	|471
|KbvDataPoolInconsistencyException	|556

HTTP compression is a capability that can be built into web servers and web clients to improve transfer speed and bandwidth utilization.

If the execution of a KBV service does not terminate normally, an exception object is returned in the error response.
This is indicated by a KBV specific, non-standard HTTP response code <> 200. In this case, a ResponseKbvException response object is created instead of service specific response objects like ResponseGetConfigurationContext or ResponseGetInitialConfiguration.
	
ResponseKbvException is derived from Response and contains the following elements (besides elements common to all responses like apiVersion, businessMessages, serverVersion, ...):
- situation: Operational information about the location where the exception occurred is summarized in the class Situation. Not relevant for KBV clients.
- kbvException: A KbvException object contains an exception object (ExceptionWrapper) and a reason code (EReasonCode). The class KbvException contains several subclasses; each subclass leads to a different HTTP response code. 
	The reason code indicates the specific error situation. A reason code is always returned with the same KbvException subclass and therefore with the same HTTP response code (but several reason codes can be returned with the same exception class).

The following table summarizes the mapping between KBV exception class and HTTP response code:
|API exceptions	|HTTP Status
| --- | ----------- 
|KbvReferenceNotResolvableException	|480
|KbvNoSalesReferenceFoundException	|481
|KbvInvalidPropertyAssignmentException	|482
|KbvInvalidConfigurationException	|483
|KbvTransformationException	|484
|KbvInvalidApiVersionException	|470
|KbvIllegalArgumentException	|471
|KbvDataPoolInconsistencyException	|556
|KbvInconsistentConfigurationException	|474
|KbvSecurityException	|475
|KbvSerializationException |476
|KbvSchemaViolationException	|477
|KbvInadequateRequestException	|478
|KbvServerException	|541
|KbvBasicRequestException	|460
|KbvRequestMessageException	|461
|KbvConfigurationException	|462

The exception hierarchy

![The exception hierarchy](exception_hierarchy.PNG)

ExceptionWrapper contains the following elements:
- cause: the nested exception as known from the Java exception classes. Not relevant for KBV clients.
- className: class name of the causing exception. Not relevant for KBV clients.
- localizedMessage: the message text assigned to the reason code with replaced message parameters in the requested language (if available). Useful for KBV clients e.g. for displaying or logging.
- stackTrace: the stack trace as known from the Java exception classes. Not relevant for KBV clients.

More details to all mentioned classes can be found in the provided JSON schemas (<https://ivk-confluence.dot.daimler.com/display/PS/Core+API>). 
	
The error handling of a KBV client should contain the following elements:
1. Check, if the HTTP response code 200 was returned from KBV. If not, a deserialization of the HTTP response string to KBV client specific will fail. 
It might be enough to just use the localized message in this case in the KBV client application for displaying or logging.
2. More specific error handling actions could depend on the HTTP response code (which is equivalent to the exception classes).
3. The most specific error handling actions depend on the reason code.
	
	
## Appendix:
The following sample error response is returned with HTTP response code 481:
![Sample file](sample_error_response.json)
