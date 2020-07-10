### 代理设置

1. 使用命令

- http代理：

git config --global https.proxy http://127.0.0.1:10800
git config --global https.proxy https://127.0.0.1:10800

- socks5代理：

git config --global http.proxy 'socks5://127.0.0.1:10800'
git config --global https.proxy 'socks5://127.0.0.1:10800'

2. 编辑文件~/.gitconfig


- 在文件添加：

[http]
proxy = socks5://127.0.0.1:10800
[https]
proxy = socks5://127.0.0.1:10800
然后就可以直接使用git命令重新下载了。

- 取消代理

git config --global --unset http.proxy
git config --global --unset https.proxy
