---
title: نهج الوصول إلى الهوية والجهاز للسماح للمستخدم الضيف والمستخدم الخارجي بالوصول إلى B2B - Microsoft 365 للمؤسسات | Microsoft Docs
description: يصف الوصول المشروط الموصى به والنهج ذات الصلة لحماية وصول الضيوف والمستخدمين الخارجيين.
ms.prod: m365-security
ms.topic: article
ms.author: dansimp
author: dansimp
audience: Admin
manager: Laurawi
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: c6784f73b431826063d94794606b373662446324
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750133"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>نهج السماح بوصول الضيف ووصول المستخدم الخارجي إلى B2B

تناقش هذه المقالة تعديل نهج الهوية ثقة معدومة والوصول إلى الأجهزة الموصى بها للسماح بالوصول إلى الضيوف والمستخدمين الخارجيين الذين لديهم حساب Azure Active Directory (Azure AD) Business-to-Business (B2B). يعتمد هذا التوجيه على [نهج الهوية والوصول إلى الجهاز الشائعة](identity-access-policies.md).

تم تصميم هذه التوصيات لتطبيقها على مستوى الحماية **لنقطة البداية** . ولكن يمكنك أيضا ضبط التوصيات بناء على احتياجاتك الخاصة لحماية الأمان الخاصة **بالمؤسسات** **والمتخصصة** .

لا يمنح توفير مسار لحسابات B2B للمصادقة مع مستأجر Azure AD هذه الحسابات الوصول إلى بيئتك بأكملها. يمكن لمستخدمي B2B وحساباتهم الوصول إلى الخدمات والموارد، مثل الملفات، التي تمت مشاركتها معهم بواسطة نهج الوصول المشروط.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>تحديث النهج الشائعة للسماح للضيوف والوصول إلى المستخدمين الخارجيين وحمايتها

يوضح هذا الرسم التخطيطي النهج التي يجب إضافتها أو تحديثها بين نهج الهوية والوصول إلى الأجهزة الشائعة، للوصول إلى الضيف B2B والمستخدم الخارجي.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="ملخص تحديثات النهج لحماية وصول الضيف" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

يسرد الجدول التالي النهج التي تحتاج إلى إنشائها وتحديثها. ترتبط النهج الشائعة بإرشادات التكوين المقترنة في مقالة [نهج الوصول إلى الأجهزة والهوية الشائعة](identity-access-policies.md) .

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[طلب المصادقة متعددة العوامل دائما للضيوف والمستخدمين الخارجيين](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|إنشاء هذا النهج الجديد وتكوين: <ul><li>بالنسبة **إلى "الواجبات" > "المستخدمون" والمجموعات > "تضمين**"، اختر **"تحديد مستخدمين ومجموعات**"، ثم حدد **"كافة المستخدمين الضيوف والخارجيين**".</li><li>بالنسبة **إلى التعيينات > الشروط > تسجيل الدخول**، اترك كافة الخيارات غير محددة لفرض المصادقة متعددة العوامل (MFA) دائما.</li></ul>|
||[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تعديل هذا النهج لاستبعاد الضيوف والمستخدمين الخارجيين.|

لتضمين الضيوف والمستخدمين الخارجيين أو استبعادهم في نهج الوصول المشروط، بالنسبة **للواجبات > المستخدمين والمجموعات > تضمينها** أو **استبعادها**، تحقق من **كافة المستخدمين الضيوف والخارجيين**.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png" alt-text="عناصر التحكم لاستبعاد الضيوف والمستخدمين الخارجيين" lightbox="../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png":::

## <a name="more-information"></a>معلومات إضافية

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>وصول الضيوف والمستخدمين الخارجيين باستخدام Microsoft Teams

يحدد Microsoft Teams المستخدمين التاليين:

- يستخدم **وصول الضيف** حساب B2B Azure AD الذي يمكن إضافته كعضو في فريق ويمكن الوصول إلى اتصالات الفريق وموارده.

- **الوصول الخارجي** هو لمستخدم خارجي ليس لديه حساب B2B. يتضمن وصول المستخدم الخارجي الدعوات والمكالمات والدردشات والاجتماعات، ولكنه لا يتضمن عضوية الفريق والوصول إلى موارد الفريق.

لمزيد من المعلومات، راجع [المقارنة بين وصول الضيوف والمستخدم الخارجي للفرق](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

لمزيد من المعلومات حول تأمين نهج الوصول إلى الهوية والجهاز ل Teams، راجع [توصيات النهج لتأمين دردشات Teams ومجموعاته وملفاته](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>طلب المصادقة متعددة العوامل دائما للمستخدمين الضيوف والخارجيين

يطالب هذا النهج الضيوف بالتسجيل للحصول على المصادقة متعددة العوامل (MFA) في المستأجر الخاص بك، بغض النظر عما إذا كانوا مسجلين في المصادقة متعددة العوامل (MFA) في مستأجر المنزل الخاص بهم. عند الوصول إلى الموارد في المستأجر الخاص بك، يطلب من الضيوف والمستخدمين الخارجيين استخدام المصادقة متعددة العوامل لكل طلب.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>استبعاد الضيوف والمستخدمين الخارجيين من المصادقة متعددة العوامل المستندة إلى المخاطر

بينما يمكن للمؤسسات فرض نهج تستند إلى المخاطر لمستخدمي B2B باستخدام Azure AD Identity Protection، هناك قيود في تنفيذ Azure AD Identity Protection لمستخدمي التعاون B2B في دليل الموارد بسبب هويتهم الموجودة في دليلهم الرئيسي. نظرا لهذه القيود، توصي Microsoft باستبعاد الضيوف من نهج المصادقة متعددة العوامل المستندة إلى المخاطر وتتطلب من هؤلاء المستخدمين استخدام المصادقة متعددة العوامل دائما.

لمزيد من المعلومات، راجع [قيود Identity Protection لمستخدمي تعاون B2B](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>استبعاد الضيوف والمستخدمين الخارجيين من إدارة الأجهزة

يمكن لمؤسسة واحدة فقط إدارة جهاز. إذا لم تستبعد الضيوف والمستخدمين الخارجيين من النهج التي تتطلب توافق الجهاز، فستؤدي هذه النهج إلى حظر هؤلاء المستخدمين.

## <a name="next-step"></a>الخطوة التالية

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="النهج الخاصة بتطبيقات سحابة Microsoft 365 Microsoft Defender for Cloud Apps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

تكوين نهج الوصول المشروط من أجل:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Microsoft Defender for Cloud Apps](mcas-saas-access-policies.md)
 
