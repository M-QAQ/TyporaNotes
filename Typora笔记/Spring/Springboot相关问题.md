---
目录
---

[TOC]



# 一、SpringBoot是怎么做自动装配的？自动配置的方式有哪些，优缺点是什么？在SpringBoot的场景是怎样使用的？

## 自动配置原理

配置文件到底能写什么？怎么写？

官网

#### 原理

1）、SpringBoot启动的时候加载主配置类，开启了自动配置功能==@EnableAutoConfiguration==

2）、@EnableAutoConfiguration作用：

	- 利用AutoConfigurationImportSelector给容器中导入了 一些组件
	- 可以查看selectImports方法的内容；
	- 

​				





























# 二、SpringBoot是怎么让“java -jar”这行代码跑起来的？

# 三、SpringBoot的条件注解实现原理是怎么样的？怎么排查项目中哪些条件注解的条件不满足？



### 1、@Conditional派生注解 ( Spring注解版原生的@Conditional作用)

作用:必须是@Conditional指定的条件成立,才给容器中添加组件,配置配里面的所有内容才生效;

| @Conditional扩展注解          | 作用(判断是否满足当前指定条件)                     |
| ----------------------------- | -------------------------------------------------- |
| @ConditionalOnJava            | 系统的java版本是否符合要求                         |
| @ConditionalOnBean            | 容器中存在指定Bean ;                               |
| @ConditionalOMissingBean      | 容器中不存在指定Bean ;                             |
| @ConditionalOnExpression      | 满足SpEL表达式指定                                 |
| @ConditionalOnClass           | 系统中有指定的类                                   |
| @ConditionalOnMissingClass    | 系统中没有指定的类                                 |
| @ConditionalOnSingleCandidate | 容器中只有一一个指定的Bean ,或者这个Bean是首选Bean |
| @ConditionalOnProperty        | 系统中指定的属性是否有指定的值                     |
| @ConditionalOnResource        | 类路径下是否存在指定资源文件                       |
| @ConditionalOnWebApplication  | 当前是web环境                                      |

**自动配置类必须在一定的条件下才能生效;**

### 2、我们怎么知道哪些自动配置类生效

我们可以通过启用==debug=true==属性;来让控制台打印自动配置报告,这样我们就可以很方便的知道哪些自动配置
类生效；

```java
=========================
AUTO- CONF IGURATION REPORT
=========================
Positive matches:(自动配置类启用的)
DispatcherServletAutoConfiguration matched:
@ConditionalOnClass found required Class
'org.springframework.web.servlet.DispatcherServlet' ; @ConditionalonMissingClass did not find
unwanted class (OnClassCondition)
@ConditionalonWebApplication (required) found StandardServletEnvironment
(OnWebApplicationCondition)
Negative matches: (没有启动,没有匹配成功的自动配置类)
ActiveMQAutoConfiguration:
Did not match: 
@ConditionalonClass did not find required cClasses 'javax.jms.connectionFactory',
'org.apache.activemq.ActiveMQConnectionFactory' (OnClassCondition)
AopAutoConfiguration:
Did not match: 
@ConditionalonClass did not find required Classes
'org.aspectj.lang.annotation.Aspect'，'org.aspectj.1ang.reflect.Advice' (OnClassCondition)

```



# 四、我们常用的“starter”有哪些？他们有什么巧妙的地方？有根据项目自定义哪些“starter”？





