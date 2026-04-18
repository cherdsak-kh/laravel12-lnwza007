# Laravel 12 - lnwza007 (React/Inertia Starter Kit)

โปรเจกต์นี้เป็นเว็บแอปพลิเคชันที่พัฒนาขึ้นจากโครงสร้างพื้นฐานของ **Laravel 12** ร่วมกับ **React, Inertia.js และ Tailwind CSS** (อ้างอิงจาก Laravel React Starter Kit) โดยภายในโปรเจกต์มีการรวบรวมตัวอย่างและฟีเจอร์ต่างๆ สำหรับการศึกษาเชิงปฏิบัติการ ไม่ว่าจะเป็นระบบการจำกัดสิทธิ์ผู้ใช้งาน (Role-based: admin, teacher, student), ตัวอย่างการ Query ฐานข้อมูลเบื้องต้นและขั้นสูง, ระบบจัดการข้อมูลแบบ CRUD สำหรับกระดานข่าวแบบประยุกต์และฟอร์มต่างๆ รวมไปถึงการจัดการระบบความสัมพันธ์ (Relationships) ระหว่างตารางข้อมูลในระบบ เช่น ข้อมูลผู้ใช้, ข้อมูลยานพาหนะ และใบอนุญาต

## การเริ่มต้นใช้งาน (Getting Started)

คำแนะนำเหล่านี้จะช่วยให้คุณสามารถเตรียมตัวและรันโปรเจกต์บนเครื่องคอมพิวเตอร์แบบ Local machine สำหรับการพัฒนาและการทดสอบ

### สิ่งที่ต้องเตรียมพร้อม (Prerequisites)

เพื่อให้ระบบสามารถทำงานได้อย่างถูกต้อง เครื่องคอมพิวเตอร์ของคุณจำเป็นต้องมีโปรแกรมดังต่อไปนี้:

```text
- PHP (เวอร์ชัน 8.2 ขึ้นไป)
- Composer
- Node.js และ NPM
- โปรแกรมจัดการฐานข้อมูล (เช่น MySQL, MariaDB, PostgreSQL หรือ SQLite)
```

### การติดตั้ง (Installing)

ขั้นตอนโดยละเอียดสำหรับการติดตั้งและการจำลองสภาพแวดล้อมการพัฒนา

1. ทำการโคลนโปรเจกต์ผ่าน Git

```bash
git clone https://github.com/your-username/laravel12-lnwza007.git
cd laravel12-lnwza007
```

2. ติดตั้งแพ็กเกจฝั่ง Backend (PHP) โดยใช้ Composer

```bash
composer install
```

3. ติดตั้งแพ็กเกจฝั่ง Frontend (Node.js/React) โดยใช้ NPM

```bash
npm install
```

4. ตั้งค่าตัวแปรสภาพแวดล้อม Environment variables

```bash
cp .env.example .env
```
*(เมื่อแก้ไขไฟล์เสร็จ กรุณาเข้าไปตั้งค่าการเชื่อมต่อฐานข้อมูลของคุณในไฟล์ `.env` ตรงส่วนขึ้นต้นด้วยคำว่า `DB_...` ให้ถูกต้อง)*

5. สร้างคีย์สำหรับโปรเจกต์ และสร้าง Link สาธารณะประยุกต์เพื่อให้สามารถเข้าถึงไฟล์อัปโหลดได้

```bash
php artisan key:generate
php artisan storage:link
```

6. ทำการสร้างตารางฐานข้อมูลและซี้ดข้อมูล(หากมี) ผ่านกระบวนการ Migrate

```bash
php artisan migrate
```

7. สั่งรันแอปพลิเคชันจำลองบนเซิร์ฟเวอร์

คุณควรทำการเปิดเทอร์มินัลจำนวน 2 หน้าต่าง เพื่อรันสคริปต์ฝั่ง Laravel และ Frontend ของ React / Vite ตามลำดับ

```bash
# เทอร์มินัลหน้าต่างที่ 1: สำหรับ Backend Laravel Server
php artisan serve

# เทอร์มินัลหน้าต่างที่ 2: สำหรับคอมไพล์ Frontend เรียลไทม์ (Vite)
npm run dev
```

จากนั้นคุณสามารถเข้าใช้งานโปรเจกต์ได้ที่เบราว์เซอร์ผ่านลิงก์ `http://localhost:8000`

## โครงสร้างฟีเจอร์ตัวอย่างที่สำคัญ (Key Features)

จากการศึกษาโครงสร้างโปรเจกต์ในปัจจุบัน ตัวระบบได้แฝงฟีเจอร์ทดสอบพื้นฐานดังนี้:
* **ระบบ Authentication และ Roles Middleware:** มีการแบ่งแยกการเข้าถึงหน้าเว็บสำหรับหลาย Role เช่น `admin`, `teacher`, `student`
* **Blade สลับการทำงานร่วมกับ Inertia (React):** บางหน้าในโปรเจกต์สามารถแสดงผลในรูปแบบเดิมด้วย Blade Templates สำหรับ SEO ในขณะที่หน้าที่มีกระบวนการโต้ตอบซับซ้อน เช่น Dashboard จัดการผ่าน Inertia.js 
* **Product Form & Upload Validation:** แสดงวิธีจัดการแบบฟอร์มตรวจสอบข้อมูล (Validation) เพิ่มข้อมูลสินค้า และอัปโหลดไฟล์รูปภาพไปยังโฟลเดอร์หลักอย่าง Storage 
* **SQL Queries Comparisons:** แสดงหน้าเพจการทดสอบและดึงข้อมูลจากการเปรียบเทียบใน 3 แบบ ได้แก่การเขียน Query แบบดิบ (Raw SQL), Query Builder และ Eloquent ORM
* **ระบบความสัมพันธ์ของ Model (Relationships):** สาธิตการออกแบบและควบคุมระหว่าง Model เช่น `User`, `License` และ `Vehicle` ผ่าน Resource Controllers แบบมาตรฐาน

## การรันการทดสอบ (Running the tests)

คุณสามารถรันการทดสอบอัตโนมัติต่างๆ ที่เขียนไว้ด้านใน (เช่น Unit test หรือ Feature test ผ่าน PHPUnit / Pest framework) ด้วยคำสั่งนี้

```bash
php artisan test
```

## เทคโนโลยีหลักที่นำมาใช้ (Built With)

* [Laravel 12](https://laravel.com/) - Web framework ภาษาแบคเอนด์
* [React](https://react.dev/) - ส่วนจัดการ UI Frontend ของระบบ 
* [Inertia.js](https://inertiajs.com/) - ตัวเชื่อมจัดการหน้าเว็บระหว่าง Laravel และฝั่ง React แบบรวมศูนย์
* [Tailwind CSS v4](https://tailwindcss.com/) - เฟรมเวิร์ก CSS สำหรับปรับแต่งดีไซน์
* [Radix UI](https://www.radix-ui.com/) - ชุดเครื่องใช้ Components พื้นฐานด้าน UI
* [Vite](https://vitejs.dev/) - เครื่องมือบิลด์ทรัพยากร Frontend ชั้นเยี่ยม

## สัญญาอนุญาต (License)

โปรเจกต์นี้ควบคุมและให้สิทธิ์การใช้งานผ่านแนวทางเบื้องต้นภายใต้สัญญาอนุญาตของ MIT License - โค้ดทั้งหมดเปิดกว้างสำหรับการดัดแปลงและศึกษาเพิ่มเติม
