---
title: DeviceAlertEvents table في مخطط الصيد المتقدم
description: تعرف على أحداث جيل التنبيه في جدول DeviceAlertEvents لم المخطط المتقدم للصيد
keywords: الصيد المتقدم، وصيد التهديدات، وصيد التهديدات الإلكترونية، و mdatp، و microsoft defender atp، و Microsoft defender لنقطة النهاية، و البحث في wdatp، والاستعلام، وتعقب البيانات، ومرجع المخطط، و kusto، وجدول، عمود، ونوع البيانات، والوصف، DeviceAlertEvents، التنبيه، الخطورة، الفئة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/22/2020
ms.technology: mde
ms.openlocfilehash: 32dbff60a37c31cdbfd492eb5d746a10d9b7a185
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63583108"
---
# <a name="devicealertevents"></a>DeviceAlertEvents

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

يحتوي `DeviceAlertEvents` الجدول في [مخطط](advanced-hunting-overview.md) الصيد المتقدم على معلومات حول التنبيهات في Microsoft 365 Defender. استخدم هذا المرجع لإنشاء استعلامات ترجع معلومات من الجدول.

للحصول على معلومات حول الجداول الأخرى في مخطط الصيد المتقدم، راجع مرجع مخطط [الصيد المتقدم](advanced-hunting-schema-reference.md).

|اسم العمود|نوع البيانات|الوصف|
|---|---|---|
|`AlertId`|سلسلة|معرف فريد للتنبيه|
|`Timestamp`|datetime|التاريخ والوقت الذي تم فيه تسجيل الحدث|
|`DeviceId`|سلسلة|معرف فريد للجهاز في الخدمة|
|`DeviceName`|سلسلة|اسم المجال المؤهل بالكامل (FQDN) للجهاز|
|`Severity`|سلسلة|تشير إلى التأثير المحتمل (عال أو متوسط أو منخفض) لمؤشر الخطر أو نشاط الخرق الذي يحدده التنبيه|
|`Category`|سلسلة|نوع مؤشر الخطر أو نشاط الخرق الذي يحدده التنبيه|
|`Title`|سلسلة|عنوان التنبيه|
|`FileName`|سلسلة|اسم الملف الذي تم تطبيق الإجراء المسجل عليه|
|`SHA1`|سلسلة|SHA-1 للملف الذي تم تطبيق الإجراء المسجل عليه|
|`RemoteUrl`|سلسلة|عنوان URL أو اسم المجال المؤهل بالكامل (FQDN) الذي كان قيد الاتصال|
|`RemoteIP`|سلسلة|عنوان IP الذي كان متصلا ب|
|`AttackTechniques`|سلسلة|MITRE ATT&تقنيات CK المقترنة بنشاط تشغيل التنبيه|
|`ReportId`|طويل|معرف الحدث استنادا إلى عداد مكرر. لتحديد أحداث فريدة، يجب استخدام هذا العمود مع `DeviceName` العمودين و `Timestamp`|
|`Table`|سلسلة|جدول يحتوي على تفاصيل الحدث|

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [فهم المخطط](advanced-hunting-schema-reference.md)
