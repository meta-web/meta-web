## Issues of today

I see the following web applications development issues as critical.

### Diverse and incomprehensible APIs

Various applications and web services communicate with each other using application interfaces - APIs. There are many different formats (JSON, XML) and various communication protocols such as REST or RPC. But when we want to integrate two applications we must study and comply with their VARIOUS protocols, understand how they work and how to implement them.

It's such a Babylonian problem. I'm sure that you have already heard the story about the [Tower of Babel](https://en.wikipedia.org/wiki/Tower_of_Babel) where god punished people by diversifying their language. APIs represent similar story. Applications need dictionaries (individual implementations) to be able to communicate with each other.

Each API has different ways to access data, various ways to call methods, various data structures, data types and so on. Subsequently, developers must write code for almost every single service they want to integrate.

We have some standards of course but they are too specific, such as OAuth.

### Complicated and difficult to develop user interfaces

User interfaces represent the second main part of applications development. Nowadays, there are many different platforms such as Windows, Linux, OSX, Android or iOS. Every platform is specific and if we want to create applications for each of these platforms we have only a few options. We can use some framework or library which provides an option to write applications once and compile them for all platforms. And we also have the WEB. A technology which is available to all platforms.

Personally, I see the web as the best option to create multiplatform applications. But there are many issues as well.

The web platform is universal and easy to understand at first sight, but if you submerge in it you will see that it is a true mayhem. There are many languages such as HTML, CSS and JavaScript (with their dialects: TypeScript, CoffeeScript, LESS), and various frameworks such as React JS or Angular. That means that working with the web platform only is not simple and effective. If we want to simplify work with the web platform we need to use a lot of code.

Too much ado for a simple goal.

And what is our goal? Our goal is to create web applications which have many things in common - navigation, lists, images, text content, connection to data. So why do we need tens of languages, frameworks and libraries to achieve something that simple? The old web itself (I mean hypertext) was created for almost the same purpose. HTML supports content tags, images, forms, tables. The only issue is that these features in themselves (in the core of HTML) are insufficient. This is the reason why we need so much extra code.

But the current frameworks for the client side provide similar features as HTML - extended input validation, table filtering, displaying of live data, communication with server using API and preferably without reloading a page. Why cannot the web platform integrate these features into its codebase?

Finally, there is the issue of design. Many web applications look almost the same so why bother? They have the same components, a clear and simple appearance. This fact results in traditional web pages increasingly looking like desktop and mobile applications.

Another common issue of user interfaces (of both applications and web pages) is their diversity. People are creatures of habit and they don't like change. Historically, navigations were always placed on the left side of a web page. Nowadays, primary navigations are being placed at the top. When you present something people are not used to they have difficulty working with it. The elderly or the handicapped, for example, find it hard to recognize a button if it looks different from the native system component.

### Application development complexity and the DRY principle issues

Many programmers know the DRY principle (Don’t Repeat Yourself) which says that we have to avoid repetition of the same parts of code to achieve more efficient work and clarity of code.

But what does the reality look like? Let's use a simple application example. Imagine an address book app. It is a collection of records - contacts. Each contact consists of several fields - first name, last name, address, e-mail, phone number and so on. There are the following parts of this application:

- **Database** - a standard application has a database where records are stored and where the record structure is defined - contact fields.
- **Application server** - next we have an application server which enables interaction between the database and the user interface. It adds some logic and most importantly it handles request validations - it validates contact fields. When a client or an attacker sends an invalid request to the server it must send an error response.
- **Web / mobile application** - user interfaces which provide ability to interact with the application. It consists of a contact list, a contact detail, an add form, an edit form, etc. So in this part we have to specify all contact fields again.

What do these parts have in common? The definition of contact fields. In each application part we need to specify all contact fields in code. We have to define them in the database, in the application server code and also in the user interface. So, if we have 6 fields then we need to code them 18 times at 3 different application parts.

But their definitions are almost the same at all the parts. We specify the field's name, its type (text / number / e-mail), validation rules, if it is mandatory and if it's linked to other records and so on.

So why do we need to code this so many times? We actually don't. First we can create a shared record definition which enables us to create a database structure, validate requests and also display and validate user interface fields.

Although we try not to break the DRY principle, the current web technologies are forcing us to violate this principle.