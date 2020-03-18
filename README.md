# Comparing REST and SOAP Web Services

To fully understand the difference between REST and SOAP, it's important to understand what an API is and how it works. 

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

API stands for application programming interface.
 - Application (A) is a piece of software code that performs a task.
 - Program (P) is a set of instructions that executes the task.
 - Interface (I) is a place where you tell the program to run.

**Simple APIs**

You can access the interface of the application using a browser or mobile app. 

For example, Google homepage is an interface on your browser through which you run a program that performs a search and returns the results.

**Complex APIs**

You have to access the interface at the server location.  

For example, the Google Translation API is an the interface for the Google translation server through which you run the translation program.

Typically, the term API refers to a complex API.

Accessing the interface where the software is located is cost efficient for the software vendor, because they do not have to build a web or mobile app for you to interact with. You also have the flexibility to write your own interface to interact with with that software. 

<a name="UnderstandingAPIs"></a>
> ## Understanding APIs

An API transaction workflow is as follows:

1. A request is made for a task to be performed.
2. A program is run to complete that request.
3. The program sends back a response with the results.
 
If the requests and responses are sent over the internet, then the API is called a web service API.

![restvssoap1](https://user-images.githubusercontent.com/4720428/53135555-8b1ac300-3530-11e9-9743-d81b20a76c88.png)

<a name="UnderstandingHTTP"></a>
> ## Understanding HTTP

The request and response are transferred over the Internet using a protocol called HTTP (HyperText Transfer Protocol). 
The HTTP protocol has four parts for request and response:

HTTP | Request | Response | Required
:--- | :--- | :--- | :---
`Start line` | Starts the program and tells it what to do. ```HTTP version - Method - API program folder name - Request parameters``` | Contains the status code that says if the request was processed successfully. ```HTTP version - Status Code``` | Yes
`Headers` | Provides additional information about the request. For example, HOST specifies the URL domain. ```HOST: www.google.com```. Another example of a request header is a token. If the API has security enabled, you can specify the token here. | Provides additional information about the response. For example, a cookie that is stored on your computer keeps track of your preferences. Another example of a response header is the size of the response file. | No
`Blank line` | Separates the header from the body | - | -
`Body` | Is the actual request to the program. In case of a GET request, the body would be empty. For POST, it might contain the information that you want to send to the server. | The requested information. For example, an HTML web page. | No

The main methods used in the HTTP request are as follows:

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

The most popular protocols used to form HTTP requests and responses are REST and SOAP.


<a name="UnderstandingSOAP"></a>
> ## Understanding SOAP

SOAP stands for simple object access protocol. It's used to complete a web service using HTTP.

A web service using SOAP has a WSDL (Web Services Description Language). This is an XML file that describes the web service and what you can do with it. 

In SOAP, the HTTP request is created as follows:

1. Start Line: `{POST} {WSDL URL} {HTTP version}`
   - POST is just a placeholder in this case because SOAP doesn't use the method. 
   - WSDL URL is the WSDL location.

2. Header Line: Content-Type: text/xml
   - SOAP only supports the XML data format for the body.

3. Body
   - Is the XML envelope formed using the specific WSDL.

An example of a SOAP-based web service is as follows:

```
Web service: HolidayService2 
This web service provides the holidays for a specified country. 
It's described by the following WSDL:

- Method:  POST 
- URL: http://www.holidaywebservice.com/HolidayService_v2/HolidayService2.asmx?WSDL 
- Headers: content-type: test/XML
- Body: 

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

REST stands for representational state transfer. It's also used to complete a web service using HTTP.

In REST, the method contains a verb which specifies the action that you want the server to perform.

In the database world, if you have a table with records in it, you can create a record, read the record, update the record, and delete the record.

REST is essentially making these calls to the server. 

The HTTP request is created as follows:

1. Start Line: {Method} {HTTP version}
   - Use GET, POST, PUT, and DELETE methods.

2. Header Line
   - Specify any data format for the body. For example, JSON, XML, HTML, and so on.

3. Body
   - Use any data format. For example, JSON, XML, HTML, and so on.

An example of using a REST-based web service is as follows:

```
- Web service: developer.ebay.com 
  - This web service provides access to items listed on eBay.

- Method:  GET
- URL: https://api.sandbox.ebay.com/buy/browse/v1/item_summary/search?q=computer&limit=5 
```

You get back a JSON document with 5 items with the term `computer` in the title. 


<a name="RESTversusSOAP"></a>
> ## REST versus SOAP

In SOAP, you have a WSDL that you have to follow. With REST, you can just tell the program what to do using the method. 

In SOAP, you can only use XML-formatted data in the body. With REST, you can use any data format.

REST is stateless. You send a request to a server, if the server is running it sends you back the results, if it's not running it waits for the server to run again and then sends you back the results. In SOAP, if the server is not running, your request results in an error.

REST is the most preferred method of creating APIs today, because REST is much simpler to implement than SOAP.

The graph below shows the growth of REST in comparison with SOAP. The usage of SOAP is declining and REST is exploding in popularity.

![restvssoap2](https://user-images.githubusercontent.com/4720428/53136395-b226c400-3533-11e9-9cb7-6828c97febcc.png)









