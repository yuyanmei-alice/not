
//先选择手工定义env的值，后续可根据具体的对接环境获取环境名(开发环境、测试环境等)

env="test"

//如果设置的环境为test，将test环境的配置添加到环境属性

if(env=='test'){
   log.info("test"); //在soapui中界面的最下方，有日志查看的tab,在script log 中可查看脚本的执行输出
}

//如果设置的环境为dev，将dev环境的配置添加到环境属性

if(env=='dev'){
   log.info("dev");
}
