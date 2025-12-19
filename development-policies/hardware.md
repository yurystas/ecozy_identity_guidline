# Hardware

1. ### Hardware Approach {#hardware-approach}

1. We studied current and promising solutions for organizing data transmission as part of smart home devices and identified the most interesting protocols for us, such as: Bluetooth 5.4, Thread, Zigbee, Matter, Wi-Fi (2.4/5GHz)  
2. Based on paragraph 1, we selected began to search for SoC manufacturers with parameters that meet our requirements: Support of radio communication protocols, low power consumption, availability of purchases, manufacturer support at the development and testing stage.  
3. Key electronic elements were selected based on modules or widely used SoMs, which in the future gives us the opportunity to easily replace individual electronic parts. For example, the BT40 module based on the nRF5340 chip selected as the main MCU can be easily replaced with a similar module with better RF parameters, but which requires more power consumption. We consider this case as an option when, without a radical change in the electronics, we can turn the thermostat circuit into a signal relay device by connecting it to electricity supply network via adapter rather than using battery power.  
4. We chose Nordic Semiconductor products. Each subsequent series of their MCs is compatible with the previous one or requires minor hardware changes during the transition.

   2. ### Thermostat Hardware Development Approach {#thermostat-hardware-development-approach}

The electrical circuit of the thermostat is divided into several parts, where each part is a separate printed circuit board. Each individual circuit (PCB) is a set of components that perform their role: providing power and motor control, polling sensors, interacting with the display and buttons. All key components of the circuit were selected based on the following characteristics: energy efficiency, availability for purchase in large quantities, and not expensive PCB manufacturing technology.  
![][image5]

3. ### Central Unit Hardware Development Approach {#central-unit-hardware-development-approach}

Before developing the electrical circuit, we determined the main hardware functionality that we want to receive from the central unit. We have focused on versatility and support of a large number of wireless communication interfaces and sufficient computing capabilities. We determined that we want to have an external connection via WI-FI with support of 2.4 GHz and 5 GHz frequencies, and communication with devices using 802.15.4 standard protocols. The central unit is built on the basis of a SOM with an nRF52840 microcontroller connected to it. Also, the central unit circuit has indication components, buttons and a display. The central unit, like other devices of this system, is equipped with a temperature and humidity sensors and a microphone(optional).  
![][image6]

4. ### Thermosensor Hardware Development Approach {#thermosensor-hardware-development-approach}

When developing the electrical circuit of the Thermosensor, the main emphasis is on its energy efficiency. The circuit is also built on the basis of microcontrollers of the nRF family (nRF52840) with temperature and humidity sensors connected to it. The circuit is powered by a replaceable battery and therefore in order to maintain its charge the circuit uses a power switch in front of the temperature and humidity sensor. The LED for display is also selected with minimal current consumption.  
![][image7]
