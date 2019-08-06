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

REST is an acronym that stands for representational state transfer. It is used to complete a web service using HTTP.

In REST, the method contains the verb which specifies the action that you want the server to perform.

In the database world, if you have a table with records in it, you can create a record, read the record, update the record, and delete the record.

REST is essentially making these calls to the records in the backend database. 

In REST, the HTTP request is created as follows:

1. Start Line: {Method} {HTTP version}
   - You can use any method. For example, GET, POST, PUT, DELETE, and so on.

2. Header Line
   - You can use any data format. For example, JSON, XML, HTML, and so on.

3. Body
   - You can use any data format. For example, JSON, XML, HTML, and so on.

`Example of using a REST-based web service`

- Web service: developer.ebay.com 
  - This web service provides access to items listed on eBay.

- Method:  GET
- URL: https://api.sandbox.ebay.com/buy/browse/v1/item_summary/search?q=computer&limit=5 

You will get back a JSON document with five items with the term “computer” in the title. 


<a name="RESTversusSOAP"></a>
> ## REST versus SOAP

In SOAP, you have a WSDL that you have to follow. With REST, you can just tell the program what to do using the method. 

In SOAP, you can only use XML-formatted data in the body. With REST, you can use any data format.

REST is stateless. You send a request to a server, if the server is running it sends you back the results, if it is not running it waits until the server starts running again and then sends you back the results. In SOAP, if the server is not running, your request results in an error.

REST is the most preferred method of creating APIs today because REST is much simpler to implement than SOAP.

The graph below shows the growth of REST in comparison with SOAP. The usage of SOAP is declining and REST is exploding in popularity.

![restvssoap2](https://user-images.githubusercontent.com/4720428/53136395-b226c400-3533-11e9-9cb7-6828c97febcc.png)









