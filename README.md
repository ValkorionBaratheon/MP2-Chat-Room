# MP2-Chat-Room
Machine Problem #2: A simple chat room

## Some thoughts:

1. We need a message structure with three fields 

```go
type Message struct {
	to string
	from string
	content []byte
}
```

The content field as type []byte to allow for messages of varying lengths and for ease of passing over the network.

The `client.go` program should leverage this structure, we don't need to have a `Client` struct per se but we should have a good representation for a message such as `type Message`.

2. The `server.go` program should use go routines to handle incoming tcp connections. We also need a go chan that takes messages.

```go
messageChannel := make(chan Message)
```

3. 
I think our  client will need the host address and the port number of the server as well as a username for itself that it will send to the server.
 `go run client.go localhost 6655 A`

4. The server will receive all of this info from the client through TCP, the address and port number as well as its username as a string (or maybe an int)

The server should have a map that translates from client usernames to their address and port numbers. So in a sense, clients are registering themselves to the server and the server handles sending messages between two clients who are already registered.
