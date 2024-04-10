# Automantion Test Postman Level 1

ก่อนที่จะไปเริ่มฝึกโจทย์ มาทำความรู้จักกับ Postman ก่อนที่ Level 0


โจทย์ตัวอย่างนี้จะเป็นโจทย์การทดสอบการสั่งซื้อสินค้า
โดยจะมี API Specification ให้ตามนี้ https://github.com/SCK-SEAL-TEAM-One/sck-online-store/wiki/API-Specification

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
ถ้า API ทำงานถูกต้อง ผล Test Results ต้องออกมาเป็น PASS 6/6

![Test](/images/testrespond.png)

# API Search Product


1. เลือก METHOD ของ request เป็น GET

    ![images](/images/METHOD.png)

2. ตั้งค่า URL เป็น http://188.166.247.72/api/v1/product/1

    ![images](/images/urlproductDetail.png)

3. เมื่อกดส่ง request จะได้ response ตามนี้
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

- เหมือนกับเส้น API ก่อนหน้านี้ เราควรเขียน test script ให้มาทดสอบใน request แทนการใช้สายตาตรวจสอบเพื่อให้ง่ายต่อการอ่านเราสามารถใช้ภาษาไทยเขียนชื่อ test script ได้
    ```sh
    var jsonData = pm.response.json();

    pm.test("Status code is 200", function () {
        pm.response.to.have.status(200);
    });

    pm.test("ตรวจสอบ product id เท่ากับ 1", function () {
        pm.expect(jsonData.id).to.eql(1);
    });

    pm.test("ตรวจสอบชื่อสินค้า Balance Training Bicycle", function () {
        pm.expect(jsonData.product_name).to.eql("Balance Training Bicycle");
    });

    pm.test("ตรวจสอบราคาสินค้า USD เท่ากับ 119.95", function () {
        pm.expect(jsonData.product_price).to.eql(119.95);
    });

    pm.test("ตรวจสอบราคาสินค้า THB เท่ากับ 4314.60", function () {
        pm.expect(jsonData.product_price_thb).to.eql(4314.60);
    });

    pm.test("ตรวจสอบราคาสินค้า THB เต็มเท่ากับ 4314.597182", function () {
        pm.expect(jsonData.product_price_full_thb).to.eql(4314.597182);
    });

    pm.test("ตรวจสอบproduct_image เท่ากับ /Balance_Training_Bicycle.png", function () {
        pm.expect(jsonData.product_image).to.eql("/Balance_Training_Bicycle.png");
    });

    ```

- ถ้า API ทำงานถูกต้อง ผล Test Results ต้องออกมาเป็น PASS 7/7
    ![images](/images/responseProductDetail.png)

# API Submit Order

1. เลือก METHOD ของ request เป็น POST

    ![images](/images/post.png)

2. ตั้งค่า URL เป็น {{BASE_URL}}/api/v1/order

    ![images](/images/urlsubmitorder.png)

3. ตั้งค่า Request Header

    ```sh
    {
    "Content-Type": "application/json"
    }
    ```
    ![images](/images/headersSubmitorder.png)

3. ตั้งค่า Body
    ```sh
            {
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
- เหมือนกับเส้น API ก่อนหน้านี้ เราควรเขียน test script ให้มาทดสอบใน request แทนการใช้สายตาตรวจสอบเพื่อให้ง่ายต่อการอ่านเราสามารถใช้ภาษาไทยเขียนชื่อ test script ได้
    ```sh
    {
    
    }
    ```
- ถ้า API ทำงานถูกต้อง ผล Test Results ต้องออกมาเป็น PASS 7/7
    ![images](/images/responseProductDetail.png)


# API : Confirm Payment
1. เลือก METHOD ของ request เป็น POST

    ![images](/images/post.png)

2. ตั้งค่า URL เป็น {{BASE_URL}}/api/v1/confirmPayment

    ![images](/images/urlsubmitorder.png)

3. ตั้งค่า Body

    ```sh
    {
    "order_id": 8004359122,
    "otp": 124532,
    "ref_otp": "AXYZ"
    }
    ```