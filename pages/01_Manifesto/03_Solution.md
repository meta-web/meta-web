## Solution? The META Web

Goal of the META Web is to find a solution to previously mentioned issues.

META Web concept consists of:

1. **META API** - goal is to define united and general API for communication between web services, user interfaces and servers.
2. **META UI** - goal is to define universal markup language which will provide a tool to build user interfaces with simplicity and without a need to break DRY rule and without a need to use various frameworks and redundant code.
3. **META Script** - goal is to create simple scripting language (something like table processor expressions) which will allow dynamic evaluation of data at META UI layer.
4. **META Dictionary** - goal is to define common dictionary of standard objects, properties and types - may be based on [schema.org](http://schema.org).

### META API

Goal of the generic META API protocol is to define universal and common way how to describe web services and how to communicate between them thus providing an effective tool of integration and to avoid babylonian problem.

META API consists of:

- Schema definition
- Request / response formats

Schema definition describes service resources, it's properties, capabilities and methods. Schema also consists of descriptive properties thus allowing other services, developers and user interfaces to understand service data model.

We already have similar projects which are addressing this issue such as Swagger, WSDL, Hydra or JSON-LD but it will be difficult to integrate them to the META Web concept.

### META UI

Goal of META UI markup languages is to provide mechanisms for effective development of multiplatform user interfaces.

META UI document defines application view. For example collection of contacts or contact detail. It also adds navigation layer.

META UI defines:

- **Data source** - where to get data and how to store them
- **Visual components** - how to present data to a user

It's not anything unusual. But the force comes with integration with META API. When we define connection to META API data source we already have description of data model available. So we know which properties resource has - in case of contact we automatically know that our contact has first name, last, name, how to label this properties, which type are they, how to validate them, how we can filter contacts collection and so on.

So in META UI we don't need to define fields and columns anymore which allows us to avoid breaking DRY rule. Also when we change a data model on a server then these changes will be automatically reflected on a client side without any reprogramming.

Only thing we have to control is a UI layout. META UI allows us to define composition of view components which I think is everything we need on a client side.

### META Script and META Dictionary

I will describe these parts another day.

