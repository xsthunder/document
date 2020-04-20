# linux上安装node
1.  uname -a  命令查看到我的Linux系统位数是64位（备注：x86_64表示64位系统， i686 i386表示32位系统）
2. http://nodejs.cn/download/  下载对应版本，`wget <连接>`
3. 解压`tar -xvf <下载的压缩包>   `
4. `mv node-v6.10.0-linux-x64  nodejs `
5. `echo export PATH=\"$(pwd)/nodejs/bin:\$PATH\" >>.bashrc`

## linux后台运行程序
1. screen -R host 创建一个新的tty
2. yarn serve
3. ctrl-A ctrl-D 回到默认tty
4. exit

screen -R host 可以重新回到这个tty