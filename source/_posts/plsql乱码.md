title: PLSql中文乱码解决方案
date: 2016-06-28 18:44:12
updated	: 2016-06-28 18:44:12
permalink: 技术铛
tags:
- 数据库
- Oracle
- 乱码
categories:
- 技术档

---

## （一）原因
Oracle服务器编码与plsql编码不一致
## （二）解决方案
1. 取得服务端编码格式
	- select userenv('language') from dual;  
	假设结果为AMERICAN_AMERICA.ZHS16GBK
2. 设置本地环境变量（PLSQL优先从环境变量中获取属性）
	- 右击 我的电脑 -> 系统属性 -> 高级系统设置 -> 环境变量 -> 系统变量栏
   - 新增：  
   变量名：'NLS_ CHARACTERSET' 变量值：'ZHS16GBK'  
   变量名：'NLS_ LANG'  变量值： 'AMERICAN_AMERICA.ZHS16GBK'
3. 重启PLSQL，再次查询原来乱码的数据，完美展示