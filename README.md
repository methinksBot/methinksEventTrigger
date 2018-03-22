## Create Event Trigger on iOS methinks project


When you run a longitudinal study on methinks, you can integrate event triggers which enables,

1. **Bookmarks** on video recording with timestamp so you can find exact spots of playback
2. **In-app question**, non-intursively asked pre-designed question for specific event when users experience is fresh



## Be aware!

Detect the right event is important. Please keep in mind situations for event trigger

1. Be aware **how often** the event called. If called too many, bookmark value would be low and testers might feel interuppted too much
2. Be sure to implement the trigger on **non active moment**. For example, when you are testing a real time PVP games, showing event trigger question will pause user's gameplay or end up unexpected errors. 

*We recoomed that you implement **less than 5 event tiggers for about 30 minutes' expected usage time** * 



## NSNotification


methinks uses `NSNotification`, a native iOS API which is **crash-free** and **no impact on performace**. Implementation is simple enough for 1 line of code. **No SDK implementation** needed.


## Usage


Use `event` value in `userInfo` to make your own event trigger. Make sure the value should be **unique**.
```objc
// Post a Notification using NSNotificationCenter
// Implement the code appropriate moment of the event, such as user just finished a tutorial.

[[NSNotificationCenter defaultCenter] postNotificationName:@"MT_EVENT_NOTIFICATION" 
                                                    object:nil
                                                  userInfo:@{@"event":@"tutorial finished"}];

// notification name is MT_EVENT_NOTIFICATION is predefined and use it as-is.
// Use your "easy to read" value for @"event" in userInfo

//Other example will be like

[[NSNotificationCenter defaultCenter] postNotificationName:@"MT_EVENT_NOTIFICATION" 
                                                    object:nil 
                                                  userInfo:@{@"event":@"achieve level 10"}];

[[NSNotificationCenter defaultCenter] postNotificationName:@"MT_EVENT_NOTIFICATION"
                                                    object:nil 
                                                  userInfo:@{@"event":@"finished first battle"}];

```

## In-app question

Once you implement event triggers on your app, please send corresponding question for each evnet trigger. For bookmark, you don't need to send question. Please contant your methinks account executive. 


