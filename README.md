Sensor calendar on Home Assistant  
Author: exlab247  
Date 24 Mar, 2020  
~----------------~

Attributes of sensor:  
```
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
 ```   

### Automation code for TTS:


    
