## 总结分割方法
#### 1.先创建表：lagou_company,再取得与公司相关的字段：company_id、company_short_name、company_full_name、company_size、financestage，去除重复，然后将数据插入到表lagou_company中;
#### 2.删除lagou表中原来与公司相关的字段，保留company_id；
#### 3.创建lagou_city表，获取p_procince表中的区id、省、市、区数据，将数据插入lagou_city表；
#### 4.将lagou表中的city和district字段改成lagou_city表相对应的字段；
#### 5.当lagou表中的district字段为空时，把lagou和lagou_city表连接查询，因为lagou_city表中的所有城市都带有“市”结尾，而lagou表中的城市没有，所以讲两个表连接查询需要用到like关键词；
#### 6.当lagou表中的district字段不为空时，需要获取的是district的id，这时这时lagou表和lagou_city表的连接条件就是二者的city相同，以及district相同。当两个表中的district字段为空，就会产生数据的混淆；
#### 7.将查询lagou和lagou_city的语句用union all 关联起来得到的结果插入lagou_position表中