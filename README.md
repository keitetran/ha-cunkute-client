# App HASS mobile

- Giao diện trực quan, đơn giản hơn.
- Tốc độ load trang nhanh hơn
- Hỗ trợ cho router không support loopback
- Không lưu lại password vào server

# Hướng dẫn cài đặt

1. Cài đặt phía hass

- Thêm password vào
- Thêm domain vào http component, để cho phép domain truy cập vào hass
- Yêu cầu hass phải có https, nếu chưa có thì cài theo hướng dẫn của hass trên trang chủ

```yaml
http:
  api_password: xxxxxxxx
  cors_allowed_origins:
    - https://myhomeiot-184105.firebaseapp.com
```

2. Chỉnh sửa file json để custom giao diện app

## Cấu hình chung cho app

<p align="center">
  <img src="https://cdn.realtor.ca/listing/TS636668615669600000/reb93/highres/9/1117099_2.jpg"  alt="accessibility text">
</p>

```json
"system": {
  "name": "Nhà của Cún Kute",
  "language": "vn-VI",
  "debug": false,
  "tempUnit": "°C",
  "colors": {
    "header": "#000",
    "switch": ""
  }
},
```

## Cấu hình cho yahoo widget

Có thể tìm code cho yahoo tại trang

```json
"yahoo": {
  "code": 1117099,
  "cityName": "Fukuoka",
  "tempUnit": "C"
},
```

## Cấu hình nút phía trên cùng của app

Set biến show bằng false nếu muốn ẩn, true nếu muốn hiện

```json
"topButton": {
  "name": "Top Button",
  "show": false,
  "buttons": [{
    "name": "Temperature",
    "icon": "wi wi-thermometer",
    "entity": "sensor.living_room_temperature"
  }, {
    "name": "Humidity",
    "icon": "wi wi-humidity",
    "entity": "sensor.living_room_humidity"
  }, {
    "name": "Air Quantity",
    "icon": "fab fa-cloudversify",
    "entity": "sensor.us_air_quality_index"
  }, {
    "name": "Air Pollution Level",
    "icon": "fab fa-hornbill",
    "entity": "sensor.us_air_pollution_level"
  }, {
    "name": "Air Main Pollutant",
    "icon": "far fa-meh-rolling-eyes",
    "entity": "sensor.us_main_pollutant"
  }, {
    "name": "Season",
    "icon": "wi wi-day-cloudy",
    "entity": "sensor.season"
  }]
},
```

## Cấu hình danh sách device bắt đầu từ dòng devices

```json
{
  "name": "Home Assistant",
  "component": "homeAssistant",
  "network": [
    {
      "name": "Upload",
      "icon": "mdi mdi-upload-network",
      "entity": "sensor.speedtest_upload"
    },
    {
      "name": "Download",
      "icon": "mdi mdi-download-network",
      "entity": "sensor.speedtest_download"
    }
  ],
  "listDetail": [
    {
      "name": "IPv4",
      "icon": "mdi mdi-counter",
      "entity": "sensor.ipv4_address_wlan0"
    },
    {
      "name": "PING",
      "icon": "mdi mdi-access-point-network",
      "entity": "sensor.speedtest_ping"
    },
    {
      "name": "Lastboot",
      "icon": "mdi mdi-power-settings",
      "entity": "sensor.last_boot"
    },
    {
      "name": "CPU usage",
      "icon": "mdi mdi-chip",
      "entity": "sensor.processor_use"
    },
    {
      "name": "CPU temp",
      "icon": "mdi mdi-oil-temperature",
      "entity": "sensor.processor_temperature"
    },
    {
      "name": "Memory",
      "icon": "mdi mdi-memory",
      "entity": "sensor.memory_use_percent"
    },
    {
      "name": "HDD usage",
      "icon": "mdi mdi-harddisk",
      "entity": "sensor.disk_use_percent_"
    },
    {
      "name": "Nhiệt độ",
      "icon": "wi wi-thermometer",
      "entity": "sensor.living_room_temperature"
    },
    {
      "name": "SSL cert expiry",
      "icon": "mdi mdi-certificate",
      "entity": "sensor.ssl_cert_expiry"
    },
    {
      "name": "Độ ẩm",
      "icon": "wi wi-humidity",
      "entity": "sensor.living_room_humidity"
    }
  ],
  "booleanButton": [
    {
      "name": "RA KHỎI NHÀ",
      "icon": "mdi mdi-home-lock",
      "entity": "input_boolean.system_go_out_mode"
    },
    {
      "name": "THÔNG BÁO BẰNG ÂM THANH",
      "icon": "mdi mdi-voice",
      "entity": "input_boolean.information_messages"
    },
    {
      "name": "ĐI NGỦ",
      "icon": "mdi mdi-hotel",
      "entity": "input_boolean.system_sleep_mode"
    }
  ]
}
```
