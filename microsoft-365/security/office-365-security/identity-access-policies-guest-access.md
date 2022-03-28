---
title: سياسات الوصول إلى الأجهزة والهوية للسماح بالوصول إلى الضيف والمستخدم الخارجي B2B - Microsoft 365 للمؤسسات | Microsoft Docs
description: يصف الوصول الشرطي الموصى به والسياسات ذات الصلة لحماية وصول الضيوف والمستخدمين الخارجيين.
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
ms.technology: mdo
ms.openlocfilehash: 71e4b3d5f2a8cbf147a9aa50dd849be14047e27d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575408"
---
# <a name="policies-for-allowing-guest-access-and-b2b-external-user-access"></a>سياسات السماح بالوصول إلى الضيف والوصول إلى المستخدم الخارجي B2B

تناقش هذه المقالة ضبط هوية الصفر الموثوق بها ونهج الوصول إلى الجهاز الموصى بها للسماح بالوصول إلى الضيوف والمستخدمين الخارجيين الذين لديهم حساب Azure Active Directory (Azure AD) Business-to-Business (B2B). يعتمد هذا الإرشاد على [الهوية المشتركة ونهج الوصول إلى الأجهزة](identity-access-policies.md).

تم تصميم هذه التوصيات لتطبيقها على **مستوى** الحماية لنقطة البداية. ولكن يمكنك أيضا ضبط التوصيات استنادا إلى احتياجاتك **الخاصة لحماية المؤسسة** **والأمان** المتخصصة.

لا يمنح توفير مسار حسابات B2B للمصادقة مع مستأجر Azure AD هذه الحسابات إمكانية الوصول إلى بيئتك بالكامل. يمكن لمستخدمي B2B وحساباتهم الوصول إلى الخدمات والموارد، مثل الملفات، التي تمت مشاركتها معهم بواسطة نهج الوصول الشرطي.

## <a name="updating-the-common-policies-to-allow-and-protect-guests-and-external-user-access"></a>تحديث السياسات الشائعة للسماح للضيوف والوصول إلى المستخدمين الخارجيين وحمايتهم

يعرض هذا الرسم التخطيطي السياسات التي تريد إضافتها أو تحديثها بين سياسات الوصول إلى الأجهزة والهوية المشتركة، لضيف B2B والوصول إلى المستخدم الخارجي.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png" alt-text="ملخص تحديثات النهج لحماية وصول الضيف." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-guest.png":::

يسرد الجدول التالي السياسات التي تحتاج إما إلى إنشائها وتحديثها. ترتبط النهج الشائعة بتعليمات التكوين المقترنة [في مقالة](identity-access-policies.md) سياسات الوصول إلى الأجهزة والهوية الشائعة.

|مستوى الحماية|السياسات|معلومات إضافية|
|---|---|---|
|**نقطة البداية**|[طلب MFA دائما للضيوف والمستخدمين الخارجيين](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|قم بإنشاء هذا النهج الجديد وتكوين: <ul><li>**للواجبات > المستخدمون** والمجموعات > تضمين، اختر تحديد المستخدمين والمجموعات، ثم حدد كل المستخدمين **الضيوف والخارجيين**.</li><li>بالنسبة **إلى > شروط >** تسجيل الدخول، اترك كل الخيارات غير محددة لفرض المصادقة متعددة العوامل (MFA) دائما.</li></ul>|
||[يتطلب MFA عندما تكون مخاطر تسجيل الدخول *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|قم بتعديل هذا النهج لاستبعاد الضيوف والمستخدمين الخارجيين.|

لتضمين الضيوف والمستخدمين الخارجيين أو استبعادهم في سياسات الوصول الشرطي، بالنسبة إلى الواجبات > المستخدمون والمجموعات > تضمين أو **استبعاد**، تحقق من جميع المستخدمين **الخارجيين والضيوف**.

![لقطة شاشة لمراقبة عناصر التحكم لاستبعاد الضيوف والمستخدمين الخارجيين.](../../media/microsoft-365-policies-configurations/identity-access-exclude-guests-ui.png)

## <a name="more-information"></a>معلومات إضافية

### <a name="guests-and-external-user-access-with-microsoft-teams"></a>وصول الضيوف والمستخدمين الخارجيين باستخدام Microsoft Teams

Microsoft Teams المستخدمين التاليين:

- **يستخدم وصول** الضيف حساب Azure AD B2B الذي يمكن إضافته كعضو في فريق والحصول على حق الوصول إلى الاتصالات والموارد الخاصة بالفريق.

- **الوصول الخارجي** للمستخدم الخارجي الذي ليس لديه حساب B2B. يتضمن وصول المستخدم الخارجي الدعوات والمكالمات والمحادثات والاجتماعات، ولكنه لا يتضمن عضوية الفريق والوصول إلى موارد الفريق.

لمزيد من المعلومات، راجع [المقارنة بين الضيوف والوصول إلى المستخدم الخارجي للفرق](/microsoftteams/communicate-with-users-from-other-organizations#compare-external-and-guest-access).

لمزيد من المعلومات حول تأمين نهج الوصول إلى Teams، راجع توصيات النهج لتأمين Teams والملفات [والمجموعات](teams-access-policies.md).

### <a name="require-mfa-always-for-guest-and-external-users"></a>طلب MFA دائما للمستخدمين الخارجيين والضيوف

يطالب هذا النهج الضيوف بالتسجيل للحصول على MFA في المستأجر الخاص بك، بغض النظر عما إذا كانوا مسجلين ل MFA في المستأجر المنزلي. عند الوصول إلى الموارد في المستأجر، يجب على الضيوف والمستخدمين الخارجيين استخدام MFA لكل طلب.

### <a name="excluding-guests-and-external-users-from-risk-based-mfa"></a>استبعاد الضيوف والمستخدمين الخارجيين من MFA المستند إلى المخاطر

في حين يمكن أن تفرض المؤسسات سياسات مستندة إلى المخاطر لمستخدمي B2B الذين يستخدمون Azure AD Identity Protection، هناك قيود في تنفيذ Azure AD Identity Protection لمستخدمي التعاون في B2B في دليل موارد بسبب هويتهم الموجودة في دليل المنزل. نظرا لهذه القيود، توصي Microsoft باستبعاد الضيوف من سياسات MFA المستندة إلى المخاطر ومطلب هؤلاء المستخدمين استخدام MFA دائما.

لمزيد من المعلومات، راجع قيود [حماية الهوية لمستخدمي التعاون في B2B](/azure/active-directory/identity-protection/concept-identity-protection-b2b#limitations-of-identity-protection-for-b2b-collaboration-users).

### <a name="excluding-guests-and-external-users-from-device-management"></a>استبعاد الضيوف والمستخدمين الخارجيين من إدارة الأجهزة

يمكن لمنظمه واحدة فقط إدارة الجهاز. إذا لم تستثني الضيوف والمستخدمين الخارجيين من السياسات التي تتطلب توافق الأجهزة، فإن هذه السياسات ستحظر هؤلاء المستخدمين.

## <a name="next-step"></a>الخطوة التالية

![الخطوة 4: سياسات تطبيقات Microsoft 365 السحابة و Microsoft Defender لتطبيقات السحابة.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

تكوين سياسات الوصول الشرطي ل:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
- [Microsoft Defender لتطبيقات السحابة](mcas-saas-access-policies.md)
 
