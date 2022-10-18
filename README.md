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
