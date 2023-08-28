# MQTT Topic and Message Documentation
| Message      | Topic Root         | Sub-Topic A   | Sub-Topic B     | Sub-Topic C | example topic                      | Message Description                                                                                                               |   | field_0      | field_1      | field_2          | field_3 |   |   | Notes                                                                                                                                                                                                                                                                                                                                                                                        |
|--------------|--------------------|---------------|-----------------|-------------|------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|---|--------------|--------------|------------------|---------|---|---|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|              |                    |               |                 |             |                                    |                                                                                                                                   |   |              |              |                  |         |   |   |                                                                                                                                                                                                                                                                                                                                                                                              |
| VWC          | brand_sensorModel/ | sensor_depth/ | data_gator_mac/ |             | meter_teros10/0_shallow/ac34552982 | Sends a single sensor reading with the address of the aggregator that sent it.                                                    | { | MAC          | VWC          | VWC_RAW          | DEPTH   | } |   | MAC is the address of the datagator that sent the message. VWC  is a measurement which is derived from the voltage represented in the VWC Raw field. Depth is the relative depth at which the sensor was burried.                                                                                                                                                                            |
| HT           | brand_sensorModel/ | sensor_mac/   |                 |             | minew_s1/mc3849:3498               | Sends the temperature and humidity plus the MAC of the sensor and the aggregator that sent the data.                              | { | MAC          | GATOR_MAC    | HUMIDITY         | TEMP    | } |   | MAC is the address of the sensor that collected the data. Gator MAC  is the datagator which polled the sensor and reported the data. Humidity is the relative humidity(%). Temp is the temperature reported by the sensor in degrees Celsius.                                                                                                                                                |
| Gator TLM    | datagator/         | tlm/          | data_gator_mac/ |             | datagator/tlm/ac34552982           | Sends telemetry data for the aggregator including battery voltage and whatever other data we might want.                          | { | MAC          | BATT_VOLTAGE | FIRMWARE_VERSION |         | } |   | MAC is the address of the datagator that sent the message. BATT_VOLTAGE is a measurement of the battery voltage of the battery connected to the datagator. Firmware version is the version/support capability indicator and can be used to look up what sensors are compatible with this device.                                                                                             |
| PH           | brand_sensorModel/ | pH/           | data_gator_mac/ |             | generic_pH/pH/ac293829             | Send the soil pH measurement data.                                                                                                | { | MAC          | PH           | PH_RAW           |         | } |   | MAC is the address of the datagator that sent the message. PH is a measurement which is derived from the voltage represented in the PH Raw field.                                                                                                                                                                                                                                            |
|              |                    |               |                 |             |                                    |                                                                                                                                   |   |              |              |                  |         |   |   |                                                                                                                                                                                                                                                                                                                                                                                              |
| Data Request | datagator/         | get_data/     | data_gator_mac/ |             | datagator/get_data/ac293829        | Retrieve data logged by the Datagator's SD card by time range. Page size and topic filter have default values but can be changed. | { | PAGE_SIZE=50 | TIME_RANGE   | TOPIC_FILTER=""  |         | } |   | Default page size is the number of timestamped entries to pull from a file before publishing with MQTT. Topic filter is a white list filter, where "" matches everything. Otherwise only entries whose topic starts with a topic filter entry will be accepted. Time range should be of the form "<timestamp>-<timestamp>" where only data collected between the two timestamps is returned. |