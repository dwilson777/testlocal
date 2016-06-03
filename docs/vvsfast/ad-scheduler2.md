# Task List: Integrating the Ad Scheduler

Now that you are familiar with the AdScheduler object let's take a look at how you integrate it into your own code.  The [CopyCode: Integrating the AdScheduler](ad-integration.md) topic has a code sample that illustrates these steps.

## Integration Steps
Follow these steps to integrate the AdScheduler.

1. Create a Player Instance.

2. Create an AdScheduler Instance using the public interface methods described in [Using the AdScheduler](construct.md).

3. Introduce the AdSchedulerInstance to the Player instance e.g. by calling:  
`player.setAdScheduler(adScheduler);`

4. The Player can then call:   
`adScheduler.get(contentResource: Object, currentPlayerState: Object)` initially and use it for scheduling.

5. The player events are tracked and whenever certain events, such as `Pause` occur, the player triggers 
   `update(currentAdSchedule: Object, eventType: String, currentPlayerState: Object)`, which returns an updated Ad Schedule. See the Events chapter for more information about the various events that can occur.

6. When the playback end is reached, the player starts with a new content video, which triggers a fresh get on the AdScheduler (step 4 above).
  





