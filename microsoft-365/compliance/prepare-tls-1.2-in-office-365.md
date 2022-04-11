---
title: التحضير ل TLS 1.2 في Office 365 Office 365 سحابة القطاع الحكومي
description: كيفية التحضير لاستخدام TLS 1.2 لجميع مجموعات خادم العميل وخادم المستعرض في Office 365 Office 365 سحابة القطاع الحكومي بعد تعطيل دعم TLS 1.0 و1.1.
author: kccross
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: shmehta
ms.reviewer: krowley
appliesto:
- Office 365 Business
ms.openlocfilehash: 8e5664149ef571a8fed3a1aee433fa97c9ed8ca4
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760416"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>التحضير ل TLS 1.2 في Office 365 Office 365 سحابة القطاع الحكومي

## <a name="summary"></a>الملخص

لتوفير أفضل تشفير في فئته لعملائنا، تخطط Microsoft لإهمال الإصدارين 1.0 و1.1 من بروتوكول أمان طبقة النقل (TLS) في Office 365 Office 365 سحابة القطاع الحكومي. نحن نفهم أن أمان بياناتك مهم، ونحن ملتزمون بالشفافية بشأن التغييرات التي قد تؤثر على استخدامك لخدمة TLS.

لا يحتوي [تطبيق Microsoft TLS 1.0](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) على ثغرات أمنية معروفة. ولكن بسبب احتمالية هجمات خفض مستوى البروتوكول المستقبلية والثغرات الأمنية الأخرى ل TLS، فإننا نوقف دعم TLS 1.0 و1.1 في Microsoft Office 365 Office 365 سحابة القطاع الحكومي.

للحصول على معلومات حول كيفية إزالة تبعيات TLS 1.0 و1.1، راجع المستند التقني التالي: [حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).

بعد الترقية إلى TLS 1.2، تأكد من أن مجموعات التشفير التي تستخدمها مدعومة من قبل Azure Front Door. Microsoft 365 وAzure Front Door اختلافات طفيفة في دعم مجموعة التشفير. للحصول على التفاصيل، راجع [ما هي مجموعات التشفير الحالية التي يدعمها Azure Front Door؟](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-).

## <a name="more-information"></a>معلومات إضافية

لقد بدأنا بالفعل في إهمال TLS 1.0 و1.1 اعتبارا من يناير 2020. أي عملاء أو أجهزة أو خدمات تتصل Office 365 من خلال TLS 1.0 أو 1.1 في DoD أو سحابة القطاع الحكومي المثيلات العالية غير معتمدة. بالنسبة إلى عملائنا التجاريين في Office 365، سيبدأ إهمال TLS 1.0 و1.1 في 15 أكتوبر 2020 وسيستمر الإطلاق خلال الأسابيع والأشهر التالية.

نوصي باستخدام جميع مجموعات خادم العميل وخادم المستعرض TLS 1.2 (أو إصدار أحدث) للحفاظ على الاتصال بخدمات Office 365. قد تحتاج إلى تحديث مجموعات معينة من خادم العميل وخادم المستعرض.

  > [!NOTE]
  > بالنسبة لتدفق البريد الوارد SMTP، بعد إهمال TLS 1.0 و1.1، سنقبل اتصال TLS 1.2 فقط. ومع ذلك، سنواصل قبول اتصال SMTP غير المشفر دون أي TLS. على الرغم من أننا لا نوصي بإرسال البريد الإلكتروني دون أي تشفير.

ستحتاج إلى تحديث التطبيقات التي تستدعي واجهات برمجة التطبيقات Microsoft 365 عبر TLS 1.0 أو TLS 1.1 لاستخدام TLS 1.2. افتراضيات .NET 4.5 إلى TLS 1.1. لتحديث تكوين .NET الخاص بك، راجع [كيفية تمكين أمان طبقة النقل (TLS) 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

من المعروف أن العملاء التاليين غير قادرين على استخدام TLS 1.2. تحديث هؤلاء العملاء لضمان الوصول دون انقطاع إلى الخدمة.

- Android 4.3 والإصدارات السابقة
- الإصدار 5.0 من Firefox والإصدارات السابقة
- Internet Explorer 8-10 على Windows 7 والإصدارات السابقة
- Internet Explorer 10 على Windows Phone 8
- Safari 6.0.4/OS X10.8.4 والإصدارات السابقة

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>TLS 1.2 ل Microsoft Teams Rooms و Surface Hub

Microsoft Teams Rooms (المعروف سابقا باسم Skype Room System V2 SRS V2) دعم TLS 1.2 منذ ديسمبر 2018. نوصي بتثبيت أجهزة الغرف Microsoft Teams Rooms إصدار التطبيق 4.0.64.0 أو أحدث. لمزيد من المعلومات، راجع [ملاحظات الإصدار](/microsoftteams/room-systems/srs2-release-note). التغييرات متوافقة مع الإصدارات السابقة وإلى الأمام.

Surface Hub إصدار دعم TLS 1.2 في مايو 2019.

يتطلب دعم TLS 1.2 لمنتجات Microsoft Teams Rooms Surface Hub أيضا تغييرات التعليمات البرمجية التالية من جانب الخادم:

- Skype for Business تم إجراء تغييرات على الخادم عبر الإنترنت مباشرة في أبريل 2019. الآن، يدعم Skype for Business Online توصيل أجهزة Microsoft Teams Rooms وأجهزة Surface Hub باستخدام TLS 1.2.
- يجب على العملاء Skype for Business Server تثبيت تحديث تراكمي (CU) لاستخدام TLS 1.2 لأنظمة غرف Teams Surface Hub.

  - بالنسبة Skype for Business Server 2015، تم إصدار CU9 بالفعل في مايو 2019.
  - بالنسبة Skype for Business Server 2019، كان من المخطط مسبقا أن يكون CU1 في أبريل 2019 ولكن تم تأخيره إلى يونيو 2019.

  > [!NOTE]
  > Skype for Business يجب ألا يقوم العملاء المحليون بتعطيل TLS 1.0/1.1 قبل تثبيت وحدات CUs معينة Skype for Business Server.

إذا كنت تستخدم أي بنية أساسية محلية لسيناريوهات مختلطة أو خدمات الأمان المشترك لـ Active Directory، فتأكد من أن البنية الأساسية يمكنها دعم كل من الاتصالات الواردة والصادرة التي تستخدم TLS 1.2.

## <a name="references"></a>مراجع

توفر الموارد التالية إرشادات للمساعدة في التأكد من أن العملاء يستخدمون TLS 1.2 أو إصدار أحدث وتعطيل TLS 1.0 و1.1.

- بالنسبة Windows 7 عملاء يتصلون Office 365، تأكد من أن TLS 1.2 هو البروتوكول الآمن الافتراضي في WinHTTP في Windows. لمزيد من المعلومات، راجع [KB 3140245 - تحديث لتمكين TLS 1.1 وTLS 1.2 كبروتوكولات آمنة افتراضية في WinHTTP في Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- [مجموعات تشفير TLS المدعومة من قبل Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- لبدء معالجة ضعف استخدام TLS عن طريق إزالة تبعيات TLS 1.0 و1.1، راجع [دعم TLS 1.2 في Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- تسهل [وظيفة IIS الجديدة](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) العثور على العملاء على [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) [وserver Windows 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) المتصلين بالخدمة باستخدام بروتوكولات أمان ضعيفة.
- احصل على مزيد من المعلومات حول كيفية [حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- للحصول على معلومات عامة حول نهجنا في الأمان، انتقل إلى [مركز التوثيق Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- لتحديد إصدار TLS المستخدم من قبل عملاء SMTP، راجع [رؤى عملاء SMTP Auth والإبلاغ في مركز التوافق & الأمان](../security/office-365-security/mfi-smtp-auth-clients-report.md).
- [التحضير لإهمال TLS 1.0/1.1 - Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server إرشادات TLS، الجزء 1: الاستعداد ل TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server إرشادات TLS الجزء 2: تمكين TLS 1.2 وتحديد العملاء الذين لا يستخدمونه](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server إرشادات TLS الجزء 3: إيقاف تشغيل TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [تمكين دعم TLS 1.1 وTLS 1.2 في Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
- [تمكين دعم TLS وSSL في SharePoint 2013](/sharepoint/security-for-sharepoint-server/enable-tls-and-ssl-support-in-sharepoint-2013)
- [تمكين دعم TLS 1.1 وTLS 1.2 في SharePoint Server 2016](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016)
- [تمكين دعم TLS 1.1 وTLS 1.2 في SharePoint Server 2019](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2019)
