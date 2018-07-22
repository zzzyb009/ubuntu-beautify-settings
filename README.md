# ubuntu-beautify-settings

软件中心安装ubuntu tweak tool
https://apps.ubuntu.com/cat/applications/saucy/docky/  安装docky

安装Flatabulous主题
sudo add-apt-repository ppa:noobslab/themes

sudo apt-get update

sudo apt-get install flatabulous-theme

配套的图标（扁平的图标）
sudo add-apt-repository ppa:noobslab/icons

sudo apt-get update

sudo apt-get install ultra-flat-icons

Numix 圆形图标

sudo add-apt-repository ppa:numix/ppa

sudo apt-get update

sudo apt-get install numix-icon-theme numix-icon-theme-circle

采用文泉译微米黑字体替代系统字体

apt-get install fonts-wqy-microhei

安装搜狗拼音输入法

oh my zsh安装

apt install -y zsh

sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"

UI配置完成


apt-fast的安装  一个多线程的安装工具，apt-get每次只能安装一个f，ast可以同时安装多个

sudo add-apt-repository ppa:apt-fast/stable

apt-get update

apt-get install apt-fast

安装miredo虚拟网卡来翻墙(现在不稳定了，还是百度吧)

https://github.com/XX-net/XX-Net/wiki/How-to-use  将文中所涉及的插件尽数安装

接下来参考：

https://github.com/XX-net/XX-Net/wiki/%E5%AE%89%E8%A3%85%E5%92%8C%E4%BD%BF%E7%94%A8-SwitchyOmega

总结为：安装完成之后每次开启需要先开启miredo虚拟网卡，然后到xx-net目录下运行 ./start 文件，正常情况下就可以科学上网了。

相关文档：https://github.com/XX-net/XX-Net/wiki/%E4%B8%AD%E6%96%87%E6%96%87%E6%A1%A3

音乐软件：网易云音乐http://music.163.com/#/download  官网直接下载

微信：ubuntu商店

安装sublime-text-3

参考：http://www.sublimetext.com/docs/3/linux_repositories.html

正常安装

wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -    //GPG key

sudo apt-get install apt-transport-https  //从https网站下载需要安装这个

echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list   //stable version稳定版本

apt-get update

apt-get install sublime-text

//不能正常的情况（终端显示已经连接却迟迟没有下载，最后下载失败了）这个时候要把上面的步骤重新来一次，把https都改为http即可，嗯应该就可以了

wget -qO - http://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -    //GPG key

echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list   //stable version稳定版本

apt-get update

apt-get install sublime-text

sublime-text的一些插件的安装
我的配置：
{
    "caret_style": "phase",  //光标闪烁方式
    "font_size": 12,  //字体大小
    "highlight_line": true,  //高亮当前光标所在的行
    "highlight_modified_tabs": true,   //高亮修改过的文件的tab
    "line_padding_bottom": 1,  //行内下间距
    "line_padding_top": 1,  //行内上间距
    "show_encoding": true,  //在下方显示文件编码
    "translate_tabs_to_spaces": true,  //将tab按键转化成为4个空格（这个...）
    "word_wrap": true,  //文本超出右边的显示范围时自动会换行到下一行显示
}
首先得安装package control：按下ctrl+shift+p，然后输入install package control，选择安装即可
插件：
A File Icon：安装了这个插件之后在左边的文件那里会显示文件类型的图标，美观一点，敲码心情更美丽
Auto File Name：鼠标在单双引号之间的时候，会有补充文件路径名的提示 （补全src、href文件路径）
Open Url：在sublime中可以点击打开web路径
SublimeCodeIntel：代码提示、function定义跳转
Emmet：一个强大的前端代码提示插件（html、xml、css）  参考http://blog.csdn.net/xiaozhi_2016/article/details/52415897
BracketHighlighter：在行号左侧显示当前标签的对应图标，找不到对应的图标会出现问号，在有多层嵌套的符号时很方便
//需在setting中添加以下配置项
```
"match_brackets": false,
"match_brackets_angle": false,
"match_brackets_braces": false,
"match_brackets_content": false,
"match_brackets_square": false,
"match_tags": false,
```
安装php语法错误提示工具(SublimeLinter+SublimeLinter-php)：
安装完之后打开sublimeLinter的配置文件，copy一份到用户的配置文件，并在path部分加入你的php执行目录路径：
```
"paths": {
    "linux": [
        "//usr//bin//php7.0"
    ],
    "osx": [],
    "windows": []
}
```
完成上述配置之后，编写php代码出错时在当前行左侧会有红点出现
DocBlock：自动生成PHPDoc风格的注释。输入  /**   之后按下tab或者enter即可
SideBarEnhancements：这个插件改进了侧边栏，增加了许多功能


一些关于nginx（nginx/1.10.3）虚拟主机的配置
1、先进入nginx的配置文件目录/etc/nginx/
2、进入sites-available目录，当前目录下有一个default文件，copy一份并命名为你的要创建的虚拟主机的域名（或者其他名字都可以），然后修改这个文件中的server_name（网站名，访问用的域名,比如：server_name www.web.com web.com）和root（站点根目录，比如：/var/www/web），并去掉17行和18行的listen后面的default_server
3、创建配置文件的软连接(从site-available链接到site-enabled)  （我创建的虚拟主机配置文件名为www.web.com）命令：ln -s /etc/nginx/sites-available/www.web.com /etc/nginx/sites-enabled/www.web.com
4、在hosts文件中配置新的站点地址，比如：127.0.0.3 wwww.web.com web.com

vim配置
```
/etc/vim/vimrc
set showmatch       " Show matching brackets.
"set ignorecase     " Do case insensitive matching
set smartcase       " Do smart case matching
set incsearch      " Incremental search
set autowrite      " Automatically save before commands like :next and :make
set hidden     " Hide buffers when they are abandoned
set mouse=a        " Enable mouse usage (all modes)
set number	"显示行号
set tabstop=4   "设定缩进的长度  
set ruler
set hlsearch    "搜索时高亮结果
```

NERDTree 文件树

安装地址：https://github.com/scrooloose/nerdtree

```
VScode配置：
{
    "workbench.colorTheme": "Default High Contrast",
    "sublimeTextKeymap.promptV3Features": true,
    "editor.multiCursorModifier": "ctrlCmd",
    "editor.snippetSuggestions": "top",
    "editor.formatOnPaste": true,
    "editor.fontSize": 14,    
    "editor.cursorStyle": "line",
    "editor.wordWrap": "on",
    "php.validate.executablePath": "/usr/bin/php7.0",
    "php.validate.run": "onType",
    "view-in-browser.customBrowser": "/snap/bin/chromium",
    "editor.cursorBlinking": "phase",
    "editor.renderLineHighlight": "all",
    
}
```
