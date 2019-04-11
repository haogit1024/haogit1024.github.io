---
title: Spring Security笔记
date: 2019-04-08 11:21:36
tags:
---
## 常用的接口
#### WebSecurityConfigurerAdapter
WebSecurityConfigurerAdapter主要用于配置Spring Security

#### UserDetail
一个包含用户信息和权限信息的类

#### UserDetailsService
用户给Spring Security返回一个UserDetail。把该接口的实现类配置成Spring Bean, Spring Security会默认使用该类返回的UserDetail来验权等操作

#### 大致流程
1. 用户提交用户名和密码，后端将密码加密有和数据库密码比对。如果一样，返回JWT
1. 用户使用JWT请求其他接口。后端获取用户名后从数据库中获取用户详细信息，然后校验权限和返回数据
