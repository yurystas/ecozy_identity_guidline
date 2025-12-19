# eCozy Climate Sensor Firmware

1. ### Introduction {#introduction-3}

The eCozy climate sensor is an indoor temperature and humidity meter. It is part of the eCozy ecosystem and is designed to improve the performance of the eCozy thermostat. The internal temperature sensor of the thermostat has a rather large measurement error, as it is located directly next to the heating radiator. The external climate sensor solves this problem.   
The eCozy climate sensor is wireless. It currently supports the Matter protocol. The hardware used also allows exchange via other protocols (Zigbee, Bluetooth).  
The temperature and humidity sensor can be easily integrated into Apple, Google, Amazon Matter-enabled ecosystems as a standalone device.  
The device is built on the NRF52840 SoC from Nordic Semiconductor.   
Link: [https://www.nordicsemi.com/Products/nRF52840](https://www.nordicsemi.com/Products/nRF52840)  
Going forward, we are ready for a quick migration to nRF54L series.  
Link: [https://www.nordicsemi.com/Products/nRF54L15](https://www.nordicsemi.com/Products/nRF54L15)  
The SHT40 from Sensirion is used as a temperature and humidity sensor.   
Link: [https://sensirion.com/products/catalog/SHT40](https://sensirion.com/products/catalog/SHT40)

2. ### Development Environment {#development-environment-1}

* **SDK:** NrfConnect SDK was used in the development process.The nRF Connect SDK (NCS) is Nordic Semiconductor's software development kit for building applications on their nRF52, nRF53,nRF54, nRF91, and nRF70 series SoCs. It is based on Zephyr RTOS and supports Matter, Bluetooth LE, Thread, Zigbee, LTE-M, and NB-IoT.

More information about SDK:  
[https://www.nordicsemi.com/Products/Development-software/nRF-Connect-SDK](https://www.nordicsemi.com/Products/Development-software/nRF-Connect-SDK)  
Used SDK version 2.9.0 release on 18 december 2024:  
[https://github.com/nrfconnect/sdk-nrf/releases/tag/v2.9.0](https://github.com/nrfconnect/sdk-nrf/releases/tag/v2.9.0)

* **IDE:** We use Visual Studio Code as the IDE and in it an extension to use the nrfConnect SDK. 

Link: [https://code.visualstudio.com/](https://code.visualstudio.com/)  
[https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-VS-Code](https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-VS-Code)

* **Debug:** Standard Segger J-link interface from NRF5340DK was used as a programmer and debugger. Version JLink\_7.94i was used. 

Link: [https://www.segger.com/downloads/jlink/](https://www.segger.com/downloads/jlink/)

* **Matter:** The ZAP (ZCL Advanced Platform) tool is used in Matter for configuring and generating ZCL (Zigbee Cluster Library) files, which define the attributes, commands, and clusters used in a Matter device. 

Link: [https://github.com/project-chip/zap](https://github.com/project-chip/zap)	

* **CHIP:** The CHIP Tool is a command-line tool used to commission, control, and test Matter (formerly CHIP) devices. It's part of the Matter SDK and is essential for validating Matter-based IoT devices.

[https://github.com/project-chip/connectedhomeip/tree/master/examples/chip-tool](https://github.com/project-chip/connectedhomeip/tree/master/examples/chip-tool) 

* **Other:** Nordic's desktop app for flashing and debugging.

[https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop](https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop)  
From this application we used the utilities:

* “Power Profiler” to measure the current consumption of the device.   
* “Programmer” for flashing and complete erasing of the device external and internal memory.

  3. ### Programming Languages {#programming-languages-2}

* C++ (version 17\) \- for the main firmware application.  Matter protocol is written in C++. Examples in SDK for working with Matter are also in C++. That is why we use this programming language.  
* C \- Zephyr RTOS is primarily written in C and natively supports applications written in the C language. All Zephyr API functions and macros are implemented in C and available as part of the C header files under the include directory, so writing Zephyr applications in C gives the developers access to the most features.

  4. ### Code Style / Coding Rules {#code-style-/-coding-rules-1}

When writing the code, we followed the following standards and guidelines:

* For C++ code \- guideline from Google: [https://google.github.io/styleguide/cppguide.html](https://google.github.io/styleguide/cppguide.html)  
* For C code \- Zephyr coding guidelines: [https://docs.zephyrproject.org/latest/contribute/coding\_guidelines/index.html](https://docs.zephyrproject.org/latest/contribute/coding_guidelines/index.html)

  5. ### Source Code Documentation {#source-code-documentation-1}

We use Doxygen for generating documentation, ensuring that the code is well-documented and easy to understand for future maintenance and development.  
Link: [https://www.doxygen.nl/](https://www.doxygen.nl/)

6. ### Firmware Development Principles {#firmware-development-principles}

In the development process of a climate sensor we use 6 principles.   
The SOLID principles are a set of software design guidelines that help developers create more maintainable, flexible, and robust software systems. Here is an explanation of each principle:

* Single Responsibility Principle (SRP) \- This principle states that each class or module should have only one reason to change, meaning it should have a single responsibility or purpose. By adhering to SRP, developers can create a more modular and maintainable codebase, as changes to one functionality do not affect unrelated parts of the system. A microservices architecture usually relies on this principle to ensure that each service has a single purpose, commonly in the repository level. See our post on microservices.  
* Open/Closed Principle (OCP) \- According to OCP, software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, developers should be able to add new features or functionality to an existing entity without changing its existing code. This is typically achieved through inheritance or composition, which allows for a more stable and less error-prone codebase.  
* Liskov Substitution Principle (LSP) \- LSP states that objects of a derived class should be able to replace objects of the base class without affecting the correctness of the program. This means that derived classes must honor the contracts, behavior, and properties of the base class, ensuring that the software remains consistent and reliable also when new subclasses are introduced.  
* Interface Segregation Principle (ISP) \- ISP emphasizes that clients should not be forced to depend on interfaces they do not use. Instead, interfaces should be segregated into smaller, more specific ones, allowing clients to depend only on the relevant interfaces. This reduces the coupling between components and improves the maintainability and flexibility of the software.  
* Dependency Inversion Principle (DIP) \- DIP advocates for the inversion of dependencies between high-level and low-level modules. High-level modules should not depend on low-level modules directly. Instead, both should depend on abstractions. For example, if a high level module requires a logging capability, it should not directly reference a low-level logging library. Instead, it should reference an abstracted logging service, making it possible to switch out the logging library in the future. This principle allows for greater flexibility and easier adaptation to changes, as high-level modules can be easily switched to work with different low-level implementations without needing modification.  
* Don’t Repeat Yourself (DRY) \- The DRY principle emphasizes the importance of avoiding duplication in code. Duplication can lead to inconsistencies, increased maintenance effort, and a higher likelihood of introducing errors when changes are required. To adhere to the DRY principle, developers should utilize abstractions, modularization, and reusable components to eliminate redundancy, ensuring that each piece of functionality is implemented in only one place. A simple example would be to create a function and call it from multiple locations, rather than implementing the same functionality multiple times.  
* Encapsulation Principle \- Encapsulation is a core concept in object-oriented programming that promotes the bundling of data (attributes) and methods (functions) that operate on the data within a single unit, typically a class. This principle advocates for hiding the internal workings of a class and exposing only what is necessary through a well-defined interface. By doing so, developers can prevent unintended access or modification of internal data, reduce coupling between components, and simplify the maintenance and modification of the code. This principle is not limited to object-oriented programing, can also be applied to data structures, file formats or network traffic.  
* Principle of Least Astonishment (PoLA) \- PoLA is a design guideline that encourages developers to create software components that behave predictably and intuitively, minimizing surprises for users or other developers interacting with the component. This principle applies to user interfaces, APIs, and code. By adhering to PoLA, developers create software that is easier to use, understand, and maintain, ultimately reducing the likelihood of errors and misunderstandings.  
* You Aren’t Gonna Need It (YAGNI) \- YAGNI is a principle that advises against implementing features or functionality before they are actually needed. This approach encourages developers to focus on the current requirements and avoid over-engineering, which can lead to increased complexity, longer development time, and wasted effort.  
* Keep It Simple, Stupid (KISS) \- The KISS principle emphasizes the importance of simplicity in software design. It encourages developers to avoid unnecessary complexity and create straightforward, easy-to-understand solutions. By keeping the design simple, developers can reduce the chances of introducing errors, improve maintainability, and make it easier for others to understand and contribute to the codebase. KISS does not mean oversimplifying or ignoring essential requirements; instead, it suggests finding the simplest solution that meets the project’s needs.

  7. ### Firmware Architecture Description {#firmware-architecture-description-1}

The firmware description of the device is shown in the figure below:  
![][image3]

Main firmware modules:

* Temperature and humidity sensor SHT40 connected via I2C interface. Used for climate control.   
* MX25R16 external 2Mbit memory IC connected via QSPI interface. This IC is used for dual bank OTA firmware update mechanisms.   
* Button for device reset and initialization;  
* LED for device status control;   
* Battery measurement module. ADC measurement of the button voltage.   
* Wireless connection. Bluetooth for device commissioning. Thread protocol and Matter application layer.

The standard HAL from RTOS Zephyr and drivers are used to control the peripherals. Main application contains 2 threads Main and Application business logic. The firmware is based on the Matter common application from the Nordic nrfConnect SDK.

8. ### Key Features {#key-features-1}

**Text:**

* **High-Accuracy Sensing:** Utilizes the Sensirion SHT40 for precise, factory-calibrated temperature and humidity readings.  
* **Matter-over-Thread:** Natively supports the Matter protocol for seamless, low-power, and reliable integration with the eCozy ecosystem and third-party hubs (Apple, Google, Amazon).  
* **Ultra-Low Power:** Optimized for multi-year battery life on a single coin cell, achieved through deep sleep modes and efficient data reporting intervals.  
* **Secure OTA Updates:** Supports secure, dual-bank Over-the-Air (OTA) firmware updates via the Thread network to deliver new features and security patches.  
* **Simple Commissioning:** Uses Bluetooth LE for initial setup and secure commissioning onto the user's Thread network.

  9. ### Libraries {#libraries}

**Text:**

* **Zephyr RTOS:** The core real-time operating system providing the kernel, drivers, and protocol stacks.  
* **nRF Connect SDK:** Provides Nordic-specific drivers (e.g., SHT40) and the Matter implementation.  
* **ZCL (Zigbee Cluster Library):** Used by Matter to define the attributes and commands for device features.  
* **Doxygen:** Used for generating source code documentation from code comments.

  10. ### Additional Documentation {#additional-documentation-1}

**Text:**

* **Climate\_Sensor\_Matter\_Clusters.pdf:** This document details the specific Matter clusters, attributes, and events implemented by the Climate Sensor. It serves as the primary technical reference for integration with the backend and third-party applications.  
* **SHT40\_Integration\_Guide.md:** Internal engineering notes on the driver implementation, power management strategies (re: polling intervals vs. battery life), and calibration data for the Sensirion SHT40 sensor.
