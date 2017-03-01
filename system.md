## 系统基础配置


1. 设置正确时区和时间。

```
dpkg-reconfigure tzdata
```

2. 避免额外问题，重新生成locales

```
cd /usr/share/locales
# 无须理会warning
./install-language-pack zh_CN
# 重新生成
locale-gen
# 检查是否正常（无报错）
locale -a
```

3. 安装基础常用软件

```
apt-get update && apt-get upgrade -y
apt-get install -y git zsh wget curl unzip vim tree
```

4. 换效率稍微高一点的shell

```
curl -L http://install.ohmyz.sh | sh
chsh -s /bin/zsh
```

5. 修改机器名称，配置绑定hosts

```
echo "go9999"> /etc/hostname
hostname -F /etc/hostname
cat /etc/hostname
echo "127.0.1.1   Pantimos" >> /etc/hosts
```

6. 配置基础应用／Runtime

```
apt-get install libreadline-dev libncurses5-dev libpcre3-dev libssl-dev perl make build-essential
wget https://openresty.org/download/openresty-1.11.2.2.tar.gz
tar -xzvf openresty-1.11.2.2.tar.gz
cd openresty-VERSION/
./configure
make
sudo make install


echo "140.211.166.134 dl.hhvm.com" >> /etc/hosts
wget -O- http://dl.hhvm.com/conf/hhvm.gpg.key | sudo apt-key add -
echo deb http://dl.hhvm.com/ubuntu xenial main | sudo tee /etc/apt/sources.list.d/hhvm.list
apt-get update && apt-get install hhvm -y
```

