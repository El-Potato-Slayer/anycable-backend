Logs of Servers

AnyCable-Go server:
```
←[34m  INFO←[0m 2022-05-05T20:47:40.707Z ←[34mcontext←[0m=main ←[34mStarting AnyCable 1.2.0-a9c7945 (pid: 2616, open file limit: unsupported)←[0m
←[34m  INFO←[0m 2022-05-05T20:47:40.708Z ←[34mcontext←[0m=main ←[34mHandle WebSocket connections at http://localhost:8080/cable←[0m
←[34m  INFO←[0m 2022-05-05T20:47:40.708Z ←[34mcontext←[0m=main ←[34mHandle health connections at http://localhost:8080/health←[0m
←[34m  INFO←[0m 2022-05-05T20:47:40.709Z ←[34mcontext←[0m=rpc ←[34mRPC controller initialized: localhost:50051 (concurrency: 28, enable_tls: false, proto_versions: v1)←[0m
←[34m  INFO←[0m 2022-05-05T20:47:40.717Z ←[34mcontext←[0m=pubsub ←[34mSubscribed to Redis channel: __anycable__
←[0m
```

RPC:
```
Starting AnyCable RPC server (pid: 5368)
AnyCable version: 1.2.3 (proto_version: v1)
Serving Rails application from ./config/environment.rb
gRPC version: 1.45.0
Broadcasting Redis channel: __anycable__
RPC server is starting...
RPC server is listening on localhost:50051 (workers_num: 30)
```

Rails server:
```
Started GET "/cable/" [WebSocket] for 127.0.0.1 at 2022-05-06 00:18:00 +0200
Successfully upgraded to WebSocket (REQUEST_METHOD: GET, HTTP_CONNECTION: keep-alive, Upgrade, HTTP_UPGRADE: websocket)  
[ActionCable] Broadcasting to room_channel: "Message sent from backend"
[2022-05-06 00:18:00.158] ERROR -- NotImplementedError: nil
Started GET "/cable" for 127.0.0.1 at 2022-05-06 00:18:00 +0200
Started GET "/cable/" [WebSocket] for 127.0.0.1 at 2022-05-06 00:18:00 +0200
Successfully upgraded to WebSocket (REQUEST_METHOD: GET, HTTP_CONNECTION: keep-alive, Upgrade, HTTP_UPGRADE: websocket)
[ActionCable] Broadcasting to room_channel: "Message sent from backend"
[2022-05-06 00:18:00.229] ERROR -- NotImplementedError: nil
```

The Room channel broadcasts the `Message sent from backend` string once subscribed.
This works without any issues in ActionCable; I'm able to subscribe and receive the string and log it to the [front-end](https://github.com/El-Potato-Slayer/anycable-frontend) console.
The [front-end](https://github.com/El-Potato-Slayer/anycable-frontend) is also setup to log if the user is connected and disconnected. However, with AnyCable only the disconnected string gets logged.
