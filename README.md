# Content
- [Introduction](https://github.com/Sakib-Mahmud13/Performance_Testing.git#introduction)  
- [Install](https://github.com/Sakib-Mahmud13/Performance_Testing.git#install)      
- [Prerequisites](https://github.com/Sakib-Mahmud13/Performance_Testing.git#prerequisites)
- [Elements of a Minimal Test Plan](https://github.com/Sakib-Mahmud13/Performance_Testing.git#Elements-of-a-minimal-test-plan)    
- [Test Plan](https://github.com/Sakib-Mahmud13/Performance_Testing.git#test-plan)
- [Collection of API](https://github.com/Sakib-Mahmud13/Performance_Testing.git#collection-of-api)   
    - [List of API](https://github.com/Sakib-Mahmud13/Performance_Testing.git#list-of-api) 
    - [Load the JMeter Script](https://github.com/Sakib-Mahmud13/Performance_Testing.git#load-the-jmeter-script)
- [Make jtl File](https://github.com/Sakib-Mahmud13/Performance_Testing.git#make-jtl-file)  
- [Make html File](https://github.com/Sakib-Mahmud13/Performance_Testing.git#make-html-file)  
- [HTML Report](https://github.com/Sakib-Mahmud13/Performance_Testing.git#html-report) 



# Introduction

This document explains how to run a performance test with JMeter against an simplelearn.com.

# Install

**Java**  
https://www.oracle.com/java/technologies/downloads/

**JMeter**  
https://jmeter.apache.org/download_jmeter.cgi  

Click =>Binaries    
=>**apache-jmeter-5.6.2.zip**

**We use BlazeMeter to generate JMX files**    
https://chrome.google.com/webstore/detail/blazemeter-the-continuous/mbopgmdnpcbohhpnfglgohlbhfongabi?hl=en

# Prerequisites
- As of JMeter 5.6, Java 8 and above are supported.
- we suggest  multicore cpus with 4 or more cores.
- Memory 16GB RAM is a good value.


# Elements of a minimal test plan
- Thread Group

    The root element of every test plan. Simulates the (concurrent) users and then run all requests. Each thread simulates a single user.

- HTTP Request Default (Configuration Element)

- HTTP Request (Sampler)

- Summary Report (Listener)

# Test Plan

Testplan > Add > Threads (Users) > Thread Group (this might vary dependent on the jMeter version you are using)

- Name: Users
- Number of Threads (users): 200 to 500
- Ramp-Up Period (in seconds): 1
- Loop Count: 1

  1) The general setting for the tests execution, such as whether Thread Groups will run simultaneously or sequentially, is specified in the item called Test Plan.

  2) All HTTP Requests will use some default settings from the HTTP Request, such as the Server IP, Port Number, and Content-Encoding.

  3) Each Thread Group specifies how the HTTP Requests should be carried out. To determine how many concurrent "users" will be simulated, one must first know the number of threads. The number of actions each "user" will perform is determined by the loop count.

  4) The HTTP Header Manager, which allows you to provide the Request Headers that will be utilized by the upcoming HTTP Requests, is the first item in Thread Groups.

# Collection of API

- Run BlazeMeter  
- Collect Frequently used API  
- Save JMX file then paste => **apache-jmeter-5.6.2\bin**

    ### List of API 

    - [https://restful-booker.herokuapp.com/](https://restful-booker.herokuapp.com/)
    - [https://restful-booker.herokuapp.com/booking](https://restful-booker.herokuapp.com/booking)
    - [https://restful-booker.herokuapp.com/bookingid](https://restful-booker.herokuapp.com/bookingid)
    - [https://restful-booker.herokuapp.com/auth](https://restful-booker.herokuapp.com/auth)
    

   **OR**
    
  ### Load the JMeter Script 
   - File > Open (CTRL + O)
   - Locate the "project_t200.jmx" file contained on this repo
   - Continue open project_t200.jmx to project_t500.jmx
   - Open those file
   - The Test Plan will be loaded
![loadjmx](https://github.com/Sakib-Mahmud13/Performance_Testing/blob/main/per5.PNG)
![loadjmx](https://github.com/Sakib-Mahmud13/Performance_Testing/blob/main/per7.PNG)


# Test execution (from the Terminal)
 
- JMeter should be initialized in non-GUI mode.
- Make a report folder in the **bin** folder.  
- Run Command in __jmeter\bin__ folder.

 ### Make jtl file

```bash
  jmeter -n -t project_t200.jmx -l report\project_t200.jtl
```      
  Then continue to upgrade Threads(200 to 400) by keeping Ramp-up Same.   

After completing this command  
   ### Make html file   
  
  ```bash
  jmeter -g report\project_t200.jtl -o report\project_t200.html
```
  - **g**: jtl results file

  - **o**: path to output folder
  - \
    ![Capture](https://github.com/Sakib-Mahmud13/Performance_Testing/blob/main/per4.PNG)  

# HTML Report

**Number of Threads 200 ; Ramp-Up Period 1s**

Requests Summary             |  Errors
:-------------------------:|:-------------------------:
![1](https://github.com/Sakib-Mahmud13/Performance_Testing/blob/main/per1.PNG)  

**Number of Threads 300 ; Ramp-Up Period 11s**
   
Requests Summary             |  Errors
:-------------------------:|:-------------------------:
![3](https://github.com/Sakib-Mahmud13/Performance_Testing/blob/main/per2.PNG) 
