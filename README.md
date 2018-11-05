# logrwap

[![GoDoc](https://godoc.org/github.com/digineo/go-logwrap?status.svg)](https://godoc.org/github.com/digineo/go-logwrap)
[![Go Report Card](https://goreportcard.com/badge/github.com/digineo/go-logwrap)](https://goreportcard.com/report/github.com/digineo/go-logwrap)

A thin layer around Go's standard library logger. It was extracted from
`github.com/digineo/fastd/fastd`.

`logwrap` exports two functions, `Infof()` and `Errorf()`. Without
any further configuration, the forward messages to `golang.org/pkg/log`.

To plug-in your own favorite logger, call `logwrap.SetLogger(Logger)`.
`Logger` only needs to satisfy this interface:

```go
type Logger interface {
  Infof(format string, args ...interface{})
  Errorf(format string, args ...interface{})
}
```

where both methods implement `fmt.Printf` semantics.

This should be compatible with:

- [sirupsen/logrus](https://github.com/sirupsen/logrus) - both `*logrus.Entry` and `*logrus.Logger`
- [uber-go/zap](https://github.com/uber-go/zap) - `*zap.SugaredLogger`
- [google/logger](https://github.com/google/logger) - `*logger.Logger`
