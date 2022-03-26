---
title: بدء استخدام أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: بدء إنشاء أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a75650484368b6ccbaf6f6d39aeead133403f5b8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63572070"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>بدء استخدام أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة

إن إنشاء نوع معلومات حساسة تستند إلى تطابق دقيق للبيانات (EDM) وجعله متوفرا هو عملية متعددة المراحل. يمكن استخدامها في سياسات منع فقدان البيانات و eDiscovery ومهام معينة لإدارة المحتوى توضح هذه المقالة سير العمل والربط بالإجراءات لكل مرحلة من المراحل

## <a name="before-you-begin"></a>قبل البدء

تعرف على المفاهيم والمصطلحات في هذه المقالات:

- [التعرف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [التعرف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>التراخيص والأذونات المطلوبة

يجب أن تكون مسؤولا عاما أو مسؤول توافق أو Exchange Online لتنفيذ المهام الموضحة في هذه المقالة. لمعرفة المزيد حول أذونات DLP، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

راجع وصف [خدمة منع فقدان البيانات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) للحصول على معلومات الترخيص الكاملة

## <a name="portal-links-for-your-subscription"></a>ارتباطات المدخل لاشتراكك

|المدخل|World Wide/سحابة القطاع الحكومي|GCC-High|DOD|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|Microsoft 365 Defender المدخل|security.microsoft.com|security.microsoft.us|security.apps.mil|
|Microsoft 365 مركز التوافق|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>سير العمل بنظرة سريعة

![أطوار سير العمل مطابقة دقيقة للبيانات](..\media\swimlane_edm_process.png)


|المرحلة|ما هو مطلوب|
|---|---|
|[المرحلة 1: تصدير بيانات المصدر لنوع المعلومات الحساسة المستندة إلى تطابق البيانات بدقة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|- قراءة الوصول إلى البيانات الحساسة|
|[المرحلة 2: إنشاء مخطط لأنواع المعلومات الحساسة المستندة إلى تطابق دقيق للبيانات](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- الوصول إلى معالج نوع المعلومات الحساسة في مركز مسؤولي Microsoft 365 </br>- الوصول إلى مركز مسؤولي Microsoft 365 [عبر الأمان & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell) |
|[المرحلة 3: قم بتهش جدول مصدر المعلومات الحساس وتحميله للحصول على بيانات دقيقة تتطابق مع أنواع المعلومات الحساسة](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|- مجموعة أمان مخصصة حساب مستخدم </br>- **اانتهاك وتحميلها** من كمبيوتر واحد: وصول المسؤول المحلي إلى كمبيوتر مع اتصال مباشر بالإنترنت واستضافة عامل EDM Upload </br>- افترق وتحميل من أجهزة كمبيوتر **منفصلة: وصول** المسؤول المحلي إلى كمبيوتر به اتصال مباشر بالإنترنت واستضافة وكيل EDM Upload للتحميل والوصول إلى المسؤول المحلي إلى كمبيوتر آمن لاستضافة وكيل EDM Upload لتقحم جدول مصدر المعلومات الحساس </br>- قراءة الوصول إلى ملف جدول مصدر المعلومات الحساس </br> ملف المخطط |
|[المرحلة 4: إنشاء بيانات دقيقة تتطابق مع نوع/حزمة قاعدة المعلومات الحساسة](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- الوصول إلى مركز Microsoft 365 التوافق |
|[اختبار نوع معلومات دقيق يطابق المعلومات الحساسة](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - الوصول إلى مركز Microsoft 365 التوافق

## <a name="see-also"></a>راجع أيضًا

- [التعرف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [تصدير بيانات المصدر لنوع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
