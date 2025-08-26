1. การเตรียมการก่อนใช้งาน
ดาวน์โหลดไฟล์ TsetlinGUI.exe
เตรียมชุดข้อมูลสำหรับ Training และ (ถ้ามี) Test
ข้อมูลต้องเป็น .csv โดยมี features ในแต่ละ column และ label ใน column สุดท้าย

ตัวอย่าง:
0,1,0,1  
1,0,1,0  
(แถวละ 1 ตัวอย่าง)

2. การเปิดโปรแกรม
ดับเบิลคลิกไฟล์ TsetlinGUI.exe → จะพบหน้าต่าง GUI พร้อมปุ่มและช่องกรอกค่าต่าง ๆ

3. ส่วนประกอบของ GUI
🔹 เลือกไฟล์
Training File: เลือกไฟล์ข้อมูลสำหรับฝึกโมเดล
Test File (optional): เลือกไฟล์ทดสอบ ถ้าไม่เลือก โปรแกรมจะใช้ Training set อย่างเดียว
🔹 พารามิเตอร์หลัก
Threshold (T) – กำหนดระดับการตัดสินใจของโมเดล
Sensitivity (s) – ควบคุมความไวในการปรับค่า
Number of Clauses – จำนวน clause ที่ใช้
Number of States – ความละเอียดของ state machine
Number of Epochs – จำนวนรอบการ train
🔹 Sweep Mode (โหมดกวาดค่า)
ใช้เพื่อทดสอบหลายค่าอัตโนมัติ (เช่น Threshold จาก 10 → 100 ก้าวทีละ 10)
SweepTarget: เลือกว่าจะ Sweep ค่า Threshold หรือ Sensitivity
SweepOrder: ลำดับการกวาด (ถ้ามีหลายพารามิเตอร์)
Step / To: ระบุค่าเริ่มต้น ก้าวทีละเท่าไร และค่าจบ
🔹 ปุ่มควบคุม
Train – เริ่มการ Train
Stop – หยุดการ Train
Reset – รีเซ็ตค่าพารามิเตอร์ทั้งหมด
Lamp Indicator – แสดงสถานะ (เขียว = Train สำเร็จ, ส้ม = มีปัญหา)

4. การใช้งานเบื้องต้น
กด Select Training File แล้วเลือก *.csv
(ถ้ามี) เลือก Test File
กำหนดค่าพารามิเตอร์ที่ต้องการ เช่น Threshold = 15, Sensitivity = 3.9
กด Train
GUI จะแสดง Accuracy และกราฟ Learning Curve

5. โหมด Sweep
ถ้าต้องการหาค่าที่เหมาะสมที่สุด
เลือก Sweep Mode
ตั้งค่า ThresholdStep และ/หรือ SensitivityStep
เลือกว่าจะ Sweep ทีละ parameter หรือหลายตัวพร้อมกัน (SweepOrder)
กด Train
GUI จะลองค่าตามช่วงที่กำหนด แล้วแสดงผลลัพธ์ที่ดีที่สุด

6. ผลลัพธ์
แสดง Training Accuracy และ Test Accuracy
แสดง กราฟเส้นความถูกต้อง (Accuracy Curve)
สามารถใช้ผลลัพธ์นี้เลือกค่าพารามิเตอร์ที่ดีที่สุด

7. ข้อควรทราบ
ถ้าไม่ได้เลือก Test file โปรแกรมจะแจ้งเตือน แต่ยังสามารถ Train ได้
ไฟล์ .csv ต้องไม่มี header row (เช่น "X1, X2, Y")
ควรตรวจสอบว่า label อยู่ใน column สุดท้ายเสมอ