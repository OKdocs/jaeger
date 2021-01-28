# jaeger
tracing with jaeger in go


## setting up

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
