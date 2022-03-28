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
description: تعرف على كيفية إعادة تسمية مستخرج في Microsoft SharePoint Syntex.
ms.openlocfilehash: 850359f71e7ca08b16265f93741ab2498e87d032
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63575452"
---
# <a name="rename-an-extractor-in-microsoft-sharepoint-syntex"></a>إعادة تسمية مستخرج في Microsoft SharePoint Syntex

في مرحلة معينة، قد تحتاج إلى إعادة تسمية مستخرج إذا كنت تريد الإشارة إلى حقل بيانات مستخرج باسم مختلف. على سبيل المثال، تقرر مؤسستك إجراء تغييرات على مستندات العقود، وتشير إلى "العملاء" ك "عملاء" في مستنداتهم. إذا كنت تستخرج حقل "عميل" في النموذج، يمكنك اختيار إعادة تسميته إلى "عميل".

عند مزامنة النموذج المحدث إلى SharePoint المستندات، سترى عمود "عميل" جديدا في طريقة عرض مكتبة المستندات. ستحتفظ طريقة العرض الخاصة بك العمود "العميل" للنشاط السابق، ولكن سيتم تحديث العمود الجديد "العميل" لجميع المستندات الجديدة التي تتم معالجتها بواسطة النموذج الخاص بك. 

> [!IMPORTANT]
>  تأكد من مزامنة النموذج المحدث إلى مكتبات المستندات حيث سبق لك تطبيقه لعرض اسم العمود الجديد. 

## <a name="rename-an-extractor"></a>إعادة تسمية مستخرج

اتبع هذه الخطوات لإعادة تسمية مستخرج كيان.

1. من مركز المحتوى، حدد **نماذج** لمشاهدة قائمة النماذج.

2. في الصفحة **نماذج** ، في العمود **الاسم** ، حدد النموذج الذي تريد إعادة تسمية مستخرج له.

3. ضمن **مستخرجات الكيانات**، حدد اسم المستخرج الذي تريد إعادة تسميته، ثم حدد **إعادة تسمية**.

    ![لقطة شاشة لمقسم "مستخرجات الكيانات" تعرض مستخرج محدد مع تمييز الخيار "إعادة تسمية".](../media/content-understanding/entity-extractor-rename.png) 

4. في اللوحة **"إعادة تسمية مستخرج الكيان** ":

   أ. ضمن **اسم جديد**، أدخل الاسم الجديد للمستخرج.

    ![لقطة شاشة تعرض لوحة استخراج الكيانات.](../media/content-understanding/rename-entity-extractor-panel.png) 

   ب. (اختياري) ضمن **إعدادات متقدمة**، حدد ما إذا كنت تريد إقران عمود موقع موجود.

5. حدد **إعادة تسمية**.

## <a name="see-also"></a>انظر أيضاً
[إنشاء مستخرج](create-an-extractor.md)

[إنشاء تصنيف](create-a-classifier.md)

[إعادة تسمية نموذج](rename-a-model.md)

[أنواع الشرح](explanation-types-overview.md)

[الاستفادة من مستخرج مخزن المصطلحات عند إنشاء مستخرج](leverage-term-store-taxonomy.md)

[نظرة عامة حول فهم المستند](document-understanding-overview.md)

[تطبيق نموذج](apply-a-model.md) 
