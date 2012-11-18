---
layout: post
title: "Spring MVC 的 response content-type 问题"
date: 2012-11-18 16:14
comments: true
categories: 
---

如果你使用 Spring MVC 写了一个 Ajax 接口，返回的数据是 json 格式，那么你可能会遇到在 IE 下请求该接口会出现一个文件下载框的问题。

之所以会产生这个问题，是因为如果采用 Spring 默认的配置，json 响应的 content-type 是 application/json，而 IE 10 以前的浏览器对于这个类型是作为文件下载的。解决方法是只要将返回响应的 content-type 改为text/plain 即可。

如果你使用了 &lt;mvc:annotation-driven /&gt;，那么修改起来比较简单：

```
    <mvc:annotation-driven conversion-service="conversionService"
        ignoreDefaultModelOnRedirect="true">
        <mvc:message-converters register-defaults="false">
            <bean class="org.springframework.http.converter.ByteArrayHttpMessageConverter" />
            <bean class="org.springframework.http.converter.StringHttpMessageConverter">
                <property name="supportedMediaTypes" value="text/plain;charset=UTF-8" />
            </bean>
            <bean class="org.springframework.http.converter.json.MappingJacksonHttpMessageConverter">
                <property name="supportedMediaTypes" value="text/plain;charset=UTF-8" />
            </bean>
        </mvc:message-converters>
    </mvc:annotation-driven>
```
