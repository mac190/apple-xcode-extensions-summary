# Apple Xcode Extensions Summary

#### Disclaimer

<details>
<summary>Disclaimer</summary>
This document was created based on an educational presentation on various target extensions in Xcode. It may contain incorrect links and may lack crucial information. Feel free to PR this document. I will be more than happy to extend this summary. It is hard to find actual information on these kinds of possibilities, and I think every developer should have a way to extend their knowledge on extensions topics.
</details>

# Index

- [iOS Extensions](#ios-extensions)
  - [Accessory Setup Extension](#accessory-setup-extension)
  - [Account Authentication Extension](#account-authentication-extension)
  - [Action Extension](#action-extension)
  - [App Intents Extension](#app-intents-extension)
  - [Audio Unit Extension](#audio-unit-extension)
  - [Authentication Services Extension](#authentication-services-extension)
  - [AutoFill Credential Provider Extension](#autofill-credential-provider-extension)
  - [Background Download Extension](#background-download-extension)
  - [Broadcast Setup UI Extension](#broadcast-setup-ui-extension)
  - [Call Directory Extension](#call-directory-extension)
  - [Capture Extension](#capture-extension)
  - [ClassKit Context Extension](#classkit-context-extension)
  - [Contact Provider Extension](#contact-provider-extension)
  - [Content Blocker Extension](#content-blocker-extension)
  - [CoreSpotlight Delegate Extension](#corespotlight-delegate-extension)
  - [Custom Keyboard Extension](#custom-keyboard-extension)
  - [Device Activity Monitor Extension](#device-activity-monitor-extension)
  - [Device Activity Report Extension](#device-activity-report-extension)
  - [File Provider Extension](#file-provider-extension)
  - [File Provider UI Extension](#file-provider-ui-extension)
  - [Generic Extension Extension](#generic-extension-extension)
  - [iMessage Extension](#imessage-extension)
  - [Intents Extension](#intents-extension)
  - [Intents UI Extension](#intents-ui-extension)
  - [Live CallerID Lookup Extension](#live-callerid-lookup-extension)
  - [Location Push Service Extension](#location-push-service-extension)
  - [Matter Extension](#matter-extension)
  - [Media Device Discovery Extension](#media-device-discovery-extension)
  - [Message Filter Extension](#message-filter-extension)
  - [Network Extension](#network-extension)
  - [Notification Content Extension](#notification-content-extension)
  - [Notification Service Extension](#notification-service-extension)
  - [Persistent Token Extension](#persistent-token-extension)
  - [Photo Editing Extension](#photo-editing-extension)
  - [Print Service Extension](#print-service-extension)
  - [Quick Look Preview Extension](#quick-look-preview-extension)
  - [Safari Extension](#safari-extension)
  - [Share Extension](#share-extension)
  - [Shield Configuration Extension](#shield-configuration-extension)
  - [Smart Card Token Extension](#smart-card-token-extension)
  - [Spotlight Import Extension](#spotlight-import-extension)
  - [Sticker Pack Extension](#sticker-pack-extension)
  - [Thumbnail Extension](#thumbnail-extension)
  - [Unwanted Communication Extension](#unwanted-communication-extension)
  - [Virtual Conference Extension](#virtual-conference-extension)
  - [Widget Extension](#widget-extension)
- [macOS only extensions](#macos-only-extensions)
  - [Finder Sync Extension](#finder-sync-extension)
  - [Mail Extension](#mail-extension)
  - [Photo Project Extension](#photo-project-extension)
  - [Xcode Source Editor Extension](#xcode-source-editor-extension)
- [watchOS has no watch only extension](#watchos-has-no-watch-only-extension)
- [tvOS only extensions](#tvos-only-extensions)
  - [TV Top Shelf Extension](#tv-top-shelf-extension)
- [visionOS has no vision only extensions](#visionos-has-no-vision-only-extensions)
- [WWDC24 updates](#wwdc24-updates)
- [Helpful docs](#helpful-docs)

# iOS Extensions

### What are those?

Extensions provide a way to extend the functionality of your app or the Apple ecosystem. Below is a list of various extensions along with a brief description and additional notes.

---

### Accessory Setup Extension
- **Features:**
  - Used for seamless third-party device setup using Bluetooth or Wi-Fi
  - No more “go to settings” path
  - AccessorySetupKit is the keyword
- **Since:** iOS 18
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
This extension allows users to set up third-party accessories directly within the app, eliminating the need to navigate to the settings.

#### Notes:
- WWDC24 session 10203

---

### Account Authentication Extension
- **Features:**
  - Can provide strong passwords
  - Can provide Sign in with Apple functionality
  - Can include additional steps like 2FA
  - Can perform automated password update
  - Can perform automated update to Sign in with Apple
- **Since:** 2020 - iOS 13
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Used to implement secure account authentication features, including strong passwords, Sign in with Apple, and two-factor authentication.

#### Notes:
- Many of the functionalities listed above need to be implemented on the backend side

---

### Action Extension
- **Features:**
  - Can modify data like text or images outside the app
  - We can import data to our app directly
  - It can work without UI
- **Documented Since:** 2014
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows apps to perform actions on content from other apps, such as modifying text or images.

#### Notes:
<!-- Add your notes here -->

---

### App Intents Extension
- **Features:**
  - Can add custom actions to spotlight search, Siri, or Shortcuts app based on our implementation
  - Can add custom UI that corresponds with custom actions
  - Can add functionality to the action button
- **Since:** 2023 - iOS 16
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS, WatchOS

#### Additional Description:
Enables apps to define custom intents that can be used in Siri, Shortcuts, and Spotlight searches, providing deeper integration with the system.

#### Notes:
- Older Intents can be converted/migrated to App Intents
- New stuff - written in Swift

---

### Audio Unit Extension
- **Features:**
  - Can specify a type of audio unit to create (e.g., Instrument or Music Effect)
  - Can send an audio stream to a host app (or act as a middleman to modify the audio stream in a custom way)
  - Can specify a Realtime Thread with the use of Workgroups
- **Documented Since:** 2014
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows developers to create custom audio processing units that can be used within host applications like GarageBand or Logic Pro.

#### Notes:
- In Apple Silicon, there are API-breaking changes (it was moved from Carbon Component API to Audio Component API)
- When dealing with realtime audio processing, we have to ensure that our threads are synced and work with regular intervals
- [Documentation Link](https://developer.apple.com/documentation/avfaudio/audio_engine/audio_units/creating_an_audio_unit_extension?changes=la___4_3_6_5_5__4_3_5_6)

---

### Authentication Services Extension
- **Features:**
  - Adds Single Sign-On (not Sign in with Apple)
  - Can have custom UI
  - Can have web implementation
  - Can work without UI
  - Works on redirections
  - Works with Identity Provider
- **Since:** 2020 - iOS 13
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Provides Single Sign-On (SSO) capabilities, allowing users to authenticate with multiple apps using a single set of credentials.

#### Notes:
- Oriented around enterprise use cases

---

### AutoFill Credential Provider Extension
- **Features:**
  - Adds a “password manager” functionality
- **Since:** 2019 - iOS 12
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables apps to provide autofill functionality for passwords and other credentials, integrating with the system's password manager.

#### Notes:
- [Documentation Link](https://nilotic.github.io/2018/09/07/Implementing-AutoFill-Credential-Provider-Extensions.html)
- [Useful Thread](https://stackoverflow.com/questions/66116582/implement-autofill-credential-provider-extension-in-ios14)
- WWDC18 - 721 session

---

### Background Download Extension
- **Features:**
  - More like “Background Assets Download Extension”
  - Can download app data outside the app bundle
  - Developers can define download limits
    - Before app launch
    - During app launch
- **Since:** 2023 - iOS 16
- **Supported Platforms:** iOS/iPadOS, macOS

#### Additional Description:
Allows apps to download assets and data in the background, even when the app is not running, improving the user experience.

#### Notes:
- Runs during app install and update
- We are receiving callbacks for every downloaded asset
- Helps with overnight automatic updates to improve user experience

---

### Broadcast Setup UI Extension
- **Features:**
  - Works in pair with Broadcast Upload
  - Used for streaming the view of our app to a remote server
- **Since:** 2017 - iOS 11
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Used to configure and initiate broadcasts from the app to a remote server, often used for live streaming.

#### Notes:
- WWDC 2017 session 606
- [Useful Link](https://pexip.github.io/pexip-swift-sdk/sdk/documentation/pexipswiftsdk/iosscreensharing/)
- [Another Useful Link](https://github.com/OurBigAdventure/Broadcast-Upload-Extension)
- For live conference apps

---

### Call Directory Extension
- **Features:**
  - Used for VoIP apps
  - Provides solutions for handling voice/video calls from custom apps
  - Index our custom call on the “Recent” list in the Phone app
- **Since:** 2018 - iOS 10
- **Supported Platforms:** iOS/iPadOS, macOS, WatchOS

#### Additional Description:
Allows apps to identify and block incoming calls, and manage call directories for handling VoIP calls.

#### Notes:
<!-- Add your notes here -->

---

### Capture Extension
- **Features:**
  - Used for adding camera action in our app straight from the lock screen
  - Device stays locked during extension use
- **Since:** iOS 18
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Enables quick access to the camera from the lock screen for capturing photos or videos directly into the app.

#### Notes:
- WWDC24 session 10204

---

### ClassKit Context Extension
- **Features:**
  - Adds a single class with one function of CLSContext
  - CLSContext represents a piece of content (chapter/lesson/quiz)
  - Used for teachers to track progress
- **Since:** 2019 - iOS 12.2
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Integrates with the ClassKit framework to help teachers track student progress and activities within educational apps.

#### Notes:
<!-- Add your notes here -->

---

### Contact Provider Extension
- **Features:**
  - For adding our own contacts in apps outside our systems
  - For separating app contacts from personal contacts
- **Since:** iOS 18
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Allows apps to manage and provide contact information to the system, separating app-specific contacts from personal contacts.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/ContactProvider)

---

### Content Blocker Extension
- **Features:**
  - Can implement elements hiding in Safari
  - Can implement load blockers in Safari
  - Can implement cookie stripping in Safari
  - Rules (as plain strings) have to be in the correct format (missing commas or braces will result in Safari not compiling them)
- **Since:** 2014 - iOS 3
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables apps to block unwanted content, such as ads or trackers, in Safari by defining a set of rules.

#### Notes:
<!-- Add your notes here -->

---

### CoreSpotlight Delegate Extension
- **Features:**
  - Used for adding search capabilities for your app content in Spotlight
  - Expiration is 1 month
  - Indexed data is not shared between devices and with Apple
  - Sensitive searches can be filtered for public indexing
- **Since:** iOS 9
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows apps to index content and make it searchable via the system's Spotlight search feature, enhancing discoverability.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/corespotlight)

---

### Custom Keyboard Extension
- **Features:**
  - Apps can disallow usage of custom keyboard
  - Can’t be used with secure fields and with `.phonePad` or `.namePhonePad`
  - Confined to system keyboard bounding box
  - No access to microphone - no dictation
- **Since:** 2014 - iOS 8
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Allows developers to create custom keyboards that users can install and use system-wide, providing unique input methods.

#### Notes:
<!-- Add your notes here -->

---

### Device Activity Monitor Extension
- **Features:**
  - Used for handling Screen Time limits
  - Can schedule a notification with a warning timer
  - Hard limit of 5MB for the extension
- **Since:** iOS 16
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Helps manage and monitor device usage, integrating with the Screen Time API to enforce usage limits and notifications.

#### Notes:
<!-- Add your notes here -->

---

### Device Activity Report Extension
- **Features:**
  - Used to get device activity data
  - Data presentation can be customized
  - Highly integrated with Family Activity
  - We can specify an exact period of device activity
- **Since:** iOS 16
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Provides detailed reports on device usage, allowing customization of the data presentation and integration with Family Activity.

#### Notes:
- Data can be customized with parameters like users or children
- Filtered by devices, applications, categories, or web domains

---

### File Provider Extension
- **Features:**
  - Adds the ability to access files and folders managed by your app from other apps
  - Can also sync with remote storage (replicated file provider)
- **Since:** iOS 11
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables apps to expose their files and folders to other apps and sync with remote storage, enhancing file management.

#### Notes:
<!-- Add your notes here -->

---

### File Provider UI Extension
- **Features:**
  - Extends File Provider Extension
  - Can add custom action to File Provider after long press
  - Can have custom UI interface
- **Since:** iOS 11
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Adds a user interface to the File Provider extension, allowing for custom actions and UI when interacting with files.

#### Notes:
<!-- Add your notes here -->

---

### Generic Extension Extension
- **Features:**
  - ExtensionKit is the keyword
  - Used for opening our app to use others' app extensions
  - They were present but not available
  - Extensions have to be approved by a user
- **Since:** Xcode 14 - iOS 16
- **Supported Platforms:** iOS/iPadOS, macOS

#### Additional Description:
Allows apps to leverage extensions from other apps, enabling integration and interaction between different app functionalities.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/extensionkit/exappextensionbrowserviewcontroller)

---

### iMessage Extension
- **Features:**
  - Add custom UI inside iMessage with specified data
  - Can update existing data
  - Can implement handling rich media types
- **Since:** iOS 10
- **Supported Platforms:** iOS/iPadOS, macOS

#### Additional Description:
Enables apps to provide custom interfaces and functionality within the Messages app, such as stickers and interactive content.

#### Notes:
- macOS is supported via Mac Catalyst

---

### Intents Extension
- **Features:**
  - Used for exposing app functionalities to Siri
  - Making Siri respond to a custom "questions"
- **Since:** iOS 12
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows apps to define custom Siri commands, enabling users to interact with the app through voice commands.

#### Notes:
<!-- Add your notes here -->

---

### Intents UI Extension
- **Features:**
  - With intent parameters, we can customize Siri or maps interface
  - We can replace the Siri and maps default interface entirely
  - We can provide Siri with a custom single view controller
- **Since:** iOS 11
- **Supported Platforms:** iOS/iPadOS, visionOS

#### Additional Description:
Provides a way to customize the user interface for Siri and Maps interactions, replacing the default UI with a custom view.

#### Notes:
<!-- Add your notes here -->

---

### Live CallerID Lookup Extension
- **Features:**
  - Can add identity providers from our servers
  - Can add call blocking services based on blacklists from our servers
  - Requires the use of Apple relay servers and endpoint validation
- **Since:** iOS 18
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Allows apps to identify and block unwanted calls by integrating with external identity and blacklist providers.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/sms_and_call_reporting/getting_up-to-date_calling_and_blocking_information_for_your_app)

---

### Location Push Service Extension
- **Features:**
  - Can add Location-based services in iOS
  - Can be used for querying locations when our app is not running
- **Since:** iOS 15
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Enables apps to receive location updates and notifications, even when the app is not running, for improved location-based services.

#### Notes:
- Needs "Always" location Authorization Status

---

### Matter Extension
- **Features:**
  - Used for providing user interface during the setup of a new Matter device
- **Since:** iOS 16
- **Supported Platforms:** iOS/iPadOS, visionOS

#### Additional Description:
Facilitates the setup and configuration of Matter-compliant smart home devices, integrating with the HomeKit ecosystem.

#### Notes:
- Hard to find information about it
- [Useful Link](https://developer.apple.com/documentation/mattersupport/adding-matter-support-to-your-ecosystem)
- Extension provides a set of useful functions for Matter device handling (rooms getter, configureDevice, validateDeviceCredentials, selectWifiNetwork, commissionDevice)

---

### Media Device Discovery Extension
- **Features:**
  - Used for adding an AirPlay device as a streaming option
- **Since:** iOS 16
- **Supported Platforms:** iOS/iPadOS, visionOS

#### Additional Description:
Allows apps to discover and add media streaming devices, such as AirPlay speakers, for enhanced media playback options.

#### Notes:
<!-- Add your notes here -->

---

### Message Filter Extension
- **Features:**
  - Used for helping with identifying unwanted messages
- **Since:** iOS 11
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Helps filter and identify unwanted messages, such as spam, by integrating with the system's message filtering capabilities.

#### Notes:
<!-- Add your notes here -->

---

### Network Extension
- **Features:**
  - Can be used to change Wi-Fi configuration
  - Can add hotspot configurations
  - Can add VPN configurations
  - Can add a content filter
  - Can add system-wide DNS configurations
- **Since:** iOS 8
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS, WatchOS

#### Additional Description:
Provides a range of networking capabilities, including configuring Wi-Fi, VPNs, and DNS settings, for enhanced network control.

#### Notes:
- Not all features are available on every platform
- Some features can work only on supervised devices

---

### Notification Content Extension
- **Features:**
  - We can replace a system notification with a custom notification UI
  - Show app-specific data inside the notification
- **Since:** iOS 10
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows apps to customize the appearance and content of notifications, providing a richer user experience.

#### Notes:
<!-- Add your notes here -->

---

### Notification Service Extension
- **Features:**
  - No UI
  - Can be used to modify incoming data
  - Can be used to download additional data
  - You can’t modify silent notifications
  - You can’t modify sound/badge only notifications
- **Since:** iOS 10
- **Supported Platforms:** iOS/iPadOS

#### Additional Description:
Enables apps to process and modify the content of incoming notifications before they are presented to the user.

#### Notes:
- Possible use case for decrypting data
- Can modify notification content (for example, add content from the host app)

---

### Persistent Token Extension
- **Features:**
  - CryptoTokenKit is the keyword
  - Used for providing always-available tokens (persistent tokens)
  - Provided tokens can be used by system or third-party apps
- **Since:** iOS 13
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS, WatchOS

#### Additional Description:
Allows apps to provide persistent cryptographic tokens for secure authentication and encryption purposes.

#### Notes:
- [Useful Link](https://github.com/Purebred/CtkProvider)
- [Another Useful Link](https://forums.developer.apple.com/forums/thread/744863)

---

### Photo Editing Extension
- **Features:**
  - Allows us to make a custom photo editing extension, for example, adding a watermark
  - Photos app provides us with a version control mechanism
- **Since:** iOS 8
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables developers to create custom photo editing tools that integrate directly with the Photos app, supporting non-destructive edits.

#### Notes:
- [Useful Link](https://developer.apple.com/library/archive/documentation/General/Conceptual/ExtensibilityPG/Photos.html)
- Photos app keeps multiple versions of each media asset data (version control-like)

---

### Print Service Extension
- **Features:**
  - Useful when we do not want to manually add a configuration profile for AirPrint
  - Extension can search for a printer (or set of printers)
- **Since:** iOS 14.5
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows apps to manage printer configurations and search for AirPrint-compatible printers, streamlining the printing process.

#### Notes:
- macOS is supported via Mac Catalyst

---

### Quick Look Preview Extension
- **Features:**
  - Can extend system Quick Look to our own data types
  - Can add a custom Preview View Controller
  - Not for editing
  - Not for audio/video playback
- **Since:** iOS 12
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables apps to provide custom previews for custom file types using the Quick Look feature, enhancing the user experience.

#### Notes:
- WWDC18 session 237 - "Quick Look Preview from the Ground Up"
- Quick Look can be implemented inside custom applications

---

### Safari Extension
- **Features:**
  - Integrating app functionality into Safari web browser
  - Replacing content
  - Blocking content
- **Since:** iOS 15
- **Supported Platforms:** iOS/iPadOS, macOS

#### Additional Description:
Allows developers to create extensions that enhance Safari's capabilities, such as blocking content or modifying web pages.

#### Notes:
<!-- Add your notes here -->

---

### Share Extension
- **Features:**
  - Can be used to share a resource to our app directly from the share system popup
  - Can be used for sharing a resource to a specific person via our app (when our app acts like a communicator)
  - A custom Share Controller can be implemented
- **Since:** iOS 13
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables apps to appear in the system's share sheet, allowing users to share content directly to the app from other apps.

#### Notes:
- Only height can be customized in custom Share Controller implementation
- If used for posting content, background mode for requests has to be implemented
- Can add validation for post sharing (for example, maximum character count)
- Can add configuration items or be replaced by custom view implementation
- [Useful Link](https://developer.apple.com/library/archive/documentation/General/Conceptual/ExtensibilityPG/Share.html#//apple_ref/doc/uid/TP40014214-CH12-SW2)

---

### Shield Configuration Extension
- **Features:**
  - Works with Shield Action Extension
  - Used for handling Screen Time API
  - Little to no information on documentation
  - Can be used for handling actions when Shield protected actions are being triggered
- **Since:** iOS 15
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Works with the Screen Time API to manage and enforce screen time limits and related actions, providing parental controls.

#### Notes:
- WWDC21 session 10123 - "Meet the Screen Time API"

---

### Smart Card Token Extension
- **Features:**
  - Used for adding hardware-based tokens (like Yubico)
  - No UI
- **Since:** iOS 10
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Enables apps to integrate with hardware-based security tokens for enhanced authentication and security.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/cryptotokenkit/authenticating_users_with_a_cryptographic_token)

---

### Spotlight Import Extension
- **Features:**
  - Used for adding searchable attributes (like file type or metadata)
  - Can launch action from Spotlight based on the added files' attributes (open our app and do stuff)
- **Since:** iOS 15
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows apps to add custom attributes to files, making them searchable through Spotlight and enabling custom actions based on searches.

#### Notes:
- [Useful Link](https://stackoverflow.com/questions/38907577/how-to-debug-a-spotlight-extension-in-ios)
- [Another Useful Link](https://developer.apple.com/documentation/corespotlight/csimportextension?language=objc)

---

### Sticker Pack Extension
- **Features:**
  - Does not require any code
  - File has to be smaller than 500kb
  - 206x206 points are 618x618 pixels
  - Stickers can be animated (with Motion for (300-0.01)zł only)
- **Since:** iOS 10
- **Supported Platforms:** iOS/iPadOS, macOS

#### Additional Description:
Allows developers to create sticker packs for iMessage without writing any code, enhancing messaging with custom stickers.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/messages/adding-your-sticker-packs-to-messages)
- [Another Useful Link](https://developer.apple.com/imessage/creating-stickers-with-motion/)

---

### Thumbnail Extension
- **Features:**
  - Provides a way to add a file thumbnail to custom files
  - NOT an icon
  - Can be used to generate a file thumbnail of (for example) a 3D model visualization
- **Since:** iOS 13
- **Supported Platforms:** iOS/iPadOS, macOS

#### Additional Description:
Enables apps to generate and display thumbnails for custom file types, improving file previews and user experience.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/quicklookthumbnailing/providing-thumbnails-of-your-custom-file-types)

---

### Unwanted Communication Extension
- **Features:**
  - Used for providing a way to report an unwanted call or SMS
  - Appears in SMS/Call Reporting system settings
  - Can send a network request or an SMS to the provided by app telephone number
  - Can be specified if call/SMS be reported or reported and blocked
- **Since:** iOS 12
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Allows users to report and block unwanted communications, integrating with the system's call and SMS reporting features.

#### Notes:
- macOS via Mac Catalyst
- Blocked numbers are added to the iOS blocked list

---

### Virtual Conference Extension
- **Features:**
  - Used for adding conference details to the calendar (like join button) for our main app or website link
  - Works with EventKit
  - Events can sync to other devices even if there is no app installed
  - For best experience, adopt universal links
- **Since:** iOS 15
- **Supported Platforms:** iOS/iPadOS, macOS, visionOS

#### Additional Description:
Facilitates adding virtual conference details to the calendar, enabling easy joining and event synchronization across devices.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/eventkit/ekvirtualconferenceprovider)

---

### Widget Extension
- **Features:**
  - Can provide app-specific data to be presented to the user outside the app
  - Game widgets can present player health or turn
  - Written in SwiftUI
  - Can also include dynamic island presentations
- **Since:** iOS 14
- **Supported Platforms:** iOS/iPadOS, macOS, tvOS 18(?)

#### Additional Description:
Allows apps to provide widgets that display information on the home screen or in the Today view, offering quick access to app data.

#### Notes:
- [WidgetKit SwiftUI Views](https://developer.apple.com/documentation/widgetkit/swiftui-views)
- [WidgetKit App Intent Configuration](https://developer.apple.com/documentation/widgetkit/appintentconfiguration)
- [WidgetKit Activity Configuration](https://developer.apple.com/documentation/widgetkit/activityconfiguration)

---

## macOS only extensions

---

### Finder Sync Extension
- **Features:**
  - Can add a synchronization status to files outside our app
  - Not for file syncing - only for user experience
- **Since:** macOS 10.10
- **Supported Platforms:** macOS

#### Additional Description:
Enhances the Finder experience by adding badges and contextual menus to files that are synced with the app.

#### Notes:
- [Useful Link](https://developer.apple.com/library/archive/documentation/General/Conceptual/ExtensibilityPG/Finder.html)

---

### Mail Extension
- **Features:**
  - MailKit is the keyword
  - Plugins replacement
  - For composing
  - For content blocking
  - For adding custom actions like mail rules
  - For adding encryption
- **Since:** macOS 12
- **Supported Platforms:** macOS

#### Additional Description:
Replaces Mail plugins with MailKit extensions, allowing developers to create features like custom compose actions, content blocking, and mail rules.

#### Notes:
- Nice WWDC talk - WWDC21 session 10168
- [Useful Link](https://developer.apple.com/documentation/mailkit/build-mail-app-extensions)

---

### Photo Project Extension
- **Features:**
  - Used for creating projects - like slideshows directly from the Photos App
  - Can implement creation of Regions of Interests (ROI)
- **Since:** macOS 11
- **Supported Platforms:** macOS

#### Additional Description:
Enables developers to create custom photo project extensions, such as slideshows or photo books, directly within the Photos app.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/photokit/creating_a_slideshow_project_extension_for_photos/)

---

### Xcode Source Editor Extension
- **Features:**
  - XcodeKit is the keyword
  - Can read and modify the source files as well as selected text
- **Since:** macOS 10.12
- **Supported Platforms:** macOS

#### Additional Description:
Allows developers to create extensions that enhance the Xcode source editor, enabling custom editing and text manipulation features.

#### Notes:
- [Useful Link](https://developer.apple.com/documentation/xcodekit/creating_a_source_editor_extension)

---

## watchOS has no watch only extension

---

## tvOS only extensions

---

### TV Top Shelf Extension
- **Features:**
  - Used for highlighting content on our Apple TV
  - Used for streamlining interactions
  - TVML - used for presenting specific app state for client-server app
- **Since:** tvOS 13
- **Supported Platforms:** tvOS

#### Additional Description:
Allows apps to feature content on the top shelf of the Apple TV home screen, enhancing visibility and user interaction.

#### Notes:
- WWDC19 session 211
- TVML since tvOS18 is deprecated
- [Useful Link](https://developer.apple.com/documentation/tvservices/tvtopshelfcontentprovider)

---

## visionOS has no vision only extensions

---

### (Not)Helpful docs
- [App Extensions](https://developer.apple.com/app-extensions/)
- [Generic Extensions](https://www.chimehq.com/blog/extensionkit-intro)
- [Extensions in Flutter](https://docs.flutter.dev/platform-integration/ios/app-extensions)
