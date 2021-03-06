# blank-ios-swift

[![circle-ci](https://img.shields.io/circleci/project/github/feedhenry-templates/blank-ios-swift/master.svg)](https://circleci.com/gh/feedhenry-templates/blank-ios-swift)

> Obj-C version is available [here](https://github.com/feedhenry-templates/blank-ios-app/).

Author: Corinne Krych, Daniel Passos   
Level: Intermediate   
Technologies: Swift 4, iOS, RHMAP, CocoaPods.   
Summary: A demonstration of how to get started with RHMAP.   
Community Project : [Feed Henry](http://feedhenry.org)   
Target Product: RHMAP   
Product Versions: RHMAP 3.7.0+   
Source: https://github.com/feedhenry-templates/blank-ios-swift   
Prerequisites: fh-ios-swift-sdk: 6+, Xcode: 9+, iOS SDK: iOS 9+, CocoaPods: 1.3.0+

## What is it?

Simple native iOS app to get you started with [fh-ios-swift-sdk](https://github.com/feedhenry/fh-ios-swift-sdk) in RHMAP.

## How do I run it?  

### RHMAP Studio

This application and its cloud services are available as a project template in RHMAP as part of the "Native iOS Blank Project" template.

### Local Clone (ideal for Open Source Development)

If you wish to contribute to this template, the following information may be helpful; otherwise, RHMAP and its build facilities are the preferred solution.

## Build instructions

1. Clone this project
1. Populate ```blank-ios-app/fhconfig.plist``` with your values as explained [here](https://access.redhat.com/documentation/en-us/red_hat_mobile_application_platform_hosted/3/html/client_sdk/native-ios-swift).
1. Run ```Pod install```
1. Open blank-ios-app.xcworkspace
1. Run the project

> NOTE: If you clone it manually to make the app buildable in RHMAP Build farm, replace the templating ```%id%``` in ```blank-ios-app\blank-ios-app-Info.plist``` in the following block:

```xml
<key>CFBundleIdentifier</key>
<string>%id%</string>
```

## How does it work?

### FH init

In ```blank-ios-app/ViewController.swift``` the synchronization loop is started.

```
override func viewDidLoad() {
    super.viewDidLoad()
    
    // FH.init using Swift FH sdk
    // trailing closure Swift syntax
    FH.init { (resp:Response, error: NSError?) -> Void in
        if let error = error {
            self.statusLabel.text = "FH init in error"
            print("Error: \(error)")
        }
        self.statusLabel.text = "FH init successful"
        print("Response: \(resp.parsedResponse)")
    }

}

```

### iOS9 and non TLS1.2 backend

If your RHMAP is depoyed without TLS1.2 support, open as source  ```blank-ios-app/blank-ios-app-Info.plist.plist``` make sure the following line are uncommented:

```
  <key>NSAppTransportSecurity</key>
  <dict>
    <key>NSAllowsArbitraryLoads</key>
    <true/>
  </dict>
```

