---
title: إعادة توجيه الحسابات من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender
description: كيفية إعادة توجيه الحسابات والجلسات من Defender for Endpoint إلى Microsoft 365 Defender.
keywords: Microsoft 365 Defender، بدء Microsoft 365 Defender، إعادة توجيه مركز الأمان
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 64a9926253ea699fa6cc62d1ec2d80d07f25fd29
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63571483"
---
# <a name="redirecting-accounts-from-microsoft-defender-for-endpoint-to-microsoft-365-defender"></a>إعادة توجيه الحسابات من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender
- Defender لنقطة النهاية

بالمحاذاة مع نهج Microsoft عبر المجالات للحماية من المخاطر باستخدام SIEM والكشف والاستجابة الموسعة (XDR)، قمنا بتحولها إلى الحماية المتقدمة من المخاطر من Microsoft Defender ك Microsoft Defender لنقطة النهاية ووحدناها في مدخل واحد متكامل: Microsoft 365 Defender.

يشرح هذا الدليل كيفية توجيه الحسابات إلى Microsoft 365 Defender من خلال تمكين إعادة التوجيه التلقائي من مدخل Microsoft Defender السابق لنقطة النهاية (securitycenter.windows.com أو securitycenter.microsoft.com)، <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender.</a>

> [!NOTE]
> يدعم Microsoft Defender ل Endpoint في Microsoft 365 Defender منح حق الوصول إلى موفري خدمات الأمان المدارة [(MSSPs)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) بالطريقة نفسها التي يتم بها منح حق الوصول في [مركز حماية Microsoft Defender](./mssp-access.md).

## <a name="what-to-expect"></a>ما يجب توقعه

بمجرد تمكين إعادة التوجيه التلقائية، سيتم توجيه الحسابات التي تقوم بالوصول إلى مدخل Microsoft Defender السابق لنقطة النهاية في securitycenter.windows.com أو securitycenter.microsoft.com تلقائيا إلى Microsoft 365 Defender في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><security.microsoft.com></a>.

تعرف على المزيد حول ما تم تغييره: [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](microsoft-365-security-center-mde.md).

يشمل ذلك إعادة التوجيه للوصول المباشر إلى المدخل السابق عبر المستعرض، بما في ذلك الارتباطات التي تشير إلى مدخل securitycenter.windows.com السابق - مثل الارتباطات في إعلامات البريد الإلكتروني والروابط التي تم إرجاعها بواسطة مكالمات SIEM API.  

 تحتوي الارتباطات الخارجية من إعلامات البريد الإلكتروني أو واجهات برمجة التطبيقات SIEM حاليا على ارتباطات إلى كلا المدخلين. بمجرد تمكين إعادة التوجيه، سيشير كلا الارتباطين إلى Microsoft 365 Defender حتى تتم إزالة الارتباط القديم في النهاية. إننا نشجعك على اعتماد الارتباط الجديد الذي يشير إلى Microsoft 365 Defender.

راجع الجدول أدناه للحصول على مزيد من المعلومات حول الارتباطات التوجيه.
## <a name="siem-api-routing"></a>توجيه API ل SIEM

| الخاصية | الوجهة عند إيقاف تشغيل إعادة التوجيه | الوجهة عند إعادة التوجيه |
|---------|---------|---------|
| LinkToWDATP | صفحة التنبيه في securitycenter.windows.com | صفحة التنبيه في security.microsoft.com |
| IncidentLinkToWDATP | صفحة الحادث في securitycenter.windows.com | صفحة الحادث في security.microsoft.com |
| LinkToMTP | صفحة التنبيه في security.microsoft.com | صفحة التنبيه في security.microsoft.com |
| IncidentLinkToMTP | صفحة الحادث في security.microsoft.com | صفحة الحادث في security.microsoft.com |

## <a name="email-alert-notifications"></a>إعلامات تنبيهات البريد الإلكتروني

| الخاصية | الوجهة عند إيقاف تشغيل إعادة التوجيه** | الوجهة عند إعادة التوجيه |
|---------|---------|---------|
| صفحة التنبيه | صفحة التنبيه في securitycenter.windows.com | صفحة التنبيه في security.microsoft.com |
| صفحة الحادث |صفحة الحادث في securitycenter.windows.com | صفحة الحادث في security.microsoft.com |
| صفحة التنبيه في مدخل Defender for Cloud | صفحة التنبيه في security.microsoft.com | صفحة التنبيه في security.microsoft.com |
| صفحة الحادث في مدخل Defender for Cloud | صفحة الحادث في security.microsoft.com | صفحة الحادث في security.microsoft.com |

## <a name="when-does-this-take-effect"></a>متى يتم هذا الأمر؟

بمجرد تمكين هذا التحديث، قد يكون هذا التحديث محدثا على الفور تقريبا لبعض الحسابات. ولكن قد يستغرق نشر إعادة التوجيه في كل حساب في مؤسستك وقتا أطول. لن يتم إخراج الحسابات في جلسات العمل النشطة أثناء تطبيق هذا الإعداد من جلسة العمل الخاصة بها ولن يتم توجيهها إلا إلى Microsoft 365 Defender بعد إنهاء جلسة العمل الحالية ثم تسجيل الدخول مرة أخرى.  

### <a name="set-up-portal-redirection"></a>إعداد إعادة توجيه المدخل

لبدء توجيه الحسابات إلى Microsoft 365 Defender:

1. تأكد من أنك مسؤول عام أو لديك أذونات مسؤول الأمان في Azure Active Directory.

2. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">الدخول إلى Microsoft 365 Defender</a>.

3. انتقل **إلى الإعدادات** >  **EndpointsGeneralPortal** >  >  **أو** [انقر هنا](https://security.microsoft.com/preferences2/portal_redirection).  

4. تبديل إعداد إعادة التوجيه التلقائي إلى **"التشغيل**".

5. انقر **فوق** تمكين لتطبيق إعادة التوجيه التلقائي على Microsoft 365 Defender.

>[!IMPORTANT]
>لن يؤدي تمكين هذا الإعداد إلى إنهاء جلسات عمل المستخدم النشط. سيتم توجيه الحسابات التي تعمل في جلسة عمل نشطة أثناء تطبيق هذا الإعداد إلى Microsoft 365 Defender بعد إنهاء جلسة العمل الحالية الخاصة بها ثم تسجيل الدخول مرة أخرى.

>[!NOTE]
>يجب أن تكون مسؤولا عاما أو أن تكون لديك أذونات مسؤول الأمان في Azure Active Directory لتمكين هذا الإعداد أو تعطيله.  

## <a name="can-i-go-back-to-using-the-former-portal"></a>هل يمكنني العودة إلى استخدام المدخل السابق؟

إذا لم يعمل شيء ما معك أو إذا كان هناك أي شيء لا يمكنك إكماله خلال Microsoft 365 Defender، فنحن نريد سماعه. إذا واجهت أي مشاكل تتعلق بإعادة التوجيه، فنحن نشجعك على أن تعلمنا باستخدام نموذج تقديم الملاحظات.

العودة إلى مدخل Microsoft Defender السابق ل Endpoint:

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">الدخول Microsoft 365 Defender</a> كمسؤول عام أو استخدام أذونات مسؤول الأمان في Azure Active directory واستخدامها.

2. انتقل إلى **الإعدادات** >  **EndpointsGeneralPortal** >  >  أو [افتح الصفحة هنا](https://security.microsoft.com/preferences2/portal_redirection).  

3. تبديل إعداد إعادة التوجيه التلقائي إلى **إيقاف التشغيل**.

4. انقر **فوق** & مشاركة الملاحظات عند مطالبتك بذلك.

يمكن تمكين هذا الإعداد مرة أخرى في أي وقت. 

بمجرد تعطيلها، لن يتم توجيه الحسابات إلى security.microsoft.com، وسيبقى لديك مرة أخرى حق الوصول إلى المدخل السابق - securitycenter.windows.com أو securitycenter.microsoft.com. 

## <a name="related-information"></a>المعلومات ذات الصلة
- [Microsoft 365 Defender عامة](microsoft-365-defender.md)
- [Microsoft Defender ل Endpoint في Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [تقدم Microsoft SIEM وXDR الموحدين لتحديث عمليات الأمان](https://www.microsoft.com/security/blog/?p=91813) 
- [رسم بياني للمعلومات ل XDR مقابل SIEM](https://afrait.com/blog/xdr-versus-siem/) 
- [`The New Defender`](https://afrait.com/blog/the-new-defender/) 
- [حول Microsoft 365 Defender](https://www.microsoft.com/microsoft-365/security/microsoft-365-defender) 
- [مداخل الأمان ومراكز الإدارة في Microsoft](portals.md)
