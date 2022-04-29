---
title: نظرة ثاقبة لتدفق البريد الصادر والوارد في لوحة معلومات تدفق البريد
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: يمكن للمسؤولين التعرف على رؤى تدفق البريد الصادر والوارد في لوحة معلومات تدفق البريد في مركز التوافق & الأمان.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f856e2b9a4829531966802f2594f26c19e6ab7e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131185"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>نظرة ثاقبة لتدفق البريد الصادر والوارد في مركز توافق & الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تجمع نتيجة تحليلات **تدفق البريد الصادر والوارد** في [لوحة معلومات تدفق البريد](mail-flow-insights-v2.md) في [مركز التوافق & الأمان](https://protection.office.com) المعلومات من [تقرير الموصل](view-mail-flow-reports.md#connector-report) **وتقرير نظرة عامة حول TLS** السابق في مكان واحد.

يعرض عنصر واجهة المستخدم تشفير TLS المستخدم للاتصال عند تسليم الرسائل من وإلى مؤسستك. يتم تشفير الاتصالات التي تم تأسيسها مع خدمات البريد الإلكتروني الأخرى بواسطة TLS عند تقديم TLS من قبل كلا الجانبين. يقدم عنصر واجهة المستخدم لقطة الأسبوع الماضي من تدفق البريد.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png" alt-text="عنصر واجهة مستخدم تدفق البريد الصادر والوارد في لوحة معلومات تدفق البريد في Security & Compliance Center" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png":::

ترتبط المعلومات في عنصر واجهة المستخدم بالموصلات وحماية رسائل TLS في Microsoft 365. لمزيد من المعلومات، راجع هذه المواضيع:

- [تكوين تدفق البريد باستخدام الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [كيفية استخدام Exchange Online TLS لتأمين اتصالات البريد الإلكتروني](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [تفاصيل المرجع التقني حول التشفير في Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>رسالة محمية أثناء النقل (بواسطة TLS)

عند النقر فوق **"عرض التفاصيل** " على عنصر واجهة المستخدم، تعرض لك القائمة المنبثقة **للرسالة المحمية أثناء النقل (بواسطة TLS)** حماية TLS للرسائل التي تدخل مؤسستك وتغادرها.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png" alt-text="القائمة المنبثقة للرسائل المحمية أثناء النقل (بواسطة TLS) التي تظهر بعد النقر فوق &quot;عرض التفاصيل&quot; على عنصر واجهة مستخدم البريد الإلكتروني الصادر والوارد" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png":::

حاليا، TLS 1.2 هو الإصدار الأكثر أمانا من TLS التي تقدمها Microsoft 365. في كثير من الأحيان، ستحتاج إلى معرفة تشفير TLS الذي يتم استخدامه لعمليات تدقيق التوافق. ربما ليس لديك علاقة مباشرة مع معظم خوادم البريد الإلكتروني المصدر والوجهة (أنت لا تملكها، ولا تملكها Microsoft)، لذلك ليس لديك العديد من الخيارات لتحسين تشفير TLS الذي تستخدمه هذه الخوادم.

ولكن، يمكنك استخدام [الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) لضمان أفضل حماية TLS متوفرة للرسائل التي يتم إرسالها بين خوادم البريد الإلكتروني وMicrosoft 365. غالبا ما يكون تدفق البريد بين Microsoft 365 وخوادم البريد الإلكتروني أو الخوادم الخاصة بك التي تنتمي إلى الشركاء أكثر أهمية وحساسة من الرسائل العادية، لذلك ستحتاج إلى تطبيق المزيد من الأمان والحذر على تلك الرسائل.

يمكنك ترقية خوادم البريد الإلكتروني الخاصة بك أو إصلاحها لتحسين تشفير TLS المستخدم، أو التواصل مع الشركاء للقيام بنفس الشيء. يعرض **"تقرير الموصل"** كل من وحدة تخزين تدفق البريد وتشفير TLS للرسائل التي تستخدم موصلات Microsoft 365.

يمكنك النقر فوق ارتباط **تقرير الموصل** للانتقال إلى [تقرير الموصل](view-mail-flow-reports.md#connector-report). قد تتوفر النتائج المعرفية التالية في صفحة **تقرير الموصل** إذا تم الكشف عن الشرط المقترن:

- **يرى موصل الشريك الوارد تدفق بريد TLS1.0 مهما**
- **يرى موصل OnPremises الوارد تدفق بريد TLS1.0 كبير**

بالنسبة إلى اتصالات TLS 1.0، تحتاج حقا إلى ترقية خادم البريد الإلكتروني أو خادم شريكك أو إصلاحه لتجنب أي مشاكل عند إهمال دعم TLS 1.0 في Microsoft 365 في النهاية.

## <a name="see-also"></a>راجع أيضًا

للحصول على معلومات حول نتائج التحليلات الأخرى في لوحة معلومات تدفق البريد، راجع [رؤى تدفق البريد في مركز التوافق & الأمان](mail-flow-insights-v2.md).
