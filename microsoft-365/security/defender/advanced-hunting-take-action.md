---
title: اتخاذ إجراء بشأن نتائج استعلام التتبع المتقدمة في Microsoft 365 Defender
description: معالجة التهديدات والأصول المتأثرة بسرعة في نتائج استعلام التتبع المتقدمة
keywords: التتبع المتقدم، وتتبع التهديدات، وتتبع التهديدات عبر الإنترنت، Microsoft 365 Defender، وmicrosoft 365، وm365، والبحث، والاستعلام، وبيانات تتبع الاستخدام، واتخاذ إجراء
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: b7fbe659902bf89023e994f4e1304f25f3934db8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097569"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>اتخاذ إجراء بشأن نتائج استعلام التتبع المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

يمكنك أن تحتوي بسرعة على تهديدات أو تعالج الأصول المخترقة التي [تجدها في التتبع المتقدم](advanced-hunting-overview.md) باستخدام خيارات إجراء قوية وشاملة. باستخدام هذه الخيارات، يمكنك:

- اتخاذ إجراءات مختلفة على الأجهزة
- ملفات العزل

## <a name="required-permissions"></a>الأذونات المطلوبة
لاتخاذ إجراء على الأجهزة من خلال التتبع المتقدم، تحتاج إلى دور في Microsoft Defender لنقطة النهاية مع [أذونات لإرسال إجراءات المعالجة على الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). إذا تعذر عليك اتخاذ أي إجراء، فاتصل بالمسؤول العام للحصول على الإذن التالي:

*إجراءات المعالجة النشطة > المخاطر إدارة الثغرات الأمنية - معالجة المعالجة*

لاتخاذ إجراء بشأن رسائل البريد الإلكتروني من خلال التتبع المتقدم، تحتاج إلى دور في Microsoft Defender لـ Office 365 [للبحث عن رسائل البريد الإلكتروني وإزالة رسائل البريد الإلكتروني](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="take-various-actions-on-devices"></a>اتخاذ إجراءات مختلفة على الأجهزة
يمكنك اتخاذ الإجراءات التالية على الأجهزة المحددة `DeviceId` بواسطة العمود في نتائج الاستعلام:

- عزل الأجهزة المتأثرة لاحتواء إصابة أو منع الهجمات من الانتقال لاحقا
- جمع حزمة التحقيق للحصول على مزيد من المعلومات الجنائية
- تشغيل فحص الحماية من الفيروسات للعثور على التهديدات وإزالتها باستخدام آخر تحديثات التحليل الذكي للأمان
- بدء تحقيق تلقائي للتحقق من التهديدات على الجهاز وربما الأجهزة المتأثرة الأخرى ومعالجتها
- تقييد تنفيذ التطبيق على الملفات التنفيذية الموقعة من Microsoft فقط، ما يمنع نشاط التهديد اللاحق من خلال البرامج الضارة أو الملفات التنفيذية الأخرى غير الموثوق بها

لمعرفة المزيد حول كيفية تنفيذ إجراءات الاستجابة هذه من خلال Microsoft Defender لنقطة النهاية، [اقرأ حول إجراءات الاستجابة على الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
### <a name="quarantine-files"></a>ملفات العزل
يمكنك نشر إجراء *العزل* على الملفات بحيث يتم عزلها تلقائيا عند مصادفتها. عند تحديد هذا الإجراء، يمكنك الاختيار بين الأعمدة التالية لتحديد الملفات الموجودة في نتائج الاستعلام التي يجب عزلها:

- `SHA1`: في جداول التتبع الأكثر تقدما، يشير هذا العمود إلى SHA-1 للملف الذي تأثر بالإجراء المسجل. على سبيل المثال، إذا تم نسخ ملف، فسيكون هذا الملف المتأثر هو الملف المنسوخ.
- `InitiatingProcessSHA1`: في معظم جداول التتبع المتقدمة، يشير هذا العمود إلى الملف المسؤول عن بدء الإجراء المسجل. على سبيل المثال، إذا تم تشغيل عملية تابعة، فسيكون ملف البادئ هذا جزءا من العملية الأصل. 
- `SHA256`: هذا العمود هو مكافئ SHA-256 للملف الذي تم تعريفه بواسطة `SHA1` العمود.
- `InitiatingProcessSHA256`: هذا العمود هو مكافئ SHA-256 للملف الذي تم تعريفه بواسطة `InitiatingProcessSHA1` العمود.

لمعرفة المزيد حول كيفية اتخاذ إجراءات العزل وكيفية استعادة الملفات، [اقرأ حول إجراءات الاستجابة على الملفات](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>لتحديد موقع الملفات وعزلها، يجب أن تتضمن `DeviceId` نتائج الاستعلام أيضا قيما كمعرفات الجهاز.  

لاتخاذ أي من الإجراءات الموضحة، حدد سجلا واحدا أو أكثر في نتائج الاستعلام ثم حدد **"اتخاذ الإجراءات**". سيرشدك المعالج خلال عملية تحديد الإجراءات المفضلة ثم إرسالها.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="الخيار &quot;اتخاذ إجراءات&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/take-action-multiple.png":::


## <a name="take-various-actions-on-emails"></a>اتخاذ إجراءات مختلفة على رسائل البريد الإلكتروني
وبصرف النظر عن خطوات المعالجة التي تركز على الجهاز، يمكنك أيضا اتخاذ بعض الإجراءات على رسائل البريد الإلكتروني من نتائج الاستعلام. حدد السجلات التي تريد اتخاذ إجراء بشأنها، وحدد **«Take actions»**، ثم ضمن **«Choose actions»**، حدد اختيارك مما يلي:
- `Move to mailbox folder` - حدد هذا الخيار لنقل رسائل البريد الإلكتروني إلى مجلد العناصر "غير الهام" أو "علبة الوارد" أو "العناصر المحذوفة"

   :::image type="content" source="../../media/advanced-hunting-take-actions-email.png" alt-text="الخيار &quot;اتخاذ إجراءات&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email.png":::

- `Delete email` - حدد هذا الخيار لنقل رسائل البريد الإلكتروني إلى مجلد العناصر المحذوفة (**حذف مبدئي**) أو حذفها نهائيا (**حذف ثابت**)

   :::image type="content" source="../../media/advanced-hunting-take-actions-email-del.png" alt-text="الخيار &quot;اتخاذ إجراءات&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-take-actions-email-del.png":::

يمكنك أيضا توفير اسم معالجة ووصف مختصر للإجراء الذي تم اتخاذه لتتبعه بسهولة في محفوظات مركز الصيانة. يمكنك أيضا استخدام "معرف الموافقة" لتصفية هذه الإجراءات في مركز الصيانة. يتم توفير هذا المعرف في نهاية المعالج:

:::image type="content" source="../../media/choose-email-actions-entities.png" alt-text="معالج اتخاذ الإجراءات الذي يعرض اختيار الإجراءات للكيانات" lightbox="../../media/choose-email-actions-entities.png":::

تنطبق إجراءات البريد الإلكتروني هذه على [عمليات الكشف المخصصة](custom-detections-overview.md) أيضا.


## <a name="review-actions-taken"></a>مراجعة الإجراءات المتخذة
يتم تسجيل كل إجراء بشكل فردي في [مركز الصيانة](m365d-action-center.md) ضمن **Action** **centerHistory** >  ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). انتقل إلى مركز الصيانة للتحقق من حالة كل إجراء.
 
>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender لنقطة النهاية. [قم بتشغيل Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل التتبع المتقدمة من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender باتباع الخطوات الواردة في [ترحيل استعلامات التتبع المتقدمة من Microsoft Defender لنقطة النهاية](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [التعرّف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [نظرة عامة على مركز الصيانة](m365d-action-center.md)
