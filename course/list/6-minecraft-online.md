---
icon: fa-solid fa-gamepad
---
# minecraft联机教程

::: info 使用须知
这个方法小白可能不太好上手，并且需要一定的网络知识，所以请有一定网络知识的人使用
:::

<iframe
  :src="$withBase('/course/list/6.html')"
  width="100%"
  height="400"
  frameborder="0"
  scrolling="No"
  leftmargin="0"
  topmargin="0"
/>

## 1. 同局域网
同局域网联机基本上点击多人游戏就会显示（服务器除外）
应该不需要过多赘述
## 2. 内网穿透
### LoCyanFrp
官网：[乐青映射 | LoCyanFrp](https://locyanfrp.cn/)  
::: warning
==**LoCyanFrp注册完需要实名认证才能正常使用**==  
==**LoCyanFrp注册完需要实名认证才能正常使用**==  
==**LoCyanFrp注册完需要实名认证才能正常使用**==  
:::

 1. 创建隧道  
 打开LoCyanFrp官网，点击导航栏的隧道操作，点击添加隧道，选择合适的节点。  
 ::: tip 节点的选择
 正常情况下**建议选择离你最近的节点**，**如果选择离你较远的节点，可能会导致延迟较高**，选择前**建议先看看节点状态再选择**。
 :::
 **配置：**  
 隧道名：任意  
 穿透协议：java版选择**TCP**  
 内网端口：游戏正在使用的端口  
 远程端口：直接点击旁边的随机端口  
 点击**创建**  

 2. 启动**LoCyanFrp**客户端  
 在 隧道操作 > 隧道列表  
 点击网页卡片的 **一键启动** 按钮  
 然后点击 **『没安装...』** 按钮  
 安装之后再点击**一键启动**按钮然后点击 **『已经安装好了』** 按钮
3. 启动**Minecraft**  
 打开Minecraft，点击多人游戏，选择**服务器**，输入**内网穿透的远程端口**，点击**加入服务器**  
## WireGuard
### Tailscale
官网：[Tailscale · Best VPN Service for Secure Networks](https://tailscale.com/)
 1. 注册并登录Tailscale  
 2. 下载客户端  
 到官网下载对应的客户端
 3. 安装客户端  
 （应该不需要描述）
 4. 登录客户端  
  运行之后右键托盘图标进行登录  
 5. 打开Tailscale管理面板  
 找到刚才添加的设备点击 **『···』** 旁边的 **『Share』** 进行分享设备
 6. 让好友添加这个设备
 7. 启动Minecraft  
 打开Minecraft，点击多人游戏，选择**服务器**，输入**分享设备的地址**，点击**加入服务器**
 ::: danger
 ==不要把分享链接给任意人，因为他们可以访问设备的所以端口==
 :::
## IPv6
IPv6测试：[www.test-ipv6.com](https://www.test-ipv6.com/)  
如果显示 **IPv6 状况评分** 是 **10/10** 那么是最佳的  
::: danger 注意
==双方必须都有IPv6地址，不然无法连接==  
==双方必须都有IPv6地址，不然无法连接==  
==双方必须都有IPv6地址，不然无法连接==  
:::

