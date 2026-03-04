# งาน WEEK 6
### Software Architecture & Design Patterns + Node.js/Express Introduction
## 👤 **ข้อมูลนักศึกษา**
* **ชื่อ** : สรภูริ์ ทองจันทร์
* **สาขา** : วิศวกรรมคอมพิวเตอร์ ( เทียบโอน )
* **รหัส** : 675430206078-7

## 📖 หน่วยเรียนและวัตถุประสงค์
### หน่วยเรียนที่ 6: Software Architecture & Design Patterns + Node.js/Express Intro

ชื่อบทเรียน:
* 6.1 รูปแบบสถาปัตยกรรมซอฟต์แวร์ (Software Architecture Patterns)
* 6.2 แนะนำ Design Patterns เบื้องต้น
* 6.3 Node.js และ Express Framework พื้นฐาน
* 6.4 การอ่านและเขียนไฟล์ JSON ด้วย Node.js

        🎯 CLO ที่เกี่ยวข้อง: CLO1, CLO3, CLO4

## Monolithic Architecture
Monolithic Architecture เป็นรูปแบบที่ทุกส่วนของแอปพลิเคชันถูกรวมอยู่ในโปรแกรมเดียว (Single Unit) รวมถึง UI, Business Logic, และ Data Access ทั้งหมด

✅ ข้อดี:
* ✔️ พัฒนาและ Deploy ง่ายในช่วงเริ่มต้น
* ✔️ ไม่ต้องจัดการกับการสื่อสารระหว่างส่วนต่างๆ ที่ซับซ้อน
* ✔️ Testing แบบ End-to-End ทำได้ง่าย
* ✔️ Performance ดีเพราะไม่มี Network Latency ภายใน

❌ ข้อเสีย:
* ✖️ ยากต่อการ Scale เพราะต้อง Scale ทั้งระบบทีเดียว
* ✖️ การแก้ไขส่วนเล็กๆ ต้อง Deploy ใหม่ทั้งหมด
* ✖️ เมื่อโค้ดเพิ่มขึ้น จะยากต่อการ Maintain และเข้าใจ
* ✖️ ทีมขนาดใหญ่ทำงานยาก เพราะทุกคนแก้ไข Codebase เดียวกัน

**ตัวอย่าง**: แอปพลิเคชัน E-Commerce แบบเล็กที่มี Frontend, Backend Logic และ Database Access รวมอยู่ในโปรเจกต์เดียว

---

## Client-Server Architecture
Client-Server Architecture แบ่งระบบออกเป็น 2 ส่วนหลัก:
* Client (ฝั่งผู้ใช้): แสดงผล UI และส่ง Request ไปยัง Server
* Server (ฝั่งให้บริการ): จัดการ Business Logic และข้อมูล

✅ ข้อดี:
* ✔️ แยกความรับผิดชอบระหว่าง Frontend และ Backend ชัดเจน
* ✔️ Client หลายตัว (Web, Mobile App) สามารถใช้ Server เดียวกันได้
* ✔️ Scale Client และ Server แยกจากกันได้ตามความต้องการ
* ✔️ ปลอดภัยมากขึ้น เพราะ Logic สำคัญอยู่ที่ Server

❌ ข้อเสีย:
* ✖️ มี Network Latency จากการสื่อสารระหว่าง Client-Server
* ✖️ ต้องออกแบบ API ให้ดี เพื่อให้ Client และ Server สื่อสารได้
* ✖️ Server อาจเป็น Bottleneck ถ้า Request เยอะ

**ตัวอย่าง**: เว็บแอปพลิเคชันทั่วไป ที่มี React/Angular ฝั่ง Client และ Node.js/Express ฝั่ง Server พร้อม REST API สำหรับการสื่อสาร

## Microservices Architecture (ภาพรวม)
Microservices Architecture แบ่งแอปพลิเคชันออกเป็นบริการเล็กๆ (Services) หลายตัวที่ทำงานอิสระจากกัน แต่ละ Service มีหน้าที่เฉพาะทาง (Single Responsibility) และสื่อสารกันผ่าน API

ข้อดี:
* ✔️ Scale แต่ละ Service แยกจากกันได้ตามความต้องการ
* ✔️ ทีมสามารถพัฒนาและ Deploy Service แต่ละตัวอิสระจากกัน
* ✔️ ใช้เทคโนโลยีที่แตกต่างกันในแต่ละ Service ได้
* ✔️ ถ้า Service ตัวหนึ่ง Fail จะไม่กระทบทั้งระบบ (Fault Isolation)

❌ ข้อเสีย:
* ✖️ ความซับซ้อนในการจัดการ: ต้องจัดการ Services หลายตัว
* ✖️ การสื่อสารระหว่าง Services ผ่าน Network ทำให้มี Latency
* ✖️ ต้องมีระบบ Monitoring และ Logging ที่ดีเพื่อติดตามปัญหา
* ✖️ Testing แบบ End-to-End ทำได้ยากกว่า Monolithic

**ตัวอย่าง**: Netflix, Amazon ที่แบ่งระบบเป็น Services เล็กๆ เช่น User Service, Payment Service, Recommendation Service ซึ่งแต่ละ Service มี Database และทีมพัฒนาของตัวเอง

## เปรียบเทียบสถาปัตยกรรมซอฟต์แวร์
|ปัจจัย|Monolithic|Client-Server|Microserives|
|:--|:--|:--|:--|
|ความซับซ้อน|ต่ำ|ปานกลาง|สูง|
การ Scale|Scale ทั้งระบบ|Scale แยก Client/Server|	Scale แยกแต่ละ Service|
|การ Deploy|Deploy ทั้งหมด|Deploy แยก Client/Server|	Deploy แยกแต่ละ Service|
|เหมาะกับ|โปรเจกต์เล็ก/ทีมเล็ก|โปรเจกต์ขนาดกลาง|โปรเจกต์ขนาดใหญ่/องค์กร|
|ทีมพัฒนา|ทีมเดียวกัน|แยกทีม Frontend/Backend|	แยกทีมแต่ละ Service|
|Technology Stack|หนึ่งเดียว|Frontend + Backend แยกได้|	แต่ละ Service เลือกได้อิสระ|
|การบำรุงรักษา|ยากเมื่อระบบใหญ่|ปานกลาง|ง่าย (แยกชัดเจน)|

