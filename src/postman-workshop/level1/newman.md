# Newman 
Newman เป็นครื่องมือที่ใช้ Run API Collection ของ Postman บน terminal

ขั้นตอนการใช้งาน
1. สร้าง 2 โฟลเดอร์ใน level1 ประกอบด้วยโฟลเดอร์ postman กับโฟลเดอร์ environment 

2. Export collection ของ postman ลงใน โฟลเดอร์ postman 

3. Export environment ของ โฟลเดอร์ environment 

4. เปิด Terminal เข้าไปในโฟลเดอร์ที่ level1

5. ใช้ command newman run < ไฟล์ collection  >
    ```sh
    {
        newman run sck-shoping-mall-level
    }
    ```    
