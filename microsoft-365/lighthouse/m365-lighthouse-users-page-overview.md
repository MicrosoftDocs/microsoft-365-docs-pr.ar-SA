---
title: نظرة عامة على صفحة المستخدمين في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على صفحة المستخدمين.
ms.openlocfilehash: d817ab74d6dd24e644561684073189e68cf7e072
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66007273"
---
# <a name="overview-of-the-users-page-in-microsoft-365-lighthouse"></a>نظرة عامة على صفحة المستخدمين في Microsoft 365 Lighthouse 

يتيح لك Microsoft 365 Lighthouse إدارة المستخدمين عبر حسابات مستأجري العملاء عن طريق تحديد **المستخدمين** في جزء التنقل الأيمن لفتح صفحة المستخدمين. من هذه الصفحة، يمكنك البحث عن المستخدمين وتقييم حالة الأمان لحسابات المستخدمين والعمل عليها. يمكنك أيضا عرض رؤى حول المستخدمين المعرضين للمخاطر وحالة المصادقة متعددة العوامل وإعادة تعيين كلمة مرور الخدمة الذاتية.  
  
## <a name="search-users-tab"></a>علامة التبويب "البحث عن المستخدمين"  
  
من علامة التبويب "البحث عن المستخدمين"، يمكنك البحث بسرعة عبر المستأجرين عن مستخدمين محددين وتنفيذ إجراءات إدارة المستخدم الأساسية مثل إعادة تعيين كلمة مرور الحساب.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-search-users-tab.png" alt-text="Screenshot of the Search users tab.":::

## <a name="risky-users-tab"></a>علامة تبويب المستخدمين المحفوفة بالمخاطر

تعرض علامة التبويب "المستخدمون المحفوفوفة بالمخاطر" حسابات المستخدمين عبر المستأجرين الذين تم وضع علامة عليهم للسلوك المحفيف. حدد أي من المستخدمين لعرض مزيد من المعلومات حول المخاطر المكتشفة أو للتخفيف من المخاطر عن طريق إعادة تعيين كلمة مرور المستخدم أو حظر تسجيل الدخول. لمزيد من المعلومات حول أنواع المخاطر والكشف، راجع [ما هي المخاطر؟](/azure/active-directory/identity-protection/concept-identity-protection-risks).

تتضمن علامة التبويب "المستخدمون المحفوفوفة بالمخاطر" أيضا الخيارات التالية:
- **تصدير:** حدد لتصدير بيانات توافق الجهاز إلى ملف قيم مفصولة بفواصل Excel (.csv).
- **تحديث:** حدد لاسترداد أحدث بيانات توافق الجهاز.
- **تأكيد المستخدم (المستخدمين) الذين تم اختراقهم:** حدد لتأكيد تعرض المستخدم للاختراق.
- **تجاهل مخاطر المستخدم (المستخدمين):** حدد لتجاهل مخاطر المستخدم.  
- **إعادة تعيين كلمة المرور:** حدد لتغيير كلمة مرور المستخدم أو إعادة تعيينها.
- **حظر تسجيل الدخول:** حدد لمنع أي شخص من تسجيل الدخول بهذا المستخدم.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-risky-users-tab.png" alt-text="لقطة شاشة لعلامة التبويب «Risky users».":::

## <a name="multifactor-authentication-tab"></a>علامة التبويب "مصادقة متعددة العوامل"

توفر علامة التبويب "مصادقة متعددة العوامل" معلومات مفصلة حول حالة تمكين المصادقة متعددة العوامل (MFA) عبر المستأجرين. حدد أي مستأجر في القائمة للاطلاع على مزيد من التفاصيل لهذا المستأجر، بما في ذلك نهج الوصول المشروط التي تتطلب المصادقة متعددة العوامل التي تم تكوينها بالفعل والمستخدمين الذين لم يسجلوا بعد للحصول على المصادقة متعددة العوامل.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-mfa-tab.png" alt-text="لقطة شاشة لعلامة تبويب المصادقة متعددة العوامل.":::

## <a name="password-reset-tab"></a>علامة التبويب "إعادة تعيين كلمة المرور"

تعرض علامة التبويب "إعادة تعيين كلمة المرور" معلومات مفصلة حول حالة تمكين إعادة تعيين كلمة مرور الخدمة الذاتية عبر المستأجرين. كما يوفر رؤى حول المستخدمين الذين تم تمكينهم ولكن لا يزالون بحاجة إلى التسجيل قبل أن يتمكنوا من إعادة تعيين كلمة المرور الخاصة بهم بأنفسهم.

:::image type="content" source="../media/m365-lighthouse-users-page-overview/users-password-reset-tab.png" alt-text="لقطة شاشة لعلامة تبويب إعادة تعيين كلمة المرور.":::

## <a name="related-content"></a>المحتويات ذات الصلة

[نظرة عامة على صفحة توافق جهاز Lighthouse Microsoft 365](m365-lighthouse-device-compliance-page-overview.md) (مقالة)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)
