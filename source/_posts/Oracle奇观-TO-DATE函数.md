---
title: Oracle奇观---TO_DATE函数
top: 99
copyright: true
date: 2019-04-25 16:12:50
tags: 神奇现象
---

挺神奇的。

<!--more-->

```sql
SELECT
	TO_DATE(TRIM(xz.OPT_TIME), 'YYYY-MM-DD hh24:MI:ss' ),
	xz.OPT_TIME,
	TO_DATE( TRIM( xz.BALMONTH ), 'yyyymm' ),
	xz.BALMONTH 
FROM
	"T_hefeixin_member_xz" xz
WHERE
	xz.MOBILE = '******';
```

{% if 1 == 1 %}
  {% asset_img 1555382543746.png %}
{% else %}
  ![](./Oracle奇观-TO-DATA函数/1555382543746.png)

{% endif %}



**而同样的逻辑和原始数据，在MySQL中是正常的。**

```sql
SELECT
	str_to_date( TRIM( sds_member_xz.OPT_TIME ), '%Y-%m-%d %H:%i:%S %T' ),
	sds_member_xz.OPT_TIME 
FROM
	`sds_member_xz` 
WHERE
	sds_member_xz.MOBILE = '******';
```

{% if 1 == 1 %}
  {% asset_img 1555382780119.png %}
{% else %}
  ![](Oracle%E5%A5%87%E8%A7%82-TO-DATA%E5%87%BD%E6%95%B0/1555382780119.png)

{% endif %}

目前分析认为，该现象的出现跟数据库日期格式设定、导入时的日期格式设定有关。

当前数据源可通过"dd-mm-yy hh24:MI:ss"得到正确结果。

{% if 1 == 1 %}
  {% asset_img 1555406402536.png %}
{% else %}
  ![](Oracle%E5%A5%87%E8%A7%82-TO-DATA%E5%87%BD%E6%95%B0/1555406402536.png)

{% endif %}