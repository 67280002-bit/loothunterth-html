# LootHuntersTH – เว็บไซต์ร้านการ์ดสะสม Pokémon และ One Piece (HTML5 + CSS ล้วน)

ใช้ HTML5 และ CSS เท่านั้น **ไม่มี JavaScript** ไม่ต้องติดตั้งโปรแกรมเพิ่ม

## วิธีเปิด
- ดับเบิลคลิก `index.html` เปิดในเบราว์เซอร์ หรือ
- เปิดโฟลเดอร์ใน VS Code → ติดตั้งส่วนขยาย **Live Server** → คลิกขวาที่ `index.html` → Open with Live Server

## ไฟล์ (23 หน้า + 1 สไตล์)
| ไฟล์ | หน้า |
|---|---|
| index.html | หน้าแรก |
| shop.html | สินค้าทั้งหมด (กรองตามเกม/ประเภทด้วย CSS) |
| product-1.html ถึง product-8.html | รายละเอียดสินค้าแต่ละชิ้น (รูป ชื่อ ราคา สต็อก ตรงกับสินค้านั้น) |
| cart.html, checkout.html, order-success.html | ตะกร้า → สั่งซื้อ → ชำระเงินสำเร็จ (เลขพัสดุ) |
| login.html, register.html, account.html | เข้าสู่ระบบ / สมัครสมาชิก / บัญชีของฉัน |
| orders.html, invoice.html, tracking.html | ประวัติคำสั่งซื้อ / ขอใบกำกับภาษี / ติดตามพัสดุ 4 สถานะ |
| sell.html, seller.html, admin.html | สมัครผู้ขาย / แดชบอร์ดผู้ขาย / แอดมิน |
| help.html | ช่วยเหลือ คำถามที่พบบ่อย |
| css/style.css | สไตล์ทั้งหมด (แก้สีที่ตัวแปรใน `:root` บนสุด) |

## รูปภาพ (โฟลเดอร์ images)
- `images/logo-header.jpg` โลโก้บนแถบเมนู (ย่อจาก `Logo.jpg`) · `images/hero.jpg` รูปหลักหน้าแรก (อัตราส่วน 3:2)
- `images/products/` รูปสินค้า ใช้ตามรายการด้านล่าง

| สินค้า | ไฟล์รูป | ราคา |
|---|---|---|
| 1 Pokémon Ninja Spinner Box 36 ซอง | pokemon-m2-box-1.jpg | ฿2,589 |
| 2 Pokémon Inferno X 1 ซอง | pokemon-m2-pack-1.jpg | ฿90 |
| 3 Pokémon Ninja Spinner 1 ซอง | pokemon-m4-pack-1.jpg | ฿84 |
| 4 Pokémon 30th Celebration | pokemon-ma6-box-1.jpg | ฿2,500 |
| 5 OP-885-PRB-01 Box 24 ซอง | op-885-prb-01-box-1.jpg | ฿6,100 |
| 6 OP-024-PRB-01 | op-024-prb-01-pack-1.jpg | ฿368 |
| 7 OP-539-OPC-EN-TCG-OP-09 | op-op-box-1.jpg | ฿26,350 |
| 8 Pokémon Starter Deck | Starter-Deck-Pokemon-1.jpg | ฿180 |

รูปที่ยังไม่ได้ใช้: `op-op13-1.jpg`, `pokemon-ma3-pack-1.jpg`, `pokemon-sv1-1-box-1.jpg` และ `one-piece-monkey-d-luffy-...webp`

## วิธีเพิ่ม/แก้ไขสินค้า
1. วางรูปใหม่ใน `images/products/` (ไฟล์ `.jpg` จริง ไม่ใช่ WebP ที่เปลี่ยนนามสกุล)
2. แก้ชื่อ ราคา รูปของแต่ละหน้าใน `shop.html` และ `product-N.html` ที่ตรงกัน
   (หน้าแรกดึงสินค้าแนะนำจากการ์ดในไฟล์ `index.html`)
3. class ของการ์ดในหน้าสินค้ากำหนดตัวกรอง: `g-pk` / `g-op` = เกม, `t-pack` / `t-deck` = ประเภท
   ต้องตรงกับป้ายที่แสดง ไม่งั้นการกรองจะเพี้ยน

## เทคนิค HTML5 / CSS ที่ใช้ (เขียนลงรายงานได้)
**HTML5:** แท็กความหมาย (`header` `nav` `main` `section` `article` `aside` `footer` `fieldset`),
ฟอร์มพร้อมการตรวจข้อมูลในตัว (`required` `pattern` `minlength` `type=email/tel/number/file`),
`details/summary` สำหรับคำถามที่พบบ่อย, `alt` ทุกรูป, `loading="lazy"`, `aria-current` และลิงก์ข้ามไปเนื้อหาหลัก

**CSS:** ตัวแปร (`--bg` `--ink` ...), Grid และ Flexbox, Responsive ด้วย `@media`, โหมดมืดด้วย `prefers-color-scheme`,
เมนูมือถือและตัวกรองสินค้าด้วย `checkbox/radio` + `:has()` โดยไม่ใช้ JavaScript, `object-fit` จัดรูปสินค้า,
ไทม์ไลน์พัสดุด้วย `::before`, `@media print` (ใบกำกับภาษี กด Ctrl + P), `:user-invalid` ขึ้นกรอบแดงเมื่อกรอกผิด

## ข้อควรรู้
- ข้อมูลทั้งหมดเป็นตัวอย่างที่เขียนไว้ในหน้า ปุ่มและฟอร์มพาไปหน้าถัดไปตามลำดับการใช้งาน ไม่มีการบันทึกข้อมูล
- ตัวกรองสินค้าใช้ `:has()` ต้องใช้เบราว์เซอร์รุ่นใหม่ (Chrome/Edge 105+, Safari 15.4+, Firefox 121+)
- ฟอนต์ Kanit/Sarabun โหลดจาก Google Fonts ถ้าไม่มีอินเทอร์เน็ตจะใช้ฟอนต์สำรองของเครื่อง
