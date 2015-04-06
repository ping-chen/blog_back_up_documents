2015.4.6	初次提交

这是我使用的.vimrc

```
"""""""""""""""""""""""""""""""""""""""""""
" 一般配制

" vim内部以utf-8格式显示
set encoding=utf-8
" Vim 所工作的终端的编码
set termencoding=utf-8
" 猜测（匹配）编码格式，都不是的情况会出现乱码
set fileencodings=utf-8,gb18030,gbk,big5
" 支持打开dos，去掉那些烦人的^M符号
set fileformats=unix,dos

" 改为打开文件时设置，防止被修改
" 保存时以unix格式保存
" set fileformat=unix
" 保存时以utf-8编码保存
" set fileencoding=utf-8
" utf-8 不带头
" set nobomb

" VIM操作，不兼容VI模式
set nocompatible
" 以十进制进行<C+a>与<C+x>操作
set nrformats=
" 显示行号
set number
" 一直显示tab标签
set showtabline=2
" 显示搜索高亮
set hlsearch
" 输入字符串的过程中就显示匹配点
set incsearch
" 区分大小写
set noignorecase

" 定义tab所等同的空格长度
set tabstop=4
" 多少个空隔会组成一个tab (tab的空格长度，与tabstop一起用)
set softtabstop=4
" 程序自动缩进的长度
set shiftwidth=4
" 把制表符转来空隔
set expandtab

" 总是显示状态行
set laststatus=2
" 显示按了哪些键，对组合键很有用
set showcmd
" 在状态行上显示当前状态
set showmode
" 在状态行上显示光标所在位置的行号和列号
set ruler

" 文件在Vim之外修改过，自动重新读入
set autoread
" 在处理未保存或只读文件的时候，弹出确认
set confirm
" 帮助文档优先找中文
set helplang=cn

" 不要生成备份文件
set nobackup
" 不要生成swap文件
set noswapfile
" 新文件不显示vim信息
set shortmess=I

" 语法高亮
syntax on

" 配色方案
" set t_Co=256
color af

" 路径为打开的目录
set path=.

"""""""""""""""""""""""""""""""""""""""""""
" 普通模式下配制

" 取消高亮
nnoremap gn :nohl<cr>

" 把当前行往上移
" nnoremap p :.m.-2<cr>
" 把当前行往下移
" nnoremap n :.m.+1<cr>
" 把当前行复制到上一行
nnoremap <C-p> :.t.-1<cr>
" 把当前行复制到下一行
nnoremap <C-n> :.t.<cr>

" 前一个tab页
nnoremap t, :tabp<cr>
" 后一个tab页
nnoremap t. :tabn<cr>
" 关闭当前tab页
nnoremap tc :tabclose<cr>
" 新建一个tab页
nnoremap tn :tabnew<cr>

" nnoremap l guiw
" nnoremap u gUiw

nnoremap n nzz
nnoremap N Nzz

" nnoremap ` <Esc><Left><Right>
" nnoremap ' `

"""""""""""""""""""""""""""""""""""""""""""
" 插入模式下配制

" 设置退格删除
set backspace=2

" inoremap l <Esc>guiwea
" inoremap u <Esc>gUiwea

inoremap <C-h> <C-o>h
inoremap <C-j> <C-o>j
inoremap <C-k> <C-o>k
inoremap <C-l> <C-o>l

inoremap <C-w> <C-o>w
inoremap <C-e> <C-o>e
inoremap <C-b> <C-o>b
inoremap <C-g><C-e> <C-o>ge

" inoremap [1;5t <C-o>$
" inoremap  <C-o>^

inoremap <C-d><C-i><C-w> <C-o>diw
inoremap <C-d><C-a><C-w> <C-o>daw

" inoremap ` <Esc><Left><Right>

"""""""""""""""""""""""""""""""""""""""""""
" 命令行模式下配制

" 告诉哪一行被改变过
set report=0
" 让命令历史记录得更多
set history=200
" 类似bash shell的补全行为
set wildmode=longest,list
" 支持自动补全<C+d>显示
set wildmenu

cnoremap <C-p> <Up>
cnoremap <C-n> <Down>

" cnoremap ` <Esc><Left><Right>

"""""""""""""""""""""""""""""""""""""""""""
" 可视模式下配制

" 把所选行上称一行
" vnoremap p :m'<-2<cr>gv
" 把所选行下称一行
" vnoremap n :m'>+1<cr>gv
" 把所选行复制到上一行
vnoremap <C-p> :t'<-1<cr>gv
" 把所选行复制到下一行
vnoremap <C-n> :t'><cr>gv

vnoremap ` <Esc><Left><Right>

"""""""""""""""""""""""""""""""""""""""""""
" 界面分隔配制

nnoremap mh 5<C-w><
nnoremap mj 5<C-w>+
nnoremap mk 5<C-w>-
nnoremap ml 5<C-w>>

nnoremap <C-h> <C-w>h
nnoremap <C-j> <C-w>j
nnoremap <C-k> <C-w>k
nnoremap <C-l> <C-w>l

"""""""""""""""""""""""""""""""""""""""""""
" 代码配制

" 以C语言缩进来格式化（基乎能满足所有语言）
set cindent
" 继承前一行的缩进方式，特别适用于多行注释
set autoindent
" 高亮显示匹配的括号
set showmatch
" 匹配括号高亮的时间（单位是十分之一秒
set matchtime=5

" 去掉行末空隔
nnoremap <F3> :%s/[ \t\r]\+$//g<CR>

"""""""""""""""""""""""""""""""""""""""""""
" Vundle插件，以及Vundle管理的插件的配制

" git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim

" 先关闭，防止Vundle插件出问题
filetype off

" VIM的加载路径中添加Vundle
set rtp+=~/.vim/bundle/Vundle.vim

" 开始
call vundle#begin()

" Vundle官方地址，用于插件更新
Plugin 'gmarik/Vundle.vim'

" 常用(共用)插件

" 依懒ctags 能显示类大纲
Plugin 'taglist.vim'
" 按名字顺序排序
let Tlist_Sort_Type = 'name'
" 只显示当前文件的taglist，默认是显示多个
let Tlist_Show_One_File = 1
" 如果taglist是最后一个窗口，则退出vim
let Tlist_Exit_OnlyWindow = 1
" 在右侧窗口中显示taglist
let Tlist_Use_Right_Window = 1
" 打开taglist时，光标保留在taglist窗口
let Tlist_GainFocus_On_ToggleOpen = 1
" 关闭和打开taglist窗口的快捷键，这个插件有BUG，和tab同时用时，切换tab，要记得先关闭taglist
nnoremap tl :Tlist<CR>

" 目录树
Plugin 'scrooloose/nerdtree'
nnoremap \ :NERDTree<cr>
nnoremap \\ :NERDTreeClose<cr>
" 窗体在左则
let NERDTreeWinPos = "left"
" 显示行号
let NERDTreeShowLineNumbers=1
" 默认打开的窗体大小
let NERDTreeWinSize = 31
" 光标超出范围，自动归中
let NERDTreeAutoCenter = 1
" 样式
let NERDChristmasTree = 1
" 打开文件之后，不自动关闭目录
let NERDTreeQuitOnOpen = 0
" 文件前面有个箭头，用+-来显示
let NERDTreeDirArrows = 0
" 不显示指定类型的文件
let NERDTreeIgnore = ['tags']

" python写的补全插件，听说是史上最强 文件太大了，后面再看吧
"Plugin 'Valloric/YouCompleteMe'
" 手动编译./install.sh
" --omnisharp-completer 支持C#  --clang-completer 支持C家族

" 快捷打文件，删除了fuf，依懒ctags
Plugin 'kien/ctrlp.vim'
" 设置打开方式，<C-p>已经被自定义快捷键占用了，所以用gf，gf是VIM打开本路径中的文件
let g:ctrlp_map = 'gf'
let g:ctrlp_open_multiple_files = 'h'

" grep 的替代
Plugin 'mileszs/ack.vim'

" 成对修改{["' html标签
Plugin 'tpope/vim-surround'

" python专用插件

" 结束，自定义插件要在放在这之前
call vundle#end()

"""""""""""""""""""""""""""""""""""""""""""
" 文件类型自动匹配，放在最后，是因为防止Vundle插件出问题

filetype on
filetype plugin on
filetype indent on

"""""""""""""""""""""""""""""""""""""""""""
" 其它

" 重新打开文件，回到上次编辑的地方
autocmd BufReadPost * if line("'\"") > 0|if line("'\"") <= line("$")|exe("norm '\"")|else|exe "norm $"|endif|endif

" 保存时以unix格式，以utf-8编码保存。由于.vimrc比其它配置先读，所以要在打开文件后设置。不然设置会被覆盖
" statusline=%F%m%r%h%w\ %{&ff}\ %{\"\".(&fenc==\"\"?&enc:&fenc).((exists(\"+bomb\")\ &&\ &bomb)?\",B\":\"\").\"\"}%=%l,%v\ %p%%\ [%{strftime(\"%m-%d\ %H:%M\")}]
" statusline=%F%m%r%h%w\ \|\ %{((&ff==\"unix\"\ &&\ &fenc==\"utf-8\")?\"\":\"error\ the\ file\ format\ format\ format\ format\ format\ format\")}
" statusline=%f%m\ \|\ %{&ff}\ \|\ %{(&fenc==\"\"?&enc:&fenc)}%=%l,%v\ %p%%\ [%{strftime(\"%m-%d\ %H:%M\")}]
" 目前找不到合适的方式处理，提示用户文件格式与编码，直接强转
" autocmd BufRead * set statusline=%f%m\ %=%l,%v\ \|\ %p%%\ \|\ %{strftime(\"%m-%d\ %H:%M\")} fileencoding=utf-8 fileformat=unix nobomb

```