---
title: خطة نشر الثقة المعدومة من Microsoft 365
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: تعرف على كيفية نشر الأمان Microsoft 365 ثقة معدومة في بيئتك للدفاع ضد التهديدات وحماية البيانات الحساسة.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: 4056310eb8e0d22a9758dfa2a572a473c83a0775
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669727"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>خطة نشر الثقة المعدومة من Microsoft 365

توفر هذه المقالة خطة نشر لبناء أمان **ثقة معدومة** باستخدام Microsoft 365. ثقة معدومة هو نموذج أمان جديد يفترض الخرق ويتحقق من كل طلب كما لو كان ينشأ من شبكة غير خاضعة للرقابة. بغض النظر عن مكان إنشاء الطلب أو المورد الذي يصل إليه، يعلمنا نموذج ثقة معدومة "عدم الثقة أبدا، التحقق دائما".

استخدم هذه المقالة مع هذا الملصق.

| البند | الوصف |
|:-----|:-----|
|[![رسم توضيحي لخطة نشر Microsoft 365 ثقة معدومة.](../media/solutions-architecture-center/m365-zero-trust-deployment-plan-thumb.png) ](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) <br/> [PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) \| [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx) <br/> محدث في مارس 2022 | **إرشادات الحلول ذات الصلة** <br/> <ul><li>[نشر البنية الأساسية لهويتك Microsoft 365](/microsoft-365/enterprise/deploy-identity-solution-overview)</li><li>[تكوينات الهوية والوصول إلى الجهاز الموصى بها](../security/office-365-security/microsoft-365-policies-configurations.md)</li><li>[إدارة الأجهزة باستخدام Intune](../solutions/manage-devices-with-intune-overview.md)</li><li>[تقييم Microsoft 365 Defender وإعداد إصدار تجريبي منه](../security/defender/eval-overview.md)</li><li>[نشر حل حماية المعلومات باستخدام Microsoft Purview](../compliance/information-protection-solution.md)</li><li>[نشر حماية المعلومات للوائح خصوصية البيانات باستخدام Microsoft 365](../solutions/information-protection-deploy.md)</li></ul>

## <a name="zero-trust-security-architecture"></a>ثقة معدومة بنية الأمان

يمتد النهج ثقة معدومة في جميع أنحاء الملكية الرقمية بأكملها ويعمل كفلسفة أمان متكاملة واستراتيجية من طرف إلى طرف.

يوفر هذا الرسم التوضيحي تمثيلا للعناصر الأساسية التي تساهم في ثقة معدومة.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="بنية الأمان ثقة معدومة" lightbox="../media/zero-trust/zero-trust-architecture.png":::

في الرسم التوضيحي:

- تطبيق نهج الأمان هو في وسط بنية ثقة معدومة. يتضمن ذلك المصادقة متعددة العوامل مع الوصول المشروط الذي يأخذ في الاعتبار مخاطر حساب المستخدم وحالة الجهاز والمعايير والنهج الأخرى التي قمت بتعيينها.
- يتم تكوين جميع الهويات والأجهزة والبيانات والتطبيقات والشبكة ومكونات البنية الأساسية الأخرى مع الأمان المناسب. يتم تنسيق النهج التي تم تكوينها لكل من هذه المكونات مع استراتيجية ثقة معدومة الشاملة. على سبيل المثال، تحدد نهج الأجهزة معايير الأجهزة السليمة وتتطلب نهج الوصول المشروط أجهزة سليمة للوصول إلى تطبيقات وبيانات معينة.
- تراقب الحماية من التهديدات والذكاء البيئة، وتعرض المخاطر الحالية، وتتخذ إجراءات تلقائية لمعالجة الهجمات.

لمزيد من المعلومات حول ثقة معدومة، راجع [_**مركز إرشادات ثقة معدومة**_](/security/zero-trust) من Microsoft.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype).
-->



## <a name="deploying-zero-trust-for-microsoft-365"></a>نشر ثقة معدومة Microsoft 365

يتم بناء Microsoft 365 عن قصد مع العديد من قدرات الأمان وحماية المعلومات لمساعدتك على بناء ثقة معدومة في بيئتك. يمكن توسيع العديد من القدرات لحماية الوصول إلى تطبيقات SaaS الأخرى التي تستخدمها مؤسستك والبيانات داخل هذه التطبيقات.

يمثل هذا الرسم التوضيحي عمل نشر قدرات ثقة معدومة. يتم تقسيم هذا العمل إلى وحدات عمل يمكن تكوينها معا، بدءا من الأسفل والعمل إلى الأعلى لضمان اكتمال عمل المتطلبات الأساسية.

:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="مكدس نشر Microsoft 365 ثقة معدومة" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

في هذا الرسم التوضيحي:

- يبدأ ثقة معدومة بأساس الهوية وحماية الجهاز.
- تستند قدرات الحماية من التهديدات إلى جانب هذا الأساس لتوفير مراقبة ومعالجة التهديدات الأمنية في الوقت الحقيقي.
- توفر حماية المعلومات والحوكمة ضوابط متطورة تستهدف أنواعا معينة من البيانات لحماية معلوماتك الأكثر قيمة ولمساعدتك على الامتثال لمعايير الامتثال، بما في ذلك حماية المعلومات الشخصية.


تفترض هذه المقالة أنك قمت بالفعل بتكوين هوية السحابة. إذا كنت بحاجة إلى إرشادات لهذا الهدف، فراجع [**نشر البنية الأساسية لهويتك Microsoft 365**](/microsoft-365/enterprise/deploy-identity-solution-overview).

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>الخطوة 1. تكوين الهوية ثقة معدومة وحماية الوصول إلى الجهاز — نهج نقطة البداية

الخطوة الأولى هي بناء أساس ثقة معدومة الخاص بك عن طريق تكوين الهوية وحماية الوصول إلى الجهاز.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="عملية تكوين الهوية ثقة معدومة وحماية الوصول إلى الجهاز" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::

انتقل إلى [**_ثقة معدومة حماية الهوية والوصول إلى الجهاز_**](office-365-security/microsoft-365-policies-configurations.md) للحصول على إرشادات توجيهية لإنجاز ذلك. تصف هذه السلسلة من المقالات مجموعة من تكوينات المتطلبات الأساسية للوصول إلى الهوية والجهاز ومجموعة من الوصول المشروط ل Azure Active Directory (Azure AD) Microsoft Intune ونهج أخرى لتأمين الوصول إلى Microsoft 365 لتطبيقات وخدمات سحابة المؤسسة وخدمات SaaS الأخرى والتطبيقات المحلية المنشورة مع وكيل تطبيق Azure AD.

|يتضمن|المتطلبات الأساسية|لا يتضمن|
|---------|---------|---------|
|نهج الهوية والوصول إلى الأجهزة الموصى بها لثلاثة مستويات من الحماية: <ul><li>نقطة البداية</li><li>Enterprise (مستحسن)</li><li>المتخصصه</li></ul> <br> توصيات إضافية ل: <ul><li>المستخدمون الخارجيون (الضيوف)</li><li>Microsoft Teams</li><li>SharePoint Online</li><li>Microsoft Defender for Cloud Apps</lu></ul>|Microsoft E3 أو E5 <br><br> Azure Active Directory في أي من هذين الوضعين: <ul><li>السحابة فقط</li><li>مختلط مع مصادقة مزامنة تجزئة كلمة المرور (PHS)</li><li>مختلط مع مصادقة المرور (PTA)</li><li>الاتحاديه</li></ul>|تسجيل الجهاز للنهج التي تتطلب أجهزة مدارة. راجع [الخطوة 2. إدارة نقاط النهاية باستخدام Intune](#step-2-manage-endpoints-with-intune) لتسجيل الأجهزة|

ابدأ بتنفيذ مستوى نقطة البداية. لا تتطلب هذه النهج تسجيل الأجهزة في الإدارة.

:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="نهج الهوية ثقة معدومة والوصول إلى الجهاز — مستوى نقطة البداية" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::

## <a name="step-2-manage-endpoints-with-intune"></a>الخطوة 2. إدارة نقاط النهاية باستخدام Intune

بعد ذلك، قم بتسجيل أجهزتك في الإدارة وابدأ في حمايتها باستخدام عناصر تحكم أكثر تعقيدا.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="إدارة نقاط النهاية باستخدام عنصر Intune" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::

انتقل إلى [**_إدارة الأجهزة باستخدام Intune_**](../solutions/manage-devices-with-intune-overview.md) للحصول على إرشادات توجيهية لإنجاز ذلك.

|يتضمن|المتطلبات الأساسية|لا يتضمن|
|---------|---------|---------|
|تسجيل الأجهزة باستخدام Intune: <ul><li>الأجهزة المملوكة للشركات</li><li>Autopilot/automated</li><li>التسجيل</li></ul> <br> تكوين النهج: <ul><li>نهج حماية التطبيقات</li><li>نهج التوافق</li><li>نهج ملف تعريف الجهاز</li></ul>|تسجيل نقاط النهاية باستخدام Azure AD|تكوين قدرات حماية المعلومات، بما في ذلك: <ul><li>أنواع المعلومات الحساسة</li><li>تسميات</li><li>نهج DLP</li></ul> <br> للحصول على هذه الإمكانات، راجع [الخطوة 5. حماية البيانات الحساسة وإدارتها](#step-5-protect-and-govern-sensitive-data) (لاحقا في هذه المقالة).|

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>الخطوة 3. إضافة هوية ثقة معدومة وحماية الوصول إلى الجهاز — نهج المؤسسة

مع الأجهزة المسجلة في الإدارة، يمكنك الآن تنفيذ المجموعة الكاملة من نهج الهوية ثقة معدومة والوصول إلى الأجهزة الموصى بها، والتي تتطلب أجهزة متوافقة.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="نهج الهوية والوصول ثقة معدومة مع إدارة الجهاز" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

ارجع إلى [**_نهج الوصول إلى الهوية والجهاز الشائعة_**](office-365-security/identity-access-policies.md) وأضف النهج في مستوى Enterprise.

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="نهج الهوية والوصول ثقة معدومة — مستوى Enterprise (مستحسن)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>الخطوة 4. تقييم Microsoft 365 Defender وتجربتها ونشرها

Microsoft 365 Defender هو حل موسع للكشف والاستجابة (XDR) يجمع بيانات الإشارة والتهديدات والتنبيهات تلقائيا ويربطها ويحللها عبر بيئة Microsoft 365، بما في ذلك نقطة النهاية والبريد الإلكتروني والتطبيقات والهويات.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="عملية إضافة Microsoft 365 Defender إلى بنية ثقة معدومة" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

انتقل إلى [**_تقييم Microsoft 365 Defender وتجربتها_**](defender/eval-overview.md) للحصول على دليل أسلوبي للبدء التجريبي وتوزيع مكونات Microsoft 365 Defender.

|يتضمن|المتطلبات الأساسية|لا يتضمن|
|---------|---------|---------|
|إعداد بيئة التقييم والإصدار التجريبي لجميع المكونات: <ul><li>Defender for Identity</li><li>Defender for Office 365</li><li>Defender لنقطة النهاية</li><li>Microsoft Defender for Cloud Apps</li></ul> <br> الحماية من التهديدات <br><br> التحقق من التهديدات والاستجابة لها|راجع الإرشادات لقراءة متطلبات البنية لكل مكون من مكونات Microsoft 365 Defender.| Azure AD Identity Protection غير مضمن في دليل الحل هذا. وهي مضمنة في [الخطوة 1. تكوين الهوية ثقة معدومة وحماية الوصول إلى الجهاز](#step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies).|

## <a name="step-5-protect-and-govern-sensitive-data"></a>الخطوة 5. حماية البيانات الحساسة وإدارتها

تنفيذ حماية البيانات في Microsoft Purview لمساعدتك على اكتشاف المعلومات الحساسة وتصنيفها وحمايتها أينما كانت تعيش أو تنتقل.

يتم تضمين قدرات حماية البيانات في Microsoft Purview مع Microsoft Purview وتعطيك الأدوات اللازمة لمعرفة بياناتك وحماية بياناتك ومنع فقدان البيانات.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="قدرات حماية المعلومات التي تحمي البيانات من خلال إنفاذ النهج" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

بينما يتم تمثيل هذا العمل في أعلى مكدس النشر الموضح سابقا في هذه المقالة، يمكنك بدء هذا العمل في أي وقت.

يوفر حماية البيانات في Microsoft Purview إطار عمل وعملية وقدرات يمكنك استخدامها لتحقيق أهداف عملك المحددة.

![حماية البيانات في Microsoft Purview](../media/zero-trust/mip-solution-overview.png)

لمزيد من المعلومات حول كيفية تخطيط حماية المعلومات ونشرها، راجع [**_نشر حل حماية البيانات في Microsoft Purview_**](../compliance/information-protection-solution.md). 

إذا كنت تنشر حماية المعلومات للوائح خصوصية البيانات، فإن دليل الحل هذا يوفر إطار عمل موصى به للعملية بأكملها: [**_نشر حماية المعلومات للوائح خصوصية البيانات باستخدام Microsoft 365_**](../solutions/information-protection-deploy.md).
