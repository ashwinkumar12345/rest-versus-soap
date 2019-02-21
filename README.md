# Comparing REST and SOAP Web Services

To fully understand the difference between REST and SOAP, it is important to understand what an API is and how it works, how to use HTTP and perform REST and SOAP operations.

> ## Contents

**[API Overview](#overview)**<br>
**[Understanding APIs](#UnderstandingAPIs)**<br>
**[Interfacing with Ethereum](#UnderstandingHTTP)**<br>
**[Understanding HTTP](#UnderstandingSOAP)**<br>
**[Understanding SOAP](#UnderstandingREST)**<br>
**[Understanding REST](#RESTversusSOAP)**<br>
**[REST versus SOAP](#RESTversusSOAP)**<br>

<a name="overview"></a>
> ## API Overview

API is an acronym that stands for application programming interface.
 - Application (A) is a piece of software code that performs a task
 - Program (P) executes the task within the application
 - Interface (I) is a place where you can tell the program to run within that application

**Simple APIs**

A simple API is where you can access the interface of the application using a browser or mobile app. 

For example, the Google homepage is an interface through which you can tell the Google application to run a program to perform a search and provide you back with a web page of the results.

**Complex APIs**

A complex API is where you have to access the interface at the server location to run the program.  

For example, to use the Google Translation API you have to access the interface on the Google translation server and run the translation program on that server.

In general, the term API refers to Complex APIs.

Accessing the interface where the software is located is cost efficient for the software vendor because they do not have to build a web or mobile app for you to interact with that software.

You also have the flexibility to interface with that software using any method you choose. 

<a name="UnderstandingAPIs"></a>
> ## Understanding APIs

An API transaction workflow is as follows:

1. A request is made for a task to be performed
2. A program is run to complete that request
3. The program sends back a response with the results
 
 If the API request and response are sent over the internet, then the API is called a “Web Service API.”

![restvssoap1](https://user-images.githubusercontent.com/4720428/53135555-8b1ac300-3530-11e9-9743-d81b20a76c88.png)

- Used to transfer money and store data
- Anyone can download an Ethereum client and run a node
- Each node has a complete copy of the blockchain

<a name="UnderstandingHTTP"></a>
> ## Understanding HTTP

The request and response are transferred over the internet using a protocol called HTTP (HyperText Transfer Protocol). The HTTP protocol has four parts for request and response:

| HTTP                   | Request                                                                                                                                                                                                                                    | Response                                                                                                                                                                                                            |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Start line (mandatory) | Starts the program and tells it what to do. - HTTP version  - Method  - API program folder name - Request parameters                                                                                                                       | Contains the status code that says if the request was processed successfully. - HTTP version  - Status Code                                                                                                         |
| Headers                | Provides additional information about the request. For example, HOST specifies the URL domain. HOST: www.google.com. Another example of a request header is a token.  If the API has security enabled then you can specify the token here. | Provides additional information about the response. For example, a cookie that is stored on your computer to keep track of your preferences. Another example of a response header is the size of the response file. |
| Blank line             | Separates the header from the body                                                                                                                                                                                                         |                                                                                                                                                                                                                     |
| Body                   | Sends the actual request to the program.  In case of a GET request, the body would be empty.  For POST, it may contain the information that you want to send to the server.                                                                | Sends back the requested information.  For example, an HTML web page.                                                                                                                                               |

The main methods used in the HTTP request are:

- GET 
  - Request information.

- POST
  - Create information.

- PUT
  - Change information.

- DELETE
  - Delete information.

An example of an HTTP request is as follows:
```
GET /search?q=API HTTP/1.1
```

An example of an HTTP response is as follows:
```
HTTP/1.1 200 OK
```
The most popular protocols used to form the HTTP requests and responses are REST and SOAP.


<a name="UnderstandingSOAP"></a>
> ## Understanding SOAP

SOAP is an acronym that stands for Simple Object Access Protocol. It is used to complete a web service using HTTP.

A web service using SOAP has a WSDL (Web Services Description Language). This is an XML file that describes the web service and what you can do with it. 

In SOAP, the HTTP request is created as follows:

1. Start Line: {POST} {WSDL URL} {HTTP version}
   - Method is not used and POST works as a placeholder. 
   - WSDL URL is the WSDL location.

2. Header Line: Content-Type: text/xml
   - SOAP only supports XML as the data format to be used in the body.

3. Body
   - The body constitutes an XML envelope formed using the specific WSDL.

`Example of using a SOAP-based web service`

Web service: HolidayService2 
This web service provides the holidays for a specified country. It is described by this WSDL.

- Method:  POST 
- URL: http://www.holidaywebservice.com/HolidayService_v2/HolidayService2.asmx?WSDL 
- Headers: content-type: test/XML
- Body: 
```
<?xml version="1.0"?>
<soap:Envelope
xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"
xmlns:hws="http://www.holidaywebservice.com/HolidayService_v2/"> //WSDL will tell you this namespace.

<soap:Body>
  <hws: GetHolidaysAvailable>
	<hws: countryCode>UnitedStates</hws: countryCode>
  </hws: GetHolidaysAvailable>
</soap:Body>

</soap:Envelope>
```
<a name="UnderstandingREST"></a>
> ## Understanding REST

- Main (productions apps and where ether has value)
- Ropsten
- Kovan
- Rinkeby
- localhost
- Custom RPC

<a name="RESTversusSOAP"></a>
> ## REST versus SOAP

- Your account consists of your account address, your public key, and your private key
- Account address is similar to your email address
- Public and private keys together form your password
- These are hex numbers, once converted to base10 => 8 x 10^79 (incomprehensibly large, cannot be guessed)

![intro-3](https://user-images.githubusercontent.com/4720428/50611521-9e43d780-0e8b-11e9-8280-74d39ab688d2.png)









