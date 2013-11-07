# blackstone

# Usage

## Install
`npm install blackstone`

## Connector
The module can be connected using the following methods:

### define (AMD/Require.js)
```js
define(['blackstone'], function(blackstone){});
```
### require (Node.js)
```js
var blackstone = require('blackstone');
```
### window (DOM)
```js
window.Blackstone(lodash, async);
```
### global (Node.js)
```js
global.Blackstone(lodash, async);
```

# API
> Uses the prefix __ to indicate the system variables.
> Use the system variables with the understanding!

## .version = 'develop'

## .Events()
System of events.
```js
var events = new blackstone.Events;
```

Options describing the behavior of an instance of an event of default.

These options can be overridden when calling bind.
```js
events.__eventsSync = false; // events.bind option: sync
events.__eventsSelf = false; // events.bind option: self
events.__eventsLimit = null; // events.bind option: limit
events.__eventsAll = '*'; // The event name is called when any event.
events.__events = {}; // An object with reference to the first handler for each event.
```

### .__index = 0
> The system variable. Use with understanding.

A unique index for each event handler created blackstone.

### .unbind(Object events, String name, Object handler)
The withdrawal of the handler chain of handlers.

### .Self(Object events, String name, Object handler)
The constructor of the object `self`.

#### .index

#### .limit()
Returns the current limit call handlers.

#### .limit(limit)
Sets a new limit handler and returns it.

#### .unbind()
Detach this handler.

### Object events instanceof .Events

#### .bind(String name, Function callback[, Object options])
Set the handler to the handler chain.

##### Default options
```js
context: events,
sync: events.__eventsSync,
self: events.__eventsSelf,
limit: events.__eventsLimit
```

#### .unbind([Object query])
Removes handlers of the handler chain as per request.

##### Default options
```js
name: lodash.isString(query.name)? query.name : undefined,
context: !lodash.isUndefined(query.context)? query.context : undefined,
callback: lodash.isFunction(query.callback)? query.callback : undefined,
sync: lodash.isBoolean(query.sync)? query.sync : undefined,
self: lodash.isBoolean(query.self)? custom.self : undefined,
limit: lodash.isNull(query.limit) || lodash.isNumber(query.limit)? query.limit : undefined
```

* If you do not submit a query will delete all the handlers of all events.
* If you pass only the name of the event, will remove all handlers for this event.
* The remaining options specify the search.

#### .trigger(String name[, Array args[, Function callback]]) or .trigger(String name[, Function callback])
Trigger all event handlers by name.

Function `callback` will be called after all the event handlers.

## .Type([Object attributes])
Returns the object which received type behavior.

The resulting type is used for the assembly item.

Inherit behavior blackstone.Events.

### .inherit([[Object args, ]Function callback])
Inherit a new type of this type.

### .__index = 0
> The system variable. Use with understanding.

A unique index for each type created blackstone.

### Object type instanceof .Type

#### .__findAllTypes()
> The system variable. Use with understanding.

Created to find all types of parenting including the source.

Returns an object of the search results.

##### Results example
```js
{
    byOrder: [],
    byIndex: {}
}
```

#### .new([[Array args, ]Function callback])
Creates an instance of the item from the instance type.

Merges all the prototypes of all the parent types.

Assigns the unique index.

Sets a reference to a type constructor.

Space for behaviors.

If there is a designer, call it in the context of the item.

Call the behavior of all types of parenting in the context of the item.

Call the event `new` only this type.

The callback function will be called when the operation of all handlers.

#### .instanceof(Type, Type, Type...)
Check chain types.

#### .inherit([[Object args, ]Function callback])
Inherit a new type of this type.

Call the event `inherit` only this type.

#### .as(name, behavior[, Object options])
Describes the behavior within the type.

## .Item()
Not intended for custom build!

Available for the possibility to check the inheritance.

### .Item.__index = 0
A unique index for each type created blackstone.

> The system variable. Use with understanding.

### Object item instanceof .Item

#### .as(String behavior)
Easy way get behavior.

#### .instanceof(Type, Type, Type...)
Check chain types.

## .Document instanceof Type
Type with special abilities inherent in the documents.

### document of blackstone.Document

### .get([Function callback])
Always returns the document.

If passed argument callback, it will be launched after the event `get`.

### .set(Object data, [Function callback])
Always returns the item of document.

Merge the argument `data` and `.__document`.

If passed argument callback, it will be launched after the event `set`.

### .reset(Object data, [Function callback])
Always returns the item of document.

Replaces the old `.__document` on a new argument `data`.

If passed argument callback, it will be launched after the events `set` and `reset`.

### .unset([Function callback])
Always returns the item of document.

Replaces the old `.__document` on a `{}`.

If passed argument callback, it will be launched after the events `set`, `reset` and `unset`.