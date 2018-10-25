(内网服务器，下载大体积安装包优先使用)[http://install.ecustnlplab.com/]

(使用清华源)[https://mirror.tuna.tsinghua.edu.cn/help/anaconda/]

```bash
# mirrors后面加6，使用ipv6下载更快
conda config --add channels https://mirrors6.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors6.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

升级linux 内核后，显卡驱动必然失效