# 使用Homebrew管理MacOS软件包


## 介绍
[Homebrew](https://brew.sh/index_zh-cn)是MacOS平台的包管理工具，你可以使用它来轻松的管理软件包的安装、卸载、更新等。它会帮助你解决各种依赖和文件路径的问题。

[Homebrew](https://brew.sh/index_zh-cn)不仅仅适用MacOS平台，在Linux和Windows Subsystem for Linux也可以使用。

这里我将着重和你分享在MacOS平台下如何使用[Homebrew](https://brew.sh/index_zh-cn)。如果你对在Linux和Windows Subsystem for Linux下使用[Homebrew](https://brew.sh/index_zh-cn)感兴趣的话，请参照官方文档，在[这里](https://docs.brew.sh/Homebrew-on-Linux)有详细的说明。

我会和你分享如下几个主题：

* 安装[Homebrew](https://brew.sh/index_zh-cn)
* 使用[Homebrew](https://brew.sh/index_zh-cn)管理软件包
* 图形化管理Brew
* 使用Brew备份软件清单
## 安装Homebrew
Homebrew的安装非常简单，你只需要一个命令就可以完成安装。你在官网的[首页](https://brew.sh/)上也能看到这个安装命令。打开你的终端执行它:

```
➜  ~ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
安装完成后，你可以使用下面命令来确认安装的版本

```
➜  ~ brew -v
Homebrew 2.2.12
Homebrew/homebrew-core (git revision ed33a; last commit 2020-04-12)
```
好了，至此我们已经完成了Homebrew的安装。是不是特别简单。

[![asciicast](https://asciinema.org/a/wHtzlGU3smqgOnhaC7CcplIgj.svg)](https://asciinema.org/a/wHtzlGU3smqgOnhaC7CcplIgj)

## 使用Homebrew管理软件
Brew使用将软件包分为两种类型来管理，一种是终端命令，另一种是图形化软件。

让我们分别演示如何操作。

#### 安装命令
如果想安装一个wget，可以直接使用`install`来安装。

```
➜  ~ brew install wget
...
```
但是，安装之前可以使用`search`和`info`来搜索和查看这个命令

```
$ brew search wget
==> Formulae
wget                    wgetpaste
```
你看这里搜索到两个包含`wget`关键字的命令。
我们可以使用`info`来查看某个命令的详细信息。

```
➜  ~ brew info wget
wget: stable 1.20.3 (bottled), HEAD
Internet file retriever
https://www.gnu.org/software/wget/
Not installed
From: https://github.com/Homebrew/homebrew-core/blob/master/Formula/wget.rb
==> Dependencies
Build: pkg-config ✘
Required: libidn2 ✘, openssl@1.1 ✔
==> Options
--HEAD
    Install HEAD version
==> Analytics
install: 105,915 (30 days), 317,104 (90 days), 1,366,851 (365 days)
install-on-request: 102,323 (30 days), 305,340 (90 days), 1,285,029 (365 days)
build-error: 0 (30 days)
```
这里你能看到这个命令的版本、官网地址、依赖项、统计分析。
其中，依赖项中显示`✘`的表示在本机还没有安装这个库文件等。之后，安装这个wget命令的时候brew会帮助你处理这些依赖。而无需你担心它们。

好的，让我们来安装它。超简单。

```
➜  ~ brew install wget
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> Updated Formulae
azcopy                                            codequery                                         link-grammar

==> Installing dependencies for wget: gettext, libunistring and libidn2
==> Installing wget dependency: gettext
==> Downloading https://homebrew.bintray.com/bottles/gettext-0.20.1.catalina.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/10/107d7f386fbeea6979f9376cdbbcf3f60943caaad61bdc754d3019ce625dffe6?__gda__=exp=1586694510~hmac=ccc067
######################################################################## 100.0%
==> Pouring gettext-0.20.1.catalina.bottle.tar.gz
==> Caveats
gettext is keg-only, which means it was not symlinked into /usr/local,
because macOS provides BSD gettext.

If you need to have gettext first in your PATH run:
  echo 'export PATH="/usr/local/opt/gettext/bin:$PATH"' >> ~/.zshrc

For compilers to find gettext you may need to set:
  export LDFLAGS="-L/usr/local/opt/gettext/lib"
  export CPPFLAGS="-I/usr/local/opt/gettext/include"

==> Summary
🍺  /usr/local/Cellar/gettext/0.20.1: 1,893 files, 18.4MB
==> Installing wget dependency: libunistring
==> Downloading https://homebrew.bintray.com/bottles/libunistring-0.9.10.catalina.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/ce/ce746662b98d93511b86920011b5cafcd2eecbce4c9c40d8c52a143cdf708456?__gda__=exp=1586694526~hmac=e67bdd
######################################################################## 100.0%
==> Pouring libunistring-0.9.10.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/libunistring/0.9.10: 54 files, 4.4MB
==> Installing wget dependency: libidn2
==> Downloading https://homebrew.bintray.com/bottles/libidn2-2.3.0.catalina.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/09/0908585cca518a83f101b2edc0417a26a4b4fc8b76e393c6f6672de6e595c914?__gda__=exp=1586694530~hmac=c7c038
######################################################################## 100.0%
==> Pouring libidn2-2.3.0.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/libidn2/2.3.0: 70 files, 727.8KB
==> Installing wget
==> Downloading https://homebrew.bintray.com/bottles/wget-1.20.3_2.catalina.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/ef/ef65c759c5097a36323fa9c77756468649e8d1980a3a4e05695c05e39568967c?__gda__=exp=1586694533~hmac=e66b1b
######################################################################## 100.0%
==> Pouring wget-1.20.3_2.catalina.bottle.tar.gz
🍺  /usr/local/Cellar/wget/1.20.3_2: 50 files, 4.0MB
==> Caveats
==> gettext
gettext is keg-only, which means it was not symlinked into /usr/local,
because macOS provides BSD gettext.

If you need to have gettext first in your PATH run:
  echo 'export PATH="/usr/local/opt/gettext/bin:$PATH"' >> ~/.zshrc

For compilers to find gettext you may need to set:
  export LDFLAGS="-L/usr/local/opt/gettext/lib"
  export CPPFLAGS="-I/usr/local/opt/gettext/include"

➜  ~
➜  ~ wget -S -nv https://www.examples.com -O /dev/null
Warning: Failed to set locale category LC_NUMERIC to zh_Hans_JP.
Warning: Failed to set locale category LC_TIME to zh_Hans_JP.
Warning: Failed to set locale category LC_COLLATE to zh_Hans_JP.
Warning: Failed to set locale category LC_MONETARY to zh_Hans_JP.
  HTTP/1.1 200 OK
  Content-Type: text/html
  Server: nginx
  Last-Modified: Sun, 12 Apr 2020 12:30:02 GMT
  ETag: W/"5e9309ca-6213"
  X-Frame-Options: SAMEORIGIN
  Content-Encoding: gzip
  Via: 1.1 varnish
  Cache-Control: max-age=31536000, public
  Access-Control-Allow-Origin: *
  Content-Length: 5751
  Accept-Ranges: bytes
  Date: Sun, 12 Apr 2020 12:30:32 GMT
  Via: 1.1 varnish
  Age: 29
  Connection: keep-alive
  X-Served-By: cache-lax8622-LAX, cache-tyo19925-TYO
  X-Cache: HIT, MISS
  X-Cache-Hits: 2, 0
  X-Timer: S1586694632.057470,VS0,VE106
  Vary: Accept-Encoding
  Strict-Transport-Security: max-age=900
```
#### 2020-04-12 21:30:32 URL:https://www.examples.com/ [5751/5751] -> "/dev/null" [1]

卸载命令
卸载也很简单

```
➜  ~ brew uninstall wget
Uninstalling /usr/local/Cellar/wget/1.20.3_2... (50 files, 4.0MB)
➜  ~
➜  ~
➜  ~ wget -S -nv https://www.examples.com -O /dev/null
zsh: command not found: wget
➜  ~
```
#### 安装软件
如果安装一个软件，你要使用`cask`子命令。

让我们试着安装atom。首先，我们使用试着搜索一下。

```
➜  ~ brew search atom
==> Formulae
atomicparsley                        atomist-cli                          libatomic_ops                        sratom
==> Casks
homebrew/cask-versions/atom-beta                  homebrew/cask-versions/atom-nightly               homebrew/cask/atom
```
查询到很多，我们试着看一下`homebrew/cask/atom`

```
➜  ~ brew cask info homebrew/cask/atom
==> Tapping homebrew/cask
Cloning into '/usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask'...
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 426061 (delta 2), reused 0 (delta 0), pack-reused 426054
Receiving objects: 100% (426061/426061), 192.50 MiB | 911.00 KiB/s, done.
Resolving deltas: 100% (301262/301262), done.
Tapped 1 command and 3524 casks (3,639 files, 206.6MB).
atom: 1.45.0 (auto_updates)
https://atom.io/
Not installed
From: https://github.com/Homebrew/homebrew-cask/blob/master/Casks/atom.rb
```
这是我想要的，我们安装它

```
➜  ~ brew cask install homebrew/cask/atom
==> Downloading https://github.com/atom/atom/releases/download/v1.45.0/atom-mac.zip
==> Downloading from https://github-production-release-asset-2e65be.s3.amazonaws.com/3228505/e28afd00-6304-11ea-8ac4-8b3de4863926?X-Amz-Algorithm=AW
######################################################################## 100.0%
==> Verifying SHA-256 checksum for Cask 'atom'.
==> Installing Cask atom
==> Moving App 'Atom.app' to '/Applications/Atom.app'.
==> Linking Binary 'apm' to '/usr/local/bin/apm'.
==> Linking Binary 'atom.sh' to '/usr/local/bin/atom'.
🍺  atom was successfully installed!
```
就这么简单，你可以使用atom了。
#### 卸载软件
卸载也简单

```
brew cask uninstall atom
```
#### 更新软件包
你用以下命令就可以更新brew管理的软件包了

```
➜  ~ brew update
Already up-to-date.
➜  ~ brew upgrade
➜  ~ brew cask upgrade
==> No Casks to upgrade
```
[![asciicast](https://asciinema.org/a/aogFAmrX3q4M2TiYU2oRdgIgm.svg)](https://asciinema.org/a/aogFAmrX3q4M2TiYU2oRdgIgm)
## 图形化管理Brew
这里有一个图形化的brew管理工具，你用下面的命令安装之后可以自行探索。

```
➜  ~ brew cask install cakebrew
```
![图片](https://uploader.shimo.im/f/VRadbREHh0pBqeq0.png!thumbnail)

## 使用Brew备份软件清单
你现在有一个很好的包管理工具，它能帮了你的大忙。

如果你想重新安装MacOS，或者你更换了新的MacBook的话，这该怎么办。电脑已经装了很多的命令工具和软件。

好了。Brew又再次出手帮你拜托这些繁琐的安装步骤。

我们使用`brew bundle`来帮助我们完成软件包的备份和还原。

首先，我希望备份更彻底，因为有些软件不是通过brew安装的。而是通过Mac App Store。所以，我们希望brew bundle备份的时候也将Mac App Store安装的软件一同备份。

```
➜  ~ brew install mas
```
完成安装，你就可以备份了。

```
brew bundle dump
```
就是这样，它在执行命令的当前路径生成一个Brewfile文件，这个就是brew备份的软件清单。之后我们需要使用这个清单文件进行还原。
让我们看看它是什么样子。

```
➜  ~ cat Brewfile
tap "caskroom/cask"
tap "homebrew/bundle"
tap "homebrew/cask"
tap "homebrew/cask-drivers"
tap "homebrew/cask-versions"
tap "homebrew/core"
tap "homebrew/services"
brew "ansible"
brew "tldr"
brew "tmux"
brew "tree"
brew "typescript"
brew "webpack"
brew "wget"
cask "cakebrew"
cask "dash"
cask "intellij-idea"
cask "iterm2"
mas "Slack", id: 803453959
```
这是我之前的一个备份。之后，我们就可以使用brew bundle来还原了。
```
➜  ~ brew bundle 
➜  ~ # Or brew bundle --file /path/to/Brewfile
```
[![asciicast](https://asciinema.org/a/v7KxT3Lmfcryv1e4oq23oFRNX.svg)](https://asciinema.org/a/v7KxT3Lmfcryv1e4oq23oFRNX)

