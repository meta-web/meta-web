## Issues of nowadays

I see following critical issues during development of web applications.

### Diverse and not understandable APIs

Various applications and web services are communication between each other using application interfaces - APIs. There are many different formats (JSON, XML) and various communication protocols such as REST or RPC. But when we want to integrate two applications together we must study and comply to their VARIOUS protocols, understand how they work and how to implement them.

It's such a babylonian problem. I'm sure that you were already heard that story about [Tower of Babel](https://en.wikipedia.org/wiki/Tower_of_Babel) where god punished people by diversifying their language. APIs are the same story. We need dictionaries (individual implementations) to be able to communicate between applications.

Each API has different ways to access data, various ways to call methods, various data structures, data types and so on. Developers must then write code almost for every service they want to integrate.

We have some standards of course but they are too narrow, such as OAuth.

### Complicated and difficult to develop user interfaces

Second main part of applications are user interfaces. We have many different platforms nowadays such as Windows, Linux, OSX, Android of iOS. Every platform is specific and if we want to create application for each of these platforms we have only few options. We can use some framework or library which provides to us an option to write applications once and compile it to all platforms. And we also have a WEB. Technology which is available to all platforms.

Personally, I see web as the best option to create multiplatform applications. But it has also many issues.

Web platform is universal and easy to understand at first look but If you dive into it you will find out that it is one big chaos. We have many languages such as HTML, CSS, JavaScript, their dialects (TypeScript, CoffeeScript, LESS) and many various frameworks (React JS, Angular). But all this is a one big problem. Working with web platform it's not simple and effective by itself. We need help of a lot of code.

Too much ado for a simple goal.

And what is our goal? Our goal is to create web applications which has many things in common - navigation, lists, images, text content, connection to data. So why we need tens of languages, frameworks and libraries to achieve something that simple? Old web on its own (I mean hypertext) was created for almost the same purpose. HTML supports content tags, images, forms, tables. Only issue is that these features (in its core) are obsolete. It's the reason why we need so much code.

But current frameworks for client side provides the same features as HTML - extended input validation, table filtering, displaying of live data, communication with server using API and preferably without reloading a page. Why a web platform cannot integrate these features in its base?

Finally, why we need to control a design when many web applications looks almost the same? They have same components, clear and simple design. And they look like desktop and mobile applications more and more compared to traditional web pages.

Another common issue of user interfaces (of applications either web pages) is their diversity. People have habits and they don't like changes. Historically navigations were placed always at left side of a web page. Nowadays primary navigation are being placed at top of pages. When you are presenting to people something they are not used to they have problems to work with it, to orient. Old or handicapped people for example, have problems to recognize a button if it looks different than native system component.

### Difficulty of application development and DRY rule

Many programmers know DRY rule (Don’t Repeat Yourself) which tells that we have to avoid repetition of same code to achieve more effective work and clarity of code.

But how reality look like? Let's use a simple application example. Image an address book app. It is a collection of records - contacts. Each contact has some fields - first name, last name, address, e-mail, phone and so on. This application consists of following parts:

- **Database** - classic application has a database where records are stored and where the record structure is defined - contact fields.
- **Application server** - next we have an application server which provides communication between database and user interface, it adds some logic and mainly it handles request validation - it validates contact fields. When client or an attackers sends an invalid request to a server it must return an error.
- **Web / mobile application** - user interfaces which provides as an ability to interact with the application. It consists of contact list, contact detail, add form, edit form etc... So in this part we have to specify all contact fields again.

What these parts have in common? Definition of contact fields. At each application part we need to specify all contact fields in a code. We have to define them in a database, in an application server and also in an user interface. So if we have 6 fields then we need to code them 18 times at 3 different places.

But their definitions are almost same at all places. We specify field's name, type (text / number / e-mail), validation rules, if it is mandatory, if it's linked to other records and so on.

So why we need to code this too much times? On a same schema we can create database structure, validate requests and also display and validate user interface fields.

Although we are trying to not to break DRY rule, current web technologies are forcing us to violate it.