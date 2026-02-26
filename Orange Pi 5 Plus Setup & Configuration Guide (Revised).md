<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Cover Page</title>
        <style>
            .cover-page {
                display: flex;
                justify-content: center;
                align-items: center;
                height: 100vh;
                text-align: center;
                flex-direction: column;
            }
            .disclaimer {
                margin-top: 40px;
                max-width: 600px;
                font-size: 0.9em;
                color: #555;
                border: 1px solid #ccc;
                padding: 20px;
                border-radius: 8px;
                text-align: left;
            }
        </style>
    </head>
<body>
    <div class="cover-page">
        <div>
            <h1>Orange Pi 5 Plus Setup & Configuration Guide</h1>
            <h3>Network Monitoring Node — Hardware Assembly, OS Configuration, Kismet & Metricbeat Integration</h3>
            <p><strong>Author: Steven Brown</strong></p>
            <p>Cybersecurity Analytics and Operations, Penn State University</p>
            <p><strong>Originally Written: 07/12/2024</strong></p>
            <p><strong>Published: 2025</strong></p>
            <div class="disclaimer">
                <strong>Public Release Notice:</strong><br><br>
                This guide was originally written as internal technical documentation during a cybersecurity internship.
                It has been reviewed and approved for public release by the original organization.
                Company-specific information including branding, personnel names, and internal IP addresses
                have been removed or replaced with generic placeholders. All technical content, steps, diagrams,
                and documentation are original work by the author.
            </div>
        </div>
    </div>
</body>
</html>

## Table of Contents:

1. [Required Tools](#required-tools)
    - [Hardware](#hardware)
    - [Software](#software)
    - [Peripherals](#peripherals)
2. [Overview](#overview)
    - [Required Tools Overview](#required-tools-overview)
    - [Assembly Overview](#assembly-overview)
    - [Startup Overview](#startup-overview)
    - [Kismet Overview](#kismet-overview)
    - [Metricbeat Overview](#metricbeat-overview)
3. [Information Flow Chart](#information-flow-chart)
4. [Assembly](#assembly)
    - [Step 1 - Install eMMC](#step-1---install-emmc)
        - [What is it?](#what-is-it)
        - [Why is an eMMC important?](#why-is-an-emmc-important)
    - [Step 2 - Install Heat Sinks](#step-2---install-heat-sinks)
        - [What are they?](#what-are-they)
        - [Why are Heat Sinks important?](#why-are-heat-sinks-important)
    - [Step 3 - Connect WiFi Card](#step-3---connect-wifi-card)
        - [What is a WiFi Card?](#what-is-a-wifi-card)
        - [Why is a WiFi Card important?](#why-is-a-wifi-card-important)
    - [Step 4 - Install NVME](#step-4---install-nvme)
        - [What is an NVME SSD?](#what-is-an-nvme-ssd)
        - [Why is an NVME SSD important?](#why-is-an-nvme-ssd-important)
    - [Step 5 - Mount Pi to Case](#step-5---mount-pi-to-case)
    - [Step 6 - Install Fan](#step-6---install-fan)
    - [Step 7 - Ensuring Continuity](#step-7---ensuring-continuity)
5. [Startup](#startup)
    - [Step 1 - Load SD Card](#step-1---load-sd-card)
    - [Step 2 - Connect Visuals](#step-2---connect-visuals)
    - [Step 3 - Connect Peripherals](#step-3---connect-peripherals)
    - [Step 4 - Connect Peripherals Part 2](#step-4---connect-peripherals-part-2)
    - [Step 5 - Add Power and Data Linkage](#step-5---add-power-and-data-linkage)
    - [Step 6 - Flash the eMMC](#step-6---flash-the-emmc)
    - [Step 7 - Power On Orange Pi 5 Plus](#step-7---power-on-orange-pi-5-plus)
    - [Step 8 - Connect ALFA WiFi Card](#step-8---connect-alfa-wifi-card)
    - [Step 9 - Assign Host Names](#step-9---assign-host-names)
6. [Kismet](#kismet)
    - [Step 1 - Kismet Server Configuration Setup](#step-1---kismet-server-configuration-setup)
    - [Step 2 - Locate Interface](#step-2---locate-interface)
    - [Step 3 - Set Aliases](#step-3---set-aliases)
    - [Step 4 - Start Kismet](#step-4---start-kismet)
    - [Step 5 - System Test](#step-5---system-test)
7. [Metricbeat](#metricbeat)
    - [Step 1 - Install Metricbeat](#step-1---install-metricbeat)
    - [Step 2 - Edit The Metricbeat Configuration File](#step-2---edit-the-metricbeat-configuration-file)
    - [Step 3 - Finalize Setup](#step-3---finalize-setup)
    - [Step 4 - Start Metricbeat](#step-4---start-metricbeat)
    - [Step 5 - Enable Service](#step-5---enable-service)
    - [Step 6 - System Test](#step-6---system-test)

<div style="page-break-after: always;"></div>

## Required Tools

### Hardware
- Orange Pi 5 Plus:
    - [Orange Pi Website](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-5-plus-32GB.html)

- 52pi Orange Pi 5 Plus Metal Case & Heat Sinks:
    - [52pi Website](https://52pi.com/products/orange-pi-5-plus-metal-protective-case-enlosure-shell-with-low-noise-cooling-fan-heatsinks)

- Orange Pi eMMC Module 256GB:
    - [Orange Pi eMMC Module Website](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-emmc.html)

- Orange Pi 5 Plus WiFi Card:
    - [Orange Pi WiFi Card Website](http://www.orangepi.org/html/hardWare/computerAndMicrocontrollers/details/Orange-Pi-R6.html)

- Samsung 990 EVO NVME M.2 SSD 2TB:
    - [Samsung 990 NVME Website](https://www.samsung.com/us/computing/memory-storage/solid-state-drives/990-evo-nvme-ssd-2tb-mz-v9e2t0b-am/)

- RevoData PoE Splitter:
    - [RevoData TypeC0504G PoE Splitter Website](https://www.amazon.com/REVODATA-5V-3A-USB-C-IEEE802-3af/dp/B0CHW5K5F4/ref=sr_1_2_sspa?crid=2WC7JLVQYQLT4&dib=eyJ2IjoiMSJ9.t88ZWfIZ8ADqze8rFv7D6w.nc2Zg7oZoKmy22p8wrbqVBOl-_MOTZs_DOrAPmCsJ-Q&dib_tag=se&keywords=revodata%2Btypec0504g&qid=1720620083&s=electronics&sprefix=revodata%2Btypec0504g%2Celectronics%2C55&sr=1-2-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)

- Nooelec RTL-SDR:
    - [Nooelec RTL-SDR Website](https://www.amazon.com/dp/B01GDN1T4S/ref=sspa_dk_hqp_detail_aax_0?psc=1&sp_csd=d2lkZ2V0TmFtZT1zcF9ocXBfc2hhcmVk)

- GlobalSat GeoPuck:
    - [GlobalSat BU-353N USB GPS Receiver Website](https://www.globalsat.com.tw/en/product-282348/USB-GPS-Receiver-BU-353N.html)

### Software
- Central Kismet Server
- ELK Stack Server
- SD Card With Operating System (Armbian):
    - Ensure that you select the Desktop version of Armbian (left option).
    - [Armbian Operating System Download Website](https://www.armbian.com/orange-pi-5-plus/)

### Peripherals:
- Monitor
- HDMI Cable
- Keyboard
- Mouse

<div style="page-break-after: always;"></div>

## Overview

### Required Tools Overview

In this section, we detail the essential hardware and software tools needed for setting up and configuring the Orange Pi 5 Plus. We cover the necessary components, such as the Orange Pi 5 Plus itself, its compatible peripherals, and the software environment required for the setup. This guide includes links to sources where you can purchase the hardware components and download the required software.

### Assembly Overview

This section provides a step-by-step guide to assembling the Orange Pi 5 Plus. From installing the eMMC module and heat sinks to connecting the WiFi card and NVME SSD, each step is described in detail with supporting images. We explain the significance of each component and offer visual aids to ensure correct installation. By following these instructions, you can ensure your Orange Pi 5 Plus is correctly assembled and ready for the startup process.

### Startup Overview

Here, we outline the procedures for powering on and configuring your Orange Pi 5 Plus for the first time. This includes loading the operating system onto an SD card, connecting peripherals, and ensuring proper power and data connections. We also cover the critical steps of flashing the eMMC, assigning hostnames, and verifying that all hardware components are functioning correctly.

### Kismet Overview

This section guides you through the configuration and setup of Kismet, a wireless network detector, sniffer, and intrusion detection system. From initial server configuration to starting data capture using WiFi and RTL-SDR interfaces, we provide detailed commands and instructions. This ensures that your Orange Pi 5 Plus can effectively monitor wireless networks and capture data for analysis.

### Metricbeat Overview

Metricbeat is used to ship metrics from the Orange Pi 5 Plus to an ELK Stack for monitoring and analysis. In this section, we provide step-by-step instructions on installing Metricbeat, configuring it to communicate with your ELK server, and ensuring it runs as a service. We also include troubleshooting tips and commands to verify that Metricbeat is correctly sending data to your monitoring setup.

<div style="page-break-after: always;"></div>

## Information Flow Chart

<div align="center">

![Information Flow Chart](images/InformationFlowChart.png)

</div>

<div style="page-break-after: always;"></div>

## Assembly

### Step 1 - Install eMMC

#### What is it?

An eMMC (embedded MultiMediaCard) is a non-volatile memory used for storage in electronic devices, including single-board computers like the Orange Pi 5 Plus.

#### Why is an eMMC important?

We are utilizing this type of storage to load and boot the contents of the SD Card. This is safer, faster, and more reliable than booting from an SD Card.

#### Connect 256GB eMMC Module to the Orange Pi motherboard:

<div align="center">

<img src="images/eMMCModuleTop.png" width="300">
<img src="images/eMMCModuleBottom.png" width="300">

</div>

- Ensure the eMMC is oriented in the correct location.
- The chipped edge should be facing in the direction of the wireless PCIe clock.
- The eMMC is installed after an audible click is made.

<div align="center">

<img src="images/eMMCLocation.png" width="400">

</div>

---

### Step 2 - Install Heat Sinks

#### What are they?

Heat sinks are devices used to dissipate heat generated by electronic components, ensuring they operate within safe temperature limits.

#### Why are Heat Sinks important?

We are utilizing these to ensure the CPU and memory components remain safe under high temperatures. This will aid in the device running smoothly.

#### Install Heat Sinks to required locations:

- The CPU requires the largest Heat Sink.
- The next two largest Heat Sinks are to be installed on the RAM.
- The last Heat Sink is to be installed on the PMU.

<div align="center">

<img src="images/HeatSinksLocation.png" width="400">
<img src="images/HeatSinks.png" width="400">

</div>

---

### Step 3 - Connect WiFi Card

#### What is a WiFi Card?

A WiFi card is a hardware component that enables a device to connect to a wireless network. It can come as an integrated component or as an add-on module that can be installed in a device.

#### Why is a WiFi Card important?

The WiFi card does not work currently; however, we are preinstalling this component with the anticipation that drivers will be released in the near future.

#### Connect the WiFi Chip to the Wi-Fi6/BT Module:

- Refer to the figure below for the install location of the Wi-Fi6/BT Module.

<div align="center">

<img src="images/WiFiCard.png" width="200">
<img src="images/WiFiLocationDiagram.png" width="400">

</div>

---

### Step 4 - Install NVME

#### What is an NVME SSD?

An NVME (Non-Volatile Memory Express) SSD is a high-speed storage device designed to take advantage of the fast data transfer speeds of the PCIe bus.

#### Why is an NVME SSD important?

Using an NVME SSD can significantly speed up the boot time and overall performance of the Orange Pi 5 Plus.

#### Install the NVME M.2 2TB SSD:

- Note: Additional M.2 screws are required. The 990 NVME M.2 2TB SSD does not include the screws.
- This is located on the back of the motherboard.

<div align="center">

<img src="images/NVME.png" width="400">
<img src="images/NVMELocationDiagram.png" width="400">

</div>

---

### Step 5 - Mount Pi to Case

#### Mount Orange Pi 5 Plus to the bottom of the Metal Case:

- Orient the motherboard so that the ports on the motherboard line up with the slots on the case.
- Use the provided silver screws to mount the board into the case.
- Refer to this [website](https://52pi.com/products/orange-pi-5-plus-metal-protective-case-enlosure-shell-with-low-noise-cooling-fan-heatsinks) for better visuals.
- Note: The fan should already be mounted on the top cover, if it's not, then follow the steps depicted in the figure below.

<div align="center">

<img src="images/CaseMount.png" width="300">

</div>

---

### Step 6 - Install Fan

#### Install and plug in the fan from the top cover of the metal case:

- There are two cables: RED and BLACK.
- The BLACK cable gets plugged into the GROUND.
- The RED cables can be plugged into either of the VCC-5V plugs.
- Refer to this [website](https://52pi.com/products/orange-pi-5-plus-metal-protective-case-enlosure-shell-with-low-noise-cooling-fan-heatsinks) for better visuals.

<div align="center">

<img src="images/FanPluginDiagram.png" width="250">
<img src="images/FanPluginLocations.png" width="250">

</div>

- Below is a completed fan plugin orientation:

<div align="center">

<img src="images/FanPluggedIn.png" width="250">

</div>

---

### Step 7 - Ensuring Continuity

- If you plan to use more than one Orange Pi node, one thing that might be useful is to label each of the nodes with the hostname. This will allow you to figure out which node is located where if issues arise.

<div style="page-break-after: always;"></div>

## Startup

### Step 1 - Load SD Card

- Plug the SD Card in the front SD Card slot reader. This is located on the side with the lights and blue USB ports.

<div align="center">

<img src="images/SDCardSlot.png" width="400">

</div>

---

### Step 2 - Connect Visuals

- Plug the HDMI cable from a monitor in either of the HDMI Out slots closest to the ethernet ports.

<div align="center">

<img src="images/HDMIPort.png" width="400">

</div>

---

### Step 3 - Connect Peripherals

- Plug the USB hub into a USB port on either side of the device.

<div align="center">

<img src="images/USBPorts.png" width="400">

</div>

---

### Step 4 - Connect Peripherals Part 2

- Connect the USB keyboard and mouse to the USB hub.

<div align="center">

<img src="images/USBHub.png" width="200">

</div>

---

### Step 5 - Add Power and Data Linkage

- Plug the ethernet cable into the PoE (Power Over Ethernet) splitter.

<div align="center">

<img src="images/PoESplitter.png" width="300">

</div>

- Plug the Type-C cable from the PoE into the Type-C 5V/4A slot.

<div align="center">

<img src="images/Type-CPower.png" width="500">

</div>

- Then plug the ethernet cable from the PoE into one of the ethernet ports next to the Type-C slot.

<div align="center">

<img src="images/EthernetPlugin.png" width="500">

</div>

- The Orange Pi should boot and display on the monitor after plugging in the Type-C cable from the PoE.

- If the Orange Pi does not boot, then power-cycle the device (If the LED is purple/pink).
    - To power cycle:
        - Unplug the PoE Type-C cable.
        - Wait about 15-30 seconds.
        - Plug the PoE Type-C back in.
- If the LED is flashing then it is reading the disk and all is good.
- To turn off the device, unplug the Type-C cable.

---

### Step 6 - Flash the eMMC

#### Open the terminal to install the Operating System onto the eMMC:

- Command:

    ```bash
    sudo nand-sata-install
    ```

- Select option #2 – Boot from eMMC – system on eMMC.

- Click Yes

- Click option #1 – ext4

    - If it says "Partition Too Small" --> go to cfdisk /dev/mmcblk0 --> delete all partitions.

- Click "Power Off" then immediately remove the SD Card.

---

### Step 7 - Power On Orange Pi 5 Plus

- To power the device back on click the button and you should see a flashing light.
- This is located on the side with the 2 (Blue) USB 3.0 ports.
- The OS should boot from the eMMC.
- Note: A user should already be created (user1).

---

### Step 8 - Connect ALFA WiFi Card:

- Connect the ALFA WiFi Card via USB 3.0 to either of the front USB ports (Blue).

- Command to check if the interface is recognized:

    ```bash
    ip a
    ```

- The interface should look something like this:

    ```bash
    wlx00**********
    ```

---

### Step 9 - Assign Host Names:

- Navigate to Settings --> System --> About.

- Change the "Device Name" to be whatever you want.

    - EX: node1

- Next, navigate to the terminal and grab the MAC Address.

    - Command:

        ```bash
        ip a
        ```

- Locate the correct ethernet interface:

    ```bash
    enP******
    ```

- Navigate to the /etc/hosts file:

    - Commands:

        ```bash
        cd /
        sudo nano /etc/hosts
        ```

    - Locate "127.0.1.1" and change "orangepi5-plus" to the new node's name.

        - Before Change:

            - orangepi5-plus

        - After Change:

            - node01

    - Locate "::1" and replace "orangepi5-plus" with the new node's name.

        - Before Change:

            ```bash
            localhost orangepi5-plus ip6-localhost ip6-loopback
            ```

        - After Change:

            ```bash
            localhost node01 ip6-localhost ip6-loopback
            ```

- Reboot to test the configuration has been set.

<div style="page-break-after: always;"></div>

## Kismet

### Step 1 - Kismet Server Configuration Setup

#### Log Into The Central Kismet Server

- Commands:

    ```bash
    ssh username@SERVERIPADDRESS
    ```

#### Navigate To The Kismet Configuration File

- Commands:

    ```bash
    cd /usr/local/etc
    sudo nano kismet.conf
    ```

- Navigate to lines #35 - #37 and edit the server_name, server_description, and server_location to your liking.

<div align="center">

<img src="images/KismetSetupStep1(1).png" width="700">

</div>

- Next, navigate to line #91 and ensure that the remote_capture_enabled is set to true. Then ensure that remote_capture_listen is = to 0.0.0.0. Finally, leave the port as is.

<div align="center">

<img src="images/KismetSetupStep1(2).png" width="700">

</div>

- Lastly, navigate to line #133 and add the following command under the comment:

    - Ensure that you change the "IPAddress" to a static IP for easy tracking in the future.

<div align="center">

<img src="images/KismetSetupStep1(3).png" width="700">

</div>

- Note: Static IP addresses should be assigned to each node for reliable tracking within the network.

---

### Step 2 - Locate Interface

#### Determine The Correct Interface For WiFi Capture & RTL-SDR Capture

- On the Orange Pi 5 Plus node navigate to the terminal and type the following command:
    - Command:

        ```bash
        ip a
        ```

- Locate either the WiFi capture interface or the RTL-SDR interface.

---

### Step 3 - Set Aliases

#### Set Aliases For Kismet Capture Types On The Orange Pi 5 Plus Node

- Alias the commands for WiFi or RTL-SDR as "kismetwificap" and "kismetdrcap":

    - Commands:
        - Setup command for WiFi capture using an ALFA WiFi Card:

            ```bash
            alias kismetwificap='kismet_cap_linux_wifi --connect IP ADDRESS OF KISMET SERVER:PORT --tcp --source wlx00********** &'
            ```

        - Setup command for RTL-SDR capture using a Nooelec RTL-SDR:

            ```bash
            alias kismetdrcap='kismet_cap_sdr_rtl433 --tcp --connect IP ADDRESS OF KISMET SERVER:PORT --source rtl***-* &'
            ```

        - If you want to start Kismet and keep it running even if the shell is closed, add "nohup" to the beginning of the alias's:

            - WiFi Capture:

                <br>
                <br>
                <br>
                <br>

                ```bash
                alias kismetwificap='nohup kismet_cap_linux_wifi --connect IP ADDRESS OF KISMET SERVER:PORT --tcp --source wlx00********** &'
                ```

            - RTL-SDR:

                ```bash
                alias kismetdrcap='nohup kismet_cap_sdr_rtl433 --tcp --connect IP ADDRESS OF KISMET SERVER:PORT --source rtl***-* &'
                ```

        - If ever you need to change the alias, this is located in the .bashrc file under the home directory:

            ```bash
            cd ~
            sudo nano .bashrc
            ```

    - Note: The source for the wificap changes based on the MAC Address of the wireless card.

- Next, type the following command to create a new shell instance with the updated .bashrc file:

    ```bash
    bash
    ```

---

### Step 4 - Start Kismet

- Command to start WiFi capture:

    ```bash
    kismetwificap
    ```

- Command to start RTL-SDR capture:

    ```bash
    kismetdrcap
    ```

---

### Step 5 - System Test

- Navigate to your Kismet web interface.
- Select hamburger menu on the left hand side.
- Navigate to Data Sources.
- You should see the interface for the service you are running.
    - EX: WiFi capture interface (wlx00**********)
    - EX: RTL-SDR capture interface (rtl***-*)

<div style="page-break-after: always;"></div>

## Metricbeat

### Step 1 - Install Metricbeat

- Command to install Metricbeat on the Orange Pi:

    ```bash
    curl -L -0 https://artifacts.elastic.co/downloads/beats/metricbeat/metricbeat-8.14.1-arm64.deb
    sudo dpkg -i metricbeat-8.14.1-arm64.deb
    ```

- Note: The Metricbeat download version (8.14.1) should be the same as your ELK Stack version.

---

### Step 2 - Edit The Metricbeat Configuration File

- Navigate to the Metricbeat configuration file:

    ```bash
    sudo nano /etc/metricbeat/metricbeat.yml
    ```

- Under setup.kibana in the Kibana section, uncomment and change the command below:

    - Before Change:

        ```bash
        host: "localhost:5601"
        ```

    - After Change:

        ```bash
        host: "ELKSERVERIPADDRESS:5601"
        ```

- Under output.elasticsearch in the Outputs section, change hosts:

    - Before Change:

        ```bash
        host: ["localhost:9200"]
        ```

    - After Change:

        ```bash
        host: ["ELKSERVERIPADDRESS:9200"]
        ```

- Next, uncomment the following line:

    ```bash
    protol: "https"
    ```

- Uncomment the following lines after the "# Authentication credentials":

    ```bash
    username: "ELKWEBINTERFACEUSERNAME"
    password: "ELKWEBINTERFACEPASSWORD"
    ```

- Add the following lines after the previously uncommented lines:

    ```bash
    ssl.verification_mode: "none"
    ```

---

### Step 3 - Finalize Setup

- To finish the setup:

    ```bash
    sudo metricbeat setup -e
    ```

---

### Step 4 - Start Metricbeat

- To start metricbeat:

    ```bash
    sudo service metricbeat start
    ```

---

### Step 5 - Enable Service

- To enable the Metricbeat service, run the following command:

    ```bash
    sudo systemctl enable metricbeat
    ```

---

### Step 6 - System Test

- Navigate to your Kibana web interface.
- Select observability.
- The node host-name should appear in the "Hosts" dropdown menu if everything was done correctly.

---

## Author

**Steven Brown**
Cybersecurity Analytics and Operations, Penn State University
[LinkedIn](https://www.linkedin.com/in/steven-b-4a699b218) | [Portfolio](https://stevenrbrown.org) | [GitHub](https://github.com/Steven6Brown)