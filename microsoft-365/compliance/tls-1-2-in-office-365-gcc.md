---
title: تعطيل TLS 1.0 و1.1 في Microsoft 365 سحابة القطاع الحكومي High و DoD
description: يناقش كيفية تعطيل Microsoft لدعم TLS 1.1 و1.0 في بيئات سحابة القطاع الحكومي High و DoD في Microsoft 365.
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
ms.openlocfilehash: bad0dc997f2c564670858d2ac35b2cd3177e0578
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760372"
---
# <a name="disabling-tls-10-and-11-in-microsoft-365-gcc-high-and-dod"></a>تعطيل TLS 1.0 و1.1 في Microsoft 365 سحابة القطاع الحكومي High و DoD

## <a name="summary"></a>الملخص

من أجل الامتثال لأحدث معايير الامتثال لبرنامج إدارة المخاطر والتخويل الفيدرالي (FedRAMP)، نقوم بتعطيل الإصدارين 1.1 و1.0 من بروتوكول أمان طبقة النقل (TLS) في Microsoft 365 لبيئات سحابة القطاع الحكومي High و DoD. تم الإعلان عن هذا التغيير مسبقا من خلال دعم Microsoft في [التحضير للاستخدام الإلزامي ل TLS 1.2 في Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

أمان بياناتك مهم، ونحن ملتزمون بالشفافية بشأن التغييرات التي قد تؤثر على استخدامك للخدمة.

على الرغم من أن [تطبيق Microsoft TLS 1.0](https://support.microsoft.com/help/3117336) لا يحتوي على ثغرات أمنية معروفة، إلا أننا ما زلنا ملتزمين بمعايير الامتثال FedRAMP. لذلك، قمنا بتعطيل TLS 1.1 و1.0 في Microsoft 365 في بيئات سحابة القطاع الحكومي High و DoD في 15 يناير 2020. للحصول على معلومات حول كيفية إزالة تبعيات TLS 1.1 و1.0، راجع المستند الأبيض التالي:

[حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266)

## <a name="more-information"></a>معلومات إضافية

بدءا من 15 يناير 2020، سيؤدي Microsoft 365 في بيئات سحابة القطاع الحكومي High و DoD إلى تعطيل TLS 1.1 و1.0.

بحلول 15 يناير 2020، يجب أن تستخدم جميع مجموعات خوادم العملاء وخوادم المستعرض إصدار TLS 1.2 (أو إصدار أحدث) للتأكد من إمكانية إجراء جميع الاتصالات دون مشاكل في Microsoft 365. قد يتطلب ذلك تحديثات إلى مجموعات معينة من خوادم العميل وخوادم المستعرض.

بالنسبة SharePoint OneDrive، ستحتاج إلى تحديث .NET وتكوينه لدعم TLS 1.2. للحصول على معلومات، راجع [كيفية تمكين TLS 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

يجب تحديث أجهزة الكمبيوتر العميلة للتأكد من الحفاظ على الوصول دون انقطاع إلى Office 365 سحابة القطاع الحكومي High و DoD.

ستحتاج إلى تحديث التطبيقات التي تستدعي واجهات برمجة التطبيقات Microsoft 365 عبر TLS 1.0 أو TLS 1.1 لاستخدام TLS 1.2. افتراضيات .NET 4.5 إلى TLS 1.1. لتحديث تكوين .NET الخاص بك، راجع [كيفية تمكين أمان طبقة النقل (TLS) 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client). لمزيد من المعلومات، راجع [التحضير للاستخدام الإلزامي ل TLS 1.2 في Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

نحن نعلم أن تطبيقات العميل التالية لا يمكنها استخدام TLS 1.2:

- Android 4.3 والإصدارات السابقة
- الإصدار 5.0 من Firefox والإصدارات السابقة
- Internet Explorer 8-10 على Windows 7 والإصدارات السابقة
- Internet Explorer 10 في Windows Phone 8.0
- Safari 6.0.4/OS X 10.8.4 والإصدارات السابقة

على الرغم من أن التحليل الحالي للاتصالات بخدمات Microsoft Online يظهر أن معظم الخدمات ونقاط النهاية ترى القليل من استخدام TLS 1.1 و1.0، فإننا نقدم إشعارا بهذا التغيير بحيث يمكنك تحديث أي عملاء أو خوادم متأثرة حسب الضرورة قبل انتهاء دعم TLS 1.1 و1.0. إذا كنت تستخدم أي بنية أساسية محلية لسيناريوهات مختلطة أو خدمات الأمان المشترك لـ Active Directory (AD FS)، فتأكد من أن البنية الأساسية يمكنها دعم كل من الاتصالات الواردة والصادرة التي تستخدم TLS 1.2 (أو إصدار أحدث).

بالإضافة إلى حالات الانقطاع التي قد تواجهها إذا كنت تستخدم العملاء المدرجين الذين لا يمكنهم استخدام TLS 1.2، ستؤدي إزالة TLS 1.1 و1.0 إلى منعك من استخدام منتج Microsoft التالي:

- هاتف Lync

## <a name="references"></a>مراجع

للحصول على إرشادات ومراجع للمساعدة في التأكد من أن عملائك يستخدمون TLS 1.2، راجع [التحضير للاستخدام الإلزامي ل TLS 1.2 في Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
