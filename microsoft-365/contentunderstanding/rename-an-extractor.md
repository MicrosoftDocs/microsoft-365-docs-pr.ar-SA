---
title: إعادة تسمية مستخرج في Microsoft SharePoint Syntex
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
description: تعرف على كيفية إعادة تسمية مستخرج في Microsoft SharePoint Syntex ولماذا.
ms.openlocfilehash: feba0d8850a534e7f5e5d985bf3424f931e0ceb0
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916150"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>إعادة تسمية مستخرج في Microsoft SharePoint Syntex

في مرحلة ما، قد تحتاج إلى إعادة تسمية مستخرج إذا كنت تريد الإشارة إلى حقل بيانات مستخرجة باسم مختلف. على سبيل المثال، تقرر مؤسستك إجراء تغييرات على مستندات العقود الخاصة بها، وتشير إلى "العملاء" ك "عملاء" في مستنداتهم. إذا كنت تقوم باستخراج حقل "العميل" في النموذج الخاص بك، يمكنك اختيار إعادة تسميته إلى "العميل".

عند مزامنة النموذج المحدث إلى مكتبة مستندات SharePoint، سترى عمود "عميل" جديدا في طريقة عرض مكتبة المستندات. ستحتفظ طريقة العرض الخاصة بك بعمود "العميل" للنشاط السابق، ولكن سيتم تحديث عمود "العميل" الجديد لكافة المستندات الجديدة التي تتم معالجتها بواسطة النموذج الخاص بك. 

> [!IMPORTANT]
>  تأكد من مزامنة النموذج المحدث إلى مكتبات المستندات حيث قمت بتطبيقه مسبقا لعرض اسم العمود الجديد. 

## <a name="rename-an-extractor"></a>إعادة تسمية مستخرج

اتبع هذه الخطوات لإعادة تسمية مستخرج كيان.

1. من مركز المحتوى، حدد **"النماذج** " لمشاهدة قائمة النماذج الخاصة بك.

2. في صفحة **النماذج** ، في عمود **"الاسم** "، حدد النموذج الذي تريد إعادة تسمية مستخرج له.

3. ضمن **مستخرجات الوحدة**، حدد اسم المستخرج الذي تريد إعادة تسميته، ثم حدد **"إعادة تسمية".**

    ![لقطة شاشة لقسم مستخرجات الوحدة تعرض مستخرجا محددا مع تمييز خيار إعادة التسمية.](../media/content-understanding/entity-extractor-rename.png) 

4. في لوحة **مستخرج كيان إعادة التسمية** :

   أ. ضمن **اسم جديد**، أدخل الاسم الجديد للمستخرج.

    ![Screenshot showing the Entity extractor panel.](../media/content-understanding/rename-entity-extractor-panel.png) 

   ب. (اختياري) ضمن **الإعدادات المتقدمة**، حدد ما إذا كنت تريد إقران عمود موقع موجود.

5. حدد **إعادة تسمية**.

## <a name="see-also"></a>راجع أيضًا
[إنشاء مستخرج](create-an-extractor.md)

[إنشاء مصنف](create-a-classifier.md)

[إعادة تسمية نموذج](rename-a-model.md)

[أنواع التفسيرات](explanation-types-overview.md)

[الاستفادة من تصنيف مخزن المصطلحات عند إنشاء مستخرج](leverage-term-store-taxonomy.md)

[نظرة عامة على فهم المستند](document-understanding-overview.md)

[تطبيق نموذج](apply-a-model.md) 
