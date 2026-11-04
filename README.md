# Smart Savings (GitHub Pages)

เว็บ Smart Savings ฉบับที่รันบน GitHub Pages ได้ โมเดลทั้งสองตัวทำงานในเบราว์เซอร์ ไม่ต้องใช้ Python หรือ Streamlit

## ไฟล์ที่ต้องอัปโหลด (ไว้ที่หน้าแรกของ repository ทั้งหมด)

| ไฟล์ | หน้าที่ |
| --- | --- |
| `index.html` | หน้าเว็บ 3 แท็บ |
| `style.css` | หน้าตาของเว็บ |
| `app.js` | โค้ดที่ใช้โมเดลทำนาย |
| `savings_model.json` | โมเดลเงินฝากประจำ (Random Forest, supervised) |
| `saver_model.json` | โมเดลกลุ่มนักออม (K-Means, unsupervised) |
| `customers.json` | ลูกค้า 200 คน สำหรับวาดกราฟ |
| `.nojekyll` | บอก GitHub ว่าไม่ต้องแปลงไฟล์ (ไม่บังคับ) |

## ขั้นตอนขึ้น GitHub Pages

1. github.com → **New repository** → ตั้งชื่อ เช่น `smart-savings` → เลือก **Public** → **Create repository**
2. กด **uploading an existing file** → ลากไฟล์ทั้งหมดข้างบนลงไป → **Commit changes**
3. ไปที่ **Settings** → **Pages** → Source เลือก **Deploy from a branch** → Branch เลือก `main` และโฟลเดอร์ `/ (root)` → **Save**
4. รอ 1-2 นาที แล้วเปิด `https://ชื่อผู้ใช้.github.io/smart-savings/`

ถ้าดับเบิลคลิกเปิด `index.html` ในเครื่องโดยตรง เว็บจะโหลดโมเดลไม่ได้ (เบราว์เซอร์ไม่ยอมให้อ่านไฟล์ .json แบบนั้น) ต้องเปิดผ่าน GitHub Pages หรือรัน `python -m http.server` ในโฟลเดอร์นี้ แล้วเปิด http://localhost:8000

## ค่าทดสอบ

- แท็บ Fixed deposit: ค่าเริ่มต้นได้ 38% · ดอกเบี้ย 1.0 ได้ 68% · retired, อายุ 65, previous 1, success ได้ 94%
- แท็บ Saver group: รายได้ 90 ใช้จ่าย 20 → High-income savers

## ถ้าเทรนโมเดลใหม่ใน Colab

รัน `export_for_web.py` (อยู่ในโฟลเดอร์ `tools`) ในโฟลเดอร์เดียวกับ `savings_model.joblib`, `saver_model.joblib` และ `customers_with_groups.csv` จะได้ไฟล์ .json ใหม่ 3 ไฟล์ แล้วอัปโหลดทับของเดิมบน GitHub

ข้อมูลจาก Kaggle ใช้เพื่อการเรียนเท่านั้น ไม่ใช่คำแนะนำทางการเงิน
