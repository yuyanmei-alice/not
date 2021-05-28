soapui中使用groovy脚本分割字符串
```
mylist = []
a = "su001;su002;su003"
str = a.split(';')
log.info(str)
  for( String values : str )
       mylist.add(values)
       log.info(mylist)
```

打印结果：
[Ljava.lang.String;@716601

[su001, su002, su003]
