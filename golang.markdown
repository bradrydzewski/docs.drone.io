---
layout: default
title: Go
tagline: Building Go Projects
icon: golang02
---

The following Go versions are available to your build:

 * Go1 (version 1.1.2 linux/amd64)

## Go Path

When compiling your Go program, it is important that your repository is cloned
to the path that matches your Go program's full package name or desired binary
name.

When creating your project we will attempt to automatically set your checkout
path based on the name and URL of the source repository:

![Go Path](img/screenshot_golang_build-path.png)

You can change the default checkout path at the
**project** > **settings** > **repository** page.

## Dependencies

Use the **go get** command to install your project's dependencies:

```
go get code.google.com/p/codesearch/index
go get github.com/petar/GoLLRB/llrb
```

## Build

Use the **go build** command to compile your code:

```
go build
``` 

## Test

Use the **go test** command to run unit tests:

```
go test -v
```

You may use alternative unit test frameworks, such as [gocheck](http://labix.org/gocheck):

```
go get launchpad.net/gocheck
go test -gocheck.v
```
<a name="cross-compile"></a>
## Cross Compiling

You may want to cross-compile your Go binaries to run on multiple platforms.
This is possible but will require a bit of extra setup and might add 1-2 minutes
to your build.

First you can build / test your project as you normally would targeting
the default linux/amd64 platform:

```
go build
go test
```

Now we need to compile Go for other platforms. First, however, we need to
remove AppEngine which has platform-specific code and will cause failures:

```
rm -rf /usr/local/go/src/pkg/appengine
rm -rf /usr/local/go/src/pkg/appengine_internal
```

Now we compile Go for our target platforms:

```
pushd /usr/local/go/src
GOOS=windows GOARCH=amd64 ./make.bash --no-clean 2> /dev/null 1> /dev/null
GOOS=darwin  GOARCH=amd64 ./make.bash --no-clean 2> /dev/null 1> /dev/null
popd
```

And finally we can run `go build` for multiple platforms:

```
GOOS=windows GOARCH=amd64 go build
GOOS=darwin  GOARCH=amd64 go build
```

CAVEATS:

* You cannot cross-compile if you use CGO
* You cannot `go test` your cross-compiled binaries

--------------------------------------------------------------------------------

## Examples

### Example 1

Example build script for [web.go](https://github.com/hoisie/web), a lightweight
web framework written in Go.

The project build path is automatically set to `github.com/hoisie/web`

```
go get
go build
go test -v
```

### Example 2

Example build script for [jkl](https://github.com/bradrydzewski/jkl), a
Jekyll-based static site generator written in Go.

The project build path is automatically set to `github.com/bradrydzewski/jkl`

```
go get
go build
go test -v
```

We can optionally archive the **jkl** binary that is generated during the build.
For more information, please see the [build artifact documentation](/archive.html).
