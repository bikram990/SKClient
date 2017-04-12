# SKClient: SlackKit Client Module
![Swift Version](https://img.shields.io/badge/Swift-3.0.2-orange.svg)
![Plaforms](https://img.shields.io/badge/Platforms-macOS,iOS,tvOS,Linux-lightgrey.svg)
![License MIT](https://img.shields.io/badge/License-MIT-lightgrey.svg)
[![SwiftPM compatible](https://img.shields.io/badge/SwiftPM-compatible-brightgreen.svg)](https://github.com/apple/swift-package-manager)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-brightgreen.svg)](https://github.com/Carthage/Carthage)
[![CocoaPods compatible](https://img.shields.io/badge/CocoaPods-compatible-brightgreen.svg)](https://cocoapods.org)

Create a custom SlackKit client.

## Installation

### CocoaPods

Add SKClient to your pod file:

```
use_frameworks!
pod 'SKClient'
```
and run

```
# Use CocoaPods version >= 1.1.0
pod install
```

### Carthage

Add SKClient to your Cartfile:

```
github "SlackKit/SKClient"
```
and run

```
carthage bootstrap
```

Drag the built `SKClient.framework` into your Xcode project.

### Swift Package Manager

Add SKClient to your Package.swift

```swift
import PackageDescription
  
let package = Package(
	dependencies: [
		.Package(url: "https://github.com/SlackKit/SKClient.git", majorVersion: 4)
	]
)
```

Run `swift build` on your application’s main directory.

To use the library in your project import it:

```
import SKClient
```

## Usage
Subclass `Client` to create a custom SlackKit client.

```
class MyClient: Client {

    override func notificationForEvent(_ event: Event, type: EventType) {
    …
    }

	override func initialSetup(JSON: [String: Any]) {
	…
	}
}
```

Pass your custom client to [`SlackKit`](https://www.github.com/SlackKit/SlackKit) when adding an RTM bot:

```
let bot = SlackKit()
bot.addRTMBotWithAPIToken(“xoxb-SLACK_AUTH_TOKEN”, client: MyClient())
```
