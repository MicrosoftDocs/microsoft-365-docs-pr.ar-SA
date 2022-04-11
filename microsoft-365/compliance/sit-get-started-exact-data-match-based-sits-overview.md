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
description: ابدأ في إنشاء أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات الدقيقة.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0f221ba0521a50f484bfb9a8d5030e33b495c495
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759734"
---
# <a name="get-started-with-exact-data-match-based-sensitive-information-types"></a>بدء استخدام أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة

إن إنشاء نوع معلومات حساسة (SIT) يستند إلى EDM وإجراء مطابقة دقيقة للبيانات (EDM) متاح هو عملية متعددة المراحل. يمكن استخدامها في نهج منع فقدان البيانات وeDiscovery وبعض مهام إدارة المحتوى توضح هذه المقالة سير العمل وارتباطات الإجراءات لكل مرحلة من المراحل

## <a name="before-you-begin"></a>قبل البدء

تعرف على المفاهيم والمصطلحات الواردة في هذه المقالات:

- [التعرّف على أنواع المعلومات الحساسة](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types)
- [التعرّف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)

## <a name="required-licenses-and-permissions"></a>التراخيص والأذونات المطلوبة

يجب أن تكون مسؤولا عاما أو مسؤول توافق أو مسؤول Exchange Online لتنفيذ المهام الموضحة في هذه المقالة. لمعرفة المزيد حول أذونات DLP، راجع [الأذونات](data-loss-prevention-policies.md#permissions).

راجع [وصف خدمة منع فقدان البيانات](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) للحصول على معلومات الترخيص الكاملة

## <a name="portal-links-for-your-subscription"></a>ارتباطات المدخل لاشتراكك

|المدخل|العالم/سحابة القطاع الحكومي|GCC-High|وزاره الدفاع|
|---|---|---|---|
|Office SCC|compliance.microsoft.com|scc.office365.us|scc.protection.apps.mil|
|مدخل Microsoft 365 Defender|security.microsoft.com|security.microsoft.us|security.apps.mil|
|مركز التوافق Microsoft 365|compliance.microsoft.com|compliance.microsoft.us|compliance.apps.mil|

## <a name="the-work-flow-at-a-glance"></a>تدفق العمل بنظرة سريعة

![تطابق البيانات الدقيقة مراحل سير العمل](..\media\swimlane_edm_process.png)


|المرحله|ما هو مطلوب|
|---|---|
|[المرحلة 1: تصدير بيانات المصدر لنوع المعلومات الحساسة المستندة إلى مطابقة البيانات الدقيقة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)|- قراءة الوصول إلى البيانات الحساسة|
|[المرحلة 2: إنشاء مخطط لأنواع المعلومات الحساسة المستندة إلى مطابقة البيانات الدقيقة](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)|- الوصول إلى معالج نوع المعلومات الحساسة في مركز مسؤولي Microsoft 365 </br>- الوصول إلى [مركز مسؤولي Microsoft 365 عبر Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) |
|[المرحلة 3: تجزئة جدول مصدر المعلومات الحساسة وتحميله لتطابق البيانات الدقيقة مع أنواع المعلومات الحساسة](sit-get-started-exact-data-match-hash-upload.md#hash-and-upload-the-sensitive-information-source-table-for-exact-data-match-sensitive-information-types)|- مجموعة أمان مخصصة وحساب مستخدم </br>- **التجزئة والتحميل من كمبيوتر واحد**: وصول المسؤول المحلي إلى كمبيوتر مع وصول مباشر إلى الإنترنت واستضافة وكيل Upload EDM </br>- **التجزئة والتحميل من أجهزة كمبيوتر منفصلة**: وصول المسؤول المحلي إلى كمبيوتر مع وصول مباشر إلى الإنترنت واستضافة عامل Upload EDM للتحميل ووصول المسؤول المحلي إلى كمبيوتر آمن لاستضافة عامل Upload EDM لتجزئة جدول مصدر المعلومات الحساسة </br>- قراءة الوصول إلى ملف جدول مصدر المعلومات الحساسة </br> ملف المخطط |
|[المرحلة 4: إنشاء تطابق دقيق للبيانات مع نوع المعلومات الحساسة/حزمة القاعدة](sit-get-started-exact-data-match-create-rule-package.md#create-exact-data-match-sensitive-information-typerule-package) |- الوصول إلى مركز التوافق Microsoft 365 |
|[اختبار نوع معلومات دقيق يطابق المعلومات الحساسة](sit-get-started-exact-data-match-test.md#test-an-exact-data-match-sensitive-information-type)| - الوصول إلى مركز التوافق Microsoft 365

## <a name="see-also"></a>راجع أيضًا

- [التعرّف على أنواع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [تصدير بيانات المصدر لنوع المعلومات الحساسة المستندة إلى مطابقة البيانات بدقة](sit-get-started-exact-data-match-export-data.md#export-source-data-for-exact-data-match-based-sensitive-information-type)
