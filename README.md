# 简介 #

> 源码地址

- GitHub：[https://github.com/battcn/swagger-spring-boot](https://github.com/battcn/swagger-spring-boot "https://github.com/battcn/swagger-spring-boot")
- 码云：[https://gitee.com/battcn/spring-boot-starter-swagger/](https://gitee.com/battcn/spring-boot-starter-swagger/ "https://gitee.com/battcn/spring-boot-starter-swagger/")

`swagger-spring-boot-starter` 是一款建立在`swagger`基础之上的工具包，利用SpringBoot自动装配的特性，简化了传统`swagger`的繁琐配置

> 项目介绍

- **`swagger-vue` ：采用 Vue 编写的源代码**
- **`swagger-vue-ui` ：编译后的纯 HTML 文件**
- **`swagger-spring-boot-starter` ： 自动装配 swagger 的扩展包**

有兴趣扩展自己的Starter包的可以参考文章：[编写自己的starter项目](http://blog.battcn.com/2017/07/13/springboot/springboot-starter-swagger/ "编写自己的starter项目")

**如果该项目对您有帮助，欢迎Fork和Star，有疑问可以加 `QQ：1837307557`一起交流 ，如发现项目BUG可以提交`Issue`**

# 使用 #


- 在`pom.xml`中引入依赖：

``` xml
<dependency>
    <groupId>com.battcn</groupId>
    <artifactId>swagger-spring-boot-starter</artifactId>
    <version>${最新版本：当前2.0.1还在开发 请用 1.4.5-RELEASE}</version>
</dependency>
```

- 在`application.yml`中添加

``` yaml
spring:
  swagger:
    enable: true
```

- 在`application.properties`中添加

``` properties 
spring.swagger.enable=true
```


# 更新记录 #
```
2.0.1
  发布时间：未定
  更新内容：
    1.重写UI
    2.升级Spring Boot 为2.0.2
1.4.5
  发布时间：2018年04月26日
  更新内容：
    1.解决配置 `context-path` 导致 `swagger-ui.html` 无法显示BUG
1.4.4
  发布时间：2018年01月05日
  更新内容：
    1.优化选项卡切换
1.4.3
  发布时间：2017年12月22日
  更新内容：
    1.修复CRUL口令
    2.提升操作体验
1.4.2
  发布时间：2017年12月15日
  更新内容：
    1.修复CRUL口令
    2.渲染菜单列表颜色
1.4.1
  发布时间：2017年12月13日
  更新内容：
    1.修复CRUL口令
    2.修复DELETE类型请求部分存在404问题
1.4.0
  发布时间：2017年12月14日
  更新内容：
    1.PATCH无法正确渲染
1.3.9
  发布时间：2017年9月17日 
  更新内容：
    1.修复对象深度拷贝
1.3.8
  发布时间：2017年12月8日 
  更新内容：
    1. 解决1.1.0发版中的bug    
1.1.0
  发布时间：2017年12月1日
  更新内容：
    1. 完成基础功能
```

# 重写UI #


> 操作风格 - 1.4.3支持

![接口说明](https://github.com/battcn/swagger-spring-boot/blob/master/doc/img/4.png)

> 接口说明：折叠式Model

![接口说明](https://github.com/battcn/swagger-spring-boot/blob/master/doc/img/1.png)


> 接口说明：折叠式表单响应内容，告别长长的滚动条

![接口说明](https://github.com/battcn/swagger-spring-boot/blob/master/doc/img/2.png)

> 在线调试

![在线调试](https://github.com/battcn/swagger-spring-boot/blob/master/doc/img/3.png)


## 配置说明 ##

`spring.swagger.enabled`：提供该配置目的是方便多环境关闭，一般生产环境中不会暴露它，这时候就可以通过 `java -jar xx.jar --spring.swagger.enabled=false` 动态关闭，也可以在多环境配置写好


### properties ###

```
spring.swagger.enabled=是否启用swagger，默认：true
spring.swagger.title=标题
spring.swagger.description=描述信息
spring.swagger.version=版本
spring.swagger.license=许可证
spring.swagger.licenseUrl=许可证URL
spring.swagger.termsOfServiceUrl=服务条款URL
spring.swagger.contact.name=维护人
spring.swagger.contact.url=维护人URL
spring.swagger.contact.email=维护人email
spring.swagger.base-package=swagger扫描的基础包，默认：全扫描
spring.swagger.base-path=需要处理的基础URL规则，默认：/**
spring.swagger.exclude-path=需要排除的URL规则，默认：空
spring.swagger.host=文档的host信息，默认：空
spring.swagger.globalOperationParameters[0].name=参数名
spring.swagger.globalOperationParameters[0].description=描述信息
spring.swagger.globalOperationParameters[0].modelRef=指定参数类型
spring.swagger.globalOperationParameters[0].parameterType=指定参数存放位置,参考ParamType:(header,query,path,body,form)
spring.swagger.globalOperationParameters[0].required=指定参数是否必传，默认false
#下面分组是
spring.swagger.groups.<name>.basePackage=swagger扫描的路径
#比如
spring.swagger.groups.基础信息.basePackage=com.battcn.controller.basic
```


### yaml ###

以下为 `application.yml` 配置示例

``` yaml
spring:
  swagger:
    enabled: true
    title: 标题
    description: 描述信息
    version: 系统版本号
    contact:
      name: 维护者信息
    base-package: swagger扫描的基础包，默认：全扫描(分组情况下此处可不配置)
    #全局参数,比如Token之类的验证信息可以全局话配置
    global-operation-parameters:
    -   description: 'Token信息,必填项'
        modelRef: 'string'
        name: 'Authorization'
        parameter-type: 'header'
        required: true
    groups:
      基础资料:
        base-package: com.battcn.controller.basic
      系统设置:
        base-package: com.battcn.controller.system
```


# 贡献者 #

Levin：1837307557@qq.com  

- 个人博文：[http://blog.battcn.com](http://blog.battcn.com "http://blog.battcn.com")

_Rock：995269937@qq.com


# 常用注解说明 #

* `@Api`:一般用于Controller中,用于接口分组。（**`如：@Api(value = "用户接口", description = "用户接口", tags = {"1.1.0"})`**

* `@ApiOperation`:接口说明,用于api方法上。（**`如： @ApiOperation(value = "用户查询", notes = "根据ID查询用户信息")`**）

* `@ApiImplicitParam`:参数说明,适用于只有一个请求参数,主要参数

* `@ApiImplicitParams`:多个参数说明,主要参数参考上面`@ApiImplicitParam`

* `@ApiModel`:实体类说明

* `@ApiModelProperty`：实体参数说明


# 如何参与 #

有兴趣的可以联系本人（Pull Request），参与进来一起开发，美化UI与配置项一起完善
