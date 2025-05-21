# advprog-module10-broadcastchat

### Tutorial 2.1
![alt text](image.png)

#### How to Run:
1. Start the server: `cargo run --bin server`
2. Start 3 clients: `cargo run --bin client`

#### What happens
When the server starts, it listens on `127.0.0.1:2000`.
- Each client connects to the server using WebSocket.
- Messages typed by one client are broadcast to all connected clients.
- The server handles multiple clients concurrently using async tasks.

### Tutorial 2.2
- All WebSocket connections in this project use the **ws:// protocol**, which is the standard for unencrypted WebSocket communication.
- The **client and server** both use port **8080**, ensuring they can communicate successfully.
- In the client, the WebSocket URI is defined using `ClientBuilder::from_uri(Uri::from_static("ws://127.0.0.1:8080"))`
- In the server, the listening port is defined using `TcpListener::bind("127.0.0.1:8080").await?;`
- The WebSocket handshake on the server side is handled by `ServerBuilder::new().accept(socket)`
- Both sides use the same `tokio_websockets` crate, ensuring consistency in the protocol and implementation.