## 致谢


感谢 https://github.com/yihong0618/running_page 和所有的贡献者，让跑步爱好者有这样的运动汇聚功能。


## 前提

- [Running_page](https://github.com/yihong0618/running_page)部署过于复杂，很多人折腾了半天也不知道怎么部署。

- 今天查看仓库页面，发现其支持了docker部署。所以构建此仓库，通过docker部署，方便更多人使用。

## 使用步骤

1. fork本仓库。
2. 进入-settings-secrets-actions添加以下New Repository Secrets。
```
- DOCKERHUB_TOKEN  填写你的dockerhub密码
- DOCKERHUB_USERNAME  填写你的dockerhub用户名
- KEEP_PASSWORD  填写你的keep密码
- KEEP_PHONE_NUMBER 填写你的keep手机号
- MY_NAME  填写你想展示的名字
- DIS1  最小距离，建议填写2
- DIS2  最小距离1，建议填写5
- DIS3  最小距离2，建议填写10
- MAPBOX 填写你自己的token
- SITEtitle 填写你想要的网站名
- SITEurl 填写你跑步的网址
- SITEdescription 填写你的网站描述
- BLOGurl  填写你的博客地址
- ABOUTurl 填写关于你的地址
- BIRTH 填写你的生日
- STRAVA_CLIENT_ID 填写你的
- STRAVA_CLIENT_SECRET 填写你的
- STRAVA_REFRESH_TOKEN 填写你的
```
3. 手动执行actions构建。
4. 每天UTC 0:00自动构建PUSH。
5. 创建compose文件。docker-compose.yml
- 简化版
```YML
services:
  running_page:
    container_name: running_page
    restart: always  
    ports:
        - 7777:80
    image: wangweitung/running_page:latest
```
- 自动更新版，需要自行配置watchtower
```YML
services:
  running_page:
    container_name: running_page
    restart: always  
    ports:
        - 7777:80
    image: wangweitung/running_page:latest
    labels:
      - "com.centurylinklabs.watchtower.enable=true"  
```
- 启动：
```
cd /vol1/1000/docker/running_page/ && sudo docker compose up -d
```
- 访问
  - http://ip:7777
  
### 版本说明

v0.0.3

- 解决了summary无法显示的问题。
- 默认调整为Strava。
- 更新了Readme。
- 增加了致谢。



v0.0.2

- 更新了页面自定义。
- 使用了自有的mapbox token。
- 调整了页面生成的距离阈值。


v0.0.1
- 使用豆包协助编写workflow文件，成功自动构建镜像并推送至GitHub。
- 后面有空就总结下操作步骤。