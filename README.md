# fish-language-server
```
                 ___
  ___======____=---=)
/T            \_--===)
[ \ (O)   \~    \_-==)
 \      / )J~~    \-=)
  \\___/  )JJ~~~   \)
   \_____/JJJ~~~~    \
   / \  , \J~~~~~     \
  (-\)\=|\\\~~~~       L__
  (\\)  (\\\)_           \==__
   \V    \\\) ===_____   \\\\\\
          \V)     \_) \\\\JJ\J\)
                      /J\JT\JJJJ)
                      (JJJ| \UUU)
                       (UU)
```
# Reading Prereqs
- [Language Server Protocol](https://microsoft.github.io/language-server-protocol/)\
- [Fish Shell](https://fishshell.com/)

# Background
Language Server Protocol is the current state of the art way to implement IDE functionality in any text editor.
The number of projects maintained to achieve IDE functionality is simplified to `editors + programmingLanguages` from `editors * programmingLanguages`.

In plain words this means that the use of [Language Server Protocol](https://microsoft.github.io/language-server-protocol/) prevents the need to re-invent the wheel for every editor.  Autocomplete can be implemented *once* per programming language.  The same goes for autoformatting, linting, jumping to definition etc.  Each text editor then implements a client following Language Server Protocol's specification.  After implementing the client the editor will gain access to all of the underlying operations.

## Fish
```
fish is a smart and user-friendly command line
shell for Linux, macOS, and the rest of the family.
```
Fish is an amazing shell that is rapidly growing.

There is currently no language server for fish so I think implementing one is a great open source contribution.

This will also be a great opportunity to learn about the Fish shell (I use fish as my shell over bash on every machine I own).

# Getting Started
To get started working on this project you should probably familiarize yourself with language server and language server clients.
The easiest way to do this is to just set up a language server client on your local workstation.

Here is a list of of common language server clients.
- [vim](https://github.com/prabirshrestha/vim-lsp)
- (atom)[https://github.com/atom/atom-languageclient]
- You can also just google `$EDITOR language server client`
- ** Note: VSCode already has language server build in.  [Docs here](https://code.visualstudio.com/api/language-extensions/language-server-extension-guide)

Follow the readme for the relevent repo and let me know if you encounter any issues setting it up/getting it configured.

# Roadmap
The features in the following road map tables are listed in no specific order.

| Run Mode | Description| Implementation Status |
|--|--|--|
|`stdin/stdout`| | ❌|
|[`jsonrpc2`](https://www.jsonrpc.org/specification)| | ❌|
|[`websocket`](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)| | ❌|
|[`grpc`](https://grpc.io/)| | ❌|

| Lsp Feature | Description| Implementation Status |
|--|--|--|
|`:LspCodeAction`| Gets a list of possible commands that can be applied to a file so it can be fixed (quick fix) | ❌|
|`:LspDeclaration`| Go to the declaration of the word under the cursor, and open in the current window | ❌|
|`:LspDefinition`| Go to the definition of the word under the cursor, and open in the current window | ❌|
|`:LspDocumentDiagnostics`| Get current document diagnostics information | ❌|
|`:LspDocumentFormat`| Format entire document | ❌|
|`:LspDocumentRangeFormat`| Format document selection | ❌|
|`:LspDocumentSymbol`| Show document symbols | ❌|
|`:LspHover`| Show hover information | ❌|
|`:LspImplementation` | Show implementation of interface in the current window | ❌|
|`:LspNextDiagnostic`| jump to next diagnostic (all of error, warning, information, hint) | ❌|
|`:LspNextError`| jump to next error | ❌|
|`:LspNextReference`| jump to next reference to the symbol under cursor | ❌|
|`:LspNextWarning`| jump to next warning | ❌|
|`:LspPeekDeclaration`| Go to the declaration of the word under the cursor, but open in preview window | ❌|
|`:LspPeekDefinition`| Go to the definition of the word under the cursor, but open in preview window | ❌|
|`:LspPeekImplementation`| Go to the implementation of an interface, but open in preview window | ❌|
|`:LspPeekTypeDefinition`| Go to the type definition of the word under the cursor, but open in preview window | ❌|
|`:LspPreviousDiagnostic`| jump to previous diagnostic (all of error, warning, information, hint) | ❌|
|`:LspPreviousError`| jump to previous error | ❌|
|`:LspPreviousReference`| jump to previous reference to the symbol under cursor | ❌|
|`:LspPreviousWarning`| jump to previous warning | ❌|
|`:LspReferences`| Find references | ❌|
|`:LspRename`| Rename symbol | ❌|
|`:LspStatus` | Show the status of the language server | ❌|
|`:LspTypeDefinition`| Go to the type definition of the word under the cursor, and open in the current window | ❌|
|`:LspTypeHierarchy`| View type hierarchy of the symbol under the cursor | ❌|
|`:LspWorkspaceSymbol`| Search/Show workspace symbol | ❌|

# Implementation
```
 ------------------------
   \
    \
     \   ,_---~~~~~----._         
  _,,_,*^____      _____``*g*\"*, 
 / __/ /'     ^.  /      \ ^@q   f 
[  @f | @))    |  | @))   l  0 _/  
 \`/   \~____ / __ \_____/    \   
  |           _l__l_           I   
  }          [______]           I  
  ]            | | |            |  
  ]             ~ ~             |  
  |                            |   
   |                           |   
```

The code structure is pretty simple.  The program will be implemented in [Golang](https://golang.org/) because the work is to be distributed amongst 3-5 people.  My reasoning here is that golang is a super simple programming language, highly in demand on the job market, and is extremely easy to read.

The top level main file accepts a series of command line arguments defining how the Language Server should run.  A great example of this is in the `main.go` file of the (golang Language Server)[https://github.com/sourcegraph/go-langserver].

I'll make an initial commit adding a main function with stubbed out callbacks for each of the LSP function handlers.  These will just return an unimplemented error that the language clients will then report back to the user.

# Contribution Structure
I'll open a Github issue for each of the LSP features.  I'll try to email you guys the most "bite sized" pieces first.

## What you'll gain from contributing
- knowledge of Language Servers/Language Clients (this is a huge boost to development quality of life)
- learn about fish shell
- golang resume project (golang is HOT amongst college recruiters)
