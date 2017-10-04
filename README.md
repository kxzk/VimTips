![VimrcTipsTricks](https://cdn-images-1.medium.com/max/2000/1*n4hLwVDtv4ywXxGuTaipbw.png)

# A Collection Of Useful Mappings + Hacks

Feel free to submit a PR with an interesting line in your Vimrc. Hopefully this can become a tool for others. Ideally, come here -> search for what you're trying to do -> add relevant line to Vimrc. The mappings you see within these examples are optional. A mapping using <leader>X can easily be <leader>Y, so long as it doesn't conflict with any existing mapping.
&nbsp;
&nbsp;
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
