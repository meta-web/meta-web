## Two-layer principle

Two-layer principle is based on idea to separate data and meta-data.

MetaWEB types are descriptive so they are describing behaviour of resources but are not containing data.

Data are fetched from external resources but MetaWEB types are specifying where to find them and how to represent them.

### Basic example

Imagine that we have database of customers. MetaWEB describes customer properties and actions (first layer) and it also specifies URL of data (second layer).

User requests MetaWEB resource and browser figures out where data are located. Browser then loads these data and displayes them as specified.

If datasource supports Web events then browser can listen to data changes and updates them in real-time.