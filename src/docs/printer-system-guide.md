# ระบบจัดการเครื่องพิมพ์ LabFlow Clinic

## ภาพรวม

ระบบจัดการเครื่องพิมพ์ของ LabFlow Clinic ช่วยให้ผู้ใช้สามารถกำหนดและจัดการเครื่องพิมพ์สำหรับการใช้งานแต่ละประเภทได้อย่างมีประสิทธิภาพ

## ฟีเจอร์หลัก

### 🖨️ การแบ่งประเภทเครื่องพิมพ์
- **สติ๊กเกอร์**: สำหรับพิมพ์สติ๊กเกอร์ผู้ป่วยและบาร์โค้ด
- **ใบเวชระเบียน**: สำหรับพิมพ์เอกสารและรายงานผลตรวจ
- **ใบเสร็จรับเงิน**: สำหรับพิมพ์ใบเสร็จและใบกำกับภาษี

### 🔍 การสแกนเครื่องพิมพ์
- สแกนหาเครื่องพิมพ์ที่เชื่อมต่อกับระบบอัตโนมัติ
- รองรับทั้ง Electron API และ Web Browser
- แสดงสถานะและข้อมูลเครื่องพิมพ์

### 💾 การจัดเก็บการตั้งค่า
- บันทึกการตั้งค่าใน localStorage
- โหลดการตั้งค่าอัตโนมัติเมื่อเปิดแอป
- สำรองข้อมูลการตั้งค่าในเครื่องผู้ใช้

## การติดตั้งและใช้งาน

### 1. การตั้งค่าเครื่องพิมพ์

#### ขั้นตอนที่ 1: เข้าสู่หน้าตั้งค่า
```
เมนู > ตั้งค่า > แท็บ "เครื่องพิมพ์"
```

#### ขั้นตอนที่ 2: สแกนเครื่องพิมพ์
```
กดปุ่ม "สแกนเครื่องพิมพ์" เพื่อค้นหาเครื่องพิมพ์ที่เชื่อมต่อ
```

#### ขั้นตอนที่ 3: กำหนดเครื่องพิมพ์
```
เลือกเครื่องพิมพ์สำหรับแต่ละประเภทการใช้งาน:
- พิมพ์สติ๊กเกอร์
- พิมพ์ใบเวชระเบียน  
- พิมพ์ใบเสร็จรับเงิน
```

#### ขั้นตอนที่ 4: ทดสอบและบันทึก
```
ทดสอบการเชื่อมต่อเครื่องพิมพ์ แล้วกดปุ่ม "บันทึกการตั้งค่า"
```

### 2. การใช้งานในโค้ด

#### วิธีที่ 1: ใช้ usePrinter Hook (แนะนำ)

```tsx
import { usePrinter } from '@/hooks/use-printer';

function MyComponent() {
  const { 
    printSticker, 
    printMedicalRecord, 
    printReceipt,
    isPrinting,
    isPrinterConfigured 
  } = usePrinter();

  const handlePrintSticker = async () => {
    const htmlContent = `
      <!DOCTYPE html>
      <html>
        <head><title>สติ๊กเกอร์</title></head>
        <body>
          <div>ข้อมูลสติ๊กเกอร์</div>
        </body>
      </html>
    `;
    
    await printSticker(htmlContent);
  };

  return (
    <button 
      onClick={handlePrintSticker}
      disabled={isPrinting || !isPrinterConfigured('sticker')}
    >
      {isPrinting ? 'กำลังพิมพ์...' : 'พิมพ์สติ๊กเกอร์'}
    </button>
  );
}
```

#### วิธีที่ 2: ใช้ Utility Functions โดยตรง

```tsx
import { 
  printSticker, 
  isPrinterConfigured, 
  getPrinterByType 
} from '@/lib/printer-utils';

async function handleDirectPrint() {
  // ตรวจสอบการตั้งค่า
  if (!isPrinterConfigured('sticker')) {
    alert('ไม่ได้กำหนดเครื่องพิมพ์สติ๊กเกอร์');
    return;
  }

  // พิมพ์
  const result = await printSticker(htmlContent);
  
  if (result.success) {
    console.log('พิมพ์สำเร็จ');
  } else {
    console.error('พิมพ์ไม่สำเร็จ:', result.message);
  }
}
```

## API Reference

### usePrinter Hook

#### Returns
```typescript
{
  // State
  isPrinting: boolean;
  
  // Print Functions
  printSticker: (content: string) => Promise<boolean>;
  printMedicalRecord: (content: string) => Promise<boolean>;
  printReceipt: (content: string) => Promise<boolean>;
  
  // Utility Functions
  testPrinter: (printerName: string) => Promise<boolean>;
  isPrinterConfigured: (type: 'sticker' | 'medical' | 'receipt') => boolean;
  getPrinterName: (type: 'sticker' | 'medical' | 'receipt') => string;
}
```

### Utility Functions

#### `getPrinterConfig(): PrinterConfig`
ดึงการตั้งค่าเครื่องพิมพ์ปัจจุบัน

#### `savePrinterConfig(config: PrinterConfig): boolean`
บันทึกการตั้งค่าเครื่องพิมพ์

#### `isPrinterConfigured(type: keyof PrinterConfig): boolean`
ตรวจสอบว่าได้กำหนดเครื่องพิมพ์สำหรับประเภทนั้นแล้วหรือไม่

#### `getPrinterByType(type: keyof PrinterConfig): string`
ดึงชื่อเครื่องพิมพ์ที่กำหนดสำหรับประเภทนั้น

#### `printSticker(content: string): Promise<{success: boolean, message?: string}>`
พิมพ์สติ๊กเกอร์ด้วยเครื่องพิมพ์ที่กำหนด

#### `printMedicalRecord(content: string): Promise<{success: boolean, message?: string}>`
พิมพ์ใบเวชระเบียนด้วยเครื่องพิมพ์ที่กำหนด

#### `printReceipt(content: string): Promise<{success: boolean, message?: string}>`
พิมพ์ใบเสร็จรับเงินด้วยเครื่องพิมพ์ที่กำหนด

## การทำงานกับ Electron

ระบบรองรับการทำงานกับ Electron API สำหรับการพิมพ์โดยตรง:

```typescript
// Electron API Interface
interface ElectronAPI {
  getPrinters(): Promise<PrinterInfo[]>;
  checkPrinterStatus(printerName: string): Promise<{
    status: 'connected' | 'disconnected' | 'error';
    message?: string;
  }>;
  printSticker(options: {
    printerName: string;
    htmlContent: string;
  }): Promise<{
    success: boolean;
    message?: string;
  }>;
  printDocument(options: any): Promise<{
    success: boolean;
    message?: string;
  }>;
}
```

## Fallback สำหรับ Web Browser

เมื่อไม่มี Electron API ระบบจะใช้ browser printing:
- เปิดหน้าต่างพิมพ์ใหม่
- แสดง HTML content
- เรียก `window.print()`

## การแก้ไขปัญหา

### ปัญหาที่พบบ่อย

#### 1. ไม่พบเครื่องพิมพ์
```
- ตรวจสอบการเชื่อมต่อเครื่องพิมพ์
- ตรวจสอบ driver เครื่องพิมพ์
- ลองสแกนใหม่
```

#### 2. พิมพ์ไม่ออก
```
- ตรวจสอบการตั้งค่าเครื่องพิมพ์
- ทดสอบการเชื่อมต่อ
- ตรวจสอบสถานะเครื่องพิมพ์
```

#### 3. การตั้งค่าหาย
```
- ตรวจสอบ localStorage
- ตั้งค่าใหม่
- ตรวจสอบ browser settings
```

## ตัวอย่างการใช้งาน

ดูตัวอย่างการใช้งานเพิ่มเติมได้ที่:
```
src/examples/printer-usage-examples.tsx
```

## การพัฒนาต่อ

### เพิ่มประเภทเครื่องพิมพ์ใหม่

1. อัปเดต `PrinterConfig` interface
2. เพิ่มฟังก์ชันใน `printer-utils.ts`
3. อัปเดต UI ในหน้า Settings
4. เพิ่มฟังก์ชันใน `usePrinter` hook

### เพิ่มรูปแบบการพิมพ์ใหม่

1. สร้าง template HTML
2. เพิ่มฟังก์ชันการพิมพ์
3. เพิ่มการจัดการ error
4. เพิ่มการทดสอบ

---

**หมายเหตุ**: ระบบนี้ออกแบบมาเพื่อใช้งานกับ LabFlow Clinic โดยเฉพาะ และรองรับการทำงานทั้งใน Electron และ Web Browser
