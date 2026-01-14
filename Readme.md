## 前提

- [Running_page](https://github.com/yihong0618/running_page)部署过于复杂，很多人折腾了半天也不知道怎么部署。

- 今天查看仓库页面，发现其支持了docker部署。所以构建此仓库，通过docker部署，方便更多人使用。
## 使用步骤

1. fork本仓库。
2. 进入-settings-secrets-actions添加以下New Repository Secrets。
- DOCKERHUB_TOKEN
- DOCKERHUB_USERNAME
- KEEP_PASSWORD
- KEEP_PHONE_NUMBER
- MY_NAME
- DIS1
- DIS2
- DIS3
- MAPBOX
- SITEtitle
- SITEurl
- SITEdescription
- BLOGurl
- ABOUTurl

3. 手动执行actions构建。

### 版本说明

v0.0.1
- 使用豆包协助编写workflow文件，成功自动构建镜像并推送至GitHub。
- 后面有空就总结下操作步骤。