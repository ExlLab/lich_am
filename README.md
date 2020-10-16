Sensor calendar on Home Assistant
Author: exlab247@gmail.com
Date 24 Mar, 2020 version 1.0
Date 16 Oct, 2020 version 2.0 
~----------------~

Attributes of sensor:  
```
lichAm:	        Ngày lịch âm
NgayRam:	Ngày Rằm lịch âm
MungMot:	Ngày mùng một lịch âm
TetNguyenDan:	Tết Nguyên Đán
TetNguyentieu:	Tết Nguyên tiêu
TetHanthuc:	Tết Hàn thực
GiotoHungVuong:	Giỗ Tổ Hùng Vương
LePhatDan:	Lễ Phật Đản
TetDoanngo:	Tết Đoan ngọ
LeVuLan:	Lễ Vu Lan
TetTrungthu:	Tết Trung thu
Ongtaochautroi:	Ông Táo chầu trời
TetDuonglich:	Tết Dương lịch
HocsinhSinhvien: Ngày Học sinh - Sinh viên Việt Nam
ThanhlapDang:	Ngày thành lập Đảng Cộng sản Việt Nam
ThaythuocVN:	Ngày Thầy thuốc Việt Nam
QuoctePhunu:	Ngày Quốc tế Phụ nữ
ThanhlapDoan:	Ngày thành lập Đoàn Thanh niên Cộng sản Hồ Chí Minh
SachVN:	        Ngày Sách Việt Nam
Giaiphong:	Ngày Thống nhất đất nước
QuocteLaodong:	Ngày Quốc tế Lao động
ThanhlapDoi:	Ngày thành lập Đội Thiếu niên Tiền phong Hồ Chí Minh
NgaysinhBacHo:	Ngày sinh của Chủ tịch Hồ Chí Minh
QuocteThieunhi:	Ngày Quốc tế Thiếu nhi
ThuongbinhLietsi: Ngày Thương binh Liệt sĩ
CachmangThang8:	Ngày Cách mạng tháng Tám thành công
Quockhanh:	Ngày Quốc khánh
DoanhnhanVN:	Ngày Doanh nhân Việt Nam
PhunuVN:	Ngày thành lập Hội Phụ nữ Việt Nam
NhagiaoVN:	Ngày Nhà giáo Việt Nam
QuandoiVN:	Ngày thành lập Quân đội Nhân dân Việt Nam
Giangsinh:	Ngày Lễ Giáng Sinh
### [ddMM]AL: Toàn bộ ngày âm lịch 
```

### Config sensor:
```
#sensor:
- platform: rest  
  name: "Lunar Exlab"
  resource: https://raw.githubusercontent.com/ExlLab/lich_am/master/sensor.json
  value_template: '{{ value_json.lichAm }}'
  force_update: true
  json_attributes:
    - NgayRam
    - MungMot
    - TetNguyenDan
    - TetNguyentieu
    - 1010AL
 ```   

### Automation code for TTS:
```
- alias: thông báo rằm
  trigger:
    platform: time
    at: '20:00:00'
  condition:
    condition: template
    value_template: '{{ state_attr("sensor.lunar_exlab", "NgayRam")|int == 1 }}'    
  action:
    - service: tts.google_say
      entity_id: media_player.room_speaker
      data:
        message: "Ngày mai là rằm."
```
```
- alias: thông báo mùng một
  trigger:
    platform: time
    at: '20:00:00'
  condition:
    condition: template
    value_template: '{{ state_attr("sensor.lunar_exlab", "MungMot")|int == 1 }}'    
  action:
    - service: tts.google_say
      entity_id: media_player.room_speaker
      data:
        message: "Ngày mai là mùng một."
```
```
- alias: thông báo ngay kỷ niệm
  trigger:
    platform: time
    at: '20:00:00'
  condition:
    condition: template
    value_template: '{{ state_attr("sensor.lunar_exlab", "1010AL")|int == 1 }}'    
  action:
    - service: tts.google_say
      entity_id: media_player.room_speaker
      data:
        message: "Ngày mai là ngày kỷ niệm xyz."
```
    
