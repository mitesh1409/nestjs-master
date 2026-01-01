# NestJS Crash Course

Reference Video:  
[NestJS Crash Course: Learn in 25 Minutes](https://www.youtube.com/watch?v=2gtiffE3__U)

There is a framework that makes it near impossible to write bad code,  
and that framework is called NestJS.

The NestJS framework achieves this by enforcing a modular architecture,  
and by using TypeScript as the main programming language.

As a result, you can build an application that is:  

- Scalable
- Testable (easy to test)
- Maintainable
- Loosely Coupled
- Reliable

Topics Covered in this Video:  
X 0:00 Create a NestJS app
X 2:17 Decorators
X 3:12 Modules
X 5:19 Controllers
9:24 Providers
11:08 Dependency injection
15:10 Testing
18:26 Error Handling
20:05 Pipes
23:52 Guards


## #1 [[00:00](http://www.youtube.com/watch?v=2gtiffE3__U&t=0)] Create a NestJS App

* **The Nest CLI:**  
This is described as NestJS's "secret weapon."  
You can install it globally via npm:  
`npm install -g @nestjs/cli`  
* **Project Creation:**  
Use the command `nest new podcast-app` to scaffold a new project.
* **Running the App:**  
Start the application in watch mode using `npm run start:dev`.  
By default, the app listens on port 3000.  
* **Main Entry Point:**  
The `main.ts` file uses `NestFactory` to create the application instance using the root `AppModule`.

The Nest CLI can do a lot more than just create projects,  
like generating modules with CRUD resources, controllers, providers, pipes, guards, test files etc.

---

## #2 [[02:17](http://www.youtube.com/watch?v=2gtiffE3__U&t=137)] Decorators

* **Definition:**  
Decorators are not "magic";  
they are functions applied to classes, methods, or parameters to add extra functionality or metadata.  
* **Usage:**  
They are used extensively throughout NestJS to define the role of a class  
(e.g., `@Module()`, `@Controller()`) or to control the behavior of methods and parameters.

---

## #3 [[03:12](http://www.youtube.com/watch?v=2gtiffE3__U&t=192)] Modules

* **Architecture:**  

NestJS is like a severe parent that knows what is best for you.  
You just need to obey the framework and things will be fine.  

A strong recommendation is to structure your code in Modules.

NestJS enforces a modular structure.  
Every app has one **Root Module** (`AppModule`), which forms an "application graph"  
by importing other modules.  

* **Encapsulation:**  
Modules encapsulate related capabilities (e.g., an "Episodes Module" or "Topics Module").  
* **CLI Command:**  
Generate a module using `nest generate module <name>`.  
* **Configuration:**  
The `@Module()` decorator takes a configuration object with properties like `imports`, `controllers`, `providers`, and `exports`.

---

## #4 [[05:19](http://www.youtube.com/watch?v=2gtiffE3__U&t=319)] Controllers

If your app has no controller then your app can't handle any incoming requests.  

A controller is a class decorated with the `@Controller` decorator.

* **Role:**  
Controllers are the entry points for handling incoming HTTP requests.  
* **Routing:**  
Defined using the `@Controller('path')` decorator.  
Methods within the class handle specific HTTP verbs using decorators like  
`@Get()`, `@Post()`, `@Put()`, and `@Delete()`.  
These method decorators accept a string as parameter as well,  
and that string argument can be a nested root path.  
* **Request Data:**  
You can access request details using parameter decorators:  
  * `@Query()` for URL query parameters.
  * `@Param()` for URL path parameters (e.g., `:id`).
  * `@Body()` for the request payload.
* **Generate Controller:**  
`nest generate controller <controller-name>`

Basically, you tell NestJS what you want by using decorators and the framework  
does the heavy lifting for you.

---

## #5 [[09:24](http://www.youtube.com/watch?v=2gtiffE3__U&t=564)] Providers

* **Concept:**  
Nearly everything in Nest is a provider. These are classes decorated with `@Injectable()`.  
* **Services:**  
The most common providers are services, which handle business logic and data manipulation.  
* **CLI Command:**  
Generate a service using `nest generate service <name>`.  
* **Registration:**  
Providers must be added to the `providers` array in a module to be available for injection.  


---

Gen AI Content


### **[[11:08](http://www.youtube.com/watch?v=2gtiffE3__U&t=668)] Dependency Injection**

* **Mechanism:** Instead of manually instantiating classes, NestJS injects them via the class **constructor** at runtime [[12:15](http://www.youtube.com/watch?v=2gtiffE3__U&t=735)].
* **Example:** To use a service in a controller, you declare it as a private parameter in the constructor: `constructor(private service: EpisodeService) {}` [[12:32](http://www.youtube.com/watch?v=2gtiffE3__U&t=752)].
* **Sharing Providers:** To use a service from another module, the providing module must list it in its `exports`, and the consuming module must list the providing module in its `imports` [[14:03](http://www.youtube.com/watch?v=2gtiffE3__U&t=843)].

### **[[15:10](http://www.youtube.com/watch?v=2gtiffE3__U&t=910)] Testing**

* **Utilities:** Nest provides a `Test` utility to create a mock module environment (`Test.createTestingModule`) [[15:25](http://www.youtube.com/watch?v=2gtiffE3__U&t=925)].
* **Isolation:** Dependency injection makes testing easier because you can swap real providers with **mock objects** using the `useValue` property [[16:05](http://www.youtube.com/watch?v=2gtiffE3__U&t=965)].
* **Assertions:** You can verify if a controller returns the expected mock data or if service methods were called with the correct arguments [[16:45](http://www.youtube.com/watch?v=2gtiffE3__U&t=1005)].

### **[[18:26](http://www.youtube.com/watch?v=2gtiffE3__U&t=1106)] Error Handling**

* **Standard Exceptions:** Nest has built-in support for HTTP exceptions like `HttpException`, `NotFoundException` (404), and `ForbiddenException` (403) [[18:52](http://www.youtube.com/watch?v=2gtiffE3__U&t=1132)].
* **Automation:** When an exception is thrown, Nest automatically converts it into a structured JSON response for the client [[19:19](http://www.youtube.com/watch?v=2gtiffE3__U&t=1159)].

### **[[20:05](http://www.youtube.com/watch?v=2gtiffE3__U&t=1205)] Pipes**

* **Purpose:** Pipes are used for **validation** (checking if data is correct) and **transformation** (converting data types) [[20:16](http://www.youtube.com/watch?v=2gtiffE3__U&t=1216)].
* **Built-in Pipes:** Examples include `ParseIntPipe` and `DefaultValuePipe` [[20:32](http://www.youtube.com/watch?v=2gtiffE3__U&t=1232)].
* **Validation with DTOs:** By using Data Transfer Objects (DTOs) with the `class-validator` and `class-transformer` libraries, you can enforce strict rules on incoming `@Body()` data [[21:49](http://www.youtube.com/watch?v=2gtiffE3__U&t=1309)].

### **[[23:52](http://www.youtube.com/watch?v=2gtiffE3__U&t=1432)] Guards**

* **Access Control:** Guards determine whether a request should be handled by a route based on conditions like authentication or permissions [[23:52](http://www.youtube.com/watch?v=2gtiffE3__U&t=1432)].
* **Implementation:** A guard is a class that implements the `CanActivate` interface and returns `true` or `false` [[24:11](http://www.youtube.com/watch?v=2gtiffE3__U&t=1451)].
* **Application:** Guards can be applied to an entire controller or a specific method using the `@UseGuards()` decorator [[24:55](http://www.youtube.com/watch?v=2gtiffE3__U&t=1495)].

---

### **Summary**

NestJS is a highly opinionated framework that enforces a rigid architecture to ensure code is scalable and maintainable. Its core strengths lie in its **Modular system**, which organizes code into logical blocks; its **Dependency Injection** system, which simplifies testing and reduces coupling; and its extensive use of **Decorators** to handle boilerplate tasks like routing, validation, and security. By following the "Nest way" using the CLI and built-in tools like Pipes and Guards, developers are guided toward writing high-quality, professional-grade APIs.

