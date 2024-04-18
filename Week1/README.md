## สรุปการเรียนในสัปดาหืที่ 1

- ### ไฟร์วอล: Fortigate 60e

<div align="center">

![Fortigate 60e](https://cdn.discordapp.com/attachments/1059148519992197251/1230376509089517568/68747470733a2f2f696d67352e7069632e696e2e74682f66696c652f7365637572652d7376312f53637265656e73686f742d323032342d30342d30362d3139353931332e706e67.png?ex=6633186b&is=6620a36b&hm=3b8b4d2ca5844212b29d6b8912c27550ded0dac75fe535ec68104f05e1e4cc18&)

-- [Datasheet Firewall] --

[Datasheet Firewall]: https://www.firewalls.com/pub/media/wysiwyg/datasheets/Fortinet/FG-FW-60E.pdf

</div>

# วิธีการกำหนดค่าให้กับไฟร์วอล
### 1. เชื่อมต่อเข้าสู่ไฟร์วอล:
* เชื่อมต่อ PC/Notebook เข้ากับไฟร์วอลผ่านพอร์ตใดก็ได้จาก 1 ถึง 7
* เปิดเบราว์เซอร์และไปที่: https://192.168.1.99/ (Default IP Address)
* เข้าสู่ระบบด้วย Username: admin (ไม่ต้องใส่รหัสผ่าน)

![img_fwlogin](https://cdn.discordapp.com/attachments/1059148519992197251/1230377316270473288/68747470733a2f2f696d67352e7069632e696e2e74682f66696c652f7365637572652d7376312f53637265656e73686f742d323032342d30342d30362d3233343332372e706e67.png?ex=6633192b&is=6620a42b&hm=e645cdc854170db3514d2f6932b733427aff9ad943d5b9580225bb40a3ac4363&)
### 2. สร้างผู้ใช้ใหม่:
  * ไปที่ User Authentication > User Definition แล้วคลิกที่ Create New
    * กรอกชื่อผู้ใช้/รหัสผ่านแล้วคลิก Next จนเสร็จสิ้น
    * สร้างกลุ่มและเพิ่มผู้ใช้ใหม่ลงไปในกลุ่ม
### 3. กำหนด Interface:
* ไปที่ Network > Interface
    * แก้ไขการตั้งค่าดังนี้:
    ![img_fwInf](https://cdn.discordapp.com/attachments/1059148519992197251/1230378287675605012/68747470733a2f2f692e706f7374696d672e63632f664c4444583931352f53637265656e73686f742d323032342d30342d30372d3030323431342e706e67.png?ex=66331a13&is=6620a513&hm=9c364378c2981ce65689cd6037ec50c78c251ebd0196bb5f02bd558f9572a164&)
    * ลบพอร์ต Internal ที่ต้องการใช้
### 4. Interface สำหรับ Service 1-4:
  * สร้าง Interface สำหรับ Service 1-4
    * ตั้งค่าประเภท: Hardware Switch
    * ตั้งค่า IP: 10.80.x.0/25 (โดยที่ x คือหมายเลขของ Service)
    * เปิดใช้งาน IPv4 พร้อมกับตัวเลือกต่อไปนี้:
    - [x] PING
### 5. Interface ชื่อ mgmt:
* สร้าง Interface ชื่อ mgmt:
    * ตั้งค่าประเภท: Hardware Switch
    * ตั้งค่า IP: 0.0.0.0/0.0.0.0
### 6. Interface ชื่อ Inf851:
* สร้าง Interface ชื่อ Inf851
    * ตั้งค่าประเภท: VLAN
    * ตั้งค่า VLAN ID: 1
    * เลือก DHCP เป็นโหมดการกำหนดที่อยู่ IP และตั้งค่า IP: 10.85.1.0
    * เปิดใช้งาน IPv4 พร้อมกับตัวเลือกต่อไปนี้:
    - [x] HTTP
    - [x] HTTPS
    - [x] PING
    - [x] SSH
### 7. กำหนดค่า VPN
### 8. สร้าง Policy สำหรับ Interface และ VPN

แหล่งข้อมูลเพิ่มเติม: [FortiGate Firewall Configuration]

[FortiGate Firewall Configuration]: https://www.youtube.com/watch?v=XcghOBrZANc&list=PLlEVCBdM7ELOSd9zLJNE3FrIMzZiWlSkm

---

- ### สวิตช์: FortiSwitch 424d

<div align="center">

![Switch FortiSwitch 424d](https://cdn.discordapp.com/attachments/1059148519992197251/1230381201395552296/68747470733a2f2f7777772e61766669726577616c6c732e636f6d2e61752f696d616765732f466f7274695377697463682f466f7274695377697463682d343234442e706e67.png?ex=66331cc9&is=6620a7c9&hm=71755b7823c3d70c8ca33e617f5652a0b067359ecdcd8c426737aeb070b7c68d&)

-- [ข้อมูลเพิ่มเติมเกี่ยวกับสวิตช์] --

[ข้อมูลเพิ่มเติมเกี่ยวกับสวิตช์]: https://www.avfirewalls.com.au/FortiSwitch-424D.asp

![Port Connectors](https://cdn.discordapp.com/attachments/1059148519992197251/1230381245029023885/68747470733a2f2f696d67322e7069632e696e2e74682f7069632f53637265656e73686f742d323032342d30342d30362d3230313835312e706e67.png?ex=66331cd4&is=6620a7d4&hm=5a9dca661d2aad0f71c5941037f97cab95501c7a7cbd88d16ed4e166bdf76867&)

</div>

- SW1 (Service):
    * รีเซ็ตสวิตช์เพื่อกลับไปสู่การตั้งค่าเริ่มต้น
    * กำหนด IP/โฮสต์จากไฟร์วอล
    * สร้างการกำหนดค่า trunk สำหรับ server1(1,2) และ server2(3,4) พร้อมกับการรวมกลุ่ม LACP
    * สร้างการกำหนดค่า VLAN 801,802,803,804

- SW2 (mgmt):
    * รีเซ็ตสวิตช์เพื่อกลับไปสู่การตั้งค่าเริ่มต้น
    * กำหนด IP/โฮสต์จากไฟร์วอล
    * สร้างการกำหนดค่า trunk สำหรับ server1(1,2) และ server2(3,4) พร้อมกับการรวมกลุ่ม LACP
    * สร้างการกำหนดค่า VLAN 851,852

---

- ### เซิร์ฟเวอร์: Dell PowerEdge R330

<div align="center">

![Dell r330](https://media.discordapp.net/attachments/1059148519992197251/1230382143226777650/68747470733a2f2f696d67322e7069632e696e2e74682f7069632f6833743839736c6c2e706e67.png?ex=66331daa&is=6620a8aa&hm=f4c546610014fac9a1193af1ec2d924b6f2278bfb716759d97364e063a929521&=&format=webp&quality=lossless)

-- [ข้อมูลเพิ่มเติมเกี่ยวกับ Dell PowerEdge R330] --

[ข้อมูลเพิ่มเติมเกี่ยวกับ Dell PowerEdge R330]:https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/aa/Dell_PowerEdge_R330_SpecSheet_final.pdf

</div>
