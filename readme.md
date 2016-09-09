# Spring Boot Web - Tutorial

# Introduction

Greetings! You are here to learn the quick run down on Spring Boot and how to build a basic Server Rendered Page (using Spring MVC) a basic RESTful API (using Spring Boot) and how to integrate basic testing.

This tutorial will cover some basic terminology of Spring, java development, and web application development. After finishing the tutorial you will have a basic understanding of what Spring Framework has to offer, how to build a basic web application, and how to write a unit test (tested code is good code).

## Who this tutorial is for

This tutorial is geared towards beginners. It will attempt to cover some basic Java concepts and terminology and will provide resources to learn more about Java and Spring itself if a deeper dive is desired.

## Why another tutorial

This tutorial is not meant to be the best tutorial nor be better than others however this tutorial is being written in a way that can easily guide someone through the basics of Spring. We know there are already plenty of tutorials out there for Java, Spring and any technology that can be made into a tutorial but like any tutorial there is a twist we are looking to fill that others may not and writing tutorials allows for greater understanding of what is being taught.

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
* Java Bean - (aka Bean/POJO) - A Java bean is a java class that follows the following standards
  * All properties are private (use [getters/setters](https://en.wikipedia.org/wiki/Mutator_method#Java_example) for access)
  * A public [no-argument constructor](https://en.wikipedia.org/wiki/Nullary_constructor)


## Dependencies

* JDK 1.8
* A Text Editor (i.e. [Atom](https://atom.io/) ) or an [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) such as [Spring Tools Suite (STS)](https://spring.io/tools)
* [Git](https://git-scm.com/) - [Git Tutorial](https://try.github.io/levels/1/challenges/1)

# How is the tutorial structured

This tutorial will walk you through step by step using Git Branches. Each step will start from the previous step allowing you to skip ahead, go back to a clean state, or look at each concept before moving on to the next step. The git commands are provided but a basic understanding of Git is advised.

## Tutorial Branches of Content
1. Checkout the branch for which step of the tutorial you wish to start.
   1. `git checkout master` ***currently here***
   2. `git checkout step/first_page` 
   3. `git checkout step/first_endpoint`
   4. `git checkout step/first_test`

2. Once the branch you want to start from is checked out localy run the gradle command from the project's base folder.

   `./gradlew clean build` - for \*Nix (Max/Linux/Unix) users

   `gradlew.bat clean build` - for Windows users


