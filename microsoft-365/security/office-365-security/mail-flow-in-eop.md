---
title: تدفق البريد في EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
ms.assetid: e109077e-cc85-4c19-ae40-d218ac7d0548
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤول التعرف على خيارات تكوين تدفق البريد التوجيه في Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1d7bca416a6144e2745a2c5d631c3e634e935ff4
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/23/2021
ms.locfileid: "63567115"
---
# <a name="mail-flow-in-eop"></a>تدفق البريد في EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في Microsoft 365 المؤسسات التي بها علب بريد Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، تمر كل الرسائل المرسلة إلى مؤسستك عبر EOP قبل أن يراها العاملون لديك. تتوفر لديك خيارات حول كيفية توجيه الرسائل التي تمر عبر EOP لطريقة المعالجة قبل توجيهها إلى علبة الوارد الخاصة بالعامل.

## <a name="working-with-messages-and-message-access-options"></a>استخدام خيارات الوصول إلى الرسائل والرسائل

يوفر EOP المرونة في كيفية توجيه رسائلك. تشرح المواضيع التالية الخطوات في عملية تدفق البريد.

[استخدام حظر Edge المستند إلى الدليل لرفض الرسائل المرسلة إلى مستلمين غير صالحين](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) يصف ميزة حظر Edge المستندة إلى الدليل التي تسمح لك برفض رسائل المستلمين غير الصالحين في محيط شبكة الخدمة.

[يصف عرض المجالات المقبولة أو تحريرها في EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) كيفية إدارة المجالات المقترنة بالخدمة EOP.

إذا أضفت مكنونات فرعية إلى مؤسستك، يمكن أن تساعدك خدمة EOP على إدارة هذه أيضا. تعرف على المزيد حول المناطق الفرعية في [تمكين تدفق البريد للمناوين](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains) الفرعية في Exchange Online.

[تكوين تدفق البريد باستخدام الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) يقدم الموصلات ويظهر كيفية استخدامها لتخصيص توجيه البريد. تتضمن السيناريوهات ضمان التواصل الآمن مع مؤسسة شريكة وإعداد مضيف ذكي.

[تصف التصفية المحسنة للموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) كيفية تكوين الموصلات إذا تم توجيه بريدك إلى خدمة أو جهاز قبل EOP.

في البيئات المختلطة حيث يحمي EOP علب بريد Exchange المحلية، ستحتاج إلى تكوين قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) في قواعد Exchange. تترجم قواعد تدفق البريد هذه قرار تصفية البريد العشوائي ل EOP بحيث يمكن لقاعدة البريد الإلكتروني غير الهام في علبة البريد نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام. للحصول على التفاصيل، راجع [تكوين EOP لتسليم البريد العشوائي إلى مجلد البريد الإلكتروني غير الهام في البيئات المختلطة](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). إذا كنت لا تريد نقل الرسائل إلى مجلد البريد الإلكتروني غير الهام الخاص بكل مستخدم، يمكنك اختيار إجراء آخر بتحرير سياسات مكافحة البريد العشوائي (المعروفة أيضا باسم سياسات تصفية المحتوى). لمزيد من المعلومات، راجع [تكوين سياسات مكافحة البريد العشوائي](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>التحقق من تدفق البريد

للتحقق من أن إعداد EOP، بما في ذلك تكوين الموصل، يعمل بشكل صحيح، راجع "كيف يمكنك معرفة كيفية عمل هذه المهمة؟" في [إعداد خدمة EOP](/exchange/standalone-eop/set-up-your-eop-service).

[اختبار تدفق البريد عن طريق التحقق من Microsoft 365 الموصلات](/exchange/mail-flow-best-practices/test-mail-flow) يوفر إرشادات لاختبار إعداد تدفق البريد بشكل صحيح.
