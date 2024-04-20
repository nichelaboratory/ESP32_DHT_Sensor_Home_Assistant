# ESP32_DHT_Sensor_Home_Assistant
 Send sensor data from ESP32 to Home Assistant via MQTT Broker
 
 Here's how to connect an ESP32 to Home Assistant and send realtime sensor data to Home Assistant over wifi. The code will also work with the ESP8266 with minimal modifications. Be warned there's something wrong with my hardware setup, but the data sending process itself works flawlessly.
 
Full code walkthrough in this video:
 
[![ESP32 Send Temperature Data to Home Assistant](https://img.youtube.com/vi/9zwToQm98Vg/0.jpg)](https://www.youtube.com/watch?v=9zwToQm98Vg)
 
Click on the image above to watch the video or go here: https://youtu.be/9zwToQm98Vg 
 
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
        
