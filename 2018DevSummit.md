



# Lighting Talks

## Push Notifications: An India Perspective
[Youtube](https://www.youtube.com/watch?v=RPQsW-dEpxY&index=7&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- India = 340M smartphone users, 16% YoY growth
- use longer "time to live" parameters
  - data $$$; most users turn data off
  - if your "time to live" param for a push notification is short & data is off, it never gets delivered
  - by switching from 4h --> 8h, you're much likelier to overlap w WiFi coverage
- use collapsible keys
  - (like everywhere) if apps have too many notifications, users turn them off
- 3 "jugaad" design patterns for better delivery
  - bucketing notifications
    - job periodically runs, refreshes FCM token, sends to server, server keeps a user FCM token mapping along w recency of update
    - you can better calculate which users would get/react to the notification
  - heartbeat-based pull
    - checks whether a notification was delivered from the last run; if not, go to a REST service, pull the notification, then display
    - can wake up device so not most effective/efficient
  - data messages w schedule
    - ex: sale today --> instead of sending it at midnight the day of, send it 2 days in advance (w 2 days time to live)
    - then schedule a job to show notification at the right time

## Building Reliable Apps When Connectivity Is Unreliable
[Youtube](https://www.youtube.com/watch?v=YWiRef3wOYY&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=10)

- connectivity is complex but you gotta hide that from the user
- esp. important for: communication apps, gaming, voice input, realtime content, media delivery
- need protocols that can migrate existing streams to a new network w/o waiting for Android to change default network
- Cronet
  - Chrome's networking stack packaged into a library
  - cross-platform support
  - will be soon part of Play Store
    - no need to bundle it in your own app
    - auto security updates
  - goal: release every 6 weeks
- QUIC
  - new transport (vs TCP which is 5+ years); included in Cronet
  - can seamlessly migrate Wifi <--> cellular

## Kotlin + Watch Faces
[Youtube](https://www.youtube.com/watch?v=lRiYvQbKoiY&index=6&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- Kotlin DSL (Domain-Specific Language)
  - type checking
  - code hints
- chained method calls
- nesting of lambdas
  - easily understandable for making watchfaces
  - [code lab](https://codelabs.developers.google.com/codelabs/watchface-kotlin/index.html?index=..%2F..%2Fio2018#0)

## Draw Me a Rainbow: Advanced VectorDrawable Rendering
[Youtube](https://www.youtube.com/watch?v=Uz99np2Hat4&index=12&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- vectors = sharp, small, flexible
  - good for animations
- [theme colors](https://developer.android.com/reference/android/graphics/drawable/VectorDrawable#applyTheme(android.content.res.Resources.Theme)
  - ex: logo --> apply as tint at runtime; better than SVG
  - use colorPrimary to color certain parts of the vector image
- [ColorStateList](https://developer.android.com/reference/android/content/res/ColorStateList)
  - ex: highlighting --> change rendering based on state
  - useful is rendering is 99% same between states
- [Gradients](https://developer.android.com/reference/android/graphics/drawable/GradientDrawable)
  - you can embed item tags inside gradients to define individual color stops; ex: 72% of the way
  - use by:
    - defining gradients in a color resource directory
    - or use the inline resource syntax to embed it inside the vector definition itself
    - at build time, APT will extract that to a color resource and insert a reference to it for you
  - ex: adaptive icons --> vectors don't support drop shadows but you can fake it
  - ex: customized spinners

## 3 Platforms in 5 Minutes with Kotlin
[Youtube](https://www.youtube.com/watch?v=0-HpOUwbp5w&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=11)

- ...

## Optimizing User Flows through Login
[Youtube](https://www.youtube.com/watch?v=dbMxvTG0KEU&index=5&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- ~1/2 your users will get new phones this year, will reinstall your app; try to give them a seamless experience
- Google Sign-in - good for activation & reactivation
- Smart Lock for passwords - ditto
  - Netflix = 20% fewer support requests
- AutoFill
  - can save username/password
  - if you set up digital asset link from your website to your app, your users will get their credentials transferred seamlessly
  - use AutoFill hints
- Auto Backup
  - back up device-specific settings
  - save which tutorials the user completed
  - up to 25 MB
  - you can include/exclude specific files

## Understand the impact of Generic System Images (GSI)
[Youtube](https://www.youtube.com/watch?v=Y-HmCIHD63w&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=8) • [Documentation](https://developer.android.com/topic/generic-system-image/) • [More Documentation](https://source.android.com/setup/build/gsi)

- purest form of Android Framework built from AOSP
- critical component in Treble compliance
  - Trebels separates the AndroidOS framework and the vendor implementation (?)





# New Features, Different Forms, etc.

## Is Your App Ready For Foldable Phones?
[Youtube](https://www.youtube.com/watch?v=UwEyK5WATFA&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=37)

- Multi-resume: resuming all top visible activities in multi-window
- How to opt-in (P only): 
  <meta-data> <android:name="android.allow_multiple_resume ..."> true
- Multi-Display
  - starting from O, activity can be launched in non-default .. ?
- to test: emulator available @ developer.samsung.com/galaxy/foldable(Q4)

## What's New for App Developers in Android Auto

[Youtube](https://www.youtube.com/watch?v=flRK5mWMPns&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=21)

- Media Template Architecutre
  - MediaBroswerService
    - provide a browse tree: onLoadTree
    - recommend only provide two levels of trees
  - MediaSessionService
    - playback control
  - onSearch
    - google assistant provide a the result (or query) back to the app?
    - UniversalMediaApp, MediaController
    - can annotate the item (category), auto can group them together
    - EXTRA_IS_DOWNLOADED (can show in the description)
    - Have Grid View

## Developing for Android & Large Screens
[Youtube](https://www.youtube.com/watch?v=H3_P3HJb-4M&index=23&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- Design
  - Design for input mediums other than touch (touch surfaces vs. keyboard etc.)
    - UX patterns are different for non-touch devices
    - view.setOnContextClickListener
    - view.setOnHoverListener
- Window Management
  - Jetpack helps with this!
  - Your app will not always be in focus (multi-window)
  - Take advantage of the features on different platforms
- Tooling
  - Android Studio Integrations
    - lint additions coming soon
  - Chrome OS emulator





# UX Improvements

## Modern Android Notifications
[Youtube](https://www.youtube.com/watch?v=_4vq2Cs_bKg&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=32)

- Respect your user's attention
  - respect user's settings
  - send well-structured notification
  - relevant and timely
  - don't send notifications that are not actionable
  - don't just send and forget
- Give user control
-Notification channels
  - don'ts: only use one or too many channels
  - Feedback from users
    - broadcast blocking state for channel, channel group and app
- What else is new on Android
- Digital Wellbeing
  - User visible notifications
- Work wit Do Not Disturb
  - exceptions: alarm, reminder, ....

## Best Practices for Themes and Styles
[Youtube](https://www.youtube.com/watch?v=sNSlDfaNq-0&index=44&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- pre-defined theme color with meaningful name, instead of just dex code 
  - primary, primary variant, primary light, Error, OnPrimrary, OnBackground, OnError
  - Common patterns: learn the material design attribute, use semantically-defined attributes, establish a common design language
- Theming
  = with theme attr
  - reduce duplication - two theme may share a lot of the same style, this reduce the duplication
  - localize modification
  - consolidate
- Applying Themes
  - can apply theme attribute on a view or a viewgroup
  - Theme is overlaid (applied on top)
    - ThemeOverlay.Material.Dark
- Understanding Platform themes
  - How to set a color for a single button (need to look at the slides)

## Improving Battery Life with Restrictions
[Youtube](https://www.youtube.com/watch?v=-7eZL3XRqas&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=34)

- what's consuming power
  - display, processors, cell radio
  - calculating powers using power profiles (per device)
- power saving feature
  - Suspending app (what is that?)
- work with the restrictions
  - evolution of restrictions: doze, doze-on-the-go, background limits, adaptive battery
  - adaptive battery: App standby bucket - active, working set, frequent, rare
  - app restrictions - restricted by user or suggested by system based on criteria
    - jobs, alarms, services, network, FCM, location updates are limited
- How is the app affected
  - work with the restrictions: when in background & not charging
    - when is the FCM messages delivered
      - if is app restricted, the message will be dropped after Jan 2019
- Design Principle: lazy first





# Android Tools

## Fun with LiveData
[Youtube](https://www.youtube.com/watch?v=2rO4r-JOQtA&index=3&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- Lifecycle aware observable dataholder
- LiveData is an Observable
- Lifecycle aware
  - observers will on be called when at the appropriate lifecycle state
- Transformations
- Bad patterns
  - Strong big objects across transformations
  - Sharing instances of live data
  - Transformation setup
- When not to use LiveData
  - If you need a lot of operators or streams, use Rx
  - If your operations are not about UI or lifecycle, use callback interfaces
  - If you have one-shot operation chaining use coroutines

## The Room in the House
[Youtube](https://www.youtube.com/watch?v=sU-ot_Oz3AE&index=4&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e) • [Documentation](https://developer.android.com/topic/libraries/architecture/room)

- offline apps need a database
- SQLite is powerful, too much boilerplate + not compile-time safe
- solution: Room persistence library; abstraction layer over SQLite
  - v 1.0 = compile-time safe, observabile, IDE integration
  - v 1.1 = write-ahead logging, paging integration
  - v 2.0 = AndroidX
  - v 2.1
    - FTS / full-text search
      - mini search engine
      - basically a different dataFts database
      - when querying, need to query from the dataFts as well
    - views
    - multi-index invalidation
    - AutoValue
    - RxRoom

    (?)
  - simplify N-N database (?)
  - Sync services: 
    - background sync services update the database
    - UI updates

## Testing Rebooted with AndroidX Test
[Youtube](https://www.youtube.com/watch?v=4m2yYSTdvIg&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=9) 

- ...

## Quick Ways to Ensure App Compatibility with Android Autofill
[Youtube](https://www.youtube.com/watch?v=POW9AXYO5Zo&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=16)

- from Android O
- doesn't require app changes
- annotate!
    - ex: should be *** `<... android:autofillHints="password" />`
    - ex: should NOT be autofilled `<... android:android:importantForAutofill="no" />`
- Autofill samples project
  - BasicService
    - only understand "autofillHints"
  - DebugService
    - tries to fill anything
    - useful to test (lack of) importantForAuto
- make sure your app works when services require authentication

## Optimize Your App Size with This One Trick
[Youtube](https://www.youtube.com/watch?v=QdoEcfibG-s&index=15&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- bad news:
  - install success rate decreases as apps get larger
  - ~ 1/5 devices in US & UK have <1GB free space
  - since 2012, apps have grown 5x larger on average
- suggested improvements:
  - smaller installs
  - dynamic features
  - faster updates
- Android App Bundle
  - Official Android app release ?
  - Deliver only what's needed
  - Split APKS: multiple installed for a single APK
  - App Bundle -> Base -> generate split APK for 
    -  different screen density
    -  different languages
    - x86_64, arm64, x86, arm
  - App signing by play (need to upload the key to google play)
  - Uncompressed native libraries
    - compressed native libraries is a waste of space
    - 16% decrease on disk, 8% decrease in download size
  - New optimizations applied only to App Bundles built with the gradle version which introduced
  - Integration the bundle
    - build.gradle 
    - Local iterations: use the new option called :APK from app bundle" in the studio run configuration
    - bundle generates APK Set Archive (.apks)
    - Internal test track (can share with the QA team)
  - Publishing and the Bundle Explore
    - play console can deal with it, can test the bundle with a small amount of users
    - Bundle Explorer: see how much the size we save using
 - Dynamic Feature
  - install and uninstall features on demand
  - or defer install in the background
  - for pre-L devices, "fuse" and deliver at install time
  - Modularize feature, and only install the feature when requested (user can see the download progress)
  - Example of modularization> plaid 2.0
  - need to integrate with "play-install" service ? for the on-demand install
  - Installing Modules & SplitCompat: Android L * M, the split requires app to restart, the compat can install the feature when the app goes into background
  - Updating modules;
    - when the app is updated, play will sync the module update
- Faster Updates w/ a new api
  - Immediate in-app update
  - Flexible in-app update: can customize the update flow in the app

## What's New With The Android Gradle Plugin
[Youtube](https://www.youtube.com/watch?v=GlwvVJNWlWg&index=22&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

-Incremental AP
  -INCAP
    - Make annotation processors incremental
    - 2levelofuppor:aggregatingor isolating
  -In-house annotation processors are your responsibility
- App Bundle - Modularity
  - appId, version code sync'ed from base module
    - no customization possible through DSL on dynamic features
    - Signature config synchronize... ?
  - Base Module
    - apply plugin: com.android.application
  - Feature Module
    -apply plugin: com.android.application.feature-module
  - Bundles/Shrinker Build Flow
    - Each module compiles and publishes classes.jar (all reside in the base module)
    - classes.jar are shrunk into dex files (R8)
    - Dex files are sent back to each modules for packaging
    - Create the module APKs
  - D8 and R8 
    - D8 is fully enabled in 3.2: we will eventually remove DX
    - R8 is experimental in 3.3 and on by default in 3.4 canaries
- 3.3
  - Lazy Task: 
    - before tasks were initialized at creation time
    - delay the initialization until we know the tasks will be executed
      = configuration block is lazy
      - OK to do real work if necessary
      - don't look up Tasks anymore
  - Light R classes
    - Faster build and sync
    - Avoid generating, compiling and indexing many R classes
    - Breaks some tools that depended on reading the R classes (including butterknife)
    = Attribution
      - why is my build slow
        - attribution of each annotation processor to compile time
        - attribution of tasks to plugins
        - why taskX ran
    - resource namespacing
      - better android resources build
      - faster saner build
      - better support dynamic features
      - Separately compile and link each library
      - Non0final IDs in application
      - 
    - Namespacing your app/library
      - Automatic namespacing
      - if a resource is in a dependency/library, the R will be remote.dep.R.string.remote_string instead of my.app.R.string.remote_string
      - Resource Visibility
        - three levels: public, private, private XML only - smaller R classes
    - what can you do
      - upgrade
      - -- scan: free tool from gradle, provide a comprehensive dash board to understand why the build is slow
      - Use --profile & --info: create a local html file to show some information about the build
      - Customization best practices, 
        - only use configuration to set up tasks (with lazy API). avoid doing any I/O or any other work
        - configuration is not the right place to query git, read tasks, search for file
        - each task declares input/outputs (even non-file), and is incremental as well as cacheable
        - Split complex steps into multiple tasks
        - ...

## ConstraintLayout Deep Dive
[Youtube](https://www.youtube.com/watch?v=P9Zstbk0lPw&index=24&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- match_constraint: takes up all the space available in the constraint space
- in the view inspector, if match constraint is selected, click the triangle to enable aspect ratio
- click the baseline in the view inspector, and drag the two baseline to make them align?
- View inspector: click the view to select center
- barrier: elements aligned to the constraint cannot cross elements in the barrier
- Creating Constraints
  - Add constraint in the context menu in the view inspector
- View Options
  -Show all constraints, live rendering
- Zoom and Plan
  - CMD/CTRL + - 0 (zoom to fit)
  - sample data
- New Feature
  - MotionLayout
    - collapsable headers
    - state feedback 
    - and more
  - Motion
    - define start and end
    - MotionLayout is a subclass of contraintLayout
    - MotionScene: where to encode the start to end animation
      - define the contraint at the start position
      - define the constraint at the end position
      - app:layoutDescription: "@xml/space_scene"
      - in space_scene:
        - <MotionScene>
    - Motion Editor (not quite ready)
  
## Modern WebView Best Practices
[Youtube](https://www.youtube.com/watch?v=HGZYtDZhOEQ&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=29)

- Launching Intent
  - override url loading and launch app instead
  - problem: javascript can trigger navigation to launch intents
    - fixed on N+
    - AndroidX exposes user gesture for L+
- Loading in-app content
  - #loadData 
    - defaults to %-encoded content (There is no API to convert to the %-encode automatically)
    - The content uses an opaque origin
    - Avoid encoding issues
      - Alternative encoding: base64
      - Avoid same-origin restrictions with loadDataWithBaseURL
        - accepts content as-is (unencoded)
        - your content has the baseUrl's origin
      - Choosing a base url

## Use Android Text Like a Pro
[Youtube](https://www.youtube.com/watch?v=vXqwRhjd7b4&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e&index=38)

- TextLayout takes the most of time in LinearLayout measure
  - Turning off hyphenation and use precomputed text decreases the time a lot
  - >90% native text processing is spent for text shaping
- Background measurement
  - before P, giant synchronization lock on native layer
  - If using precomputed text, you shall not call setSpan(metricAffecting...?) after construction
- RecyclerView prefetch
  - .setTextFuture: go to the background to to measure text and generate precomputedText 
  - need to apply all the styling before .setTextFuture
- How to turn off hyphenation: in style sheet 
- turn off hyphenation, and enable it when you need it
- check precomputedText (AndroidP & Android X)
- *** INCOMPLETE ***

## Re-stiching Plaid with Kotlin
[Youtube](https://www.youtube.com/watch?v=NNWejxBORgc&index=43&list=PLWz5rJ2EKKc8WFYCR9esqGGY0vOZm2l6e)

- Kotlin Coroutin as the backbone 
  - handle async operations
  - has a scope (e.g. pressing back button also canceling the network request)
- Kotlin favoring composition than inheritance
- when expression must be exhaustive 
- Test with the data class & the copy function makes it more readable

The components of material design
  - Starting using Material Components
    - depedencies: com.google.android.material:material:1.0.0,
            androidx.appcompat
    - Material Themes: i.e. MaterialComponents.Light
    - Bridge: provide attribute of styling, but not the entire theme (?)
  - Components: 
    - Bottom App Bar
  - Theming
    - View <- Style <- Default Style <- Theme
    - check material.io for each component to see how the attribute react
  - Theming Subsystems
    -Shape: adding materialShapeDrawable
    - edge and corner treatments
    - Component Shape Mapping
    - shadow support
  - Updating
    - AppCompat.Theme -> MaterialComponent
    - new theming attributes: onPrimary, onSecondary etc.
  - ThemeOverlay
  https://github.com/material-components/material-components-android

Single Activity
- Sharing data between activities
  - destinations inside activities : a subsection your Activity's UI
  - Making destinations easy
  - Navigation Architecture Component
- NavigationView
- findNavController
  - from within activity, fragment, view
- DeepLinking
  - he Android framework only knows how to deep link activities
  - can add deeplink and nav-graph tag to the xml
- Testing
  - Don't test at the destination level
    - extract business logic out of your destination, write test against a view model
  - FragmentScenario  
    - test a fragment in isolation
    - useful for espresso tests
    - FragmentScenario builds upon ActivityScenario
    - launchFragmentInContainer
  - Testing Navigation
    - Combining FragmentSenario and NavController
    - Testing the connections between destinations
- FragmentFactory
  - Allow for constructor injection
- Use case for multiple activities
  - multiple tasks actually
  - what are tasks - what users actually interact with
    - each task is a "window", 1-1
- So, use cases for multiple windows ?
  - documentLaunchMode
  - multitasking - "intoExisiting"
    - A separate window for each document/conversation
      - Each document has a unique URI 
      - example: google docs
    - Creating new content
      - Allows referencing existing content in the creation flow
      - Can have multiple ongoing operations at once
      - Example: Gmail
    - Picture-in-Picture
      - Using a separate task, e.g. Google Play, Movies on Android TV
      - Using a single task, e.g. Duo, Google Maps
- Being dynamics
  - instant experience for your app bundle
  - dynamic feature modules
  -  



    



