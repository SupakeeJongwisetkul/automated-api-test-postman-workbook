# Environment variable

ในการทำงานเราอาจจะมีหลาย Environment เช่น Dev Environment, QA Environment ,Local Environment 
เมื่อเราต้องการใช้งาน Test script กับหลาย environment แทนที่เราจะเปลี่ยนค่าบางอย่างสำหรับ Environment ที่ต่างกัน เราสามารถตั้งค่าที่เปลี่ยนทุก Environment เป็น Environment variable ได้ เพื่อที่จะเลือก Environment สำหรับการ run collection 

ตัวอย่างจากโจทย์เช่น 

การเปลี่ยน urls สำหรับ Test ใน local environment ใน collection ของการซื้อสินค้า มี 4 request จะต้องทำการเปลี่ยน urls ทั้งหมด 4  request

การตั้ง urls เป็น Environment variable มีขั้นตอนดังนี้ 

1. เพิ่ม environment 
2. ตั้งตัวแปลไว้ใช้เก็บค่า variable ซึ่งในโจทย์นี้ ตั้งตัวแปล BASE_URL ไว้ใช้เก็บค่า Urls แล้วกด save

จากใน workshop ได้สร้าง environment ได้แก่ 

sck-shopping-mall-dev

sck-shopping-mall-qa

sck-shopping-mall-local

ในส่วนของการใช้ environment มีขั้นตอนดังนี้

1. นำตัวแปลที่เราตั้งไว้ใน environment แทนที่ Urls จากโจทย์แทนที่ http://127.0.0.1 ด้วย BASE_URL

2. กลับไปที่ collection เลือก No environment แล้วเแลี่ยนเป็น environment ที่ต้องการใช้งาน 

3. เมื่อเปลี่ยน environment แล้วสามารถลอง run requset ดูว่าสามารถใช้งานได้ถูกต้องหรือไม่

