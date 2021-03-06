# Django Girls Tutorial

[![Gitter](https://badges.gitter.im/DjangoGirls/tutorial.svg)](https://gitter.im/DjangoGirls/tutorial)

> งานนี้ได้รับการอนุญาตภายใต้อนุญาตสร้างสรรค์คอมมอนส์ครีเอทีฟ 4.0 อินเตอร์เนชั่นแนล สำเนาใบอนุญาต ชม https://creativecommons.org/licenses/by-sa/4.0/thai

## ยินดีต้อนรับ

ยินดีต้อนรับเข้าสู่บทเรียนของ Django Girls! We are happy to see you here. :) In this tutorial, we will take you on a journey under the hood of web technologies, offering you a glimpse of all the bits and pieces that need to come together to make the web work as we know it.

As with all unknown things, this is going to be an adventure - but no worries, since you already worked up the courage to be here, you'll be just fine. :)

## บทนำ

คุณเคยรู้สึกไหมว่าโลกเราทุกวันนี้ มีเทคโนโลยีใหม่ๆมากขึ้นทุกวัน จนคุณตามไม่ทัน? และเคยรู้สึกไหมว่า ไม่มีแรงจูงใจที่จะเริ่มสร้างเว็บไซต์? เคยคิดไหมว่า โลกของการทำซอฟต์แวร์ช่างซับซ้อนมากเกินไปสำหรับคุณ หากจะลงมือทำเอง?

เรามีข่าวดีสำหรับคุณ! การเขียนโปรแกรมมันไม่ยากเหมือนอย่างที่คิด และเราจะโชว์ให้ดูถึงความสนุกของมัน

บทเรียนนี้ ไม่ได้ทำให้คุณกลายร่างเป็นโปรแกรมเมอร์ได้ในทันทีทันได้ ถ้าคุณต้องการที่จะเป็นโปรแกรมเมอร์ที่เก่ง คุณต้องการเวลาเพื่อเรียนรู้และฝึกฝน ไม่ว่าจะหลายเดือนหรือหลายปี แต่เราอยากจะแสดงให้คุณดูว่า การเขียนโปรแกรมหรือสร้างเว็บไซต์ไม่ได้ยุ่งยากอะไรขนาดนั้น เราจะพยายามอธิบายให้เข้าใจง่ายที่สุดเท่าที่จะทำได้ เพราะงั้นคุณไม่จำเป็นต้องกลัวอะไรเกี่ยวกับเทคโนโลยีสายนี้

เราหวังว่า จะทำให้คุณหลงรักเทคโนโลยีมากได้เท่าๆ กับที่พวกเรารักมัน!

## คุณจะได้เรียนรู้อะไรบ้างในบทเรียนนี้?

เมื่อคุณเรียนจนจบบทเรียนนี้แล้ว คุณจะสามารถสร้างเว็บแอพลิเคชั่นอย่างง่ายๆ และใช้งานได้จริง นั่นก็คือบล็อกของคุณเอง เราจะแสดงให้คุณดูว่าเราจะอัพโหลดบล็อกของคุณลงบนอินเตอร์เน็ตได้อย่างไร คนอื่นในโลกนี้ก็จะเห็นงานของคุณด้วยไง!

ซึ่งผลลัพธ์จะออกมาประมาณนี้ (อาจจะต่างจากนี้หน่อย แต่ไม่มาก):

![รูปที่ 0.1](images/application.png)

> หากคุณเรียนบทเรียนนี้ด้วยตัวคุณเอง โดยที่ไม่มีใครช่วยคุณ เรามีช่องทางให้คุณผ่านช่องทางสนทนา: !(https://badges. gitter. im/Join Chat. svg)![Gitter](https://badges.gitter.im/DjangoGirls/tutorial.svg) ซึ่งเราได้ขอให้โค้ชและคนที่เคยผ่านบทเรียนนี้มาช่วยตอบคำถามให้กับคนอื่นที่มาเรียนบทเรียนนี้ด้วย! อย่ากลัวที่จะถามคำถามนะ!</p> </blockquote> 
> 
> โอเค, [เรามาเริ่มกันเลยดีกว่า...](./how_the_internet_works/README.md)
> 
> ## การทำตามบทเรียนจากที่บ้าน
> 
> มันจะสุดยอดมากถ้าได้เป็นส่วนหนึ่งในการประชุมเชิงปฏิบัติการ Django Girls แต่เราตระหนักดีว่า มันไม่เสมอไปที่จะได้เข้าร่วม นี่คือเหตุผลที่เราแนะนำให้คุณลองทำตามบทเรียนนี้ที่บ้าน สำหรับผู้อ่านทางบ้าน ตอนนี้เรากำลังเตรียมวิดีโอที่จะช่วยให้การศึกษาบทเรียนด้วยตัวคุณเองง่ายยิ่งขึ้น มันยังอยู่ในระหว่างการดำเนินการ แต่จะมีการเพิ่มเนื้อหามากขึ้นในเร็วๆนี้ ที่ช่อง [Coding is for girls](https://www.youtube.com/channel/UC0hNd2uW8jTR5K3KBzRuG2A/feed) บน YouTube
> 
> ในบทที่เราครอบคลุมแล้ว จะมีการเชื่อมโยงไปยังวิดิโอที่เกี่ยวข้อง
> 
> ## เกี่ยวกับบทเรียนนี้ และ การร่วมพัฒนา
> 
> บทเรียนนี้ดูแลโดย [DjangoGirls](https://djangogirls.org/) ถ้าคุณเห็นข้อผิดพลาดหรืออยากจะอัปเดตบทเรียนนี้ กรุณา [ดูรายละเอียด แนวทางการร่วมพัฒนา](https://github.com/DjangoGirls/tutorial/blob/master/README.md).
> 
> ## คุณอยากที่จะช่วยเราแปลบทเรียนนี้เป็นภาษาอื่นๆ?
> 
> ขณะนี้ การแปลภาษาต่างๆสามารถทำได้ผ่านแพลตฟอร์ม crowdin.com ที่:
> 
> https://crowdin.com/project/django-girls-tutorial
> 
> หากภาษาของคุณไม่อยู่ในลิสต์ของ [crowdin](https://crowdin.com/) กรุณาแจ้งให้เราทราบโดยการ [เปิดประเด็นใหม่](https://github.com/DjangoGirls/tutorial/issues/new) และบอกเราว่าคุณต้องการให้เราเพิ่มภาษาอะไร