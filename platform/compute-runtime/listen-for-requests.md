# Listen for Requests

All Swift Cloud applications start with listening for an incoming HTTP request. This is accomplished by calling `onIncomingRequest` in your main handler function:

```swift
import Compute

@main
struct App {
    static func main() async throws {
        try await onIncomingRequest(handleIncomingRequest)
    }

    static func handleIncomingRequest(req: IncomingRequest, res: OutgoingResponse) async throws {
        print("Handling request:", req.url.pathname)
    }
}
```

