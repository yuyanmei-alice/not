import com.eviware.soapui.support.types.StringToStringsMap 

def GetCookie=testRunner.testCase.testSteps["Login.to"].testRequest.response.responseHeaders["Set-Cookie"] //获取登录步骤里的COOKIE信息

log.info(GetCookie)

def headers = new StringToStringsMap()
def Referer = context.expand( '${#Project#Wshttp}' )

headers.put("Cookie",GetCookie)
headers.put("Referer",Referer)


testRunner.testCase.testSuite.project.getTestSuiteList().each //将Cookie信息传递给后续步骤

{
      if(it.getName()!="Login.do"){  
      it.getTestCaseList().each{
             it.getTestStepList().each{
                           if(it.config.type=~/request/){
                           it.testRequest.setRequestHeaders(headers)
                           }
             }
      }
}}
