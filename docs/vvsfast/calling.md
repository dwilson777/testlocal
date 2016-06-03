# Loading and Calling the Player
Let's start with some VVS Player basics. This chapter covers key information about the player such as the .js file that the code is stored in and the PLAYER-ID which is a unique identifier for players. It also covers how to initialize and start the player. To view a complete code sample, see [CopyCode: Calling the Player](callcode.md).

## The glomex-loader.js File

The primary loading code for the VVS Player is defined in a single JavaScript code file: glomex-loader.js. After including this file in your `<script src>` parameter at the top of your own JavaScript code file, you then initialize the VVS Player by calling `glomex.init` with a PLAYER-ID parameter.

## The PLAYER-ID Parameter
Each individual player configuration is identified by a PLAYER-ID. The ***Glomex Self-Service-Tool*** is used to configure various players. Before you initialize a player, decide which player configuration you wish to use and write down its PLAYER-ID. You will need it when you initialize the player.

## Initializing both Players: glomex.init

To initialize the VVS Player, you call the `glomex.init` method and pass it the PLAYERID as the second parameter:

`glomex.init(domNode<DomNode>, identifier<PLAYER-ID>)`

This returns an object with two functions: 

* onGlomexPlayer
* onPublisherPlayer

These two functions allow the registration of callbacks. Based on the configuration settings in the player, either the onGlomexPlayer or onPublisherPlayer is triggered based on certain events.

### Starting the Glomex Player

This function starts the Glomex Player: `onGlomexPlayer(callback<Function>)`<a name="on-glomex-player"></a>

The callback will be called with the [Player Methods: General](../vvsref/api.md) instance as the first argument. For further information visit the dedicated [Player Methods: General](../vvsref/api.md) topic.

### Starting the Publisher Player

This function starts the Publisher's Player: `onPublisherPlayer(callback<Function>)`<a name="on-publisher-player"></a>

The callback will be called without any arguments.
