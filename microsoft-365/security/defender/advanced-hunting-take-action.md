---
title: اتخاذ إجراء بشأن نتائج استعلام البحث المتقدم في Microsoft 365 Defender
description: معالجة التهديدات والأصول المتأثرة بسرعة في نتائج استعلام البحث المتقدم
keywords: الصيد المتقدم، وصيد التهديدات، والصيد عبر الإنترنت، Microsoft 365 Defender، microsoft 365، m365، البحث، الاستعلام، بيانات التعقب، اتخاذ إجراء
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
ms.openlocfilehash: eb881611ad4b983eb80d028dfe3dee20c3ed6216
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754661"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>اتخاذ إجراء بشأن نتائج استعلام البحث المتقدمة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender
- Microsoft Defender لنقطة النهاية

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

يمكنك أن تحتوي بسرعة على تهديدات أو تعالج الأصول التي تم اختراقها التي تعثر عليها في عملية البحث [المتقدم باستخدام خيارات](advanced-hunting-overview.md) إجراءات فعالة وشاملة. باستخدام هذه الخيارات، يمكنك:

- اتخاذ إجراءات متنوعة على الأجهزة
- عزل الملفات

## <a name="required-permissions"></a>الأذونات المطلوبة
لاتخاذ إجراء من خلال البحث المتقدم، تحتاج إلى دور في Microsoft Defender لنقطة النهاية مع أذونات لإرسال إجراءات الإصلاح [على الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). إذا لم تتمكن من اتخاذ أي إجراء، فاتصل بمسؤول عام للحصول على الإذن التالي:

*إجراءات المعالجة النشطة > المخاطر إدارة الثغرات الأمنية - معالجة المعالجة*

## <a name="take-various-actions-on-devices"></a>اتخاذ إجراءات متنوعة على الأجهزة
يمكنك اتخاذ الإجراءات التالية على الأجهزة المحددة بواسطة العمود `DeviceId` في نتائج الاستعلام:

- عزل الأجهزة المتأثرة لاحتواء إصابة أو منع الهجمات من التحرك بشكل لاحق
- تجميع حزمة التحقيق للحصول على مزيد من المعلومات المتعلقة بالطب الشرعي
- تشغيل فحص الحماية من الفيروسات للعثور على التهديدات وإزالتها باستخدام آخر تحديثات معلومات الأمان
- بدء تحقيق تلقائي للتحقق من التهديدات على الجهاز وربما الأجهزة الأخرى المتأثرة بها وفحصها
- تقييد تنفيذ التطبيق على الملفات القابلة للتنفيذ الموقعة من Microsoft فقط، مما يمنع نشاط التهديدات اللاحقة من خلال البرامج الضارة أو غيرها من الملفات القابلة للتنفيذ غير الملوثة

لمعرفة المزيد حول كيفية تنفيذ إجراءات الاستجابة هذه من خلال Microsoft Defender لنقطة النهاية، اقرأ [حول إجراءات الاستجابة على الأجهزة](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
## <a name="quarantine-files"></a>عزل الملفات
يمكنك نشر إجراء *الفحص* على الملفات بحيث يتم عزلها تلقائيا عند مصادفتها. عند تحديد هذا الإجراء، يمكنك الاختيار من بين الأعمدة التالية لتحديد الملفات الموجودة في نتائج الاستعلام التي يجب فحصها:

- `SHA1`: في معظم جداول الصيد المتقدمة، يشير هذا العمود إلى SHA-1 للملف الذي تأثر بالتحرك المسجل. على سبيل المثال، إذا تم نسخ ملف، سيكون هذا الملف المتأثر هو الملف المنسوخ.
- `InitiatingProcessSHA1`: في معظم جداول الصيد المتقدمة، يشير هذا العمود إلى الملف المسؤول عن بدء الإجراء المسجل. على سبيل المثال، إذا تم تشغيل عملية طفل، سيكون ملف البادء هذا جزءا من العملية الأصل. 
- `SHA256`: هذا العمود هو مكافئ SHA-256 للملف المعرف بواسطة `SHA1` العمود.
- `InitiatingProcessSHA256`: هذا العمود هو مكافئ SHA-256 للملف المعرف بواسطة `InitiatingProcessSHA1` العمود.

لمعرفة المزيد حول كيفية اتخاذ إجراءات الفحص وكيفية استعادة الملفات، اقرأ [حول إجراءات الاستجابة على الملفات](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>لتحديد موقع الملفات وفحصها، يجب أن تتضمن نتائج الاستعلام أيضا `DeviceId` قيما كمعرفات الأجهزة.  

## <a name="take-action"></a>اتخاذ إجراء
لاتخاذ أي من الإجراءات الموضحة، حدد سجلا واحدا أو أكثر في نتائج الاستعلام، ثم حدد **اتخاذ إجراءات**. سيرشدك المعالج خلال عملية تحديد الإجراءات المفضلة لديك ثم إرسالها.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="الخيار &quot;اتخاذ الإجراءات&quot; في مدخل Microsoft 365 Defender" lightbox="../../media/take-action-multiple.png":::

## <a name="review-actions-taken"></a>مراجعة الإجراءات التي تم اتخاذها
يتم تسجيل كل إجراء بشكل فردي في [مركز الإجراءات](m365d-action-center.md) ضمن **Action** **centerHistory** >  ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)). انتقل إلى مركز الإجراءات للتحقق من حالة كل إجراء.
 
>[!NOTE]
>قد لا تتوفر بعض الجداول في هذه المقالة في Microsoft Defender for Endpoint. [قم Microsoft 365 Defender](m365d-enable.md) للبحث عن التهديدات باستخدام المزيد من مصادر البيانات. يمكنك نقل مهام سير عمل الصيد المتقدمة من Microsoft Defender ل Endpoint إلى Microsoft 365 Defender باتباع الخطوات الواردة في ترحيل استعلامات الصيد المتقدمة من [Microsoft Defender ل Endpoint](advanced-hunting-migrate-from-mde.md).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [نظرة عامة متقدمة حول الصيد](advanced-hunting-overview.md)
- [تعرف على لغة الاستعلام](advanced-hunting-query-language.md)
- [استخدام نتائج الاستعلام](advanced-hunting-query-results.md)
- [فهم المخطط](advanced-hunting-schema-tables.md)
- [نظرة عامة حول مركز الإجراءات](m365d-action-center.md)
