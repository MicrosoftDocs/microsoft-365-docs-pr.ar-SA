---
title: نظرة ثاقبة حول تدفق البريد الصادر والداخل في لوحة معلومات تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: يمكن للمسؤولين التعرف على معلومات تدفق البريد الصادر والداخل في لوحة معلومات تدفق البريد في مركز التوافق & الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: acd1b46dfd93e2baee7861daae7b24daa42a324b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566570"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>نظرة ثاقبة حول تدفق البريد الصادر والداخل في مركز & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تجمع **معلومات** تدفق البريد الصادر والداخل في لوحة معلومات تدفق [](mail-flow-insights-v2.md) البريد في مركز التوافق & [](https://protection.office.com) الأمان المعلومات من تقرير [الموصل](view-mail-flow-reports.md#connector-report) والتقرير السابق ل **نظرة عامة حول TLS** في مكان واحد.

يعرض عنصر واجهة المستخدم تشفير TLS المستخدم للاتصال عند تسليم الرسائل إلى مؤسستك أو منها. يتم تشفير الاتصالات التي يتم تأسيسها مع خدمات البريد الإلكتروني الأخرى بواسطة TLS عندما يتم تقديم TLS من قبل الجانبين. يوفر عنصر واجهة المستخدم لقطة عن الأسبوع الأخير من تدفق البريد.

![عنصر واجهة مستخدم تدفق البريد الصادر والداخل في لوحة معلومات تدفق البريد في مركز & الأمان.](../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png)

ترتبط المعلومات في عنصر واجهة المستخدم بالموصلات وحماية رسائل TLS في Microsoft 365. لمزيد من المعلومات، راجع المواضيع التالية:

- [تكوين تدفق البريد باستخدام الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [تفاصيل المراجع التقنية حول التشفير في Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>رسالة محمية أثناء النقل (بواسطة TLS)

عندما تنقر فوق **عرض التفاصيل** على عنصر واجهة المستخدم، تعرض لك عنصر واجهة المستخدم من خلال عنصر واجهة مستخدم الرسالة المحمية أثناء النقل **(بواسطة TLS) حماية TLS** للرسائل التي تقوم بإدخال مؤسستك ومغادرتها.

![الرسائل المحمية أثناء النقل (بواسطة TLS) التي تظهر بعد النقر فوق عرض التفاصيل على عنصر واجهة مستخدم البريد الإلكتروني الصادر والداخل.](../../media/mfi-outbound-and-inbound-mail-flow-report-details.png)

حاليا، TLS 1.2 هو الإصدار الأكثر أمانا من TLS الذي يقدمه Microsoft 365. ستحتاج في أغلب الأحيان إلى معرفة تشفير TLS الذي يتم استخدامه لتدقيقات التوافق. من المحتمل ألا تكون لديك علاقة مباشرة مع معظم خوادم البريد الإلكتروني المصدر والوجهة (ولا تملكها Microsoft أيضا)، وبالتالي ليس لديك العديد من الخيارات لتحسين تشفير TLS الذي تستخدمه هذه الخوادم.

ولكن، يمكنك استخدام [الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) لضمان أفضل حماية متوفرة ل TLS للرسائل المرسلة بين خوادم البريد الإلكتروني Microsoft 365. غالبا ما يكون تدفق Microsoft 365 بين خوادم البريد الإلكتروني أو خوادم البريد الإلكتروني الخاصة بك التي تنتمي إلى الشركاء أكثر أهمية وحساسية من الرسائل العادية، لذا يجب تطبيق المزيد من الأمان وتوخي الحذر على تلك الرسائل.

يمكنك ترقية خوادم البريد الإلكتروني الخاصة بك أو إصلاحها لتحسين تشفير TLS الذي يتم استخدامه، أو التواصل مع الشركاء للقيام بالشيء نفسه. يعرض **"تقرير الموصل**" كلا من حجم تدفق البريد وتشفير TLS للرسائل التي تستخدم Microsoft 365 الموصلات.

يمكنك النقر فوق ارتباط **تقرير الموصل** للذهاب إلى [تقرير الموصل](view-mail-flow-reports.md#connector-report). قد تتوفر الرؤى التالية على صفحة تقرير **الموصل** إذا تم الكشف عن الحالة المقترنة:

- **موصل الشريك الوارد يرى تدفق بريد TLS1.0 هام**
- **Inbound OnPremises connector seeing significant TLS1.0 mail flow**

بالنسبة إلى اتصالات TLS 1.0، تحتاج فعلا إلى ترقية خادم البريد الإلكتروني أو خادم شريكك أو إصلاحه لتجنب أي مشاكل عند إهمال دعم TLS 1.0 في النهاية Microsoft 365.

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول رؤى أخرى في لوحة معلومات تدفق البريد، راجع تحليلات تدفق البريد في مركز التوافق & [الأمان](mail-flow-insights-v2.md).