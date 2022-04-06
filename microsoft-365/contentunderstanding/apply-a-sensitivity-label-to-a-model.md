---
title: تطبيق تسمية حساسية على نموذج في Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: تعرف على كيفية تطبيق تسمية حساسية على نموذج في SharePoint Syntex.
ms.openlocfilehash: 189db9314e01a52618890daf6b0e5d4e81317de9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681689"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>تطبيق تسمية حساسية على نموذج في Microsoft SharePoint Syntex

يمكنك بسهولة تطبيق تسمية [حساسية](../compliance/sensitivity-labels.md) على نماذج فهم المستندات في Microsoft SharePoint Syntex. هذه الميزة غير متوفرة بعد لنماذج معالجة النماذج.

تسمح لك تسميات الحساسية بتطبيق التشفير على المستندات التي تحددها نماذجك. على سبيل المثال، تريد أن يحدد النموذج الخاص بك ليس فقط أي مستندات مالية تحتوي على أرقام حسابات بنكية أو أرقام بطاقات ائتمان يتم تحميلها إلى مكتبة المستندات، ولكن أيضا لتطبيق تسمية الحساسية التي تم تكوينها مع إعدادات التشفير لتقييد الأشخاص الذين يمكنهم الوصول إلى هذا المحتوى وكيفية استخدامه. SharePoint Syntex النماذج الجديدة قواعد [ترتيب](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) التسميات ولا ت الكتابة فوق تسمية موجودة تم تطبيقها يدويا من قبل المستخدم على الملف. 

يمكنك تطبيق تسمية حساسية موجودة مسبقا على النموذج من خلال إعدادات النموذج على الصفحة الرئيسية للنموذج. يجب أن تكون التسمية منشورة بالفعل لتكون متوفرة للاختيار من إعدادات النموذج. تنطبق التسميات Office ملفات Word (.docx) PowerPoint (.pptx) Excel (.xlsx). 

> [!Important]
> لكي تتوفر تسميات الحساسية لتطبيقها على نماذج فهم المستندات، يجب إنشاؤها ونشرها [في مركز Microsoft 365 التوافق](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>إضافة تسمية حساسية إلى نموذج فهم المستند

1. من الصفحة الرئيسية للنموذج، حدد **إعدادات النموذج**.

   ![لقطة شاشة لصفحة "النماذج" مع تمييز الخيار "إعدادات النموذج".](../media/content-understanding/sensitivity-model-settings.png)

2. في **جزء إعدادات** النموذج، في المقطع توافق،  حدد قائمة تسمية الحساسية لرؤية  قائمة تسميات الحساسية المتوفرة لتطبيقها على النموذج.

   ![لقطة شاشة ل جزء إعدادات النموذج تعرض قائمة تسمية الحساسية.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. حدد تسمية الحساسية التي تريد تطبيقها على النموذج، ثم حدد **حفظ**.

بعد تطبيق تسمية الحساسية على النموذج، يمكنك تطبيقها على:

- مكتبة مستندات جديدة
- مكتبة المستندات التي تم تطبيق النموذج عليها بالفعل
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>تطبيق تسمية الحساسية على مكتبة مستندات تم تطبيق النموذج عليها بالفعل

إذا تم بالفعل تطبيق نموذج فهم المستند على مكتبة مستندات، يمكنك القيام بما يلي لمزامنة تحديث تسمية الحساسية لتطبيقه على مكتبة المستندات:

1. في الصفحة الرئيسية للنموذج، في المقطع  مكتبات بهذا النموذج، حدد مكتبة المستندات التي تريد تطبيق تحديث تسمية الحساسية عليها.

2. حدد **مزامنة**.

   ![لقطة شاشة تعرض المكتبات التي تحتوي على مقطع النموذج هذا مع تمييز "مزامنة".](../media/content-understanding/sensitivity-libraries-sync.png)

بعد تطبيق التحديث ومزامنته مع النموذج، يمكنك تأكيد أنه قد تم تطبيقه من خلال القيام بالخطوات التالية:

1. في مركز المحتوى، في **قسم المكتبات** التي تحتوي على هذا النموذج، حدد المكتبة التي تم تطبيق النموذج المحدث عليها. 

2. في طريقة عرض مكتبة المستندات، حدد أيقونة المعلومات للتحقق من خصائص النموذج.

3. في القائمة **نماذج** نشطة، حدد النموذج المحدث.

4. في المقطع **تسمية الحساسية** ، سترى اسم تسمية الحساسية المطبقة.

في صفحة عرض النموذج في مكتبة المستندات، سيتم عرض عمود تسمية حساسية جديد. بما أن النموذج يصنف الملفات التي يحددها على أنها تنتمي إلى نوع المحتوى الخاص به ويدرجها في طريقة عرض المكتبة،  سيعرض عمود تسمية الحساسية أيضا اسم تسمية الحساسية التي تم تطبيقها عليها من خلال النموذج.

على سبيل المثال، سيتم أيضا تطبيق تسمية حساسية التشفير على كل المستندات المالية التي يحددها النموذج، مما يمنع الأشخاص غير المصرح لهم بالوصول إليها. إذا تم إجراء محاولة للوصول إلى الملف من مكتبة المستندات من قبل شخص غير مصرح به، سيتم عرض خطأ يقول إنه غير مسموح به بسبب تسمية الحساسية المطبقة.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft 365 Compliance Center](../admin/security-and-compliance/set-up-compliance.md).

You can either apply a sensitivity label to a form processing model when you are creating a model, or apply it to an existing model.

### Add a sensitivity label when you create a form processing model

1. When you [create a new form processing model](create-a-form-processing-model.md), select **Advanced settings**.

2. In **Advanced settings**, in the **Sensitivity label** section, select the menu and then select the sensitivity label you want to apply to the model.

3.  After you've completed your remaining model settings, select **Create** to build your model.

### Add a sensitivity label to an existing form processing model

You can add a sensitivity label to an existing form processing model in different ways:

- Through the **Automate** menu in the document library
- Through the **Active model** settings in the document library 

#### Add a sensitivity label to an existing form processing model through the Automate menu

You can add a sensitivity label to an existing form processing model that you own through the **Automate** menu in the document library in which the model is applied.

1. In your document library to which the form processing model is applied, select the **Automate** menu, select **AI Builder**, and then select **View form processing model details**.

2. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

#### Add a sensitivity label to an existing form processing model in the active model settings

You can add a sensitivity label to an existing form processing model that you own through the **Active model** settings in the document library in which the model is applied.

1. In the SharePoint document library in which the model is applied, select the **View active models** icon, and then select **View active models**.

2. In **Active models**, select the form processing model to which you want to apply the sensitivity label.

3. On the **Model details** pane, in the **Sensitivity label** section, select the sensitivity label you want to apply. Then select **Save**.

   > [!NOTE]
   > You must be the model owner for the **Model settings** pane to be editable. 
--->

## <a name="see-also"></a>راجع أيضًا

[تطبيق تسمية استبقاء](apply-a-retention-label-to-a-model.md)

[إنشاء تصنيف](create-a-classifier.md)

[إنشاء مستخرج](create-an-extractor.md)

[نظرة عامة حول فهم المستند](document-understanding-overview.md)
