# 简介

sidecar 的方式使用 nacos 动态更新Nginx upstream 实现对Nacos的服务发现.

# 版本要求

nacos2.x 测试通过

# 快速启动

## 配置config.toml

配置文件使用[TOML](<https://github.com/toml-lang/toml>)进行配置

| 参数               | 描述                                | 例子                                                      |
| ------------------ |-----------------------------------|---------------------------------------------------------|
| nginx_cmd          | nginx命令的全路径                       | "/usr/sbin/nginx"                                       |
| nacos_addr         | nacos的地址                          | "172.16.0.100:8848,172.16.0.101:8848,172.16.0.102:8848" |
| nacos_namespace    | nacos的namespace(Id)               | "xxxxxx"                                                | 
| nacos_group    | nacos的group                       | "xxxxxx"                                                | 
| reload_interval    | nginx reload命令执行间隔时间（ms  默认值1000） | 1000                                                    |
| nginx_config       | 需要修改nginx配置的路径                    | "/etc/nginx/nginx.conf"                                 |
| nginx_upstream     | nginx中upstream的名字                 | "nacos-service"                                         |
| nacos_service_name | nacos服务名                          | 对应nacos 服务列表-服务名称                                       |

## 启动

需要与NGINX同一机器

```shell
java -jar target/nacos-nginx-template-jar-with-dependencies.jar --config=xxx.toml
```

参考: https://github.com/YeautyYE/nacos-nginx-template