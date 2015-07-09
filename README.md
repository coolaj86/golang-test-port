golang-test-port
================

Tests wether or not a port is already in use by another application. Written in Go.

See https://coolaj86.com/articles/how-to-test-if-a-port-is-available-in-go/

Install
=======

```bash
go get github.com/coolaj86/golang-test-port

go build -o $GOPATH/bin/test-port github.com/coolaj86/golang-test-port
```

Usage
=====

Test an open port

```
test-port 65535
> TCP Port "65535" is available

echo $?
> 0
```

Test an in-use, reserved, or invalid port

```
test-port 22
> Can't listen on port "22": listen tcp :22: bind: permission denied

echo $?
> 1
```

```
test-port 8080
> Can't listen on port "8080": listen tcp :8080: bind: address already in use

echo $?
> 1
```

```
test-port sandwich
> Invalid port "sandwich": strconv.ParseUint: parsing "sandwich": invalid syntax
```
