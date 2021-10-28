因为权限问题，项目被 http://192.168.131.1/opensource/dependency-check-suppression 代替

# dependency-check 是什么
dependency-check 是一款根据项目依赖来检查漏洞的白盒审计工具。

但是会有较高的误报概率。

# 目的
创建抑制误报的文件大家共同维护，避免每次需要重复识别被误报的依赖。

# 用法
执行检测命令时使用 --suppression suppression.xml 抑制误报


eg.
```shell
~/dev/dependency-check/bin/dependency-check.sh --suppression http://192.168.131.1/opensource/dependency-check-suppression/raw/master/suppression.xml -s /bedrock-oss-server-1.0.0-SNAPSHOT.jar -o /2021-10-26/文件存储2.2.5版本20.html
```


> https://jeremylong.github.io/DependencyCheck/general/internals.html
> 漏洞查询：http://www.cnnvd.org.cn/web/vulnerability/querylist.tag

# suppression list
1. jedis 被误认为是 redis 
1. 公司包(格式：cn.*.bjca.*:*.*)被认为是 spring、springboot、sword、mybatis/storage
1. mybatis-plus 被认为是 mybatis
1. mybatis-plus-* 被认为是 mybatis
1. CVE-2020-8022 是 SUSE openSUSE 安全漏洞，通过打 SUSE 补丁的方式升级 

## 主动忽略
1. 主动忽略 jquery

## 临时忽略
1. jdom2 2.0.6 有漏洞但是官方最新版本还没有解决，临时忽略到 2022-06-01Z