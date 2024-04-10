# Automantion Test Postman Level 1
โจทย์ตัวอย่างนี้จะเป็นโจทย์การทดสอบการสั่งซื้อสินค้า ซึ่งประกอบด้วย API 4 เส้น

เริ่มจากการสร้าง collection ใน postman
และเริ่ม add request ลงใน collection

ใน request แรก เราจะมาเริ่มจาก 

# API Search Product


1. เลือก METHOD ของ request เป็น GET

    ![images](/images/METHOD.png)

2. ตั้งค่า URL เป็น http://188.166.247.72/api/v1/product?q=Bicycle&offset=0&limit=20

    ![images](/images/url.png)


3. ตั้งค่า Query Params เป็น


    ![images](/images/params.png)

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

ถ้าสังเกต ในส่วนของ response ตรง Tests จะยังไม่มีอะไรขึ้นเลย เพราะเรายังไม่ได้เขียน test script ให้มาทดสอบใน request นี้ 

![Test](/images/Test.png)

โดยสิ่งที่เราควรตรวจอย่างแรกว่า API ทำงานได้ปกติคือ status code = 200 

```sh
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });
```
ตรวจสอบจำนวนสินค้า เท่ากับ 29 รายการ

```sh
        pm.test("ตรวจสอบจำนวนสินค้า เท่ากับ 29 รายการ", function () {
            var jsonData = pm.response.json();
            pm.expect(jsonData.total).to.eql(29);
        });
 ```

ตรวจสอบไอดีสินค้า เท่ากับ 1

```sh
        pm.test("ตรวจสอบไอดีสินค้า เท่ากับ 1", function () {
            var jsonData = pm.response.json();
            pm.expect(jsonData.products[0].id).to.eql(1);
        });
 ```

ตรวจสอบชื่อสินค้า Balance Training Bicycle

```sh
        pm.test("ตรวจสอบชื่อสินค้า Balance Training Bicycle", function () {
            var jsonData = pm.response.json();
            pm.expect(jsonData.products[0].product_name).to.eql("Balance Training Bicycle");
        });
 ```

ตรวจสอบราคาสินค้า USD เท่ากับ 119.95

```sh
        pm.test("ตรวจสอบราคาสินค้า USD เท่ากับ 119.95", function () {
            var jsonData = pm.response.json();
            m.expect(jsonData.products[0].product_price).to.eql(119.95);
        });

 ```

ตรวจสอบราคาสินค้า THB เท่ากับ 4314.60

```sh
        pm.test("ตรวจสอบราคาสินค้า THB เท่ากับ 4314.60", function () {
            pm.expect(jsonData.products[0].product_price_thb).to.eql(4314.60);
            var jsonData = pm.response.json();
        });
 ```
ถ้า API ทำงานถูกต้อง ผล Test ตรง response ต้องออกมาเป็น success 6/6

![Test](/images/testrespond.png)

# API Search Product


1. เลือก METHOD ของ request เป็น GET

    ![images](/images/METHOD.png)

2. ตั้งค่า URL เป็น http://188.166.247.72/api/v1/product/1

    ![images](/images/urlproductDetail.png)

4. เมื่อกดส่ง request จะได้ response ตามนี้
    ```sh
        {
            "id": 1,
            "product_name": "Balance Training Bicycle",
            "product_price": 119.95,
            "product_price_thb": 4314.6,
            "product_price_full_thb": 4314.597182,
            "product_image": "/Balance_Training_Bicycle.png",
            "stock": 100,
            "product_brand": "SportsFun"
        }
    ```