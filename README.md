## methinks Event Trigger (iOS only)
Integrating methinks event triggers in your app enables:

- **Bookmarks:** Add timestamps to the automatically recorded videos, allowing you to quickly find the most important video segments.
- **In-app Questions:** Ask predefined questions anywhere in the user flow.

## Caution
To gain the most authentic and meaningful feedback from your users, it’s strongly recommended to add event triggers in a non-intrusive way.

- **Frequency of events:** Too many events will annoy your users.
- **Time of events:** Interrupting in the middle of your user fighting a boss is never a good idea.

We recommend less than 5 event triggers within 30 minutes.

## NSNotification
methinks uses `NSNotification`, a native crash-free iOS API that has no impact on performance. Implementation is as simple as 1 line of code. No SDK implementation is needed.

## Usage
Use **unique** `event` value in `userInfo` to create your own event trigger. 

```objc
// Post a Notification using NSNotificationCenter
// The following example adds an event trigger at the time when users finish the tutorial
[[NSNotificationCenter defaultCenter] postNotificationName:@"MT_EVENT_NOTIFICATION" 
                                                    object:nil
                                                  userInfo:@{@"event":@"finished tutorial"}];

// The notification name MT_EVENT_NOTIFICATION is predefined. Please don’t change it.
// Use human-readable strings for @"event" in userInfo

// More examples
[[NSNotificationCenter defaultCenter] postNotificationName:@"MT_EVENT_NOTIFICATION" 
                                                    object:nil 
                                                  userInfo:@{@"event":@"achieved level 10"}];

[[NSNotificationCenter defaultCenter] postNotificationName:@"MT_EVENT_NOTIFICATION"
                                                    object:nil 
                                                  userInfo:@{@"event":@"finished first battle"}];

```

## In-app Question
Please provide methinks a list of questions you designed, one for each event trigger.

No question is needed for bookmarks. Please contact your methinks account executive.

