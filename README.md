# jaeger
tracing with jaeger in go


## setting up
imports
```go 
"contrib.go.opencensus.io/exporter/jaeger"
"go.opencensus.io/trace"
```

set up
```go
je, err := jaeger.NewExporter(jaeger.Options{
		AgentEndpoint: endpoint,
		Process: jaeger.Process{
			ServiceName: name,
			Tags:        []jaeger.Tag{},
		},
	})

// handle error

trace.RegisterExporter(je)
trace.ApplyConfig(trace.Config{})

```
The New() function can be placed in a separate package.
Variables `name` is identifying string, `endpoint` is hostname:6831 or another endpoint, but usually, should hostname:6831.

Thereafter import this package into your main and call the New() function from there
```go 
jaeger := tracing.New(args...)
	defer jaeger.Flush()

```

## tracing spans

```go
import "go.opencensus.io/trace"
```
source

```go
ctx, span := trace.StartSpan(ctx, name) // name to identify
	defer span.End()

	span.AddAttributes(
		trace.StringAttribute("key", value),
	)
```
other attributes like bool, int etc exist 
these can be searched later in jaeger ui to different traces within a "function call span"

## send to jaeger server

## jaeger ui
