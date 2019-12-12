[![GoDoc](https://godoc.org/github.com/next-lucasmenendez/interpretext-text-summarizer?status.svg)](https://godoc.org/github.com/next-lucasmenendez/interpretext-text-summarizer)
[![Go Report Card](https://goreportcard.com/badge/github.com/next-lucasmenendez/interpretext-text-summarizer)](https://goreportcard.com/report/github.com/next-lucasmenendez/interpretext-text-summarizer)

# Interpretext text summarizer
Gobstract package make extraction summaries from text provided. The algorithm measures sentence relations (measuring relevant token similarity), position and length to pick the text highlights.

## Installation
### PoS Tagging
For more information check instructions [here](https://github.com/next-lucasmenendez/interpretext-text-summarizer#train-corpus).

### Abstracts
```bash
export MODELS="<postagging trained models folder path>"

go get github.com/next-lucasmenendez/interpretext-text-summarizer
```

### Use it
```go
package main

import (
    "fmt"
    "io/ioutil"
    summarizer "github.com/next-lucasmenendez/interpretext-text-summarizer"
)

func main() {
    var input string
    if raw, err := ioutil.ReadFile("input"); err != nil {
        fmt.Println(err)
        return
    } else {
        input = string(raw)
    }

    if text, err := summarizer.NewText(input, "es"); err != nil {
        fmt.Println(err)
    } else {
        var summary []string = text.Summarize()
        for _, sentence := range summary {
            fmt.Println(sentence)
        }
    }    
}
```