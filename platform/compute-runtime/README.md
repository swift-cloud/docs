---
description: The core library for building apps on Swift Cloud
---

# Compute Runtime

To get started building apps on Swift Cloud, you must install the \[Swift Compute Runtime]\([https://github.com/AndrewBarba/swift-compute-runtime](https://github.com/AndrewBarba/swift-compute-runtime)) using Swift Package Manager:

```
.package(url: "https://github.com/AndrewBarba/swift-compute-runtime", from: "1.0.0")
```

The compute runtime provides bindings to the underlying WASM runtime giving you the ability to listen for HTTP requests, make outgoing HTTP requests, read dictionary and environment variables, and a whole lot more.

The library was designed with modern Swift features like async/await to make concurrent programing as easy and safe to use as possible. It also provides lower level abstractions for working directly with streaming data, giving developers the highest level of flexibility when working building their API's. One main advantage of building on the Fastly platform is the superior HTTP stack compared to other serverless platforms like AWS Lambda. Lambda does not have any ability to stream responses to clients and thus limits what you can do with binary data like images and MP3's. On Swift Cloud you have full control over streaming requests and responses.
