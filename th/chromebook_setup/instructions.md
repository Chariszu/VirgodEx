คุณสามารถ[ข้ามส่วนนี้ไป](http://tutorial.djangogirls.org/en/installation/#install-python)หากคุณไม่ได้ใช้ Chromebook ถ้าคุณไม่ได้ใช้ ประสบการณ์การติดตั้งจะแตกต่างกันเล็กน้อย คุณสามารถมองข้ามส่วนที่เหลือของขั้นตอนการติดตั้ง

### Cloud 9

Cloud 9 is a tool that gives you a code editor and access to a computer running on the Internet where you can install, write, and run the software. สำหรับระยะเวลา ของบทเรียนนี้ Cloud 9 จะทำหน้าที่เป็น *local machine* คุณจะยังคงใช้คำสั่งในอินเตอร์เฟซเทอร์มินัลเหมือนเพื่อนบน OS X, Ubuntu หรือ Windows แต่เทอร์มินัลของคุณจะเชื่อมต่อกับคอมพิวเตอร์ที่ใช้ที่อื่นที่ Cloud 9 ตั้งค่าไว้สำหรับคุณ

1. ติดตั้ง Cloud 9 จาก [Chrome เว็บสโตร์](https://chrome.google.com/webstore/detail/cloud9/nbdmccoknlfggadpfkmcpnamfnbkmkcp)
2. ไปที่ [c9.io](https://c9.io)
3. ลง​ทะเบียน​บัญชี​ผู้​ใช้
4. คลิก*สร้างพื้นที่ทำงานใหม่*
5. ตั้งชื่อมันว่า *django-girls*
6. เลือก *Blank* (ที่ 2 จากขวาแถวล่างมีโลโก้สีส้ม)

ตอนนี้ คุณควรเห็นอินเทอร์เฟซกับแถบข้าง หน้าต่างหลักใหญ่กับข้อความ และหน้าต่างขนาดเล็กด้านล่างที่มีลักษณะดังนี้:

{% filename %}Cloud 9{% endfilename %}

    ชื่อผู้ใช้ของคุณ: ~ /workspace $
    

This bottom area is your *terminal*, where you will give the computer Cloud 9 has prepared for your instructions. You can resize that window to make it a bit bigger.

### สภาพแวดล้อมเสมือน

สภาพแวดล้อมเสมือน (เรียกว่าเป็น virtualenv) เป็นเหมือนกล่องส่วนตัวที่เราสามารถบรรจุโค๊ดคอมพิวเตอร์ที่เป็นประโยชน์ ลงไปสำหรับโครงการที่เรากำลังทำงานอยู่ เราใช้มันเพื่อเก็บบิตของโค๊ดมากมาย ที่เราต้องการแยกโครงการหลายๆโครงการออกจากกัน ทำให้ไม่มีการผสมกันระหว่างโครงการ

ใน terminal ของคุณ ที่ด้านล่างของอินเตอร์เฟซ Cloud 9 เรียกใช้ดังนี้:

{% filename %}Cloud 9{% endfilename %}

    sudo apt update
    sudo apt install python3.6-venv
    

ถ้าไม่สำเร็จ ถามโค้ชของคุณสำหรับความช่วยเหลือ

จากนั้น เรียกใช้:

{% filename %}Cloud 9{% endfilename %}

    mkdir djangogirls
    cd djangogirls
    python3.6 -mvenv myvenv
    source myvenv/bin/activate
    pip install django~=1.11.0
    

(หมายเหตุว่า บรรทัดสุดท้าย เราใช้ tilde ตาม ด้วยเครื่องหมายเท่ากับ: ~ =)

### Github

สร้างบัญชี [Github](https://github.com)

### PythonAnywhere

บทเรียน Django Girls ประกับด้วย ส่วนที่เรียกหว่า Deployment ซึ่งเป็นกระบวนการของการรับโค๊ดที่สนับสนุนแอ็พพลิเคชันเว็บใหม่ของคุณ และการย้ายไปยังคอมพิวเตอร์สาธารณะที่สามารถเข้าถึงได้ (เรียกว่าเซิร์ฟเวอร์) ทำให้คนอื่นสามารถเห็นผลงานของคุณได้

ส่วนนี้แปลกเล็กน้อย เมื่อทำตามบทเรียนบน Chromebook เนื่องจากเรากำลังใช้คอมพิวเตอร์ที่อยู่บนอินเทอร์เน็ตอยู่แล้ว (ที่ตรงกันข้ามกับ laptop ที่พูดถึง) อย่างไรก็ตามก็ยังมีประโยชน์อยู่ เนื่องจากเราสามารถคิดว่า Cloud 9 เป็นสถานที่ทำงานของเรา หรือ "แสดงความคืบหน้า" งานของเราและ Python Anywhere เป็นสถานที่เพื่อแสดงผลงานที่เรา เมื่อมันเริ่มจะสมบูรณ์มากขึ้น

ดังนั้น สมัครสมาชิกสำหรับงบัญชี Python Anywhere ใหม่ได้ที่ [www.pythonanywhere.com](https://www.pythonanywhere.com)