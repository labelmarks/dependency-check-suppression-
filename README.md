# dependency-check 是什么
dependency-check 是一款根据项目依赖来检查漏洞的白盒审计工具。

但是会有较高的误报概率。

# 目的
创建抑制误报的文件大家共同维护，避免每次需要重复识别被误报的依赖。

# 用法
执行检测是通过 --suppression suppression.xml 抑制误报


eg.
```shell
~/dev/dependency-check/bin/dependency-check.sh
--suppression ~/dev/dependency-check/suppression/suppression.xml
-s ~/Documents/DBJCA/preserve-local-V2.0/bjca-preserve-receive/bjca-preserve-receive-server/target/bjca-preserve-receive-server-2.1.2-RELEASE.jar
-o ~/Downloads/2021-10-25/存证28.html
```


> https://jeremylong.github.io/DependencyCheck/general/internals.html
> 漏洞查询：http://www.cnnvd.org.cn/web/vulnerability/querylist.tag

# suppression list
1. jedis 被误认为是 redis 
1. 公司包(格式：cn.*.bjca.*:*.*)被认为是 spring、springboot
1. cn.bjca.footstone.sword:json-api 被误认为 SWORD Project 
1. cn.bjca.footstone.sword:json-api-impl-jackson-jdk8 被误认为 SWORD Project 
1. mybatis-helper-core 被认为是 sword
1. mybatis-helper-core 被认为是 mybatis
1. mybatis-helper-boot-starter 被认为是 sword
1. mybatis-helper-boot-starter 被认为是 mybatis
1. mybatis-plus 被认为是 mybatis
1. mybatis-plus-core 被认为是 mybatis
1. mybatis-plus-helper 被认为是 mybatis
1. mybatis-plus-extension 被认为是 mybatis
1. mybatis-plus-annotation 被认为是 mybatis
1. mybatis-plus-boot-starter 被认为是 mybatis
1. CVE-2020-8022 是 SUSE openSUSE 安全漏洞，通过打 SUSE 补丁的方式升级 
## 主动忽略
1. 主动忽略 jquery 的错误
## 临时忽略
1. jdom2 2.0.6 有漏洞但是官方最新版本还没有解决，临时忽略到 2022-06-01Z