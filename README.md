# wastetrack-se

Development of a Garbage Truck Tracking System for Mae Kha Subdistrict Administrative Organization, Fang District, Chiang Mai Province (WasteTrack) — Project Code: SE02

**การพัฒนาระบบติดตามรถขยะสำหรับองค์การบริหารส่วนตำบลแม่คะ อำเภอฝาง จังหวัดเชียงใหม่**

หลักสูตรวิศวกรรมซอฟต์แวร์ มหาวิทยาลัยเทคโนโลยีราชมงคลล้านนา · ENGSE211 / ENGSE212

## ภาพรวม

แอปพลิเคชันบนโทรศัพท์เคลื่อนที่ระบบปฏิบัติการ Android (Mobile App) แบบรวมศูนย์เพียงช่องทางเดียว สำหรับการติดตามรถเก็บขยะและการจัดการข้อมูลเชิงพื้นที่ในพื้นที่รับผิดชอบ 15 หมู่บ้าน รองรับผู้ใช้งาน 4 บทบาท ได้แก่ ประชาชน (ไม่ต้องเข้าสู่ระบบ) พนักงานเก็บขยะ เจ้าหน้าที่หน้าเคาน์เตอร์ และหัวหน้าฝ่าย

| โมดูล / กลุ่มฟังก์ชัน | หน้าที่ |
|---|---|
| **Real-time Tracking & Geofencing** | ติดตามตำแหน่งรถเก็บขยะด้วย GPS แบบเรียลไทม์ ตรวจสอบรัศมีจุดจัดเก็บด้วย Geofencing + Haversine Formula ยืนยันผลการจัดเก็บรายจุด และแสดงสถานะจุดจัดเก็บบนแผนที่ |
| **Route Recommendation** | แนะนำลำดับจุดและเส้นทางการจัดเก็บที่เหมาะสมด้วยแนวคิด Vehicle Routing Problem (VRP) ร่วมกับ Clarke-Wright Savings Algorithm |
| **Spatial Dashboard & Bin Management** | แดชบอร์ดสรุปข้อมูลเชิงพื้นที่รายหมู่บ้านสำหรับหัวหน้าฝ่าย และการเพิ่ม/ลบจุดถังขยะพร้อมบันทึกประวัติตรวจสอบย้อนหลัง |
| **Waste Problem Reporting & Task Assignment** | แจ้งปัญหาขยะแบบย่อพร้อมรูปภาพและพิกัดบนแผนที่ (ด้วยตนเองหรือผ่านเจ้าหน้าที่หน้าเคาน์เตอร์) การมอบหมายงานแก้ไขให้พนักงาน และการรายงานผลการแก้ไขพร้อมรูปภาพ |

ทุกฟังก์ชันทำงานร่วมกันบนแผนที่และฐานข้อมูลชุดเดียวกัน ควบคุมสิทธิ์การเข้าถึงด้วย Role-Based Access Control (RBAC) และอัปเดตสถานะแบบเรียลไทม์

## เทคโนโลยี

- Mobile App: Flutter (Dart) บน Android ร่วมกับ `fl_chart`
- Backend / API Server: Supabase (Auth, PostgREST, Edge Functions / TypeScript, Storage, Realtime)
- Database: PostgreSQL (Supabase)
- Tracking & Route Engine: GPS, Geofencing, Haversine Formula, VRP + Clarke-Wright Savings Algorithm
- Map / GPS Service: Google Maps Platform (สำรองด้วย OpenStreetMap + Leaflet)
- สถาปัตยกรรม: Client-Server Architecture (C4 Model: C1 & C2)

## ทีม

| ชื่อ | ความรับผิดชอบ |
|---|---|
| นางสาวกชพร วงศ์ใหญ่ (หัวหน้าโครงงาน) | สถาปัตยกรรมระบบ ฐานข้อมูล และ RBAC/RLS; เข้าสู่ระบบ 3 บทบาท; ติดตามรถด้วย GPS แบบเรียลไทม์; Geofencing + Haversine และการยืนยันผลการจัดเก็บ; Tracking & Route Engine (Clarke-Wright Savings); การนำระบบขึ้นใช้งานและสำรองข้อมูล |
| นางสาวดาวประกาย เสาร์สิงห์ | วิเคราะห์กระบวนการและออกแบบ UI/UX (UCD); แผนที่สถานะจุดจัดเก็บ; แดชบอร์ดเชิงพื้นที่; การจัดการจุดถังขยะ; การมอบหมายงานและรายงานผลการแก้ไข; การแจ้งปัญหาขยะและหน้าจอเจ้าหน้าที่หน้าเคาน์เตอร์; การทดสอบ UAT และคู่มือการใช้งาน |

อาจารย์ที่ปรึกษา: อาจารย์นุรักษ์ ไชยศรี

## เอกสาร

เอกสารของโครงงานอยู่ในโฟลเดอร์ [`docs/`](https://github.com/itskotcha/wastetrack-se/tree/main/docs)