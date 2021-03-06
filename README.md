# jshint2.vim

Lightweight, customizable and functional Vim plugin for [JSHint](http://jshint.com/) integration.

![jshint2.vim](https://dl.dropbox.com/s/ab95l1gnbub8m04/jshint2.vim.png)

## Features

* Linting whole file or selected lines without saving to disk.
* Finding configuration files inside linting file path or upper in directories.
* Using project-specific, locally installed version of jslint (i.e. installed as dev dependency) if available.
* Setting lint flags from command line with autocompletion.
* Optionally opening list of linting errors with useful shortcuts.
* Optionally validating files after reading or saving.
* Working on Linux, Windows (with JSHint 2.1.5 and newer) and OS X.

## Installation

1. [Install Node.js](http://nodejs.org/download/).
2. [Install JSHint](http://jshint.com/install/), either globally or locally.
3. Place [.jshintrc](http://www.jshint.com/docs/options/) into your `~`, optionally place it into your project directory.
4. [Install Pathogen](https://github.com/tpope/vim-pathogen#installation), necessarily check [super-minimal example](https://github.com/tpope/vim-pathogen#runtime-path-manipulation).
5. Clone plugin into your `~/.vim/bundle/jshint2.vim/`.
6. ???
7. PROFIT!

## Usage

Use `:JSHint` command inside Vim to lint whole file or `:'<,'>JSHint` to lint only selected lines.  
Add `!` to suppress opening error list (number of lint errors still will be shown) — `:JSHint!`.  
Add space and use tab key to complete space separated lint flags — `:JSHint white:true eqeqeq:true`.  
Use `-` to ignore errors by their codes — `:JSHint -E001 -W002 -I003`.  

## Configuration

Set JSHint command path:

```vim
let jshint2_command = '~/path/to/jshint'
```
**Note** You don't need to set this if JSHint was installed via npm, either locally or globally. If you specified JSHint as a development dependency in your `package.json`, jshint2.vim will find and use that exact version.

Lint JavaScript files after reading it:

```vim
let jshint2_read = 1
```

Lint JavaScript files after saving it:

```vim
let jshint2_save = 1
```

Do not automatically close orphaned error lists:
```vim
let jshint2_close = 0
```

Skip lint confirmation for non JavaScript files:

```vim
let jshint2_confirm = 0
```

Do not use colored messages:

```vim
let jshint2_color = 0
```

Hide error codes in error list (if you don't use error ignoring or error codes confuses you):

```vim
let jshint2_error = 0
```

Set default height of error list:

```vim
let jshint2_height = 20
```

## Error List Shortcuts

`t` — open error in new tab.  
`v` — open error in new vertical split.  
`s` — open error in new horizontal split.  
`i` — ignore selected error.  
`n` — scroll to selected error.  
`q` — close error list.  

## Tips

Quick lint mapping:

```vim
" jshint validation
nnoremap <silent><F1> :JSHint<CR>
inoremap <silent><F1> <C-O>:JSHint<CR>
vnoremap <silent><F1> :JSHint<CR>

" show next jshint error
nnoremap <silent><F2> :lnext<CR>
inoremap <silent><F2> <C-O>:lnext<CR>
vnoremap <silent><F2> :lnext<CR>

" show previous jshint error
nnoremap <silent><F3> :lprevious<CR>
inoremap <silent><F3> <C-O>:lprevious<CR>
vnoremap <silent><F3> :lprevious<CR>
```

## Author & License

Written by [Nikolay S. Frantsev](http://frantsev.ru/) under [GNU GPL 3 License](http://www.gnu.org/licenses/gpl.html).
