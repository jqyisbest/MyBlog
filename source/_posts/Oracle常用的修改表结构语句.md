---
title: Oracle常用的修改表结构语句
top: 2
copyright: true
date: 2019-08-23 10:33:00
categories:
- 实现
- 工具代码
- 数据库
- oracle
tags:
- 修改表结构
---

```java
/**
 * ALTER TABLE TABLENAME RENAME COLUMN COLUMNNAME TO COLUMNNAME_NEW
 */
String alterFieldSql = "ALTER TABLE " + tableName + " RENAME COLUMN ";
/**
 * ALTER TABLE TABLENAME MODIFY COLUMNNAME TYPE(SIZE)
 */
String alterFieldTypeAndSizeSql = "ALTER TABLE " + tableName + " MODIFY ";
/**
 * ALTER TABLE TABLENAME MODIFY COLUMNNAME DEFAULT(VALUE)
 */
String alterFieldDefaultSql = "ALTER TABLE " + tableName + " MODIFY ";
/**
 * ALTER TABLE TABLENAME MODIFY COLUMNNAME NULL/NOT NULL
 */
String alterFieldNullableSql = "ALTER TABLE " + tableName + " MODIFY ";
/**
 *  修改主键逻辑：
 *  1、查询主键约束名(复合主键也只有一个约束)
 *  SELECT CONSTRAINT_NAME FROM USER_CONSTRAINTS WHERE TABLE_NAME=TABLENAME AND CONSTRAINT_TYPE ='P'
 *  2、删除旧主键约束
 *  ALTER TABLE TABLENAME DROP CONSTRAINT CONSTRAINTNAME
 *  3、添加新主键约束
 *  ALTER TABLE TABLENAME ADD CONSTRAINT CONSTRAINTNAME（建议设为：P_TABLENAME）PRIMARY KEY(COLUMNNAME1,COLUMNNAME2...)
 */
String selectPKConstraintSql = "SELECT CONSTRAINT_NAME FROM USER_CONSTRAINTS WHERE TABLE_NAME=" + tableName + " AND CONSTRAINT_TYPE ='P'";
String deleteOldPKConstraintSql = "ALTER TABLE TABLENAME DROP CONSTRAINT ";
String addPKConstraintSql = "ALTER TABLE " + tableName + " ADD CONSTRAINT P_"+tableName + " PRIMARY KEY(";
/**
 * COMMENT ON COLUMN 表名.字段名 IS '字段的注释信息';
 */
String alterCommentSql = "COMMENT ON COLUMN " + tableName + ".";
```

