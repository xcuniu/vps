新装宝塔
1.直接安装V7.7.0的版本，之后的版本都会验证userInfo.json，虽然网上有大把的开心版，但不敢用啊。

国外机可以用github，用下面的代码 作者github地址

curl -sSO https://raw.githubusercontent.com/8838/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
国内机器，或者连不上github的，用下面这个代码 国内文件地址

curl -sSO http://d.moe.ms/AAAAA/btpanel-v7.7.0/install/install_panel.sh && bash install_panel.sh
Ps:代码都能看到，如果有疑问，大家可自行看源码。

2.开始开心版手动制作
1，屏蔽手机号

sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|" /www/server/panel/BTPanel/static/js/index.js
2.删除强制绑定手机js文件

rm -f /www/server/panel/data/bind.pl
3.还嫌麻烦，直接一键优化脚本吧

wget -O optimize.sh http://f.cccyun.cc/bt/optimize.sh && bash optimize.sh
插件开心版操作
1.手动解锁宝塔所有付费插件为永不过期
文件路径：/www/server/panel/data/plugin.json
搜索字符串："endtime": -1全部替换为"endtime": 999999999999
2.给plugin.json文件上锁防止自动修复为免费版

chattr +i /www/server/panel/data/plugin.json
如果嫌烦，一键脚本啊

curl -sSO https://raw.githubusercontent.com/ztkink/bthappy/main/one_key_happy.sh && bash one_key_happy.sh
已经安装了宝塔新版本,降级
1.下载离线包

wget https://d.ybfl.xyz/bt/LinuxPanel-7.7.0.zip
2.解压缩

unzip LinuxPanel-7.7.0.zip
如有提示，输入大写A即可，全部替换
3.进入升级目录

cd /root/panel
4.运行降级

bash update.sh
然后重复上面屏蔽手机的代码和是否要开启开心版插件，自己定吧。
