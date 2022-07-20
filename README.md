# day-01

			HTTP/1.1   Vs  HTTP/2

HTTP (HYPERTEXT TRANSFER PROTOCOL):
		Hypertext Transfer Protocol (HTTP) is an application layer protocol for transmitting hypermedia documents, such as HTML. It was designed for communication between web browsers and web servers, but it can also be used for other purposes. It was developed by Tim Berners-Lee in 1989.There are few version of HTTP such as HTTP/0.9,HTTP/1.0,HTTP/1.1 and HTTP/2.
		GET and POST is the similar method ensuring that the requests and responses traveling between the server and client in both protocols reach their destinations as traditionally formatted messages with headers and bodies.

HTTP/1.1:
		   HTTP is a top-level application protocol that exchanges information between a client computer and remote web server. HTTP\1.1 was came into use in 1997. Before that there was version called HTTP/1.0.
			In HTTP/1.0, the client had to break and remake the TCP connection with every new request, it take more time and resources. HTTP/1.1 takes care of this problem by introducing persistent connections and pipelining. With persistent connections, HTTP/1.1 assumes that a TCP connection should be kept open unless directly told to close. This allows the client to send multiple requests along the same connection without waiting for a response to each, this   improves the performance of HTTP/1.1 over HTTP/1.0.
                        HTTP/1.1 transfers the information   in plain-text messages. The first response that a client receives on an HTTP GET request is often not the fully rendered page. Instead, it contains links to additional resources needed by the requested page. The client discovers that the full rendering of the page requires these additional resources from the server only after it downloads the page. Because of this, the client will have to make additional requests to retrieve these resources. This makes more time to load the page.
PROBLEMS in HTTP/1.1:
	       Multiple data packets cannot pass each other when traveling to the same destination, there are situations in which a request at the head of the queue that cannot retrieve its required resource will block all the requests behind it. This is known as head-of-line (HOL) blocking, and is a significant problem with optimizing connection efficiency in HTTP/1.1. Adding separate, parallel TCP connections could control this issue, but there are limits to the number of concurrent TCP connections possible between a client and server, and each new connection requires significant resources.
                HTTP/1.1, flow control relies on the underlying TCP connection.  When this connection initiates, both client and server establish their buffer sizes using their system default settings. If the receiver’s buffer is partially filled with data, it will tell the sender it receive window. This receive window is advertised in a signal known as an ACK packet, which is the data packet that the receiver sends to acknowledge that it received the opening signal. If this advertised receive window size is zero, the sender will send no more data until the client clears its internal buffer and then requests to resume data transmission.  using  receive windows based on the underlying TCP connection can only implement flow control on either end of the connection. Because HTTP/1.1 relies on the transport layer to avoid buffer overflow, each new TCP connection requires a separate flow control mechanism.

HTTP/2:
		HTTP/2 was came in to the publication in May 2015. HTTP/2 began as the SPDY protocol, developed primarily at Google with the intention of reducing web page load latency by using techniques such as compression, multiplexing, and prioritization. The template for the HTTP/2 has  standardization by the IETF(Internet Engineering Task Force) .
            HTTP/2 has a feature called binary framing layer, it make the HTTP/2 more significant from the HTTP/1.1. HTTP/1.1, which keeps all requests and responses in plain text format, HTTP/2 uses the binary framing layer to encapsulate all messages in binary format, while still maintaining HTTP semantics, such as verbs, methods, and headers. An application level API would still create messages in the conventional HTTP formats, but the underlying layer would then convert these messages into binary. This ensures that web applications created before HTTP/2 can continue functioning as normal when interacting with the new protocol.
	 HTTP/2 uses a more advanced compression method called HPACK that eliminates redundant information in HTTP header packets. This eliminates a few bytes from every HTTP packet.
ADVANTAGES of HTTP/2:
  In HTTP/2, the binary framing layer encodes requests/responses and cuts them up into smaller packets of information, greatly increasing the flexibility of data transfer. To lessen the effect of HOL blocking HTTP/1.1 makes a multiple TCP connections, but HTTP/2 establishes a single connection object between the two machines. Within this connection there are multiple streams of data. Each stream consists of multiple messages in the familiar request/response format. Finally, each of these messages split into smaller units called frame.
      The communication channel consists of a bunch of binary-encoded frames, each tagged to a particular stream. The identifying tags allow the connection to interleave these frames during transfer and reassemble them at the other end. The interleaved requests and responses can run in parallel without blocking the messages behind them, a process called multiplexing. Multiplexing resolves the head-of-line blocking issue in HTTP/1.1 by ensuring that no message has to wait for another to finish. This also means that servers and clients can send concurrent requests and responses, allowing for greater control and more efficient connection management



Objects And Its Internal Representation In JavaScript

			Objects, in JavaScript, is it’s most important data-type and forms the building blocks for modern JavaScript. Everything can be an object and objects do have properties and properties have values, so an object is a key value pair. The order of the key is not reserved, or there is no order. To create an object literal, we use two curly brackets. 
                     Objects are different than primitive datatypes (i.e. number, string, boolean, etc.). Primitive data types contain one value but Objects can hold many values in form of Key: value pair. These keys can be variables or functions and are called properties and methods, respectively, in the context of an object.

Syntax:
  Variable objectname  = {
             Key : value
             }
For Eg. If object is a student, it will have properties like name, age, address, id, etc .

Example:
let student = {
name:”dhanesh”,
age:20,
year:2022
}
Objects and properties:
                     A JavaScript object has properties associated with it. A property of an object can be explained as a variable that is attached to the object. Object properties are basically the same as ordinary JavaScript variables, except for the attachment to objects. The properties of an object define the characteristics of the object. You access the properties of an object with a simple dot-notation:
(objectName.propertyName)
Like all JavaScript variables, both the object name  and property name are case sensitive. You can define a property by assigning it a value. 
 Example
 let’s create an object named  “myCar” and give it properties name
Var myCar = new object();
myCar.make= ‘ford’;
myCar.model = ‘mustang’;
myCar.year = 1970;
Unassigned properties of an object are  called  as undefined .

Example:
myCar.color;  // output : undefined
   To access the properties in object JavaScript have some ways, Properties of JavaScript objects can also be accessed or set using a bracket notation . Objects are sometimes called associative arrays, since each property is associated with a string value that can be used to access it.
myCar[‘make’] = ‘ford’;
myCar[‘year’] = 1970.
Creating Objects In JavaScript :

To create object in javascript there are few ways ,such as
             *Object with Object literal
             *Objesct with constructor
             *JavaScript keyword NEW
             *Object.create method
Create JavaScript Object with Object Literal:
       One of easiest way to create a JavaScript object is object literal, simply define the property and values inside curly braces 
let car = { name: ‘mustang’, make: ‘ford’, year:1970};
Create JavaScript Object with Constructor
Constructor is nothing but a function and with help of new keyword, constructor function allows to create multiple objects of same .
Function Vehicle(name,maker){
this.name = name;
this.maker = maker;
}
let car1 = new Vehicle(‘swift’, ‘maruti’);
let car2 = new Vehicle(‘mustang’, ‘ford’);
console.log(car1.name);   // output : swift;
console.log(car2.maker);  // output : ford;
Using the JavaScript Keyword new:
 The following example also creates a new JavaScript object with four properties:
Example
var person = new Object();
person.firstName = “John”;
person.lastName = “Doe”;
person.age = 50;
person.eyeColor = “blue”;
Using the “Object.create” method:
   Objects can also be created using the Object.create() method. This method can be very useful, because it allows you to choose the prototype object for the object you want to create, without having to define a constructor function.

Object Methods:
     There are different methods to manipulate an object. 
	*Object.assign(To copy an object without modifying the original object),

             *Object.keys (To get the keys or properties of an object as an array), 

	*Object.values (To get values of an object as an array),

           * Object.entries (To get the keys and values in an array)
