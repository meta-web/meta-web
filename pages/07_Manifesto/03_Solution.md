## Solution? The META Web

The goal of the META Web is to find a solution to the previously mentioned issues.

The META Web concept consists of:

1. **META API** - the goal is to define united and general API for communication between web services, user interfaces and servers.
2. **META UI** - the goal is to define universal markup language which will provide a tool to build user interfaces with simplicity and without the need for breaking the DRY principle and without the need to use various frameworks and redundant code.
3. **META Script** - the goal is to create simple scripting language (something like table processor expressions) which will allow dynamic evaluation of data at META UI layer.
4. **META Dictionary** - the goal is to define a common dictionary of standard objects, properties and types - may be based on [schema.org](http://schema.org).

### META API

The goal of the generic META API protocol is to define a universal and common way how to describe web services and how to communicate between them thus providing an effective tool for integration and to avoid the Babylonian problem.

META API consists of:

- Schema definition
- Request / response formats

The schema definition describes service resources, its properties, capabilities and methods. Schema also consists of descriptive properties thus allowing other services, developers and user interfaces to understand the service data model.

We already have similar projects which address the same issue as Swagger, WSDL, Hydra or JSON-LD but it will be difficult to integrate them into the META Web concept.

### META UI

The goal of META UI markup languages is to provide mechanisms for effective development of multiplatform user interfaces.

The META UI document defines the application view. For example a collection of contacts or contact detail. It also adds the navigation layer.

META UI defines:

- **Data source** - where to get data and how to store them.
- **Visual components** - how to present data to a user.

It's not anything unusual. But the effect comes with integration with META API. When we define the connection to META API data source we already have a description of the data model available. So we know which properties the resource has - with the contact app example we automatically know that our contact record has a first name, last name, we know how to label these properties, which type they are, how to validate them or how we can filter contacts collection and so on.

So in the META UI we don't need to define fields and columns anymore, which allows us to avoid breaking the DRY principle. Also when we change the data model on a server then these changes will be automatically reflected on the client-side application without any reprogramming.

The only thing we have to deal with is a UI layout. The META UI allows us to define composition of view components, which I think is everything we need on a the client side.

### META Script and META Dictionary

I will describe these parts another day.

