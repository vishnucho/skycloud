---
title: '2023-07-20 Go 1.21 重點摘要'
description: 'Golang 1.21 Features'
categories: ['Tech']
tags: ['Tech']
---

## Go 1.21 important features

## 講者： Jeff

> 80/20 rule

### Release Policy

Each major Go release is supported until there are two newer major releases.

- Go 1.20 Release: 1.18, 1.19, 1.20 support

### Go 1.21

#### Fixing Loop Variable Capture

```sh
GOEXPERIMENT=loopvar go run main.go
```

```go
func main() {
  myStuff := []string{"one", "two", "three"}
  wg := sync.WaitGroup{}
  for _, v := range myStuff {
    wg.Add(1)
    go func() {
      fmt.Println(v)
      wg.Done()
    }()
  }

  wg.Wait()
}
```

Before Go 1.21 loopvar

```txt
three three three
```

After Go 1.21

```txt
one two three
```

#### New Built-ins: max, min, and clear

`max` and `min`

Before Go 1.21

```go
math.Max(1, 2)
math.Min(1, 2)
```

After Go 1.21

```go
max(1, 2)
max(x, y, 10)
max(1, 2.0, 10)
max(1, 2, 3, 4, 5)
max(s...) // invalid: slice arguments are not permitted
```

clear

```go
mySlice := []bool{true, true, true}
fmt.Printf("mySlice (before): %v \n", mySlice)
clear(mySlice)
fmt.Printf("mySlice (after): %v \n", mySlice)

myMap := map[string]bool{"one": true, "two": true, "three": true}
fmt.Printf("myMap (before): %v \n", myMap)
clear(myMap)
fmt.Printf("myMap (after): %v \n", myMap)
```

```txt
mySlice (before): [true true true]
mySlice (after): [false false false]
myMap (before): map[one:true three:true two:true]
myMap (after): map[]
```

#### New log/slog package

Usage

```go
logger := slog.New(slog.NewTextHandler(os.Stderr, nil))
logger.Info("hello", "count", 3)
// time=2022-11-08T15:28:26.000-05:00 level=INFO msg=hello count=3

logger = slog.New(slog.NewJSONHandler(os.Stdout, nil))
logger.Info("hello", "count", 3)
// {"time":"2022-11-08T15:28:26.000000000-05:00","level":"INFO","msg":"hello","count":3}
```

Level

```go
const (
 LevelDebug Level = -4
 LevelInfo  Level = 0
 LevelWarn  Level = 4
 LevelError Level = 8
)
```

Arrt

```go
slog.LogAttr(
  slog.ErrorLevel,
  "failed to brabrabra",
  slog.Int("status", 500),
  slog.Any("err", err)
)
```

## Go 1.20 important features

> Russ Cox: Go 2.0 is dead, long live with Go 1.x.

### Arena

```sh
GOEXPERIMENT=arenas go run main.go
```

```go
mem := arena.NewArena()
defer mem.Free()

for i := 0; i < 10; i++ {
  obj := arena.New[T](mem)
}

slice := arena.MakeSlice[string](mem, 0, 0)
```

> No Maps support

### context.WithCancelCause

```go
ctx, cancel := context.WithCancelCause(context.Background())
cancel(errors.New("something went wrong"))
fmt.Println(ctx.Err()) // context.Canceled
fmt.Println(context.Cause(ctx)) // something went wrong
```

### Wrapping multiple errors

```go
err1 := errors.New("first error")
err2 := errors.New("second error")
err3 := errors.New("third error")
err := errors.Join(err1, err2, err3)
fmt.Println(err)
// first error
// second error
// third error
if errors.Is(err, err1) {
  fmt.Println("err1 is err")
}

if errors.Is(err, err2) {
  fmt.Println("err2 is err")
}
```
