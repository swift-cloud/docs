# Respond to Requests

Responding to HTTP requests is just as simple as listening for them, simply call the various `send()` methods on the `OutgoingResponse` object:

```swift
import Compute

@main
struct HelloCompute {
    static func main() async throws {
        try await onIncomingRequest(handleIncomingRequest)
    }

    static func handleIncomingRequest(req: IncomingRequest, res: OutgoingResponse) async throws {
        let text = "Hello, World."
        try await res.status(200).send(text)
    }
}
```

The Compute library provides various versions of `send` that allow you to pass JSON data, Encodable's, HTML, XML and raw bytes / streams of data.
