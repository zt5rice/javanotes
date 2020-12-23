### Lesson 1 Web Application
#### Local Environment Setup
<details>
<summary>What is IDE and why do we need IDE?</summary>
    <ul>
        <li>Integrated Development Environment</li>
        <li>Quickly navigating to a type without needing to worry about namespace, project etc</li>
        <li>Navigating to members by treating them as hyperlinks</li>
        <li>Autocompletion when you can't remember the names of all members by heart</li>
        <li>Automatic code generation</li>
        <li>Refactoring (massive one)</li>
        <li>Organise imports (automatically adding appropriate imports in Java, using directives in C#)</li>
        <li>Warning-as-you-type (i.e. some errors don't even require a compile cycle)</li>
        <li>Hovering over something to see the docs</li>
        <li>Keeping a view of files, errors/warnings/console/unit tests etc and source code all on the screen at the same time in a useful way</li>
        <li>Ease of running unit tests from the same window</li>
        <li>Integrated debugging</li>
        <li>Integrated source control</li>
        <li>Navigating to where a compile-time error or run-time exception occurred directly from the error details.</li>
        Etc!
        <a>https://stackoverflow.com/questions/208193/why-should-i-use-an-ide</a>
    </ul> 
</details>

<details>
<summary>What is Java SE vs Java EE?</summary>
    <ul>
        <li>Java Platform, Standard Edition (Java SE) is a computing platform for development and deployment of portable code for desktop and server environments.</li>
        <li>Jakarta EE, formerly Java Platform, Enterprise Edition (Java EE) and Java 2 Platform, Enterprise Edition (J2EE) is a set of specifications, extending Java SE 8 with specifications for enterprise features such as distributed computing and web services. </li>
        <li>Java ME = Micro Edition. </li>
    </ul> 
</details>

<details>
<summary>What are differences between Java Development Kit(JDK) vs Java Runtime Environment(JRE)?</summary>
    <ul>
        <li>The JRE is the Java Runtime Environment. It is a package of everything necessary to run a compiled Java program, including the Java Virtual Machine (JVM), the Java Class Library, the java command, and other infrastructure. However, it cannot be used to create new programs.</li>
        <li>The JDK is the Java Development Kit, the full-featured SDK for Java. It has everything the JRE has, but also the compiler (javac) and tools (like javadoc and jdb). It is capable of creating and compiling programs.</li>
    </ul> 
</details>

<details>
<summary>What is a web browser and How does it work?</summary>
    <ul>
        <li>A web browser (commonly referred to as a browser) is a software application for accessing (locate, retrieve and display) information on the World Wide Web.</li>
        <li>As a client/server model, the browser is the client run on a computer that contacts the Web server and requests information. The Web server sends the information back to the Web browser which displays the results on the computer or other Internet-enabled device that supports a browser. </li>
    </ul> 
</details>
[Wikipedia] [Link] [Link]

<details>
<summary>What is API testing? What is Postman and why we use it? </summary>
    <ul>
        <li>API testing is a type of software testing that involves testing application programming interfaces (APIs) directly and as part of integration testing to determine if they meet expectations for functionality, reliability, performance, and security.</li>
        <li>Postman is a great tool when trying to dissect RESTful APIs made by others or test ones you have made yourself. It offers a sleek user interface with which to make HTML requests, without the hassle of writing a bunch of code just to test an API's functionality. </li>
    </ul> 
</details>

#### Web Application Basics
What's a web server? [Wikipedia] [Link]
Client Server Architecture(Server vs Client) [Wikipedia] [Link]
Backend vs Frontend [Wikipedia] [GeeksforGeeks]
What is localhost? [Wikipedia] [Link]
Network Protocols and OSI model [Network Protocols Wikipedia] [OSI Model Wikipedia]
TCP/IP [IP Wikipedia] [TCP Wikipedia] [IP Suite Wikipedia]
TCP vs UDP [UDP Wikipedia] [Link] [Link]
Port [Wikipedia]
What’s HTTP? [Wikipedia] [W3School] [MDN]
HTTP 1.0 vs HTTP 1.1 vs HTTP 2.0 [stackoverflow] [Link]
HTTP vs HTTPS [HTTPS Wikipedia] [stackoverflow] [Link] [Link]
What is an HTTP server and what does it do? [Quora]
HTTP messages(request and response) [Link]
HTTP request methods(GET vs POST vs PUT) [Link]
HTTP headers [Link]
Content-Type header [Link] [Media Type]
Access-Control-* header and CORS [Link] 
HTTP Status [Link]
HTTP message body [Wikipedia]
What’s JSON? [Wikipedia] [Link] 
JSON vs XML [Link]
What’s URL? [Wikipedia]
URL vs URI [stackoverflow] [Link]
URL format [Link]

#### Apache Tomcat Server and Maven Project
Apache Tomcat Server [Wikipedia] [Official Website] [Source code]
HTTP server vs Application server [Link] [stackoverflow]
HTTP port vs AJP port [Official Website] [stackoverflow]
What is Server Location(aka CATALINA_HOME)? [stackoverflow]
Options other than Tomcat
Apache HTTP Server [Wikipedia] [Official Website]
Apache HTTP Server vs Apache Tomcat Server [Link]
Node.js [Wikipedia] [Official Website]
Node.js vs Java [Link]
Nginx [Wikipedia] [Official Website]
Nginx vs Tomcat [Link]
Maven Project
What is Maven and why do we need it? [Wikipedia] [Official website] [Quora]
Conventions of groupId, artifactId and version [Official Website] [stackoverflow]
Maven Archetypes [Official Link]
What’s the difference between Maven Build and Maven Install [stackoverflow]