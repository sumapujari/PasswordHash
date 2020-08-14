# Disclaimer: Following the testing life cycle of the Password Hash application has been executed in the windows 10 platform. In this executions following tools have been used.
1) GIT BASH
2) POSTMAN
3) SOAP UI
4) GIT REPO
# Prerequisites
# Note: I have provided abstract introductory document with name TakeHomeAssignment_JumpCloud.docx
# Step1: Download the .tpz files using the following
    https://s3.amazonaws.com/qa-broken-hashserve/broken-hashserve.tgz
# Step2: Install GIT BASH using the following URL
    https://gitforwindows.org/
# Step3: Set PORT in env variables by using the following path
type environmental variables in cortana->select environmental variables->click new->add under users ->     PORT=8088
# Step4: Open the GIT BASH tool and navigate to the application download folder
# Step5: Set port in BASH using the following command
    EXPORT PORT=8088
# Step6: Confirm PORT is SET using the following command
    ECHO $PORT
# Step7: Using command PWD to make sure you are in an application download directory
# Step8: Start the application using the following command
    ./broken-hashserve_win.exe
# Step9: Open second GIT BASH Terminal
# Step10: Confirm if 8088 port is listening by executing the following command
    netStat -a
# Step11: Open the excel sheet that is provided in the folder by name "broken_hashserve_test_cases.xls"
# Step12: The columns in the document broken-hashserve_test cases.xls is self-explanatory. Please note in this document I have provided suggestions and finding from an end-user and testing engineer perspectives. These suggestions follow best practices of an application development
#note: The test case numbers used will correspond to the test cases created in SOAP UI excluding the manual run steps which are not configured in SOAP UI. Example cases in SOAP UI TCO3, TC0 3.1, etc. This is a best practice to link the test scripts with test execution.
# SOAP UI SETUP
To run the test scenarios. I have used the SOAP UI so that it will provide details of all the execution strategies and scenarios which are used to test this application. The free version is used to test the application.
# Step1: Download SOAP UI using the following link
    https://www.soapui.org/downloads/soapui/
# Step2: Install the application form downloaded folder by executing the .exe file
# Step3: Import the project with name broken_hashserve_soapui_project.xml from the folder using the following path
    Open SOAP UI-> Go to File menu->click import-> Go to project folder download from GIT REPO-> Select -> broken_hashserve_soapui_project->click open
# Step4: Verify project is imported into SOAP UI and it looks as below screenshot provided in a folder with name broken_hashserve_soapui_project.png
# Step5: Expand the test suite in the project by name REST Project 1
# Step6: You should see the following resources and followed by test suites at the abstract level as shown below.
    http://127.0.0.1:8088
      http://127.0.0.1:8088 TestSuite
      http://127.0.0.1:8088 TestSuite_Multiple_Threads
      http://127.0.0.1:8088 TestSuite_Parallel
 # Executing Test Scenarios In SOAP UI - Testsuite       http://127.0.0.1:8088 TestSuite
 In this test suite. There are are following test cases
  Hash-OPTIONS_TestCase
  Hash-POST_TestCase
  Hash-GET_KEY_TestCase
  Hash_GET_STATS
  Hash-POST_SHUTDOWN
  #Details of each test case
  # 1) This test cases contains Hash-OPTIONS TestCase corresponing to Test Case # TC02.01   broken_hashserve_test_cases.xls
 # 2)  This test case contains Hash-POST TestCase corresponding to Test Case # (s) as mentioned below.
  TC03,TC03.01,TC03.03,TC03.04,TC03.05,TC03.06,TC03.07,TC03.08,TC03.09,TC03.10,TC03.11
 # 3) This test case contains Hash-GET_KEY TestCase corresponding to Test Case # (s) as mentioned below.
    TC03.12,TC03.13,TC03.14
# 4) This test case contains Hash_GET_STATS TestCase corresponding to Test Case # (s) as mentioned below.
    TC03.16 and TC03.17
# 5) This test case contains Hash-POST_SHUTDOWN TestCase TestCase corresponding to Test Case # (s) as mentioned below.
    TC05 and TC05.2
# Load Tests
To perform load test you need to use a test case suite http://127.0.0.1:8088 TestSuite_Multiple_Threads which consists of test case Hash-POST_MultipleThreads_TestCase. In this test case, the steps correspond to TC04 Test Case # in broken_hashserve_test_cases.xls document.
 Following steps should be followed to run load test
 # Step1: Expand http://127.0.0.1:8088 TestSuite_Multiple_Threads->Hash-POST_MultipleThreads_TestCase->Load Tests (1)-> double click LoadTest_TCO4_MultipleThreads
 # Step2: Set following parameters in the load test screen
 Threads: 1000
 Strategy: Burst
 Test Delay: 7
 Burst Duration:7
 Limit : 100000 select total runs
 # Paralle Tests
 To perform a parallel test you need to use test case suite  http://127.0.0.1:8088 TestSuite_Parallel which consists of test case Hash-POST ShutDown_Parallel_TestCase. In this test case the steps corresponds to TC05.03 Test Case # in broken_hashserve_test_cases.xls document. The Test Case # TC05.03 has a child created in SOAP UI which is not present in the broken_hashserve_test_cases.xls document.
 Following steps should be performed to run a parallel test
 # Step1: Double click test suite http://127.0.0.1:8088 TestSuite_Parallel
 # Step2 Select parallel processing which is 4th option in the test runner

# Load Test
To perform dynamic load testing. I have used the groovy script to create POST, GET the key value and then retrieve the stats. To perform the load test use the project REST Password-Hash Load Test which contains a test suite http://127.0.0.1:8088 TestSuite_LoadTest.
# Note I have provided reports of the load test in the folder Reports
# Steps to run Load Test
# Step1: Import the project with name REST-Password-Hash-soapui-project.xml from the folder using the following path
    Open SOAP UI-> Go to File menu->click import-> Go to project folder download from GIT REPO-> Select -> REST-Password-Hash-soapui-project->click open
# Step2 Double click LoadTest to open test runner
# Step3 Set following parameters
    Thread = 200
    Strategy = Burst
    Bust Duration = 7 sec
    Limit = 100000 total runs
 