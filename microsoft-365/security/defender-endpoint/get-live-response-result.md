---
title: الحصول على نتائج استجابة مباشرة
description: تعرف على كيفية استرداد نتيجة أمر استجابة مباشرة محددة بواسطة الفهرس الخاص بها.
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
ms.openlocfilehash: bd8b3c997a8efceb2791eca4de0b0e42d47513f8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63571708"
---
# <a name="get-live-response-results"></a>الحصول على نتائج استجابة مباشرة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>وصف API

استرداد نتيجة أمر استجابة مباشرة محددة بواسطة الفهرس الخاص بها.

## <a name="limitations"></a>القيود

1. قيود السعر ل API هذه هي 100 مكالمة في الدقيقة و1500 مكالمة في الساعة.

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
Application|Machine.Read.All|'قراءة كل ملفات تعريف الجهاز'
Application|"Machine.ReadWrite.All|"قراءة كل معلومات الجهاز وكتابتها"
|مفوض (حساب العمل أو المدرسة)|Machine.LiveResponse|تشغيل الاستجابة المباشرة على جهاز معين|

## <a name="http-request"></a>طلب HTTP

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/{machine action
id}/GetLiveResponseResultDownloadLink(index={command-index})
```

## <a name="request-headers"></a>طلب رؤوس

|الاسم|النوع|الوصف|
|---|---|---|
|التخويل|سلسلة|حامل {token}. مطلوب.|

## <a name="request-body"></a>طلب الحصول على "هيئة"

فارغ

## <a name="response"></a>الاستجابة

إذا نجح هذا الأسلوب، فيرجع رمز الاستجابة 200، موافق مع كائن يحتفظ بالارتباط إلى نتيجة الأمر في *خاصية* القيمة. هذا الارتباط صالح لمدة 30 دقيقة ويجب استخدامه على الفور لتنزيل الحزمة إلى مساحة تخزين محلية. يمكن إعادة إنشاء ارتباط منتهية الصلاحية بواسطة مكالمة أخرى، ولا حاجة لتشغيل الاستجابة المباشرة مرة أخرى.

*خصائص نسخة Runscript:*

|الخاصية|الوصف|
|---|---|
|script_name|اسم البرنامج النصي الذي تم تنفيذه|
|exit_code|رمز إنهاء البرنامج النصي الذي تم تنفيذه|
|script_output|الإخراج القياسي للنص الذي تم تنفيذه|
|script_errors|إخراج الخطأ القياسي للنص النصي المنفذ|

## <a name="example"></a>مثال

### <a name="request-example"></a>مثال على طلب

فيما يلي مثال على الطلب.

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/GetLiveResponseResultDownloadLink(index=0)
```

### <a name="response-example"></a>مثال على الاستجابة

فيما يلي مثال على الاستجابة.

HTTP/1.1 200 Ok

نوع المحتوى: التطبيق/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Edm.String",
    "value": "https://core.windows.net/investigation-actions-data/ID/CustomPlaybookCommandOutput/4ed5e7807ad1fe59b00b664fe06a0f07?se=2021-02-04T16%3A13%3A50Z&sp=r&sv=2019-07-07&sr=b&sig=1dYGe9rPvUlXBPvYSmr6/OLXPY98m8qWqfIQCBbyZTY%3D"
}
```

*محتوى الملف:*

```JSON
{
    "script_name": "minidump.ps1",
    "exit_code": 0,
    "script_output": "Transcript started, output file is C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Temp\\PSScriptOutputs\\PSScript_Transcript_{TRANSCRIPT_ID}.txt
C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip\n51 MB\n\u0000\u0000\u0000",
    "script_errors":""
}
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الحصول على API للعمل على الجهاز](get-machineaction-object.md)
- [إجراء إلغاء الجهاز](cancel-machine-action.md)
- [تشغيل الاستجابة المباشرة](run-live-response.md) 
