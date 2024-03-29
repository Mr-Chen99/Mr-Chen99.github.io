---
title: 一、环境搭建
date: 2023-03-11 22:10:40
categories:
- Java
- 项目整理
- 某马XX交友项目技术与业务整理
tags:
- 项目
- 学习
---

## 1、项目介绍

探花交友是一个陌生人的在线交友平台，在该平台中可以搜索附近的人，查看好友动态，平台还会通过大数据计算进行智能推荐，通过智能推荐可以找到更加匹配的好友，这样才能增进用户对产品的喜爱度。探花平台还提供了在线即时通讯功能，可以实时的与好友进行沟通，让沟通随时随地的进行。

### 1.1、功能列表

| 功能       | 说明                                           | 备注                                           |
| ---------- | ---------------------------------------------- | ---------------------------------------------- |
| 注册、登录 | 用户无需单独注册，直接通过手机号登录即可       | 首次登录成功后需要完善个人信息                 |
| 交友       | 主要功能有：测灵魂、桃花传音、搜附近、探花等   |                                                |
| 圈子       | 类似微信朋友圈，用户可以发动态、查看好友动态等 |                                                |
| 消息       | 通知类消息 + 即时通讯消息                      |                                                |
| 小视频     | 类似抖音，用户可以发小视频，评论等             | 显示小视频列表需要进行推荐算法计算后进行展现。 |
| 我的       | 我的动态、关注数、粉丝数、通用设置等           |                                                |

### 1.2、项目背景

探花交友项目定位于 **陌生人交友市场**。

- 根据《2018社交领域投融资报告》中指出：虽然相比2017年，投融资事件减少29.5%，但是融资的总额却大幅增长，达到68%。
- 这些迹象说明：社交领域的发展规模正在扩大，而很多没有特色的产品也会被淘汰。而随着那些尾部产品的倒下，对我们来说就是机会，及时抓住不同社交需求的机会。以社交为核心向不同的细分领域衍生正在逐渐走向成熟化。
- 而我们按照娱乐形式和内容为主两个维度，将社交行业公司分类为：即时通信、内容社群、陌生人社交、泛娱乐社交以及兴趣社交几个领域。
- 而在2018年社交的各个细分领域下，均有备受资本所关注的项目，根据烯牛数据2018年的报告中，也同样指出：内容社交及陌生人社交为资本重要关注领域，合计融资占比达73%。

![img](clip_image002.jpg)

根据市场现状以及融资事件来看：陌生人社交、内容社群、兴趣社交在2019年仍然保持强劲的动力，占到近70%的比例，它们仍然是资本市场主要关注领域。从增长率来看陌生人社交的增长速度远远大于其他几类，因此我们要从这个方向入手

### 1.3、功能概述

#### 1.3.1 用户登录

业务说明：

用户通过手机验证码进行登录，如果是第一次登录则需要完善个人信息，在上传图片时，需要对上传的图片做人像的校验，防止用户上传非人像的图片作为头像。流程完成后，则登录成功。

![1563681330146](1563681330146.png)

![1563681348382](1563681348382.png)

![1563681365123](1563681365123.png)

![1563681382592](1563681382592.png)

![1563681397466](1563681397466.png)

![1563681412881](1563681412881.png)

#### 1.3.2、交友

交友是探花项目的核心功能之一，用户可以查看好友，添加好友，搜索好友等操作。

![1563698504256](1563698504256.png)

##### 首页

在首页中，主要功能有“今日佳人”、“推荐”、“最近访客”等

- 今日佳人
    - 按照“缘分值”进行匹配，将“缘分值”最高的用户展现出来
- 推荐
    - 按照“缘分值”进行推荐，由后台的推荐系统计算得出，展现出来
- 最近访客
    - 显示最近来看“我”的用户

##### 探花

![1563714212568](1563714212568.png)

> 说明：左划喜欢，右划不喜欢，每天限量不超过100个，开通会员可增加限额。双方互相喜欢则配对成功。
>
> 实现：数据来源推荐系统计算后的结果。

##### 搜附近

![1563714826374](1563714826374.png)

根据用户当前所在的位置进行查询，并且在10km的范围内进行查询，可以通过筛选按钮进行条件筛选。

##### 桃花传音

功能类似QQ中的漂流瓶，用户可以发送和接收语音消息，陌生人就会接收到消息。

![1563718868686](1563718868686.png)

##### 测灵魂

1. 测试题用于对用户进行分类，每次提交答案后更新用户属性
2. 测试题在后台进行维护
3. 测试题测试完后产生结果页可以进行分享

4. 测试题为顺序回答，回答完初级题解锁下一级问题

5. 点击锁定问题 显示提示 请先回答上一级问题

![1563719052277](1563719052277.png)

![1563719092059](1563719092059.png)

![1563719100855](1563719100855.png)

#### 1.3.3、圈子

1、推荐频道为根据问卷及喜好推荐相似用户动态

2、显示内容为用户头像、用户昵称、用户性别、用户年龄、用户标签和用户发布动态

3、图片最多不超过6张或发布一个小视频

4、动态下方显示发布时间距离当时时间，例如10分钟前、3小时前、2天前，显示时间进行取整

5、动态下方显示距离为发布动态地与本地距离

6、显示用户浏览量

7、显示点赞数、评论数 转发数

![1563719380223](1563719380223.png)

![1563719403171](1563719403171.png)

#### 1.3.4、消息

消息包含通知类的消息和好友消息。

![1563719621939](1563719621939.png)

#### 1.3.5、小视频

用户可以上传小视频，也可以查看小视频列表，并且可以进行点赞操作。

![1563719761162](1563719761162.png)

#### 1.3.6、我的

显示关注数、喜欢数、粉丝数、我的动态等信息。

![1563719894481](1563719894481.png)

![1563719949700](1563719949700.png)



。

### 1.4、技术方案

前端：

- flutter + android + 环信SDK + redux + shared_preferences + connectivity + iconfont + webview + sqflite

后端：

- Spring Boot + SpringMVC + Mybatis + MybatisPlus + Dubbo
- Elasticsearch geo 实现地理位置查询
- MongoDB 实现海量数据的存储
- Redis 数据的缓存
- Spark + MLlib 实现智能推荐
- 第三方服务 环信即时通讯
- 第三方服务 阿里云 OSS 、 短信服务
- 第三方服务 虹软开放平台 / 阿里云

![1563457093887](1563457093887.png)

### 1.5、技术解决方案

- 使用Elasticsearch geo实现附近的人的解决方案
- 使用Spark + Mllib实现智能推荐的解决方案
- 使用MongoDB进行海量数据的存储的解决方案
- 使用采用分布式文件系统存储小视频数据的解决方案
- 使用百度人脸识别的解决方案
- 使用阿里云进行短信验证码发送的解决方案

## 2、前后端分离

### 2.1、前后端分离的概述

项目基于前后端分离的架构进行开发，前后端分离架构总体上包括前端和服务端，通常是多人协作开发

* 前后端分离开发基于**HTTP+JSON**交互

* 通过接口文档（API文档）定义规范

* 前后端按照文档定义请求及响应数据

![image-20210714095914770](image-20210714095914770.png)

### 2.2、YAPI介绍

> YAPI已经在linux虚拟机中准备好了
>
> 请求地址：http://192.168.136.160:3000/
>
> 用户名/密码：tanhua@itcast.cn/123456

对于接口的定义我们采用YApi进行管理，YApi是一个开源的接口定义、管理、提供mock数据的管理平台。

![image-20201017100705286](image-20201017100705286-1626228296625.png)

接口定义：

![image-20201017100848313](image-20201017100848313-1626228296625.png)

mock数据，YApi提供了mock功能，就是模拟服务端返回测试数据：

![image-20201017101228582](image-20201017101228582-1626228296625.png)

![image-20201017101252482](image-20201017101252482-1626228296625.png)

还可以运行http请求（需要在Chrome中安装支持跨域扩展 https://juejin.im/post/6844904057707085832）：

![image-20201017103028622](image-20201017103028622-1626228296626.png)

![image-20201017103045864](image-20201017103045864-1626228296626.png)

## 3、开发工具

探花交友项目的开发统一使用提供的Centos7环境，该环境中部署安装了项目所需要的各种服务，如：RabbitMQ,MongoDB、Redis等。

- 虚拟机的root用户密码为：<font color=red>root123</font>
- 默认参数：CPU：2核，内存：4G，硬盘：60G
- IP地址建议设置为192.168.136.160，否则有些服务将不可用，比如：Redis、RocketMQ等。

### 3.1、虚拟机配置

由于课程中使用了较多的软件，且之间会有联系，推荐同学IP地址设置为192.168.136.160

![image-20210714100818029](image-20210714100818029.png)

仅仅需要修改虚拟机中的子网IP即可。

### 3.2、Android模拟器

客户端由前端团队进行开发，前端提供apk进行对接，所以，需要我们安装安卓的模拟器进行测试。

目前对开发者有很多专业的模拟器如genymotion，但是这些模拟器功能强大，空间占用率高并不适用于教学，甚至在某些环境下不能正常的启动。所以可以选择国内的安卓模拟器产品，比如：网易、夜神等，在这里我们推荐使用网易模拟器，其兼容性好、功能完善而且还简洁，但是它不支持虚拟机中安装。

下载：https://mumu.163.com/

![image-20201016214917500](image-20201016214917500-1626229234043.png)

### 3.3、调试工具PostMan

Postman是一款功能强大的网页调试与发送网页HTTP请求的Chrome插件。postman被500万开发者和超100,000家公司用于每月访问1.3亿个API。

官方网址：https://www.postman.com/

解压资料文件夹中的软件，安装即可

![image-20210714102512760](image-20210714102512760.png)

## 4、环境搭建

### 4.1、MYSQL数据库

数据库设计规范：详见资料文件夹下[《](../资料/黑马头条-数据库规范设计说明书.md)[探花交友](../资料/黑马头条-数据库规范设计说明书.md)[-](../资料/黑马头条-数据库规范设计说明书.md)[mysq](../资料/黑马头条-数据库规范设计说明书.md)[表](../资料/黑马头条-数据库规范设计说明书.md)[.md》](../资料/黑马头条-数据库规范设计说明书.md)文件

| 数据库表        | 说明       |
| --------------- | ---------- |
| tb_user         | 用户表     |
| tb_user_info    | 用户详情表 |
| tb_settings     | 用户设置表 |
| tb_question     | 好友问题表 |
| tb_black_list   | 黑名单     |
| tb_announcement | 公告表     |

将资料中数据库表导入到MYSQL中

#### 4.1.1、导入数据库

（1） 打开Navicat ，点击右键选择新建数据库，**名字跟我们要导入的数据库的名字一样**，字符集一般选utf-8

![image-20210714114346530](image-20210714114346530.png)

（2） 在新建的数据库上右击，选择“运行SQL文件”，在提示框中选择文件所在的路径，编码保持一致选择utf-8

![image-20210714114414990](image-20210714114414990.png)

（3） 提示Successfully 导入成功后，可能在左侧看不到导入的数据库，关闭Navicat，重新打开即可看到

### 4.2、基础服务组件

探花交友学习中，除MySQL数据库部署到本地电脑中。其他涉及到的所有组件都已经以docker形式安装到虚拟机中。我们只需要进入虚拟机，使用简单的命令即可。为了方便学习与减少基础服务占用的学习时间，全部使用docker-compose的方式集中式部署。这些文件在linux虚拟机中的/root/docker-file文件夹下

![image-20210714102740424](image-20210714102740424.png)

每个文件夹中都包含一个docker-compose.yml配置文件，一键启动并部署应用。

```shell
#进入组件目录
cd /root/docker-file/base/
#执行docker-compose命令
docker-compose up -d 
```

**base**

* 其中包含redis，nacos，yapi，mongo

**fastdfs**

* 包含fastdfs操作需要的组件

**rmq**

* 包含RabbitMQ需要所有组件

**recommend**

* 包含推荐系统需要所有组件

### 4.3、IDEA配置

项目依赖环境（需提前安装好）

* JDK1.8

* Intellij Idea

* maven-3.x以上

* Git

* UTF-8编码格式

#### 设置项目编码格式

![image-20210714102921973](image-20210714102921973.png)

#### 设置Maven仓库

设置本地仓库，建议使用资料中提供好的仓库

![image-20210714102941712](image-20210714102941712.png)

### 4.4、Maven模块分析

整体项目使用Maven架构搭建，采用聚合工程形式管理模块，为了便于调用，dubbo需要拆分为接口模块和服务模块

![image-20210714103025777](image-20210714103025777.png)

**工程主体结构**

| **父工程**   | **工程名称**           | **说明**                                       |
| ------------ | ---------------------- | ---------------------------------------------- |
| tanhua       | tanhua-autoconfig      | 自动装配的工具类                               |
| tanhua       | tanhua-domain          | 实体类模块                                     |
| tanhua       | tanhua-dubbo           | Dubbo子模块（可以理解为文件夹，管理dubbo模块） |
| tanhua       | tanhua-app             | 与手机端交互的入口模块                         |
| tanhua-dubbo | tanhua-dubbo-interface | Dubbo接口模块                                  |
| tanhua-dubbo | tanhua-dubbo-db        | Dubbo服务模块（数据库部分）                    |
| tanhua-dubbo | tanhua-dubbo-mongo     | Dubbo服务模块（MongoDB部分）                   |

**模块依赖分析**

![image-20210714103104326](image-20210714103104326.png)

### 4.5、模块依赖

#### tanhua

```xml
<properties>
    <maven.compiler.source>8</maven.compiler.source>
    <maven.compiler.target>8</maven.compiler.target>
    <mysql.version>5.1.47</mysql.version>
    <jackson.version>2.11.0</jackson.version>
    <druid.version>1.0.9</druid.version>
    <servlet-api.version>2.5</servlet-api.version>
    <jsp-api.version>2.0</jsp-api.version>
    <joda-time.version>2.5</joda-time.version>
    <commons-lang3.version>3.3.2</commons-lang3.version>
    <commons-io.version>1.3.2</commons-io.version>
    <mybatis.version>3.5.6</mybatis.version>
    <mybatis.mybatis-plus>3.4.1</mybatis.mybatis-plus>
    <lombok.version>1.18.8</lombok.version>
    <mongo.version>4.0.5</mongo.version>
    <spring-cloud.version>Hoxton.SR10</spring-cloud.version>
    <spring-cloud-alibaba.version>2.2.5.RELEASE</spring-cloud-alibaba.version>
</properties>

<!--通用依赖-->
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.12</version>
        <scope>test</scope>
    </dependency>
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
    </dependency>
    <dependency>
        <groupId>cn.hutool</groupId>
        <artifactId>hutool-all</artifactId>
        <version>5.4.3</version>
    </dependency>
    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>fastjson</artifactId>
        <version>1.2.8</version>
    </dependency>
</dependencies>

<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>io.netty</groupId>
            <artifactId>netty-bom</artifactId>
            <version>4.1.59.Final</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>

        <dependency>
            <groupId>io.projectreactor</groupId>
            <artifactId>reactor-bom</artifactId>
            <version>2020.0.4</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>

        <dependency>
            <groupId>io.projectreactor.netty</groupId>
            <artifactId>reactor-netty</artifactId>
            <version>0.9.8.RELEASE</version>
        </dependency>

        <dependency>
            <groupId>org.springframework.cloud</groupId>
            <artifactId>spring-cloud-dependencies</artifactId>
            <version>${spring-cloud.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>

        <dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-alibaba-dependencies</artifactId>
            <version>${spring-cloud-alibaba.version}</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>

        <dependency>
            <groupId>joda-time</groupId>
            <artifactId>joda-time</artifactId>
            <version>${joda-time.version}</version>
        </dependency>

        <!-- mybatis-plus插件依赖 -->
        <dependency>
            <groupId>com.baomidou</groupId>
            <artifactId>mybatis-plus</artifactId>
            <version>${mybatis.mybatis-plus}</version>
        </dependency>

        <!-- MySql -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>${mysql.version}</version>
        </dependency>

        <dependency>
            <groupId>org.mongodb</groupId>
            <artifactId>mongodb-driver-sync</artifactId>
            <version>${mongodb.version}</version>
        </dependency>

        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
            <version>${lombok.version}</version>
        </dependency>

        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-lang3</artifactId>
            <version>${commons-lang3.version}</version>
        </dependency>

        <dependency>
            <groupId>org.apache.commons</groupId>
            <artifactId>commons-lang3</artifactId>
            <version>3.7</version>
        </dependency>
        <!-- Jackson Json处理工具包 -->
        <dependency>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-databind</artifactId>
            <version>${jackson.version}</version>
        </dependency>
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid</artifactId>
            <version>${druid.version}</version>
        </dependency>
        <dependency>
            <groupId>commons-codec</groupId>
            <artifactId>commons-codec</artifactId>
            <version>1.11</version>
        </dependency>
    </dependencies>
</dependencyManagement>

<build>
    <plugins>
        <!-- java编译插件 -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.2</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
                <encoding>UTF-8</encoding>
            </configuration>
        </plugin>
    </plugins>
</build>
```

#### tanhua-app-server

```xml
<dependencies>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <!--SpringDataRedis依赖-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-redis</artifactId>
    </dependency>

    <!--lombok依赖-->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
    </dependency>

    <!--工具包-->
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
    </dependency>
    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
    </dependency>
    <dependency>
        <groupId>commons-codec</groupId>
        <artifactId>commons-codec</artifactId>
    </dependency>
    <dependency>
        <groupId>joda-time</groupId>
        <artifactId>joda-time</artifactId>
    </dependency>

    <!--jwt依赖-->
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt</artifactId>
        <version>0.9.1</version>
    </dependency>

    <!--fastdfs文件存储-->
    <dependency>
        <groupId>com.github.tobato</groupId>
        <artifactId>fastdfs-client</artifactId>
        <version>1.26.7</version>
        <exclusions>
            <exclusion>
                <groupId>ch.qos.logback</groupId>
                <artifactId>logback-classic</artifactId>
            </exclusion>
        </exclusions>
    </dependency>


    <!-- Dubbo Spring Cloud Starter-->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-dubbo</artifactId>
    </dependency>

    <!-- Spring Cloud Nacos Service Discovery-->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
    </dependency>

    <!-- nacos配置中心依赖支持
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
    </dependency>
	-->
    <!--RabbitMQ
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-amqp</artifactId>
    </dependency>
	-->
    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-dubbo-interface</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-commons</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-autoconfig</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>

<build>
    <finalName>tanhua-app-server</finalName>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <version>2.3.9.RELEASE</version>
        </plugin>
    </plugins>
</build>
```

#### tanhua-autoconfig

```xml
<dependencies>
    <!--阿里云核心API-->
    <dependency>
        <groupId>com.aliyun</groupId>
        <artifactId>aliyun-java-sdk-core</artifactId>
        <version>4.5.3</version>
    </dependency>
    <dependency>
        <groupId>com.aliyun</groupId>
        <artifactId>dysmsapi20170525</artifactId>
        <version>2.0.1</version>
    </dependency>
    <!--阿里云oss存储API-->
    <dependency>
        <groupId>com.aliyun.oss</groupId>
        <artifactId>aliyun-sdk-oss</artifactId>
        <version>3.10.2</version>
    </dependency>
    <!--阿里云人识别-->
    <dependency>
        <groupId>com.aliyun</groupId>
        <artifactId>facebody20191230</artifactId>
        <version>1.0.10</version>
    </dependency>
    <!--百度人脸识别API-->
    <dependency>
        <groupId>com.baidu.aip</groupId>
        <artifactId>java-sdk</artifactId>
        <version>4.8.0</version>
    </dependency>
    <!--springboot基础起步依赖-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>com.easemob.im</groupId>
        <artifactId>im-sdk-core</artifactId>
        <version>0.2.5</version>
    </dependency>
    <dependency>
        <groupId>com.aliyun</groupId>
        <artifactId>aliyun-java-sdk-green</artifactId>
        <version>3.6.1</version>
    </dependency>
</dependencies>
```

#### tanhua-commons

```xml
<dependencies>
    <!--工具包-->
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
    </dependency>
    <dependency>
        <groupId>commons-codec</groupId>
        <artifactId>commons-codec</artifactId>
    </dependency>
    <dependency>
        <groupId>joda-time</groupId>
        <artifactId>joda-time</artifactId>
    </dependency>
    <!--jwt依赖-->
    <dependency>
        <groupId>io.jsonwebtoken</groupId>
        <artifactId>jjwt</artifactId>
        <version>0.9.1</version>
    </dependency>
</dependencies>
```

#### tanhua-dubbo-db

```xml
<dependencies>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <dependency>
        <groupId>com.baomidou</groupId>
        <artifactId>mybatis-plus</artifactId>
    </dependency>

    <dependency>
        <groupId>com.baomidou</groupId>
        <artifactId>mybatis-plus-boot-starter</artifactId>
        <version>${mybatis.mybatis-plus}</version>
    </dependency>

    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
    </dependency>

    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>druid</artifactId>
    </dependency>

    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
    </dependency>

    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
    </dependency>

    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
    </dependency>

    <dependency>
        <groupId>commons-codec</groupId>
        <artifactId>commons-codec</artifactId>
    </dependency>

    <dependency>
        <groupId>joda-time</groupId>
        <artifactId>joda-time</artifactId>
    </dependency>

    <!-- Dubbo Spring Cloud Starter -->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-dubbo</artifactId>
    </dependency>

    <!-- Spring Cloud Nacos Service Discovery -->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
    </dependency>

    <!-- nacos配置中心依赖支持
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
    </dependency>
	-->
    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-dubbo-interface</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>

<build>
    <finalName>tanhua-dubbo-db</finalName>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <version>2.3.9.RELEASE</version>
        </plugin>
    </plugins>
</build>
```

#### tanhua-dubbo-interface

```xml
<dependencies>
    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-model</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>
```

#### tanhua-dubbo-mongo

```xml
<dependencies>

    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>

    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
    </dependency>

    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
    </dependency>

    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
    </dependency>

    <dependency>
        <groupId>commons-codec</groupId>
        <artifactId>commons-codec</artifactId>
    </dependency>

    <dependency>
        <groupId>joda-time</groupId>
        <artifactId>joda-time</artifactId>
    </dependency>

    <!-- Dubbo Spring Cloud Starter -->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-dubbo</artifactId>
    </dependency>

    <!-- Spring Cloud Nacos Service Discovery -->
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
    </dependency>

    <!-- nacos配置中心依赖支持
    <dependency>
        <groupId>com.alibaba.cloud</groupId>
        <artifactId>spring-cloud-starter-alibaba-nacos-config</artifactId>
    </dependency>
	-->
    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-commons</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>

    <dependency>
        <groupId>com.itheima</groupId>
        <artifactId>tanhua-dubbo-interface</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
</dependencies>

<build>
    <finalName>tanhua-dubbo-db</finalName>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
            <version>2.3.9.RELEASE</version>
        </plugin>
    </plugins>
</build>
```

#### tanhua-model

```xml
<dependencies>
    <!--SpringDataMongo起步依赖
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-mongodb</artifactId>
    </dependency>
    <dependency>
        <groupId>org.mongodb</groupId>
        <artifactId>mongodb-driver-sync</artifactId>
        <version>${mongodb.version}</version>
    </dependency>
	-->
    <!--MybatisPlus起步依赖-->
    <dependency>
        <groupId>com.baomidou</groupId>
        <artifactId>mybatis-plus</artifactId>
    </dependency>
</dependencies>
```

### 4.6、搭建环境

tanhua-app-server端添加引导类和配置文件application.yml

```java
//启动类
@SpringBootApplication
public class AppServerApplication {

    public static void main(String[] args) {
        SpringApplication.run(AppServerApplication.class,args);
    }
}
```

### 4.7、Lombok

lombok 提供了简单的注解的形式来帮助我们简化消除一些必须有但显得很臃肿的 java 代码，尤其是针对pojo。

官网：https://projectlombok.org/

#### 配置安装

导入依赖：

~~~xml
<!--简化代码的工具包-->
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <optional>true</optional>
</dependency>
~~~

安装IDEA插件： ![1542036205393](1542036205393.png)

> 如果不安装插件，程序可以正常执行，但是看不到生成的一些代码，如：get、set方法。

#### 常用注解

- @Data：注解在类上；提供类所有属性的 getting 和 setting 方法，此外还提供了equals、canEqual、hashCode、toString 方法
- @Setter：注解在属性上；为属性提供 setting 方法
- @Getter：注解在属性上；为属性提供 getting 方法
- @Slf4j：注解在类上；为类提供一个 属性名为log 的 slf4j日志对象
- @NoArgsConstructor：注解在类上；为类提供一个无参的构造方法
- @AllArgsConstructor：注解在类上；为类提供一个全参的构造方法
- @Builder：使用Builder模式构建对象

> 测试一：使用@Data注解

![image-20201116113610810](image-20201116113610810.png)

是不是很神奇？！

> 测试二：使用@Slf4j注解

![image-20201116113645107](image-20201116113645107.png)

测试：

![image-20201116113812602](image-20201116113812602.png)

> 测试三：@AllArgsConstructor、@NoArgsConstructor注解的使用

![image-20201116114013519](image-20201116114013519.png)

> 测试四：@Builder

![image-20201116114233416](image-20201116114233416.png)

测试结果：

![image-20201116114254202](image-20201116114254202.png)

## 5、注册登录需求分析

### 5.1、业务说明

用户通过手机验证码进行登录，如果是第一次登录则需要完善个人信息，在上传图片时，需要对上传的图片做人像的校验，防止用户上传非人像的图片作为头像。流程完成后，则登录成功。

* 已注册用户：
    * 输入手机号发送验证码
    * 输入验证码，进行比对完成登录
* 未注册用户：
    * 输入手机号发送验证码
    * 输入验证码，进行比对，自动注册（保存用户）
    * 完善用户信息

### 5.2、需求分析

服务端接受客户端请求

Java代码调用第三方服务实现短信返送（发送短信需要运营资质，只能借助第三方实现）

![image-20210714114654518](image-20210714114654518.png)

### 5.3、数据库表

数据库使用的mysql：

~~~sql
CREATE TABLE `tb_user` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `mobile` varchar(11) DEFAULT NULL COMMENT '手机号',
  `password` varchar(32) DEFAULT NULL COMMENT '密码，需要加密',
  `created` datetime DEFAULT NULL,
  `updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `mobile` (`mobile`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=utf8 COMMENT='用户表';

CREATE TABLE `tb_user_info` (
  `id` bigint(20) NOT NULL AUTO_INCREMENT,
  `user_id` bigint(20) NOT NULL COMMENT '用户id',
  `nick_name` varchar(50) DEFAULT NULL COMMENT '昵称',
  `logo` varchar(100) DEFAULT NULL COMMENT '用户头像',
  `tags` varchar(50) DEFAULT NULL COMMENT '用户标签：多个用逗号分隔',
  `sex` int(1) DEFAULT '3' COMMENT '性别，1-男，2-女，3-未知',
  `age` int(11) DEFAULT NULL COMMENT '用户年龄',
  `edu` varchar(20) DEFAULT NULL COMMENT '学历',
  `city` varchar(20) DEFAULT NULL COMMENT '居住城市',
  `birthday` varchar(20) DEFAULT NULL COMMENT '生日',
  `cover_pic` varchar(50) DEFAULT NULL COMMENT '封面图片',
  `industry` varchar(20) DEFAULT NULL COMMENT '行业',
  `income` varchar(20) DEFAULT NULL COMMENT '收入',
  `marriage` varchar(20) DEFAULT NULL COMMENT '婚姻状态',
  `created` datetime DEFAULT NULL,
  `updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `user_id` (`user_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='用户信息表';

~~~

### 5.4、实体类

**User**

```java
@Data
@AllArgsConstructor  //满参构造方法
@NoArgsConstructor   //无参构造方法
public class User extends BasePojo {

    private Long id;
    private String mobile;
    private String password;

    //环信用户信息
    private String hxUser;
    private String hxPassword;
}
```

## 6、短信验证码

### 6.1、阿里云短信服务

![image-20210714114820624](image-20210714114820624.png)

官方网站：https://www.aliyun.com/product/sms?spm=5176.19720258.J_8058803260.611.48192c4abPvXEp

#### 6.1.1、申请签名与模板

使用阿里云短信服务非常简单，仅需要简单的申请和认证即可

https://dysms.console.aliyun.com/dysms.htm?spm=5176.12818093.0.ddysms.2a4316d0ql6PyD

![image-20201016193819097](image-20201016193819097.png)

> 说明：申请签名时，个人用户只能申请一个并且签名的名称必须为“ABC商城”，否则审核不通过。

申请模板：

![image-20201016193927924](image-20201016193927924.png)

> 审核时间需要1~2小时，请耐心等待~

#### 6.1.2、示例代码

文档：https://help.aliyun.com/document_detail/101414.html?spm=a2c4g.11186623.6.625.18705ffa8u4lwj：

导入依赖：

~~~xml
<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>dysmsapi20170525</artifactId>
    <version>2.0.1</version>
</dependency>
~~~

~~~java
package com.tanhua.sso.service;

import com.aliyun.dysmsapi20170525.models.SendSmsRequest;
import com.aliyun.dysmsapi20170525.models.SendSmsResponse;
import com.aliyun.dysmsapi20170525.models.SendSmsResponseBody;
import com.aliyun.teaopenapi.models.Config;

public class SendSms {

    /**
     * 使用AK&SK初始化账号Client
     * @param accessKeyId
     * @param accessKeySecret
     * @return Client
     * @throws Exception
     */
    public static com.aliyun.dysmsapi20170525.Client createClient(String accessKeyId, String accessKeySecret) throws Exception {
        Config config = new Config()
                // 您的AccessKey ID
                .setAccessKeyId(accessKeyId)
                // 您的AccessKey Secret
                .setAccessKeySecret(accessKeySecret)
                .setEndpoint("dysmsapi.aliyuncs.com");
        // 访问的域名
        return new com.aliyun.dysmsapi20170525.Client(config);
    }

    public static void main(String[] args_) throws Exception {
        java.util.List<String> args = java.util.Arrays.asList(args_);
        com.aliyun.dysmsapi20170525.Client client = SendSms
                .createClient("**********", "**********");

        SendSmsRequest sendSmsRequest = new SendSmsRequest()
                .setPhoneNumbers( "158****7944") //目标手机号
                .setSignName("ABC商城") //签名名称
                .setTemplateCode("SMS_204756062") //短信模板code
                .setTemplateParam("{\"code\":\"1111\"}"); //模板中变量替换
        SendSmsResponse sendSmsResponse = client.sendSms(sendSmsRequest);

        SendSmsResponseBody body = sendSmsResponse.getBody();

        // code = OK 代表成功
        System.out.println(body.getCode() + "  " + body.getMessage());
    }

}
~~~

##### 3.6.1.4、实现发送短信方法

配置文件：aliyun.properties

~~~properties
aliyun.sms.accessKeyId = ***********
aliyun.sms.accessKeySecret = ***********
aliyun.sms.domain= dysmsapi.aliyuncs.com
aliyun.sms.signName= ABC商城
aliyun.sms.templateCode= SMS_204756062
~~~

需要注意中文编码问题：

![image-20201016203847636](image-20201016203847636.png)

读取配置：

~~~java
package com.tanhua.sso.config;

import lombok.Data;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.PropertySource;

@Configuration
@PropertySource("classpath:aliyun.properties")
@ConfigurationProperties(prefix = "aliyun.sms")
@Data
public class AliyunSMSConfig {

    private String accessKeyId;
    private String accessKeySecret;
    private String domain;
    private String signName;
    private String templateCode;

}
~~~

代码实现：

~~~java
package com.tanhua.sso.service;

import cn.hutool.core.util.RandomUtil;
import cn.hutool.core.util.StrUtil;
import com.aliyun.dysmsapi20170525.Client;
import com.aliyun.dysmsapi20170525.models.SendSmsRequest;
import com.aliyun.dysmsapi20170525.models.SendSmsResponse;
import com.aliyun.dysmsapi20170525.models.SendSmsResponseBody;
import com.aliyun.teaopenapi.models.Config;
import com.tanhua.sso.config.AliyunSMSConfig;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
@Slf4j
public class SmsService {

    @Autowired
    private AliyunSMSConfig aliyunSMSConfig;

    /**
     * 发送短信验证码
     *
     * @param mobile
     * @return
     */
    public String sendSms(String mobile) {
        //随机生成6位数字验证码
        String code = RandomUtil.randomNumbers(6);
        try {
            Config config = new Config()
                    .setAccessKeyId(this.aliyunSMSConfig.getAccessKeyId())
                    .setAccessKeySecret(this.aliyunSMSConfig.getAccessKeySecret())
                    .setEndpoint(this.aliyunSMSConfig.getDomain());

            Client client = new Client(config);
            SendSmsRequest sendSmsRequest = new SendSmsRequest()
                    .setPhoneNumbers(mobile)//目标手机号
                    .setSignName(this.aliyunSMSConfig.getSignName()) //签名名称
                    .setTemplateCode(this.aliyunSMSConfig.getTemplateCode()) //短信模板code
                    .setTemplateParam("{\"code\":\"" + code + "\"}"); //模板中变量替换
            SendSmsResponse sendSmsResponse = client.sendSms(sendSmsRequest);
            SendSmsResponseBody body = sendSmsResponse.getBody();
            if (StrUtil.equals("OK", body.getCode())) {
                return code;
            }
        } catch (Exception e) {
            log.error("发送短信验证码失败！" + mobile, e);
        }
        return null;
    }
}

~~~

### 6.2、模板组件

企业开发中，往往将常见工具类封装抽取，以简洁便利的方式供其他工程模块使用。而SpringBoot的自动装配机制可以方便的实现组件抽取。SpringBoot执行流程如下

1. 扫描依赖模块中META-INF/spring.factories
2. 执行装配类中方法
3. 对象存入容器中
4. 核心工程注入对象，调用方法使用

#### 6.2.1、配置类

tanhua-autoconfig创建配置信息类

```java
@Data
@ConfigurationProperties(prefix = "tanhua.sms")
public class SmsProperties {
    private String signName;
    private String templateCode;
    private String accessKey;
    private String secret;
}
```

#### 6.2.2、发送短信模板对象

tanhua-autoconfig创建模板对象对象发送信息

```java
package com.tanhua.autoconfig.template;

import com.aliyun.dysmsapi20170525.models.SendSmsRequest;
import com.aliyun.dysmsapi20170525.models.SendSmsResponse;
import com.aliyun.dysmsapi20170525.models.SendSmsResponseBody;
import com.aliyun.teaopenapi.models.Config;
import com.tanhua.autoconfig.properties.SmsProperties;

public class SmsTemplate {

    private SmsProperties properties;

    public SmsTemplate(SmsProperties properties) {
        this.properties = properties;
    }

    public void sendSms(String mobile,String code) {

        try {
            //配置阿里云
            Config config = new Config()
                    // 您的AccessKey ID
                    .setAccessKeyId(properties.getAccessKey())
                    // 您的AccessKey Secret
                    .setAccessKeySecret(properties.getSecret());
            // 访问的域名
            config.endpoint = "dysmsapi.aliyuncs.com";

            com.aliyun.dysmsapi20170525.Client client =  new com.aliyun.dysmsapi20170525.Client(config);

            SendSmsRequest sendSmsRequest = new SendSmsRequest()
                    .setPhoneNumbers(mobile)
                    .setSignName(properties.getSignName())
                    .setTemplateCode(properties.getTemplateCode())
                    .setTemplateParam("{\"code\":\""+code+"\"}");
            // 复制代码运行请自行打印 API 的返回值
            SendSmsResponse response = client.sendSms(sendSmsRequest);

            SendSmsResponseBody body = response.getBody();

            System.out.println(body.getMessage());

        }catch (Exception e) {
            e.printStackTrace();
        }

    }

}
```

#### 6.2.3、自动装配类

tanhua-autoconfig创建自动装配的配置类

```java
package com.tanhua.autoconfig;


import com.tanhua.autoconfig.properties.*;
import com.tanhua.autoconfig.template.*;
import org.springframework.boot.autoconfigure.condition.ConditionalOnProperty;
import org.springframework.boot.context.properties.EnableConfigurationProperties;
import org.springframework.context.annotation.Bean;

@EnableConfigurationProperties({
        SmsProperties.class
})
public class TanhuaAutoConfiguration {

    @Bean
    public SmsTemplate smsTemplate(SmsProperties properties) {
        return new SmsTemplate(properties);
    }
}
```

#### 6.2.4、自动装配配置

根据自动装配原则，在tanhua-autoconfig工程创建 /META-INF/spring.factories文件

```properties
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
com.tanhua.autoconfig.TanhuaAutoConfiguration
```

#### 6.2.5、测试

tanhua-app-server工程加入短信配置

```yaml
tanhua:
  sms:
    signName: 物流云商
    templateCode: SMS_106590012
    accessKey: LTAI4GKgob9vZ53k2SZdyAC7
    secret: LHLBvXmILRoyw0niRSBuXBZewQ30la
```

编写单元测试类

```java
@RunWith(SpringRunner.class)
@SpringBootTest(classes = AppServerApplication.class)
public class SmsTemplateTest {

    //注入
    @Autowired
    private SmsTemplate smsTemplate;

    //测试
    @Test
    public void testSendSms() {
        smsTemplate.sendSms("18618412321","4567");
    }
}
```

#### 3.6.2、SSO短信接口服务

##### 3.6.2.1、mock接口

地址：https://mock-java.itheima.net/project/35/interface/api/581

![1564535110994](1564535110994.png)

##### 3.6.2.2、编写接口服务

编写ErrorResult，ErrorResult对象是与前端约定好的结构，如果发生错误需要返回该对象，如果未发生错误响应200即可。

~~~java
package com.tanhua.sso.vo;

import lombok.Builder;
import lombok.Data;

@Data
@Builder
public class ErrorResult {

    private String errCode;
    private String errMessage;
}

~~~

SmsController：

~~~java
package com.tanhua.sso.controller;

import com.tanhua.sso.service.SmsService;
import com.tanhua.sso.vo.ErrorResult;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.Map;

@RestController
@RequestMapping("user")
@Slf4j
public class SmsController {

    @Autowired
    private SmsService smsService;

    /**
     * 发送短信验证码接口
     *
     * @param param
     * @return
     */
    @PostMapping("login")
    public ResponseEntity<ErrorResult> sendCheckCode(@RequestBody Map<String, String> param) {
        ErrorResult errorResult = null;
        String phone = param.get("phone");
        try {
            errorResult = this.smsService.sendCheckCode(phone);
            if (null == errorResult) {
                return ResponseEntity.ok(null);
            }
        } catch (Exception e) {
            log.error("发送短信验证码失败~ phone = " + phone, e);
            errorResult = ErrorResult.builder().errCode("000002").errMessage("短信验证码发送失败！").build();
        }
        return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(errorResult);
    }

}

~~~

SmsService：

~~~java
package com.tanhua.sso.service;

import cn.hutool.core.util.RandomUtil;
import cn.hutool.core.util.StrUtil;
import com.aliyun.dysmsapi20170525.Client;
import com.aliyun.dysmsapi20170525.models.SendSmsRequest;
import com.aliyun.dysmsapi20170525.models.SendSmsResponse;
import com.aliyun.dysmsapi20170525.models.SendSmsResponseBody;
import com.aliyun.teaopenapi.models.Config;
import com.tanhua.sso.config.AliyunSMSConfig;
import com.tanhua.sso.vo.ErrorResult;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.data.redis.core.RedisTemplate;
import org.springframework.stereotype.Service;

import java.time.Duration;

@Service
@Slf4j
public class SmsService {

    @Autowired
    private AliyunSMSConfig aliyunSMSConfig;

    @Autowired
    private RedisTemplate<String, String> redisTemplate;

    /**
     * 发送短信验证码
     *
     * @param mobile
     * @return
     */
    public String sendSms(String mobile) {
        //随机生成6位数字验证码
        String code = RandomUtil.randomNumbers(6);
        try {
            Config config = new Config()
                    .setAccessKeyId(this.aliyunSMSConfig.getAccessKeyId())
                    .setAccessKeySecret(this.aliyunSMSConfig.getAccessKeySecret())
                    .setEndpoint(this.aliyunSMSConfig.getDomain());

            Client client = new Client(config);
            SendSmsRequest sendSmsRequest = new SendSmsRequest()
                    .setPhoneNumbers(mobile)//目标手机号
                    .setSignName(this.aliyunSMSConfig.getSignName()) //签名名称
                    .setTemplateCode(this.aliyunSMSConfig.getTemplateCode()) //短信模板code
                    .setTemplateParam("{\"code\":\"" + code + "\"}"); //模板中变量替换
            SendSmsResponse sendSmsResponse = client.sendSms(sendSmsRequest);
            SendSmsResponseBody body = sendSmsResponse.getBody();
            if (StrUtil.equals("OK", body.getCode())) {
                return code;
            }
        } catch (Exception e) {
            log.error("发送短信验证码失败！" + mobile, e);
        }
        return null;
    }

    /**
     * 发送短信验证码
     * 实现：发送完成短信验证码后，需要将验证码保存到redis中
     * @param phone
     * @return
     */
    public ErrorResult sendCheckCode(String phone) {
        String redisKey = "CHECK_CODE_" + phone;

        //先判断该手机号发送的验证码是否还未失效
        if(this.redisTemplate.hasKey(redisKey)){
            String msg = "上一次发送的验证码还未失效！";
            return ErrorResult.builder().errCode("000001").errMessage(msg).build();
        }

        String code = this.sendSms(phone);
        if(StrUtil.isEmpty(code)){
            String msg = "发送短信验证码失败！";
            return ErrorResult.builder().errCode("000000").errMessage(msg).build();
        }

        //短信发送成功，将验证码保存到redis中，有效期为5分钟
        this.redisTemplate.opsForValue().set(redisKey, code, Duration.ofMinutes(5));

        return null;
    }
}

~~~

## 7、用户登录

### 7.1、登录验证码

![image-20210714115937330](image-20210714115937330.png)

#### 7.1.1、接口说明

![image-20210714120045422](image-20210714120045422.png)

参见YAPI接口地址：http://192.168.136.160:3000/project/19/interface/api/94

#### 7.1.2、流程分析

![image-20210714120354128](image-20210714120354128.png)

客户端发送请求

服务端调用第三方组件发送验证码

验证码发送成功，存入redis

响应客户端，客户端跳转到输入验证码页面

#### 7.1.3、代码实现

##### **LoginController**

```java
@RestController
@RequestMapping("/user")
public class LoginController {

    @Autowired
    private UserService userService;

    /**
     * 获取登录验证码
     *   请求参数：phone （Map）
     *   响应：void
     */
    @PostMapping("/login")
    public ResponseEntity login(@RequestBody Map map){
        String phone =(String) map.get("phone");
        userService.sendMsg(phone);
        return ResponseEntity.ok(null); //正常返回状态码200
    }
}
```

##### UserService

```java
@Service
public class UserService {

    @Autowired
    private SmsTemplate template;

    @Autowired
    private RedisTemplate<String,String> redisTemplate;

    /**
     * 发送短信验证码
     * @param phone
     */
    public void sendMsg(String phone) {
        //1、随机生成6位数字
        //String code = RandomStringUtils.randomNumeric(6);
        String code = "123456";
        //2、调用template对象，发送手机短信
        //template.sendSms(phone,code);
        //3、将验证码存入到redis
        redisTemplate.opsForValue().set("CHECK_CODE_"+phone,code, Duration.ofMinutes(5));
    }
 }
```

### 7.2、JWT

#### 7.2.1、简介

JSON Web token简称JWT， 是用于对应用程序上的用户进行身份验证的标记。也就是说, 使用 JWTS 的应用程序不再需要保存有关其用户的 cookie 或其他session数据。此特性便于可伸缩性, 同时保证应用程序的安全

#### 7.2.2、格式

* JWT就是一个字符串，经过加密处理与校验处理的字符串，形式为：A.B.C

* A由JWT头部信息header加密得到

* B由JWT用到的身份验证信息json数据加密得到

* C由A和B加密得到，是校验部分

![image-20210714121154190](image-20210714121154190.png)


#### 7.2.3、流程

![image-20210714121203246](image-20210714121203246.png)

#### 7.2.4、示例

导入依赖：

~~~xml
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt</artifactId>
    <version>0.9.1</version>
</dependency>
~~~

编写测试用例：

~~~java
    @Test
    public void testCreateToken() {
        //生成token
        //1、准备数据
        Map map = new HashMap();
        map.put("id",1);
        map.put("mobile","13800138000");
        //2、使用JWT的工具类生成token
        long now = System.currentTimeMillis();
        String token = Jwts.builder()
                .signWith(SignatureAlgorithm.HS512, "itcast") //指定加密算法
                .setClaims(map) //写入数据
                .setExpiration(new Date(now + 30000)) //失效时间
                .compact();
        System.out.println(token);
    }

    //解析token

    /**
     * SignatureException : token不合法
     * ExpiredJwtException：token已过期
     */
    @Test
    public void testParseToken() {
        String token = "eyJhbGciOiJIUzUxMiJ9.eyJtb2JpbGUiOiIxMzgwMDEzODAwMCIsImlkIjoxLCJleHAiOjE2MTgzOTcxOTV9.2lQiovogL5tJa0px4NC-DW7zwHFqZuwhnL0HPAZunieGphqnMPduMZ5TtH_mxDrgfiskyAP63d8wzfwAj-MIVw";
        try {
            Claims claims = Jwts.parser()
                    .setSigningKey("itcast")
                    .parseClaimsJws(token)
                    .getBody();
            Object id = claims.get("id");
            Object mobile = claims.get("mobile");
            System.out.println(id + "--" + mobile);
        }catch (ExpiredJwtException e) {
            System.out.println("token已过期");
        }catch (SignatureException e) {
            System.out.println("token不合法");
        }

    }
~~~

通过解析Token得知，如果抛出SignatureException异常表示token不合法，如果抛出ExpiredJwtException异常表示token已过期

#### 7.2.5 JWT工具类

```java
public class JwtUtils {

    // TOKEN的有效期1小时（S）
    private static final int TOKEN_TIME_OUT = 1 * 3600;

    // 加密KEY
    private static final String TOKEN_SECRET = "itcast";


    // 生成Token
    public static String getToken(Map params){
        long currentTime = System.currentTimeMillis();
        return Jwts.builder()
                .signWith(SignatureAlgorithm.HS512, TOKEN_SECRET) //加密方式
                .setExpiration(new Date(currentTime + TOKEN_TIME_OUT * 1000)) //过期时间戳
                .addClaims(params)
                .compact();
    }


    /**
     * 获取Token中的claims信息
     */
    public static Claims getClaims(String token) {
        return Jwts.parser()
                .setSigningKey(TOKEN_SECRET)
                .parseClaimsJws(token).getBody();
    }


    /**
     * 是否有效 true-有效，false-失效
     */
    public static boolean verifyToken(String token) {
      
        if(StringUtils.isEmpty(token)) {
            return false;
        }
        
        try {
            Claims claims = Jwts.parser()
                    .setSigningKey("itcast")
                    .parseClaimsJws(token)
                    .getBody();
        }catch (Exception e) {
            return false;
        }

      return true;
    }
}
```

### 7.3、用户登录

用户接收到验证码后，进行输入验证码，点击登录，前端系统将手机号以及验证码提交到服务端进行校验。

![image-20210714121439345](image-20210714121439345.png)

#### 7.3.1、接口文档

![image-20210714121642629](image-20210714121642629.png)

YAPI接口地址：https://mock-java.itheima.net/project/164/interface/api/12593

#### 7.3.2、LoginController

~~~java
    /**
     * 检验登录
     */
    @PostMapping("/loginVerification")
    public ResponseEntity loginVerification(@RequestBody Map map) {
        //1、调用map集合获取请求参数
        String phone = (String) map.get("phone");
        String code = (String) map.get("verificationCode");
        //2、调用userService完成用户登录
        Map retMap = userService.loginVerification(phone,code);
        //3、构造返回
        return ResponseEntity.ok(retMap);
    }
~~~

#### 7.3.3、UserService

~~~java
    /**
     * 验证登录
     * @param phone
     * @param code
     */
    public Map loginVerification(String phone, String code) {
        //1、从redis中获取下发的验证码
        String redisCode = redisTemplate.opsForValue().get("CHECK_CODE_" + phone);
        //2、对验证码进行校验（验证码是否存在，是否和输入的验证码一致）
        if(StringUtils.isEmpty(redisCode) || !redisCode.equals(code)) {
            //验证码无效
             throw new RuntimeException();
        }
        //3、删除redis中的验证码
        redisTemplate.delete("CHECK_CODE_" + phone);
        //4、通过手机号码查询用户
        User user = userApi.findByMobile(phone);
        boolean isNew = false;
        //5、如果用户不存在，创建用户保存到数据库中
        if(user == null) {
            user = new User();
            user.setMobile(phone);
            user.setPassword(DigestUtils.md5Hex("123456"));
            Long userId = userApi.save(user);
            user.setId(userId);
            isNew = true;
        }
        //6、通过JWT生成token(存入id和手机号码)
        Map tokenMap = new HashMap();
        tokenMap.put("id",user.getId());
        tokenMap.put("mobile",phone);
        String token = JwtUtils.getToken(tokenMap);
        //7、构造返回值
        Map retMap = new HashMap();
        retMap.put("token",token);
        retMap.put("isNew",isNew);

        return retMap;
    }
~~~

#### 7.3.4、测试

![1564300534797](1564300534797.png)

## 8、代码优化

### 8.1 抽取BasePojo

为了简化实体类中created和updated字段，抽取BasePojo

```java
@Data
public abstract class BasePojo implements Serializable {

    @TableField(fill = FieldFill.INSERT) //自动填充
    private Date created;
    @TableField(fill = FieldFill.INSERT_UPDATE)
    private Date updated;

}
```

### 8.2 自动填充

对于created和updated字段，每次操作都需要手动设置。为了解决这个问题，mybatis-plus支持自定义处理器的形式实现保存更新的自动填充

```java
package com.tanhua.dubbo.server.handler;

import com.baomidou.mybatisplus.core.handlers.MetaObjectHandler;
import org.apache.ibatis.reflection.MetaObject;
import org.springframework.stereotype.Component;

import java.util.Date;

@Component
public class MyMetaObjectHandler implements MetaObjectHandler {

    @Override
    public void insertFill(MetaObject metaObject) {
        Object created = getFieldValByName("created", metaObject);
        if (null == created) {
            //字段为空，可以进行填充
            setFieldValByName("created", new Date(), metaObject);
        }

        Object updated = getFieldValByName("updated", metaObject);
        if (null == updated) {
            //字段为空，可以进行填充
            setFieldValByName("updated", new Date(), metaObject);
        }
    }

    @Override
    public void updateFill(MetaObject metaObject) {
        //更新数据时，直接更新字段
        setFieldValByName("updated", new Date(), metaObject);
    }
}
```


