# อินเทอร์เน็ตทำงานอย่างไร

> สำหรับผู้อ่านทางบ้าน ส่วนนี้จะครอบคลุมในส่วนวิดิโอของ [Python Basics: Dictionaries](https://www.youtube.com/watch?v=oM9yAA09wdc)
> 
> บทเรียนนี้ได้แรงบันดาลใจจาก "How the Internet works" โดย Jessica McKellar (http://web.mit.edu/jesstess/www/)

เรารู้ว่าคุณใช้อินเทอร์เน็ตแทบทุกวัน แต่คุณรู้ไหมว่าจริงๆ แล้ว เวลาที่คุณพิมพ์ที่อยู่เว็บ เช่น https://djangogirls.org และกดปุ่ม `enter` มันมีอะไรเกิดขึ้นบ้าง?

The first thing you need to understand is that a website consists of a bunch of files saved on a hard disk -- just like your movies, music, or pictures. However, there is one part that is unique for websites: they include computer code called HTML.

If you're not familiar with programming, it can be hard to grasp HTML at first, but your web browsers (like Chrome, Safari, Firefox, etc.) love it. เว็บเบราว์เซอร์ถูกออกแบบมาเพื่อทำความเข้าใจรหัสเหล่านี้ ทำตามคำสั่งและแสดงผลจาไฟล์เว็บไซต์ของคุณ ให้ตรงกับสิ่งที่คุณต้องการ

เช่นเดียวกับไฟล์ทุกไฟล์ เราต้องการเก็บไฟล์ HTML ลงบนฮาร์ดดิสก์ สำหรับอินเทอร์เน็ตนั้น เราใช้เครื่องคอมพิวเตอร์พิเศษ และทรงพลัง เรียก่วา *servers* คอมพิวเตอร์เหล่านี้ ไม่มีหน้าจอ เมาส์ หรือแป้นพิมพ์ เพราะหน้าที่หลักคือการเก็บข้อมูลและให้บริการข้อมูลเหล่านี้ นั่นคือที่มาของชื่อ *servers* เพราะพวกเขา *serve* ข้อมูลให้คุณ

แต่คุณอยากการรู้ว่าอินเทอร์เน็ตหน้าตาเป็นยังไง ใช่มั้ย?

เราวาดรูปมาให้คุณ! และมันหน้าตาแบบนี้:

![รูปที่ 1.1](images/internet_1.png)

ดูยุ่งเหยิง ไม่เป็นระเบียบ ใช่ไหม? จริงๆ มันคือเครือข่ายที่เชื่อมต่อเครื่องต่างๆ เข้าด้วยกัน (เครื่องที่ว่าก็คือ *servers* นั่นเอง) นับแสนเครื่อง! สายเคเบิ้ลไกลหลายกิโลเมตรทั่วโลก! คุณสามารถไปชมแผนที่เคเบิ้ลใต้น้ำได้ที่ (http://submarinecablemap.com) เพื่อดูว่าซับซ้อนขนาดไหน นี่เป็นภาพตัวตัวอย่างจากเว็บข้างต้น:

![รูปที่ 1.2](images/internet_3.png)

น่าสนใจใช่ไหม? But it is not possible to have a wire between every machine connected to the Internet. ดังนั้น การเข้าถึงเครื่อง (ตัวอย่างเช่นเครื่องที่เก็บเว็บ https://djangogirls.org ไว้) เราจำเป็นต้องผ่านการ ร้องขอ จำนวนมาก และผ่านหลายเครื่อง

หน้าตาประมาณนี้:

![รูปที่ 1.3](images/internet_2.png)

ลองนึกภาพว่า เมื่อคุณพิมพ์ http://djangogirls.org เป็นการส่งจดหมายเพื่อบอกว่า: "เฮ้ Django Girls เราอยากดูหน้าเว็บ djangogirls.org จัง ได้โปรดช่วยส่งมันมาให้ฉันดูหน่อย!"

จดหมายของคุณส่งไปยังที่ไปรษณีย์ใกล้บ้านคุณ และมันก็ถูกส่งต่อไปยังที่อื่นที่อยู่ห่างบ้านคุณไปนิดหน่อย และส่งไปเรื่อยๆ ไปเรื่อยๆ จนกระทั่งถึงปลายทาง สิ่งที่เป็นเอกลักษณ์คือ ถ้าคุณส่งจดหมายจำนวนมาก (*data packets*) ไปยังที่เดิม จดหมายเหล่านั้นจะถูกส่งต่อไปยังไปรษณีย์อื่นๆ (*routers*) ที่แตกต่างกันโดยสิ้นเชิง ขึ้นกับว่าพวกเขากระจายแต่ละสำนักงานยังไง

![รูป 1.4](images/internet_4.png)

That's how it works - you send messages and you expect some response. Instead of paper and pen you use bytes of data, but the idea is the same!

แทนที่จะเป็นที่อยู่ ชื่อถนน ชื่อเมือง รหัสไปรษณีย์และชื่อประเทศ เราจะใช้ที่อยู่ IP แทน เครื่องคอมของคุณจะถามไปยัง DNS (Domain Name System) ที่จะแปลงชื่อ djangogirls.org ไปเป็นที่อยู่ IP ก่อน มันทำงานคล้ายๆ กับสมุดโทรศัพท์สมัยก่อน ซึ่งคุณสามารถหาเบอร์โทรศัพท์และที่อยู่จากชื่อที่อยู่ในสมุดโทรศัพท์ได้

เมื่อคุณต้องการส่งจดหมาย คุณต้องใช้สิ่งอื่นร่วมด้วยเพื่อให้การส่งถูกต้อง: คือ ที่อยู่ สแตมป์ ฯลฯ คุณใช้ภาษาที่ผู้รับจดหมายเข้าใจด้วย ถูกมั้ย? เช่นเดียวกันกับ *data packets* ที่ส่งไปเพื่อขอดูเว็บไซต์ เราใช้กระบวนการหรือ protocol ที่เรียกว่า HTTP (Hypertext Transfer Protocol)

ดังนั้น โดยทั่วไป หากคุณมีเว็บไซต์ คุณต้องมี *server* (เครื่อง) ที่เก็บเว็บไซต์ เมื่อ *server* ได้รับ *request* เข้ามา (มีจดหมายส่งมา) มันจะส่งเว็บไซต์กลับไป (จดหมายตอบกลับ)

คุณคงสงสัย นี่คือบทเรียน Django แล้ว Django ทำอะไรบ้าง เมื่อคุณต้องการตอบกลับ คุณไม่จำเป็นต้องส่งข้อมูลที่เหมือนๆ กัน ไปยังทุกคน มันจะดีกว่ามาก ถ้าจดหมายของคุณนั้นส่งไปในรูปแบบส่วนบุคคล โดยเฉพาะอย่างยิ่งสำหรับคุณที่เขียนถึงคุณ ถูกไหม? Django ช่วยคุณสร้างสิ่งเหล่านั้น ทำให้เป็นจดหมายที่น่าสนใจยิ่ง. :)

เอาล่ะพูดเยอะแล้ว เรามาเริ่มทำกันเลยดีกว่า!