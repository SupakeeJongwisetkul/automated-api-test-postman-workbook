# Chapter 1
## Software Process Development and Test Development

> สามารถเข้าไปดูได้ที่บอร์ด [MiroBoard](https://miro.com/app/board/uXjVKZPHSL4=/)

ในที่นี้ จะให้ความสำคัญของการทำ Functional Automation Test ในระดับ API เนื่องจากว่า
1. การทดสอบทำงานได้เร็วขึ้นและลดการใช้คนในการทำการทดสอบ
2. มีความเสถียรมากกว่า เนื่องจากหน้าจอ มีโอกาสที่จะเปลี่ยนแปลงได้บ่อย
3. สามารถตรวจจับข้อบกพร่องในการทำงานของซอฟต์แวร์ได้ไวขึ้น

![Automation Test Target](/images/automation-tests-target.png)


###  Tools
| Tool         |            version             |  Download    |  Description   |
|---------------|--------------------------------|--------------|--------------|
| Visual Studio Code (vscode)    |   Windows 10,11 macOS 10.11 ขึ้นไป |  [vscode](https://code.visualstudio.com)      |       โปรแกรมแก้ไขโค้ด       |
| postman             |           10.23.5              |        [postman](https://www.postman.com/downloads/postman-agent/)      |       เครื่องมือสำหรับ Test API's       |
| Newman        |               6.1.2                |      [newman](https://www.npmjs.com/package/newman)        |       Run collection ของ postman บน terminal       |
| Htmlextra         |               1.23.1               |       [Htmlextra](https://www.npmjs.com/package/newman-reporter-htmlextra)        |       แสดง test report ของ newman        |
| mountebank         |               2.9.1              |       [mountebank](http://www.mbtest.org/docs/gettingStarted)        |       open source จำลอง พฤติกรรม server        |
