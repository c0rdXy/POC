## Vulnerability Author: 

c0rdXy

## Affected Version: 

PublicCMS V4.0.202406.f

![image](https://github.com/user-attachments/assets/29ef1aad-0bd5-40e4-a85c-e6df15e0cb6d)


## Vendor:

www.publiccms.com

https://github.com/sanluan/PublicCMS

https://github.com/sanluan/PublicCMS/releases

## Vulnerability File:

PublicCMS-V4.0.202406.f\publiccms-parent\publiccms-core\src\main\java\com\publiccms\controller\admin\cms\CmsSurveyAdminController.java

## Vulnerability Description:

PublicCMS V4.0.202406.f was discovered to contain a cross-site scripting (XSS) vulnerability via a crafted script to the Category Managment feature.

## Vulnerability hazards

After a successful attack using XSS code, malicious users may get high permissions. The XSS vulnerability mainly has the following hazards:

1. Steal various user accounts;
2. Steal the user's Cookie information, impersonate the user's identity to enter the website;
3. Hijack user sessions and perform arbitrary operations; Refers to operating the user's browser;
4. Brush stream display, execution of commercial advertising;
5. Spread worms;
6. And so on...

## Payload

Open the questionnaire management function node in the content function area and click Add.

打开内容功能区中的问卷调查管理功能点，点击添加按钮。

![image](https://github.com/user-attachments/assets/68ef347a-6ada-41f9-92bd-2eaf4fd45013)

Insert XSS malicious code and click Save.

插入XSS恶意代码，然后点击保存。

![image](https://github.com/user-attachments/assets/f4c6a937-8eae-4b68-9b01-a873a081621a)

![image](https://github.com/user-attachments/assets/5594e209-dace-41f1-8327-ab9c4fab9fc1)

Click the title of the questionnaire just added to trigger the XSS vulnerability.

点击刚添加的调查问卷的标题，触发XSS漏洞。

![image](https://github.com/user-attachments/assets/dd2a51df-9d78-4286-bcf5-2c66063c8c6c)

![image](https://github.com/user-attachments/assets/024c087b-4be7-482d-a3ec-200a67074fc8)

After debugging the background code, it was found that the input data was not inspected and entity coded, resulting in an XSS vulnerability.

对后台代码进行调试，发现未对所输入的数据进行检验以及实体化编码，导致形成XSS漏洞。

![image](https://github.com/user-attachments/assets/29084efc-fa77-45d7-8ab9-c76371524694)

## Modification suggestion

It is recommended to encode the input and output parameters in an entity format.
建议对输入输出参数进行实体化编码。
