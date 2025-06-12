GoTodo
GoTodo is a Go package and CLI tool that scans your project for TODO comments and generates a todo.md file in Markdown format.
Installation
Install the CLI tool:
go install github.com/yourusername/gotodo/cmd/gotodo@latest

Add as a dependency to your Go project:
go get github.com/yourusername/gotodo

Usage
As a Command-Line Tool
Run in your project directory:
gotodo

This scans for TODO comments in files with extensions .go, .js, .html, and .css, and generates todo.md.
As a Library
package main

import (
"fmt"
"github.com/yourusername/gotodo/internal/gotodo"
)

func main() {
cfg := gotodo.Config{
Directory: ".",
Extensions: []string{".go", ".js"},
OutputFile: "todo.md",
}
todos, err := gotodo.FindTodos(cfg)
if err != nil {
fmt.Printf("Error: %v\n", err)
return
}
err = gotodo.GenerateTodoMD(todos, cfg.OutputFile)
if err != nil {
fmt.Printf("Error: %v\n", err)
return
}
fmt.Printf("Generated %s with %d tasks\n", cfg.OutputFile, len(todos))
}

Example Output
For a project with:
main.go:
// TODO: add page for the login screen

index.html:

<!-- TODO: fix CSS for mobile view -->

The generated todo.md will be:

# Project TODO List

## File: main.go

- [ ] add page for the login screen (Line 1)

## File: index.html

- [ ] fix CSS for mobile view (Line 1)

Customization

Extensions: Modify Config.Extensions to scan different file types.
Output File: Change Config.OutputFile to specify a different output path.
Directory: Set Config.Directory to scan a specific directory.

License
MIT
