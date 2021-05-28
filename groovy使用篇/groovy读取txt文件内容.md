 ```
 //测试groovy读取txt文件
new File("${filepath}").eachLine {  
         line -> log.info( "line : $line")
      } 
     
文件路径实例：C:/Users/Documents/Example.txt
  ```
