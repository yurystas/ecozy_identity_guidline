# Quality Assurance

1. ### Objectives {#objectives}

* Detection and prioritization of defects   
* Providing timely feedback about the current quality of the product   
* Establishing confidence in the quality of the system as a whole   
* Verification that all functional and non-functional requirements of the system have been implemented   
* Validating that the system is complete and will work as expected 

  2. ### Approach {#approach}

**Text:** Our QA approach is built on a **continuous testing model** that integrates hardware, firmware, mobile, and backend validation at every stage of the development lifecycle. We combine automated and manual testing to ensure comprehensive coverage.

This strategy is layered, as visualized by our testing pyramid. We focus on building a strong foundation of **Unit** and **Component Tests** to catch issues early, supplemented by broad **Integration** and **System Testing** to validate end-to-end user scenarios. This structured approach allows us to detect defects efficiently, minimize regression, and release high-quality, reliable products to our users.

1. #### Test Levels {#test-levels}

The testing has been divided into the following levels, as shown in the pyramid diagram below.  
![][image8]  
At the bottom level of the pyramid is **Unit Testing**. The main goal of this testing is to verify individual functions, methods, or classes within the codebase to ensure their behavior aligns with expectations.   
The next level is **Component Testing**. We use this level to test groups of interconnected components or modules and ensure that they work together as expected. For example, testing the interaction between dependent functions or classes.   
To verify the connection between different modules or subsystems of software and hardware, ensure the correctness of data flow, and proper functioning of interfaces, we conduct **Integration Testing**.   
The fourth level is **System Testing**. It allows us to test the entire product to ensure it meets the specified requirements.   
The top level of the pyramid includes testing the product from the perspective of the end- users, ensuring that the product meets their needs and expectations. This is **User Acceptance Testing**.

2. #### Test Types {#test-types}

The following types of testing are used for our product.   
**Smoke testing** \- This test is done to make sure that the software and hardware under test are ready or stable for further testing.   
**Critical path testing** \- This type focuses on testing the functionality that is essential for the core business processes or critical functions of the application.   
**Extended testing** is used to check the product's behavior in all possible and available scenarios, data variations, and system operating conditions.   
The following additional types of Extended testing have been chosen for execution: 

* Exploratory Testing   
* Usability Testing   
* Compatibility Testing   
* Recovery Testing   
* Load Testing 

**New Feature testing** \- refers to the process of testing newly developed functionalities or features within a software application to ensure they meet the specified requirements, work as intended, and do not adversely impact existing features.   
**Regression testing** is performed to ensure that recent changes or modifications in the software do not adversely affect the existing functionalities. It involves retesting the previously tested functionalities to verify that they still work correctly after any code changes, updates, or enhancements have been made.

3. #### Timeline for Key Test Types {#timeline-for-key-test-types}

* Smoke testing \- After each build deployment   
* New Feature testing \- During active development phase (develop branch)   
* Regression testing \- Stabilization phase, no active development, code freeze is required (release branch)

  4. #### Test Activities and Tasks {#test-activities-and-tasks}

A testing process includes the following primary groups of activities: 

* Requirements Analysis   
* Test Planning   
* Test Development   
* Preparation of the testing environment   
* Test Execution   
* Bugs Reporting   
* Bug Fixes Validation   
* Test Results Reporting

  5. #### Defect Management {#defect-management}

All identified defects are logged in Jira.   
The defect report contains the following information:

* Issue Type \- Bug   
* Summary   
* Priority  
* Assignee   
* Environment \- environment and build/patch version    
* Description \- in the following format:   
  * Steps to Reproduce  
  * Actual Result  
  * Expected Result  
* Linked issues   
* Sprint 

An issue has a priority level which indicates its importance or urgency of fixing. The currently defined priorities are listed below.

| Priority | Description | Workaround |
| ----- | ----- | ----- |
| Blocker | Blocks development and/or testing work, production could not run. This has to be fixed immediately. | Does not have a workaround |
| Critical | Crashes, loss of data, severe memory leak. | Does not have a workaround |
| Major | The defect affects major functionality or major data. | Has a workaround but is not obvious and difficult. |
| Minor | The defect affects minor functionality or non-critical data. | Has an easy workaround. |
| Trivial | Does not affect functionality or data. Does not affect productivity or efficiency. | Does not need a workaround. |

3. ### Test Environment {#test-environment}

We use the following environment and infrastructure for testing:

* Test Cloud  
* Wi-Fi routers  
* Cellular networks  
* IOS and Android mobile devices  
* Test Rooms with the ability to install Thermostats  
* Central Units  
* Temperature Sensors

Specialized **Testing Rooms** were created to adjust temperature and humidity levels within these spaces. Each Testing Room is equipped with a **thermometer, hygrometer**, and **Wi-Fi network** for internet access. Additionally, each heating radiator in these rooms is outfitted with a Test **Thermostat**. The Thermostat communicates with the **Central Unit** according to the Matter standard. Furthermore, a Test **Temperature Sensor** is installed in the Testing Rooms, also interfacing with the Central Unit based on the Matter standard. The Сentral Unit transmits information about the test devices over the Wi-Fi network to the **Test Cloud**. Mobile clients can connect to the system using either a **Cellular** or Wi-Fi network from any location, or locally at the test space.  
![][image9]

1. #### Tools {#tools}

**Software:**

* Jira \- Defects, stories, tasks  
* Charles [www.charlesproxy.com](https://www.charlesproxy.com)  
* Wireshark [www.wireshark.org](https://www.wireshark.org)  
* Postman [www.postman.com](https://www.postman.com)  
* Swagger [www.swagger.io](https://swagger.io)  
* Jmeter [www.jmeter.apache.org](https://jmeter.apache.org)  
* PyCharm [www.jetbrains.com/pycharm](https://www.jetbrains.com/pycharm)  
* Google Chrome [www.google.com/chrome](https://www.google.com/chrome)  
* Minicom [www.help.ubuntu.com/community/Minicom](https://help.ubuntu.com/community/Minicom)  
* adb [www.developer.android.com/tools/adb](https://developer.android.com/tools/adb)  
* Altium Designer [www.altium.com](http://www.altium.com) 

**Test Repository:**

* SharePoint \- document management and storage system  
* GitLab [www.about.gitlab.com](https://about.gitlab.com)

**Hardware:**

* Development boards  
* Thermometers  
* Hygrometers  
* Different types of thermostatic valves  
* Amazon Echo 4th  
* Wi-Fi routers  
* IOS and Android mobile devices

  4. ### Artefacts {#artefacts}

* Test Plans  
* Checklists  
* Defect reports  
* Test scripts
