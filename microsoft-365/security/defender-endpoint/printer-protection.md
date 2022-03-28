---
title: Microsoft Defender للحماية من الطابعة للتحكم في جهاز نقطة النهاية
description: يمنع Microsoft Defender for Endpoint Device Control Printer Protection الأشخاص من الطباعة عبر طابعات غير خاصة بالشركة أو طابعة USB غير معتمدة.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: dansimp
author: lovina-saldanha
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 496d9bf729eaaff6cf12e9734ae80eedacf98a63
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63574331"
---
# <a name="device-control-printer-protection"></a>حماية الطابعة للتحكم في الجهاز

**ينطبق على**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمنع Microsoft Defender for Endpoint Device Control Printer Protection الأشخاص من الطباعة عبر طابعات غير خاصة بالشركة أو طابعة USB غير معتمدة.

## <a name="licensing"></a>الترخيص

قبل بدء استخدام "حماية الطابعة"، يجب تأكيد [اشتراكك Microsoft 365 الطابعة](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). للوصول إلى حماية الطابعة واستخدامها، يجب أن يكون لديك ما يلي:

- Microsoft 365 E3 لنشر الوظائف/النهج
- Microsoft 365 E5 لإعداد التقارير

## <a name="permission"></a>الإذن

لنشر النهج في Intune، لنشر النهج عبر OMA-URI، يجب أن يكون للحساب أذونات لإنشاء ملفات تعريف تكوين الجهاز أو تحريرها أو تحديثها أو حذفها. يمكنك إنشاء أدوار مخصصة أو استخدام أي من الأدوار المضمنة باستخدام هذه الأذونات:

- دور إدارة ملفات التعريف والسياسات.
- أو دور مخصص مع تشغيل أذونات إنشاء/تحرير/تحديث/قراءة/حذف/عرض التقارير لملفات تعريف تكوين الجهاز
- أو المسؤول العام

لعرض تقارير تكوين الجهاز، يجب أن يكون للحساب أذونات عرض التقارير. يمكنك إنشاء أدوار مخصصة أو استخدام الأدوار المضمنة باستخدام هذه الأذونات:

- مسؤول الأمان العام
- مسؤول الأمان
- قارئ الأمان

## <a name="prepare-your-endpoints"></a>تحضير نقاط النهاية

تأكد من أن Windows 10 أو Windows 11 التي تخطط لها لنشر حماية الطابعة لتلبية هذه المتطلبات.

1. تم تثبيت Windows التالية.
    - بالنسبة Windows 1809: تثبيت Windows [KB5003217](https://support.microsoft.com/topic/may-20-2021-kb5003217-os-build-17763-1971-preview-08687c95-0740-421b-a205-54aa2c716b46)
    - بالنسبة Windows 1909: تثبيت Windows [KB5003212](https://support.microsoft.com/topic/may-20-2021-kb5003212-os-build-18363-1593-preview-05381524-8380-4b30-b783-e330cad3d4a1)
    - بالنسبة Windows 2004 أو أي وقت لاحق

2. إذا كنت تخطط لنشر نهج عبر "نهج المجموعة"، فيجب أن يكون الجهاز منضما إلى Microsoft Defender لنقطة النهاية المنضمة إليه؛ إذا كنت تخطط لنشر النهج عبر إدارة نقاط النهاية من Microsoft، فيجب أن يكون الجهاز منضما باستخدام Microsoft Intune.

## <a name="deploy-device-control-printer-protection-policy"></a>نهج حماية الطابعة "نشر التحكم في الجهاز"

يمكنك نشر النهج عبر نهج المجموعة أو Intune.

<br>

****

|العنوان|الوصف|دعم CSP | دعم GPO | الدعم المستند إلى المستخدم | دعم يستند إلى جهاز |
|---|---|:---:|:---:|:---:|:---:|
|**تمكين قيود الطباعة للتحكم في الجهاز**|منع الأشخاص من الطباعة عبر طابعة غير الشركة|نعم|نعم|نعم|نعم|
|**قائمة أجهزة الطباعة المعتمدة المتصلة ب USB**\*|السماح بطابعة USB معينة|نعم|نعم|نعم|نعم|
|

\* يجب استخدام هذا النهج مع **تمكين التحكم في الجهاز قيود الطباعة**.

## <a name="deploy-policy-via-intune"></a>نشر النهج عبر Intune

بالنسبة إلى Intune، تدعم حاليا "حماية الطابعة للتحكم في الجهاز" OMA-URI فقط.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-intune"></a>السيناريو 1: منع الأشخاص من الطباعة عبر أي طابعة غير الشركة باستخدام Intune

- تطبيق النهج على الجهاز:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControl`

- تطبيق النهج على المستخدم:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControlUser`

سلسلة دعم CSP مع `<enabled/>`:

:::image type="content" source="../../media/customeditrow.png" alt-text="صف تحرير مخصص.":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-intune"></a>السيناريو 2: السماح بطابعات USB معينة معتمدة باستخدام Intune

- تطبيق النهج على الجهاز:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevices`

- تطبيق النهج على المستخدم:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevicesUser`

سلسلة دعم CSP مع طابعات USB المعتمدة عبر خاصية 'تمت الموافقة على استخدام الطباعة'، على سبيل المثال `<enabled><data id="ApprovedUsbPrintDevices_List" value="03F0/0853,0351/0872"/>`:

:::image type="content" source="../../media/editrow.png" alt-text="تحرير الصف.":::

## <a name="deploy-policy-via-group-policy"></a>نهج النشر عبر نهج المجموعة

إذا لم يكن الجهاز منضما إلى Intune، يمكنك أيضا نشر النهج عبر نهج المجموعة.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-group-policy"></a>السيناريو 1: منع الأشخاص من الطباعة عبر أي طابعة غير شركات باستخدام "نهج المجموعة"

- تطبيق النهج على الجهاز:

  طابعة القوالب \> الإدارية لتكوين \> الكمبيوتر: تمكين التحكم في الجهاز قيود الطباعة

- تطبيق النهج على المستخدم:

  طابعات لوحة التحكم \> في \> \> قوالب تكوين المستخدم الإدارية: تمكين التحكم في الجهاز قيود الطباعة

:::image type="content" source="../../media/enable-device-ctrl-printing-restrictions.png" alt-text="تمكين قيود طباعة الجهاز.":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-group-policy"></a>السيناريو 2: السماح باستخدام طابعات USB معينة معتمدة باستخدام "نهج المجموعة"

- تطبيق النهج على الجهاز:

  طابعة قوالب \> تكوين الكمبيوتر \> الإدارية: قائمة أجهزة الطباعة المعتمدة المتصلة ب USB

- تطبيق النهج على المستخدم:

  طابعات لوحة التحكم \> في \> \> قوالب تكوين المستخدم الإدارية: قائمة أجهزة الطباعة المعتمدة المتصلة ب USB

:::image type="content" source="../../media/list-of-approved-connected-print-devices.png" alt-text="قائمة أجهزة الطباعة المعتمدة المتصلة ب usb.":::

## <a name="view-device-control-printer-protection-data-in-microsoft-defender-for-endpoint-portal"></a>عرض بيانات حماية الطابعة للتحكم في الجهاز في مدخل Microsoft Defender لنقطة النهاية

يعرض <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender الإلكتروني</a> الطباعة المحظورة بواسطة نهج "حماية الطابعة للتحكم في الجهاز" أعلاه.

```kusto
DeviceEvents
| where ActionType == 'PrintJobBlocked'
| extend parsed=parse_json(AdditionalFields)
| extend PrintedFile=tostring(parsed.JobOrDocumentName)
| extend PrintPortName=tostring(parsed.PortName)
| extend PrinterName=tostring(parsed.PrinterName)
| extend Policy=tostring(parsed.RestrictionReason) 
| project Timestamp, DeviceId, DeviceName, ActionType, InitiatingProcessAccountName, Policy, PrintedFile, PrinterName, PrintPortName, AdditionalFields
| order by Timestamp desc
```

 :::image type="content" source="../../media/device-control-advanced-hunting.png" alt-text="الصيد المتقدم.":::

 يمكنك استخدام حدث PnP للعثور على طابعة USB المستخدمة في المؤسسة:

```kusto
//find the USB Printer VID/PID
DeviceEvents
| where ActionType == "PnpDeviceConnected"
| extend parsed=parse_json(AdditionalFields)
| extend DeviceDescription = tostring(parsed.DeviceDescription) 
| extend PrinterDeviceId = tostring(parsed.DeviceId) 
| extend VID_PID_Array = split(split(PrinterDeviceId, "\\")[1], "&")
| extend VID_PID = replace_string(strcat(VID_PID_Array[0], '/', VID_PID_Array[1]), 'VID_', '')
| extend VID_PID = replace_string(VID_PID, 'PID_', '')
| extend ClassId = tostring(parsed.ClassId) 
| extend VendorIds = tostring(parsed.VendorIds) 
| where DeviceDescription == 'USB Printing Support'
| project Timestamp , DeviceId, DeviceName, ActionType, DeviceDescription, VID_PID, ClassId, PrinterDeviceId, VendorIds, parsed
| order by Timestamp desc
```

 :::image type="content" source="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png" alt-text="الصيد المتقدم":::
