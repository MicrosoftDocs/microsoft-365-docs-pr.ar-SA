---
title: تطبيق وصف الحساسية على نموذج في Microsoft SharePoint Syntex
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
description: تعرف على كيفية تطبيق وصف الحساسية على نموذج في SharePoint Syntex.
ms.openlocfilehash: 4ab530fbd4a187f03617b01b6b9661332ad1a7d9
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945594"
---
# <a name="apply-a-sensitivity-label-to-a-model-in-microsoft-sharepoint-syntex"></a>تطبيق وصف الحساسية على نموذج في Microsoft SharePoint Syntex

يمكنك بسهولة تطبيق [وصف الحساسية](../compliance/sensitivity-labels.md) على نماذج فهم المستندات في Microsoft SharePoint Syntex. هذه الميزة غير متوفرة بعد لنماذج معالجة النماذج.

تتيح لك تسميات الحساسية تطبيق التشفير على المستندات التي تحددها نماذجك. على سبيل المثال، تريد أن لا يحدد النموذج الخاص بك أي مستندات مالية تحتوي على أرقام حسابات بنكية أو أرقام بطاقات ائتمان يتم تحميلها إلى مكتبة المستندات فحسب، بل تريد أيضا تطبيق وصف الحساسية الذي تم تكوينه مع إعدادات التشفير لتقييد من يمكنه الوصول إلى هذا المحتوى وكيفية استخدامه. تحترم النماذج SharePoint Syntex قواعد [ترتيب التسمية](../compliance/apply-sensitivity-label-automatically.md#how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label) ولا تقوم أيضا بالكتابة فوق تسمية موجودة تم تطبيقها يدويا من قبل مستخدم على الملف. 

يمكنك تطبيق وصف حساسية موجود مسبقا على النموذج الخاص بك من خلال إعدادات النموذج الخاص بك على الصفحة الرئيسية لنموذجك. يجب نشر التسمية مسبقا لتكون متوفرة للتحديد من إعدادات النموذج. تنطبق التسميات على ملفات Office ل Word (.docx) PowerPoint (.pptx) Excel (.xlsx). 

> [!Important]
> لكي تتوفر أوصاف الحساسية لتطبيقها على نماذج فهم المستندات، يجب [إنشاؤها ونشرها في مدخل توافق Microsoft Purview](../admin/security-and-compliance/set-up-compliance.md).

## <a name="add-a-sensitivity-label-to-a-document-understanding-model"></a>إضافة وصف الحساسية إلى نموذج فهم المستند

1. من الصفحة الرئيسية للنموذج، حدد **إعدادات النموذج**.

   ![لقطة شاشة لصفحة النماذج مع تمييز خيار إعدادات النموذج.](../media/content-understanding/sensitivity-model-settings.png)

2. في جزء **"Model settings** "، في قسم **"Compliance** "، حدد قائمة **وصف الحساسية** لمشاهدة قائمة أوصاف الحساسية المتوفرة لك لتطبيقها على النموذج.

   ![لقطة شاشة لجزء إعدادات النموذج تعرض قائمة وصف الحساسية.](../media/content-understanding/sensitivity-model-settings-pane.png) 

3. حدد وصف الحساسية الذي تريد تطبيقه على النموذج، ثم حدد **"حفظ**".

بعد تطبيق وصف الحساسية على نموذجك، يمكنك تطبيقه على:

- مكتبة مستندات جديدة
- مكتبة المستندات التي تم تطبيق النموذج عليها بالفعل
 
### <a name="apply-the-sensitivity-label-to-a-document-library-to-which-the-model-is-already-applied"></a>تطبيق وصف الحساسية على مكتبة مستندات تم تطبيق النموذج عليها بالفعل

إذا تم بالفعل تطبيق نموذج فهم المستند على مكتبة مستندات، يمكنك القيام بما يلي لمزامنة تحديث وصف الحساسية لتطبيقه على مكتبة المستندات:

1. في الصفحة الرئيسية للنموذج، في **مكتبات قسم النموذج هذا** ، حدد مكتبة المستندات التي تريد تطبيق تحديث وصف الحساسية عليها.

2. حدد **"مزامنة**".

   ![Screenshot showing Libraries with this model section with Sync highlighted.](../media/content-understanding/sensitivity-libraries-sync.png)

بعد تطبيق التحديث ومزامنته مع النموذج الخاص بك، يمكنك التأكد من أنه قد تم تطبيقه من خلال تنفيذ الخطوات التالية:

1. في مركز المحتوى، في **المكتبات التي تحتوي على قسم النموذج هذا** ، حدد المكتبة التي تم تطبيق النموذج المحدث عليها. 

2. في طريقة عرض مكتبة المستندات، حدد أيقونة المعلومات للتحقق من خصائص النموذج.

3. في قائمة **النماذج النشطة** ، حدد النموذج المحدث.

4. في قسم **وصف الحساسية** ، سترى اسم وصف الحساسية المطبقة.

في صفحة عرض النموذج في مكتبة المستندات، سيتم عرض عمود **وصف الحساسية** الجديد. بينما يصنف نموذجك الملفات التي يحددها على أنها تنتمي إلى نوع المحتوى الخاص به ويسردها في طريقة عرض المكتبة، سيعرض عمود **وصف الحساسية** أيضا اسم وصف الحساسية الذي تم تطبيقه عليه من خلال النموذج.

على سبيل المثال، ستطبق على جميع المستندات المالية التي يحددها نموذجك أيضا تسمية حساسية *التشفير* ، ما يمنع الوصول إليها من قبل أشخاص غير مصرح لهم. إذا تمت محاولة الوصول إلى الملف من مكتبة المستندات من قبل شخص غير مصرح به، فسيظهر خطأ يقول إنه غير مسموح به بسبب تسمية الحساسية المطبقة.

<!---
## Add a sensitivity label to a form processing model

> [!Important]
> For sensitivity labels to be available to apply to your form processing model, they need to be [created and published in the Microsoft Purview compliance portal](../admin/security-and-compliance/set-up-compliance.md).

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

[إنشاء مصنف](create-a-classifier.md)

[إنشاء مستخرج](create-an-extractor.md)

[نظرة عامة على فهم المستند](document-understanding-overview.md)
