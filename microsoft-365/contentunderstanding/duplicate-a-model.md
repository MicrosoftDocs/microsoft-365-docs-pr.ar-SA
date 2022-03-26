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
description: تعرف على كيفية تكرار نموذج فهم المستند في Microsoft SharePoint Syntex.
ms.openlocfilehash: 979d5b2cddfa7c565abade7ac66c06e3053bbe4d
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/10/2022
ms.locfileid: "63570214"
---
# <a name="duplicate-a-model-in-microsoft-sharepoint-syntex"></a>تكرار نموذج في Microsoft SharePoint Syntex

يمكن أن يوفر لك تكرار نموذج فهم المستند الوقت والجهد إذا كنت بحاجة إلى إنشاء نموذج جديد، وتعرف أن النموذج الموجود يشبه إلى حد كبير ما تحتاج إليه.

على سبيل المثال، يصنف نموذج موجود يسمى "العقود" الملفات نفسها التي تحتاج إلى العمل عليها. سيستخرج النموذج الجديد بعض البيانات الموجودة، ولكن يجب تحديثه لاستخراج بعض البيانات الإضافية. بدلا من إنشاء نموذج جديد والتدريب عليه من البداية، يمكنك استخدام ميزة النموذج المكرر لإنشاء نسخة من نموذج العقود، الذي ينسخ أيضا كل عناصر التدريب المقترنة، مثل الملفات ومستخرجات الكيانات على سبيل المثال.

عند تكرار النموذج، بعد إعادة تسميته (على سبيل المثال، إلى "تجديد العقد")، يمكنك بعد ذلك إجراء تحديثات عليه. على سبيل المثال، يمكنك اختيار إزالة بعض الحقول المستخرجة الموجودة التي لا تحتاج إليها، ثم تدريب النموذج لاستخراج حقل جديد (على سبيل المثال، "تاريخ التجديد").

## <a name="duplicate-a-model"></a>تكرار نموذج

اتبع هذه الخطوات لتكرار نموذج فهم المستند.

1. من مركز المحتوى، حدد **نماذج** لمشاهدة قائمة النماذج.

2. في صفحة **النماذج** ، حدد النموذج الذي تريد تكراره.

3. باستخدام الشريط أو الزر **إظهار الإجراءات** (إلى جانب اسم النموذج)، حدد **تكرار**.</br>

    ![لقطة شاشة لصفحة "النماذج" تعرض نموذجا محددا مع تمييز الخيارات "تكرار".](../media/content-understanding/select-model-duplicate-both.png) </br>

4. في لوحة **النموذج المكرر** :

   أ. ضمن **الاسم**، أدخل الاسم الجديد للنموذج الذي تريد تكراره.</br>

    ![لقطة شاشة تعرض لوحة النموذج المكرر.](../media/content-understanding/duplicate-model-panel.png) </br>

   ب. ضمن **الوصف**، أضف وصفا للنموذج الجديد.

   c. (اختياري) ضمن **إعدادات متقدمة**، حدد ما إذا كنت تريد إقران نوع محتوى [موجود](/sharepoint/governance/content-type-and-workflow-planning#content-type-overview).

5. حدد **تكرار**.

## <a name="see-also"></a>انظر أيضاً
[إنشاء تصنيف](create-a-classifier.md)

[إعادة تسمية نموذج](rename-a-model.md)

[إنشاء مستخرج](create-an-extractor.md)

[نظرة عامة حول فهم المستند](document-understanding-overview.md)

[أنواع الشرح](explanation-types-overview.md)

[تطبيق نموذج](apply-a-model.md) 

[SharePoint Syntex وضع إمكانية وصول ذوي الاحتياجات الخاصة](accessibility-mode.md)