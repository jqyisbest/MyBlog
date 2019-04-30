---
title: oracle创建带自增主键的表
top: 2
copyright: true
date: 2019-04-30 14:20:51
categories:
- 实现
- 数据库
- oracle
tags:
- oracle
- 数据库
- 工具代码
---

常用的两种方式如下。

<!--more-->

1. 通过触发器实现自增，例如：

   ```sql
   -- Create table
   create table T_BASE_DATA_ALL
   (
     ID	NUMBER(20) primary key,
   INFO_ID	NUMBER(20) NOT NULL,
   IMPORT_RECORD_ID	NUMBER(20) NOT NULL,
   IMPORT_RECORD_TABLE_NAME	VARCHAR2(255) NOT NULL,
   TABLE_NAME	VARCHAR2(255) NOT NULL,
   IS_NEW	NUMBER(1) DEFAULT 0 NOT NULL,
   RECORD_TIME	DATE NOT NULL
   );
   
   -- Create sequence
   create sequence SEQ_T_BASE_DATA_ALL
   minvalue 1
   maxvalue 9999999999999
   start with 1
   increment by 1
   cache 50;
   
   
   -- Create trigger
   CREATE OR REPLACE TRIGGER "TRI_BASEINFO_ALL_FOR_PK"
     BEFORE INSERT ON T_BASE_DATA_ALL
     REFERENCING OLD AS OLD NEW AS NEW FOR EACH ROW
   DECLARE
   BEGIN
     SELECT SEQ_T_BASE_DATA_ALL.NEXTVAL INTO :NEW.ID FROM DUAL;
   END TRI_BASEINFO_ALL_FOR_PK;
   ```

   

2. 通过显示调用实现自增，例如：

   ```sql
   -- Create table
   create table test( 
   ID integer 
   ,stu_name nvarchar2(4) 
   ,stu_age number 
   );
   
   -- Create sequence
   create sequence seq_on_test 
   increment by 1 
   start with 1 
   nomaxvalue 
   nocycle 
   nocache;
   
   -- Invoke explicitly while insert
   insert into test values(seq_on_test.nextval,'Mary',15); 
   insert into test values(seq_on_test.nextval,'Tom',16); 
   ```

   

   