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

## 快捷键,为了简洁好记原则，最多2个键
```
dw和de:删除一个单词从光标往后删除（包括光标本身以及单词后面的空格）
db:删除到前一个单词包括标点在内
shift+d:删除光标开始到行尾的字符串
d0 删除光标到行首(不包括光标本身)
x 删除光标所在字符
s 删除光标所在字符并进入插入模式

```
