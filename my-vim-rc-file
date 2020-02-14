"this is a function that is called to spell check what you have written
func! WordProcessorMode()
    setlocal textwidth=80
    setlocal smartindent
    setlocal spell spelllang=en_us
    setlocal noexpandtab
endfu

"the alias of the function is WP
com! WP call WordProcessorMode()



" 256-color terminal
set t_Co=256

"set text wrap
set tw=79


"switch on line numbering
set number

" syntax highlighting
syntax on

" map cut & paste to what they bloody should be
vnoremap <C-c> "+y
vnoremap <C-x> "+x
map <C-v> "+gP

" sane text files
set fileformat=unix
set encoding=utf-8

" sane editing
set tabstop=4
set shiftwidth=4
set softtabstop=4

" convert all typed tabs to spaces
set expandtab

"autocompletion with ctrl+space
inoremap <c-space> <c-n>
inoremap <Nul> <c-n>

"ctags mapper
map <f12> :!ctags -R .<cr>


"now this is for vundle package manager
set nocompatible              " be iMproved, required
filetype off                  " required

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

Plugin 'VundleVim/Vundle.vim'

Plugin 'w0ng/vim-hybrid'

Plugin 'tpope/vim-commentary'

Plugin 'scrooloose/nerdtree'

Plugin 'wincent/command-t'

Plugin 'vim-scripts/Emmet.vim'

Plugin 'fholgado/vim-autoclose'

Plugin 'Valloric/YouCompleteMe'

Plugin 'Shougo/vimproc.vim'

Plugin 'Quramy/tsuquyomi'

Plugin 'leafgarland/typescript-vim'

Plugin 'vim-syntastic/syntastic'

Plugin 'arnaud-lb/vim-php-namespace'

Plugin 'tpope/vim-surround'

Plugin 'skammer/vim-css-color'

Plugin 'easymotion/vim-easymotion'

Plugin 'itchyny/lightline.vim'

Plugin 'maksimr/vim-jsbeautify'

Plugin 'jnwhiteh/vim-golang'

Plugin 'mdempsky/gocode', {'rtp': 'vim/'}

Plugin 'fatih/vim-go'

Plugin 'JamshedVesuna/vim-markdown-preview'

Plugin 'johngrib/vim-game-snake'


call vundle#end()            " required


filetype plugin indent on    " required

"this is for hybrid theme
syntax enable
set background=dark
colorscheme hybrid

"font type and size
if has("gui_running")
    if has("gui_gtk2")
        set guifont=Inconsolata\ 12
    elseif has("gui_macvim")
        set guifont=Menlo\ Regular:h14
    elseif has("gui_win32")
        set guifont=Consolas:h11:cANSI
    endif
endif



"nerd tree setting
"start nerd tree as vim starts
autocmd vimenter * NERDTree
"open a NERDTree automatically when vim starts up if no files were specified
autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 0 && !exists("s:std_in") | NERDTree | endif
"map a specific key or shortcut to open NERDTree
map <C-n> :NERDTreeToggle<CR>
"open NERDTree automatically when vim starts up on opening a directory?  autocmd StdinReadPre * let s:std_in=1
autocmd VimEnter * if argc() == 1 && isdirectory(argv()[0]) && !exists("s:std_in") | exe 'NERDTree' argv()[0] | wincmd p | ene | endif
"map f2 to toggle nerdtree on and off
map <F2> :NERDTreeToggle<CR>
let g:NERDTreeWinSize = 50


"vim commentary
noremap <leader>/ :Commentary<cr>


"mapping swapping between tabs
nnoremap H gT
nnoremap L gt


"vim autoclose in should be deativated in vimrc because one quotation mark is
"used for commenting
let g:autoclose_vim_commentmode = 1

"youcomplete me settings
let g:ycm_global_ycm_extra_conf = '~/.vim/bundle/YouCompleteMe/.ycm_extra_conf.py'
let g:ycm_auto_trigger = 1
let g:ycm_min_num_of_chars_for_completion = 2



"this is for syntastics syntatic error  checking plugin
set statusline+=%#warningmsg#
set statusline+=%{SyntasticStatuslineFlag()}
set statusline+=%*

let g:syntastic_always_populate_loc_list = 1
let g:syntastic_auto_loc_list = 1
let g:syntastic_check_on_open = 1
let g:syntastic_check_on_wq = 0

"typescript autocompletion
let g:tsuquyomi_completion_detail = 1
let g:tsuquyomi_disable_quickfix = 1
let g:syntastic_typescript_checkers = ['tsuquyomi'] " You shouldn't use 'tsc' checker.

let g:tsuquyomi_use_local_typescript = 0
let g:tsuquyomi_use_dev_node_module = 0


set completeopt-=preview

"undo persistent changes
if has('persistent_undo')      "check if your vim version supports it
    set undofile                 "turn on the feature  
    set undodir=$HOME/.vim/undo  "directory where the undo files will be stored
endif



"beautify html
map <c-f> :call JsBeautify()<cr>
" or
autocmd FileType javascript noremap <buffer>  <c-f> :call JsBeautify()<cr>
" for json
autocmd FileType json noremap <buffer> <c-f> :call JsonBeautify()<cr>
" for jsx
autocmd FileType jsx noremap <buffer> <c-f> :call JsxBeautify()<cr>
" for html
autocmd FileType html noremap <buffer> <c-f> :call HtmlBeautify()<cr>
" for css or scss
autocmd FileType css noremap <buffer> <c-f> :call CSSBeautify()<cr>

"lightline status bar settings   
set laststatus=2
if !has('gui_running')
    set t_Co=256
endif
set noshowmode

"set up autocomplete for html
:set omnifunc=htmlcomplete#CompleteTags

if &term =~ "xterm\\|rxvt"
  " use an orange cursor in insert mode
  let &t_SI = "\<Esc>]12;orange\x7"
  " use a red cursor otherwise
  let &t_EI = "\<Esc>]12;red\x7"
  silent !echo -ne "\033]12;red\007"
  " reset cursor when vim exits
  autocmd VimLeave * silent !echo -ne "\033]112\007"
  " use \003]12;gray\007 for gnome-terminal
endif

set guicursor=i:ver100-iCursor

set guicursor+=n-v-c:blinkon0


noremap <silent> <C-S>          :update<CR>
vnoremap <silent> <C-S>         <C-C>:update<CR>
inoremap <silent> <C-S>         <C-O>:update<CR>



" let g:EasyMotion_do_mapping = 0 " Disable default mappings

" " Jump to anywhere you want with minimal keystrokes, with just one key binding.
" " `s{char}{label}`
" nmap s <Plug>(easymotion-overwin-f)
" " or
" " `s{char}{char}{label}`
" " Need one more keystroke, but on average, it may be more comfortable.
" nmap s <Plug>(easymotion-overwin-f2)

" " Turn on case insensitive feature
" let g:EasyMotion_smartcase = 1

" " JK motions: Line motions
" map <Leader>j <Plug>(easymotion-j)
" map <Leader>k <Plug>(easymotion-k)
"
"
"remapping control s to for save all files opened
"
"
"markdown preview

