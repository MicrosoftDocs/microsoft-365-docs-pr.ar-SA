---
title: الأحداث والحصول على الوظائف الإضافية من المتجر
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: تعرف على لوائح القانون العام لحماية البيانات (GDPR) التي تحكم البيانات الشخصية للقصر.
ms.openlocfilehash: 15b35798ba03132b35285dc16ce57b139e4d7222
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782358"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>الأحداث والحصول على الوظائف الإضافية من المتجر

القانون العام لحماية البيانات (GDPR) هو لائحة الاتحاد الأوروبي التي تصبح سارية المفعول في 25 مايو 2018. فهو يمنح المستخدمين حقوقا وحماية لبياناتهم. أحد جوانب القانون العام لحماية البيانات هو أن الأحداث لا يمكنهم إرسال بياناتهم الشخصية إلى الأطراف التي لم يوافق عليها أحد الوالدين أو الوصي. يعتمد العمر المحدد المعرف على أنه ثانوي على المنطقة التي يوجد فيها الفرد.

تشمل المناطق التي لديها لوائح قانونية حول موافقة الوالدين الولايات المتحدة وكوريا الجنوبية والمملكة المتحدة والاتحاد الأوروبي. بالنسبة إلى هذه المناطق، سيتم حظر أي ثانوي (عبر Azure Active Directory) من الحصول على أي وظائف إضافية Office جديدة من المتجر وتشغيل الوظائف الإضافية التي تم الحصول عليها مسبقا. بالنسبة للبلدان التي لا تحتوي على لوائح قانونية، لن تكون هناك قيود على التنزيل.

يتم تحديد المستخدم ليكون ثانويا استنادا إلى البيانات المحددة في Azure Active Directory. مسؤول المؤسسة مسؤول عن الإعلان عن مجموعة العمر القانوني وموافقة الوالدين لهذا المستخدم.

إذا وافق أحد الوالدين/الوصي على أحد الأحداث باستخدام وظيفة إضافية معينة، فيمكن لمسؤول المؤسسة استخدام النشر المركزي لنشر هذه الوظيفة الإضافية لجميع الأحداث الذين لديهم موافقة.

لكي تكون متوافقا مع القانون العام لحماية البيانات للقصر، تحتاج إلى التأكد من نشر أحد الإصدارات التالية من Office في مدرستك/مؤسستك.

 **بالنسبة إلى Word، Excel، PowerPoint، Project**:

|منصه|رقم النسخة|
|---|---|
|Microsoft 365 Apps for enterprise (خيار التحديث الحالي)|9001.2138|
|Microsoft 365 Apps for enterprise (قناة المؤسسة نصف السنوية)|8431.2159|
|Office 2016 for Windows|16.0.4672.1000|
|Office 2013 for Windows|15.0.5023.1000|
|Office 2016 for Mac|16.11.18020200|
|Office للويب|N/A|

 **بالنسبة Outlook**:

|منصه|رقم النسخة|
|---|---|
|Outlook 2016 ل Windows (MSI)|إنشاء No TBD|
|Outlook 2016 ل Windows (C2R)|16.0.9323.1000|
|Office 2016 for Mac|16.0.9318.1000|
|Outlook للأجهزة المحمولة لنظام التشغيل iOS|2.75.0|
|Outlook للأجهزة المحمولة لنظام التشغيل Android|2.2.145|
|Outlook.com|N/A|

 **متطلبات Office 2013**

سيدعم Word و Excel و PowerPoint 2013 for Windows نفس عمليات التحقق من الأحداث إذا تم تمكين "مكتبة مصادقة Active Directory" (ADAL). هناك خياران للامتثال، كما هو موضح بعد ذلك.

- **تمكين ADAL**. تشرح هذه المقالة كيفية تمكين ADAL Office 2013: [استخدام المصادقة الحديثة Microsoft 365 مع عملاء Office](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>تحتاج أيضا إلى تعيين مفاتيح التسجيل لتمكين ADAL كما هو موضح في [تمكين المصادقة الحديثة Office 2013 على أجهزة Windows](../security-and-compliance/enable-modern-authentication.md).<br/>بالإضافة إلى ذلك، تحتاج إلى تثبيت تحديثات شهر أبريل التالية Office 2013:

  - [وصف تحديث الأمان Office 2013: 10 أبريل 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)

  - [3 أبريل 2018، تحديث Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)

- **لا تقم بتمكين ADAL**. إذا لم تتمكن من تمكين ADAL في Office 2013، فإن توصيتنا هي استخدام نهج المجموعة لإيقاف تشغيل المتجر لعملاء Office. توجد [هنا](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)) معلومات حول كيفية إيقاف تشغيل التطبيق لإعدادات Office.

## <a name="related-articles"></a>المقالات ذات الصلة

[استخدام الوظائف الإضافية في مركز الإدارة](./manage-deployment-of-add-ins.md)

[إدارة الوظائف الإضافية في مركز الإدارة](./manage-addins-in-the-admin-center.md)
