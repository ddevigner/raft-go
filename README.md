# The Raft Consensus Algorithm
Distributed Systems University Project: "KEY/VALUE" Storage system via distributed server. Raft Consensus Algorythm in Golang. Implements:
- Leader selection.
- Log validation and replication.
- State machine application.

For more information, visit the [raft github repository]

## How can I execute your code and check how it works?
Execution of the application/service's raft node: pass as many addresses as raft nodes you want and indicate which one, the current node you are trying to launch, is.
```bash
# Run it immediatly.
go run storage_srvraft.go <me> <ip/dns:port>...

# Or if you preffer, you can build and launch it.
go build storage_srvraft.go
{storage_srvraft|./storage_srvraft} <me> <ip/dns:port>...
```

Execution of the client: sends operation to the server indefinitely.
```bash
# Run it immediatly.
go run simple_cltraft.go <ip/dns:port>...

# Or if you preffer, you can build and launch it.
go build simple_cltraft.go 
{simple_cltraft|./simple_cltraft} <ip/dns:port>...
```

Execution of the interactive client: implements several operations to interact with the raft server.
```bash
# Run it immediatly.
go run interactive_cltraft.go <ip/dns:port>...

# Or if you preffer, you can build and launch it.
go build interactive_cltraft.go
{interactive_cltraft|./interactive_cltraft} <ip/dns:port>...
```

Execution of the tests: it has already defined the ip, then for interacting with new addresses you must change them.
```bash
go test -v raft_integration_test.go 
```

## How can I use just the raft module?
For using the raft module apart to another desired application, create the new main file with your application logic (the state machine), and import the raft code for creating the correspondent raft node, furthermore, don't forget about modify [the operation struct] defined in the raft code (in the future I'll manage a way for implementing a generic operation for break this dependency and convert the raft code fully modular). Its recommended to check, before starting to work with it, files like the raft code itself or the given examples for the raft node and the state machine creation under an specific service (in my case, the key-value storage service example) or the small client implementations for testing the raft node behaviour.


## Notes
- Developed with ***go1.17.2 windows/amd64.***
- It can be compiled on both linux and windows. 
- This code does not have in count the backend about the connection system in which it can be builded on, it fully depends on your own design decision (ssh, local connections, Kubernetes-Docker).

[raft github repository]: https://raft.github.io
[the operation struct]:https://github.com/ddevigner/raft-go/blob/main/internal/raft/raft.go#L84-L88
