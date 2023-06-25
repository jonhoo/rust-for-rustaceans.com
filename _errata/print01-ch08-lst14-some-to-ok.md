---
chapter: 8
kind: code
reporter: SARDONYX
page: 138
date: 2023-06-25
---

Listing 8-14 says

```rust
async fn handle_client(socket: TcpStream) -> Result<()> {
    // Interact with the client over the given socket.
}

async fn server(socket: TcpListener) -> Result<()> {
    while let Some(stream) = socket.accept().await? {
        handle_client(stream).await?;
    }
}
```

but should say

```rust
async fn handle_client(socket: TcpStream) -> Result<()> {
    // Interact with the client over the given socket.
}

async fn server(socket: TcpListener) -> Result<()> {
    while let Ok(stream) = socket.accept().await? {
        handle_client(stream).await?;
    }
}
```
