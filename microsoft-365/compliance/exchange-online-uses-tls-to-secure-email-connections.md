---
title: كيفية Exchange Online "أمان طبقة النقل" (TLS) لتأمين اتصالات البريد الإلكتروني
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/08/2021
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4cde0cda-3430-4dc0-b489-f2c0736c929f
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: تعرف على Exchange Online Microsoft 365 استخدام أمان طبقة النقل (TLS) و إعادة توجيه المعلومات (FS) لتأمين اتصالات البريد الإلكتروني. احصل أيضا على معلومات حول الشهادة الصادرة عن Microsoft Exchange Online.
ms.openlocfilehash: 1caf4a8425f4a8e7c340e8a52d785027e99a1618
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63565909"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني

تعرف على Exchange Online Microsoft 365 استخدام أمان طبقة النقل (TLS) و إعادة توجيه المعلومات (FS) لتأمين اتصالات البريد الإلكتروني. يوفر أيضا معلومات حول الشهادة الصادرة عن Microsoft Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>أساسيات TLS Microsoft 365 Exchange Online

إن أمان طبقة النقل (TLS) وSSL الذي يأتي قبل TLS هو بروتوكولات تشفير آمنة للاتصالات عبر الشبكة باستخدام شهادات الأمان لتشفير اتصال بين أجهزة الكمبيوتر. تحل TLS مكان طبقة مآخذ التوصيل الآمنة (SSL) وغالبا ما يشار إليها ب SSL 3.1. Exchange Online TLS لتشفير الاتصالات بين خوادم Exchange والاتصالات بين خوادم Exchange وغيرها من الخوادم مثل خوادم Exchange أو خوادم البريد الخاصة بالمستلمين. بمجرد تشفير الاتصال، يتم إرسال كل البيانات المرسلة عبر هذا الاتصال عبر القناة المشفرة. ومع ذلك، إذا قمت ب إعادة توجيه رسالة تم إرسالها عبر اتصال مشفر بواسطة TLS، فمن غير الضروري تشفير هذه الرسالة. لا يقوم TLS بتشفير الرسالة، بل فقط الاتصال.
  
إذا كنت تريد تشفير الرسالة، فاستخدم تقنية تشفير تقوم بتشفير محتويات الرسالة. على سبيل المثال، يمكنك استخدام تشفير Office أو S/MIME. راجع [تشفير البريد الإلكتروني في Office 365](email-encryption.md) تشفير الرسائل من Office 365 [(OME) للحصول](ome.md) على معلومات حول تشفير الرسائل في Office 365.
  
استخدم TLS في الحالات التي تريد فيها إعداد قناة مراسلة آمنة بين Microsoft والمنظمة أو مؤسسة أخرى، مثل شريك. Exchange Online دائما استخدام TLS أولا لتأمين بريدك الإلكتروني ولكن لا يمكنه ذلك إذا لم يقدم الطرف الآخر أمان TLS. تابع القراءة لمعرفة كيفية تأمين كل البريد إلى الخوادم أو الشركاء المهمين المحليين باستخدام *الموصلات*.

لتوفير التشفير الأفضل في فئة العملاء، قامت Microsoft ب إهمال الإصدارين 1.0 و1.1 من أمان طبقة النقل (TLS) في Office 365 [Office 365 سحابة القطاع الحكومي](tls-1-2-in-office-365-gcc.md).[](tls-1.0-and-1.1-deprecation-for-office-365.md) ومع ذلك، يمكنك الاستمرار في استخدام اتصال SMTP غير مشفر بدون أي TLS. لا نوصي ببث البريد الإلكتروني بدون أي تشفير.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>كيفية Exchange Online استخدام TLS بين Exchange Online العملاء

Exchange Online تشفير الاتصالات إلى خوادم Exchange Online أخرى في مراكز البيانات لدينا باستخدام TLS 1.2. عندما ترسل رسالة إلى مستلم داخل مؤسستك، Exchange Online إرسال الرسالة تلقائيا عبر اتصال مشفر باستخدام TLS. Exchange Online أيضا إرسال البريد الإلكتروني الذي ترسله إلى العملاء الآخرين عبر الاتصالات المشفرة باستخدام TLS الآمنة باستخدام إعادة توجيه التكفير.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>كيفية Microsoft 365 استخدام TLS بين Microsoft 365 والشركاء الخارجيين الموثوق بهم

بشكل افتراضي، Exchange Online استخدام *TLS الانتهازية* دائما. تعني TLS الانتهازية أن Exchange Online دائما ما يحاول تشفير الاتصالات باستخدام الإصدار الأكثر أمانا من TLS أولا، ثم يعمل في أسفل قائمة Ciphers TLS حتى يعثر على واحد يمكن لكلا الطرفين الموافقة عليه. إلا إذا قمت بتكوين Exchange Online للتأكد من أن الرسائل التي يتم إرسالها إلى ذلك المستلم يجب أن تستخدم اتصالات آمنة، سيتم إرسال الرسالة بشكل افتراضي بدون تشفير إذا لم تكن مؤسسة المستلم تدعم تشفير TLS. إن TLS الانتهازية كافية لمعظم الشركات. ومع ذلك، بالنسبة للشركات التي لديها متطلبات توافق مثل المؤسسات الطبية أو المصرفية أو الحكومية، يمكنك تكوين Exchange Online طلب TLS أو فرضها. للحصول على الإرشادات، راجع [تكوين تدفق البريد باستخدام الموصلات في Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
إذا قررت تكوين TLS بين مؤسستك والمنظمة الشريكة الموثوق بها، Exchange Online استخدام *TLS* إجباريا لإنشاء قنوات اتصال موثوق بها. تتطلب TLS المجبرة من مؤسستك الشريكة Exchange Online شهادة أمان لإرسال البريد إليك. سيحتاج شريكك إلى إدارة شهاداته الخاصة. Exchange Online موصلات لحماية الرسائل التي ترسلها من الوصول غير المصرح به قبل وصولها إلى موفر البريد الإلكتروني للمستلم. للحصول على معلومات حول استخدام الموصلات لتكوين تدفق البريد، راجع تكوين تدفق البريد [باستخدام الموصلات في](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) Office 365.
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>عمليات نشر TLS Exchange Server المختلطة

إذا كنت تقوم بإدارة نشر Exchange مختلط، يجب أن يصادق خادم Exchange الداخلي على Microsoft 365 باستخدام شهادة أمان لإرسال البريد إلى المستلمين الذين لا توجد علب بريدهم إلا في Office 365. ونتيجة لذلك، ستحتاج إلى إدارة شهادات الأمان الخاصة بك للخوادم Exchange الخاصة بك. يجب أيضا تخزين شهادات الخادم هذه والمحافظة عليها بشكل آمن. لمزيد من المعلومات حول إدارة الشهادات في عمليات النشر المختلط، راجع [متطلبات الشهادة للنشرات المختلطة](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>كيفية إعداد TLS إجباريا Exchange Online في Office 365

بالنسبة Exchange Online العملاء، لكي تعمل TLS إجباريا على تأمين كل رسائل البريد الإلكتروني المرسلة والمستلمة، ستحتاج إلى إعداد أكثر من موصل واحد يتطلب TLS. ستحتاج إلى موصل واحد للرسائل المرسلة إلى علب بريد المستخدمين وموصل آخر للرسائل المرسلة من علب بريد المستخدمين. أنشئ هذه الموصلات في مركز إدارة Exchange في Office 365. للحصول على الإرشادات، راجع [تكوين تدفق البريد باستخدام الموصلات في Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>معلومات شهادة TLS Exchange Online

يتم وصف معلومات الشهادة التي Exchange Online بها في الجدول التالي. إذا كان شريك العمل الخاص بك يضبط TLS إجباريا على خادم البريد الإلكتروني الخاص به، فسوف تحتاج إلى توفير هذه المعلومات له. لأسباب تتعلق الأمان، تتغير شهاداتنا من وقت إلى آخر. الشهادة الحالية صالحة من 24 سبتمبر 2020.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>معلومات الشهادة الحالية صالحة من 24 سبتمبر 2020
  
| السمة | القيمة |
|:-----|:-----|
|مصدر جذر المرجع المشهادات|DigiCert CA – 1|
|اسم الشهادة|mail.protection.outlook.com|
|المؤسسة|Microsoft Corporation|
|وحدة المؤسسة|www.digicert.com|
|قوة مفتاح الشهادة|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>الحصول على مزيد من المعلومات حول TLS والشهادات Microsoft 365 الشهادات وتنزيلها

[Microsoft 365 التشفير وتنزيلها بالشهادات](encryption-office-365-certificate-chains.md)

[Microsoft 365 التشفير وتنزيل الشهادات - DOD سحابة القطاع الحكومي High](encryption-office-365-certificate-chains-itar.md)

للحصول على قائمة ب مجموعات الترميز المعتمدة، راجع [تفاصيل المراجع التقنية حول التشفير](technical-reference-details-about-encryption.md).
  
[إعداد الموصلات لتدفق البريد الآمن مع مؤسسة شريكة](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[الموصلات مع أمان محسن للبريد الإلكتروني](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[التشفير في Microsoft 365](encryption.md)
