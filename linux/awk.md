### awk

始末字符串

awk '/# Time: '191020'/,/# Time: '191021'/' slow-last-20191021.log.bak > slow-191020.log

时间范围 $4代表第4位

cat  access.log | awk '$4 >="[14/Mar/2019:00:00:00" && $4 <="[14/Mar/2019:23:59:59"'  > 20190314-access.log