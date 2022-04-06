---
title: سياسات Teams الموصى بها - Microsoft 365 للمؤسسات | Microsoft Docs
description: يصف هذه المقالة سياسات توصيات Microsoft حول كيفية تأمين Teams الوصول إلى الملفات والاتصالات.
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
ms.technology: mdo
ms.openlocfilehash: b659853d9323b4a1503cd75cff66a83cbd06e85e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682890"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>توصيات النهج لتأمين Teams الدردشات والمجموعات والملفات

تصف هذه المقالة كيفية تنفيذ الهوية الصفرية الموصى بها ونهج الوصول إلى الجهاز لحماية Microsoft Teams الدردشات والمجموعات والمحتوى مثل الملفات والتقويمات. يعتمد هذا الإرشاد على [الهوية](identity-access-policies.md) المشتركة ونهج الوصول إلى الجهاز، مع معلومات إضافية Teams خاصة. نظرا Teams التكامل مع منتجاتنا الأخرى، راجع أيضا توصيات النهج لتأمين SharePoint والملفات وتوصيات النهج [لتأمين البريد الإلكتروني](secure-email-recommended-policies.md).[](sharepoint-file-access-policies.md)

تستند هذه التوصيات إلى ثلاثة مستويات مختلفة من الأمان والحماية Teams يمكن تطبيقها بالاستناد إلى مجموعة احتياجاتك: نقطة البداية والمؤسسة والأمان المتخصص. يمكنك معرفة المزيد حول مستويات الأمان هذه ونهج الموصى بها التي تشير إليها هذه التوصيات في تكوينات الوصول إلى الأجهزة [والهوية](microsoft-365-policies-configurations.md).

يتم تضمين مزيد من Teams الخاصة بنشر المعلومات في هذه المقالة لتغطية ظروف مصادقة معينة، بما في ذلك للمستخدمين من خارج مؤسستك. ستحتاج إلى اتباع هذه الإرشادات للحصول على تجربة أمان كاملة.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>بدء العمل مع Teams قبل الخدمات التابعة الأخرى

لست بحاجة إلى تمكين الخدمات التابعة للبدء باستخدام Microsoft Teams. كل هذه الخدمات "تعمل فقط". ومع ذلك، يجب أن تكون مستعدا لإدارة العناصر التالية ذات الصلة بالخدمة:

- Microsoft 365 المجموعات
- SharePoint مواقع الفريق
- OneDrive for Business
- Exchange علب البريد
- دفق مقاطع الفيديو وخطط Planner (إذا تم تمكين هذه الخدمات)

## <a name="updating-common-policies-to-include-teams"></a>تحديث السياسات الشائعة لتضمين Teams

لحماية الدردشة والمجموعات والمحتوى في Teams، يوضح الرسم التخطيطي التالي السياسات التي يجب تحديثها من سياسات الوصول إلى الأجهزة والهوية المشتركة. لكل نهج يتم تحديثه، تأكد من تضمين Teams والخدمات التابعة في تعيين تطبيقات السحابة.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="ملخص تحديثات النهج لحماية الوصول إلى Teams والخدمات التابعة لها." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

هذه الخدمات هي الخدمات التابعة لتضمينها في تعيين تطبيقات السحابة Teams:

- Microsoft Teams
- SharePoint OneDrive for Business
- Exchange Online
- Skype for Business Online
- Microsoft Stream (تسجيلات الاجتماع)
- Microsoft Planner (مخطط المهام وخطط البيانات)

يسرد هذا الجدول النهج التي تحتاج إلى إعادة زيارة والربط بكل نهج في نهج الوصول إلى الأجهزة [](identity-access-policies.md)والهوية المشتركة، والتي تحتوي على مجموعة نهج أوسع لكل تطبيقات Office.

|مستوى الحماية|السياسات|مزيد من المعلومات Teams التطبيق|
|---|---|---|
|**نقطة البداية**|[يتطلب MFA عندما تكون مخاطر تسجيل الدخول *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|تأكد من Teams الخدمات التابعة في قائمة التطبيقات. Teams قواعد الوصول إلى الضيوف والوصول الخارجي التي يجب أن تفكر فيها أيضا، ستتعرف على المزيد حول هذه القواعد لاحقا في هذه المقالة.|
||[حظر العملاء الذين لا يدعمون المصادقة الحديثة](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|تضمين Teams والخدمات التابعة في تعيين تطبيقات السحابة.|
||[يجب على المستخدمين المعرضين لمخاطر عالية تغيير كلمة المرور](identity-access-policies.md#high-risk-users-must-change-password)|يجب Teams المستخدمين بتغيير كلمة المرور الخاصة بهم عند تسجيل الدخول إذا تم الكشف عن نشاط عالي المخاطر لحسابهم. تأكد من Teams الخدمات التابعة في قائمة التطبيقات.|
||[تطبيق سياسات حماية بيانات التطبيق](identity-access-policies.md#apply-app-data-protection-policies)|تأكد من Teams الخدمات التابعة في قائمة التطبيقات. تحديث النهج لكل نظام أساسي (iOS وAndroid Windows).|
|**Enterprise**|[تتطلب MFA عندما تكون مخاطر تسجيل الدخول *منخفضة* أو *متوسطة* أو *عالية*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams قواعد الوصول إلى الضيوف والوصول الخارجي التي يجب أن تفكر فيها أيضا، ستتعرف على المزيد حول هذه القواعد لاحقا في هذه المقالة. تضمين Teams والخدمات التابعة في هذا النهج.|
||[تعريف سياسات توافق الأجهزة](identity-access-policies.md#define-device-compliance-policies)|تضمين Teams والخدمات التابعة في هذا النهج.|
||[يتطلب أجهزة كمبيوتر وأجهزة *محمولة* متوافقة](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|تضمين Teams والخدمات التابعة في هذا النهج.|
|**أمان متخصص**|[*طلب* MFA دائما](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|بغض النظر عن هوية المستخدم، سيتم استخدام MFA من قبل مؤسستك. تضمين Teams والخدمات التابعة في هذا النهج. |

## <a name="teams-dependent-services-architecture"></a>Teams التابعة للخدمات

للمرجع، يوضح الرسم التخطيطي التالي الخدمات Teams تعتمد عليها. لمزيد من المعلومات والتوضيحات، راجع Microsoft Teams وخدمات الإنتاجية ذات الصلة [في Microsoft 365 لمهندسي تكنولوجيا المعلومات](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="رسم تخطيطي Teams على SharePoint OneDrive for Business و Exchange." lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>وصول الضيف والخارجي Teams

Microsoft Teams أنواع الوصول التالية:

- **يستخدم وصول** الضيف حساب Azure AD B2B لضيف أو مستخدم خارجي يمكن إضافته كعضو في فريق والحصول على كل حق الوصول إلى اتصالات الفريق وموارده.

- **الوصول الخارجي** للمستخدم الخارجي الذي ليس لديه حساب Azure AD B2B. يمكن أن يتضمن الوصول الخارجي الدعوات والمشاركة في المكالمات والمحادثات والاجتماعات، ولكنه لا يتضمن عضوية الفريق والوصول إلى موارد الفريق.

تنطبق سياسات الوصول الشرطي فقط على وصول الضيف في Teams بسبب وجود حساب Azure AD B2B مقابل.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

للحصول على سياسات مستحسنة للسماح بالوصول للمستخدمين الضيوف والخارجيين الذين لديهم حساب Azure AD B2B، راجع سياسات السماح بالوصول إلى حساب [B2B الخارجي والضيف](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>وصول الضيف في Teams

بالإضافة إلى سياسات المستخدمين الداخليين في شركتك أو مؤسستك، يمكن للمسؤولين تمكين وصول الضيف للسماح للأشخاص من خارج شركتك أو مؤسستك بالوصول إلى موارد Teams والتفاعل مع الأشخاص الداخليين لأشياء مثل المحادثات الجماعية والدردشة والاجتماعات.

لمزيد من المعلومات حول وصول الضيف وكيفية تنفيذه، راجع Teams [وصول الضيف](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>الوصول الخارجي في Teams

في بعض الأحيان، يتم الخلط بين الوصول الخارجي والوصول إلى الضيف، لذلك من المهم أن تكون واضحا أن هاتين الآليتين غير الداخليتين للوصول نوعان مختلفان من الوصول.

الوصول الخارجي هو طريقة Teams المستخدمين من مجال خارجي بأكمله للعثور على الاجتماعات مع المستخدمين والمتصلين بها والدردشة معهم في Teams. Teams يقوم المسؤولون بتكوين الوصول الخارجي على مستوى المؤسسة. لمزيد من المعلومات، راجع [إدارة الوصول الخارجي في Microsoft Teams](/microsoftteams/manage-external-access).

أما مستخدمو الوصول الخارجي، فيقل لديهم إمكانية الوصول والوظائف عن أي شخص تم إضافته عبر وصول الضيف. على سبيل المثال، يمكن لمستخدمي الوصول الخارجي الدردشة مع المستخدمين الداخليين باستخدام Teams ولكن لا يمكنهم الوصول إلى قنوات الفريق أو الملفات أو الموارد الأخرى.

لا يستخدم الوصول الخارجي حسابات مستخدم Azure AD B2B، وبالتالي لا يستخدم سياسات الوصول الشرطي.

## <a name="teams-policies"></a>Teams الجديدة

خارج نطاق السياسات الشائعة المذكورة أعلاه، هناك Teams خاصة يمكن ويجب تكوينها لإدارة وظائف Teams مختلفة.

### <a name="teams-and-channels-policies"></a>Teams والقنوات

Teams والقنوات عنصرين شائعي استخدام في Microsoft Teams، وهناك سياسات يمكنك وضعها للتحكم في ما يمكن للمستخدمين وما لا يمكنهم القيام به عند استخدام الفرق والقنوات. على الرغم من أنه يمكنك إنشاء فريق عام، إذا كانت مؤسستك تملك 5000 مستخدم أو أقل، فمن المرجح أن تجد أنه من المفيد أن يكون لديك فرق وقنوات أصغر لأغراض معينة، بما يتماشى مع احتياجاتك التنظيمية.

من المستحسن تغيير النهج الافتراضي أو إنشاء نهج مخصصة، كما يمكنك معرفة المزيد حول إدارة النهج في هذا الارتباط: إدارة نهج الفرق في [Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>سياسات المراسلة

يمكن أيضا إدارة المراسلة أو الدردشة من خلال النهج العام الافتراضي، أو من خلال النهج المخصصة، وقد يساعد ذلك المستخدمين على التواصل مع الآخرين بطريقة مناسبة لمنظمتك. يمكن مراجعة هذه المعلومات في [إدارة سياسات المراسلة في Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>سياسات الاجتماع

لن تكتمل Teams من دون تخطيط وتنفيذ سياسات حول Teams الاجتماعات. الاجتماعات هي مكون أساسي Teams، مما يسمح للأشخاص بالاجتماعات والعرض رسميا للعديد من المستخدمين في وقت واحد، ومشاركة المحتوى ذي الصلة للاجتماع. من الضروري تعيين السياسات المناسبة لمنظمتك حول الاجتماعات.

لمزيد من المعلومات، راجع [إدارة سياسات الاجتماع في](/microsoftteams/meeting-policies-in-teams) Teams.

### <a name="app-permission-policies"></a>سياسات أذونات التطبيق

Teams أيضا استخدام التطبيقات في أماكن مختلفة، مثل القنوات أو الدردشات الشخصية. من الضروري وجود سياسات حول التطبيقات التي يمكن إضافتها أو استخدامها وأين يجب الحفاظ على بيئة غنية بالمحتوى تكون آمنة أيضا.

لمزيد من القراءة حول "سياسات أذونات التطبيق"، راجع [إدارة](/microsoftteams/teams-app-permission-policies) سياسات أذونات التطبيق في Microsoft Teams.

## <a name="next-steps"></a>الخطوات التالية

![الخطوة 4: سياسات Microsoft 365 السحابية.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

تكوين سياسات الوصول الشرطي ل:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)