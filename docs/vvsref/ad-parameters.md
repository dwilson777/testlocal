# Player Events Related to Ad Scheduler

This topic describes player events related to the AdScheduler.  It focuses on the `get()` and `update()` methods of the AdScheduler.

## The get() and update() Methods

The `get()` and `update()` methods of the AdScheduler do the bulk of the work in terms of ad scheduling.  Fundamentally, get() returns an AdSchedule independent of user events.  Whereas update() returns a new AdSchedule based on user events. The `get()` and `update()` methods are described in more detail in the table below:

| Method   |  Description
| ---------|  -------------
| `get`    |  Returns an initial Ad Schedule object or an Ad Schedule object as a promise. Called before new content starts to get played back. 
| `update` |  Returns an updated Ad Schedule object or an Ad Schedule object as a promise. `update` gets called for the events listed below.


##Events (updateAds)
These events results in the `update` method being called:

| Name                    | Description (gets triggered when ...)         | Category (See Event Categories below)   |
| ----------------------- | --------------------------------------------- | ------------------------------------------------------- |
| `metadatareceived`     | Player receives new MetaData (e.g. from stream).                | Extending/Updating                      |
| `fullscreenchanged`    | The fullscreen state changed.                  | Updating                                                 |
| `pause`                 | "Pause" was triggered through player.                    | Extending/Updating                            |
| `adresourceresolved`   | The Player resolved an AdResource from VAST.   | Updating                                                |
| `adblockerstatechanged` | The AdBlocker state has changed.               | Updating                                                |
| `vmapresolved`         | The Player resolved a VMAP.                    | Updating                                                |

##Event Categories

Events expect special behaviour by their call site, so they are categorized in the following classes:

| Category                | Description         
| ----------------------- | --------------------------------------------- 
| Extending               | The AdScheduler has the opportunity to add a new position schedule to the given `currentPlayerState.timestamp`. When something gets added at the given position the call site will start interpreting it.            
| Updating                | The AdScheduler has the opportunity to fully update the given Ad Schedule.


##The Event Object

An Event object is passed to `update`:

| Name           | Description                          | Type           | Event    | Example  | Default                  | Origin                            |
| -------------- | ------------------------------------ | -------------- | -------- | -------- |------------------------- | --------------------------------- |
| `type`       | The event type | String         | always | `{type: 'Pause'}` | `undefined` | VideoPlayer   |
| `metadata`       | Transmits Metadata coming in e.g. from a live stream [See: Metadata Model](#metadata) | Object         | `metadatareceived` |  `{name: adSingleMidroll}` | `undefined` | Meta Data -> VideoPlayer   |
| `resolvedAdPosition` | Transmits the pointer to the last resolved AdResource | Object         | `adresourceresolved` | `{position: 'start', tagIndex: 0}` | `undefined`              | VideoPlayer        |
