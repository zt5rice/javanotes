# Spring

<details>
<summary>Tell me something about your online shopping system. </summary>
    <ul>
        Used Spring framework to build a web application for users to shop and order items online. 
        <li>Built a web application based on Spring MVC to support item search and listing (dependency injection, inversion of control, REST API, etc.).</li>
        <li>Implemented security workflow via in-memory and JDBC authentication provided by Spring Security. </li>
        <li>Utilized Hibernate to provide better support of database operations</li>
        <li>Developed a Spring Web Flow to support item ordering.</li>
</ul>
</details>

<details>
<summary>Why do you design such system? </summary>
<ul>
</ul>
</details>

<br>

<details>
<summary>What is the Spring framework?</summary>
<ul>Spring framework is an open source development framework for Enterprise Java. The core features of the Spring Framework can be used in developing any Java application, but there are extensions for building web applications on top of the Java EE platform.</ul>
</details>



<details>
<summary>What does the Spring framework solve for us?</summary>
<ul>Spring Framework is loosely coupled because it has concepts like Dependency Injection, AOP etc. These features help in reducing dependency and increasing the modularity within the code.</ul>
</details>



<details>
<summary>How do we use the Spring framework in our project? </summary>
<ul>We use annotation-based and java based configuration to let spring framework to initialize all the classes that needed to run the application. </ul>
</details>

<details>
<summary>What is the spring ioc container? </summary>
<ul>The Spring container is responsible for creating the objects, configuring and wiring them, and also managing their complete lifecycle.</ul>
</details>


<details>
<summary>What is the inversion of control/Dependency Injection in Spring?</summary>
<ul>控制反转是相对于正向而言的，那么什么是正向呢？考虑一下常规情况下的应用程序，如果要在A里面使用B，你会怎么做呢？当然是直接去创建B的对象，也就是说，是在A类中主动去获取所需要的外部资源B，这种情况被称为正向。那么什么是反向呢？就是A类不再主动去获取B，而是被动等待，等待从spring的容器获取一个B的实例，然后反向的注入到A类中.</ul>
</details>

<details>
<summary>What are Spring bean & scopes? </summary>
<ul>
    <li></li>
The Spring beans are java objects that are instantiated, assembled, and managed by the Spring container.
In singleton scope, it defines a class that only has one single instance in the Spring container.
In prototype scope,  it defines a class that has any number of object instances in the Spring container.
</ul>
</details>




<details>
<summary>How do you provide configuration metadata to the Spring Container?</summary>

````
<li>XML based configuration file <bean>
Annotation-based configuration: @Component
Java-based configuration: @Configuration and @Bean
````

</details>


<details>
<summary>What is Spring Java-Based Configuration?  </summary>
<ul>
Java based configuration enables you to write most of your Spring configuration without XML but with the help of few Java-based annotations.
Example is the @Bean annotated method that will return an object that should be registered as a bean in the Spring container.
</ul>
</details>



<details>
<summary>Differentiate @Component, @Repository and @Service and @Controller</summary>
<ul>
Typically a web application is developed in layers like the controller (which is the initial point of client communication), business (where the actual code or logic of the application is written) and DAO (where the database connections and interaction happens). In such an architecture web application, @Component can be used in any of the layers. Whereas, the @Controller is used in the controller/web layer. @Service is used in the business layer and @Repository is used in the DAO layer.
</ul>
</details>


<details>
<summary>What is @Autowire?</summary>
<ul>
The @Autowired annotation can be used with fields or methods for injecting a bean by type.
</ul>
</details>



<details>
<summary>What are the benefits of using Spring? </summary>
<ul>
1. It gives good support for IoC and Dependency Injection results in loose coupling.
2. It facilitates good programming practice such as programming using interfaces instead of classes.
</ul>
</details>


<details>
<summary>What is the Spring MVC framework? </summary>
<ul>
The Spring Web MVC framework provides Model-View-Controller (MVC) architecture and ready components that can be used to develop flexible and loosely coupled web applications.
</ul>
</details>



<details>
<summary>Why do you design such system? </summary>
<ul>
</ul>
</details>
DispatcherServlet
The Spring Web MVC framework is designed around a DispatcherServlet that handles all the HTTP requests and responses.

<details>
<summary>What is Controller in Spring MVC framework?</summary>
<ul>
Controller handles navigation logic and transfer to service layer
Annotations used in Spring mvc framework
@Controller
The @Controller annotation indicates that a particular class serves the role of a controller. Spring does not require you to extend any controller base class or reference the Servlet API.
@RequestMapping annotation
@RequestMapping annotation is used to map a URL to either an entire class or a particular handler method.
@PathVariable/@RequestParam annotation
Use @PathVariable annotation on a method argument to bind it to the value of a URI template variable.
For example, if we want to fetch an owner id from the www.xxx.com/owners/123, we should map our method in the controller as /owners/{ownerId}:
````java
@RequestMapping(value="/owners/{ownerId}", method=RequestMethod.GET)
public String findOwner(@PathVariable(“ownerId”) int ownerId) {
    ...
}
````
</ul>
</details>



Use @RequestParam annotation on a method argument to access servlet request parameters

For example, if we want to fetch an owner id from the www.xxx.com/owners?id=123, we should map our method in the controller as /owner and use @RequestParam to fetch the id
````
@RequestMapping("/owner")
public String handleRequest(@RequestParam("id") int userId) {}
````

<details>
<summary>What is ModelAndView? </summary>
<ul>
ModelAndView contains the view name and model, it allows us to pass all the information required by Spring MVC in one return.
</ul>
</details>



<details>
<summary>What is hibernate? </summary>
<ul>
Hibernate is an object-relational mapping tool for the Java programming language. It provides a framework for mapping an object-oriented domain model to a relational database.
</ul>
</details>



<details>
<summary>Identifiers in Hibernate </summary>
<ul>
Simple identifiers map to a single basic attribute, and are denoted using the javax.persistence.Id annotation
Composite identifiers correspond to one or more persistent attributes.
https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#identifiers-composite
</ul>
</details>



<details>
<summary>Associations in Hibernate </summary>
<ul>
@OneToOne is identical to the @ManyToOne association, as the client-side controls the relationship based on the foreign key column.
@ManyToOne is the most common association, having a direct equivalent in the relational database (e.g. foreign key), and so it establishes a relationship between a child entity and a parent. 
The @OneToMany association links a parent entity with one or more child entities.
The @ManyToMany association requires a link table that joins two entities.
</ul>
</details>



<details>
<summary>What is mappedBy used for? </summary>
<ul>
mappedBy signals hibernate that the key for the relationship is on the other side. This means that although you link 2 tables together, only 1 of those tables has a foreign key constraint to the other one. 
    Three important interfaces in hibernate
    SessionFactory: it is a heavyweight object which usually is created during application start up for connecting to a database and kept for later use. It also services clients to obtain Session instances from this factory.
    Session: this is the central API class abstracting the notion of a persistence service, the main function of the Session is to offer create, read and delete operations for instances of mapped entity classes.
    Transaction: allows the application to define units of work.
</ul>
</details>