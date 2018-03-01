# 开发环境

## 环境说明

一般情况下，一个项目 **应该** 有以下三个基本的项目环境：

- Local - 开发环境
- Staging - 线上测试环境
- Production - 线上生产环境

## Production 生产环境

一般由运维配置

## Local 开发环境

开发中台项目时使用中台提供的开发环境，其他项目 **必须** 使用 **Homestead** 作为应用程序运行的环境。请阅读 [为什么必须使用 Homestead 来开发 Laravel 应用？](https://laravel-china.org/articles/4668/why-do-you-have-to-use-homestead-to-develop-laravel-applications) 。

## Staging 线上测试环境

除了域名等其他独立应用配置以外，环境 **必须** 跟 Production 保持高度一致性，可以的话 **应该** 与 Production 使用同台机器。