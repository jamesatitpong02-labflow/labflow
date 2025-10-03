# 🚀 LabFlow Clinic - คู่มือติดตั้งแบบง่าย

## 📦 สิ่งที่คุณจะได้:
- ✅ LabFlow-Clinic-Setup-1.0.0.exe (Installer หลัก)
- ✅ Start-LabFlow-Full.bat (Launcher สำหรับรัน Backend)
- ✅ คู่มือนี้

## 🎯 วิธีติดตั้งและใช้งาน

### ขั้นตอนที่ 1: ติดตั้งโปรแกรม
1. ดับเบิลคลิก `LabFlow-Clinic-Setup-1.0.0.exe`
2. ติดตั้งตามปกติ
3. จะได้ Desktop shortcut "LabFlow Clinic" (ยังไม่มี Backend)

### ขั้นตอนที่ 2: Copy Launcher ไปโฟลเดอร์ติดตั้ง
1. Copy ไฟล์ `Start-LabFlow-Full.bat` 
2. ไปที่โฟลเดอร์ติดตั้ง (มักจะเป็น `C:\Program Files\LabFlow Clinic\`)
3. Paste ไฟล์ `Start-LabFlow-Full.bat` ลงไป

### ขั้นตอนที่ 3: สร้าง Desktop Shortcut
1. คลิกขวาที่ `Start-LabFlow-Full.bat` → Create shortcut
2. ลาก shortcut ไปวางที่ Desktop
3. เปลี่ยนชื่อเป็น "LabFlow Clinic (Full System)"

## 🎊 การใช้งาน

### เริ่มระบบเต็ม (แนะนำ):
- ดับเบิลคลิก **"LabFlow Clinic (Full System)"**
- จะเห็น:
  - 🖥️ **CMD Window** = Backend Server (http://localhost:3001)
  - 🏥 **LabFlow Window** = Main Application
- **ทั้งสองโปรแกรมทำงานพร้อมกัน**

### เริ่มแค่ Frontend (ไม่แนะนำ):
- ดับเบิลคลิก **"LabFlow Clinic"** (shortcut เดิม)
- จะได้แค่ Main Application (ไม่มี Backend)

## 🔧 การแก้ปัญหา

### ❌ ถ้า Backend ไม่รัน:
1. **ตรวจสอบ Node.js:**
   - เปิด CMD → พิมพ์ `node --version`
   - ถ้าไม่มี ให้ติดตั้งจาก: https://nodejs.org

2. **ลองรัน Backend แยก:**
   ```
   cd "C:\Program Files\LabFlow Clinic\resources\app.asar.unpacked\backend"
   node server.js
   ```

### ❌ ถ้า Main App ไม่รัน:
1. ลองรัน `LabFlow Clinic.exe` โดยตรง
2. ตรวจสอบ Windows Defender / Antivirus
3. รัน Command Prompt as Administrator

### ❌ ถ้าไม่เจอไฟล์:
ลองหาในตำแหน่งเหล่านี้:
- `C:\Program Files\LabFlow Clinic\`
- `C:\Program Files (x86)\LabFlow Clinic\`
- `C:\Users\[Username]\AppData\Local\Programs\LabFlow Clinic\`

## 📋 ข้อกำหนดระบบ

### ✅ ระบบปฏิบัติการ:
- Windows 10 (64-bit) หรือใหม่กว่า
- Windows 11 (แนะนำ)

### ✅ ซอฟต์แวร์ที่ต้องมี:
- **Node.js** (สำหรับ Backend) - ดาวน์โหลดจาก: https://nodejs.org
- .NET Framework 4.7.2+ (ติดตั้งอัตโนมัติ)

### ✅ ฮาร์ดแวร์:
- RAM: 4 GB ขึ้นไป
- พื้นที่ว่าง: 500 MB
- หน้าจอ: 1024x768 ขึ้นไป

## 🎉 สรุป

หลังจากทำตามขั้นตอนแล้ว คุณจะมี:

1. **LabFlow Clinic** = แอปอย่างเดียว
2. **LabFlow Clinic (Full System)** = แอป + Backend ครบครัน ⭐

**ใช้ตัวที่ 2 เพื่อการทำงานที่สมบูรณ์!**

---

## 🆘 ติดต่อสอบถาม
- 📧 Email: support@labflow.clinic
- 📞 โทร: 02-xxx-xxxx
- 💬 Line: @labflowclinic

**LabFlow Clinic v1.0.0**  
© 2024 LabFlow Team. All rights reserved.
