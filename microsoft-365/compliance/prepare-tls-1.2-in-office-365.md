---
title: التحضير ل TLS 1.2 في Office 365 Office 365 سحابة القطاع الحكومي
description: كيفية التحضير لاستخدام TLS 1.2 لكل تركيبات خادم العميل ومستعرض الخادم في Office 365 و Office 365 سحابة القطاع الحكومي بعد تعطيل دعم TLS 1.0 و1.1.
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
ms.openlocfilehash: d2562e52c307fcf251b0b3030219aca68dc96a0a
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63567475"
---
# <a name="preparing-for-tls-12-in-office-365-and-office-365-gcc"></a>التحضير ل TLS 1.2 في Office 365 Office 365 سحابة القطاع الحكومي

## <a name="summary"></a>الملخص

لتوفير التشفير الأفضل في فئة العملاء، تخطط Microsoft ل إهمال الإصدارين 1.0 و1.1 من أمان طبقة النقل (TLS) في Office 365 Office 365 سحابة القطاع الحكومي. ندرك أهمية أمان بياناتك، ونحن نلتزم بالشفافية بشأن التغييرات التي قد تؤثر على استخدامك لخدمة TLS.

لا [يوجد لدى تنفيذ Microsoft TLS 1.0](https://support.microsoft.com/help/3117336/schannel-implementation-of-tls-1-0-in-windows-security-status-update-n) أي ثغرات أمان معروفة. ولكن نظرا لاحتمالات خفض البروتوكولات المستقبلية للهجمات والنقاط الأمنية الأخرى ل TLS، سنتوقف عن دعم TLS 1.0 و1.1 في Microsoft Office 365 Office 365 سحابة القطاع الحكومي.

للحصول على معلومات حول كيفية إزالة تبعيات TLS 1.0 و1.1، راجع الورقة البيضاء التالية: حل مشكلة [TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).

بعد الترقية إلى TLS 1.2، تأكد من أن مجموعات رموز التي تستخدمها مدعومة بواسطة Azure Front Door. Microsoft 365 Azure Front Door اختلافات بسيطة في دعم مجموعة رموز. للحصول على التفاصيل، راجع [ما هي مجموعات التشفير الحالية التي يدعمها Azure Front Door؟](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-).

## <a name="more-information"></a>معلومات إضافية

لقد بدأنا بالفعل في إهمال TLS 1.0 و1.1 من يناير 2020. إن أي عملاء أو أجهزة أو خدمات تتصل Office 365 عبر TLS 1.0 أو 1.1 في DoD أو سحابة القطاع الحكومي High غير معتمدة. بالنسبة إلى عملائنا التجاريين في Office 365، سيبدأ إهمال TLS 1.0 و1.1 في 15 أكتوبر 2020 وستستمر عملية طرحها على مدار الأسابيع والأشهر التالية.

نوصي بأن تستخدم كل تركيبات خادم العميل ومستعرض الخادم TLS 1.2 (أو إصدار أحدث) للحفاظ على الاتصال Office 365 الخدمات. قد تحتاج إلى تحديث تركيبات معينة من الخادم العميل ومستعرض الخادم.

  > [!NOTE]
  > لتدفق البريد الوارد SMTP، بعد إهمال TLS 1.0 و1.1، سنقبل اتصال TLS 1.2 فقط. ومع ذلك، سنستمر في قبول اتصال SMTP غير مشفر بدون أي TLS. على الرغم من أننا لا نوصي ببث البريد الإلكتروني بدون أي تشفير. 

ستحتاج إلى تحديث التطبيقات التي تتصل ب واجهات Microsoft 365 عبر TLS 1.0 أو TLS 1.1 لاستخدام TLS 1.2. .NET 4.5 افتراضيا ل TLS 1.1. لتحديث تكوين .NET، راجع [كيفية تمكين 1.2 أمان طبقة النقل (TLS) على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

من المعروف أن العملاء التاليين غير قادرين على استخدام TLS 1.2. قم بتحديث هؤلاء العملاء لضمان الوصول دون انقطاع إلى الخدمة.

- Android 4.3 والإصدارات السابقة
- الإصدار 5.0 من Firefox والإصدارات السابقة
- Internet Explorer 8-10 على Windows 7 والإصدارات السابقة
- Internet Explorer 10 على Windows Phone 8
- Safari 6.0.4/OS X10.8.4 والإصدارات السابقة

### <a name="tls-12-for-microsoft-teams-rooms-and-surface-hub"></a>TLS 1.2 Microsoft Teams Rooms Surface Hub

Microsoft Teams Rooms (المعروف سابقا باسم Skype Room System V2 SRS V2) TLS 1.2 منذ ديسمبر 2018. نوصي بتثبيت أجهزة الغرف Microsoft Teams Rooms التطبيق 4.0.64.0 أو إصدار أحدث. لمزيد من المعلومات، راجع [ملاحظات الإصدار](/microsoftteams/room-systems/srs2-release-note). تكون التغييرات متوافقة مع الإصدارات إلى الخلف وإلى الأمام.

Surface Hub إصدار دعم TLS 1.2 في مايو 2019.

يتطلب دعم TLS 1.2 Microsoft Teams Rooms ومنتجات Surface Hub أيضا تغييرات التعليمات البرمجية من جانب الخادم التالية:

- Skype for Business تغييرات الخادم عبر الإنترنت مباشرة في أبريل 2019. الآن، Skype for Business Online الاتصال Microsoft Teams Rooms Surface Hub باستخدام TLS 1.2.
- Skype for Business Server العملاء على تثبيت تحديث تراكمي (CU) لاستخدام TLS 1.2 غرف Teams وS Surface Hub.

  - بالنسبة Skype for Business Server 2015، تم إصدار CU9 بالفعل في مايو 2019.
  - بالنسبة Skype for Business Server 2019، تم التخطيط مسبقا ل CU1 لشهر أبريل 2019 ولكن تم تأخيره إلى يونيو 2019.

  > [!NOTE]
  > Skype for Business على العملاء في الموقع أن لا يقوموا بتعطيل TLS 1.0/1.1 قبل تثبيت أجهزة CUs معينة Skype for Business Server.

إذا كنت تستخدم أي بنية أساسية في الموقع المحلي لسيناريوهات مختلطة أو خدمات اتحاد Active Directory، فتأكد من أن البنية الأساسية يمكن أن تدعم الاتصالات الواردة والداخلة التي تستخدم TLS 1.2.

## <a name="references"></a>المراجع

توفر الموارد التالية إرشادات للمساعدة في التأكد من أن العملاء يستخدمون TLS 1.2 أو إصدار أحدث وتعطيل TLS 1.0 و1.1.

- بالنسبة Windows 7 عملاء يتصلون Office 365، تأكد من أن TLS 1.2 هو البروتوكول الآمن الافتراضي في WinHTTP في Windows. لمزيد من المعلومات، راجع [KB 3140245 - التحديث لتمكين TLS 1.1 و TLS 1.2](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in) كبروتوكولات آمنة افتراضية في WinHTTP في Windows.
- [مجموعات رموز TLS المدعمة بواسطة Office 365](/microsoft-365/compliance/technical-reference-details-about-encryption#tls-cipher-suites-supported-by-office-365)
- لبدء معالجة استخدام TLS الضعيف من خلال إزالة تبعيات TLS 1.0 و1.1، راجع دعم [TLS 1.2 في Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- تسهل [وظيفة IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) الجديدة العثور على العملاء على [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) وs Windows [Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) الذين يتصلون بالخدمة باستخدام بروتوكولات أمان ضعيفة.
- احصل على مزيد من المعلومات حول [كيفية حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- للحصول على معلومات عامة حول نهجنا في التعامل مع الأمان، انتقل إلى Office 365 [الثقة](https://www.microsoft.com/trustcenter/cloudservices/office365).
- لتحديد إصدار TLS الذي يستخدمه عملاء SMTP، راجع معلومات العملاء [في SMTP Auth والتقارير في مركز التوافق & الأمان](../security/office-365-security/mfi-smtp-auth-clients-report.md).
- [التحضير ل 1.0/1.1 TLS - Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server إرشادات TLS، الجزء 1: الاستعداد ل TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server إرشادات TLS 2: تمكين TLS 1.2 وتحديد العملاء الذين لا يستخدمونه](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server إرشادات TLS 3: إيقاف تشغيل TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [تمكين دعم TLS 1.1 و TLS 1.2 في Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
- [تمكين دعم TLS وSSL في SharePoint 2013](/sharepoint/security-for-sharepoint-server/enable-tls-and-ssl-support-in-sharepoint-2013)
- [تمكين دعم TLS 1.1 و TLS 1.2 في SharePoint Server 2016](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2016)
- [تمكين دعم TLS 1.1 و TLS 1.2 في SharePoint Server 2019](/sharepoint/security-for-sharepoint-server/enable-tls-1-1-and-tls-1-2-support-in-sharepoint-server-2019)
