# Newman 
ในการใช้ Newman ในการ Run API Collection หากต้องการใช้ ไฟล์ environment กับ ไฟล์ data ประกอบสามารถทำได้โดย


1. สร้าง 3 โฟลเดอร์ใน level2 ประกอบด้วยโฟลเดอร์ postman โฟลเดอร์ environment โฟลเดอร์ data

2. Export collection ของ postman ลงใน โฟลเดอร์ postman 

3. Export environment ของ โฟลเดอร์ environment 

4. นำไฟล์ data ที่ต้องการ run ไว้ที่  โฟลเดอร์ data 

5. เปิด Terminal เข้าไปในโฟลเดอร์ที่ level2

6. ใช้ command newman run < ไฟล์ collection  > -e < ไฟล์ environment  > -d < ไฟล์ data  >
    ```sh
        newman run sck-shoping-mall-level -e sck-shopping-mall-local_environment.json -d data.json
    ```    
- เมื่อ run command newman แล้วจะได้ Report ที่ค่อนข้างดูยากบน Terminal หากอย่างได้ report ที่ดูง่าย สามารถใช้ htmaextea ได้โดยใข้ command

    ```sh
        newman run -r htmlextra sck-shoping-mall-level -e sck-shopping-mall-local_environment.json -d data.json
    ```    