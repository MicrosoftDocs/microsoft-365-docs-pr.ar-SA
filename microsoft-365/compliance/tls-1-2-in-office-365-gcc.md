---
title: تعطيل TLS 1.0 و1.1 في Microsoft 365 سحابة القطاع الحكومي High و DoD
description: يناقش كيفية تعطيل Microsoft لدعم TLS 1.1 و1.0 في سحابة القطاع الحكومي عالية و DoD في Microsoft 365.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.collection: M365-security-compliance
ms.service: information-protection
ms.topic: article
ms.reviewer: krowley
ms.author: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 29ee02c7c54fc7de6ee178f8219f7148a8cb4bfd
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/15/2022
ms.locfileid: "63567871"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>تعطيل TLS 1.0 و1.1 في Microsoft 365 سحابة القطاع الحكومي High و DoD

## <a name="summary"></a>الملخص

للالتزام بأحدث معايير التوافق لبرنامج إدارة المخاطر والتخويل الفيدرالي (FedRAMP)، نقوم بتعطيل الإصدارين 1.1 و1.0 من أمان طبقة النقل (TLS) في Microsoft 365 لبيئات سحابة القطاع الحكومي العالية و DoD. تم الإعلان عن هذا التغيير مسبقا من خلال دعم Microsoft في التحضير للاستخدام الإلزامي ل [TLS 1.2 في](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) Office 365.

أمان بياناتك مهم، ونحن ملتزمون بالشفافية بشأن التغييرات التي قد تؤثر على استخدامك للخدمة.

على الرغم من أن [تنفيذ Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) لا يوجد به أي ثغرات أمان معروفة، إلا أننا ما ونظل ملتزمين بمعايير التوافق في FedRAMP. لذلك، قمنا بتعطيل البيئات TLS 1.1 و1.0 في Microsoft 365 في سحابة القطاع الحكومي عالية و DoD في 15 يناير 2020. للحصول على معلومات حول كيفية إزالة تبعيات TLS 1.1 و1.0، راجع الورقة البيضاء التالية:

[حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>معلومات إضافية

بدءا من 15 يناير 2020، Microsoft 365 في بيئات سحابة القطاع الحكومي العالية و DoD تعطيل TLS 1.1 و1.0.

بحلول 15 يناير 2020، يجب أن تستخدم كل مجموعات خوادم العملاء وخادمات المستعرض الإصدار 1.2 من TLS (أو إصدار أحدث) للتأكد من أنه يمكن إجراء كل الاتصالات بدون مشاكل في Microsoft 365. قد يتطلب ذلك إجراء تحديثات على مجموعات معينة من خوادم العملاء ومستعرضات الخوادم.

للحصول SharePoint OneDrive، ستحتاج إلى تحديث .NET وتكوينه لدعم TLS 1.2. للحصول على معلومات، [راجع كيفية تمكين TLS 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

يجب تحديث أجهزة الكمبيوتر العميلة للتأكد من الاحتفاظ بالوصول بدون انقطاع إلى Office 365 سحابة القطاع الحكومي High و DoD.

ستحتاج إلى تحديث التطبيقات التي تتصل ب واجهات Microsoft 365 عبر TLS 1.0 أو TLS 1.1 لاستخدام TLS 1.2. .NET 4.5 افتراضيا ل TLS 1.1. لتحديث تكوين .NET، راجع [كيفية تمكين 1.2 أمان طبقة النقل (TLS) على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). لمزيد من المعلومات، راجع التحضير للاستخدام الإلزامي ل [TLS 1.2 في](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) Office 365.

نحن نعلم أنه يتعذر على تطبيقات العميل التالية استخدام TLS 1.2:

- Android 4.3 والإصدارات السابقة
- الإصدار 5.0 من Firefox والإصدارات السابقة
- Internet Explorer 8–10 على Windows 7 والإصدارات السابقة
- Internet Explorer 10 على Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 والإصدارات السابقة

على الرغم من أن التحليل الحالي للاتصالات مع خدمات Microsoft Online يظهر أن معظم الخدمات ونقاط النهاية ترى القليل من استخدام TLS 1.1 و1.0، إلا أننا نقدم إشعارا بهذا التغيير بحيث يمكنك تحديث أي عملاء أو خوادم متأثرين كما هو ضروري قبل انتهاء دعم TLS 1.1 و1.0. إذا كنت تستخدم أي بنية أساسية في الموقع المحلي لسيناريوهات مختلطة أو خدمات اتحاد Active Directory (AD FS)، فتأكد من أن البنية الأساسية يمكن أن تدعم الاتصالات الواردة والداخلة التي تستخدم TLS 1.2 (أو إصدار أحدث).

بالإضافة إلى انقطاع الخدمة الذي قد تواجهه إذا كنت تستخدم العملاء المدرجين الذين لا يمكنهم استخدام TLS 1.2، ستمنعك إزالة TLS 1.1 و1.0 من القدرة على استخدام منتج Microsoft التالي:

- هاتف Lync

## <a name="references"></a>المراجع

للحصول على الإرشادات والمراجع لمساعدتك على التأكد من أن عملائك يستخدمون TLS 1.2، راجع التحضير للاستخدام الإلزامي ل [TLS 1.2 في](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) Office 365.