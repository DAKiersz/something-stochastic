# Go - Language Theory

## CLI

Compile the source code from one (or more) files, link with libraries and run the executable:

```shell
go run <source.go>
```

Compile and create an executable:

```shell
go build <source.go>
```

Initialise project. The command below creates a new module, that can correspond to repo that you will publish it.

```shell
go mod init <module path>
```

## Basics

### Packages

- Go programs are **constructed** by linking together packages packages. 
- A package consists of one or more source files containing functions and variables etc.
- Packages also live on a **path** - similar to your UNIX-based systems.
- Go programs start executing **at** package called `main`, which also contains the `main()` function (and `init()` that is executed prior). The `main` package is special, as it includes an entry-point.
- _"All other package names (w.r.t. main) declare a package that must be `import`ed into another package."_
- i.e., packages can be declared with a name different to `main`, which usually take a name of their current directory (`cd`), but they have to be `import`ed into another package (usually `main`).
- On that note, you can **import more packages** to your Go program with `import` paths like `fmt` or `math/rand` for more functions (akin to modules in Python, libraries in C). This is importing the package (in this instance, to `main`).
- A **complete program** in Go links the main package with imported packages, as per [this reference](https://go.dev/ref/spec#Program_execution)
### Boilerplate

```go
// A package clause starts every source file.
// Main is a special name declaring an executable, rather than a library.
package main

// Import declaration declares library packages referenced in this file.
import (
	"fmt"       // A package in the Go standard library.
	"io/ioutil" // Implements some I/O utility functions.
	"math"      // Math library with local alias m.
	"net/http"  // Yes, a web server!
	"os"        // OS functions like working with the file system
	"strconv"   // String conversions.
)
```

### Misc.

- Compile error if variable is unused - variable names must be utilised somewhere. Same with packages.
- in `Println`, a space is added between commas.

## References

* https://go.dev/tour/welcome/1
* https://go.dev/ref/spec#Program_execution (from https://stackoverflow.com/questions/42333488/package-main-and-func-main )
* https://www.golearningsource.com/fundamentals/main-package-and-main-function-in-golang/
* "Go for DevOps" (book)
