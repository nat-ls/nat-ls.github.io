---
title: Natural Language Server (NatLS)
toc: false
---

[![GitHub Releases](https://img.shields.io/github/v/release/markusamshove/natls?color=blue)](https://github.com/MarkusAmshove/natls/releases/tag/v0.16)

###

NatLS is a language server implementation for the [Natural language](https://en.wikipedia.org/wiki/ADABAS#Natural_(4GL)) created by Software AG.

It aims to provide useful features to drive daily development in Natural and provide a modern approach for development tools for Natural.

A [VS Code extension](https://marketplace.visualstudio.com/items?itemName=markusamshove.vscode-natural) is available to use the language server in Visual Studio Code. This extension serves as a reference client implementation and is already used for daily Natural development.

The latest release of tools are available on [GitHub Releases](https://github.com/MarkusAmshove/natls/releases/tag/v0.16).

## Explore

{{< cards >}}
  {{< card link="docs" title="Documentation" icon="book-open" >}}
  {{< card link="docs/lsp-features" title="Features" icon="sparkles" >}}
  {{< card link="diagnostics" title="Diagnostics" icon="exclamation" >}}
  {{< card link="https://marketplace.visualstudio.com/items?itemName=markusamshove.vscode-natural" title="VSCode extension" icon="puzzle" >}}
{{< /cards >}}

## Static code analysis with NatLint

NatLS includes a static code analysis tool called NatLint, which can also be used standalone without the language server.

It features analysis rules that help to find potential bugs and code smells in Natural code. Rules can span different statement types to find potential issues that are hard to find by hand.

As an example, in the following code snippet a file path is constructed using `COMPRESS` and then used in a `DEFINE WORK FILE` statement.

```natural
COMPRESS '$HOME/folder' #FILENAME INTO #FILEPATH 
DEFINE WORK FILE 1 #FILEPATH
```

NatLint recognizes that `#FILEPATH` is compressed without `LEAVING NO` so that the resulting file path will have spaces in it. [NL015](/diagnostics/nl015/) will catch this and report it, even when those two statements are far apart in the code.

