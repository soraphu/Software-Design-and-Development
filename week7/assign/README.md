# Week 7 Lab
### Backend & API Design + SQLite Integration
## 👤 **ข้อมูลนักศึกษา**
* **ชื่อ** : สรภูริ์ ทองจันทร์
* **สาขา** : วิศวกรรมคอมพิวเตอร์ ( เทียบโอน )
* **รหัส** : 675430206078-7

## หน่วยเรียนและวัตถุประสงค์
บทเรียน:
* 7.1 หลักการออกแบบ RESTful API
* 7.2 Data Modelling และ ER Diagram
* 7.3 SQLite และการเชื่อมต่อกับ Express
* 7.4 การแบ่งเลเยอร์โค้ด (Layered Architecture)

วัตถุประสงค์การสอน:
* 7.1.1 อธิบายหลักการออกแบบ RESTful API ตาม REST Principles ได้
* 7.1.2 ออกแบบ API Endpoints ตาม Resources และ HTTP Methods ที่เหมาะสมได้
* 7.2.1 สร้าง ER Diagram จาก Requirements ของระบบได้
* 7.2.2 แปลง ER Diagram เป็น Database Tables ได้
* 7.3.1 เปรียบเทียบข้อดี-ข้อเสียระหว่าง JSON file และ SQLite ได้
* 7.3.2 เชื่อมต่อ Express กับ SQLite และทำ CRUD Operations ได้
* 7.4.1 อธิบายบทบาทของแต่ละเลเยอร์ (Router, Controller, Service, Database) ได้
* 7.4.2 จัดโครงสร้างโค้ด Backend ตาม Layered Architecture ได้

## หลักการออกแบบ RESTful API
REST ย่อมาจาก Representational State Transfer เป็นรูปแบบการออกแบบ (Architectural Style) สำหรับระบบ Distributed Hypermedia โดยเฉพาะ Web Services

### หลักการตั้งชื่อ Resource:
|หลักการ|❌ ไม่ดี|✅ ดี|
|:--|:--|:--|
|ใช้คำนาม ไม่ใช้คำกริยา|`/getUsers`|`/users`|
|ใช้พหูพจน์|`/user`|`/users`|
|ใช้ตัวพิมพ์เล็ก|`/Users`|`/users`|
|ใช้ขีด - แทนขีดล่าง|/user_profiles|/user-profiles|
|ไม่ลงท้ายด้วย /|/users/|/users|

### HTTP Methods (Verbs)
|HTTP Method|CRUD Operation|ความหมาย|Idempotent?|Safe?|
|:--|:--|:--|:--|:--|
|GET	|Read	|ดึงข้อมูล|✅ Yes|✅ Yes|
|POST	|Create	|สร้างใหม่|❌ No|❌ No|
|PUT	|Update	|แทนที่ทั้งหมด|✅ Yes|❌ No|
|PATCH	|Update	|แก้ไขบางส่วน|❌ No|❌ No|
|DELETE	|Delete	|ลบ	|✅ Yes|❌ No|

### HTTP Status Codes
|Code|ชื่อ|ใช้เมื่อ|ตัวอย่าง|
|:--|:--|:--|:--|
|200	|OK	|Request สำเร็จ|	GET, PUT successful|
|201	|Created|	สร้างข้อมูลสำเร็จ|	POST successful|
|204	|No Content|	สำเร็จ แต่ไม่มีข้อมูล return|	DELETE successful|
|400	|Bad Request|	Request ไม่ถูกต้อง|	Missing required fields|
|401	|Unauthorized|	ไม่ได้ Login|	No authentication token|
|403	|Forbidden|	ไม่มีสิทธิ์	|Not allowed to access|
|404	|Not Found|	ไม่พบข้อมูล|	Resource doesn't exist|
|409	|Conflict	|ข้อมูลซ้ำ	|Duplicate email|
|422	|Unprocessable Entity|	Validation failed|	Invalid data format|
|500	|Internal Server Error|	Server เกิดข้อผิดพลาด| Database error|