---
title: Microsoft 365 نشر الثقة الصفرية
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: تعرف على كيفية نشر Microsoft 365 "الثقة الصفرية" في بيئتك للحماية من التهديدات وحماية البيانات الحساسة.
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
ms.openlocfilehash: 9b37e353af74b7a01c0647f99b149f5fac0ae8a3
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63575931"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Microsoft 365 نشر الثقة الصفرية

توفر هذه المقالة خطة نشر لبناء **أمان "الثقة** الصفرية" Microsoft 365. إن Zero Trust هو نموذج أمان جديد يفترض الخرق ويتحقق من كل طلب كما لو أنه من شبكة غير خاضعة لرقم. بغض النظر عن مصدر الطلب أو المورد الذي يمكن الوصول إليه، يعلمنا نموذج "صفر الثقة" أنه "لا تثق أبدا، تحقق دائما".


## <a name="zero-trust-security-architecture"></a>بنية أمان "الثقة الصفرية"

يمتد نهج "الثقة الصفرية" عبر الممتلكات الرقمية بالكامل، وهو يعمل كفلسفة أمان متكاملة وإستراتيجية شاملة. 

يوفر هذا الرسم التوضيحي تمثيلا للعناصر الأساسية التي تساهم في الثقة الصفرية.

<!---
[![Zero Trust security architecture](../media/zero-trust/zero-trust-architecture.png)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/zero-trust/zero-trust-architecture.png)
-->

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="بنية أمان &quot;الثقة الصفرية&quot;" lightbox="../media/zero-trust/zero-trust-architecture.png":::



في الرسم التوضيحي:
- يوجد تطبيق نهج الأمان في وسط بنية "الثقة الصفرية". يشمل ذلك المصادقة متعددة العوامل مع الوصول الشرطي الذي يأخذ في الاعتبار مخاطر حساب المستخدم، حالة الجهاز، والمعايير والسياسات الأخرى التي تقوم بتعيينها.
- يتم تكوين الهويات والأجهزة والبيانات والتطبيقات والشبكات ومكونات البنية الأساسية الأخرى باستخدام الأمان المناسب. يتم تنسيق النهج التي تم تكوينها لكل مكون من هذه المكونات مع استراتيجية "الثقة الصفرية" الشاملة. على سبيل المثال، تحدد سياسات الأجهزة معايير الأجهزة الصحية وتتطلب سياسات الوصول الشرطي أجهزة سليمة للوصول إلى تطبيقات وبيانات معينة.
- تقوم الحماية من المخاطر وا المعلومات الاستخبارية بمراقبة البيئة، كما تعرض المخاطر الحالية، وتأخذ إجراءات تلقائية من أجل معالجة الهجمات.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype). 
-->

لمزيد من المعلومات حول Zero Trust، راجع مركز إرشادات الثقة [_**الصفرية ل**_](/security/zero-trust) Microsoft.

## <a name="deploying-zero-trust-for-microsoft-365"></a>نشر الثقة الصفرية Microsoft 365

Microsoft 365 عن قصد مع العديد من قدرات حماية المعلومات والأمان لمساعدتك على بناء الثقة الصفرية في بيئتك. يمكن توسيع العديد من الإمكانات لحماية الوصول إلى تطبيقات SaaS الأخرى التي تستخدمها مؤسستك والبيانات ضمن هذه التطبيقات.

يمثل هذا الرسم التوضيحي عمل نشر قدرات الثقة الصفرية. يتم تقسيم هذا العمل إلى وحدات عمل يمكن تكوينها معا، بدءا من الأسفل والعمل إلى الأعلى لضمان اكتمال العمل الأساسي.


:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Microsoft 365 نشر &quot;الثقة الصفرية&quot;" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

في هذا الرسم التوضيحي:
- يبدأ الصفر الثقة بأساس الهوية وحماية الجهاز. 
- لقد تم بناء قدرات الحماية من المخاطر في أعلى هذا الأساس لتوفير المراقبة في الوقت الحقيقي والحماية من التهديدات الأمنية. 
- توفر إدارة وحماية المعلومات عناصر تحكم متطورة تستهدف أنواعا معينة من البيانات لحماية المعلومات الأكثر قيمة وللمساعدة على الامتثال لمعايير التوافق، بما في ذلك حماية المعلومات الشخصية.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>الخطوة 1. تكوين الهوية الصفرية والحماية من الوصول إلى الجهاز — سياسات نقاط البداية

الخطوة الأولى هي إنشاء الأساس "صفر الثقة" من خلال تكوين حماية الوصول إلى الأجهزة والهوية. 


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="تكوين الهوية الصفرية والحماية من الوصول إلى الجهاز" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::



انتقل إلى [**_حماية الوصول_**](office-365-security/microsoft-365-policies-configurations.md) إلى هوية الثقة الصفرية والوصول إلى الجهاز للحصول على إرشادات وصفية لتنفيذ هذا الأمر. تصف هذه السلسلة من المقالات مجموعة من تكوينات المتطلبات الأساسية للوصول إلى الأجهزة والهوية، كما تصف مجموعة من Azure Active Directory (Azure AD) الوصول الشرطي و Microsoft Intune ونهج أخرى لتأمين الوصول إلى Microsoft 365 لتطبيقات وخدمات السحابة الخاصة بالمؤسسة وخدمات SaaS الأخرى والتطبيقات المحلية المنشورة مع وكيل تطبيق Azure AD.



|يتضمن  |المتطلبات الأساسية  |لا يتضمن  |
|---------|---------|---------|
|سياسات الوصول إلى الأجهزة والهوية الموصى بها لثلاثة مستويات من الحماية:<br>- نقطة البداية<br>- Enterprise (مستحسن)<br>- متخصص<br><br>توصيات إضافية ل:<br>- المستخدمون الخارجيون (الضيوف)<br>- Microsoft Teams<br>- SharePoint Online<br>- Microsoft Defender لتطبيقات السحابة| Microsoft E3 أو E5<br><br>Azure Active Directory في أي من هذين الأوضاع:<br>- السحابة فقط<br>- مختلط مع مصادقة مزامنة كلمة المرور (PHS)<br>- مختلط مع مصادقة تمريرية (PTA)<br>- المتحدة     |تسجيل الجهاز لنهج تتطلب أجهزة مدارة. راجع "إدارة نقاط النهاية باستخدام Intune" لتسجيل الأجهزة |
| | | |

ابدأ بتنفيذ مستوى نقطة البداية. لا تتطلب هذه السياسات تسجيل الأجهزة في الإدارة. 


:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="الهوية الصفرية ونهج الوصول إلى الجهاز — مستوى نقطة البداية" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::


## <a name="step-2-manage-endpoints-with-intune"></a>الخطوة 2. إدارة نقاط النهاية باستخدام Intune

بعد ذلك، سجل أجهزتك في الإدارة وابدأ في حماية هذه الأجهزة باستخدام عناصر تحكم أكثر تعقيدا. 

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="إدارة نقاط النهاية باستخدام Intune" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::


انتقل إلى [**_إدارة الأجهزة باستخدام Intune_**](../solutions/manage-devices-with-intune-overview.md) للحصول على إرشادات وصفية لتنفيذ ذلك. 


|يتضمن  |المتطلبات الأساسية  |لا يتضمن  |
|---------|---------|---------|
|تسجيل الأجهزة باستخدام Intune<br>- الأجهزة المملوكة للشركات<br>- Autopilot/automated<br>- التسجيل<br><br>تكوين السياسات<br>- سياسات حماية التطبيق<br>- سياسات التوافق<br>- سياسات ملف تعريف الجهاز | تسجيل نقاط النهاية باستخدام Azure AD     | تكوين قدرات حماية المعلومات، بما في ذلك:<br>- أنواع المعلومات الحساسة<br>- التسميات<br>- سياسات DLP<br>للحصول على هذه الإمكانات، راجع الخطوة 5. حماية البيانات وتحكمها (لاحقا في هذه المقالة).       |
|    |         |         |

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>الخطوة 3. إضافة حماية الوصول إلى الأجهزة وهوية الثقة الصفرية — سياسات المؤسسة

باستخدام الأجهزة التي تم تسجيلها في الإدارة، يمكنك الآن تنفيذ مجموعة كاملة من سياسات الوصول إلى الأجهزة وهوية الصفر الموصى بها والتي تتطلب أجهزة متوافقة.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="عدم الثقة في الهوية ونهج الوصول باستخدام إدارة الأجهزة" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

قم بالعودة [**_إلى سياسات الوصول إلى_**](office-365-security/identity-access-policies.md) الأجهزة والهوية الشائعة وأضف النهج في مستوى المؤسسة.  

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="الهوية الصفرية ونهج الوصول — مستوى المؤسسة (مستحسن)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>الخطوة 4. تقييم وتقييم ونشر Microsoft 365 Defender

Microsoft 365 Defender هو حل موسع للكشف والاستجابة (XDR) يقوم تلقائيا بتجميع بيانات الإشارة والتهديدات والتنبيهات من بيئة Microsoft 365، بما في ذلك نقطة النهاية والبريد الإلكتروني والتطبيقات والهويات وربطها وتحليلها.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="إضافة Microsoft 365 Defender إلى بنية &quot;الثقة الصفرية&quot;" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

انتقل إلى [**_تقييم Microsoft 365 Defender_**](defender/eval-overview.md) تجريبية للحصول على دليل أسلوبي لتدليل Microsoft 365 Defender ونشرها. 

|يتضمن  |المتطلبات الأساسية  |لا يتضمن  |
|---------|---------|---------|
| إعداد التقييم وبيئة التجربة لكل المكونات:<br>- Defender for Identity<br>- Defender for Office 365<br>- Defender لنقطة النهاية<br>- Microsoft Defender لتطبيقات السحابة<br><br>الحماية من التهديدات<br><br> التحقق من التهديدات والاستجابة لها   | راجع الإرشادات التي يجب قراءتها حول متطلبات البنية لكل مكون من مكونات Microsoft 365 Defender.        | لا يتم تضمين Azure AD Identity Protection في دليل الحل هذا. يتم تضمينه في الخطوة 1: تكوين هوية صفرية الثقة وحماية الوصول إلى الجهاز.        |
|    |         |         |

## <a name="step-5-protect-and-govern-sensitive-data"></a>الخطوة 5. حماية البيانات الحساسة وتحكمها

يمكنك حماية البيانات في Microsoft (MIP) لمساعدتك على اكتشاف المعلومات الحساسة وتصنيفها وحمايتها أينما كانت أو تتنقل.

يتم تضمين قدرات MIP مع Microsoft 365 والتوافق، كما تمنحك الأدوات اللازمة لمعرفة بياناتك، وحماية البيانات، ومنع فقدان البيانات.


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="قدرات حماية المعلومات تحمي البيانات من خلال تطبيق النهج" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

بينما يتم تمثيل هذا العمل في أعلى مكدس النشر الموضح سابقا في هذه المقالة، يمكنك بدء هذا العمل في أي وقت. 

حماية البيانات في Microsoft إطار عمل وعملية وإمكانيات يمكنك استخدامها لتحقيق أهداف أعمالك المحددة.

![حماية البيانات في Microsoft (MIP)](../media/zero-trust/mip-solution-overview.png)

لمزيد من المعلومات حول كيفية التخطيط لحماية المعلومات ونشرها، راجع [**_نشر حل حماية البيانات في Microsoft._**](../compliance/information-protection-solution.md) 

إذا كنت تقوم بنشر حماية المعلومات لأنظمة خصوصية البيانات، فإن دليل الحل هذا يوفر إطار عمل مستحسنا للعملية [**_بأكملها_**](../solutions/information-protection-deploy.md): نشر حماية المعلومات لأنظمة خصوصية البيانات مع Microsoft 365.