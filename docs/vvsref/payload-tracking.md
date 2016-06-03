# Tracking Event Payloads
The [Getting Started with Player Events](overview-tracking.md) chapter introduced you to player events that are tracked as well as the associated payload that is transmitted from the player.  This chapter looks at the Payload in more detail. Complete information about Payloads is provided below:

| Prefix       | Name                      | Description                                                                | Type           | Example                                           | Default     |
| ------------ | ------------------------- | -------------------------------------------------------------------------- | -------------- | ------------------------------------------------- | ----------- |
| **content.** |                         |   Contains the original contentResource                                      | [ContentResource](player-api#content-model.md) |                   | `null`      |
| **ad.**      | id                        | Ad identifier (separate by `-` into orderId, lineitemId, creativeId)       | String         | `"12345-67890-87654"`                             | `null`      |
|              | positionName              | Name of the displayed ad.                                                  | AdPositionName | `"preroll1b"`                                     | `null`      |
|              | rollName                  | Name of the displayed ad roll block.                                       | AdRollName     | `"preroll"`                                       | `null`      |
|              | rollIndex                 | Index of the ad roll block (e.g. midroll block at index 2).                | Number         | `2`                                               | `null`      |
| **runtime.** | mediaType                 | Marks the type of media that is tracked.                                   | MediaType      | `"ad"`                                            | `"content"` |
|              | technologyType            | Used playback technology of media (e.g. Flash, HTML5).                     | TechnologyType | `html5`                                           | `null`      |
|              | duration                  | Duration of the currently tracked media in seconds (ad or content).        | Number         | `3323.34`                                         | `0`         |
|              | position                  | Current position within current clip (ad or content) in seconds.           | Number         | `10.35`                                           | `0`         |
|              | fromPosition              | Where was seeked from?                                                     | Number         | `8.30`                                            | `null`      |
|              | positionType              | Can be filled when `Position Change` and can mark a special `Position Change` event. | PositionType | `"firstquartile"`                         | `null`      |
|              | contentViewtime           | Total viewtime of the content clip.                                        | Number         | `20.34`                                           | `null`      |
|              | viewtimeType              | Can be filled when `Viewtime Change` and marks a special `Viewtime Change` event. | ViewtimeType | `"viewtimexplus"`                            | `null`      |
|              | isInFullscreen            | Indicates if the player is in fullscreen.                                  | Boolean        | `true`                                            | `false`     |
|              | isMuted                   | Indicates if the player is muted.                                          | Boolean        | `true`                                            | `false`     |
|              | volume                    | Contains the currently set volume (0 = mute, 1 = full volume).             | Number(0-1)    | `0.53`                                            | `1`         |
|              | errorCode                 | Error code that explains the current runtime / creation error.             | String         | `'A specific Error'` or `'11'`                    | `null`      |
|              | errorType                 | Type of error                                                              | ErrorType      | `'socketconnection'`                              | `null`      |
|              | adBlockerState            | State of the AdBlocker detection.                                          | String         | `'ab'`, `'abx'`, `'noab'` or `'noabx'`            | `null`      |
|              | lifecycleAbortReason      | Reason of `Lifecycle Abort`                                                | LifecycleAbortReason | `mediaerror`                                | `null`      |
|              | playlistIndex             | Identifier on which position within a playlist a video is                  | Number         | `3`                                               | `null`      |
|              | playlistLength            | Full length of a playlist a video is running on                            | Number         | `5`                                               | `null`      |
|              | contentDeliveryNetwork    | Name of the CDN the content video file is delivered over                   | String         | `Akamai`                                          | `null`      |
|              | lifecycleId               | A GUID that identfies the current lifcecycle                               | String         | `abc-cde-fge`                                     | `null`      |
|              | adViewtime                | Played time of ads                                                         | Number         | `3`                                               | `123`       |
|              | adOmitReason              | Ad omit reason                                                             | String         | `503.101`                                         | `null`      |
|              | isStartedByUser           | If the play request was started by user or autoplay                        | Boolean        | `true`                                            | `false`     |
