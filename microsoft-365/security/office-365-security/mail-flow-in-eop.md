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
description: يمكن مسؤول التعرف على خيارات تكوين تدفق البريد والتوجيه في Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: e0267af0297dce41657c76e97964e5c02fbe5815
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648734"
---
# <a name="mail-flow-in-eop"></a>تدفق البريد في EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في المؤسسات Microsoft 365 التي تحتوي على علب بريد Exchange Online أو مؤسسات Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online، تمر جميع الرسائل المرسلة إلى مؤسستك عبر EOP قبل أن يراها المستخدمون. لديك خيارات حول كيفية توجيه الرسائل التي تمر عبر EOP للمعالجة قبل توجيهها إلى علب بريد المستخدمين.

## <a name="working-with-messages-and-message-access-options"></a>استخدام خيارات الوصول إلى الرسائل والرسائل

يوفر EOP المرونة في كيفية توجيه رسائلك. تشرح المواضيع التالية الخطوات في عملية تدفق البريد.

[استخدام حظر الحافة المستندة إلى الدليل لرفض الرسائل المرسلة إلى مستلمين غير صالحين](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking) يصف ميزة حظر الحافة المستندة إلى الدليل التي تتيح لك رفض الرسائل للمستلمين غير الصالحين في محيط شبكة الخدمة.

توضح [طريقة عرض المجالات المقبولة أو تحريرها في EOP](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) كيفية إدارة المجالات المقترنة بخدمة EOP.

إذا أضفت مجالات فرعية إلى مؤسستك، يمكن أن تساعدك خدمة EOP على إدارة هذه المجالات أيضا. تعرف على المزيد حول المجالات الفرعية في [تمكين تدفق البريد للمساومات الفرعية في Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains).

[تكوين تدفق البريد باستخدام الموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) يقدم الموصلات ويظهر كيف يمكنك استخدامها لتخصيص توجيه البريد. تتضمن السيناريوهات ضمان الاتصال الآمن مع مؤسسة شريكة وإعداد مضيف ذكي.

تصف [التصفية المحسنة للموصلات](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) كيفية تكوين الموصلات إذا تم توجيه بريدك إلى خدمة أو جهاز قبل EOP.

في البيئات المختلطة حيث يحمي EOP علب بريد Exchange المحلية، تحتاج إلى تكوين قواعد تدفق البريد (المعروفة أيضا باسم قواعد النقل) في Exchange المحلية. تترجم قواعد تدفق البريد هذه حكم تصفية البريد العشوائي EOP بحيث يمكن لقاعدة البريد الإلكتروني غير الهام في علبة البريد نقل الرسالة إلى مجلد البريد الإلكتروني غير الهام. للحصول على التفاصيل، راجع [تكوين EOP لتسليم البريد العشوائي إلى مجلد البريد الإلكتروني غير الهام في البيئات المختلطة](/exchange/standalone-eop/configure-eop-spam-protection-hybrid). إذا كنت لا تريد نقل الرسائل إلى مجلد البريد الإلكتروني غير الهام لكل مستخدم، يمكنك اختيار إجراء آخر عن طريق تحرير نهج مكافحة البريد العشوائي (المعروفة أيضا بنهج تصفية المحتوى). لمزيد من المعلومات، راجع [تكوين نهج مكافحة البريد العشوائي](configure-your-spam-filter-policies.md).

## <a name="verify-mail-flow"></a>التحقق من تدفق البريد

للتحقق من أن إعداد EOP، بما في ذلك تكوين الموصل، يعمل بشكل صحيح، راجع "كيف تعرف أن هذه المهمة عملت؟" في [إعداد خدمة EOP.](/exchange/standalone-eop/set-up-your-eop-service)

[اختبار تدفق البريد عن طريق التحقق من صحة موصلات Microsoft 365](/exchange/mail-flow-best-practices/test-mail-flow) توفر إرشادات لاختبار إعداد تدفق البريد بشكل صحيح.
