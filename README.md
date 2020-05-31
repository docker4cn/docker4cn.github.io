# docker4cn - Docker for China

在中国使用基础镜像，除了基本的镜像下载以外，还有一系列问题，影响`docker build`的效率。
[docker4cn]这个项目的目的，是提供一些基础镜像，原生解决这些问题。

由于使用GitHub开源与Docker Hub自动构建的形式，因此镜像内容公示，也不会被篡改，安全性向官方镜像看齐。

[docker4cn]:https://docker-4.cn

## 定制

为了中国区的使用，会做出以下定制：

- [x] 换官方源为中国的https源，在TAG中会以后缀体现
    - `ustc`：[mirrors.ustc.edu.cn](https://mirrors.ustc.edu.cn)
    - `tuna`：[mirrors.tuna.tsinghua.edu.cn](https://mirrors.tuna.tsinghua.edu.cn)
    - `aliyun`：[mirrors.aliyun.com](https://mirrors.aliyun.com)
    - `huawei`：[mirrors.huaweicloud.com](https://mirrors.huaweicloud.com)
    - `163`：[mirrors.163.com](https://mirrors.163.com)
- [x] 预装`ca-certificates`证书包
- [x] 预装`tzdata`，设置时区为中国的`+8`区（`Asia/Shanghai`）
- [x] 在root用户配置中国PyPI镜像
- [x] 在root用户配置中国NPM镜像
- [x] 在root用户配置中国Gradle镜像
- ……

## 镜像

目前计划中，有以下类型的镜像及版本：

- 系统类
    - [x] [debian]
        - [x] buster
        - [x] stretch
    - [x] [alpine]
        - [x] 3.12
        - [x] 3.11
        - [x] 3.10
    - [ ] [ubuntu]
    - [ ] [centos]
- 语言类
    - [ ] [python]
    - [ ] [node]
    - [ ] java
- 工具类
    - [ ] [nginx]
    - [ ] [jenkins]

镜像命名方式，统一为`docker4cn/<名称>:<版本>-<类型>`。
比如，`docker4cn/debian:buster-ustc`、`docker4cn/alpine:3.12-tuna`等。

[debian]:/debian/
[alpine]:/alpine/
[ubuntu]:/ubuntu/
[centos]:/centos/
[python]:/python/
[node]:/node/
[nginx]:/nginx/
[jenkins]:/jenkins/

## 设计

虽然在设计上采用同一种镜像配置同一种源，比如标记为`huawei`的镜像统一配`huawei`的系统源与`pip`、`npm`等。
但是由于国内各大镜像站的支持各不相同，因此会有细节上的不同之处。

- `ustc`的PyPI，实际配置的是`tuna`的源，因为它会重定向过去到`tuna`。
- alpine没有`163`镜像，因为它不提供。
- `ustc`、`tuna`没有Gradle的镜像，实际配置的是`aliyun`。
- `ustc`、`tuna`和`163`没有NPM的镜像，实际配置的是`aliyun`。

另外，华为源（<https://mirrors.huaweicloud.com>）是各镜像站中，帮助信息最完善的。
docker4cn计划的方案，大量参考了其文档、照搬了其配置。
推荐不懂行的小白用户，在配置自己的源时优先参考。

至于镜像的选择，则取决于运行环境。
教育网用户推荐使用`ustc`或`tuna`，各云服务用户推荐使用匹配的云服务镜像。
如果是本地开发，建议通过`ping`等网络测试手段，确认最合适的镜像站。

## 计划

这是一个业余项目，分阶段进行。

- [第一阶段]：建立常用的[debian]和[alpine]镜像，探索相关信息，验证自动构建方案。
- [第二阶段]：补充系统镜像，添加具有代表性的语言级与工具类镜像。
- 第三阶段：尚未规划，也可能没有。这取决于是否有人使用，以及人力与兴趣情况。

详情可查看[Projects]。

[Projects]:https://github.com/orgs/docker4cn/projects
[第一阶段]:https://github.com/orgs/docker4cn/projects/1
[第二阶段]:https://github.com/orgs/docker4cn/projects/2

## 维护

如果希望新增、更新、改进，请提[issues]或PR。

[issues]:https://github.com/docker4cn/docker4cn.github.io/issues/new
