project = testRunner.testCase.testSuite.project ;

tcase = project.testSuites["${testsuite}"].testCases["${testcase}"] ;

tstep = tcase.getTestStepByName("${teststep}");

def status = tstep.run(testRunner, context)

def result = status.getStatus().toString();

log.info ("   ----   "+result)
