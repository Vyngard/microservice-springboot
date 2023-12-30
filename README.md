# Spring Boot 3 Microservice
As a software engineer, you hear the term "Microservice" a lot. But there is a good chance that you don't see an actual implementation of it. So, in order to learn in practical way, I 
decided to implement a simple microservice project. In this project, I used Spring Boot 3 to get familiar with this framework too.   

# Description
In this project, you have two different services:   

- Department Service
- Employee Service   

Each service has its own responsibility. So, the department service is in charge of adding and showing departments, and the employee service is in charge of adding and showing employees.    
Also, the department service interacts with the employee service, so if we want to get a list of employees of a specific department, we can call the employee service from the department service.   
below, you can see the entire architecture of this project.

![Architecture](./Project%20Architecture.jpg)

# Technologies
- HttpExchange: To connect department and employee services with each other.
- Eureka Service Registry: It has all the information about the services. So we can use this for scaling. Also, when we want to do the API call from department service, we use the service registry, since it has all the information about the employee service instances. So, it will handle load balancing as well.
- Spring Cloud API Gateway: It is a gateway for each public request coming to our architecture. So, others cannot call our APIs directly. We also handle security here to make sure that only authorized users can call our APIs.
- Config Server: It will serve all the default configurations for each service.
- Zipkin: It does the log tracing for each request so that we can do the debugging easily.

# How to run
Just clone the project and run all services.

# Endpoints
You can use Postman for that matter.    

- for department service:
  - Add a department: `POST http://localhost:8081/department`
  - Get all departments: `GET http://localhost:8081/department`
  - Get a department by id: `GET http://localhost:8081/department/{id}`
  - Get all employees of all departments: `GET http://localhost:8081/department/with-employees`

- for employee service:
    - Add an employee: `POST http://localhost:8082/employee`
    - Get all employees: `GET http://localhost:8082/employee`
    - Get an employee by id: `GET http://localhost:8082/employee/{id}`
- to see Spring Eureka Service Registry: `http://localhost:8761/`    
- To see Zipkin: `http://localhost:9411/zipkin/`

