[TOC]

# 【README】

java字段校验方法，总结自[java字段校验](https://blog.csdn.net/rao991207823/article/details/117001686)

本文采用spring框架对字段进行校验，总结自[https://spring.io/guides/gs/validating-form-input](https://spring.io/guides/gs/validating-form-input)  , [spring校验方法](https://docs.spring.io/spring-framework/reference/core/validation/beanvalidation.html)

# 【1】需求来源：日常校验需求

日常开发中，我们时常需要提供可靠的 API 接口，此时对于请求的入参就需要校验，以保证最终数据入库的正确性，这就成了必不可少的活。例如说，用户注册时，会校验手机格式的正确性、邮箱格式的正确性、密码非弱密码等。

# 【2】validation介绍

## validation介绍

validation 技术在Java中运用最早在2009 年，Java 官方提出了 Bean Validation 规范，而后经历了JSR303、JSR349、JSR380 三次标准的更迭，发展到了 2.0 。

Bean Validation 和 我们以前学习过的 JPA 一样，只提供规范，不提供具体的实现。因此实际使用过程，常用的是 hibernate 的校验组件：org.hibernate.hibernate-validator

### 【2.1】常见的注解

通常情况下，在javax.validation.constraints 包下，定义了一系列的约束（constraint）注解，一共 22 个注解，快速略过即可。如下：

空和非空检查

- @NotBlank：只能用于字符串不为 null ，并且字符串 .trim() 以后 length 要大于 0 。

- @NotEmpty：集合对象的元素不为 0 ，即集合不为空 。
- @NotNull：不能为 null 。
- @Null：必须为 null 。

数值检查

- @DecimalMax(value)：被注释的元素必须是一个数字，其值必须小于等于指定的最大值。

- @DecimalMin(value)：被注释的元素必须是一个数字，其值必须大于等于指定的最小值。
- @Digits(integer, fraction)：被注释的元素必须是一个数字，其值必须在可接受的范围内。
- @Positive：判断正数。
- @PositiveOrZero：判断正数或 0 。
- @Max(value)：该字段的值只能小于或等于该值。
- @Min(value)：该字段的值只能大于或等于该值。
- @Negative：判断负数。
- @NegativeOrZero：判断负数或 0 。

Boolean 值检查

- @AssertFalse：被注释的元素必须为 true 。

- @AssertTrue：被注释的元素必须为 false 。

长度检查

- @Size(max, min)：检查字段的 size 是否在 min 和 max 之间，可以是字符串、数组、集合、Map 等。


日期检查

- @Future：被注释的元素必须是一个将来的日期。

- @FutureOrPresent：判断日期是否是将来或现在日期。
- @Past：检查该字段的日期是在过去。
- @PastOrPresent：判断日期是否是过去或现在日期。

其它检查

- @Email：被注释的元素必须是电子邮箱地址。
- @Pattern(value)：被注释的元素必须符合指定的正则表达式。



## 【2.2】@Valid和 @Validated

@Valid 注解，是 Bean Validation 所定义，可以添加在普通方法、构造方法、方法参数、方法返回、成员变量上，表示它们需要进行约束校验。

@Validated 注解，是 Spring Validation 锁定义，可以添加在类、方法参数、普通方法上，表示它们需要进行约束校验。同时，@Validated 有 value 属性，支持分组校验。

对于初学者来说，很容易搞混 @Valid 和 @Validated 注解。

<br>

---

# 【3】maven引入spring-boot-starter-validation依赖

```xml
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-validation</artifactId>
            <version>3.5.7</version>
        </dependency>
```

<br>

---

# 【4】测试案例

【4.1】

















