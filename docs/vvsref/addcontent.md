# Player Methods: Adding and Removing Content
Two functions of the player let you add and remove content:

* `addContent()`
* `removeContentAt()`

These two functions are decribed below along with the corresponding data model and valid source values for the `addContent()` method. For additional functions of the player, see [Player Methods: General](api.md).


## The addContent Method

The addContent function can be called with up to two parameters.  The second parameter is optional:

 `addContent(contentResource[, index])`

This method provides a mechanism to add a `contentResource` to a playlist.
The index can be optionally passed to add a `contentResource` at a specific position.



## The removeContentAt(index) Method

Provides a mechanism to remove a `contentResource` from the playlist by passing the playlist `index` on which the `contentResource` should be removed.

