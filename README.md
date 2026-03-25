#  IoT Monitoring System with Socket, MQTT, and Grafana

This project implements a **real-time IoT monitoring system** that simulates environmental sensor data 
(temperature) and visualizes it using a dashboard.

The system consists of:

* **Laptop 1 (Sensor Simulator)**
  Generates sensor data and sends it via a TCP socket.

* **Laptop 2 (Edge Device)**
  Receives socket data and forwards it to an MQTT broker.

* **MQTT Broker**
  Handles message distribution between publisher and subscribers.

* **Grafana Dashboard**
  Displays the data in real-time for monitoring.

---

##  2. Socket Data Flow (Laptop 1 → Laptop 2)

1. Laptop 1 generates sensor values:

   * Temperature

2. Laptop 2:

   * Receives the message
   * Splits the values
   * Converts them into JSON
   * Publishes to MQTT

---

##  3. MQTT Configuration

###  Topic Used

```text
savonia/Yetunde/sensors
```

### Message Format (JSON)

```json
{
  "temperature": 25.4,
}
```


##  4. MQTT Broker Used

* Public broker: **EMQX Broker**

```text
broker.emqx.io
```

* Port: `1883`
* Protocol: MQTT (TCP)

---



##  6. Dashboard Explanation

The Grafana dashboard displays real-time sensor data using panels such as:

* **Temperature Panel**
  Shows current temperature values in °C


###  What the Panel Shows

* Live updates of incoming MQTT data
* Trends of sensor values over time (if stored)
* Easy visualization for monitoring environmental conditions

---

##  7. Limitation of Live-Only MQTT Visualization

MQTT by itself is **not designed for data storage**, only for message delivery.

### Key limitations:

* ❌ No historical data
* ❌ No data persistence
* ❌ Cannot analyze past trends
* ❌ Data is lost if subscriber is offline

 This means Grafana can only show:

* **Live data (real-time)**
* NOT **past data**, unless integrated with a database (e.g., InfluxDB)

---

#  Reflection Questions

---

##  What is the role of Grafana in this system?

Grafana is used as a **visualization and monitoring tool**.

### Its role:

* Converts raw MQTT data into **interactive dashboards**
* Displays sensor data in **graphs, gauges, and charts**
* Enables **real-time monitoring**
* Improves understanding of system behavior

 In short:
**Grafana turns data into meaningful visual insights.**

---

##  Why is MQTT useful for monitoring applications?

MQTT is ideal for monitoring systems because:

###  Advantages:

* Lightweight (low bandwidth usage)
* Fast and efficient communication
* Works well with IoT devices
* Supports **publish/subscribe model**
* Enables **real-time data streaming**


##  What is the difference between live monitoring and historical storage?

###  Live Monitoring

* Shows **real-time data only**
* No data saved
* Example: current temperature reading

###  Historical Storage

* Stores data over time in a database
* Enables:

  * Trend analysis
  * Reports
  * Predictions

---

###  Key Difference

| Feature           | Live Monitoring | Historical Storage |
| ----------------- | --------------- | ------------------ |
| Data Availability | Present only    | Past + Present     |
| Storage           | ❌ No            | ✅ Yes              |
| Analysis          | Limited         | Advanced           |
| Example Tools     | MQTT            | InfluxDB, SQL      |



###  Conclusion

* MQTT → **real-time communication**
* Database → **long-term storage**
* Grafana → **visualization layer**


#  Final Summary

This project demonstrates how to build a **complete IoT pipeline**:

**Sensor → Socket → MQTT → Dashboard**

It highlights:

* Real-time communication using MQTT
* Edge processing with sockets
* Visualization using Grafana



