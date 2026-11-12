# ค้นหาที่อยู่และรหัสไปรษณีย์ไทย

เว็บสำหรับค้นหาตำบล/แขวง อำเภอ/เขต จังหวัด และรหัสไปรษณีย์ของประเทศไทย

**ทดลองใช้งาน:** [https://nkomsan.github.io/thai-zipcode/](https://nkomsan.github.io/thai-zipcode/)

## วิธีใช้งาน

1. เปิดเว็บไซต์ แล้วพิมพ์ชื่อตำบล อำเภอ จังหวัด หรือรหัสไปรษณีย์ เช่น `คลองเตย`, `เชียงใหม่` หรือ `10110`
2. ค้นหาหลายคำพร้อมกันได้ และเลือกผลลัพธ์ที่ต้องการจากรายการแนะนำ
3. ใช้ปุ่มลูกศรขึ้น/ลงเพื่อเลื่อนรายการ กด Enter เพื่อเลือก หรือกด Escape เพื่อปิดรายการ
4. คัดลอกรหัสไปรษณีย์หรือที่อยู่แบบเต็มจากหน้ารายละเอียด

เว็บโหลดข้อมูลจากไฟล์ JSON ผ่าน jsDelivr หากโหลดข้อมูลไม่ได้ เว็บจะแสดงข้อมูลตัวอย่างสำรอง ซึ่งมีรายการไม่ครบ

## ดาวน์โหลด `thai-zipcode.json`

- [ดาวน์โหลดข้อมูลเวอร์ชัน v1.0.0](https://cdn.jsdelivr.net/gh/nkomsan/thai-zipcode@v1.0.0/thai-zipcode.json) — เป็นเวอร์ชันเดียวกับที่เว็บใช้อยู่
- [ดาวน์โหลดข้อมูลจาก branch main](https://raw.githubusercontent.com/nkomsan/thai-zipcode/main/thai-zipcode.json) — ใช้เมื่อต้องการข้อมูลล่าสุดใน branch

หรือดาวน์โหลดผ่าน command line:

```bash
curl -L "https://raw.githubusercontent.com/nkomsan/thai-zipcode/main/thai-zipcode.json" -o thai-zipcode.json
```

PowerShell:

```powershell
Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/nkomsan/thai-zipcode/main/thai-zipcode.json" `
  -OutFile "thai-zipcode.json"
```

ตัวอย่างการโหลดข้อมูลจาก JavaScript:

```javascript
const response = await fetch(
  "https://cdn.jsdelivr.net/gh/nkomsan/thai-zipcode@v1.0.0/thai-zipcode.json"
);
const addresses = await response.json();

console.log(addresses[0].zipcode);
```

ไฟล์เป็น JSON array โดยแต่ละรายการมีฟิลด์ `id`, `zipcode`, `tambonId`, `subdistrict`, `district`, `province`, `region` และ `areaGroup`; ฟิลด์ `note` มีเฉพาะบางรายการ ค่า `zipcode` เป็นข้อความ ควรเก็บเป็น string เพื่อรักษาเลขศูนย์นำหน้า

## ร่วมพัฒนา (Contribute)

ยินดีรับรายงานข้อมูลที่ควรแก้ไขและ Pull Request:

1. เปิด [Issues](https://github.com/nkomsan/thai-zipcode/issues) เพื่อแจ้งข้อผิดพลาดหรือเสนอการปรับปรุง หากมีแหล่งอ้างอิง โปรดแนบมาด้วย
2. หากต้องการแก้ไข ให้ Fork repository แล้วสร้าง branch สำหรับการเปลี่ยนแปลง
3. แก้ไข `thai-zipcode.json` โดยคงรูปแบบข้อมูลเดิม ใช้ `zipcode` เป็น string และตรวจสอบว่า `id` ไม่ซ้ำ
4. ตรวจสอบว่าไฟล์ยังเป็น JSON ที่ถูกต้อง:

   ```bash
   python -c "import json; json.load(open('thai-zipcode.json', encoding='utf-8')); print('JSON is valid')"
   ```

5. ส่ง Pull Request พร้อมสรุปการเปลี่ยนแปลงและแหล่งข้อมูลที่ใช้ตรวจสอบ

โปรดตรวจสอบความถูกต้องและเงื่อนไขการใช้ข้อมูลจากแหล่งต้นทางก่อนส่งการแก้ไข ข้อมูลในโครงการนี้ควรใช้เป็นข้อมูลอ้างอิง และควรตรวจสอบกับหน่วยงานที่เกี่ยวข้องก่อนนำไปใช้ในงานสำคัญ
