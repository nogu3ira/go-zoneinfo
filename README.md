# go-zoneinfo
[![Build Status](https://travis-ci.org/nogu3ira/go-zoneinfo.svg?branch=master)](https://travis-ci.org/nogu3ira/go-zoneinfo) [![Go Report Card](https://goreportcard.com/badge/github.com/nogu3ira/go-zoneinfo)](https://goreportcard.com/report/github.com/nogu3ira/go-zoneinfo)

Zoneinfo embedded data in Go, helpful for applications running on Windows or if you want to load within the application, regardless of the operating system.

#### Known errors

    [ORM] Detect DB timezone: America/Araguaina open C:\Go/lib/time/zoneinfo.zip: not found path
    
    "open /go/lib/time/zoneinfo.zip: no such file or directory"
    
    open c:\go\lib\time\zoneinfo.zip: The system cannot find the file specified.
    
    zoneinfo.zip: O sistema não pode encontrar o arquivo especificado.

## Quick Example

#### Download and install in console

    go get github.com/nogu3ira/go-zoneinfo

#### Create file `test.go`
```go
package main

import "github.com/nogu3ira/go-zoneinfo"

func main() {
	tz := "America/Kentucky/Louisville"
	loc, err := zoneinfo.LoadLocation(tz)
	if err != nil {
		println("Problem in", tz, err.Error())
	} else {
		println("OK to", tz, loc)
	}
}
```
#### Build and run

    go build test.go

#### Run in Windows

    test.exe

#### Run in Linux

    ./test

#### Result if successful

    OK to America/Kentucky/Louisville 0xc0000be000

#### Result if error/fail (tz := "America/Kentucky/Loull")

    Problem in LoadLocation America/Kentucky/Loull not found

## Adding to an existing project

Replace in your project all use of:
```
    time.LoadLocation(tz)
```
To:
```
    zoneinfo.LoadLocation(tz)
```

