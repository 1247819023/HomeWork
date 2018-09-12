##查询出所有广东省的市、县”做思路总结

###1.先查询出广东省下所有的区
select x.id,p.cityName as 省,s.cityName as 市,x.cityName as 县 from s_provinces s 
left join s_provinces x on x.parentId=s.id
join s_provinces p on s.parentId=p.id 
where p.cityName='广东省'

###2.再查询出广东省下所有的市
select p.id,p.cityName as 省,s.cityName as 市,null from s_provinces s 
left join s_provinces p on s.parentId=p.id 
where p.cityName='广东省'
###3.最后通union将两条语句拼接在一起
select x.id,p.cityName as 省,s.cityName as 市,x.cityName as 县 from s_provinces s 
left join s_provinces x on x.parentId=s.id
join s_provinces p on s.parentId=p.id 
where p.cityName='广东省'
union
select p.id,p.cityName as 省,s.cityName as 市,null from s_provinces s 
left join s_provinces p on s.parentId=p.id 
where p.cityName='广东省'

**union 查询不重复的数据；union 查询全部数据