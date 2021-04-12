[vim-lsp][] + [ALE][]
=====================

[vim-lsp-ale][] is a Vim plugin for bridge between [vim-lsp][] and [ALE][].

When simply using ALE and vim-lsp, both plugins run LSP servers respectively. vim-lsp-ale takes
diagnostics results from vim-lsp and passes them to ALE. The diagnostics results are shown as part
of lint results by ALE.

## Installation

Install [vim-lsp][], [ale][ALE], [vim-lsp-ale][] with your favorite package manager or `:packadd` in your `.vimrc`.

An exmaple with [vim-plug](https://github.com/junegunn/vim-plug):

```viml
Plug 'dense-analysis/ale'
Plug 'prabirshrestha/vim-lsp'
Plug 'rhysd/vim-lsp-ale'
```

## Usage

Register LSP servers you want to use with `lsp#register_server` and set `vim-lsp` linter to `g:ale_linters`
for filetypes you want to check with vim-lsp.

The following example configures `gopls` to check Go sources.

```vim
if executable('gopls')
    autocmd User lsp_setup call lsp#register_server({
        \ 'name': 'gopls',
        \ 'cmd': ['gopls'],
        \ 'allowlist': ['go', 'gomod'],
        \ })
endif
let g:ale_linters = {
    \   'go': ['vim-lsp'],
    \ }
```

This plugin configures vim-lsp and ALE automatically unless `g:lsp_ale_setup_variables` is not set.

- Disable showing diagnostics results from vim-lsp since ALE will show the results
- Disable LSP support of ALE since vim-lsp handles all LSP requests/responses

You don't need to set several variables in your `.vimrc`.

## License

Licensed under [the MIT license](./LICENSE).

[vim-lsp]: https://github.com/prabirshrestha/vim-lsp
[ALE]: https://github.com/dense-analysis/ale
[vim-lsp-ale]: https://github.com/rhysd/vim-lsp-ale
