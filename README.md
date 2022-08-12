<div align="center">
    <img src="https://github-resources.oss-cn-hangzhou.aliyuncs.com/logo.png" alt="logo"/>
</div>


[![AUR](https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg)](https://github.com/RotaNova/rotanova-boot/blob/master/LICENSE)
[![java](https://img.shields.io/badge/language-java-red.svg)](https://www.java.com/zh-CN/)

# 智慧安防管理平台简介
&emsp; 智慧安防管理平台(以下简称ISC), 基于[asmoboot](https://github.com/RotaNova/asmoboot) 框架开发，天然具有完备的权限管理与安全机制，因具备低代码开发特性以及轻量数据中台等特性，非常适用安防项目快速二次开发。<br>
&emsp; 智慧安防平台主持市面上所有主流摄像头接入，支持rtsp, rtmp等，并可动态配置所需的AI算法，实现智能识别，目前已有海量的场景算法，同时支持算法定制等。用户也可自行开发上传，支持插件化AI能力部署。


# 快速安装部署
    商业版体验版部署后，默认有24小时的试用时间。重装服务可重新获得24小时，需要长时间连续稳定测试使用的，请联系游先生：18965916106.
 1. 在release选择最新版，下载其中的[install.tar.gz], 下载后将文件解压到要部署的服务器，会出现如下四个文件:
    > .env: 项目环境变量 <br>
      isc.tar.gz: 业务数据 <br>
      install.sh: 安装脚本 <br>
      uninstall.sh: 卸载脚本 <br>
 2. 进入 install目录，修改.env文件中的如下变量：
     > SIP_DOMAIN:  为国标域，可按客户需求自行更改。<br>
       SIP_ID: 为服务器国标编码，可按客户需求自行更改，需满足要求编码规范。 <br>
       SIP_PASSWORD: 国标连接密码，自行修改。<br>
       AIHUB_URL: AI服务器地址，填写部署了AI服务的IP地址， 格式为：http://{IP}:8866，例如：http://127.0.0.1:8866 <br>
       SYSTEM_MONITORING_URL:  填写部署了业务服务的IP地址，格式为：http://{IP}:9877，例如：http://127.0.0.1:9877 <br>
       MINIO_ENDPOINT: 填写部署了业务服务的IP地址，格式为：http://{IP}:9000，例如：http://127.0.0.1:9000 <br>
       SIP_IP: 填写部署了业务服务的IP地址，格式为：{IP},  例如：127.0.0.1 <br>
 3. 开放服务器端口：
    1. 必须开放:
       > 80: web页面端口 <br>
       9000: 图片服务端口 <br>
       9877: 鉴权服务端口 <br>
       *8866: AI服务端口，如果安装了离线AI部署包，则必须开放 <br>
    3. 按需开放:
       > 5060: 国标设备接入端口 <br>
       8083: MQTT端口 <br>
       8082: 低代码开发页面端口 <br>
       7044: 安防服务swagger接口文档 <br>
       7035: 物联网设备swagger接口文档 <br>
       
      
 4. 安装单机业务服务，执行命令：
     > sh install.sh
 5. 卸载单机业务服务，执行命令：
     > sh uninstall.sh
 
 > 注： 业务服务默认安装地址为：/home/rotanova 
 
## 常见问题
 1. 网卡修改服务无法正常工作：ubuntu 14以上默认没有nmcli命令，需安装网络管理组件。安装命令为：
     > apt install network-manager
 2. 重启服务无法正常工作：
     > systemctl restart docker

# 平台授权流程
 1. 打开浏览器，输入部署业务服务的服务器IP地址，登录页面。[默认管理员账号：admin, 密码：admin]
 2. 进入到[平台配置]板块的[系统维护]栏目，进入[系统授权]页面，点击下载机器码。
 3. 将机器码文件发给授权商进行授权证书生成。
 4. 将获得的授权证书通过[系统授权]页面的‘上传证书’上传即可完成授权。

# 功能清单


