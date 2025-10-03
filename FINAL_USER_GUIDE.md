# 🏥 LabFlow Clinic - คู่มือผู้ใช้งานสุดท้าย

## 📦 ไฟล์ที่คุณจะได้รับ

1. **`LabFlow-Clinic-Setup-1.0.0.exe`** - ตัวติดตั้งหลัก (80.95 MB)
2. **`LabFlow-Production-Launcher.bat`** - ตัวเปิดโปรแกรมแบบเต็มระบบ
3. **ไฟล์คู่มือนี้**

## 🚀 วิธีติดตั้งและใช้งาน

### ขั้นตอนที่ 1: ติดตั้งโปรแกรม
1. ดับเบิลคลิก **`LabFlow-Clinic-Setup-1.0.0.exe`**
2. ติดตั้งตามปกติ (เลือกโฟลเดอร์ติดตั้งได้)
3. เสร็จแล้วจะมี Desktop shortcut **"LabFlow Clinic"**

### ขั้นตอนที่ 2: เพิ่ม Launcher สำหรับระบบเต็ม
1. Copy ไฟล์ **`LabFlow-Production-Launcher.bat`**
2. ไปที่โฟลเดอร์ติดตั้ง (มักจะเป็น `C:\Program Files\LabFlow Clinic\`)
3. Paste ไฟล์ลงไป
4. คลิกขวาที่ **`LabFlow-Production-Launcher.bat`** → **"Create shortcut"**
5. ลาก shortcut ไปวางที่ Desktop
6. เปลี่ยนชื่อเป็น **"LabFlow Clinic (Full System)"**

## 🎯 การใช้งาน

### 🌟 วิธีที่ 1: ระบบเต็ม (แนะนำ)
**ดับเบิลคลิก "LabFlow Clinic (Full System)"**

จะเห็น:
- 🖥️ **CMD Window** = Backend Server (http://localhost:3001)
- 🏥 **LabFlow Window** = โปรแกรมหลัก

**ข้อดี:**
- ✅ ระบบทำงานครบครัน
- ✅ เห็น Backend logs
- ✅ แก้ปัญหาได้ง่าย

### 🔧 วิธีที่ 2: แอปอย่างเดียว
**ดับเบิลคลิก "LabFlow Clinic" (shortcut เดิม)**

จะได้:
- 🏥 **LabFlow Window** = โปรแกรมหลัก (ไม่มี Backend)

**ข้อจำกัด:**
- ❌ ไม่สามารถ Login ได้
- ❌ ไม่มีฟีเจอร์ที่ต้องใช้ Backend

## 🔧 การแก้ปัญหา

### ❌ ถ้า Backend ไม่รัน

#### 1. ตรวจสอบ Node.js
```cmd
node --version
```
- ถ้าไม่มี ให้ติดตั้งจาก: https://nodejs.org
- แนะนำ: Node.js LTS (Long Term Support)

#### 2. ลองรัน Backend แยก
```cmd
cd "C:\Program Files\LabFlow Clinic\resources\app.asar.unpacked\backend"
node server.js
```

#### 3. ตรวจสอบ Port
```cmd
netstat -an | find "3001"
```
- ถ้ามีโปรแกรมอื่นใช้ Port 3001 ให้ปิดก่อน

### ❌ ถ้าโปรแกรมหลักไม่รัน

#### 1. ตรวจสอบ Windows Defender
- เพิ่ม LabFlow Clinic ใน Exclusion list

#### 2. รัน as Administrator
- คลิกขวาที่ shortcut → "Run as administrator"

#### 3. ตรวจสอบไฟล์
```cmd
cd "C:\Program Files\LabFlow Clinic"
dir *.exe
```

### ❌ ถ้าไม่เจอโฟลเดอร์ติดตั้ง

ลองหาในตำแหน่งเหล่านี้:
- `C:\Program Files\LabFlow Clinic\`
- `C:\Program Files (x86)\LabFlow Clinic\`
- `C:\Users\[Username]\AppData\Local\Programs\LabFlow Clinic\`

## 📋 ข้อกำหนดระบบ

### ✅ ระบบปฏิบัติการ
- Windows 10 (64-bit) หรือใหม่กว่า
- Windows 11 (แนะนำ)

### ✅ ซอฟต์แวร์ที่จำเป็น
- **Node.js** (สำหรับ Backend) - https://nodejs.org
- .NET Framework 4.7.2+ (ติดตั้งอัตโนมัติ)

### ✅ ฮาร์ดแวร์
- RAM: 4 GB ขึ้นไป
- พื้นที่ว่าง: 500 MB
- หน้าจอ: 1024x768 ขึ้นไป

## 🎊 สรุป

หลังจากติดตั้งเสร็จ คุณจะมี:

1. **"LabFlow Clinic"** = แอปอย่างเดียว
2. **"LabFlow Clinic (Full System)"** = แอป + Backend ⭐

**ใช้ตัวที่ 2 เพื่อการทำงานที่สมบูรณ์!**

## 🆘 ติดต่อสอบถาม

- 📧 **Email:** support@labflow.clinic
- 📞 **โทร:** 02-xxx-xxxx
- 💬 **Line:** @labflowclinic
- 🌐 **Website:** https://labflow.clinic

---

**LabFlow Clinic v1.0.0**  
© 2024 LabFlow Team. All rights reserved.

*คู่มือนี้อัปเดตล่าสุด: 25 กันยายน 2024*
