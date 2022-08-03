---
title: متطلبات البنية الأساسية الرئيسية قبل التسجيل في خدمة Microsoft Defender Experts for Hunting
ms.reviewer: ''
description: يوضح هذا القسم متطلبات البنية الأساسية الرئيسية التي يجب عليك تلبيتها والمعلومات المهمة حول الوصول إلى البيانات والامتثال
keywords: خدمة تتبع التهديدات المدارة، والتتبع المدار للمخاطر، وخدمة الكشف والاستجابة المدارة (MDR)، وMTE، خبراء المخاطر في Microsoft، وMTE-TAN، وإخطار خبراء defender، وإخطار الهجوم المستهدف، وخبراء Microsoft Defender للتتبع، وتتبع التهديدات وتحليلها.
search.product: Windows 10
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f686777e32aac9bea4a9d45d365ff977bf0fb357
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67171638"
---
# <a name="before-you-begin-using-defender-experts-for-hunting"></a>قبل البدء في استخدام Defender Experts للتتبع

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

يوضح هذا المستند متطلبات البنية الأساسية الرئيسية التي يجب عليك تلبيتها ومعلومات هامة حول الوصول إلى البيانات والامتثال الذي يجب معرفته قبل التسجيل في خدمة Microsoft Defender Experts for Hunting. تدرك Microsoft أن العملاء الذين يستخدمون خدماتنا المدارة يسندون إلينا أصولهم الأكثر قيمة وبياناتهم.

## <a name="check-if-your-environment-meets-licensing-and-access-prerequisites"></a>التحقق مما إذا كانت بيئتك تفي بالمتطلبات الأساسية للترخيص والوصول

Microsoft Defender Experts for Hunting هي خدمة منفصلة عن منتجات Defender الموجودة لديك. قبل التسجيل في هذه الخدمة، تأكد من أن لديك الترخيص والوصول اللازمين. 

### <a name="eligibility-and-licensing"></a>الأهلية والترخيص

سيتم تعيين اثنين من خبراء Defender Experts لعملاء التتبع إلى اثنين من أرصدة الطلب في الأول من كل شهر، والتي يمكن استخدامها لإرسال الأسئلة. تنتهي صلاحية الرصيد غير المستخدم لمدة 90 يوما من تاريخ التعيين أو في نهاية مدة الاشتراك، أيهما أقصر.

لمزيد من المعلومات حول شروط الترخيص التجاري لشركة Microsoft، تفضل بزيارة [هذه الصفحة](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).

### <a name="access-requirements"></a>متطلبات الوصول

يمكن لأي شخص من مؤسستك إكمال نموذج اهتمام العملاء لخدمة Microsoft Defender Experts for Hunting، ومع ذلك، تحتاج إلى العمل مع مديرك التنفيذي التجاري لمعالجة SKU. قد تحتاج إلى أدوار وأذونات معينة للوصول الكامل إلى قدرات الخدمة. راجع [الأدوار المخصصة في التحكم في الوصول استنادا إلى الدور للحصول على Microsoft 365 Defender](custom-roles.md) للحصول على التفاصيل.

## <a name="understand-the-services-availability-and-data-access-requirements"></a>فهم متطلبات توفر الخدمة والوصول إلى البيانات

Defender Experts for Hunting هي خدمة تتبع المخاطر المدارة التي تبحث بشكل استباقي عن التهديدات عبر نقاط النهاية والبريد الإلكتروني والهوية وتطبيقات السحابة. لتنفيذ التتبع نيابة عنك، يحتاج خبراء Microsoft إلى الوصول إلى بيانات التتبع المتقدمة Microsoft 365 Defender. يعني التسجيل في هذه الخدمة أنك تمنح إذنا لخبراء Microsoft للوصول إلى البيانات المذكورة.

تقوم الأقسام التالية بتعداد معلومات إضافية حول استخدام بيانات الخدمة وتوافقها وتوفرها. لمزيد من المعلومات حول التزام Microsoft بتقييم بياناتك وحمايتها، تفضل بزيارة [مركز التوثيق](https://aka.ms/trustcenter-dex4hunting) > التمرير لأسفل وصولا إلى **خدمات** > **الأمان المدارة** الإضافية من  > [**Microsoft Defender Expert for Hunting**](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE51fRH).

### <a name="data-collection-usage-and-retention"></a>تجميع البيانات واستخدامها واستبقاءها

ستستمر جميع البيانات المستخدمة للتتبع من خدمات Defender الموجودة في موقع تخزين خدمة Microsoft 365 Defender الأصلي للعميل. [معرفة المزيد](../../enterprise/o365-data-locations.md)

يتم إنشاء وتخزين بيانات Defender Experts for Hunting التشغيلية، مثل تذاكر الحالة وملاحظات المحللين، في مركز بيانات Microsoft في منطقة الولايات المتحدة لطول الخدمة، بغض النظر عن موقع تخزين الخدمة Microsoft 365 Defender. يتم تخزين البيانات التي تم إنشاؤها للوحة معلومات التقارير في موقع تخزين خدمة Microsoft 365 Defender العميل. سيتم الاحتفاظ ببيانات التقارير والبيانات التشغيلية لفترة سماح لا تقل عن 90 يوما بعد مغادرة العميل للخدمة.

يتتبع خبراء Microsoft [سجلات التتبع المتقدمة](../../security/defender/advanced-hunting-schema-tables.md) في Microsoft 365 Defender جداول التتبع المتقدمة. تعتمد البيانات الموجودة في هذه الجداول على مجموعة خدمات Defender التي يتم تمكين العميل لها (على سبيل المثال، Microsoft Defender لنقطة النهاية، Microsoft Defender لـ Office 365، Microsoft Defender for Identity، Microsoft Defender for Cloud Apps وAzure Active Directory). يستخدم الخبراء أيضا مجموعة كبيرة من بيانات التحليل الذكي للمخاطر الداخلية لإعلامهم بالتتبع والتشغيل الآلي.

### <a name="security-and-compliance"></a>الأمان والتوافق

عند الشراء والإلحاق ب Defender Experts for Hunting، فإنك تمنح إذنا لخبراء Microsoft للوصول إلى بيانات التتبع المتقدمة.

تم تطوير هذه الخدمة بما يتماشى مع معايير الأمان والخصوصية الحالية وتعمل على الحصول على العديد من الشهادات، بما في ذلك ISO 27001 و ISO 27018.

### <a name="availability"></a>التوفر

تتوفر هذه الخدمة في جميع أنحاء العالم للعملاء في سحبنا العامة التجارية. وهي غير متوفرة حاليا للعملاء في السحب الحكومية والسياادية.

### <a name="languages"></a>اللغات

يتم تقديم هذه الخدمة حاليا باللغة الإنجليزية فقط.

## <a name="apply-for-microsoft-defender-experts-for-hunting-service"></a>التقدم بطلب للحصول على خدمة Microsoft Defender Experts for Hunting

إذا لم تكن قد فعلت ذلك بعد، يمكنك إكمال نموذج اهتمام العملاء ل Defender Experts for Hunting:

1. أكمل نموذج فائدة العميل. يمكن لأي شخص من شركتك التقدم بطلب، ولكن إذا تم قبولك، فأنت بحاجة إلى العمل مع المدير التنفيذي التجاري الخاص بك لمعالجة SKU.
2. أدخل معرف البريد الإلكتروني للشركة.
3. حدد **"إرسال**". سيتواصل شخص ما من فريق المبيعات لدينا في غضون خمسة أيام عمل.


### <a name="next-step"></a>الخطوة التالية

- [بدء استخدام Defender Experts for Hunting](onboarding-defender-experts-for-hunting.md)
