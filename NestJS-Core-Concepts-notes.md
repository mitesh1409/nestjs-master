# NestJS Core Concepts

Reference Video:  
[Every NestJS Concept Explained in 9 Minutes](https://www.youtube.com/watch?v=IdsBwplQAMw)

## #1 What is NestJS?

A progressive Node.js framework for building efficient, reliable and scalable server-side applications.

What you can build with NestJS?  

- An HTTP Server Application
  Using `NestFactory.create()` method.
- A Microservice Application
  Using `NestFactory.createMicroservice()` method.
  Microservices are similar to HTTP server applications.
  Microservices can communicate with each other using different transport layers like TCP, Redis, NATS, MQTT etc.
  Microservices are ideal for building distributed systems and event-driven architectures.
  Microservices can be independently deployed and scaled.
- A Standalone Application
  Using `NestFactory.createApplicationContext()` method.
  Standalone applications are not connected to any network protocols.
  They are ideal for building CLI tools, background jobs, data processing tasks etc.

All these applications have one thing in common -  
They are all built using the same building blocks of NestJS,  
which are Modules, Controllers, Providers, Middlewares, Guards, Interceptors, Pipes and Exception Filters.

## #2 Modules

Analogy  
Think of modules as the departments in a company.  
Each department has its own responsibilities and functions,  
but they all work together to achieve the company's goals.

Modules are the building blocks of a NestJS application.

At the top there is a Root Module,  
and this Root Module can have other modules under it.

In terms of implementation a module is a class  
that is annotated with `@Module` decorator.

## #3 Decorators

Analogy  
Think of decorators as wearing accessories or suits that gives you extra powers.

A decorator is a special kind of function,  
and it can be attached to classes, methods, properties etc.  
and it modifies their behavior  
and it can even add metadata.

## #4 Controllers

Analogy  
Think of controllers as the air traffic controllers at an airport.  
OR  
Think of controllers as the receptionist at a hotel.  

Controllers are classes that are annotated with the `@Controller` decorator.

A controller is simply in charge of  
receiving incoming request and returning a response.

The main role of a controller is to receive requests and return responses.  
Anything else is delegated to other classes such as providers.

Controllers must be THIN.

## #5 Providers

Analogy  
You can think of providers as freelance workers,  
and NestJS is an agency that places those freelance workers  
wherever they are needed.

Most of the code that you will be writing in NestJS is within providers.

A provider is simply a class that can be  
injected in other classes as dependency.

A provider class is annotated with the `@Injectable` decorator.

This is how Dependency Injection and Singleton Pattern is used in NestJS.

## #6 Middlewares

Analogy  
When you want to travel by plane,  
you have to go through different stages like check in your luggage, passing the security check etc.  

Similarly, in NestJS,  
Middlewares are functions that are invoked before the request reaches the controller.
Middlewares have access to the request and response objects,
and they can modify them if needed.

Middlewares are useful for tasks such as logging, authentication, etc.

NestJS comes with built-in features for common request flow management.

## #7 Guards

Analogy  
You can think of guards as security personnel  
who check if you have the right credentials to enter a building.  
OR  
You can think of guards as the security personnel at the airport  
who check if you have the right credentials to board the plane.

Guards are critical part of the request lifecycle in NestJS.
They determine whether a request will be handled by the route handler or not.

The primary purpose of guards is to determine whether the request will be  
handled by the route handler or not based on certain conditions such as  
user roles, permissions, or any other custom logic etc.  

Guards are implemented by creating classes that implement the `CanActivate` interface.

## #8 Interceptors

Analogy  
You can think of interceptors as the customs officers at the airport  
who inspect your luggage before you leave and when you arrive.

After the guards, interceptors come into play in the request lifecycle.

They run before and after the route handler is executed.
So they give you full control over the request-response cycle.

Interceptors implement the `NestInterceptor` interface.
They can perform tasks like - logging, caching, transforming the request/response, etc.

## #9 Pipes

Analogy  
You can think of pipes as quality control inspectors  
who check the products before they are shipped out to customers.  
OR  
You can think of pipes as the security scanners at the airport  
who check your luggage for prohibited items before you board the plane.

Pipes allow you to transform and validate incoming data before it reaches the route handler.

Pipes are classes that implement the `PipeTransform` interface,  
they are annotated with the `@Injectable` decorator.

[Built-in pipes](https://docs.nestjs.com/pipes#built-in-pipes)

## #10 Exception Filters

Analogy  
You can think of Exception Filters as the customer service representatives  
who handle complaints and issues raised by customers.  
OR  
You can think of Exception Filters as the emergency response team  
who handle unexpected situations during a flight.

Exception Filters are used to handle exceptions thrown during the request lifecycle.
You can customize the error handling logic in your application using Exception Filters.

Exception Filters are classes that implement the `ExceptionFilter` interface,  
and they are annotated with the `@Catch` decorator.

They can catch exceptions thrown by any part of the request handling process  
(middlewares, guards, interceptors, pipes, route handlers etc.),  
and provide a custom response to the client.

This ensures that the client receives a consistent and meaningful error response,  
and that sensitive information is not exposed.

Exception Filters provide a centralized way to manage errors in your application.

## #11 Request Lifecycle in NestJS

Request Lifecycle in NestJS:  

1. Request
2. Middlewares
3. Guards
4. Interceptors
5. Pipes
6. Route Handler
7. Interceptors (again)
8. Exception Filters (if any exception occurs)
9. Response
