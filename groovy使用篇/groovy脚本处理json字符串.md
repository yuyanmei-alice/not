```
import groovy.json.JsonSlurper
import net.sf.json.*
    
import groovy.sql.Sql;
def driver= context.expand('${#Project#driver}')
def sqlconnect= context.expand('${#Project#SqlConnect}')
def sqlConnectUsername= context.expand('${#Project#SqlConnectUsername}')
def sqlConnectPassword= context.expand('${#Project#SqlConnectPassword}')
def sql = Sql.newInstance(sqlconnect, sqlConnectUsername, sqlConnectPassword, driver);


def ibid = context.expand('${#TestCase#ibid}')
def expect_navid_map = [:]
def actual_navid_map = [:]
try{
 //获取数据库记录，封装成map（预期结果）
sql.eachRow("select ${tableColumn1},${tableColumn2} from ${databaseName}.{tableName} where ibid ='"+ibid+"' and status = '0'  "){ row ->
       expect_navid_map.put(row.${tableColumn1},row.${tableColumn2})
}
//获取接口返回的数据,封装成map（实际结果）
def response = context.expand( '${getHistoryNavid#Response}' )
def slurper=new JsonSlurper()
def result=slurper.parseText(response)
def message= result.body.message
for(int i=0;i<message.size();i++){
def navid = message[i].${colunmName1}
def local_file_path = message[i].${colunmName2}
actual_navid_map.put(${colunmName1},${colunmName2})
}
}
//如果脚本异常，那么定义脚本失败
catch(Exception e){
if (e != null){
	assert false
	}
}
//业务逻辑相关代码执行完，关闭数据库链接
finally{
sql.close()
log.info("actual:"+actual_navid_map)
log.info("expect:"+expect_navid_map)
}
//检查预期结果和实际结果是否相同
assert actual_navid_map== expect_navid_map

````
