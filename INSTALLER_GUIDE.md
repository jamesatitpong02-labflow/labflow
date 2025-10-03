# 🚀 คู่มือสร้างและใช้งาน LabFlow Clinic Installer

## 📦 วิธีสร้างไฟล์ Installer

### ขั้นตอนที่ 1: เตรียมความพร้อม
```bash
# ตรวจสอบ Node.js และ npm
node --version
npm --version

# ติดตั้ง dependencies
npm install
```

### ขั้นตอนที่ 2: สร้าง Installer
```bash
# วิธีที่ 1: ใช้ script อัตโนมัติ (แนะนำ)
npm run build:installer

# วิธีที่ 2: สร้างทั้ง installer และ portable
npm run build:all
```

### ขั้นตอนที่ 3: ตรวจสอบไฟล์ที่สร้างขึ้น
ไฟล์จะอยู่ในโฟลเดอร์ `dist-electron/`:
- 🎯 `LabFlow-Clinic-Setup-1.0.0.exe` - **INSTALLER** (แนะนำ)
- 📱 `LabFlow-Clinic-1.0.0-portable.exe` - Portable version

## 🎯 ความแตกต่างระหว่าง Installer และ Portable

### 📦 Installer Version (`LabFlow-Clinic-Setup-1.0.0.exe`)
**ข้อดี:**
- ✅ ติดตั้งอัตโนมัติ ไม่ต้องทำอะไรเพิ่ม
- ✅ สร้าง Desktop Icon อัตโนมัติ
- ✅ เพิ่มใน Start Menu
- ✅ เพิ่มใน Add/Remove Programs
- ✅ สร้าง Uninstaller
- ✅ ตั้งค่า File Associations
- ✅ สร้างโฟลเดอร์ข้อมูลอัตโนมัติ

**การใช้งาน:**
1. ส่งไฟล์ `LabFlow-Clinic-Setup-1.0.0.exe` ให้ผู้ใช้
2. ผู้ใช้ดับเบิลคลิก → เสร็จ!

### 📱 Portable Version (`LabFlow-Clinic-1.0.0-portable.exe`)
**ข้อดี:**
- ✅ ไม่ต้องติดตั้ง รันได้ทันที
- ✅ พกพาได้ (USB Drive)
- ✅ ไม่แก้ไข Registry

**ข้อเสีย:**
- ❌ ต้องสร้าง Desktop Icon เอง
- ❌ ไม่มี Uninstaller

## 🎊 ฟีเจอร์ของ Installer

### การติดตั้งอัตโนมัติ:
1. **ตรวจสอบระบบ** - Windows 10+ เท่านั้น
2. **สร้าง Desktop Icon** - พร้อม icon สวยงาม
3. **เพิ่มใน Start Menu** - โฟลเดอร์ "LabFlow Clinic"
4. **สร้างโฟลเดอร์ข้อมูล** - `%APPDATA%\LabFlow Clinic\`
5. **ตั้งค่า Permissions** - สิทธิ์การเขียนไฟล์
6. **เพิ่มใน Control Panel** - Add/Remove Programs

### หน้าจอ Installer:
- 🏠 **Welcome Page** - ข้อความต้อนรับภาษาไทย
- 📂 **Directory Selection** - เลือกโฟลเดอร์ติดตั้ง
- ⚙️ **Components** - เลือกส่วนประกอบ
- 📋 **Ready to Install** - ยืนยันการติดตั้ง
- ⏳ **Installing** - แสดงความคืบหน้า
- 🎉 **Finish** - เสร็จสิ้นการติดตั้ง

## 📋 การใช้งาน Installer

### สำหรับ Developer:
```bash
# สร้าง installer
npm run build:installer

# ทดสอบ installer
# 1. รันไฟล์ .exe ที่สร้างขึ้น
# 2. ติดตั้งในเครื่องทดสอบ
# 3. ตรวจสอบ desktop icon
# 4. ทดสอบการทำงานของโปรแกรม
```

### สำหรับผู้ใช้:
1. **ดาวน์โหลด** `LabFlow-Clinic-Setup-1.0.0.exe`
2. **ดับเบิลคลิก** ไฟล์ installer
3. **ทำตาม wizard** (กด Next ไปเรื่อยๆ)
4. **เสร็จ!** โปรแกรมพร้อมใช้งาน

## 🛠️ การแก้ไขปัญหา

### ปัญหาที่พบบ่อย:

#### 1. "Windows protected your PC"
**สาเหตุ**: ไฟล์ไม่ได้ signed
**แก้ไข**:
- คลิก "More info"
- คลิก "Run anyway"

#### 2. "The app you're trying to install isn't a Microsoft-verified app"
**สาเหตุ**: Windows SmartScreen
**แก้ไข**:
- คลิก "Install anyway"
- หรือ Disable SmartScreen ชั่วคราว

#### 3. การติดตั้งล้มเหลว
**สาเหตุ**: ไม่มีสิทธิ์ Administrator
**แก้ไข**:
- คลิกขวาที่ installer
- เลือก "Run as administrator"

#### 4. Desktop icon ไม่ปรากฏ
**สาเหตุ**: ไม่ได้เลือก option สร้าง desktop shortcut
**แก้ไข**:
- หาโปรแกรมใน Start Menu
- คลิกขวา → "Pin to desktop"

## 🔧 การปรับแต่ง Installer

### แก้ไขข้อความ:
แก้ไขไฟล์ `build/installer.nsh`:
```nsis
!define MUI_WELCOMEPAGE_TITLE "ข้อความต้อนรับ"
!define MUI_WELCOMEPAGE_TEXT "รายละเอียดโปรแกรม"
```

### เปลี่ยน Icon:
แทนที่ไฟล์ `public/iconlabflow.ico`

### เพิ่ม Components:
แก้ไขไฟล์ `package.json` ส่วน `build.nsis`

## 📊 ขนาดไฟล์โดยประมาณ

| ประเภท | ขนาด | คำอธิบาย |
|--------|------|----------|
| **Installer** | 80-120 MB | ไฟล์ติดตั้งที่บีบอัด |
| **Installed** | 200-300 MB | ขนาดหลังติดตั้ง |
| **Portable** | 150-250 MB | ไฟล์เดียวพกพาได้ |

## 🎯 Best Practices

### สำหรับการแจกจ่าย:
1. **ทดสอบใน VM** ก่อนส่งให้ลูกค้า
2. **สร้าง Checksum** เพื่อตรวจสอบความถูกต้อง
3. **เตรียมคู่มือ** การใช้งานเบื้องต้น
4. **ระบุ System Requirements** ชัดเจน

### สำหรับการสนับสนุน:
1. **Remote Desktop** สำหรับช่วยติดตั้ง
2. **Video Tutorial** การใช้งาน
3. **FAQ** ปัญหาที่พบบ่อย
4. **Contact Info** ช่องทางติดต่อ

---

## 🚀 คำสั่งสำคัญ

```bash
# สร้าง installer
npm run build:installer

# สร้างทั้ง installer และ portable
npm run build:all

# ทดสอบ build
npm run build && npm run electron

# ล้างไฟล์ build
rmdir /s /q dist dist-electron
```

**LabFlow Clinic Installer v1.0.0**  
© 2024 LabFlow Team. All rights reserved.
