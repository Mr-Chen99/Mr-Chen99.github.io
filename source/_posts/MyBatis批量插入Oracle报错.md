---
title: MyBatis批量插入Oracle报错
date: 2022-11-24 14:34:40
categories:
- Java
- Java框架
tags:
- 工作
- 遇坑
---

## MyBatis

### Oracle数据库批量插入
> **问题描述**: 我想一次性插入多条记录，数据库使用的oracle,crud框架为mybatis。出现【SQL 命令未正确结束】的错误。

> MyBatis SQL 如下:
``` sql
<insert id="insertList" parameterType="java.util.List" useGeneratedKeys="false">
    insert into TD_S_LONGSHORTLINK_JT (LINK_ID, LONG_LINK, SHORT_LINK, 
      DEAL_TIME, DESC_INFO, BAK1, 
      BAK2, BAK3)
     values
     <foreach collection="list" item="item" index="index" separator="," >  
         #{item.linkId,jdbcType=VARCHAR},
         #{item.longLink,jdbcType=VARCHAR},
         #{item.shortLink,jdbcType=VARCHAR},
         #{item.dealTime,jdbcType=TIMESTAMP},
         #{item.descInfo,jdbcType=VARCHAR},
         #{item.bak1,jdbcType=VARCHAR},
         #{item.bak2,jdbcType=VARCHAR},
         #{item.bak3,jdbcType=VARCHAR} 
    </foreach> 
  </insert>
```

> 解决代码如下：
```sql
<insert id="insertList" parameterType="java.util.List" useGeneratedKeys="false">
    insert into TD_S_LONGSHORTLINK_JT (LINK_ID, LONG_LINK, SHORT_LINK, 
      DEAL_TIME, DESC_INFO, BAK1, 
      BAK2, BAK3)
    <foreach collection="list" item="item" index="index" separator="UNION" >  
        select 
            #{item.linkId,jdbcType=VARCHAR},
            #{item.longLink,jdbcType=VARCHAR},
            #{item.shortLink,jdbcType=VARCHAR},
            #{item.dealTime,jdbcType=TIMESTAMP},
            #{item.descInfo,jdbcType=VARCHAR},
            #{item.bak1,jdbcType=VARCHAR},
            #{item.bak2,jdbcType=VARCHAR},
            #{item.bak3,jdbcType=VARCHAR} 
        from dual  
    </foreach>  
  </insert>
```
> **原因**:
> 由于**oracle数据库搭配MyBatis框架不支持values**，所以只能使用 **sparator='UNION'**
> 将插入的数据临时保存并连接起来一起插入
