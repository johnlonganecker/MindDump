## GO

### cross compile go

** compile linux binary on macos **
```
GOOS=linux GOARCH=386 CGO_ENABLED=0 go build -o al-broker main.go
```

** useful info **
http://stackoverflow.com/questions/12168873/cross-compile-go-on-osx

### CURL to Go

** Nice way to learn http in go if you already know curl **

http://mholt.github.io/curl-to-go/

### Make a ReadCloser

ioutil.NopCloser(bytes.NewReader([]byte("foo")))

### streaming into json encoder/decoder
When possible use streams `ioutil.ReadAll(r io.Reader)` should only be used when necessary

** example from **
http://blog.golang.org/json-and-go

```go
package main

import (
    "encoding/json"
    "log"
    "os"
)

func main() {
    dec := json.NewDecoder(os.Stdin)
    enc := json.NewEncoder(os.Stdout)
    for {
        var v map[string]interface{}
        if err := dec.Decode(&v); err != nil {
            log.Println(err)
            return
        }
        for k := range v {
            if k != "Name" {
                delete(v, k)
            }
        }
        if err := enc.Encode(&v); err != nil {
            log.Println(err)
        }
    }
}
```

### interface zero value

is nil
