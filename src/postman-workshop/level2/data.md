# Data postman level 2
หากเราต้องการที่จะ ทดสอบ Test scenario เดียวจำนวนมากกว่า 1 ครั้งโดยใช้ data ที่ต่างกัน สามารถทำได้ 2 วิธี 
    1 คือ สร้าง collection ใหม่แล้วแก้ไขข้อมูล วิธีนี้จะมีข้อเสียที่จะต้องสร้าง collection มากตาม data ที่ต้องการทดสอบ
    2 สร้างไฟล์ data แล้วนำมาใช้ Run collection บน postman วิธีนี้สามารถใช้ 1 collection ในการ run ซ้ำตามจำนวนชุดของข้อมูลในไฟล์ Data ได้
postman สามารถรับค่า data ได้จากไฟล์ 2 แบบ 

1. ไฟล์ .json
    ตัวอย่างไฟล์ .json
    ```sh
        [
            {
                "q": "Bicycle",
                "offset": 0,
                "limit": 20,
                "productId": 1,
                "quantity": 1,
                "burnPoint": 0,
                "subTotalPrice": 4314.6,
                "discountPrice": 0,
                "totalPrice": 4364.6,
                "shippingMethodId": 1,
                "shippingAddress": "189/413หมู่2",
                "shippingSubDistrict": "แพรกษาใหม่",
                "shippingDistrict": "เมืองสมุทรปราการ",
                "shippingProvince": "สมุทรปราการ",
                "shippingZipCode": "10280",
                "recipientFirstName": "พงศกร",
                "recipientLastName": "รุ่งเรืองทรัพย์",
                "recipientPhoneNumber": "090912799",
                "paymentMethodId": 1,
                "cardName": "พงศกรรุ่งเรืองทรัพย์",
                "cardNumber": "4719700591590995",
                "expireDate": "02/26",
                "cvv": "75",
                "otp": 124532,
                "refOtp": "AXYZ",
                "expected": {
                "responseTime": 500,
                "productName": "Balance Training Bicycle",
                "productPrice": 119.95,
                "productPriceThb": 4314.6,
                "productPriceFullThb": 4314.597182,
                "total": 29,
                "productImage": "/Balance_Training_Bicycle.png",
                "trackingNumberPrefix": "KR-"
                }
            }
        ]
    ```
2. ไฟล์ .csv
    ตัวอย่างไฟล์ .csv    
    ```sh
        "q","offset","limit"
        "Bicycle",0,20
    ```

หากต้องการนำ data จากไฟล์ ข้างนอกมาใช้งานใน body สามารถทำได้โดย


1. แทนค่า value ด้วยตัวแปลของค่าที่ต้องการเอามาแทนและตั้งค่าตัวแปลนั้นเป็น variable
     ![Postman Structure](/images/usedata-in-body.png)

2. เมื่อเราจะใช้งาน data จากไฟล์อื่นเราไม่สามารถ run ด้วยวิธีปกติได้ต้อง run collection เท่านั้น เมื่อกด run collection ให้ไปที่ select file ตรง data จากนั้นให้เลือกไฟล์ data ที่ต้องการใช้งาน 
    ![Postman Structure](/images/selectdata.png)

3. เราสามารถกด preview เพื่อดู data ที่เราเอาเข้ามาใช้งานได้
    ![Postman Structure](/images/file-data.png)

