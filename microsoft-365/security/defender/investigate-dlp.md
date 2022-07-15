---
title: التحقيق في حوادث فقدان البيانات باستخدام Microsoft 365 Defender
description: التحقيق في فقدان البيانات في Microsoft 365 Defender.
keywords: منع فقدان البيانات والحوادث والتنبيهات والتحقيق والتحليل والاستجابة والارتباط والهجوم والأجهزة والأجهزة والمستخدمين والهويات والهوية وعلبة البريد والبريد الإلكتروني و365 وmicrosoft وm365
f1.keywords:
- NOCSH
ms.prod: m365-security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 1f81a9c4cc3bbd77d7269f04c4a6854d1370d5bb
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66822758"
---
# <a name="investigate-data-loss-incidents-with-microsoft-365-defender"></a>التحقيق في حوادث فقدان البيانات باستخدام Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

يمكن الآن إدارة أحداث تفادي فقدان البيانات في Microsoft Purview (DLP) في مدخل Microsoft 365 Defender. يمكنك إدارة حوادث DLP جنبا إلى جنب مع الحوادث الأمنية من **الحوادث & تنبيهات الحوادث** \> على الإطلاق السريع <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">لمدخل Microsoft 365 Defender</a>. من هذه الصفحة، يمكنك:

- عرض جميع تنبيهات DLP التي تم تجميعها ضمن الحوادث في قائمة انتظار الأحداث Microsoft 365 Defender.
- عرض الحلول التفاعلية الذكية (DLP-MDE وDLP-MDO) والتنبيهات المرتبطة داخل الحل (DLP-DLP) في حالة وقوع حادث واحد.
- البحث عن سجلات التوافق جنبا إلى جنب مع الأمان ضمن التتبع المتقدم.
- إجراءات معالجة المسؤول الموضعية على المستخدم والملف والجهاز. 
- إقران العلامات المخصصة بحوادث DLP والتصفية حسبها.
- قم بالتصفية حسب اسم نهج DLP والعلامة والتاريخ ومصدر الخدمة وحالة الحادث والمستخدم في قائمة انتظار الحدث الموحدة. 

يمكنك أيضا استخدام موصل Microsoft 365 Defender في Microsoft Sentinel لسحب أحداث DLP جنبا إلى جنب مع الأحداث والأدلة في Microsoft Sentinel للتحقيق والمعالجة.

## <a name="licensing-requirements"></a>متطلبات الترخيص

للتحقيق في أحداث تفادي فقدان البيانات في Microsoft Purview في مدخل Microsoft 365 Defender، تحتاج إلى ترخيص من أحد الاشتراكات التالية: 

- Microsoft Office 365 E5/A5
- Microsoft 365 E5/A5
- توافق Microsoft 365 E5/A5
- Microsoft 365 E5/A5 Security
- Microsoft 365 E5/A5 حماية البيانات والحوكمة

> [!NOTE] 
> عندما تكون مرخصا ومتأهلا لهذه الميزة، ستتدفق تنبيهات DLP تلقائيا إلى Microsoft 365 Defender. افتح حالة دعم إذا كنت تريد تعطيل هذه الميزة. 

## <a name="dlp-investigation-experience-in-the-microsoft-365-defender-portal"></a>تجربة التحقيق DLP في مدخل Microsoft 365 Defender

قبل البدء، [قم بتشغيل التنبيهات لكافة نهج DLP](/microsoft-365/compliance/dlp-configure-view-alerts-policies#alert-configuration-experience) في <a href="https://purview.microsoft.com" target="_blank">مدخل التوافق في Microsoft Purview</a>.

1. انتقل إلى مدخل Microsoft 365 Defender، وحدد **«Incidents**» في قائمة التنقل اليسرى لفتح صفحة «incidents».

2. حدد **عوامل التصفية** في الجزء العلوي الأيسر، واختر **مصدر الخدمة : منع فقدان البيانات** لعرض جميع الحوادث باستخدام تنبيهات DLP.

3. ابحث عن اسم نهج DLP للتنبيهات والحوادث التي تهتم بها.

4. لعرض صفحة ملخص الحدث، حدد الحدث من قائمة الانتظار. وبالمثل، حدد التنبيه لعرض صفحة تنبيه DLP.

5. عرض **قصة التنبيه** للحصول على تفاصيل حول النهج وأنواع المعلومات الحساسة التي تم الكشف عنها في التنبيه. حدد الحدث في قسم **"الأحداث ذات الصلة** " للاطلاع على تفاصيل نشاط المستخدم.

6. عرض المحتوى الحساس المطابق في علامة التبويب **"أنواع المعلومات الحساسة** " ومحتوى الملف في علامة التبويب **"المصدر** " إذا كان لديك الإذن المطلوب (راجع التفاصيل <a href="/microsoft-365/compliance/dlp-alerts-dashboard-get-started#roles" target="_blank">هنا</a>).

7. يمكنك أيضا استخدام Advanced Hunting للبحث من خلال سجلات التدقيق للمستخدم والملفات ومواقع الموقع للتحقيق الخاص بك. يحتوي جدول **CloudAppEvents** على جميع سجلات التدقيق عبر جميع المواقع مثل Sharepoint وOneDrive وExchange والأجهزة.

8. يمكنك أيضا تنزيل البريد الإلكتروني عن طريق تحديد **البريد الإلكتروني "تنزيل** **الإجراءات**\>". 

9. لإجراءات المعالجة على الملفات على مواقع SPO أو ODB، يمكنك مشاهدة إجراءات مثل:

    - تطبيق تسمية الاستبقاء
    - تطبيق وصف الحساسية
    - إلغاء مشاركة الملف
    - حذف

   لإجراءات المعالجة، حدد **بطاقة المستخدم** في أعلى صفحة التنبيه لفتح تفاصيل المستخدم.

   بالنسبة إلى تنبيهات DLP للأجهزة، حدد بطاقة الجهاز في أعلى صفحة التنبيه لعرض تفاصيل الجهاز واتخاذ إجراءات المعالجة على الجهاز.

10. انتقل إلى صفحة ملخص الحدث وحدد **"إدارة الحدث** " لإضافة علامات الحادث أو تعيين حدث أو حله.

## <a name="dlp-investigation-experience-in-microsoft-sentinel"></a>تجربة التحقيق في DLP في Microsoft Sentinel

يمكنك استخدام موصل Microsoft 365 Defender في Microsoft Sentinel لاستيراد جميع أحداث DLP إلى Sentinel لتوسيع الارتباط والكشف والتحقيق عبر مصادر البيانات الأخرى وتوسيع تدفقات التزامن التلقائي باستخدام قدرات SOAR الأصلية ل Sentinel. 

1. اتبع الإرشادات المتعلقة بتوصيل البيانات من Microsoft 365 Defender إلى Microsoft Sentinel لاستيراد جميع الحوادث بما في ذلك حوادث DLP والتنبيهات إلى Sentinel. تمكين `CloudAppEvents` موصل الحدث لسحب جميع سجلات تدقيق O365 إلى Sentinel.

   يجب أن تكون قادرا على رؤية أحداث DLP في Sentinel بمجرد إعداد الموصل أعلاه.

2. حدد **التنبيهات** لعرض صفحة التنبيه.

3. يمكنك استخدام **AlertType** و **startTime** و **endTime** للاستعلام عن جدول **CloudAppEvents** للحصول على جميع أنشطة المستخدم التي ساهمت في التنبيه. استخدم هذا الاستعلام لتحديد الأنشطة الأساسية:

```kusto
let Alert = SecurityAlert
| where TimeGenerated > ago(30d)
| where SystemAlertId == ""; // insert the systemAlertID here
CloudAppEvents
| extend correlationId1 = parse_json(tostring(RawEventData.Data)).cid
| extend correlationId = tostring(correlationId1)
| join kind=inner Alert on $left.correlationId == $right.AlertType
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

## <a name="related-articles"></a>المقالات ذات الصلة

- [نظرة عامة على الحوادث](incidents-overview.md)
- [تحديد أولوية الأحداث](incident-queue.md)
- [إدارة الأحداث](manage-incidents.md)
