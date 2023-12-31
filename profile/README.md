# Data Gator

Welcome to the home of the Data Gator! This organization hosts the hardware design files, firmware, and documentation for each. Check out the table of contents below for quick links
to helpful information!


| Link | Description |
| :---: | :---: | 
| [data-gator.github.io](https://data-gator.github.io) | Main documentation, go here! | 
| [Data Gator Firmware + User/Dev Docs](https://github.com/Data-Gator/data-gator) | Source code, firmware releases, and documentation for users/developers. |
| [Doxygen Firmware Documentation](https://data-gator.github.io/doxygen_firmware_docs/) | Documents firmware API and configuration variables used in production firmware. |
| [Hardware Documentation](https://data-gator.github.io/Hardware)| Documents hardware components, manufacturing, and assembly process. Also has design files. |


# What is a Data Gator?

The Data Gator is an embedded system solution for wireless sensor integration and network extension. It is a custom PCB with an ESP32, uSD card holder, and various ports for sensors. In the diagram below, DGs serve as [_**Aggregators**_](https://github.com/Project-VineHeart/scarecro#aggregator), collecting data from sensors and relaying it to [_**Gateways**_](https://github.com/Project-VineHeart/scarecro#gateway) which store the data in a cloud database. From there the data is available to the user.

![SCARECRO System Architecture](/profile/images/diagram_overview.png)

