### 1. Description
The Rideau Canal Skateway, a historic attraction in Ottawa, requires constant monitoring to ensure skater safety. Our team has been commissioned by the National Capital Commission (NCC) to create a real-time monitoring system that tracks vital weather and ice conditions using Internet of Things (IoT) sensors, giving actionable insights to identify dangerous skating conditions.

The three main locations—Dow's Lake, Fifth Avenue, and NAC—are used by this system to mimic Internet of Things sensors that produce data on ice thickness, surface temperature, snow accumulation, and external temperature. Azure IoT Hub and Azure Stream Analytics are used to process the data in real time, while Azure Blob Storage is used to store the data for analysis and reporting.

### 2. System Architecture
The following diagram illustrates the architecture and data flow:

1. IoT Sensors simulate and send JSON payloads every 10 seconds to Azure IoT Hub.
   
2. Azure IoT Hub ingests real-time sensor data.

3. Azure Stream Analytics processes the data, performing aggregations over a 5-minute window.
   
4. Processed data is output to Azure Blob Storage for storage and analys

### 3. Architecture Diagram
![image](https://github.com/user-attachments/assets/a2cffdff-1724-4e72-b364-571ffc1ea57e)

### 4. Implementation Details

#### 1. IOT Sesnor Simulation
The simulated IoT sensors are actual equipment positioned at three strategic points along the Rideau Canal Skateway: the NAC, Fifth Avenue, and Dow's Lake. These sensors are intended to keep an eye on important ice-related and environmental parameters, protecting skaters.

### How It Works:
1. Data Generation: For every metric, the script produces a random value within a plausible range.
   
2. Payload Creation: A JSON payload is created by packaging data.
   
3. Transmission: The IoTHubDeviceClient is used to send the payload to Azure IoT Hub.
   
4. Continuous Data Flow: New data is pushed every ten seconds as the script runs endlessly.

### IOT Hub Configuration
1. Device Registration with Device id (dows_lake, fifth_avenue, nac_sensors)

2. Connection string to send the data

3. Message routing for downstream processing.

### OutCome
Real-time data is received by the IoT Hub, processed by Azure Stream Analytics, aggregated, and stored in Azure Blob Storage.
