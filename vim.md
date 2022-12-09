# vim配置和使用
## 优先使用neovim,glibc库版本大于2.1.7
```
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim.appimage
chmod u+x nvim.appimage
./nvim.appimage
```
## neovim不能用，推荐vim配置
https://github.com/amix/vimrc
```
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh
```

## 快捷键
```
dw:删除一个单词从光标往后删除（包括光标本身以及单词后面的空格）
d$ 删除光标开始到行尾的字符串
d0 删除光标到行首(不包括光标本身)
d^ 删除光标到行第一个字符(不包括光标本身)
dw:删除一个单词(光标以后的字符,包括光标与空格)
diw:删除一个单词(光标前后的字符，不包括空格)
daw:删除一个单词，光标前后的字符包括后面的空格
x 删除光标所在字符
s 删除光标所在字符并进入插入模式

```
