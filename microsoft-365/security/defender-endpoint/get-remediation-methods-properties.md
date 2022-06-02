---
title: أساليب وخصائص نشاط الإصلاح
description: تحتوي استجابة واجهة برمجة التطبيقات على أنشطة معالجة & إدارة الثغرات الأمنية التهديد التي تم إنشاؤها في المستأجر الخاص بك. يمكنك طلب جميع أنشطة المعالجة أو نشاط معالجة واحد فقط أو معلومات حول الأجهزة المكشوفة لمهمة معالجة محددة.
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
ms.openlocfilehash: 14f57d6590d580e0145abc2da788f184c88a721e
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840244"
---
# <a name="remediation-activity-methods-and-properties"></a>أساليب وخصائص نشاط الإصلاح

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

تحتوي استجابة واجهة برمجة التطبيقات على أنشطة معالجة [& إدارة الثغرات الأمنية التهديد](next-gen-threat-and-vuln-mgt.md) التي تم إنشاؤها في المستأجر الخاص بك.

## <a name="methods"></a>اساليب

الاسلوب|نوع البيانات|الوصف
:---|:---|:---
[سرد كل أنشطة المعالجة](get-remediation-all-activities.md)|مجموعة التحقيق|إرجاع معلومات حول كافة أنشطة المعالجة.
[سرد الأجهزة التي تم عرضها لنشاط معالجة واحد](get-remediation-exposed-devices-activities.md)|كيان التحقيق|إرجاع معلومات حول الأجهزة المكشوفة لنشاط المعالجة المحدد.
[الحصول على نشاط معالجة واحد بواسطة المعرّف](get-remediation-one-activity.md)|كيان التحقيق|إرجاع معلومات لنشاط المعالجة المحدد.

تعرف على المزيد حول [أنشطة المعالجة](tvm-remediation.md).

## <a name="properties"></a>خصائص

معرف الخاصية|نوع البيانات|الوصف
:---|:---|:---
الفئة|سلسلة|فئة نشاط المعالجة (تكوين البرامج/الأمان)
completerEmail|سلسلة|إذا قام شخص ما بإكمال نشاط المعالجة يدويا، فإن هذا العمود يحتوي على بريده الإلكتروني
معرف الإكمال|سلسلة|إذا تم إكمال نشاط المعالجة يدويا من قبل شخص ما، فإن هذا العمود يحتوي على معرف الكائن
CompletionMethod|سلسلة|يمكن إكمال نشاط المعالجة "تلقائيا" (إذا تم تصحيح جميع الأجهزة) أو "يدويا" بواسطة شخص يحدد "وضع علامة كمكتمل".
createdOn|Datetime|وقت إنشاء نشاط المعالجة هذا
الوصف|سلسلة|وصف نشاط المعالجة هذا
تاريخ الاستحقاق|Datetime|تاريخ الاستحقاق الذي عينه المنشئ لنشاط المعالجة هذا
fixedDevices||عدد الأجهزة التي تم تصحيحها
المعرّف|سلسلة|معرف نشاط المعالجة هذا
معرف الاسم|سلسلة|اسم المنتج ذي الصلة
الاولويه|سلسلة|الأولوية التي عينها المنشئ لنشاط المعالجة هذا (عالي\متوسط\منخفض)
Productid|سلسلة|معرف المنتج ذي الصلة
productivityImpactRemediationType|سلسلة|يمكن طلب بعض تغييرات التكوين فقط للأجهزة التي لا تؤثر على المستخدمين. تشير هذه القيمة إلى التحديد بين "كافة الأجهزة المكشوفة" أو "الأجهزة التي لا تؤثر على المستخدم فقط".
rbacGroupNames|سلسلة|أسماء مجموعات الأجهزة ذات الصلة
مخطط موصى به|سلسلة|البرنامج الموصى به للترقية إلى
RecommendedVendor|سلسلة|المورد الموصى به للترقية إلى
recommendedVersion|سلسلة|الإصدار الموصى به للتحديث/الترقية إليه
الحوسبة ذات الصلة|سلسلة|المكون ذي الصلة لنشاط المعالجة هذا (على غرار المكون ذي الصلة لتوصية الأمان)
requesterEmail|سلسلة|عنوان البريد الإلكتروني لمنشئ
معرف الطالب|سلسلة|معرف كائن المنشئ
requesterNotes|سلسلة|الملاحظات (النص المجاني) التي أضافها المنشئ لنشاط المعالجة هذا
Scid|سلسلة|SCID لتوصية الأمان ذات الصلة
حاله|سلسلة|حالة نشاط المعالجة (نشط/مكتمل)
statusLastModifiedOn|Datetime|تاريخ تحديث حقل الحالة
targetDevices|طويله|عدد الأجهزة المكشوفة التي تنطبق عليها هذه المعالجة
عنوان|سلسلة|عنوان نشاط المعالجة هذا
نوع|سلسلة|نوع المعالجة
معرف المورد|سلسلة|اسم المورد ذي الصلة

## <a name="see-also"></a>راجع أيضًا

- [الحصول على نشاط معالجة واحد بواسطة المعرّف](get-remediation-one-activity.md)

- [سرد كل أنشطة المعالجة](get-remediation-all-activities.md)

- [سرد الأجهزة التي تم عرضها لنشاط معالجة واحد](get-remediation-exposed-devices-activities.md)

- [& إدارة الثغرات الأمنية المخاطر المستندة إلى المخاطر](next-gen-threat-and-vuln-mgt.md)

- [الثغرات الأمنية في مؤسستك](tvm-weaknesses.md)
