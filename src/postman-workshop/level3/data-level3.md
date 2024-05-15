# Data postman level 3
จาก Data postman level 2 จะสังเกตุว่า หากชุดข้อมูลมีจำนวนมากก็จะใช้เวลามากขึ้นในการ เปลี่ยน value ให้เป็น variable ยึ่งมี collection มากเวลาที่ใช้ก็มากตามไปด้วย เราสามารถลดเวลาได้ด้วยการ 

1. สร้าง variable ไว่ใน requset body 
    ![Postman datalevel3](/images/DataLevel3.png)
2. เข้าไปที่ไฟล์ data แล้วนำ data ที่เราต้องการทดสอบ ใส่ไว้ใน key ชื่อเดียวกับ requset body 
    ```sh
        "order": {
                "cart": [
                    {
                    "product_id": 1,
                    "quantity": 1
                    }
                ],
                "burn_point": 0,
                "sub_total_price": 4314.6,
                "discount_price": 0,
                "total_price": 4364.6,
                "shipping_method_id": 1,
                "shipping_address": "189/413 หมู่ 2",
                "shipping_sub_district": "แพรกษาใหม่",
                "shipping_district": "เมืองสมุทรปราการ",
                "shipping_province": "สมุทรปราการ",
                "shipping_zip_code": "10280",
                "recipient_first_name": "พงศกร",
                "recipient_last_name": "รุ่งเรืองทรัพย์",
                "recipient_phone_number": "090912799",
                "payment_method_id": 1,
                "payment_information": {
                    "card_name": "พงศกร รุ่งเรืองทรัพย์",
                    "card_number": "4719 7005 9159 0995",
                    "expire_date": "02/26",
                    "cvv": "75"
                }
            }
    ```
# Get data from respond
เมื่อเจอเคสที่ ต้องรับค่าจาก request ที่ 1 ไปใช้ใน request ที่ 2 เช่น request ที่ 1 สร้าง order id request ที่ 2 ตรวจสอบ order id ของ request ที่ 1 สามารถทำได้โดยใช้

    
        pm.test("ออเดอร์ ID ต้องได้รับค่า" + jsonData.order_id, function () {
            pm.collectionVariables.set("orderid", jsonData.order_id);
        });
    
