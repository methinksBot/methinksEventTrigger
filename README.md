## methinks Event Trigger (iOS only)
Integrating methinks event triggers in your app enables:

- **Bookmarks:** Add timestamps to the automatically recorded videos, allowing you to quickly find the most important video segments.
- **In-app Questions:** Ask predefined questions anywhere in the user flow.
- **Custom Log:** Log any custom logs in native iOS key-value pairs.

<br>
<br>

## Caution
To gain the most authentic and meaningful feedback from your users, it’s strongly recommended to add event triggers in a non-intrusive way.

- **Frequency of events:** Too many events will annoy your users.
- **Time of events:** Interrupting in the middle of your user fighting a boss is never a good idea.

We recommend less than 5 event triggers within 30 minutes.

<br>
<br>

## Use native `NSNotification`
methinks uses `NSNotification`, a native crash-free iOS API that has no impact on performance. Implementation is as simple as 1 line of code. No SDK implementation is needed.

<br>
<br>

## Usage - Event Trigger
Use **unique** value for `event` key in `userInfo` to create your own event trigger. Make sure that the notification name is `MTK_EVENT_NOTIFICATION`  

<br>
<br>

Obj-C


```objc
// Post a Notification using NSNotificationCenter
// The following example adds an event trigger at the time when users finish the tutorial
[[NSNotificationCenter defaultCenter] postNotificationName:@"MTK_EVENT_NOTIFICATION" 
                                                    object:nil
                                                  userInfo:@{@"event":@"finished tutorial"}];

// The notification name MT_EVENT_NOTIFICATION is predefined. Please don’t change it.
// Use human-readable strings for @"event" in userInfo

// More examples
[[NSNotificationCenter defaultCenter] postNotificationName:@"MTK_EVENT_NOTIFICATION" 
                                                    object:nil 
                                                  userInfo:@{@"event":@"achieved level 10"}];

[[NSNotificationCenter defaultCenter] postNotificationName:@"MTK_EVENT_NOTIFICATION"
                                                    object:nil 
                                                  userInfo:@{@"event":@"finished first battle"}];

```

<br>

Swift 3,4,5


```swift

NotificationCenter.default.post(name: NSNotification.Name(rawValue: "MTK_EVENT_NOTIFICATION"),
                              object: nil,
                            userInfo: ["event": "finished tutorial"]) 

```

<br>
<br>


## Usage - Cusstom Log
Use standard key-value pair for custom log. Make sure that the notification name is `MTK_CUSTOM_LOG_NOTIFICATION`

<br>
<br>

Obj-C


```objc

[[NSNotificationCenter defaultCenter] postNotificationName:@"MTK_CUSTOM_LOG_NOTIFICATION" 
                                                    object:nil
                                                  userInfo:@{@"freq":@(201)}];


[[NSNotificationCenter defaultCenter] postNotificationName:@"MTK_CUSTOM_LOG_NOTIFICATION" 
                                                    object:nil
                                                  userInfo:@{@"frames":@[@(12),@(34),@(56),@(78)]}];

```

<br>

Swift 3,4,5

```swift

let customLog:[String: Int] = ["freq": 201]
NotificationCenter.default.post(name: NSNotification.Name(rawValue: "MTK_CUSTOM_LOG_NOTIFICATION"),
                              object: nil,
                            userInfo: customLog) 


let customLog:[String: [Int]] = ["frames": [12,34,56,78]]
NotificationCenter.default.post(name: NSNotification.Name(rawValue: "MTK_CUSTOM_LOG_NOTIFICATION"),
                              object: nil,
                            userInfo: customLog) 


```

<br>
<br>
<br>

## In-app Question
Please provide methinks a list of questions you designed, one for each event trigger.

No question is needed for bookmarks. Please contact your methinks account executive.

