---
title: Vim 配置
sidebar: mydoc_sidebar
permalink: others_vim.html
folder: mydoc
---

{{site.data.alerts.callout_primary}}
<p>温斯顿·雷德莫尔：我们有工具！我们是天才！</p>
<p>彼得·温克曼：现在是 Miller 时间！</p>
<p align="right">—— 《捉鬼敢死队》(1984)</p>
{{site.data.alerts.end}}

更多信息可见我的 Github repository：[Vim-LaTeX-Configuration](https://github.com/anyeZHY/Vim-LaTeX-Configuration).

## .vimrc 文件配置

```vb
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
" Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Install L9 and avoid a Naming conflict if you've already installed a
" different version somewhere else.
" Plugin 'ascenator/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ


"-------------------------------------------------------------------
" Plugins Here
set rtp+=~/.vim/bundle/Vundle.vim  
call vundle#begin()
Plugin 'VundleVim/Vundle.vim'
Plugin 'https://github.com/vim-latex/vim-latex'
Plugin 'SirVer/ultisnips'
Plugin 'honza/vim-snippets'
Plugin 'Chiel92/vim-autoformat'
Plugin 'https://github.com/bling/vim-airline'
Plugin 'kien/rainbow_parentheses.vim'
Plugin 'https://github.com/scrooloose/nerdtree'
Plugin 'crusoexia/vim-monokai'
call vundle#end()            " required
filetype plugin indent on    " required

set nu " 行号
set relativenumber " 相对行号
colo monokai " color字体配色
nnoremap <C-V> <C-W><C-V>
nnoremap <C-S> <C-W><C-S>

"-------------------------------------------------------------------
" LaTeX Settings
set grepprg=grep\ -nH\ $*
let g:tex_flavor='latex'
set iskeyword+=:
"autocmd Filetype tex setl updatetime=1
let g:Tex_ViewRule_pdf = 'skim'
let g:livepreview_previewer = 'open -a Skim'
let g:Tex_Leader=';'

"中文支持
let g:Tex_CompileRule_pdf = 'xelatex -synctex=1 --interaction=nonstopmode $*'
let g:vimtex_compiler_latexmk_engines = {'_':'-xelatex'}
let g:vimtex_compiler_latexrun_engines ={'_':'xelatex'}

" bib调试
let g:Tex_MultipleCompileFormats='pdf,bibtex,pdf'

"
" remove warnings
let g:vimtex_quickfix_ignore_filters = [
  \'Package',
  \]
let g:vimtex_quickfix_enabled = 0
let g:vimtex_quickfix_open_on_warning=0

"-------------------------------------------------------------------
"UltiSnips
let g:UltiSnipsExpandTrigger = '<tab>'
let g:UltiSnipsJumpForwardTrigger = '<tab>'
let g:UltiSnipsJumpBackwardTrigger = '<s-tab>'

"-------------------------------------------------------------------
" 'Chiel92/vim-autoformat' Settings
nnoremap <F6> :Autoformat<CR>
let g:autoformat_autoindent = 0
let g:autoformat_retab = 0
let g:autoformat_remove_trailing_spaces = 0
let g:formatdef_latexindent = '"latexindent -"'

"-------------------------------------------------------------------
" Commenting blocks of code.
autocmd FileType c,cpp,java,scala let b:comment_leader = '// '
autocmd FileType sh,ruby,python   let b:comment_leader = '# '
autocmd FileType conf,fstab       let b:comment_leader = '# '
autocmd FileType tex              let b:comment_leader = '% '
autocmd FileType mail             let b:comment_leader = '> '
autocmd FileType vim              let b:comment_leader = '" '
noremap <silent> ,cc :<C-B>silent <C-E>s/^/<C-R>=escape(b:comment_leader,'\/')<CR>/<CR>:nohlsearch<CR>
noremap <silent> ,cu :<C-B>silent <C-E>s/^\V<C-R>=escape(b:comment_leader,'\/')<CR>//e<CR>:nohlsearch<CR>

"-------------------------------------------------------------------
let g:rbpt_colorpairs = [
                        \ ['brown',       'RoyalBlue3'],
                        \ ['Darkblue',    'SeaGreen3'],
                        \ ['darkgray',    'DarkOrchid3'],
                        \ ['darkgreen',   'firebrick3'],
                        \ ['darkcyan',    'RoyalBlue3'],
                        \ ['darkred',     'SeaGreen3'],
                        \ ['darkmagenta', 'DarkOrchid3'],
                        \ ['brown',       'firebrick3'],
                        \ ['gray',        'RoyalBlue3'],
                        \ ['darkmagenta', 'DarkOrchid3'],
                        \ ['Darkblue',    'firebrick3'],
                        \ ['darkgreen',   'RoyalBlue3'],
                        \ ['darkcyan',    'SeaGreen3'],
                        \ ['darkred',     'DarkOrchid3'],
                        \ ['red',         'firebrick3'],
                        \ ]
let g:rbpt_max = 16
let g:rbpt_loadcmd_toggle = 0
au VimEnter * RainbowParenthesesToggle
au Syntax * RainbowParenthesesLoadRound
au Syntax * RainbowParenthesesLoadSquare
au Syntax * RainbowParenthesesLoadBraces

"-------------------------------------------------------------------
nnoremap ,m :NERDTreeToggle<CR>
nnoremap m, :NERDTreeToggle<CR>
autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTreeType") &&b:NERDTreeType == "primary") | q | endif
" autocmd VimEnter * NERDTree

```




{% include links.html %}