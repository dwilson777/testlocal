# CopyCode: Integrating the AdScheduler

Now that you are familiar with the AdScheduler and the basics of how to integrate it into your player we can walk you through a full code example to illustrate how to set up your own code.


## Overview of the Code Sample
The example below starts by instantiating a `player`, `adScheduler` and `contentResource` in the usual way.  The `contentResource` is then added as content to the player and the player starts with `play`. Within the player, the `get()` method returns a `currentAdSchedule`.  Sample code is also provided for the case where the user triggers a pause event. If the user pauses, the `update()` method is called and the `updatedAdSchedeule` replaces the `currentAdSchedule`. Finaly, if the player reaches the end of playback and starts with a new video the `get()` method is used again to replace the previous Ad Schedule with `currentAdSchedule`.

## CopyCode
![Run](assets/runthiscode2.png)  ![Open](assets/opencode2.png)  ![View](assets/viewobject2.png) 


```js
var player = new Player();
var adScheduler = new AdScheduler();

player.setAdScheduler(adScheduler);

var contentResource = {
  id: '12345',
  duration: 120,
  formatName: 'myFormat'
};
player.addContent(contentResource);
player.play();

// --- WITHIN THE PLAYER ----
....
var currentPlayerState = {
  isInFullscreen: false,
  isAdBlock: false
};

adScheduler.get(contentResource, currentPlayerState).then(function(currentAdSchedule) {
  /* 
   * player reads returned timed positions, so that it can trigger ad-fetching 
   * and -rendering, when those positions got reached 
   */
});

// User triggers Pause Event
var timestamp = currentPlayerState.timestamp = Date.now();
var event = {type: 'Pause'};
adScheduler.update(currentAdSchedule, event, currentPlayerState).then(function(updatedAdSchedule) {
  /* 
   * Player uses the updatedAdSchedule as currentAdSchedule.
   * When the updated Ad Schedule contains an entry for that 
   * timestamp it starts to fetch and render the ad.
   */
});

// Player reaches the end of the playback and starts with a new content video
adScheduler.get(contentResource, currentPlayerState).then(function(currentAdSchedule) {
  /* 
   * Player replaces the previous Ad Schedule with the new currentAdSchedule
   */
});
...
// --- End: WITHIN THE PLAYER ----
```

