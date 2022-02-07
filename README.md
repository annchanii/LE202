# LE202
# การสมัคร Github 
ให้สมัครแบบฟรี โดยใช้อีเมล และโหลดโปรแกรม Github Desktop และ Git scm
# การสร้าง Repo
1.กด + บนมุมขวามือ เลือก New reposity

2.ตั้งชื่อไฟล์ และ description เกียวกับ repo ที่สร้าง

3.กดเลือก Public

4.กดเลือก lnitialize this repository with a README

5.กด Create repository
# Basic writing
### 1.Headings 

### 2.Styling taxt 
ใช้  **ตัวหนา**   *ตัวเอียง* 

### 3.Link 
ใช้ [ inline link ] (linl) และ commad + k

### Images 
ใช้ ![text](link)

### list
- Drink
- food
  - pizza
    

### Emoji
: emojocode :
👍 🧑‍🚀

# Web hosting
1.สร้าง repo

2.กด setting แล้วไปที่ github pages

3.github pages > source > master branch >save

4.นำ URL ไปใช้ได้เลย

# 01 Digital
นำข้อมูลดิจิตอลมาใช้งาน มีตัวเลข1และ0ที่แสดงค่าต่างๆ ซึ่งขึ้นอยู่กับแรงดัน และสามารถใช้ตัวเลขแทนตัวอักษรได้ เช่น A = 41 

# 02 voltage 
แรงดันไฟฟ้าเกิดจากความต่างศักย์ระหว่างจุดสองจุด ซึ่งมีทั้งแรงดันไฟฟ้าจากไฟกระแสสลับ(ไฟบ้าน 220v)และแรงดันไฟฟ้าจากไฟกระแสตรง(แบตเตอร์รี่ 1.6v)

# 03 computer
มีทั้งคอมพิวเตอร์ขนาดใหญ่/ขนาดกลาง/single board/arduino microcontroller

# 04 internet
เป็นการเชื่อมโยงทุกอย่างเข้าด้วยกันทั้งที่มีสายและไร้สาย เช่นพวก WiFi Blurtooth

# 05 program lang
การเขียนซอฟแวร์ด้วยภาษา c /java/python

# 06 platform io
การโปรแกรมลงในคอมพิมเตอร์ขนาดเล็ก(microcontroller)

# ESP01 
มีทั้งหมด 6 การทดลอง
# 01
- นำ microcontroller มาเชื่อมต่อกับ USB เพื่อเขียนโปรแกรม
- เปิดโปรแกรม 01_serial-Moniter
- อัปโหลดโปรแกรมเขียนโค้ด pio run -t upload
- กดปุ่มสีดำที่microcontroller เพื่ออัปโหลด
- กดปุ่มสีแดงเพื่อ reset
- ดูผลลัพธ์จากโค้ด pio device moniter

# 02
- โปรแกรมแสกนหา wifi 
- อัปโหลดโปรแกรมเขียนโค้ด pio run -t upload
- กดปุ่มสีดำที่microcontroller เพื่ออัปโหลด
- กดปุ่มสีแดงเพื่อ reset
- ดูผลลัพธ์จากโค้ด pio device moniter

# 03
- โปรแกรมทดลองสัญญาณที่ output ออกไปภายนอก
- ใช้ adapter เสียบระหว่าง USB กับ microcontroller โดยสัญญาณ0อยู่ที่สายสีขาว และ 1อยู่ที่สายสีเหลือง
- เปิดโปรแกรม 03_output-port
- อัปโหลดโปรแกรมเขียนโค้ด pio run -t upload
- กดปุ่มสีดำที่microcontroller เพื่ออัปโหลด
- กดปุ่มสีแดงเพื่อ reset
- ดูผลลัพธ์จากโค้ด pio device moniter และก็จะมีไฟเปล่งแสงที่สัญญาณ 0

# 04
- โปรแกรมทดลองนำสัญญาณ input เข้ามาใน microcontroller
- เปิดโปรแกรม 04_input-port
- อัปโหลดโปรแกรมเขียนโค้ด pio run -t upload
- กดปุ่มสีดำที่microcontroller เพื่ออัปโหลด
- กดปุ่มสีแดงเพื่อ reset
- ดูผลลัพธ์จากโค้ด pio device monite
- ต่อมา นำLDR กับ resistor มาต่อกับ microcontroller
- จะเห็นผลลัพธ์เป็น เมื่อมีแสงส่องLDR สัญญาณเป็น 0=ไฟติด และเมื่อไม่มีแสงส่องLDR สัญญาณเป็น 1=ไฟไม่ติด

# 05
- โปรแกรมสร้าง Web server ผ่าน wifi
- เปิดโปรแกรม 05_WiFi-web-server
- อัปโหลดโปรแกรมเขียนโค้ด pio run -t upload
- กดปุ่มสีดำที่microcontroller เพื่ออัปโหลด
- กดปุ่มสีแดงเพื่อ reset
- ดูผลการรันจากโค้ด pio device monite
- เช็คผลลัพธ์ได้จาก Web browser

# 06
- โปรแกรมร้าง wifi ขึ้นมาเอง
- เปิดโปรแกรม 06_WiFi-AP-Web-Server
- อัปโหลดโปรแกรมเขียนโค้ด pio run -t upload
- กดปุ่มสีดำที่ microcontroller เพื่ออัปโหลด
- กดปุ่มสีแดงเพื่อ reset
- ดูผลการรันจากโค้ด pio device monite
- เช็คผลลัพธ์จาก ค้นหา wifi ในโทรศัพท์


