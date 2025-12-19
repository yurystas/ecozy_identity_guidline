# Thermostat Firmware

1. ### Introduction {#introduction-1}

The thermostat firmware is being developed for the NRF5340 microcontroller by Nordic Semiconductor. The Nordic SDK is based on the Zephyr RTOS. The SDK version used for thermostat development is 2.6.0.  
Link: [https://github.com/nrfconnect/sdk-nrf/releases/tag/v2.6.0](https://github.com/nrfconnect/sdk-nrf/releases/tag/v2.6.0)

2. ### Programming Languages {#programming-languages}

The following programming languages are used in the project: 

* **C++** (version 17\) \- for the main firmware application.   
* **C** \- Zephyr RTOS is primarily written in C and natively supports applications written in the C language. All Zephyr API functions and macros are implemented in C and available as part of the C header files under the include directory, so writing Zephyr applications in C gives the developers access to the most features.  
* **Python** \- It is used for developing the PID controller, collecting data, calculating coefficients, and writing other auxiliary software.

  3. ### Code Style / Coding Rules {#code-style-/-coding-rules}

When writing the code, we followed the following standards and guidelines:

* For C++ code \- guideline from Google:  
  * [https://google.github.io/styleguide/cppguide.html](https://google.github.io/styleguide/cppguide.html)  
* For C code \- Zephyr coding guidelines:  
  * [https://docs.zephyrproject.org/latest/contribute/coding\_guidelines/index.html](https://docs.zephyrproject.org/latest/contribute/coding_guidelines/index.html)

    4. ### Source Code Documentation {#source-code-documentation}

We use Doxygen for generating documentation, ensuring that the code is well-documented and easy to understand for future maintenance and development.  
Link: [https://www.doxygen.nl/](https://www.doxygen.nl/)

5. ### Firmware Architecture Description {#firmware-architecture-description}

During the development of the thermostat firmware, we followed a **modular approach**, which included the following key principles:

* **Separation into independent modules** \- Each functional block was divided into separate modules with clearly defined tasks. For example, a module for temperature sensor management, a module for PID controller calculations, etc. More detailed diagram is provided below.   
* **Data encapsulation** \- Each module was responsible for its own domain and hid the internal implementation details. The interaction with the modules only through well-defined interfaces (e.g., public functions), which simplified the use and testing of individual components.	  
* **Reusability** \- Modules were designed to be easily reusable in other projects or parts of the system. For example, the PID controller code was isolated into a separate module, which can be used not only in the current project but also in other applications with similar tasks.	  
* **Testability** \- Each module was developed with testability in mind. Separate unit tests were created for each module, allowing them to be isolated and tested independently, ensuring system stability and correctness as a whole.	  
* **Code cleanliness and organization** \- The modular approach helped avoid spaghetti code and made the project easier to navigate. Each module was responsible for its part of the functionality, making the code more structured and easier to understand.  
* **Use of libraries and third-party solutions** \- For implementing certain functionalities, we used ready-made libraries and solutions, which helped reduce development time and improve reliability. For example, standard Zephyr and Nordic libraries were used for communication protocols. In this way, the modular approach made the system more flexible, improved maintainability and extensibility, and simplified the development and testing processes.

More detailed information can be found in the firmware architecture file.  
	  
//TODO: need to develop file

6. ### Key Features {#key-features}

   1. #### “Matter-over-thread” Communication Protocol {#“matter-over-thread”-communication-protocol}

For wireless communication, we use Matter communication protocol.  
Link: [https://csa-iot.org/all-solutions/matter/](https://csa-iot.org/all-solutions/matter/)  
The Matter protocol provides seamless integration with various smart home ecosystems, ensuring cross-platform compatibility and enhanced security. This allows the thermostat to interact with devices from other Matter-supported platforms such as Apple HomeKit, Google Home and Amazon Alexa, offering users a more unified and flexible experience.	  
A more detailed description of clusters, attributes, and events are in the file: “eCozy Smart Radiator Thermostat. Matter protocol nodes, endpoints, clusters, attributes description”

//TODO: need to develop file

2. #### Alarm Sound Recognition {#alarm-sound-recognition}

The AI-based microphone system for eCozy Smart Thermostat is the additional module which is used to detect and recognize different environmental sounds using artificial intelligence. This is the Edge AI solution, all calculations and recognitions are done inside the microcontroller.  No external servers or internet connections are used.  
The system for now can detect the following sound pattern:

* fire alarm siren; 

In the future, the following patterns are planned:

* Child crying;  
* Dog barking;  
* Other sounds.

For development, we used TensorFlow Lite (Lite RT), which is a lightweight version of TensorFlow designed for running machine learning models on mobile and embedded devices with limited resources. TensorFlow Lite is optimized for performance and efficiency, making it ideal for applications like your thermostat, where real-time processing and low power consumption are key.  
Link: [https://developers.googleblog.com/en/tensorflow-lite-is-now-litert/](https://developers.googleblog.com/en/tensorflow-lite-is-now-litert/)

7. ### Development Environment {#development-environment}

   1. #### Visual Studio Code IDE {#visual-studio-code-ide}

**Text:** The primary IDE for firmware development. It is lightweight, fast, and provides powerful integration with the nRF Connect SDK extension for debugging, code navigation, and managing build configurations.

2. #### NrfConnectSDK Version 2.6.0. Extension {#nrfconnectsdk-version-2.6.0.-extension}

**Text:** The official Nordic Semiconductor extension for VS Code. It is mandatory for development as it manages the nRF Connect SDK installation, toolchain, and provides a GUI for Kconfig and Devicetree settings, as well as one-click build and flash commands.

3. #### West (Zephyr’s meta-tool) {#west-(zephyr’s-meta-tool)}

**Text:** The primary command-line tool for managing the Zephyr project. `west` is used to:

* Initialize the project and manage module dependencies (`west init`, `west update`).  
* Build the firmware (`west build`).  
* Flash the firmware to the target (`west flash`).  
* Debug the target (`west debug`).

  4. #### Segger J-Link for Debug {#segger-j-link-for-debug}

**Text:** The standard hardware debug probe used by the team. It provides the physical interface between the developer's PC and the nRF5340's SWD port, enabling reliable flashing, RTT logging, and in-circuit debugging (breakpoints, memory inspection).

5. #### PyCharm [www.jetbrains.com/pycharm](http://www.jetbrains.com/pycharm) {#pycharm-www.jetbrains.com/pycharm}

**Text:** Used by the firmware team for developing and testing auxiliary Python scripts, such as PID controller simulation, log parsing, and test automation scripts.

8. ### Additional Documentation {#additional-documentation}

   1. #### Thermostat\_fw\_arch.drawio \- Thermostat Class Architecture UML Diagram {#thermostat_fw_arch.drawio---thermostat-class-architecture-uml-diagram}

**Text:** This diagram illustrates the high-level software architecture. It defines the main classes (e.g., `SensorManager`, `MotorController`, `MatterHandler`, `DisplayManager`), their primary responsibilities, and their interactions (dependencies, interfaces). This document is essential for understanding how to add new functionality without violating separation of concerns.
