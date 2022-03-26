---
title: أساليب وخصائص نشاط الإصلاح
description: تحتوي استجابة API على تهديدات & إدارة الثغرات الأمنية المعالجة التي تم إنشاؤها في المستأجر. يمكنك طلب كل أنشطة الإصلاح أو نشاط إصلاح واحد فقط أو معلومات حول الأجهزة التي يتم عرضها لمهمة إصلاح محددة.
keywords: apis, remediation, remediation api, get, remediation tasks, remediation methods, remediation properties,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 124a44f6a04e4e4e77d80ac91ed4da169e2a4aae
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/19/2022
ms.locfileid: "63574278"
---
# <a name="remediation-activity-methods-and-properties"></a>أساليب وخصائص نشاط الإصلاح

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

تحتوي استجابة API على [& إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md) إصلاح المخاطر التي تم إنشاؤها في المستأجر.

## <a name="methods"></a>الأساليب

الأسلوب|نوع البيانات|الوصف
:---|:---|:---
[سرد كل أنشطة الإصلاح](get-remediation-all-activities.md)|مجموعة التحقيق|إرجاع معلومات حول كل أنشطة الإصلاح.
[سرد الأجهزة التي تم عرضها لنشاط إصلاحي واحد](get-remediation-exposed-devices-activities.md)|كيان التحقيق|إرجاع معلومات حول الأجهزة التي يتم عرضها لنشاط الإصلاح المحدد.
[الحصول على نشاط إصلاحي واحد بواسطة الم ID](get-remediation-one-activity.md)|كيان التحقيق|إرجاع معلومات لنشاط الإصلاح المحدد.

تعرف على المزيد [حول أنشطة الإصلاح](tvm-remediation.md).

## <a name="properties"></a>الخصائص

"معرّف الخاصية"|نوع البيانات|الوصف
:---|:---|:---
الفئة|سلسلة|فئة نشاط الإصلاح (تكوين البرامج/الأمان)
completerEmail|سلسلة|إذا تم إكمال نشاط المعالجة يدويا من قبل شخص ما، فإن هذا العمود يحتوي على بريده الإلكتروني
completerId|سلسلة|إذا تم إكمال نشاط المعالجة يدويا من قبل شخص ما، فإن هذا العمود يحتوي على "معروض الكائن" الخاص به
completionMethod|سلسلة|يمكن إكمال نشاط المعالجة "تلقائيا" (إذا تم تصحيح جميع الأجهزة) أو "يدويا" من قبل شخص يقوم بتحديد "وضع علامة كمكتملة".
createdOn|DateTime|الوقت الذي تم فيه إنشاء نشاط الإصلاح هذا
الوصف|سلسلة|وصف لنشاط الإصلاح هذا
dueOn|DateTime|تاريخ الاستحقاق الذي حدده المبدع لنشاط الإصلاح هذا
fixedDevices||عدد الأجهزة التي تم إصلاحها
الم ID|سلسلة|الم ID الخاص بنشاط الإصلاح هذا
nameId|سلسلة|اسم المنتج ذي الصلة
الأولوية|سلسلة|أولوية مجموعة المبدعين لنشاط الإصلاح هذا (High\Medium\Low)
productId|سلسلة|"معرّف المنتج ذي الصلة"
productivityImpactRemediationType|سلسلة|يمكن طلب بعض تغييرات التكوين فقط للأجهزة التي لا تؤثر على المستخدمين. تشير هذه القيمة إلى التحديد بين "جميع الأجهزة المعرضة" أو "الأجهزة التي لا تؤثر على المستخدم فقط".
rbacGroupNames|سلسلة|أسماء مجموعة الأجهزة ذات الصلة
المستحسنProgram|سلسلة|البرنامج المستحسن للترقية إلى
recommendedVendor|سلسلة|المورد المستحسن للترقية إلى
recommendedVersion|سلسلة|الإصدار المستحسن للتحديث/الترقية إلى
relatedComponent|سلسلة|المكون ذو الصلة لنشاط الإصلاح هذا (مماثل للمكون ذي الصلة لتوصية الأمان)
requesterEmail|سلسلة|عنوان البريد الإلكتروني "منشئ"
requesterId|سلسلة|"معر ة كائن منشئ"
requesterNotes|سلسلة|الملاحظات (نص مجاني) التي أضافها المبدع لنشاط الإصلاح هذا
Scid|سلسلة|SCID لتوصية الأمان ذات الصلة
الحالة|سلسلة|حالة نشاط المعالجة (نشط/مكتمل)
statusLastModifiedOn|DateTime|تاريخ تحديث حقل الحالة
targetDevices|طويل|عدد الأجهزة التي يتم عرضها التي ينطبق هذا الإصلاح على
العنوان|سلسلة|عنوان نشاط الإصلاح هذا
النوع|سلسلة|نوع المعالجة
موردمزيد|سلسلة|اسم المورد ذي الصلة

## <a name="see-also"></a>راجع أيضًا

- [الحصول على نشاط إصلاحي واحد بواسطة الم ID](get-remediation-one-activity.md)

- [سرد كل أنشطة الإصلاح](get-remediation-all-activities.md)

- [سرد الأجهزة التي تم عرضها لنشاط إصلاحي واحد](get-remediation-exposed-devices-activities.md)

- [المخاطر المستندة إلى المخاطر & إدارة الثغرات الأمنية](next-gen-threat-and-vuln-mgt.md)

- [نقاط الضعف في مؤسستك](tvm-weaknesses.md)
