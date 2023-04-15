---
sidebar_position: 1
---

# Introduction

Pulse is a web framework for building web applications written in Go (Golang). It features a fast and flexible router, easy to use middleware system, and a powerful dependency injection container.

## Installation

First, download and install Go `1.19` or higher is required

Pulse is available as a module. To install it, run:

```bash
go get github.com/gopulse/pulse
```

## Hello World

```go
package main

import (
    "github.com/gopulse/pulse"
)

func main() {
    app := pulse.New()
	router := pulse.NewRouter()

	app.Router = router

    router.Get("/", func(c *pulse.Context) error {
        return c.String("Hello, World!")
    })

    app.Run(":8080")
}
```