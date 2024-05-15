# Newman level3
การใช้ global variable บน Newman สามารถทำได้ 2 วิธี 
1. ประกาศค่า global variable ผ่าน command โดยใช้ command newman run --global-var < global variable ที่ต้องการใช้ > < ไฟล์ collection  >
    ```sh
        newman run --global-var id=1 Global_Variables.postman_collection.json
    ```    
2. เรียกใช้ global variable ผ่าน ไฟล์ โดยใช้ command newman run --globals < ไฟล์ global variable > < ไฟล์ collection  >
    ```sh
        newman run --globals globalfile.json Global_Variables.postman_collection.json
    ```    