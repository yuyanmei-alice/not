```
import groovy.sql.Sql;
**连接数据库**
driver= context.expand('${#Project#driver}')
sqlconnect= context.expand('${#Project#SqlConnect}')
sqlConnectUsername= context.expand('${#Project#SqlConnectUsername}')
sqlConnectPassword= context.expand('${#Project#SqlConnectPassword}')
sql = Sql.newInstance(sqlconnect, sqlConnectUsername, sqlConnectPassword, driver);

**执行删除操作**

fbkId= context.expand('${GenerateFeedbackId#Response}')

 sql.connection.autoCommit = false
      def sqlstr = "delete from commentdb.t_sh_feedback where id ='"+fbkId+"'"
   
      try {
         sql.execute(sqlstr);
         sql.commit()
         log.info("Successfully committed")
      }catch(Exception ex) {
         sql.rollback()
         log.info("Transaction rollback")
      }


**关闭连接**
      sql.close()
```


groovy连接数据库进行查询操作

```

import groovy.sql.Sql;
**连接数据库**
driver= context.expand('${#Project#driver}')
sqlconnect= context.expand('${#Project#SqlConnect}')
sqlConnectUsername= context.expand('${#Project#SqlConnectUsername}')
sqlConnectPassword= context.expand('${#Project#SqlConnectPassword}')
sql = Sql.newInstance(sqlconnect, sqlConnectUsername, sqlConnectPassword, driver);


try{
	sql.eachRow('SELECT VERSION()'){ row ->
         println row[0]
      }
	}


catch(Exception e){
	
	}

finally{
	sql.close()
	}
```
