---
description: Compile your Swift applications to web assembly
---

# Web Assembly

Swift Cloud is made possible by the incredible [SwiftWasm](https://swiftwasm.org) project, but probably not in the way you might think. Web Assembly is making waves as being a new high performance environment for web application development but its also powering cloud computing platforms like Cloudflare Workers and Fastly Compute@Edge. Swift Cloud works by compiling your code to Web Assembly and deploying it to the Fastly Compute@Edge platform. Swift Cloud builds your code and manages Fastly compute services behind the scenes so you do not need a Fastly account or any existing knowledge about how the Fastly platform works.

### Limitations

There's no two ways about it - Swift Cloud has serious limitations that will take some getting used to. First of all, it's important to understand that these limitations exist today because of the platform we chose to build on first. We have plans to introduce other deployment targets (like AWS Lambda) that remove some limitations and introduce others. We chose to build on the Fastly platform as we believe it provides the absolute best HTTP stack available today. Starting with HTTP allows us to focus on the primary way we think iOS developers and macOS developers will use the platform when getting started. We're thinking basic integrations with Stripe, Slack, Twilio etc. all of which will require an HTTP backend for your apps.

### Swift Foundation and Dispatch

[The Foundation core library](https://swift.org/core-libraries/#foundation) is available in SwiftWasm, but in a limited capacity. The main reason is that [the Dispatch core library](https://swift.org/core-libraries/#libdispatch) is unavailable due to [the lack of standardized multi-threading support](https://github.com/swiftwasm/swift/issues/1887)in WebAssembly and SwiftWasm itself. Many Foundation APIs rely on the presence of Dispatch under the hood, specifically file system access and threading helpers. A few other types are unavailable in browsers or aren't standardized in WASI hosts, such as support for sockets and low-level networking, or support for time zone files, and they had to be disabled. These types are therefore absent in SwiftWasm Foundation:

* `FoundationNetworking` types, such as `URLSession` and related APIs
* `FileManager`
* `Host`
* `Notification`
* `NotificationQueue`
* `NSKeyedArchiver`
* `NSKeyedArchiverHelpers`
* `NSKeyedCoderOldStyleArray`
* `NSKeyedUnarchiver`
* `NSNotification`
* `NSSpecialValue`
* `Port`
* `PortMessage`
* `Process`
* `ProcessInfo` (Partially available since 5.7)
* `PropertyListEncoder`
* `RunLoop`
* `Stream`
* `Thread`
* `Timer`
* `UserDefaults`

Related functions and properties on other types are also absent or disabled. We would like to make them available in the future as soon as possible, and [we invite you to contribute](https://book.swiftwasm.org/contribution-guide/index.html) and help us in achieving this goal.
