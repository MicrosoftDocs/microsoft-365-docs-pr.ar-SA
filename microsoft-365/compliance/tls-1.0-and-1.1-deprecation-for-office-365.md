---
title: تعطيل TLS 1.0 و1.1 Microsoft 365
description: يصف هذا الخيار إيقاف TLS 1.0 و1.1 وتعطيله Microsoft 365.
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
ms.openlocfilehash: 3084232f267a1180425d2daa3fcd2ba2fbcbd063
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569303"
---
# <a name="disabling-tls-10-and-11-for-microsoft-365"></a>تعطيل TLS 1.0 و1.1 Microsoft 365

> [!IMPORTANT]
> لقد أوقفنا مؤقتا تعطيل TLS 1.0 و1.1 للعملاء التجاريين بسبب COVID-19. مع ضبط سلاسل التزويد وفتح بعض البلدان مجددا، قمنا بإعادة تشغيل عملية فرض TLS 1.2 في 15 أكتوبر 2020. سيستمر طرحه على مدار الأسابيع والأشهر التالية.

في 31 أكتوبر 2018، يتم إهمال بروتوكولي أمان طبقة النقل (TLS) 1.0 و1.1 لخدمة Microsoft 365. التأثير الذي يتم على المستخدمين النهائيين هو الحد الأدنى. تم الإعلان عن هذا التغيير لأكثر من عامين، مع الإعلان العام الأول الذي تم الإعلان عنه في ديسمبر 2017. هذه المقالة مخصصة فقط لتغطية Office 365 المحلي فيما يتعلق بالخدمة في Office 365 ولكن يمكنها أيضا أن تنطبق على مشاكل TLS المحلية في تطبيقات ويب Office Office Online Server/Office ويب.

للحصول SharePoint OneDrive، ستحتاج إلى تحديث .NET وتكوينه لدعم TLS 1.2. للحصول على معلومات، [راجع كيفية تمكين TLS 1.2 على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="office-365-and-tls-overview"></a>Office 365 نظرة عامة على TLS

يعتمد Office العميل على Windows ويب (WINHTTP) لإرسال حركة المرور وتلقيها عبر بروتوكولات TLS. يمكن Office العميل استخدام TLS 1.2 إذا كانت خدمة الويب الخاصة بالكمبيوتر المحلي يمكنها استخدام TLS 1.2. يمكن Office العملاء استخدام بروتوكولات TLS، حيث أن بروتوكولات TLS وSSL هي جزء من نظام التشغيل ولا تكون خاصة Office العميل.

### <a name="on-windows-8-and-later-versions"></a>على Windows 8 والإصدارات الأحدث

بشكل افتراضي، يتوفر بروتوكولا TLS 1.2 و1.1 إذا لم يتم تكوين أجهزة الشبكة لرفض حركة مرور TLS 1.2.

### <a name="on-windows-7"></a>في Windows 7

لا تتوفر بروتوكولات TLS 1.1 و1.2 بدون تحديث [3140245 KB](https://support.microsoft.com/help/3140245) . يعالج التحديث هذه المشكلة ويضيف مفتاح السجل الفرعي التالي:

```console
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp
```

> [!NOTE]
> Windows 7 مستخدمين ليس لديهم هذا التحديث حتى 31 أكتوبر 2018. [يقدم 3140245 KB](https://support.microsoft.com/help/3140245) تفاصيل حول كيفية تغيير إعدادات WINHTTP لتمكين بروتوكولات TLS.

#### <a name="more-information"></a>معلومات إضافية

تحدد قيمة مفتاح التسجيل **DefaultSecureProtocols** الذي تصفه مقالة KB بروتوكولات الشبكة التي يمكن استخدامها:

|القيمة DefaultSecureProtocols|البروتوكول الذي تم تمكينه|
|-|-|
|0x00000008|تمكين SSL 2.0 بشكل افتراضي|
|0x00000020|تمكين SSL 3.0 بشكل افتراضي|
|0x00000080|تمكين TLS 1.0 بشكل افتراضي|
|0x00000200|تمكين TLS 1.1 بشكل افتراضي|
|0x00000800|تمكين TLS 1.2 بشكل افتراضي|

## <a name="office-clients-and-tls-registry-keys"></a>Office العملاء ومفاتيح تسجيل TLS

يمكنك الرجوع إلى [KB 4057306 التحضير للاستخدام الإلزامي ل TLS 1.2 في](https://support.microsoft.com/help/4057306) Office 365. هذه مقالة عامة لمسؤولي تكنولوجيا المعلومات، وهي وثائق رسمية حول تغيير TLS 1.2.

يعرض الجدول التالي قيم مفتاح التسجيل المناسبة في Office 365 العملاء بعد 31 أكتوبر 2018.

|البروتوكولات التي تم تمكينها Office 365 الخدمة بعد 31 أكتوبر 2018|قيمة ست عشرية|
|-|-|
|TLS 1.0 + 1.1 + 1.2|0x00000A80|
|TLS 1.1 + 1.2|0x00000A00|
|TLS 1.0 + 1.2|0x00000880|
|TLS 1.2|0x00000800|

> [!IMPORTANT]
> لا تستخدم بروتوكولي SSL 2.0 و3.0، الذي يمكن تعيينه أيضا باستخدام المفتاح **DefaultSecureProtocols** . يعتبر SSL 2.0 و3.0 بروتوكولين قديمين وغير آمنين. أفضل ممارسة هي إنهاء استخدام SSL 2.0 وSSL 3.0، على الرغم من أن قرار القيام بذلك يعتمد في النهاية على ما يلبي احتياجات المنتج بشكل أفضل. لمزيد من المعلومات حول نقاط الضعف في SSL 3.0، راجع نقاط الضعف [3009008](https://support.microsoft.com/help/3009008).

يمكنك استخدام الإعداد الافتراضي Windows الحاسبة في وضع المبرمج لإعداد قيم مفاتيح التسجيل المرجعية نفسها. لمزيد من المعلومات، راجع [KB 3140245 Update لتمكين TLS 1.1 و TLS 1.2](https://support.microsoft.com/help/3140245) كبروتوكولات آمنة افتراضية في WinHTTP في Windows.

بغض النظر عما إذا كان Windows 7 ([KB 3140245](https://support.microsoft.com/help/3140245)) مثبتا أم لا، فإن المفتاح الفرعي للسجل DefaultSecureProtocols غير موجود ويجب إضافته يدويا أو من خلال كائن نهج المجموعة (GPO). وهذا يعني أنه ما لم يكن عليك تخصيص البروتوكولات الآمنة التي تم تمكينها أو تقييدها، فهذا يعني أن هذا المفتاح غير مطلوب. تحتاج فقط إلى تحديث Windows 7 SP1 ([KB 3140245](https://support.microsoft.com/help/3140245)).

## <a name="update-and-configure-the-net-framework-to-support-tls-12"></a>تحديث البيانات وتكوينها .NET Framework TLS 1.2

ستحتاج إلى تحديث التطبيقات التي تتصل ب واجهات Microsoft 365 عبر TLS 1.0 أو TLS 1.1 لاستخدام TLS 1.2. .NET 4.5 افتراضيا ل TLS 1.1. لتحديث تكوين .NET، راجع [كيفية تمكين 1.2 أمان طبقة النقل (TLS) على العملاء](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client).

## <a name="more-information"></a>معلومات إضافية

لمزيد من المعلومات، راجع التحضير للاستخدام الإلزامي ل [TLS 1.2 في](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) Office 365.

## <a name="references"></a>المراجع

توفر الموارد التالية إرشادات للمساعدة في التأكد من أن العملاء يستخدمون TLS 1.2 أو إصدار أحدث وتعطيل TLS 1.0 و1.1:

- بالنسبة Windows 7 عملاء يتصلون Office 365، تأكد من أن TLS 1.2 هو البروتوكول الآمن الافتراضي في WinHTTP في Windows. لمزيد من المعلومات، راجع [KB 3140245 - تحديث لتمكين TLS 1.1 و TLS 1.2](https://support.microsoft.com/help/3140245/update-to-enable-tls-1-1-and-tls-1-2-as-a-default-secure-protocols-in) كبروتوكولات آمنة افتراضية في WinHTTP في Windows.
- لمعالجة ضعف استخدام TLS عن طريق إزالة تبعيات TLS 1.0 و1.1، راجع دعم [TLS 1.2 في Microsoft](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/20/tls-1-2-support-at-microsoft/).
- تسهل [وظيفة IIS](https://cloudblogs.microsoft.com/microsoftsecure/2017/09/07/new-iis-functionality-to-help-identify-weak-tls-usage/) الجديدة العثور على العملاء على [Windows Server 2012 R2](https://support.microsoft.com/help/4025335/windows-8-1-windows-server-2012-r2-update-kb4025335) وs Windows [Server 2016](https://support.microsoft.com/help/4025334/windows-10-update-kb4025334) الذين يتصلون بالخدمة باستخدام بروتوكولات أمان ضعيفة.
- احصل على مزيد من المعلومات حول [كيفية حل مشكلة TLS 1.0](https://www.microsoft.com/download/details.aspx?id=55266).
- للحصول على معلومات عامة حول نهجنا في التعامل مع الأمان، انتقل إلى Office 365 [الثقة](https://www.microsoft.com/trustcenter/cloudservices/office365).
- [التحضير ل 1.0/1.1 TLS - Office 365 Skype for Business](https://techcommunity.microsoft.com/t5/Skype-for-Business-Blog/Preparing-for-TLS-1-0-1-1-Deprecation-O365-Skype-for-Business/ba-p/222247)
- [Exchange Server إرشادات TLS، الجزء 1: الاستعداد ل TLS 1.2](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-1-getting-ready-for-tls-1-2/ba-p/607649)
- [Exchange Server إرشادات TLS 2: تمكين TLS 1.2 وتحديد العملاء الذين لا يستخدمونه](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-2-enabling-tls-1-2-and/ba-p/607761)
- [Exchange Server إرشادات TLS 3: إيقاف تشغيل TLS 1.0/1.1](https://techcommunity.microsoft.com/t5/exchange-team-blog/exchange-server-tls-guidance-part-3-turning-off-tls-1-0-1-1/ba-p/607898)
- [تمكين دعم TLS 1.1 و TLS 1.2 في Office Online Server](/officeonlineserver/enable-tls-1-1-and-tls-1-2-support-in-office-online-server)

