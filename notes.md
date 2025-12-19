# NestJS

## #1 What is NestJS?

A progressive Node.js framework for building efficient, reliable and scalable server-side applications.

## #2 What you can build with NestJS?

- An HTTP Server Application
- A Microservice Application
- A Standalone Application

## #3 Modules

Modules are the building blocks of a NestJS application.

At the top there is a Root Module,  
and this Root Module can have other modules under it.

In terms of implementation a module is a class  
that is annotated with `@Module` decorator.

## #4 Decorators

A decorator is a special kind of function,  
and it can be attached to methods, classes, properties  
and it modifies their behavior  
and it can even add metadata.

Analogy  
Think of decorators as wearing accessories or suits that gives you extra power.

## #5 Controllers

Controllers are classes that are annotated with the `@Controller` decorator.

A controller is simply in charge of  
receiving incoming request and returning a response.

## #6 Providers

Most of the code that you will be writing in NestJS is within providers.

A provider is simply a class that can be  
injected in other classes as dependency.

Analogy  
You can think of providers as freelance workers,  
and NestJS is an agency that places those freelance workers  
wherever they are needed.

This is how Dependency Injection and Singleton Pattern is used.
