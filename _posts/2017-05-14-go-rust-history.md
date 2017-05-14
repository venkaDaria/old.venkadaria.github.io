---
layout: post
title: Interesting languages
tags: go rust history
---

## Go
Go (часто также Golang) — компилируемый многопоточный язык программирования, разработанный компанией Google.

go run hello-world.go

или:

go build hello-world.go

hello-world

```go
package main

import "fmt"

func main() {
    fmt.Println("hello world")
}
```

[Учебник](http://golang-book.ru/)

## Rust
Rust - язык программирования от Mozilla, поддерживает функциональное и процедурное программирование.

Появился в 2010г.

$ mkdir ~/projects

$ cd ~/projects

$ mkdir hello_world

$ cd hello_world

$ rustc main.rs

$ main

Привет, мир!

```rust
fn main() {
    println!("Привет, мир!");
}
```

[Учебник](http://rurust.github.io/rust_book_ru/).