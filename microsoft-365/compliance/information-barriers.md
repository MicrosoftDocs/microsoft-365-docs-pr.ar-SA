---
title: التعرّف على عوائق المعلومات
description: تعرف على حواجز المعلومات في Microsoft Purview.
keywords: Microsoft 365 وMicrosoft Purview والامتثال وحواجز المعلومات
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b302231d7dbdcc92ee2e8e2e0564cedb27a4218e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621106"
---
# <a name="learn-about-information-barriers"></a>التعرّف على عوائق المعلومات

يعد Microsoft Purview Information Barriers (IB) حلا للامتثال يسمح لك بتقييد الاتصال والتعاون ثنائي الاتجاه بين المجموعات والمستخدمين في Microsoft Teams وSharePoint Online OneDrive for Business. غالبا ما يستخدم في الصناعات المنظمة للغاية، يمكن أن يساعد IB في تجنب تضاربات الاهتمام وحماية المعلومات الداخلية بين المستخدمين والمجالات التنظيمية.

عندما تكون نهج IB في مكانها، لن يتمكن المستخدمون الذين لا يجب عليهم الاتصال بالملفات أو مشاركتها مع مستخدمين محددين آخرين من العثور على هؤلاء المستخدمين أو تحديدهم أو الدردشة معهم أو الاتصال معهم. تضع نهج IB عمليات التحقق تلقائيا للكشف عن الاتصالات غير المصرح بها والتعاون بين المجموعات والمستخدمين المحددين ومنعها. نهج IB مستقلة عن [حدود التوافق](/microsoft-365/compliance/set-up-compliance-boundaries) لتحقيقات eDiscovery التي تتحكم في مواقع محتوى المستخدم التي يمكن لمديري eDiscovery البحث فيها.

يمكن أن تسمح نهج IB بالاتصال والتعاون بين المجموعات والمستخدمين أو تمنعها لسيناريوهات المثال التالية:

- يجب ألا يقوم المستخدمون في مجموعة *"التاجر اليوم"* بتوصيل الملفات أو مشاركتها مع *فريق التسويق*
- يجب ألا يقوم موظفو التمويل الذين يعملون على معلومات سرية للشركة بتوصيل الملفات أو مشاركتها مع مجموعات معينة داخل مؤسستهم
- يجب ألا يتصل الفريق الداخلي الذي يحتوي على مواد سرية تجارية أو يدردش عبر الإنترنت مع أشخاص في مجموعات معينة داخل مؤسستهم
- يجب على فريق البحث الاتصال أو الدردشة عبر الإنترنت فقط مع فريق تطوير المنتجات
- لا يجب مشاركة موقع SharePoint لمجموعة *"متداول اليوم"* أو الوصول إليه من قبل أي شخص خارج مجموعة *"التاجر اليوم"*

> [!IMPORTANT]
> **لا تدعم** حواجز المعلومات سوى قيود الاتصال والتعاون في الاتجاهين. على سبيل المثال، لا **يتم دعم** سيناريو حيث يمكن للتسويق التواصل والتعاون مع Day Traders، ولكن لا يمكن لشركة Day Traders التواصل والتعاون في العمل مع التسويق.

## <a name="information-barriers-and-microsoft-teams"></a>حواجز المعلومات وMicrosoft Teams

في Microsoft Teams، تحدد نهج IB الأنواع التالية من الاتصالات والتعاون غير المصرح بها وتمنعها:

- البحث عن مستخدم
- إضافة عضو إلى فريق
- بدء جلسة محادثة مع شخص ما
- بدء دردشة جماعية
- دعوة شخص ما للانضمام إلى اجتماع
- مشاركة شاشة
- إجراء مكالمة
- مشاركة ملف مع مستخدم آخر
- الوصول إلى ملف من خلال مشاركة ارتباط

إذا كان المستخدمون الذين يقومون بهذه الأنشطة في Microsoft Teams مضمنين في نهج IB لمنع النشاط، فلن يتمكنوا من المتابعة. بالإضافة إلى ذلك، يمكن منع جميع الأشخاص المضمنين في نهج IB من التواصل مع مستخدمين آخرين في Microsoft Teams. عندما يكون الأشخاص المتأثرون بنهج IB جزءا من نفس دردشة الفريق أو المجموعة، فقد تتم إزالتهم من جلسات الدردشة هذه وقد لا يسمح بإجراء مزيد من الاتصالات مع المجموعة.

لمزيد من المعلومات، راجع [حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

## <a name="information-barriers-and-sharepoint-and-onedrive"></a>حواجز المعلومات وSharePoint وOneDrive

في SharePoint Online وOneDrive، تكتشف نهج IB الأنواع التالية من التعاون غير المصرح به وتمنعها:

- إضافة عضو إلى موقع
- الوصول إلى الموقع أو المحتوى من قبل مستخدم
- مشاركة الموقع أو المحتوى مع مستخدم آخر
- البحث في موقع

لمزيد من المعلومات، راجع [حواجز المعلومات في حواجز SharePoint](/sharepoint/information-barriers) والمعلومات [في OneDrive](/onedrive/information-barriers).

## <a name="information-barriers-and-exchange-online"></a>حواجز المعلومات Exchange Online

لا تتوفر نهج IB لتقييد الاتصال والتعاون بين المجموعات والمستخدمين في رسائل البريد الإلكتروني. تستند نهج IB [إلى نهج دفتر العناوين Exchange Online (ABPs).](/exchange/address-books/address-book-policies/address-book-policies) تسمح برامج ABPs للمؤسسات بتعيين المستخدمين في مجموعات معينة تقريبا من أجل توفير طرق عرض مخصصة دفاتر العناوين العمومية للمؤسسة (GAL). عند إنشاء نهج IB، يتم إنشاء ABPs للنهج تلقائيا. مع إضافة نهج IB في مؤسستك، ستتغير بنية وسلوك GAL الخاص بك للامتثال لنهج IB.

قبل تحديد نهج IB وتطبيقها، يجب إزالة كافة نهج دفتر عناوين Exchange الموجودة في مؤسستك. تستند نهج IB إلى نهج دفتر العناوين ولا تتوافق نهج ABPs الحالية مع ABPs التي تم إنشاؤها بواسطة IB. لإزالة نهج دفتر العناوين الموجودة، راجع [إزالة نهج دفتر العناوين في Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). بمجرد تمكين نهج IB وإذا كان لديك دفتر عناوين هرمي ممكن، فسيشاهد جميع المستخدمين غير المضمنين في مقطع IB [دفتر العناوين الهرمي](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) في Exchange عبر الإنترنت.

يتم دعم عمليات نشر Exchange Online فقط حاليا لنهج IB. إذا كانت مؤسستك بحاجة إلى تعريف اتصالات البريد الإلكتروني والتحكم فيها، ففكر في استخدام [قواعد تدفق بريد Exchange](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

## <a name="ready-to-get-started"></a>هل أنت جاهز لبدء الاستخدام؟

- [بدء استخدام حواجز المعلومات](information-barriers-policies.md)
- [إدارة نهج IB](information-barriers-edit-segments-policies.md)
- [راجع السمات التي يمكن استخدامها لنهج IB](information-barriers-attributes.md)
