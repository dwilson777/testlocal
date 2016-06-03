# CopyCode: Calling the Player
Copycode topics provide code that you can copy into your own applications. The code provided her lets you initialize the loader and call both the glomex player or your own player.

## The Code: Starting Both Players<a name="example"></a>
The code sample below illustrates a typical implementation. In this example, the PLAYER-ID is `12345`. The player instance is named `myplayer`. After initializing `myplayer` it can be used to call valid Player API functions, such as  `AddContent()` and `play()`, as indicated in the code that is commented out below. 

``` html
<div id="playerNode"></div>
<script src="glomex-loader.js"></script>

<script>
  var domNode = document.getElementById('playerNode');
  glomex.init(domNode, '12345')
    .onGlomexPlayer(function(myplayer) {
      // myplayer.addContent(…)
      // myplayer.play()
    })
    .onPublisherPlayer(function() {
      // e.g. initialize the publishers own player
    });
  });
</script>
```

![Run](assets/runthiscode2.png)  ![Open](assets/opencode2.png)  ![View](assets/viewobject2.png) 


