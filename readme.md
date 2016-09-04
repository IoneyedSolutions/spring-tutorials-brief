# Spring Boot Web - Tutorial

# Step 1 - First Page

## Introduction

This Step in the tutorial will teach you how to implement a basic index page into a Spring Boot application. This will be a very basic implementation so that concepts are discussed.

## Terminology

* URL - A URL is a URI (Unified Resource Identifier). This is the generic term for all types of addresses on the WWW (World Wide Web). A URL is broken into several parts. Let's take this URL as an example 

    [http://localhost:8080/greeting?name=MyName](http://localhost:8080/greeting?name=MyName)
    
    `http://` is the Protocol (this can be ftp, tcp, mqtt, ssh, etc) 
  
    `localhost` is the server that we want to view
  
    `:8080` is the port that is being targeted to view
  
    `/greeting` is the context path. The context path is the path to which you are trying to access on the application
    
    `?` denotes query parameters (or called url parameters) are being sent to the server as well. These are generally used for data that is not sensitive to normal operations as it is viewable by anyone who can get on the computer assuming techniques like *Incognito Mode* are not used.
    
    `name=` denotes the key, or parameter, that is being sent while `MyName` is the value that is being sent.
* RequestMapping - This is the URL context in which you want the page to be display.
* JSP - Java Server Page, this is a html file that is served up by a Java based application. JSP's allow for server-side processing to happen (such as dynamic values in the html) before the page is sent to the client.
* Template - This is a Html Template that will be served up by the embedded Tomcat instance that is provided by the Spring Boot framework.
* MVC - MVC is an acronym that stands for Model-View-Control. This is a design pattern that is used to separate the concerns of the Data/Presentation/ Interaction of a website.
* Controller - This is the function that will control the server side user interaction for the context path.
* View - This is the Template that will control the presentation for the context path.

## Dependencies

* spring-boot-starter-thymeleaf - This Starter enables the Spring Framework MVC (a.k.a Spring MVC) packages using the [Thymeleaf](http://www.thymeleaf.org/) templating engine. 

# Let's Begin

During this step you will learn how to:

* Add the `spring-boot-starter-thymeleaf` package to our gradle dependency list.
* Create a Spring Controller
  * Serve up a static html template  
  * Serve up a dynamic html template

## Add Dependency to Gradle

To complete this step we will need to add a dependency to our `build.gradle` file so that gradle will download the necessary dependency.

1. Open `build.gradle`
2. Find the line 

   `compile('org.springframework.boot:spring-boot-starter-web')`

   Add the following below this line

   `compile('org.springframework.boot:spring-boot-starter-thymeleaf')`
3. Download the dependency via gradle

   \*Nix - `./gradlew clean build`

   Windows - `gradlew.bat clean build`
   
## Create a Controller

1. To begin we will navigate to the `src/main/java/com/example/demo` folder in our application in your favorite IDE/Editor.
2. Create a new Folder/Package (Synonymous with each other) named `controller` (all lower case, singular)
3. Create the Index Controller. This default controller which is served up on the `/` context path will be our static html file that we serve up.
    
    `src/main/java/com/example/demo/controller/IndexController.java`

        package com.example.demo.controller;
    
        import org.springframework.stereotype.Controller;
        import org.springframework.web.bind.annotation.RequestMapping;

        @Controller
        public class IndexController {

           @RequestMapping("/")
           public String index() {
               return "index";
           }
        }

## Create the Index Html

1. Navigate to `src/main/resources/templates`. This is the default location that the Spring Framework will look for JSP Templates.
2. Create a new File. 

    `src/main/resources/templates/index.html`

        <html>
          <head><title>Spring Boot Tutorial - Step 1</title>
          <body>
            <h1>Welcome to the Index Template</h1>
          </body>
        </html>

3. Once both the Controller and the Index file are created, run the application via the gradle task.

    `./gradlew bootRun` - \*Nix users

    `gradle.bat bootRun` - Windows users

4. When the application has booted you will see a log entry in your terminal that states

    `Tomcat started on port(s): 8080 (http)`

   You may now visit [http://localhost:8080/](http://localhost:8080/)

5. Validate our Controller is serving up our Template of "Welcome to the Index Template"

## Modify the IndexController/Index Html to be Dynamic

We will be modifying our newly created `IndexController.java` and `Index.html` to accept URL parameters to render a dynamic value onto the page. We will start with modifying the controller to accept the URL parameters.

1. Make the following changes to the `IndexController`

    `src/main/java/com/example/demo/controller/IndexController.java`

    Add the new annotation that is needed `RequestParam` to the `import` section
    
        import org.springframework.stereotype.Controller;
        import org.springframework.web.bind.annotation.RequestMapping;
        import org.springframework.web.bind.RequestParam;
        import org.springframework.ui.Model;

    Create a new `dynamic()` method to allow for parameters to be passed into the function.

        @Controller
        public class IndexController {

           @RequestMapping("/")
           public String index(){
               return "index";
           }

           @RequestMapping("/dynamic")
           public String dynamic(@RequestParam(value = "name", required = false, default = "Anonymous") String name, Model model) {
               model.addAttribute("name",name);
               return "dynamic";
           }
        }

2. Create a new file called `dynamic.html` in the `src/main/resources/templates/` directory.

      `src/main/resources/templates/dynamic.html`

        <html>
          <head><title>Spring Boot Tutorial - Step 1</title></head>
          <body>
            <h1>Welcome, <span th:text="${name}" />, to the dynamic Controller</h1>
          </body>
        <html>

3. Run the application and test it out.

      `./gradlew bootRun` - for \*Nix (Mac/Linux/Unix) users;
     
      `./gradlew.bat bootRun` - for Windows users;

   Once running you will see the Spring Boot output showing that it started up. If you do not get an error you will see the following line at the end.

        .... Tomcat started on port(s): 8080 (http)
        .... Started StarterApplication

   Now you can visit our application at [http://localhost:8080/](http://localhost:8080/). By visiting the root context you will see the `Static` page. Now navigate to the new context path `/dynamic` that we created [http://localhost:8080/dynamic](http://localhost:8080/dynamic).

   Once you have loaded the `dynamic` controller you will see that the text has changed to "Welcome, Anonymous, to the dynamic Controller". Now at the end of our URL add the following `?name=MYNAME` replacing `MYNAME` with your name.


# Tutorial Branches of Content
1. Checkout the branch for which step of the tutorial you wish to start.
   1. `git checkout master`
   2. `git checkout step/introduction` 
   3. `git checkout step/first_page` ***currently here***
   4. `git checkout step/first_endpoint`
   5. `git checkout step/first_test`

2. Once the branch you want to start from is checked out localy run the gradle command from the project's base folder.

   `./gradlew clean build` - for \*Nix (Max/Linux/Unix) users

   `gradlew.bat clean build` - for Windows users


