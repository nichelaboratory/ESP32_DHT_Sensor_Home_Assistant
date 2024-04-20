# ESP32_DHT_Sensor_Home_Assistant
 Send sensor data from ESP32 to Home Assistant via MQTT Broker
 
 This is the configuration.yaml file I've used to configure the DHT22/11 sensors so they send both temperature and humidity data to Home Assistant via a MQTT Broker:

```  
 # Loads default set of integrations. Do not remove.
 default_config:
 
 # Load frontend themes from the themes folder
 frontend:
   themes: !include_dir_merge_named themes
 
 automation: !include automations.yaml
 script: !include scripts.yaml
 scene: !include scenes.yaml
 
 mqtt:
     sensor:
     -   state_topic: "DHT22/01"
         name: "DHT22.HumiditySensor"
         unique_id: DHT22.Humidity
         value_template: "{{ value_json.humidity }}"
 
     -   state_topic: "DHT22/01"
         name: "DHT22.TemperatureSensor"
         unique_id: DHT22.Temperature
        value_template: "{{ value_json.temperature }}"
```        
        
