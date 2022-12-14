<div align="center">
    <img src="https://github-resources.oss-cn-hangzhou.aliyuncs.com/logo.png" alt="logo"/>
    <div>
        <a href="http://rotanovaiot.cn/">福建新航物联网科技有限公司</a>
    </div>+69
</div>
 

[![AUR](https://img.shields.io/badge/license-Apache%20License%202.0-blue.svg)](https://github.com/RotaNova/rotanova-boot/blob/master/LICENSE)
[![java](https://img.shields.io/badge/language-java-red.svg)](https://www.java.com/zh-CN/)
[![npm](https://camo.githubusercontent.com/6a1ee221c99c800e8d3b104c99033afa11d84c16f58e77632d21ed9d2370f49d/68747470733a2f2f696d672e736869656c64732e696f2f6e706d2f762f7675652e7376673f73616e6974697a653d74727565)](https://www.npmjs.com/package/vue)

[![中文文档](https://camo.githubusercontent.com/a1600097d2890201165d5e70230e40ff689e0248e028afaa1f9ca574bf78840f/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f2545362539362538372545362541312541332d2545342542382541442545362539362538372545372538392538382d626c75652e737667)](https://rotanova.yuque.com/books/share/1f659d3d-1316-4c68-93bf-3498f1b89e8a/uw90fb)
[![英文文档](https://camo.githubusercontent.com/a636695a76286d4751020a87763f0b65cbfedcd892d5750430f886f46bba7515/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f646f63756d656e742d456e676c6973682d626c75652e737667)]()


# 智慧安防管理平台简介
&emsp;&emsp; 智慧安防管理平台(以下简称ISC), 基于[asmoboot](https://github.com/RotaNova/asmoboot) 框架开发，天然具有完备的权限管理与安全机制，因具备低代码开发特性以及轻量数据中台等特性，非常适用安防项目快速二次开发。<br>
&emsp;&emsp; 智慧安防平台主持市面上所有主流摄像头接入，支持GB28181、RTSP等协议，并具备完整的级联平台以及PTZ控制；由于项目以物联网性质为主，所以还参考阿里云物联网平台开发了基于物模型管理的设备管理模块，支持直接对接阿里与物联网平台。<br>
&emsp;&emsp; 可动态配置所需的AI算法，实现智能识别，目前已有海量的场景算法，同时支持算法定制等。用户也可自行开发上传，支持插件化AI能力部署。

## 在线快速体验
在线体验网址：http://isc.rotanova.top:9980
账号：guest
密码：guest123

# 快速安装部署
    商业版体验版部署后，默认有24小时的试用时间。重装服务可重新获得24小时，需要长时间连续稳定测试使用的，请联系游先生：18965916106.


## 系统配置要求
|关键参数|要求|推荐值|推荐型号|备注|
|---|---|---|---|---|
|操作系统|x86架构Linux|CentOS7.6|CentOS7.6/Ubuntu Server|可按需兼容x86架构系统，包含所有x86架构国产操作系统。注：其他异构系统需定制开发。|
|CPU|≥2核|24核|INTEL Xeon E5-2650 V4 12C 2.2GHZ*2|主频3GHZ以下的CPU,推荐核心数为：摄像头数量/2。主频3.5GHZ以上的CPU，推荐核心数为：摄像头数量/4。|
|内存|≥32G|64G| |如果单机选择部署私有化AI服务，则需额外占用10G内存，即单机最低内存要求为48G。每个AI模型启动时约占450MB内存。 注：大型生产环境，建议集群部署，AI推理服务单独部署GPU服务器。|
|硬盘|500GB|1TB|SSD| |
|GPU|无|Nvidia GPU|≥GTX2080Ti/A100等|无GPU硬性要求，如果部署有AI推理服务，建议增加英伟达显卡，AI推理速度平均提高10倍以上。注：每个AI模型启动后，大约占用400MB显存。|
|网卡|单口千兆|多扣千兆| |摄像头数量多的情况下，需至少2个网口，将视频网与数据网隔离。注：推荐每增加64个摄像头，增加一个千兆网卡。服务器网卡背板带宽增加600MB以上。|

## 下载安装包
 > 进入[下载地址](https://github.com/RotaNova/isc/releases)
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
       SYSTEM_MONITORING_URL: 系统鉴权服务，填写部署了业务服务的IP地址，格式为：http://{IP}:9877，例如：http://127.0.0.1:9877 <br>
       MINIO_ENDPOINT: 图片服务器，填写部署了业务服务的IP地址，格式为：http://{IP}:9000，例如：http://127.0.0.1:9000 <br>
       SIP_IP: 国标接入IP, 填写部署了业务服务的IP地址，格式为：{IP},  例如：127.0.0.1 <br>
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

 6. 登录：
    > 安装完成后，浏览器[推荐chrome]进入{IP}页面，输入初始用户名：admin，密码：admin，登录成功。

 > 注： 业务服务默认安装地址为：/home/rotanova 
 
## 常见问题
 1. 网卡修改服务无法正常工作：ubuntu 14以上默认没有nmcli命令，需安装网络管理组件。安装命令为：
     > apt install network-manager
 2. 重启服务无法正常工作：
     > systemctl restart docker

## 平台授权流程
 1. 登录平台。 **默认管理员账号：admin, 密码：admin**
 2. 进入到 ***平台配置*** 板块的 ***系统维护*** 栏目，进入 ***系统授权*** 页面，点击下载机器码。
 3. 将机器码文件发给 **授权商** 进行授权证书生成。
 4. 将获得的 **授权证书** 通过 ***系统授权*** 页面的 *上传证书* 上传即可完成授权。
 
# 功能简介
## 快速入门
[产品功能使用手册](https://rotanova.yuque.com/books/share/1f659d3d-1316-4c68-93bf-3498f1b89e8a/adc6gt)
## 功能清单
<table>
<caption>智慧安防功能清单</caption>
    <tr>
        <th>系统</th>
        <th>功能模块</th>
        <th>子功能模块</th>
        <th>功能描述</th>
    </tr>
    <tr>
        <th rowspan="27">低代码套件[asmoboot]()基础包</th>
        <th rowspan="14">平台配置</th>
        <th>数据驾驶舱</th>
        <th>访问数据统计展示</th>
    </tr>
    <tr>
        <th>账户管理</th>
        <th>负责系统平台权限管理，涵盖角色管理、用户管理、部门管理与二级部门等</th>
    </tr>
    <tr>
        <th>账号设置</th>
        <th>个人账号信息设置</th>
    </tr>
    <tr>
        <th>通告管理</th>
        <th>平台消息记录中心，涵盖通知消息、系统消息、告警消息</th>
    </tr>
    <tr>
        <th>网络配置</th>
        <th>负责宿主机的物理网卡配置，默认单节宿主机部署生效。
            注：集群与分布式版本需二次沟通部署。</th>
    </tr>
    <tr>
        <th>系统监控</th>
        <th>平台运行基本信息，涵盖基本信息，性能监控，在线用户。</th>
    </tr>
    <tr>
        <th>系统维护</th>
        <th>平台信息维护，涵盖时间配置、升级维护、日志管理、系统授权</th>
    </tr>
    <tr>
        <th>安全管理</th>
        <th>平台账号安全设置内容</th>
    </tr>
    <tr>
        <th>高级配置</th>
        <th>基础涵盖钉钉对接配置、LDAP对接等</th>
    </tr>
    <tr>
        <th>平台配置</th>
        <th>涵盖样式对接、消息通知配置等</th>
    </tr>
    <tr>
        <th>消息中心</th>
        <th>个人消息管理中心，涵盖我的消息与消息接收配置</th>
    </tr>
    <tr>
        <th>资源管理</th>
        <th>技术运维人员使用，涵盖页面管理、接口管理、数据字典、表格管理、数据服务[数据源管理、API管理、应用注册]</th>
    </tr>
    <tr>
        <th>问题反馈</th>
        <th>平台用户发起问题反馈的页面</th>
    </tr>
    <tr>
        <th>反馈处理</th>
        <th>平台管理员处理问题反馈的页面</th>
    </tr>
    <tr>
        <th rowspan="7">设备配置</th>
        <th>设备管理</th>
        <th>对设备进行增删改查以及功能性操作</th>
    </tr>
    <tr>
        <th>设备分组管理</th>
        <th>涵盖设备分组信息与分组概览</th>
    </tr>
    <tr>
        <th>日志管理</th>
        <th>设备日志，涵盖设备运行 日志以及操作日志</th>
    </tr>
    <tr>
        <th>项目管理</th>
        <th>设备项目管理，涵盖项目信息与项目运维信息</th>
    </tr>
    <tr>
        <th>地图分布</th>
        <th>涵盖设备分布、网关分布、项目分布等信息，以GIS地图方式展示</th>
    </tr>
    <tr>
        <th>智能执行</th>
        <th>对设备进行软定义策略配置，涵盖策略配置、场景配置、告警配置</th>
    </tr>
    <tr>
        <th>运维管理</th>
        <th>设备运维管理，涵盖设备故障报警与隐患报警管理</th>
    </tr>
    <tr>
        <th rowspan="6">物联网平台[私有化]基础版本</th>
        <th>统计分析</th>
        <th>平台设备计入统计</th>
    </tr>
    <tr>
        <th>系统设置</th>
        <th>平台用户管理、权限管理、角色管理</th>
    </tr>
    <tr>
        <th>设备管理</th>
        <th>物联网设备的产品、设备及网关管理</th>
    </tr>
    <tr>
        <th>设备接入</th>
        <th>设备接入证书管理、协议管理、网络组件管理、设备网关管理</th>
    </tr>
    <tr>
        <th>通知管理</th>
        <th>平台通知配置、通知模板管理</th>
    </tr>
    <tr>
        <th>日志管理</th>
        <th>平台访问日志、系统日志管理</th>
    </tr>
    <tr>
        <th rowspan="33">智慧安防</th>
        <th rowspan="7">基础资料</th>
        <th>以图搜人</th>
        <th>上传图片利用人脸识别检测人员</th>
    </tr>
    <tr>
        <th>人脸分组管理</th>
        <th>人脸分组信息管理</th>
    </tr>
    <tr>
        <th>白名单管理</th>
        <th>白名单人员人脸信息管理</th>
    </tr>
    <tr>
        <th>黑名单管理</th>
        <th>黑名单人员人脸信息管理</th>
    </tr>
    <tr>
        <th>访客名单管理</th>
        <th>访客人员人脸信息管理</th>
    </tr>
    <tr>
        <th>陌生人归档名单管理</th>
        <th>系统自动研判归档的陌生人人脸信息管理</th>
    </tr>
    <tr>
        <th>名单库配置</th>
        <th>人脸名单库相关功能配置页</th>
    </tr>
    <tr>
        <th rowspan="7">智慧安防</th>
        <th>视频监控</th>
        <th>web版视频监控中台，实时预览视频画面</th>
    </tr>
    <tr>
        <th>通行记录</th>
        <th>人脸抓拍的通行记录，涵盖比对记录，陌生人记录，访客/陌生人归档记录、黑名单记录等</th>
    </tr>
    <tr>
        <th>门禁管理</th>
        <th>门禁设备通讯权限管理，涵盖通行权限配置、门禁设备管理</th>
    </tr>
    <tr>
        <th>安防服务配置</th>
        <th>安防服务功能配置页</th>
    </tr>
    <tr>
        <th>智能分析</th>
        <th>AI分析汇总页</th>
    </tr>
    <tr>
        <th>安防设备管理</th>
        <th>安防设备管理汇总页</th>
    </tr>
    <tr>
        <th>级联系统</th>
        <th>流媒体系统管理，涵盖国际接入设备管理、推流设备管理、拉流代理管理、云录像管理、流媒体节点管理、国标级联管理、国标接入信息管理、智能分析上报管理</th>
    </tr>
    <tr>
        <th rowspan="19">提供演示的AI算法</th>
        <th>人脸检测识别算法</th>
        <th>基于虹软的人脸检出与识别页面算法</th>
    </tr>
    <tr>
        <th>人员逗留检测</th>
        <th>人员长时间滞留检测</th>
    </tr>
    <tr>
        <th>人员聚集检测</th>
        <th>人员长时间聚集检测</th>
    </tr>
    <tr>
        <th>区域入侵检测</th>
        <th>人员或车辆区域入侵检测</th>
    </tr>
    <tr>
        <th>反光衣检测</th>
        <th>未穿戴反光衣检测</th>
    </tr>
    <tr>
        <th>安全帽检测</th>
        <th>未佩戴安全帽检测</th>
    </tr>
    <tr>
        <th>摔倒检测</th>
        <th>人员摔倒检测</th>
    </tr>
    <tr>
        <th>灭火器检测</th>
        <th>未按规定放置灭火器检测</th>
    </tr>
    <tr>
        <th>烟火识别检测</th>
        <th>火焰及烟雾检测</th>
    </tr>
    <tr>
        <th>攀高检测</th>
        <th>检测是否进入违规攀高区</th>
    </tr>
    <tr>
        <th>物品遗留检测</th>
        <th>检测是否遗留物品</th>
    </tr>
    <tr>
        <th>违停检测</th>
        <th>检测车辆是否违停</th>
    </tr>
    <tr>
        <th>鼠患检测</th>
        <th>检测是否有老鼠出现</th>
    </tr>
    <tr>
        <th>打电话检测</th>
        <th>检测是否有打电话或看手机等行为</th>
    </tr>
    <tr>
        <th>吸烟检测</th>
        <th>检测是否有抽烟等行为</th>
    </tr>
    <tr>
        <th>违规作业监测</th>
        <th>检测是否有人员与车辆在限制时段违规进入作业区</th>
    </tr>
    <tr>
        <th>值岗检测</th>
        <th>检测是否有规范值岗行为[多人同时巡逻]</th>
    </tr>
    <tr>
        <th>离岗检测</th>
        <th>检测是否有违规离岗行为[多人同时巡逻]</th>
    </tr>
    <tr>
        <th>消防通道阻塞检测</th>
        <th>检测消防通道是否有被阻塞</th>
    </tr>
    <tr>
        <th rowspan="2">定制</th>
        <th rowspan="2">按需定制</th>
        <th>定制设备对接</th>
        <th>视情况而定，支持硬件定制开发以及定制开发设备对接中间件</th>
    </tr>
    <tr>
        <th>定制算法</th>
        <th>视情况而定，定制开发所需的AI模型</th>
    </tr>
</table>

# 开放能力

## AI能力支持

## 现有算法清单

![现在算法清单](https://github-resources.oss-cn-hangzhou.aliyuncs.com/aiList.png)
## 动态配置设备AI能力
![AIdemo](https://github-resources.oss-cn-hangzhou.aliyuncs.com/AI.jpeg)

在我们平台中，可自由针对接入的摄像头、无人机监控等视频流数据配置AI扩展能力，快速交付业务。

# 友情链接


