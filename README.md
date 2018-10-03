# App HASS mobile
- Change log https://github.com/keitetran/ha-cunkute-client/wiki/Change-log
- Giao diện trực quan, đơn giản hơn.
- Tốc độ load trang nhanh hơn
- Hỗ trợ cho router không support loopback
- Không lưu lại password vào server
- Hướng dẫn chưa được đầy đủ vì mình bận quá. BÁc nào có thể viết thay mình xong commit lên mình sẽ gộp lại cho :D Chân thành cảm ơn bác luôn đó. 
# Đường dẫn UI 
https://myhomeiot-184105.firebaseapp.com

# Hỗ trợ
- AC, TV, Audio system component chỉ hỗ trợ Climate component
- Hẹn giờ tắt bật trong AC, các nút chức năng khác thì thêm component input_boolean xong viết automation cho nó
- Support webapp trên mobile, goolge tìm cách đưa 1 webapp ra màn hình thì sẽ được như hình dưới
- Thêm nhiều component giống nhau nếu muốn bằng cách không thay đổi đoạn code này 
```json
"component": "room",
```
- Hiện tại hỗ trợ các component sau
```json
homeAssistant
light
room
aircon
mediaPlayer
vacuumCleaner
computer
fan
camera
```
# Hướng dẫn cài đặt

## Cài đặt phía hass

- Thêm password vào
- Thêm domain vào http component, để cho phép domain truy cập vào hass
- Yêu cầu hass phải có https, nếu chưa có thì cài theo hướng dẫn của hass trên trang chủ

```yaml
http:
  api_password: xxxxxxxx
  cors_allowed_origins:
    - https://myhomeiot-184105.firebaseapp.com
```

## Cấu hình chung cho app

- Nếu modem không hộ trợ loopback thì không nên download file config.json về thư mục www của hass. Up lên github sau đó copy link RAW (không dc copy link html của file). File pải đúng định dạng json nếu ko sẽ lỗi json không thể load file json.
- Có thể nhập 2 đường dẫn Online và local giống nhau nếu có loopback.
- Không lưu lại pass ở server nên cứ thoải mái dùng :D không tin cứ check thử :D
- Xóa những entity không có trong hass ở json đi vì có thể phát sinh lỗi ko mong muốn
- Sai ở đâu sẽ ko hiện component đó nên quay lại chỗ đó check lại entity xem đúng như trong hass chưa
  <p align="center">
    <img src="https://raw.githubusercontent.com/keitetran/ha-cunkute-client/master/img/myhomeiot-184105.firebaseapp.com_(iPhone%206_7_8)%20(1).png"  style="width:50%; float:left;" alt="accessibility text">
     <img src="https://raw.githubusercontent.com/keitetran/ha-cunkute-client/master/img/myhomeiot-184105.firebaseapp.com_(iPhone%206_7_8).png"  style="width:50%" alt="accessibility text">
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

## Component homeAssistant

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
