# Automantion Test Postman Level 1
โจทย์ตัวอย่างนี้จะเป็นโจทย์การทดสอบการสั่งซื้อสินค้า

เริ่มจากการสร้าง collection ใน postman
และเริ่ม add request ลงใน collection

ใน request แรก เราจะมาเริ่มจาก API Search Product

1. เลือก METHOD ของ request เป็น GET

2. ตั้งค่า URL เป็น http://188.166.247.72/api/v1/product?q=Bicycle&offset=0&limit=20

3. ตั้งค่า Query Params เป็น

    | key           |            Value               |
    |---------------|--------------------------------|
    | q             |           Bicycle              |
    | offset        |               0                |
    | limit         |               20               |

4. เมื่อกดส่ง request จะได้ response ตามนี้
    ```sh
    status code : 200 
            {
            "total": 2,
            "products": [
                    {
                        "id": 1,
                        "product_name": "Balance Training Bicycle",
                        "product_price": 119.95,
                        "product_price_thb": 4314.6,
                        "product_price_full_thb": 4314.597182,
                        "product_image": "/Balance_Training_Bicycle.png"
                    },
                    {
                        "id": 2,
                        "product_name": "43 Piece dinner Set",
                        "product_price": 12.95,
                        "product_price_thb": 465.81,
                        "product_price_full_thb": 465.811034,
                        "product_image": "/43_Piece_dinner_Set.png"
                    }
                ]
            }
    ```