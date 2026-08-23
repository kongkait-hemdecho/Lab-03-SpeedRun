# ⚡ Lab 03: Speed Run Network Setup & Troubleshooting

## 📌 Overview
Lab นี้เป็นการซ้อมมือแบบ Speed Run โดยออกแบบและคอนฟิกระบบเครือข่ายใหม่ทั้งหมดตั้งแต่กระดาษเปล่า (Scratch) เพื่อทดสอบความชำนาญในการใช้ CLI Command และวิเคราะห์ปัญหาการเชื่อมต่อ (Troubleshooting)

---

## 📐 Network Topology & Configuration Summary
* **LAN Subnets:** `192.168.10.0/24`, `192.168.20.0/24`, `192.168.30.0/24`, `192.168.40.0/24`
* **WAN Link:** `100.1.1.0/30` (HQ: `100.1.1.1`, ISP: `100.1.1.2`)
* **Internet / Destination Server:** `1.1.1.1`

---

## ⚙️ Key Technical Features
1. **Inter-VLAN Routing:** คอนฟิก 802.1Q Sub-interfaces บน Router-HQ
2. **NAT Overload (PAT):** สร้าง Access List กวาดวง `192.168.0.0/16` และทำ NAT ออกทาง Interface ขา WAN (`GigabitEthernet0/2`)
3. **Default Routing:** ชี้ Gateway of Last Resort (`0.0.0.0 0.0.0.0`) ไปยัง IP ขา WAN ของ ISP (`100.1.1.2`)

---

## 🛠️ Key Troubleshooting Notes (สิ่งเรียนรู้จาก Lab นี้)
* **Routing Table Check:** หากขึ้น `Gateway of last resort is not set` แสดงว่า Router ยังไม่มี Default Route ชี้ออกสู่อินเทอร์เน็ต ต้องเพิ่มคำสั่ง `ip route 0.0.0.0 0.0.0.0 <Next-Hop-IP>`
* **ISP Configuration:** Router ฝั่ง ISP ไม่จำเป็นต้องตั้งค่า NAT (`ip nat outside`) ให้เน้นการตั้งค่า IP Interface และ Routing กลับให้ถูกต้อง

---

## ✅ Test Results
<img width="960" height="1040" alt="สกรีนช็อต 2026-08-23 182348" src="https://github.com/user-attachments/assets/bee30c35-d687-4f8b-8714-d686d1bc5ecc" />

<img width="752" height="563" alt="สกรีนช็อต 2026-08-23 182439" src="https://github.com/user-attachments/assets/0a05cd95-a1f1-4c83-ac95-df45042bd2eb" />
