# Technical Specification

Pebble is a battery-powered, cellular-based, multi-sensor **development board** designed by IoTeX and [Nordic Semiconductor](https://www.nordicsemi.com/), combining tamper-proof hardware and tamper-proof software to generate verifiable data.

Pebble is equipped with high-quality **GPS**, **climate**, **motion**, and **light** sensors. Data can be easily streamed in real-time to an MQTT endpoint for use in Cloud or blockchain-based applications.

Pebble utilizes a **secure element** \(nRF9160\) to cryptographically sign all data, providing unparalleled verifiability and traceability for asset tracking, supply chain, and other applications.

### Processor <a id="processor"></a>

Pebble is powered by a 64 MHz Arm® Cortex®-M33, 1 MB Flash and 256 KB RAM, with automated power and clock management, Arm TrustZone, and Arm CryptoCell 310

### Integrated Sensors <a id="integrated-sensors"></a>

Pebble combines an **environmental sensor** \(temperature, relative humidity, barometric pressure, altitude, and volatile organic compounds - VOCs\), a **motion sensor** \(3-axis gyroscope, 3-axis accelerometer\), and an ambient **light sensor**. It's also equipped with cellular network connectivity and integrated GPS supporting precise, long range tracking of asset data using established cellular infrastructure.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Sensor</th>
      <th style="text-align:left">Details</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="https://www.bosch-sensortec.com/products/environmental-sensors/gas-sensors-bme680/">Environmental Sensor BME680</a>
      </td>
      <td style="text-align:left">
        <p>Relative humidity</p>
        <p>Barometric pressure</p>
        <p>Ambient temperature</p>
        <p>Air quality (VOC)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://www.invensense.com/products/motion-tracking/6-axis/icm-42605/">Motion Sensor ICM-42605</a>
      </td>
      <td style="text-align:left">
        <p>3-axis gyroscope</p>
        <p>3-axis accelerometer</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="http://www.techtotop.com/detail.aspx?cid=956">External GPS TD1030</a>
      </td>
      <td style="text-align:left">
        <p>Position accuracy: 3m</p>
        <p>Speed accuracy: 0.1 m/s</p>
        <p>Data frequency: 1 hz to 10 Hz</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://ams.com/tsl25721">Ambient Light Sensor AMS TSL2572</a>
      </td>
      <td style="text-align:left">
        <p>45,000,000:1 Dynamic Range</p>
        <p>Operation to 60,000 lux in Sunlight</p>
        <p>Very High Sensitivity</p>
        <p>Package UV Rejection Filter</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://www.mallory-sonalert.com/DetailPage.aspx?Catalog_Number=AST7525MATRQ&amp;Part_Id=452">Buzzer Mallory Sonalert AST7525MATRQ</a>
      </td>
      <td style="text-align:left">
        <p>Frequency: 2700 Hz</p>
        <p>Sound Pressure Level (dB/min): 85 at 10cm</p>
      </td>
    </tr>
  </tbody>
</table>

### Network Connectivity <a id="network-connectivity"></a>

Pebble includes a Multimode LTE-M/NB-IoT modem for cellular communication. To have your Pebble connected to the Internet you will need an _I_oT-enabled\*\* SIM card that supports either NB-IoT or LTE standards.

### Data format <a id="data-format"></a>

JavaScript Object Notation \(JSON\) is utilized to represent the sensor data collected by a Pebble as well as the corresponding ECDSA digital signature. Pebble utilizes ECDSA over the elliptic curve `sepc256r1` to sign the collected sensor data \(i.e., the _message_ field in the Pebble data format\)

Supported data types include _Number_, _String_ and _Array_ defined as follows:

| Data Type | Data Size | Data Range |
| :--- | :--- | :--- |
| Array | 16-bit | -32768 ~ +32768 |
| Number | 64-bit | -1.79E+308 ~ +1.79E+308 |
| String | null-terminated string |  |

An example of a JSON object containing a data point collected by the Pebble is shown below, it consists of a sensor data object named _"message"_, and a digital signature data object named _"signature"_:

```javascript
{
	message: {
		SNR: 2,
		VBAT: 4.0750732421875,
		latitude: 3050.69225,
		longitude: 11448.65815,
		gas\_resistance: 1166811,
		temperature: 36.23188400268555,
		pressure: 1003.82000732421885,
		humidity: 55.755001068115234,
		gyroscope: [-12, 11, 14],
		accelerometer: [-711, -231, 8260],
		timestamp: 3443547577,
    random: "3767398368",
    rsa_n: "0xa709e2f84ac0e21eb0caa018cf7f697...8f628698f0c7b420c4b7",
    rsa_e: "0x010001"
	},

	signature:  {
		r: "D7797968EAA3FFE5F8057C9D97F707A4A96CBFC250115FE6293EBA5E90327174",
		s: "643A8CB823110376A5D30201463CF69CDF8CBF1C050EB85B023CABFB589C3222"
	}
}
```

The _message_ object includes the following sensor data:

| Sensor Data | Data Type | Description |
| :--- | :--- | :--- |
| SNR | Number | Signal-to-noise ratio of NB-IoT/LET-M |
| VBAT | Number | Voltage of battery |
| latitude | Number | gps latitude |
| longitude | Number | gps longitude |
| gas\_resistance | Number | Air quality |
| temperature | Number | Environmental temperature |
| pressure | Number | Air pressure |
| humidity | Number | Environmental humidity |
| gyroscope | Array | Angular velocity around the X-axis, Y-axis and Z-axis |
| accelerometer | Array | Acceleration along the X-axis, Y-axis and Z-axis |
| timestamp | String | Timestamp of sensor data sampling |

The _signature_ data object contains the following signature data:

| Digital Signature | Data Type | Description |
| :--- | :--- | :--- |
| r | Number | r value of an ECDSA signature |
| s | Number | s value of an ECDSA signature |

### Onboard RGB Led <a id="onboard-rgb-led"></a>

Pebble includes an RGB led to show the status of the Pebble, the table below shows all the possible led states and the respective meaning:

| LED Color \(Blink Rate\) | GPS Signal | Charging | NB-IoT/LTE Connection | Flashing the Firmware |
| :--- | :--- | :--- | :--- | :--- |
| Blue \(fast\) |  |  |  |  |
| Blue \(slow\) |  |  | ✓ |  |
| Red \(steady\) + Purple \(fast\) |  | ✓ |  |  |
| Red \(steady\) + Purple \(slow\) |  | ✓ | ✓ |  |
| Cyan \(fast\) | ✓ |  |  |  |
| Cyan \(slow\) | ✓ |  | ✓ |  |
| Red \(steady\) + White \(fast\) | ✓ | ✓ |  |  |
| Red \(steady\) + White \(slow\) | ✓ | ✓ | ✓ |  |
| Red \(fast\) |  |  |  | ✓ |

Note that the led will blink at least twice in 1 second when in _fast_ mode, and once in 5 seconds when in _slow_ mode.

### 2D Drawing <a id="_2d-drawing"></a>

![](../../.gitbook/assets/pebble-drawing.jpg)

{% file src="../../.gitbook/assets/pebble-drawing.pdf" caption="2D Drawing \| PDF" %}

{% file src="../../.gitbook/assets/pebble-top-view.dxf" caption="2D Drawing \| DXF" %}



