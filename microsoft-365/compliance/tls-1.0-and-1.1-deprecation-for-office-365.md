---
title: تعطيل TLS 1.0 و1.1 Microsoft 365
description: يصف إهمال TLS 1.0 و1.1 وتعطيل Microsoft 365.
author: workshay
manager: laurawi
ms.localizationpriority: medium
search.appverid:
- MET150
audience: ITPro
ms.service: O365-seccomp
ms.topic: article
ms.author: fasqiu
ms.reviewer: krowley
appliesto:
- Microsoft 365 Apps for enterprise
- Office 365 Business
- Office 365 Personal
- Office Online Server
- Office Web Apps
ms.openlocfilehash: 519b2c025236be49f2f1c96e098c841f789c079b
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759656"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>تعطيل TLS 1.0 و1.1 Microsoft 365

> [!IMPORTANT]
> أوقفنا مؤقتا تعطيل TLS 1.0 و1.1 للعملاء التجاريين بسبب COVID-19. مع تعديل سلاسل التوريد وفتح بعض البلدان مرة أخرى، قمنا بإعادة تشغيل إطلاق تطبيق TLS 1.2 في 15 أكتوبر 2020. سيستمر الإطلاق التدريجي خلال الأسابيع والأشهر التالية.

اعتبارا من 31 أكتوبر 2018، يتم إهمال بروتوكولي أمان طبقة النقل 1.0 و1.1 لخدمة Microsoft 365. تأثير المستخدمين النهائيين هو الحد الأدنى. تم نشر هذا التغيير لأكثر من عامين، مع الإعلان العام الأول الذي تم إجراؤه في ديسمبر 2017. تهدف هذه المقالة فقط إلى تغطية Office 365 العميل المحلي فيما يتعلق بخدمة Office 365 ولكن يمكن أن تنطبق أيضا على مشكلات TLS المحلية مع Office وتطبيقات ويب Office Online Server/Office.

بالنسبة SharePoint OneDrive، ستحتاج إلى تحديث .NET وتكوينه لدعم TLS 1.2. للحصول على معلومات، راجع [كيفية تمكين TLS 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>نظرة عامة على Office 365 وTLS

يعتمد عميل Office على خدمة الويب Windows (WINHTTP) لإرسال واستقبال نسبة استخدام الشبكة عبر بروتوكولات TLS. يمكن لعميل Office استخدام TLS 1.2 إذا كانت خدمة الويب للكمبيوتر المحلي يمكنها استخدام TLS 1.2. يمكن لجميع عملاء Office استخدام بروتوكولات TLS، حيث تعد بروتوكولات TLS وSSL جزءا من نظام التشغيل وليست خاصة بالعميل Office.

### <a name="on-windows-8-and-later-versions"></a>في الإصدارات Windows 8 والإصدارات الأحدث

بشكل افتراضي، يتوفر بروتوكولا TLS 1.2 و1.1 إذا لم يتم تكوين أي أجهزة شبكة لرفض نسبة استخدام الشبكة TLS 1.2.

### <a name="on-windows-7"></a>في Windows 7

لا يتوفر بروتوكولا TLS 1.1 و1.2 بدون تحديث [3140245 KB](https://support.microsoft.com/help/3140245) . يعالج التحديث هذه المشكلة ويضيف المفتاح الفرعي للسجل التالي:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows تأثر 7 مستخدمين ليس لديهم هذا التحديث اعتبارا من 31 أكتوبر 2018. [يحتوي KB 3140245](https://support.microsoft.com/help/3140245) على تفاصيل حول كيفية تغيير إعدادات WINHTTP لتمكين بروتوكولات TLS.

#### <a name="more-information"></a>معلومات إضافية

تحدد قيمة مفتاح تسجيل **DefaultSecureProtocols** الذي تصفه مقالة KB بروتوكولات الشبكة التي يمكن استخدامها:

|قيمة DefaultSecureProtocols|تم تمكين البروتوكول|
|---|---|
|0x00000008|تمكين SSL 2.0 بشكل افتراضي|
|0x00000020|تمكين SSL 3.0 بشكل افتراضي|
|0x00000080|تمكين TLS 1.0 بشكل افتراضي|
|0x00000200|تمكين TLS 1.1 بشكل افتراضي|
|0x00000800|تمكين TLS 1.2 بشكل افتراضي|

## <a name="office-clients-and-tls-registry-keys"></a>Office العملاء ومفاتيح تسجيل TLS

يمكنك الرجوع إلى [KB 4057306 التحضير للاستخدام الإلزامي ل TLS 1.2 في Office 365](https://support.microsoft.com/help/4057306). هذه مقالة عامة لمسؤولي تكنولوجيا المعلومات، وهي وثائق رسمية حول تغيير TLS 1.2.

يعرض الجدول التالي قيم مفتاح التسجيل المناسبة في عملاء Office 365 بعد 31 أكتوبر 2018.

|البروتوكولات الممكنة لخدمة Office 365 بعد 31 أكتوبر 2018|قيمة سداسية عشرية|
|---|---|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> لا تستخدم بروتوكولات SSL 2.0 و3.0، والتي يمكن تعيينها أيضا باستخدام المفتاح **DefaultSecureProtocols** . تعتبر SSL 2.0 و3.0 بروتوكولات قديمة وغير آمنة. أفضل الممارسات هي إنهاء استخدام SSL 2.0 وSSL 3.0، على الرغم من أن قرار القيام بذلك يعتمد في نهاية المطاف على ما يلبي احتياجات المنتج بشكل أفضل. لمزيد من المعلومات حول الثغرات الأمنية SSL 3.0، راجع [KB 3009008](https://support.microsoft.com/help/3009008).

يمكنك استخدام حاسبة Windows الافتراضية في وضع المبرمج لإعداد نفس قيم مفتاح التسجيل المرجعي. لمزيد من المعلومات، راجع [KB 3140245 Update لتمكين TLS 1.1 وTLS 1.2 كبروتوكولات آمنة افتراضية في WinHTTP في Windows](https://support.microsoft.com/help/3140245).

بغض النظر عما إذا كان تحديث Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)) مثبتا أم لا، فإن المفتاح الفرعي لتسجيل DefaultSecureProtocols غير موجود ويجب إضافته يدويا أو من خلال كائن نهج المجموعة (GPO). أي أنه ما لم يكن عليك تخصيص البروتوكولات الآمنة التي تم تمكينها أو تقييدها، فهذا المفتاح غير مطلوب. تحتاج فقط إلى تحديث Windows 7 SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)).

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>تحديث وتكوين .NET Framework لدعم TLS 1.2

ستحتاج إلى تحديث التطبيقات التي تستدعي واجهات برمجة التطبيقات Microsoft 365 عبر TLS 1.0 أو TLS 1.1 لاستخدام TLS 1.2. افتراضيات .NET 4.5 إلى TLS 1.1. لتحديث تكوين .NET الخاص بك، راجع [كيفية تمكين أمان طبقة النقل (TLS) 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>معلومات إضافية

لمزيد من المعلومات، راجع [التحضير للاستخدام الإلزامي ل TLS 1.2 في Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).

## <a name="references"></a>مراجع

توفر الموارد التالية إرشادات للمساعدة في التأكد من أن عملائك يستخدمون TLS 1.2 أو إصدار أحدث وتعطيل TLS 1.0 و1.1:

- بالنسبة Windows 7 عملاء يتصلون Office 365، تأكد من أن TLS 1.2 هو البروتوكول الآمن الافتراضي في WinHTTP في Windows. لمزيد من المعلومات، راجع [KB 3140245 - تحديث لتمكين TLS 1.1 وTLS 1.2 كبروتوكولات آمنة افتراضية في WinHTTP في Windows](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in).
- لمعالجة ضعف استخدام TLS عن طريق إزالة تبعيات TLS 1.0 و1.1، راجع [دعم TLS 1.2 في Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- تسهل [وظيفة IIS الجديدة](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) العثور على العملاء على [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) [وserver Windows 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) المتصلين بالخدمة باستخدام بروتوكولات أمان ضعيفة.
- احصل على مزيد من المعلومات حول كيفية [حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- للحصول على معلومات عامة حول نهجنا في الأمان، انتقل إلى [مركز التوثيق Office 365](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [التحضير لإهمال TLS 1.0/1.1 - Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server إرشادات TLS، الجزء 1: الاستعداد ل TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server إرشادات TLS الجزء 2: تمكين TLS 1.2 وتحديد العملاء الذين لا يستخدمونه](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server إرشادات TLS الجزء 3: إيقاف تشغيل TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [تمكين دعم TLS 1.1 وTLS 1.2 في Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)
