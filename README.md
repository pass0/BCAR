# BCAR
en: Be careful about registration | zh: 谨慎注册

# 中文
所有不给注销的、账号删不干净的，不管什么服务，都是流氓！流氓！！！

# English
Some websites and applications, the above registered accounts are difficult to delete, or can not completely clear the history (even, some *dirty words * does not provide "delete account" function), but when people register, these websites and applications are absolutely No hints will be given. 
In order to avoid, people will find such a bad thing when they want to delete the account. I initiated this project.

# JSON
```
{
name:name,
site:url,
sharing:1(no)|url,
clean:1(can not)|2(incomplete)|3(complete),
delete:(1(can not)|2(incomplete)|3(complete))+
(url|lang("zh"|"en"|something)+String to explain how to delete the account),
replace:1(can not)|lang("zh"|"en"|something)+String to explain how to delete the account,
history:1(can not)|2(incomplete)|3(complete),
data:1(can not)|2(incomplete)|3(complete),
edit:1(can not)|2(incomplete)|3(complete) if not 1(can not edit) push + 4(can edit history)&|6(can edit data),
}
or
{
name:xxx,
site:"xxx.com",
sharing:1,
clean:1,
 \<!-- if clean is 1 ,the others pass--\>
}
to
["name","url",1,2,1,1,1,1,6]
or
["name","url",1,1]
```
name - 服务名

site - 服务地址，URL

sharing - 同源服务的地址，URL，如果此地址在库中没有，应该一并添加

clean - 是否可以清理账户信息，1不可以，2可以不完全清理，3可以完全清理

delete - 是否可以直接删除，1不可以，如果可以，说明操作方式

replace - 是否可以用删除以外的的方式清理账户信息，1不可以，如果可以，说明操作方式

history - 是否可以清理账户痕迹（帖子、评价……），1不可以，2可以不完全清理，3可以完全清理

data - 是否可以清理账户个人资料，1不可以，2可以不完全清理，3可以完全清理

edit - 是否可以保留账号功能的编辑账户信息，1不可以，2+4=6可以不完全编辑历史痕迹，2+4+6=12可以不完全编辑账户信息，3+6=9可以完全编辑个人资料，类推……

# PATH
按site地址取第一位分类放入文件夹（非英文字符转为UNICODE），子文件中再按域名分类，然后再由顶级域名TLD，单文件以site命名。
URL的特殊字符转义为UNICODE码（小写）。
转换UNICODE使用encodeURIComponent()

example：

a_new_item =
{
name:xxx,
site:"example.com/some/index.html",
others……
}

a_new_item save to =

./e/com/orz.com/example.com%2Fsome%2Findex.html.json
