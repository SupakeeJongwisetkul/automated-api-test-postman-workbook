# global variable
หากต้องการนำ value ไปใช้ข้าม collection สามารถประกาศเป็นตัวแปร global variable สำหรับเก็บค่า value ได้โดย
1. Highlight ข้อความที่ต้องการประกาศเป็น global variable 
2. เลือก Set as Variable
3. เลือก Set as a new variable
4. กำหนดชื่อตัวแปร, ค่าของตัวแปรและ เลือก Scope เป็น global variable

หรือใช้ Test script สำหรับ ประกาศเป็นตัวแปร global variable ได้โดย 
```sh
    pm.globals.set("ชื่อตัวแปร", "ค่าตัวแปร") 

```    