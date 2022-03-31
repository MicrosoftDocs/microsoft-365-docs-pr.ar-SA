---
title: تشغيل أوامر الاستجابة المباشرة على جهاز
description: تعرف على كيفية تشغيل سلسلة من أوامر الاستجابة المباشرة على جهاز.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، التحميل إلى المكتبة
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: e81c235105a7c7479a917c7cb7cc404e2553f2f1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63578262"
---
# <a name="run-live-response-commands-on-a-device"></a>تشغيل أوامر الاستجابة المباشرة على جهاز

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)


[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

تشغيل تسلسل أوامر الاستجابة المباشرة على جهاز

## <a name="limitations"></a>القيود

1. حدود السعر ل API هذه هي 10 مكالمات في الدقيقة (يتم الرد على طلبات إضافية باستخدام HTTP 429).

2. 25 جلسة عمل يتم تشغيلها بشكل متزامن (ستتلقى الطلبات التي تتجاوز حد تقييد المستخدم استجابة "429 - عدد كبير جدا من الطلبات").

3. إذا لم يكن الجهاز متوفرا، سيتم إعداد جلسة العمل في قائمة الانتظار لمدة تصل إلى 3 أيام.

4. تشغيل 20 دقيقة من انتهاء 10 دقائق.

5. لا يمكن أن تكون أوامر الاستجابة المباشرة في قائمة الانتظار ويمكن تنفيذها واحدة فقط في كل مرة.

6. إذا كان الجهاز الذي تحاول تشغيل استدعاء API هذا في مجموعة أجهزة RBAC لم يتم تعيين مستوى المعالجة التلقائية له، ستحتاج على الأقل إلى تمكين الحد الأدنى لمستوى المعالجة لمجموعة أجهزة معينة.

7. يمكن تشغيل أوامر استجابة مباشرة متعددة في مكالمة API واحدة. ومع ذلك، عندما يفشل أمر استجابة مباشرة، لن يتم تنفيذ جميع الإجراءات التالية.

## <a name="minimum-requirements"></a>الحد الأدنى للمتطلبات

قبل أن تتمكن من بدء جلسة عمل على جهاز، تأكد من استيفاء المتطلبات التالية:

- **تحقق من أنك تقوم بتشغيل إصدار** معتمد من Windows.

  يجب أن تكون الأجهزة قيد تشغيل أحد الإصدارات التالية من Windows

  - **Windows 11**
  
  - **Windows 10**
    - [الإصدار 1909 أو](/windows/whats-new/whats-new-windows-10-version-1909) الإصدارات الأحدث
    - [الإصدار 1903 مع](/windows/whats-new/whats-new-windows-10-version-1903) [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [الإصدار 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) مع [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [الإصدار 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) مع [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [الإصدار 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) مع [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **Windows Server 2019 - ينطبق فقط على المعاينة العامة**
    - الإصدار 1903 أو ([مع KB4515384) لاحقا](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - الإصدار 1809 ( [مع KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

## <a name="permissions"></a>الأذونات

أحد الأذونات التالية مطلوبة لاستدعاء API هذه. لمعرفة المزيد، بما في ذلك كيفية اختيار الأذونات، راجع [بدء العمل](apis-intro.md).

|نوع الإذن|الإذن|اسم عرض الأذونات|
|---|---|---|
|Application|Machine.LiveResponse|تشغيل الاستجابة المباشرة على جهاز معين|
|مفوض (حساب العمل أو المدرسة)|Machine.LiveResponse|تشغيل الاستجابة المباشرة على جهاز معين|

## <a name="http-request"></a>طلب HTTP

```HTTP
POST https://api.securitycenter.microsoft.com/API/machines/{machine_id}/runliveresponse
```

## <a name="request-headers"></a>طلب رؤوس

|الاسم|النوع|الوصف|
|---|---|---|
|التخويل|سلسلة|حامل\<token>\. مطلوب.|
|نوع المحتوى|سلسلة|application/json. مطلوب.|

## <a name="request-body"></a>طلب الحصول على "هيئة"

|المعلمة|النوع|الوصف|
|---|---|---|
|تعليق|سلسلة|التعليق على إقران الإجراء.|
|الأوامر|صفيف|الأوامر التي يجب تشغيلها. القيم المسموح بها هي PutFile و RunScript و GetFile.|

## <a name="commands"></a>الأوامر

|نوع الأمر|المعلمات|الوصف|
|---|---|---|
|PutFile|المفتاح: FileName <p> القيمة: \<file name\>|يضع ملفا من المكتبة على الجهاز. يتم حفظ الملفات في مجلد عمل، كما يتم حذفها عند إعادة تشغيل الجهاز بشكل افتراضي.
|RunScript|المفتاح: ScriptName <br> القيمة: \<Script from library\> <p> المفتاح: Args <br> القيمة: \<Script arguments\>|تشغيل برنامج نصي من المكتبة على جهاز. <p>  يتم تمرير معلمة Args إلى البرنامج النصي. <p> المهات بعد 10 دقائق.|
|GetFile|المفتاح: المسار <br> القيمة: \<File path\>|تجميع ملف من جهاز. ملاحظة: يجب أن يتم تحرير رموش مبللة بالخلف في المسار.|

## <a name="response"></a>الاستجابة

- إذا نجح هذا الأسلوب، فيرجع 201 تم إنشاؤه.

  كيان الإجراء. إذا لم يتم العثور على الجهاز الذي به الم ID المحدد - 404 لم يتم العثور عليه.

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```HTTP
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runliveresponse

```JSON
{
   "Commands":[
      {
         "type":"RunScript",
         "params":[
            {
               "key":"ScriptName",
               "value":"minidump.ps1"
            },
            {
               "key":"Args",
               "value":"OfficeClickToRun"
            }

         ]
      },
      {
         "type":"GetFile",
         "params":[
            {
               "key":"Path",
               "value":"C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
            }
         ]
      }
   ],
   "Comment":"Testing Live Response API"
}
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

```HTTP
HTTP/1.1 200 Ok
```

نوع المحتوى: التطبيق/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "{machine_action_id}",
    "type": "LiveResponse",
    "requestor": "analyst@microsoft.com",
    "requestorComment": "Testing Live Response API",
    "status": "Pending",
    "machineId": "{machine_id}",
    "computerDnsName": "hostname",
    "creationDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "lastUpdateDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "errorHResult": 0,
    "commands": [
        {
            "index": 0,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "RunScript",
                "params": [
                    {
                        "key": "ScriptName",
                        "value": "minidump.ps1"
                    },{
                        "key": "Args",
                        "value": "OfficeClickToRun"
                    }
                ]
            }
        }, {
            "index": 1,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "GetFile",
                "params": [{
                        "key": "Path", "value": "C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
                    }
                ]
            }
        }
    ]
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الحصول على API للعمل على الجهاز](get-machineaction-object.md)
- [الحصول على نتيجة استجابة مباشرة](get-live-response-result.md)
- [إجراء إلغاء الجهاز](cancel-machine-action.md)
