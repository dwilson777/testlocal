# Tracking Event Names

This topic provides a comprehensive list of tracking events transmitted by the player.  Each event has an associated payload.  The payload is described in detail in [Payload Reference](payload-tracking.md). 

The following events are tracked by the player.

| Event Name                | Occurrence                                                                                                                                                                         | Payload property details
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -----------------------------------------------------------
| Lifecycle Create          | When a new lifecycle got created through a content configuration (e.g. skipping to a different playlist item).                                                                     |
| Lifecycle Play            | When a play was requested successfully | `isStartedByUser (true or false)`
| Lifecycle Playreject      | When a lifecycle couldn't play automatically (e.g. on mobile) or was not meant to start automatically |
| Lifecycle Start           | When a lifecycle was succesfully prepared and is started. |
| Lifecycle Abort           | An existing lifecycle is destroyed when skipping to a different playlist item or the user left the current page. Either a `Lifecycle Abort` or a `Lifecycle End` must occur.       | `lifecycleAbortReason` must be provided
| Lifecycle End             | An existing lifecycle ended normally (with postroll = when postroll ends / without postroll = when content ends). Either a `Lifecycle Abort` or a `Lifecycle End` must occur.      |
| AdRoll Request            | When an ad-roll (e.g. pre-, mid-, postroll block) gets requested from an ad server.                                                                                                | `ad.rollIndex` and `ad.rollName` must be provided.
| AdRoll Start              | When an ad-roll contains at least one playable ad (no faulty or fallback ads) and it is pushed into playback.                                                                      | `ad.rollIndex` and `ad.rollName` must be provided.
| AdRoll End                | When the last ad of an ad-roll completed playback.                                                                                                                                 | `ad.rollIndex` and `ad.rollName` must be provided.
| Ad Begin                  | When a ad clip starts playing or ad image starts displaying.                                                                                                                       | `position` must contain the initial start position (mostly `0`) or `NaN` when no `duration`.
| Ad Complete               | When a ad clip is at the end or when ad image gets hidden.                                                                                                                         | `position` must match ad media's `duration`.
| Ad Omit                   | Unsold ad impression.                                                                                                                                                              | 
| Content Begin             | When a content clip starts playing or content image starts displaying.                                                                                                             | `position` must contain the initial start position (mostly `0`) or `NaN` when no `duration`.
| Content Complete          | When a content clip is at the end or when content image gets hidden.                                                                                                               | `position` must match content media's `duration`.
| Position Change           | When a position change happens on a particular clip (e.g. content / ad). Preferably provided at least every second.                                                                | `positionType` and `position` contain further details of a position change.
| Position Seek             | When a seek occurred on the current clip.                                                                                                                                          | `fromPosition` must be filled in.
| Viewtime Change           | When a named viewtime is reached on a clip. See special `Viewtime Change` events below that are required.                                                                          | `viewtimeType` and `viewtime` contain further details of a viewtime change
| Error                     | When an error occurred, which should be reported. Some errors will trigger a `Lifecycle Abort` event.                                                                              | An error classification must be provided within `errorType` and optionally an `errorCode` can be passed.
| Click                     | When a click occurred on the current clip (ad or content).                                                                                                                         |
| Pause                     | When a clip (ad or content) got paused.                                                                                                                                            |
| Play                      | When a clip (ad or content) got played.                                                                                                                                            |
| Fullscreen Change         | When the player was put into fullscreen or fullscreen was exited.                                                                                                                  | `isInFullscreen` indicates if fullscreen was entered or left.
| Volume Change             | When volume was changed or when the player got muted / unmuted.                                                                                                                    | `isMuted` and `volume` provide the current volume states.

### Required Viewtime Change events

| Position Type    | Description                                                                |
| -------------    | -------------------------------------------------------------------------- |
| `viewtimexplus`  | Emitted once when a content clip reaches a total of 3 minutes of viewtime. |


<a name="payload"></a>
