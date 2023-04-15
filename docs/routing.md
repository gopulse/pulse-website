---
sidebar_position: 2
---

# Routing

Pulse comes with a fast and flexible router. It supports named parameters, regular expressions, and wildcard routes, grouping, static files

# Handlers

Pulse supports the following handler types:

```go
// Http Method Handlers
func (r *Router) Get(path string, handlers ...Handler)
func (r *Router) Post(path string, handlers ...Handler)
func (r *Router) Put(path string, handlers ...Handler)
func (r *Router) Delete(path string, handlers ...Handler)
func (r *Router) Patch(path string, handlers ...Handler)
func (r *Router) Head(path string, handlers ...Handler)
func (r *Router) Options(path string, handlers ...Handler)
func (r *Router) Connect(path string, handlers ...Handler)
func (r *Router) Trace(path string, handlers ...Handler)
```

# Basic Routing

```go
package main

import (
    "github.com/gopulse/pulse"
)

func main() {
    app := pulse.New()
    router := pulse.NewRouter()

    app.Router = router

    router.Get("/list", func(c *pulse.Context) error {
        return c.String("GET /list")
    })
    
    router.Post("/store", func(c *pulse.Context) error {
        return c.String("POST /store")
    })

    app.Run(":8080")
}
```

# Named Parameters

```go
package main

import (
    "github.com/gopulse/pulse"
)

func main() {
    app := pulse.New()
    router := pulse.NewRouter()

    app.Router = router

    router.Get("/user/:id", func(c *pulse.Context) error {
        return c.String("GET /user/" + c.Param("id"))
    })

    app.Run(":8080")
}
```