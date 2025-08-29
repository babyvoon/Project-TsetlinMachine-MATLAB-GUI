📘 คู่มือการใช้งาน Tsetlin GUI

1. การติดตั้งโปรแกรม
	1. รันไฟล์ MyAppInstaller_web.exe
   	   - ถ้า Windows เตือน “Windows protected your PC” → กด More info → Run anyway
	2. เลือกโฟลเดอร์สำหรับติดตั้ง (เช่น 'C:\Program Files\TsetlinGUI') แล้วกด Next / Install
	3. โปรแกรมจะติดตั้ง TsetlinGUI.exe พร้อมสร้าง shortcut บน Desktop หรือ Start Menu
	4. MATLAB Runtime
  	   - ถ้าเครื่องยังไม่มี MATLAB Runtime ที่ต้องใช้ โปรแกรม Installer จะดาวน์โหลดและติดตั้งให้อัตโนมัติ
	5. เมื่อติดตั้งเสร็จ สามารถดับเบิลคลิก TsetlinGUI.exe เพื่อเริ่มใช้งานได้ทันที

 2. การเตรียมการก่อนใช้งาน
	- ดาวน์โหลดไฟล์ TsetlinGUI.exe (หรือจากขั้นตอนติดตั้งด้านบน)
	- เตรียมชุดข้อมูลสำหรับ Training และ (ถ้ามี) Test
	- ข้อมูลต้องเป็น '.csv' โดยมี features ในแต่ละ column และ label ใน column สุดท้าย

	ตัวอย่าง:
	0,1,0,1
	1,0,1,0
	(แถวละ 1 ตัวอย่าง)

3. การเปิดโปรแกรม
   	ดับเบิลคลิกไฟล์ TsetlinGUI.exe → จะพบหน้าต่าง GUI พร้อมปุ่มและช่องกรอกค่าต่าง ๆ

4. ส่วนประกอบของ GUI
	🔹 เลือกไฟล์
		- Training File: เลือกไฟล์ข้อมูลสำหรับฝึกโมเดล
		- Test File (optional): เลือกไฟล์ทดสอบ ถ้าไม่เลือก โปรแกรมจะใช้ Training set อย่างเดียว

	🔹 พารามิเตอร์หลัก
		- Threshold (T) – กำหนดระดับการตัดสินใจของโมเดล
		- Sensitivity (s) – ควบคุมความไวในการปรับค่า
		- Number of Clauses – จำนวน clause ที่ใช้
		- Number of States – ความละเอียดของ state machine
		- Number of Epochs – จำนวนรอบการ train

		💡 Number of Classes: ในเวอร์ชันนี้ไม่มีช่องให้กรอก เพราะโปรแกรมจะตรวจจับจำนวนคลาส อัตโนมัติจาก Training file (โดยดูจาก label คอลัมน์สุดท้ายว่ามีกี่ค่าที่แตกต่างกัน)

	🔹 Sweep Mode (โหมดกวาดค่า)
		- ใช้เพื่อทดสอบหลายค่าอัตโนมัติ (เช่น Threshold จาก 10 → 100 ก้าวทีละ 10)
		- SweepTarget: เลือกว่าจะ Sweep ค่า Threshold หรือ Sensitivity
		- SweepOrder: ลำดับการกวาด (ถ้ามีหลายพารามิเตอร์)
		- Step / To: ระบุค่าเริ่มต้น ก้าวทีละเท่าไร และค่าจบ

	🔹 ปุ่มควบคุม
		- Train – เริ่มการ Train
		- Stop – หยุดการ Train
		- Reset – รีเซ็ตค่าพารามิเตอร์ทั้งหมด
		- Lamp Indicator – แสดงสถานะ (เขียว = Train สำเร็จ, ส้ม = มีปัญหา)

5. การใช้งานเบื้องต้น
	1. กด Select Training File แล้วเลือก '.csv'
	2. เลือก Test File (ถ้ามี)
	3. กำหนดค่าพารามิเตอร์ที่ต้องการ เช่น Threshold = 15, Sensitivity = 3.9
	4. กด Train
	5. GUI จะแสดง Accuracy และกราฟ Learning Curve

6. โหมด Sweep
	ถ้าต้องการหาค่าที่เหมาะสมที่สุด:
		1. เลือก Sweep Mode
		2. ตั้งค่า ThresholdStep และ/หรือ SensitivityStep
		3. เลือกว่าจะ Sweep ทีละ parameter หรือหลายตัวพร้อมกัน (SweepOrder)
		4. กด Train
		5. GUI จะลองค่าตามช่วงที่กำหนด แล้วแสดงผลลัพธ์ที่ดีที่สุด

7. ผลลัพธ์
	- แสดง Training Accuracy และ Test Accuracy
	- แสดง กราฟเส้นความถูกต้อง (Accuracy Curve)
	- สามารถใช้ผลลัพธ์นี้เลือกค่าพารามิเตอร์ที่ดีที่สุด

8. ข้อควรทราบ
	- ถ้าไม่ได้เลือก Test file โปรแกรมจะแจ้งเตือน แต่ยังสามารถ Train ได้
	- ไฟล์ '.csv' ต้อง ไม่มี header row (เช่น '"X1, X2, Y"')
	- ควรตรวจสอบว่า label อยู่ใน column สุดท้ายเสมอ
	- จำนวนคลาสถูกตรวจจับอัตโนมัติจาก Training file ไม่ต้องกรอกเอง
