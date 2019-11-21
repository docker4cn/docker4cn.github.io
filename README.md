# docker4cn - Docker for China

在中国使用基础镜像，除了基本的镜像下载以外，还有一系列问题，影响`docker build`的效率。
[docker4cn]这个项目的目的，是提供一些基础镜像，原生解决这些问题。

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
- [ ] 在root用户配置中国PyPI镜像
- [ ] 在root用户配置中国NPM镜像
- [ ] 在root用户配置中国Maven镜像

## 镜像

目前计划中，有以下镜像及版本：

- 系统类
    - [x] [debian](/debian/)
        - [x] buster
        - [x] stretch
    - [ ] alpine
    - [ ] ubuntu
    - [ ] centos
- 语言类
    - [ ] python
    - [ ] java
    - [ ] node
- 工具类
    - [ ] nginx
    - [ ] postgres
    - [ ] jenkins

## 其它

如果希望更新、改进，请提[issues]或PR。

[issues]:https://github.com/docker4cn/docker4cn.github.io/issues/new
