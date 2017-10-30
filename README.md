![VimrcTipsTricks](https://cdn-images-1.medium.com/max/2000/1*n4hLwVDtv4ywXxGuTaipbw.png)

# A Collection Of Useful Mappings + Hacks

Feel free to submit a PR with an interesting line in your Vimrc. Hopefully this can become a tool for others. Ideally, come here -> search for what you're trying to do -> add relevant line to Vimrc. **The mappings you see within these examples are optional**. A mapping using <leader>X can easily be <leader>Y, so long as it doesn't conflict with any existing mapping.
&nbsp;
&nbsp;
&nbsp;
#### Statusline Tips -> [Click Here](https://github.com/beigebrucewayne/VimTips/blob/master/statusline.md)
&nbsp;
&nbsp;
&nbsp;
* (neovim): live search substitution
```vimL
set inccomand=nosplit
```
&nbsp;
* Remove search highlighting with delete/backspace key
```vimL
nnoremap <silent> <BS> :nohlsearch<CR>
```
&nbsp;
* Quote words under cursor
```vimL
nnoremap <leader>" viW<esc>a"<esc>gvo<esc>i"<esc>gvo<esc>3l
nnoremap <leader>' viW<esc>a'<esc>gvo<esc>i'<esc>gvo<esc>3l
```
&nbsp;
* Delete all Trailing space in file
```vimL
nnoremap <Leader>T :%s/\s\+$//<CR>:let @/=''<CR>:nohlsearch<CR>
```
&nbsp;
* Count j & k as jumps
```vimL
nnoremap <expr> k (v:count > 1 ? "m'" . v:count : '') . 'gk'
nnoremap <expr> j (v:count > 1 ? "m'" . v:count : '') . 'gj'
```
&nbsp;
* Execute shell commands in buffer
```vimL
nnoremap Q !!$SHELL <CR>
```
&nbsp;
* Edit & Reload .vimrc
```vimL
map <leader>ev :e $HOME/.vimrc
map <leader>rv :source ~/.vimrc<CR>
```
&nbsp;
* Grep word under cursor
```vimL
nnoremap K :execute 'grep!"\b"'.expand('<cword>').'"\b"'<CR>:cw<CR>
```
&nbsp;
* Cursor only active in current window
```vimL
augroup Cursoractive
    au!
    autocmd VimEnter, WinEnter, BufWinEnter * set local cursorline
    autocmd WinLeave * setlocal nocursorline
augroup END
```
&nbsp;
* Window splits automatically equalized
```vimL
set equalalways
```
&nbsp;
* Open plugin Github page in browser
```vimL
" Keybinding for visiting the GitHub page of the plugin defined on the current line
autocmd FileType vim nmap <silent> gp :call OpenPluginHomepage()<CR>

function! OpenPluginHomepage()
  " Get line under cursor
  let l:line = getline('.')

  " Matches for instance Plug 'tpope/surround' -> tpope/surround
  " Greedy match in order to not capture trailing comments
  let l:plugin_name = '\w\+ \([''"]\)\(.\{-}\)\1'
  let l:repository = matchlist(l:line, l:plugin_name)[2]

  " Open the corresponding GitHub homepage with $BROWSER
  " You need to set the BROWSER environment variable in order for this to work
  " For MacOS, you can set the following for opening it in your default
  " browser: 'export BROWSER=open'
  exec '!$BROWSER https://github.com/'.l:repository
endfunction
```
