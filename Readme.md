# AHK v1.1 GUI ตัวอย่างพร้อมระบบอัพเดทจาก GitHub

## 📋 สารบัญ

- [ภาพรวม](#ภาพรวม)
- [คุณสมบัติ](#คุณสมบัติ)
- [การติดตั้ง](#การติดตั้ง)
- [การตั้งค่า GitHub](#การตั้งค่า-github)
- [การใช้งานระบบอัพเดท](#การใช้งานระบบอัพเดท)
- [โครงสร้างโปรเจค](#โครงสร้างโปรเจค)
- [การปรับแต่ง](#การปรับแต่ง)

---

## 🎯 ภาพรวม

โปรเจคนี้เป็นตัวอย่างการสร้าง GUI Application ด้วย AutoHotkey v1.1 ที่มีระบบอัพเดทอัตโนมัติผ่าน GitHub Releases โดยโปรแกรมจะตรวจสอบเวอร์ชันใหม่จากไฟล์ `version.ini` บน GitHub Repository และดาวน์โหลดอัพเดทได้อัตโนมัติ

---

## ✨ คุณสมบัติ

### GUI หลัก
- **หน้าจอหลัก**: แสดงข้อมูลโปรแกรมและสถานะระบบ
- **Menu Bar**: เมนูไฟล์และช่วยเหลือพร้อม Hotkeys
- **Progress Bars**: แสดง CPU และ Memory Usage แบบ Real-time
- **Action Buttons**: ปุ่มสำหรับการดำเนินการต่างๆ

### ระบบอัพเดท
- **ตรวจสอบอัพเดท**: ตรวจสอบเวอร์ชันใหม่จาก GitHub
- **ดาวน์โหลดอัตโนมัติ**: ดาวน์โหลดไฟล์อัพเดทพร้อม Progress Bar
- **ติดตั้งอัตโนมัติ**: อัพเดทโปรแกรมโดยอัตโนมัติหลังดาวน์โหลด
- **เปรียบเทียบเวอร์ชัน**: เปรียบเทียบเวอร์ชัน Semantic Versioning

### หน้าต่างเพิ่มเติม
- **Settings**: หน้าต่างตั้งค่าโปรแกรม
- **About**: หน้าต่างเกี่ยวกับโปรแกรม
- **Log Viewer**: ดู Log ของโปรแกรม
- **Demo Window**: ทดสอบฟีเจอร์ต่างๆ

---

## 🚀 การติดตั้ง

### ข้อกำหนด
- AutoHotkey v1.1 หรือใหม่กว่า
- Windows 7 หรือใหม่กว่า
- การเชื่อมต่ออินเทอร์เน็ต (สำหรับระบบอัพเดท)

### ขั้นตอนการติดตั้ง
1. ดาวน์โหลดไฟล์ `AHK_GitHub_Updater_Example.ahk`
2. แก้ไขการตั้งค่าในส่วน `การตั้งค่า` ให้ตรงกับ GitHub ของคุณ
3. รันไฟล์ด้วย AutoHotkey

---

## ⚙️ การตั้งค่า GitHub

### ขั้นตอนที่ 1: สร้าง Repository

```bash
# สร้าง repository ใหม่บน GitHub
# ชื่อที่แนะนำ: MyAHKApp หรือชื่อโปรแกรมของคุณ
```

### ขั้นตอนที่ 2: อัพโหลดไฟล์

อัพโหลดไฟล์ต่อไปนี้ไปที่ repository:

```
your-repo/
├── version.ini          # ไฟล์เก็บข้อมูลเวอร์ชัน
├── releases/            # โฟลเดอร์เก็บไฟล์ releases
│   └── v1.0.0/
│       └── MyAHKApp.exe
└── README.md
```

### ขั้นตอนที่ 3: แก้ไขโค้ด

แก้ไขส่วนการตั้งค่าในไฟล์ AHK:

```autohotkey
global AppName := "MyAHKApp"
global AppVersion := "1.0.0"
global GitHubUser := "your-username"      ; เปลี่ยนเป็น username ของคุณ
global GitHubRepo := "your-repo"          ; เปลี่ยนเป็นชื่อ repository
```

### ขั้นตอนที่ 4: สร้าง Release

1. ไปที่ GitHub Repository → Releases → Draft a new release
2. ตั้งค่า Tag version: `v1.0.0`
3. อัพโหลดไฟล์ `.exe` ของโปรแกรม
4. Publish release

---

## 🔄 การใช้งานระบบอัพเดท

### วิธีการตรวจสอบอัพเดท

**วิธีที่ 1: ผ่าน Menu**
```
ไฟล์ → ตรวจสอบอัพเดท
```

**วิธีที่ 2: ใช้ Hotkey**
```
Ctrl + U
```

**วิธีที่ 3: อัตโนมัติเมื่อเปิดโปรแกรม**
เอา comment ออกจากบรรทัดสุดท้ายในไฟล์:
```autohotkey
Gosub, CheckUpdate  ; เอา comment ออกถ้าต้องการตรวจสอบอัตโนมัติ
```

### การอัพเดท version.ini

เมื่อต้องการปล่อยเวอร์ชันใหม่:

1. แก้ไข `version.ini`:
```ini
[Version]
Version=1.0.1
ReleaseDate=2025-01-15
ReleaseNotes=- เพิ่มฟีเจอร์ใหม่`n- แก้ไขบัค
Mandatory=0
```

2. Commit และ Push ไป GitHub

3. สร้าง Release ใหม่บน GitHub

---

## 📁 โครงสร้างโปรเจค

```
AHK_GitHub_Updater_Example/
│
├── AHK_GitHub_Updater_Example.ahk   # ไฟล์หลัก
│   ├── การตั้งค่า
│   ├── GUI หลัก
│   ├── ระบบอัพเดท
│   ├── Helper Functions
│   └── Event Handlers
│
├── version.ini                       # ไฟล์เวอร์ชัน (อัพโหลดไป GitHub)
│
└── README.md                         # เอกสารนี้
```

---

## 🔧 การปรับแต่ง

### เปลี่ยนสี GUI

```autohotkey
Gui, Color, F5F5F5  ; เปลี่ยนสีพื้นหลัง
GuiControl, +cGreen, CPUProgress  ; เปลี่ยนสี Progress Bar
```

### เพิ่มฟีเจอร์ตรวจสอบ Beta

```autohotkey
IniRead, BetaVersion, %TempFile%, Beta, BetaVersion, 0.0.0
IniRead, BetaAvailable, %TempFile%, Beta, BetaAvailable, 0

if (BetaAvailable = 1) {
    MsgBox, มีเวอร์ชัน Beta: v%BetaVersion%
}
```

### เพิ่มการตรวจสอบ Checksum

```autohotkey
FileGetHash(FilePath, "MD5")  ; ต้องมีฟังก์ชันนี้
IniRead, ExpectedMD5, %TempFile%, Checksum, MD5
if (CalculatedMD5 != ExpectedMD5) {
    MsgBox, ไฟล์เสียหาย!
}
```

---

## 📝 Notes

- โปรแกรมใช้ `WinHttp.WinHttpRequest` สำหรับดาวน์โหลดไฟล์
- รองรับ Semantic Versioning (x.y.z)
- สามารถตั้งค่าให้บังคับอัพเดทได้ (Mandatory=1)

---

## 📜 License

MIT License - สามารถนำไปใช้และดัดแปลงได้อย่างอิสระ
