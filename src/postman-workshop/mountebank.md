# mountebank
ในการทดสอบ E2E ผ่านทาง api อาจมีบาง service ที่ไม่สามารถยิง api ไปต่อได้โดยตรงเช่น Third party เป็นต้น เพื่อให้สามารถ run E2E test ต่อได้ เราสามารถใช้ mountebank ในการจำลองพฤติกรรม service ที่เราต้องการทดสอบได้ 

วิธีใช้งาน

1. install mountebank 
```sh
        npm install -g mountebank
```
2. สร้างไฟล์ imposter.json โจทย์ตัวอย่าง เมื่อยิง api เสั้น จะต้องขึ้นว่า status processing ในครั้งที่ 1 ถึงครั้งที่ 4 และจะ ขึ้น status completed ในครั้งที่ 5 
```sh
{
  "port": 8882,
  "protocol": "http",
  "defaultResponse": {
    "statusCode": 400,
    "headers": {
      "Connection": "Keep-Alive",
      "Content-Length": 0
    }
  },
  "stubs": [
    {
      "name": "long process",
      "predicates": [
        {
          "equals": {
            "method": "GET",
            "path": "/api/v1/status"
          }
        }
      ],
      "responses": [
        {
          "is": {
            "statusCode": 200,
            "headers": {
              "Content-Type": "application/json; charset=utf-8"
            },
            "body": {
              "status": "processing"
            }
          }
        },
        {
          "is": {
            "statusCode": 200,
            "headers": {
              "Content-Type": "application/json; charset=utf-8"
            },
            "body": {
              "status": "processing"
            }
          }
        },
        {
          "is": {
            "statusCode": 200,
            "headers": {
              "Content-Type": "application/json; charset=utf-8"
            },
            "body": {
              "status": "processing"
            }
          }
        },
        {
          "is": {
            "statusCode": 200,
            "headers": {
              "Content-Type": "application/json; charset=utf-8"
            },
            "body": {
              "status": "processing"
            }
          }
        },
        {
          "is": {
            "statusCode": 200,
            "headers": {
              "Content-Type": "application/json; charset=utf-8"
            },
            "body": {
              "status": "completed"
            }
          }
        }
      ]
    }
  ]
}
```
3. start mountebank
```sh
	mb start --configfile imposter.json 
```
ถ้าสามารถ start mountebank ลองใช้ postman ทดสอบ mountebank ที่ start ขึ้นมาโดย
1. สร้าง collection ใหม่แล้ว add requet ใน collection และ set METHOD ก้บ URL ตามที่ได้จำลองไว้

![images](/images/postmanMounetbankPart.png)
2. ในการทดสอบนี้จะสั้งเกตได้ว่ามีการยิง api ไปที่เส้นเดิม 5 ครั้ง ซึ่งสามารถทำได้ 2 วิธี 
- วิธีแรก สร้าง 5 request สำหรับการยิง api 5 ครั้ง 
![images](/images/requsrtMountebank.png)
- วิธีที่สองสร้าง request เดียว แต่ใช้ loop ยิง จนครบ 5 ครั้ง

    เริ่มจาก ประกาษตัวแปรเก็บค่า loop ใน pre-request และจะบวก 1 ทุกครั้งที่มีการเรียกใช้ request นี้ซ้ำ
    ![images](/images/preTest.png)
    หลักจากนั้นไปที่ post-response รับค่าตัวแปรจาก post request มาตรวจสอบ ถ้าอยู่ในช่วงครั้งที่ 1 - 4 ต้องขึ้น  status processing และ status completed ในครั้งที่ 5 จากนั้นจบการทำงาน

```sh
        npm install -g mountebank
```

```sh
        pm.test("Status code is 200", function () {
        pm.response.to.have.status(200);
        });

        pm.test("Response time is less than 200ms", function () {
            pm.expect(pm.response.responseTime).to.be.below(200);
        });

        pm.test("Your test name", function () {
            var jsonData = pm.response.json();
            let counter = pm.collectionVariables.get("counter");

            if(counter < 4) {
                pm.expect(jsonData.status).to.eql("processing");
                postman.setNextRequest("check-status");
            } else {
                pm.expect(jsonData.status).to.eql("completed");
            }
        });
 ```


