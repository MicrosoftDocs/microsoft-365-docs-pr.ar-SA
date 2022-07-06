---
title: كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني
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
description: تعرف على كيفية استخدام كل من Exchange Online وMicrosoft 365 لأمان طبقة النقل (TLS) وإعادة توجيه السرية (FS) لتأمين اتصالات البريد الإلكتروني. احصل أيضا على معلومات حول الشهادة الصادرة عن Microsoft Exchange Online.
ms.openlocfilehash: 93f71e38e3063aeec0c423dbfea25ac463a3e46f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641549"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني

تعرف على كيفية استخدام كل من Exchange Online وMicrosoft 365 لأمان طبقة النقل (TLS) وإعادة توجيه السرية (FS) لتأمين اتصالات البريد الإلكتروني. كما يوفر معلومات حول الشهادة الصادرة عن Microsoft Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>أساسيات TLS ل Microsoft 365 و Exchange Online

أمان طبقة النقل (TLS) وSSL التي جاءت قبل TLS، هي بروتوكولات تشفير تؤمن الاتصال عبر شبكة باستخدام شهادات الأمان لتشفير اتصال بين أجهزة الكمبيوتر. تحل TLS محل طبقة مآخذ التوصيل الآمنة (SSL) وغالبا ما يشار إليها باسم SSL 3.1. تستخدم Exchange Online TLS لتشفير الاتصالات بين خوادم Exchange والاتصالات بين خوادم Exchange والخوادم الأخرى مثل خوادم Exchange المحلية أو خوادم البريد الخاصة بالمستلمين. بمجرد تشفير الاتصال، يتم إرسال جميع البيانات المرسلة من خلال هذا الاتصال من خلال القناة المشفرة. ومع ذلك، إذا قمت بإعادة توجيه رسالة تم إرسالها من خلال اتصال مشفر بواسطة TLS، فلن يتم تشفير هذه الرسالة بالضرورة. TLS لا يقوم بتشفير الرسالة، فقط الاتصال.
  
إذا كنت تريد تشفير الرسالة، فاستخدم تقنية تشفير تقوم بتشفير محتويات الرسالة. على سبيل المثال، يمكنك استخدام تشفير الرسائل في Microsoft Purview أو S/MIME. راجع [تشفير البريد الإلكتروني في Office 365](email-encryption.md) [وتشفير الرسائل](ome.md) للحصول على معلومات حول تشفير الرسالة في Office 365.
  
استخدم TLS في الحالات التي تريد فيها إعداد قناة آمنة من المراسلات بين Microsoft والمؤسسة المحلية أو مؤسسة أخرى، مثل شريك. يحاول Exchange Online دائما استخدام TLS أولا لتأمين بريدك الإلكتروني ولكن لا يمكنه ذلك إذا لم يقدم الطرف الآخر أمان TLS. تابع القراءة لمعرفة كيفية تأمين كل البريد إلى الخوادم المحلية أو الشركاء المهمين باستخدام *الموصلات*.

لتوفير أفضل تشفير في فئته لعملائنا، قامت Microsoft بإهمال الإصدارين 1.0 و1.1 من بروتوكول أمان طبقة النقل (TLS) في [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) [Office 365 GCC](tls-1-2-in-office-365-gcc.md). ومع ذلك، يمكنك الاستمرار في استخدام اتصال SMTP غير مشفر دون أي TLS. لا نوصي بإرسال البريد الإلكتروني دون أي تشفير.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>كيفية استخدام Exchange Online TLS بين العملاء Exchange Online

تقوم Exchange Online الخوادم دائما بتشفير الاتصالات بخوادم Exchange Online الأخرى في مراكز البيانات الخاصة بنا باستخدام TLS 1.2. عند إرسال رسالة إلى مستلم موجود داخل مؤسستك، Exchange Online إرسال الرسالة تلقائيا عبر اتصال مشفر باستخدام TLS. Exchange Online أيضا إرسال البريد الإلكتروني الذي ترسله إلى عملاء آخرين عبر الاتصالات المشفرة باستخدام TLS المؤمنة باستخدام Forward Botcy.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>كيف يستخدم Microsoft 365 TLS بين Microsoft 365 والشركاء الخارجيين الموثوق بهم

بشكل افتراضي، تستخدم Exchange Online دائما *TLS انتهازية*. تعني TLS الانتهازية Exchange Online تحاول دائما تشفير الاتصالات مع الإصدار الأكثر أمانا من TLS أولا، ثم تعمل في طريقها لأسفل قائمة عبارات TLS حتى تجد واحدا يمكن لكلا الطرفين الاتفاق عليه. إذا لم تكن قد قمت بتكوين Exchange Online للتأكد من أن الرسائل الموجهة إلى هذا المستلم يجب أن تستخدم اتصالات آمنة، فسيتم إرسال الرسالة بشكل افتراضي دون تشفير إذا كانت المؤسسة المستلمة لا تدعم تشفير TLS. تعد TLS الانتهازية كافية لمعظم الشركات. ومع ذلك، بالنسبة للشركات التي لديها متطلبات توافق مثل المؤسسات الطبية أو المصرفية أو الحكومية، يمكنك تكوين Exchange Online لطلب TLS أو فرضه. للحصول على الإرشادات، راجع [تكوين تدفق البريد باستخدام الموصلات في Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
إذا قررت تكوين TLS بين مؤسستك ومنظمة شريكة موثوق بها، Exchange Online يمكن استخدام *TLS المفروض* لإنشاء قنوات اتصال موثوق بها. تتطلب TLS المفروضة من مؤسستك الشريكة المصادقة على Exchange Online بشهادة أمان لإرسال البريد إليك. سيحتاج شريكك إلى إدارة شهاداته الخاصة. تستخدم Exchange Online الموصلات لحماية الرسائل التي ترسلها من الوصول غير المصرح به قبل وصولها إلى موفر البريد الإلكتروني للمستلم. للحصول على معلومات حول استخدام الموصلات لتكوين تدفق البريد، راجع [تكوين تدفق البريد باستخدام الموصلات في Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>عمليات نشر Exchange Server المختلطة و TLS

إذا كنت تدير نشر Exchange المختلط، فسيحتاج خادم Exchange المحلي إلى المصادقة إلى Microsoft 365 باستخدام شهادة أمان لإرسال بريد إلى المستلمين الذين توجد علب بريدهم في Office 365 فقط. ونتيجة لذلك، تحتاج إلى إدارة شهادات الأمان الخاصة بك لخوادم Exchange المحلية. يجب أيضا تخزين شهادات الخادم هذه وصيانتها بشكل آمن. لمزيد من المعلومات حول إدارة الشهادات في عمليات النشر المختلطة، راجع [متطلبات الشهادة لعمليات التوزيع المختلطة](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>كيفية إعداد TLS المفروض Exchange Online في Office 365

بالنسبة Exchange Online العملاء، لكي يعمل TLS المفروض على تأمين كل رسائل البريد الإلكتروني المرسلة والمستلمة، تحتاج إلى إعداد أكثر من موصل واحد يتطلب TLS. ستحتاج إلى موصل واحد للرسائل المرسلة إلى علب بريد المستخدمين وموصل آخر للرسائل المرسلة من علب بريد المستخدمين. أنشئ هذه الموصلات في مركز إدارة Exchange في Office 365. للحصول على الإرشادات، راجع [تكوين تدفق البريد باستخدام الموصلات في Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>معلومات شهادة TLS Exchange Online

يتم وصف معلومات الشهادة المستخدمة من قبل Exchange Online في الجدول التالي. إذا كان شريك عملك يقوم بإعداد TLS مفروض على خادم البريد الإلكتروني الخاص به، فستحتاج إلى توفير هذه المعلومات له. لأسباب أمنية، تتغير شهاداتنا من وقت لآخر. الشهادة الحالية صالحة اعتبارا من 24 سبتمبر 2020.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>معلومات الشهادة الحالية صالحة من 24 سبتمبر 2020
  
| السمه | قيمه |
|:-----|:-----|
|مصدر جذر المرجع المصدق|DigiCert CA - 1|
|اسم الشهادة|mail.protection.outlook.com|
|المنظمه|Microsoft Corporation|
|وحدة المؤسسة|www.digicert.com|
|قوة مفتاح الشهادة|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>الحصول على مزيد من المعلومات حول TLS والشهادات وMicrosoft 365 وتنزيل الشهادات

[سلاسل تشفير Microsoft 365 وتنزيلات الشهادات](encryption-office-365-certificate-chains.md)

[سلاسل تشفير Microsoft 365 وتنزيلات الشهادات - DOD و GCC High](encryption-office-365-certificate-chains-itar.md)

للحصول على قائمة بمجموعات التشفير المدعومة، راجع [تفاصيل المرجع التقني حول التشفير](technical-reference-details-about-encryption.md).
  
[إعداد الموصلات لتدفق البريد الآمن مع مؤسسة شريكة](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[الموصلات مع أمان البريد الإلكتروني المحسن](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[التشفير في Microsoft 365](encryption.md)
