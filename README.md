# META Web

Repository for the official site - [metahub.cloud](http://metahub.cloud/).

Concept of mechanisms to UNITE the WEB. Web application protocols and formats that puts meta-data and data into information meaning and united APIs.

## About META Web

The META Web open-source project aims to create a unified API structure for applications, services and devices and also to create a unified language to build multiplatform user interfaces.

Why? Because currently almost every application has its own API structure which cannot be automatically understood and we must integrate all APIs manually. Although we have the Swagger, JSON-LD and others they don't provide a unified structure to access data and services.

Our goal is to build one unified language so everything can be connected.

### The concept

A purpose of the META Web is to unify a way how applications and devices communicate so every service, client and device is able to understand each other effectively.

How can we achieve this goal? Firstly by specifying API structures for common use cases such as working with collections, individual records or how to invoke methods. Secondly an every META Web API resource must provide a meta document which describes its data model and capabilities in a machine readable and programmer friendly way.

Also building UIs is often time-consuming and inefficient. We aim to solve this issue by defining the unified UI language for all platforms.

## How to compile this documentation
```bash
npm install
npm run doc

#Same as doc but starts local server and watches for changes
npm run server
```
