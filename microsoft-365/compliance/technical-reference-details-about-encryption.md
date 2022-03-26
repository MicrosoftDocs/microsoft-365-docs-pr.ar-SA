---
title: تفاصيل المراجع التقنية حول التشفير
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
- Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: 862cbe93-4268-4ef9-ba79-277545ecf221
description: تعرف على مجموعات رموز أمان طبقة النقل (TLS) والتقنيات والشهادات المختلفة المستخدمة للتشفير في Office 365 Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6b5df1f9e983ab2e8add09b50c2dfbd30dc1243e
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/06/2021
ms.locfileid: "63567156"
---
# <a name="technical-reference-details-about-encryption"></a>تفاصيل المراجع التقنية حول التشفير

راجع هذه المقالة للتعرف على الشهادات والتقنيات و مجموعات رموز TLS المستخدمة [للتشفير في](encryption.md) Office 365. توفر هذه المقالة أيضا تفاصيل حول الاهمات المخطط لها.
  
- إذا كنت تبحث عن معلومات نظرة عامة، فاطلع على التشفير [في](encryption.md) Office 365.
- إذا كنت تبحث عن معلومات الإعداد، فاطلع على [إعداد التشفير في](set-up-encryption.md) Office 365 Enterprise.
- للحصول على معلومات حول مجموعات رموز التشفير المدعمة بواسطة إصدارات معينة من Windows، راجع [مجموعات Cipher في TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Microsoft Office 365 الملكية والإدارة للشهادات

لست بحاجة إلى شراء شهادات أو الاحتفاظ بها Office 365. بدلا من Office 365، تستخدم هذه Office 365 الشهادات الخاصة بها.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>معايير التشفير الحالية والتشفيرات المخطط لها

لتوفير التشفير الأفضل في الفئة، Office 365 معايير التشفير المعتمدة بشكل منتظم. في بعض الأحيان، يتم إهمال المعايير القديمة لأنها تصبح قديمة وأقل أمانا. تصف هذه المقالة مجموعات رموز مدعمة حاليا ومقاييس وتفاصيل أخرى حول حالات الاهمل المخطط لها.

## <a name="fips-compliance-for-office-365"></a>توافق FIPS Office 365

تستخدم كل مجموعات رموز Office 365 الخوارزميات المقبولة ضمن FIPS 140-2. Office 365 التحقق من صحة FIPS من Windows (عبر Schannel). للحصول على معلومات حول Schannel، راجع [مجموعات Cipher في TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).
  
## <a name="versions-of-tls-supported-by-office-365"></a>إصدارات TLS المدعمة بواسطة Office 365

تعد TLS وSSL التي تأتي قبل TLS بروتوكولات تشفير آمنة للاتصالات عبر الشبكة باستخدام شهادات الأمان لتشفير اتصال بين أجهزة الكمبيوتر. Office 365 TLS الإصدار 1.2 (TLS 1.2).

يتم دعم إصدار TLS 1.3 (TLS 1.3) بواسطة بعض الخدمات.

> [!IMPORTANT]
> يجب أن تدرك أن إصدارات TLS مهمل، وأن الإصدارات التي تم إهمالها يجب ألا تستخدم  في حالة توفر الإصدارات الأحدث. إذا كانت خدماتك القديمة لا تتطلب TLS 1.0 أو 1.1، يجب تعطيلها.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>دعم إهمال TLS 1.0 و1.1

Office 365 دعم TLS 1.0 و1.1 في 31 أكتوبر 2018. لقد أكملنا تعطيل TLS 1.0 و1.1 في سحابة القطاع الحكومي عالية و DoD. بدأنا بتعطيل TLS 1.0 و1.1 لبيئات سحابة القطاع الحكومي و حول العالم بدءا من 15 أكتوبر 2020 وسنستمر في طرحها على مدار الأسابيع والأشهر القادمة.

للحفاظ على اتصال آمن Office 365 وخدمات Microsoft 365، تستخدم كل مجموعات خادم العميل ومستعرض الخادم مجموعات رموز TLS 1.2 و مجموعات رموز حديثة. قد تحتاج إلى تحديث تركيبات معينة من الخادم العميل ومستعرض الخادم. للحصول على معلومات حول كيفية تأثير هذا التغيير عليك، راجع التحضير للاستخدام الإلزامي ل [TLS 1.2 في](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365) Office 365.
  
## <a name="deprecating-support-for-3des"></a>إهمال دعم 3DES

منذ 31 أكتوبر 2018، Office 365 دعم استخدام مجموعات رموز 3DES للاتصال Office 365. وبشكل أكثر تحديدا Office 365 لم تعد تدعم مجموعة TLS_RSA_WITH_3DES_EDE_CBC_SHA cipher. منذ 28 فبراير 2019، تم تعطيل مجموعة رموز التشفير هذه في Office 365. يجب أن يدعم العملاء Office 365 اتصال واحد أو أكثر من ciphers المعتمدة. للحصول على قائمة من الفهارس المعتمدة، راجع مجموعات [رموز TLS](#tls-cipher-suites-supported-by-office-365) المدعمة بواسطة Office 365.
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>إهمال دعم شهادة SHA-1 في Office 365

منذ يونيو 2016، Office 365 قبول شهادة SHA-1 للاتصالات الصادرة أو الواردة. استخدم SHA-2 (خوارزمية التجزئة الآمنة 2) أو خوارزمية تالتجزئة الأقوى في سلسلة الشهادة.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>مجموعات رموز TLS المدعمة بواسطة Office 365

تستخدم TLS *مجموعات رموز*، مجموعات من خوارزميات التشفير، لإنشاء اتصالات آمنة. Office 365 هذه القائمة مجموعات رموز التشفير المدرجة في الجدول التالي. يسرد الجدول مجموعات رموز التشفير حسب ترتيب القوة، مع إدراج مجموعة رموز أقوى أولا.

Office 365 استجابة لطلب اتصال من خلال محاولة الاتصال أولا باستخدام مجموعة رموز أكثر أمانا. إذا لم يعمل الاتصال، Office 365 مجموعة رموز ثاني أكثر أمانا في القائمة، وهكذا. تستمر الخدمة في أسفل القائمة حتى يتم قبول الاتصال. وبالمثل، Office 365 طلب اتصال، تختار الخدمة المتلقية ما إذا كان سيتم استخدام TLS أو مجموعة رموز يجب استخدامها.

| اسم مجموعة Cipher | خوارزمية/قوة تبادل المفاتيح | إعادة توجيه العمل | Cipher/strength | خوارزمية/قوة المصادقة |
|:-----|:-----|:-----|:-----|:-----|
| TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  <br/> | ECDH/192  <br/> | نعم  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  <br/> | ECDH/128  <br/> | نعم  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384  <br/> | ECDH/192  <br/> | نعم  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256  <br/> | ECDH/128  <br/> | نعم  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA     <br/> | ECDH/192  <br/> | نعم  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA     <br/> | ECDH/128  <br/> | نعم  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_256_GCM_SHA384        <br/> | RSA/112   <br/> | لا   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_128_GCM_SHA256        <br/> | RSA/112   <br/> | لا   <br/> | AES/256  <br/> | RSA/112  <br/> |

تدعم مجموعات التشفير التالية بروتوكولات TLS 1.0 و1.1 حتى تاريخ الاهمية. بالنسبة سحابة القطاع الحكومي عالية و DoD التي تم إهمالها في 15 يناير 2020. بالنسبة للبيئات سحابة القطاع الحكومي وبيئات العالم التي كان تاريخها 15 أكتوبر 2020.

| البروتوكولات | اسم مجموعة Cipher | خوارزمية/قوة تبادل المفاتيح | إعادة توجيه العمل | Cipher/strength | خوارزمية/قوة المصادقة | 
|:-----|:-----|:-----|:-----|:-----|:-----|
| TLS 1.0، 1.1، 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> | ECDH/192  <br/> | نعم  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0، 1.1، 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> | ECDH/128  <br/> | نعم  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0، 1.1، 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA        <br/> | RSA/112   <br/> | لا   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0، 1.1، 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA        <br/> | RSA/112   <br/> | لا   <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0، 1.1، 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> | RSA/112   <br/> | لا   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0، 1.1، 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> | RSA/112   <br/> | لا   <br/> | AES/256  <br/> | RSA/112  <br/> |

تستخدم Office 365 منتجات معينة (بما في ذلك Microsoft Teams) [Azure Front Door](/azure/frontdoor/front-door-overview) لإنهاء اتصالات TLS واتصالات توجيه حركة مرور الشبكة بفعالية. يجب تمكين مجموعة واحدة على الأقل من مجموعات التشفير التي يدعمها [Azure Front Door عبر TLS 1.2](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-) للاتصال بهذه المنتجات بنجاح. بالنسبة Windows 10 أعلاه، نوصي بتمكين إحدى مجموعات رموز ECDHE أو كليهما من أجل أمان أفضل. Windows 7 و8 و8.1 مع مجموعات رموز ECDHE ل Azure Front Door وقد تم توفير مجموعات رموز DHE للتوافق مع أنظمة التشغيل هذه.

## <a name="related-articles"></a>المقالات ذات الصلة

[مجموعات TLS Cipher في Windows 10 v1903](/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[التشفير في Office 365](encryption.md)
  
[إعداد التشفير في Office 365 Enterprise](set-up-encryption.md)
  
[تنفيذ خطة TLS 1.0 في Windows حالة الأمان: 24 نوفمبر 2015](https://support.microsoft.com/kb/3117336)
  
[تحسينات تشفير TLS/SSL (Windows مركز المعلومات)](/previous-versions/windows/it-pro/windows-vista/cc766285(v=ws.10))
  
[التحضير ل TLS 1.2 في Office 365 Office 365 سحابة القطاع الحكومي](/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)

[ما هي مجموعات رموز التشفير الحالية التي يدعمها Azure Front Door؟](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-)
