---
title: نهج Teams الموصى بها - Microsoft 365 for enterprise | Microsoft Docs
description: يصف النهج الخاصة بتوصيات Microsoft حول كيفية تأمين اتصال Teams والوصول إلى الملفات.
author: MicrosoftHeidi
manager: serdars
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.author: heidip
ms.date: 09/30/2020
ms.reviewer: anmorgan
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
ms.openlocfilehash: 0e26923925416db48b0547bd9d044e367b56cef7
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750009"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>توصيات النهج لتأمين دردشات Teams ومجموعاته وملفاته

تصف هذه المقالة كيفية تنفيذ نهج الهوية والوصول إلى الأجهزة الموصى بها ثقة معدومة لحماية دردشات Microsoft Teams ومجموعاته ومحتواه مثل الملفات والتقويمات. تعتمد هذه الإرشادات على [نهج الهوية والوصول إلى الأجهزة الشائعة](identity-access-policies.md)، مع معلومات إضافية خاصة ب Teams. نظرا لأن Teams يتكامل مع منتجاتنا الأخرى، راجع أيضا [توصيات النهج لتأمين مواقع SharePoint وملفاته وتوصيات](sharepoint-file-access-policies.md) [النهج لتأمين البريد الإلكتروني](secure-email-recommended-policies.md).

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية ل Teams التي يمكن تطبيقها بناء على نقاوة احتياجاتك: نقطة البداية والمؤسسة والأمان المتخصص. يمكنك معرفة المزيد حول مستويات الأمان هذه والنهج الموصى بها المشار إليها من قبل هذه التوصيات في [تكوينات الوصول إلى الهوية والجهاز](microsoft-365-policies-configurations.md).

يتم تضمين المزيد من التوصيات الخاصة بنشر Teams في هذه المقالة لتغطية ظروف مصادقة معينة، بما في ذلك للمستخدمين من خارج مؤسستك. ستحتاج إلى اتباع هذه الإرشادات للحصول على تجربة أمان كاملة.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>بدء استخدام Teams قبل الخدمات التابعة الأخرى

لا تحتاج إلى تمكين الخدمات التابعة لبدء استخدام Microsoft Teams. كل هذه الخدمات "تعمل فقط". ومع ذلك، يجب أن تكون مستعدا لإدارة العناصر التالية المتعلقة بالخدمة:

- مجموعات Microsoft 365
- مواقع فريق SharePoint
- OneDrive for Business
- علب بريد Exchange
- دفق مقاطع الفيديو وخطط Planner (إذا تم تمكين هذه الخدمات)

## <a name="updating-common-policies-to-include-teams"></a>تحديث النهج الشائعة لتضمين Teams

لحماية الدردشة والمجموعات والمحتوى في Teams، يوضح الرسم التخطيطي التالي النهج التي يجب تحديثها من نهج الوصول إلى الأجهزة والهوية الشائعة. لكل نهج يتم تحديثه، تأكد من تضمين Teams والخدمات التابعة في تعيين تطبيقات السحابة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى Teams وخدماته التابعة" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

هذه الخدمات هي الخدمات التابعة التي يجب تضمينها في تعيين تطبيقات السحابة ل Teams:

- Microsoft Teams
- SharePoint و OneDrive for Business
- Exchange Online
- Skype for Business Online
- Microsoft Stream (تسجيلات الاجتماع)
- Microsoft Planner (مهام Planner وبيانات الخطة)

يسرد هذا الجدول النهج التي يجب إعادة النظر فيها وارتباطات بكل نهج في [نهج الوصول إلى الأجهزة والهوية الشائعة](identity-access-policies.md)، والتي تتضمن مجموعة النهج الأوسع لجميع تطبيقات Office.

|مستوى الحماية|السياسات|مزيد من المعلومات لتنفيذ Teams|
|---|---|---|
|**نقطة البداية**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تأكد من تضمين Teams والخدمات التابعة في قائمة التطبيقات. لدى Teams قواعد وصول الضيف والوصول الخارجي التي يجب مراعاتها أيضا، ستتعرف على المزيد حول هذه القواعد لاحقا في هذه المقالة.|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين Teams والخدمات التابعة في تعيين تطبيقات السحابة.|
||[يجب على المستخدمين المعرضين لمخاطر عالية تغيير كلمة المرور](identity-access-policies.md#high-risk-users-must-change-password)|يجبر مستخدمي Teams على تغيير كلمة المرور الخاصة بهم عند تسجيل الدخول إذا تم الكشف عن نشاط عالي المخاطر لحسابهم. تأكد من تضمين Teams والخدمات التابعة في قائمة التطبيقات.|
||[تطبيق نهج حماية بيانات APP](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من تضمين Teams والخدمات التابعة في قائمة التطبيقات. تحديث النهج لكل نظام أساسي (iOS وAndroid وWindows).|
|**Enterprise**|[طلب المصادقة متعددة العوامل (MFA) عندما يكون خطر تسجيل الدخول *منخفضا* أو *متوسطا* أو *مرتفعا*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|لدى Teams قواعد وصول الضيف والوصول الخارجي التي يجب مراعاتها أيضا، ستتعرف على المزيد حول هذه القواعد لاحقا في هذه المقالة. تضمين Teams والخدمات التابعة في هذا النهج.|
||[تحديد نهج توافق الجهاز](identity-access-policies.md#define-device-compliance-policies)|تضمين Teams والخدمات التابعة في هذا النهج.|
||[طلب أجهزة كمبيوتر وأجهزة *محمولة متوافقة*](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|تضمين Teams والخدمات التابعة في هذا النهج.|
|**أمان متخصص**|[*طلب المصادقة* متعددة العوامل (MFA) دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|بغض النظر عن هوية المستخدم، سيتم استخدام المصادقة متعددة العوامل من قبل مؤسستك. تضمين Teams والخدمات التابعة في هذا النهج. |

## <a name="teams-dependent-services-architecture"></a>بنية الخدمات التابعة ل Teams

للرجوع إليها، يوضح الرسم التخطيطي التالي الخدمات التي يعتمد عليها Teams. لمزيد من المعلومات والتوضيحات، راجع [Microsoft Teams وخدمات الإنتاجية ذات الصلة في Microsoft 365 لمهندسي تكنولوجيا المعلومات](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="رسم تخطيطي يوضح تبعيات Teams على SharePoint و OneDrive for Business وExchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>وصول الضيف والخارجي إلى Teams

يحدد Microsoft Teams أنواع الوصول التالية:

- يستخدم **وصول الضيف** حساب B2B Azure AD لضيف أو مستخدم خارجي يمكن إضافته كعضو في فريق والحصول على حق الوصول إلى اتصالات الفريق وموارده.

- **الوصول الخارجي** هو لمستخدم خارجي ليس لديه حساب B2B Azure AD. يمكن أن يتضمن الوصول الخارجي الدعوات والمشاركة في المكالمات والدردشات والاجتماعات، ولكنه لا يتضمن عضوية الفريق والوصول إلى موارد الفريق.

تنطبق نهج الوصول المشروط فقط على وصول الضيف في Teams لأن هناك حسابا مقابلا Azure AD B2B.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

للحصول على النهج الموصى بها للسماح بالوصول للمستخدمين الضيوف والخارجيين الذين لديهم حساب B2B Azure AD، راجع [نهج السماح بالوصول إلى حساب B2B الضيف والخارجي](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>وصول الضيف في Teams

بالإضافة إلى النهج الخاصة بالمستخدمين الداخليين لأعمالك أو مؤسستك، قد يقوم المسؤولون بتمكين وصول الضيف للسماح، على أساس المستخدم حسب المستخدم، للأشخاص من خارج شركتك أو مؤسستك بالوصول إلى موارد Teams والتفاعل مع أشخاص داخليين لأشياء مثل محادثات المجموعة والدردشة والاجتماعات.

لمزيد من المعلومات حول وصول الضيف وكيفية تنفيذه، راجع  [وصول الضيف إلى Teams](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>الوصول الخارجي في Teams

في بعض الأحيان يتم الخلط بين الوصول الخارجي والوصول إلى الضيف، لذلك من المهم أن يكون واضحا أن آليتي الوصول غير الداخليتين هاتين هما أنواع مختلفة من الوصول.

يعد الوصول الخارجي طريقة لمستخدمي Teams من مجال خارجي بأكمله للعثور على الاجتماعات واتصالها ومحادثتها وإعدادها مع المستخدمين في Teams. يقوم مسؤولو Teams بتكوين الوصول الخارجي على مستوى المؤسسة. لمزيد من المعلومات، راجع [إدارة الوصول الخارجي في Microsoft Teams](/microsoftteams/manage-external-access).

يتمتع مستخدمو الوصول الخارجي بإمكانية وصول ووظائف أقل من الفرد الذي تمت إضافته عبر وصول الضيف. على سبيل المثال، يمكن لمستخدمي الوصول الخارجي الدردشة مع المستخدمين الداخليين باستخدام Teams ولكن لا يمكنهم الوصول إلى قنوات الفريق أو الملفات أو الموارد الأخرى.

لا يستخدم الوصول الخارجي حسابات مستخدمي B2B Azure AD وبالتالي لا يستخدم نهج الوصول المشروط.

## <a name="teams-policies"></a>نهج Teams

خارج النهج الشائعة المذكورة أعلاه، هناك نهج خاصة ب Teams يمكن ويجب تكوينها لإدارة وظائف Teams المختلفة.

### <a name="teams-and-channels-policies"></a>نهج الفرق والقنوات

الفرق والقنوات هما عنصران شائعا الاستخدام في Microsoft Teams، وهناك نهج يمكنك وضعها للتحكم في ما يمكن للمستخدمين وما لا يمكنهم القيام به عند استخدام الفرق والقنوات. بينما يمكنك إنشاء فريق عمومي، إذا كان لدى مؤسستك 5000 مستخدم أو أقل، فمن المحتمل أن تجد أنه من المفيد أن يكون لديك فرق وقنوات أصغر لأغراض محددة، بما يتماشى مع احتياجاتك التنظيمية.

من المستحسن تغيير النهج الافتراضي أو إنشاء نهج مخصصة، ويمكنك معرفة المزيد حول إدارة نهجك في هذا الارتباط: [إدارة نهج الفرق في Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>نهج المراسلة

يمكن أيضا إدارة المراسلة أو الدردشة من خلال النهج العمومي الافتراضي، أو من خلال نهج مخصصة، وهذا يمكن أن يساعد المستخدمين على التواصل مع بعضهم بطريقة مناسبة لمؤسستك. يمكن مراجعة هذه المعلومات في [إدارة نهج المراسلة في Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>نهج الاجتماعات

لن تكتمل أي مناقشة حول Teams دون تخطيط النهج وتنفيذها حول اجتماعات Teams. تعد الاجتماعات مكونا أساسيا في Teams، ما يسمح للأشخاص بالاجتماعات والتقديم رسميا للعديد من المستخدمين في وقت واحد، ومشاركة المحتوى ذي الصلة بالاجتماع. يعد تعيين النهج المناسبة لمؤسستك حول الاجتماعات أمرا ضروريا.

لمزيد من المعلومات، راجع [إدارة نهج الاجتماع في Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>نهج أذونات التطبيق

يسمح لك Teams أيضا باستخدام التطبيقات في أماكن مختلفة، مثل القنوات أو الدردشات الشخصية. يعد وجود نهج حول التطبيقات التي يمكن إضافتها واستخدامها، وأين، أمرا ضروريا للحفاظ على بيئة غنية بالمحتوى آمنة أيضا.

لمزيد من القراءة حول نهج أذونات التطبيق، راجع [إدارة نهج أذونات التطبيق في Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>الخطوات التالية

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="الخطوة 4: نهج تطبيقات سحابة Microsoft 365" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

تكوين نهج الوصول المشروط من أجل:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
