---
title: تكرار نموذج في Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
audience: admin
ms.reviewer: ssquires
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: تعرف على كيفية تكرار نموذج فهم المستند في Microsoft SharePoint Syntex وسبب تكراره.
ms.openlocfilehash: 56e05389cad4ad9010324a3efd48bf679700be76
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882231"
---
# <a name="duplicate-a-model-in-microsoft-sharepoint-syntex"></a>تكرار نموذج في Microsoft SharePoint Syntex

يمكن أن يوفر تكرار نموذج فهم المستند الوقت والجهد إذا كنت بحاجة إلى إنشاء نموذج جديد، ومعرفة أن النموذج الموجود مشابه جدا لما تحتاجه.

على سبيل المثال، يصنف نموذج موجود يسمى "العقود" الملفات نفسها التي تحتاج إلى العمل معها. سيقوم نموذجك الجديد باستخراج بعض البيانات الموجودة، ولكن ستحتاج إلى تحديث لاستخراج بعض البيانات الإضافية. بدلا من إنشاء نموذج جديد وتدريبه من البداية، يمكنك استخدام ميزة النموذج المكرر لإنشاء نسخة من نموذج العقود، والتي ستنسخ أيضا جميع عناصر التدريب المرتبطة، مثل الملفات النموذجية ومستخرجات الكيانات.

عند تكرار النموذج، بعد إعادة تسميته (على سبيل المثال، إلى "تجديدات العقد")، يمكنك بعد ذلك إجراء تحديثات عليه. على سبيل المثال، يمكنك اختيار إزالة بعض الحقول المستخرجة الموجودة التي لا تحتاج إليها، ثم تدريب النموذج على استخراج حقل جديد (على سبيل المثال، "تاريخ التجديد").

## <a name="duplicate-a-model"></a>تكرار نموذج

اتبع هذه الخطوات لتكرار نموذج فهم المستند.

1. من مركز المحتوى، حدد **"النماذج** " لمشاهدة قائمة النماذج الخاصة بك.

2. في صفحة **النماذج** ، حدد النموذج الذي تريد تكراره.

3. باستخدام الشريط أو الزر **"إظهار الإجراءات** " (بجوار اسم النموذج)، حدد **"تكرار**".</br>

    ![لقطة شاشة لصفحة «Models» تعرض نموذجا محددا مع تمييز «Duplicate options».](../media/content-understanding/select-model-duplicate-both.png) </br>

4. في لوحة **النموذج المكرر** :

   أ. ضمن **الاسم**، أدخل الاسم الجديد للنموذج الذي تريد تكراره.</br>

    ![Screenshot showing the Duplicate model panel.](../media/content-understanding/duplicate-model-panel.png) </br>

   ب. ضمن **الوصف**، أضف وصفا للنموذج الجديد.

   c. (اختياري) ضمن **الإعدادات المتقدمة**، حدد ما إذا كنت تريد إقران [نوع محتوى](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview) موجود.

5. حدد **"تكرار**".

## <a name="see-also"></a>راجع أيضًا

[إنشاء مصنف](create-a-classifier.md)

[إعادة تسمية نموذج](rename-a-model.md)

[إنشاء مستخرج](create-an-extractor.md)

[نظرة عامة على فهم المستند](document-understanding-overview.md)

[أنواع التفسيرات](explanation-types-overview.md)

[تطبيق نموذج](apply-a-model.md) 

[SharePoint Syntex وضع إمكانية وصول ذوي الاحتياجات الخاصة](accessibility-mode.md)