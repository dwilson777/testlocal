# Player Methods: General

This chapter provides a list of commonly used public functions provided by the VVS Player. The exception being the `addContent` and `removeContent` functions which are a bit more sophisticated than most so they have their own chapter: [Player Methods: Adding and Removing Content](addcontent.md).

## Basic Control Methods

### `play()`

Starts the playback.

### `pause()`

Pauses content and ads.

### `destroy(callback<Function>))`

Destroys this player instance.
Callback will be called with no arguments when the player instance was destroyed.
The callback is optional.

## Playlist Methods

### `onPlaylistIndexChange(callback)`

Detect when a playlist changed. 
Callback will be called with: `callback({playlistIndex: 0})`.

### `onContentPositionChange`

Calls the callback with the current position of a content video.
Callback will be called with current position (in seconds): `callback({position: 234})`.

### `skipToPlaylistItem(playlistIndex)`

Skips to a particular playlist item.

## Ad Methods

### `setAdScheduler(adScheduler)`

Provides a mechanism to set the `adScheduler` for the player instance. For more information, see [Ad Scheduler](ad-scheduler.md).

### `onLinearAdRollStart(callback)`

Detects when an ad block starts. Callback will be called with: `callback({rollName: 'preroll', rollIndex: 0})`.

Valid values for the `rollName` parameter are:

* preroll
* midroll
* postroll

Valid values for `rollIndex` are:

* 0
* 1
* 2

Note that the value is always 0 for a preroll and postroll.


### `onLinearAdRollEnd(callback)`

Detects when an ad block ends. Callback will be called with: `callback({rollName: 'preroll', rollIndex: 0})`.

Valid values for the `rollName` parameter are:

* preroll
* midroll
* postroll

Valid values for `rollIndex` are:

* 0
* 1
* 2

Note that the value is always 0 for a preroll and postroll.

## Tracking Methods

### `on(eventName, callback)`

Provides a mechanism to listen for player-related events. To implement a custom tracker, see [Tracking](tracking.md).

### List of on() events

| name | arguments | description |
|---------------|---------|------|
|`trackingevent`|`trackingEventName`, `payload`|Gets triggered for all tracking related events|

## User Methods

###`requestFullscreen()`

Requests fullscreen. This can only be triggered by a user. For example:

```js
var domElement = document.getElementsByClassName('k-player')[0];
domElement.addEventListener('click', function() { player.requestFullscreen() }, true);
``

**CAUTION!**: This function call will only work in HTML5.  It does not work in Flash.


