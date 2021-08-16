# Golang concepts

## Module path
The module path, used in commands such as `go init`, is where the go tool will
look for go modules. It's also used in imports.

## Exported names
Names started with capital letters are known as exported names and can be used
outside the current package.

## Go main package
In Go, code executed as an application must be in a main package.

## Formatting
- Use `go fmt`;
- Use tabs with a span of 4 characters;
- There's no line length limit;
- Use spaces to emphasize operations. E.g. `x<<8 + y<<16`;

## Naming
### Packages
> By convention, packages are given lower case, single-word names.

> Another convention is that the package name is the base name of its source
> directory; the package in src/encoding/base64 is imported as
> "encoding/base64" but has name base64,

[Golang tutorials](https://golang.org/doc/tutorial/)
[Effective Go](https://golang.org/doc/effective_go)

#golang
