# Using the AdScheduler

This topic describes how to use the AdScheduler object.


## Creating an AdScheduler
The public interface to the `AdScheduler` consists of a `constructor()` method as well as a `get()` and `update()` methods:
```js
AdScheduler { 
  constructor(config: Object, dependencies: Object), 
  
  get(contentResource: Object, currentPlayerState: Object)
    => adSchedule: Object | promisedAdSchedule: Promise ,
     
  update(currentAdSchedule: Object, event: Object, currentPlayerState: Object) 
    => updatedAdSchedule: Object | promisedUpdatedAdSchedule: Promise 
}
```
## AdScheduler Parameters

There are two crucial parameters in the code above which are described in more detail below.

### The dependencies Parameter

The second parameter passed to the constructor method is `dependencies`. Valid dependencies are:

| Dependency                                   | Description
| -------------------------------------------- | -------------
| `fetchHidden(src: String, handler: Function)`| Provides a method to load sources in a hidden way in the AdBlocker case. `handler` gets called with `(null, {content})`, the content of the requested file, or `(error)` if the loading failed.

### The currentPlayerState Parameter

Describes player state, which gets passed to the `get` and `update` method calls.

| Name           | Description                          | Type           | Example  | Default                  | Origin                            |
| -------------- | ------------------------------------ | -------------- | -------- |------------------------- | --------------------------------- |
| `isAdBlock`    | Transmits the AdBlocker state        | Boolean        | `true`   | `false`                | VideoPlayer                       |
| `isInFullscreen` | Transmits the Fullscreen state       | Boolean        | `true`   | `false`                | VideoPlayer                       |
| `timestamp`    | Transmits the current playback time as timestamp | Timestamp | `1458550174330` | `null`          | VideoPlayer                       |





