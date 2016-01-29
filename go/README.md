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
