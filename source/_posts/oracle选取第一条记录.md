---
title: oracle选取第一条记录
top: 2
copyright: true
date: 2019-05-15 15:49:59
categories:
- 实现
- 工具代码
- 数据库
- oracle
tags:
- 选取有限条记录
---

```sql
SELECT
	* 
FROM
	( 这里写实际的select逻辑 ) 
WHERE
	ROWNUM = 1;
```

ROWNUM数字可以改成你想要的条数**n**，但注意**是从前往后选取n条**。