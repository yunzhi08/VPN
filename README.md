# VPN環境搭建
爲實現簡單易懂，在此推薦不同影片綜合學習 https://youtu.be/jeXPVqz4OEs https://youtu.be/Ka5_ZrSX5Ms?si=6EWSzcPYk_b_jdMK 
https://youtu.be/9iClv5GwPIA?si=gUOSe7zE3DWPaojn https://youtu.be/I7B23tqyBzQ?si=WJGRC9aAQNTDsg2x 
1.準備伺服器 Vultr服务器注册：https://www.vultr.com/?ref=8753714
有谷歌賬戶者可以直接選擇谷歌登錄
2.下载搭建工具 下載FinalShell Windows版 https://kjfx.lanzoui.com/iqm6Uosbzha 
3.儅按照視頻内容完成連接伺服器之後，我們需要進行伺服器運行環境搭建
# Hysteria 2的運行環境搭建 https://youtu.be/jeXPVqz4OEs 
更新 VPS 系统
apt update -y
apt install curl sudo -y
Hysteria 2 一键搭建代码 
wget -N --no-check-certificate https://raw.githubusercontent.com/flame1ce/hysteria2-install/main/hysteria2-install-main/hy2/hysteria.sh && bash hysteria.sh
systemctl enable hysteria-server.service   # 设置 hysteria 服务 开机自启动
systemctl status hysteria-server.service   # 查看 hysteria 服务 状态
這時我們已經完成了Hysteria 2伺服器環境搭建（此後繼續跟視頻步驟走在root文件夾找到hy文件夾將.json和.txt文件全部下載。。。。）
# xui（socks，vmess） 運行環境搭建 可用於clash  https://youtu.be/Ka5_ZrSX5Ms?si=dsM3NwG126IgIqST
我們前面已經完成了vps更新所以無需再做，
X-UI 一鍵安裝代码：
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
設置完伺服器賬號密碼之後就要給伺服器放行
放行端口
iptables -I INPUT -p tcp --dport 443 -j ACCEPT
iptables -I INPUT -p tcp --dport 54321 -j ACCEPT
如果你的面板打不開，百分百是你的放行端口出現了問題！
x-ui 管理面板设置
添加证书和密钥路径，重启面板
這時我們已經完成了xui的環境搭建（下一步是通过域名访问x-ui 管理面板：https://你的域名:54321 對你的伺服器進行下一步管理，可添加不同協議。。。）
