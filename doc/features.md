## Features

This incomplete list tracks noteble features currently implemented or planned.

- [x] Goto definition. `textDocument/definition`
  - [x] References to parameters, `let` and `rec {}` bindings.
  - [x] Relative paths.
- [x] Find references. `textDocument/reference`
  - [x] Parameters, `let` and `rec {}` bindings.
  - [x] With expression.
- [x] Completion. `textDocument/completion`
  - [x] Builtin names.
    - With documentations.
  - [x] Local bindings and rec-attrset fields.
  - [x] Keywords.
  - [ ] Attrset fields.
- [x] Diagnostics. `textDocument/publishDiagnostics`
  - [x] Syntax errors. 
  - [x] Hard semantic errors reported as parse errors by Nix, like duplicated keys in attrsets.
  - [x] Undefiend names.
  - [x] Warnings of legacy syntax.
  - [x] Warnings of unnecessary syntax.
  - [x] Warnings of unused bindings, `with` and `rec`.
  - [ ] Client pulled diagnostics.
  - [x] Custom filter
    - You can disable some diagnostic messages via LSP setting `diagnostics.ignored`,
      which accepts an array of ignored diagnostic code strings,
      eg. `["unused_binding","unused_with"]`.
      The code of diagnostics is usually shows in parentheses together with the message.

      See documentations of your editor about how to set LSP settings.

- [x] Expand selection. `textDocument/selectionRange`
- [x] Renaming. `textDocument/renamme`, `textDocument/prepareRename`
  - [x] Identifiers in parameters and bindings, from `let`, rec and non-rec attrsets.
  - [x] Static string literal bindings.
  - [x] Merged path-value binding names.
  - [x] Names introduced by `inherit`.
  - [x] Names used by `inherit`.
  - [ ] Conflict detection.
  - [x] Rename to string literals.
- [x] Semantic highlighting. `textDocument/semanticTokens/{range,full}`
  - [ ] Delta response. `textDocument/semanticTokens/full/delta`
  - :warning: Currently it has performance issue for large files.
    It may be slow to respond when editing `all-packages.nix`.

    [`coc.nvim`] doesn't enable semantic highlighting by default.
    You need to manually enable it in settings.
    ```json
    {
      "semanticTokens": { "filetypes": ["nix"] }
    }
    ```

    [`coc.nvim`]: https://github.com/neoclide/coc.nvim


- [x] Hover text. `textDocument/hover`.
  - [x] Show kind of names.
  - [x] Documentation for builtin names.
- [x] File symbols with hierarchy (aka. outline). `textDocument/documentSymbol`
- [ ] Cross-file analysis.
- [ ] Multi-threaded.