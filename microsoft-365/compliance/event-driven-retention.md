---
title: بدء الاستبقاء عند وقوع حدث
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-may2020
- seo-marvel-jun2020
description: عادة ما تكون جزءا من حل إدارة السجلات، يمكنك تكوين تسمية استبقاء لبدء فترة الاستبقاء استنادا إلى حدث تحدده.
ms.openlocfilehash: ad5fb2ef567525fa021acb0388ebc5cc98b1148c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568559"
---
# <a name="start-retention-when-an-event-occurs"></a>بدء الاستبقاء عند وقوع حدث

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

عندما تحتفظ بالمحتوى، غالبا ما تستند فترة الاستبقاء إلى عمر المحتوى. على سبيل المثال، يمكنك الاحتفاظ بالمستندات لمدة سبع سنوات بعد إنشائها ثم حذفها. ولكن عند تكوين تسميات [الاستبقاء](retention.md#retention-labels)، يمكنك أيضا إنشاء أساس لفترة استبقاء عند حدوث نوع معين من الأحداث. يؤدي الحدث إلى تشغيل بداية فترة الاستبقاء، ويفرض على كل المحتوى الذي تم تطبيق تسمية استبقاء عليه لهذا النوع من الأحداث إجراءات استبقاء التسمية.
  
أمثلة لاستخدام الاستبقاء المستند إلى الحدث:
  
- **الموظفون الذين يغادرون المؤسسة** لنفترض أنه يجب الاحتفاظ بسجلات الموظفين لمدة 10 سنوات من وقت مغادرة الموظف المؤسسة. بعد مرور 10 سنوات، يجب التخلص من كل المستندات المتعلقة بتوظيف هذا الموظف وأداءه وإنهائه. الحدث الذي يقوم بتشغيل فترة الاستبقاء لمدة 10 سنوات هو الموظف الذي يغادر المؤسسة. 
    
- **انتهاء صلاحية العقد** لنفترض أنه يجب الاحتفاظ بجميع السجلات ذات الصلة بالتعاقدات لمدة خمس سنوات من وقت انتهاء مدة العقد. الحدث الذي يؤدي إلى تشغيل فترة الاستبقاء لمدة خمس سنوات هو انتهاء مدة العقد. 
    
- **مدة حياة المنتج** قد يكون لدى مؤسستك متطلبات استبقاء ذات صلة بتاريخ التصنيع الأخير للمنتجات للمحتوى مثل المواصفات التقنية. في هذه الحالة، يكون تاريخ التصنيع الأخير هو الحدث الذي يؤدي إلى تشغيل فترة الاستبقاء. 
    
يتم عادة استخدام الاستبقاء المستند إلى الحدث كجزء من عملية إدارة السجلات. وهذا يعني ما يلي:
  
- تقوم تسميات الاستبقاء التي تستند إلى أحداث أيضا عادة بعلامة العناصر كسجل، كجزء من حل إدارة السجلات. لمزيد من المعلومات، راجع [التعرف على إدارة السجلات](records-management.md).

- يتم الاحتفاظ بالمستند الذي تم الإعلان عن سجله ولكن لم يتم حتى الآن تشغيل الحدث له إلى أجل غير مسمى (لا يمكن حذف السجلات نهائيا)، حتى يؤدي الحدث إلى تشغيل فترة استبقاء هذا المستند.
    
- عادة ما تقوم تسميات الاستبقاء المستندة إلى الأحداث بتشغيل مراجعة الترتيب في نهاية فترة الاستبقاء، بحيث يمكن لمدير السجلات مراجعة المحتوى والتخلص منه يدويا. لمزيد من المعلومات، راجع [تغيير موضع المحتوى](disposition.md).
    

إن تسمية الاستبقاء التي تستند إلى حدث لها القدرات نفسها التي لديها أي تسمية استبقاء في Microsoft 365. لمزيد من المعلومات، راجع [التعرف على سياسات الاستبقاء وتسميات الاستبقاء](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>فهم العلاقة بين أنواع الأحداث والتسميات والأحداث وم IDS

لاستخدام الاستبقاء المستند إلى الحدث بنجاح، من المهم فهم العلاقة بين أنواع الأحداث وتسميات الاستبقاء والأحداث ومستندات الأصول كما هو موضح في الرسومات التخطيطية والشرح التالي: 
  
![الرسم التخطيطي 1 من 2: نوع الحدث والتسميات والأحداث ومخططات الأصول.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![الرسم التخطيطي 2 من 2: نوع الحدث والتسميات والأحداث ومخططات الأصول.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. يمكنك إنشاء تسميات استبقاء لأنواع مختلفة من المحتويات ثم إقرانها بنوع حدث. على سبيل المثال، تقترن تسميات الاستبقاء لأنواع مختلفة من ملفات المنتجات والسجلات بنوع حدث يسمى "عمر المنتج" لأنه يجب الاحتفاظ بهذه السجلات لمدة 10 سنوات من الوقت الذي يصل فيه المنتج إلى نهاية عمره الافتراضي.
    
2. يقوم المستخدمون (مديرو السجلات عادة) بتطبيق تسميات الاستبقاء هذه على المحتوى، ويدخل (للمستندات الموجودة في SharePoint OneDrive) معرّف الأصول لكل عنصر. في هذا المثال، إن "معر ة الأصل" هو اسم منتج أو رمز تستخدمه المؤسسة. بعد ذلك، يتم تعيين تسمية استبقاء لكل سجل، ويحتوي كل سجل على خاصية تحتوي على "معرّف الأصول". يمثل الرسم **التخطيطي كل المحتوى** لكل سجلات المنتجات في مؤسسة، ويتحمل كل عنصر معانات في الملج الموجود به سجله. 
    
3. عمر المنتج هو نوع الحدث؛ منتج معين يصل إلى نهاية العمر هو حدث. عند وقوع حدث من نوع الحدث هذا، في هذه الحالة، عندما يصل منتج إلى نهاية العمر الإنتاجي، تقوم بإنشاء حدث يحدد:
    
   - مستند أصول (لمستندات SharePoint OneDrive أخرى)
    
   - الكلمات الأساسية (Exchange الأساسية). في هذا المثال، تستخدم المؤسسة رمز منتج في الرسائل التي تحتوي على سجلات المنتجات، وبالتالي فإن الكلمة الأساسية لعناصر Exchange هي نفسها وظيفيا كمستندات SharePoint OneDrive المستند.
    
   - تاريخ وقوع الحدث. يتم استخدام هذا التاريخ كبداية فترة الاستبقاء. يمكن أن يكون هذا التاريخ هو التاريخ الحالي أو الماضي أو المستقبلي.

4. بعد إنشاء حدث، يتم مزامنة تاريخ الحدث هذا مع كل المحتوى الذي يحتوي على تسمية استبقاء لنوع الحدث هذا ويحتوي على اسم الأصل المحدد أو الكلمة الأساسية المحددة. مثل أي تسمية استبقاء، قد تستغرق هذه المزامنة ما يصل إلى سبعة أيام. في الرسم التخطيطي السابق، يتم تشغيل كل العناصر التي تم وضع دائرة باللون الأحمر عليها فترة استبقاء بواسطة هذا الحدث. بعبارة أخرى، عندما يصل هذا المنتج إلى نهاية العمر الإنتاجي، فإن هذا الحدث يؤدي إلى تشغيل فترة الاستبقاء لسجلات هذا المنتج.

من المهم أن تدرك أنه إذا لم تحدد أي من "معرّف الأصول" أو الكلمات الأساسية لحدث ما،  فإن كل المحتوى الذي لديه تسمية استبقاء من نوع الحدث هذا سيتم تشغيل فترة استبقاء له بواسطة الحدث. وهذا يعني أنه في الرسم التخطيطي السابق، سيتم بدء الاحتفاظ بكل المحتوى. قد لا يكون هذا ما تنوي القيام به.

وأخيرا، تذكر أن كل تسمية استبقاء لها إعدادات استبقاء خاصة بها. في هذا المثال، يتم تحديد كل منها لمدة 10 سنوات، ولكن من الممكن أن يؤدي الحدث إلى تشغيل تسميات استبقاء حيث يكون لكل تسمية فترة استبقاء مختلفة.
  
## <a name="how-to-set-up-event-driven-retention"></a>كيفية إعداد استبقاء مدفوع بالأحداث

سير عمل عالي المستوى للاحتفاظ بالأحداث:
  
![رسم تخطيطي لسير العمل لإعداد استبقاء مدفوع بالأحداث.](../media/event-based-retention-process.png)
  
> [!TIP]
> راجع استخدام تسميات الاستبقاء لإدارة دورة حياة المستندات المخزنة في [SharePoint](auto-apply-retention-labels-scenario.md) للحصول على سيناريو مفصل حول استخدام الخصائص المدارة في SharePoint لتطبيق تسميات الاستبقاء بشكل تلقائي وتطبيق استبقاء مستند إلى الأحداث.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>الخطوة 1: إنشاء تسمية تستند فترة استبقاءها إلى حدث

لإنشاء تسمية استبقاء وتكوينها، راجع إرشادات إنشاء تسميات [](file-plan-manager.md#create-retention-labels) استبقاء لإدارة السجلات، أو كيفية إنشاء تسميات استبقاء [لإدارة المعلومات](create-retention-labels-information-governance.md). ولكن بشكل خاص بالاحتفاظ بالأحداث، في الصفحة  تعريف إعدادات الاستبقاء عند إنشاء تسمية الاستبقاء، بعد بدء فترة الاستبقاء بالاستناد إلى، حدد أحد أنواع الأحداث الافتراضية من القائمة المنسدلة، أو قم بإنشاء نوع الحدث الخاص بك عن طريق تحديد إنشاء نوع حدث **جديد**:

![إنشاء نوع حدث جديد لتسمية استبقاء.](../media/SPRetention6.png)

إن نوع الحدث هو مجرد وصف عام لحدث تريد إقرانه بتسمية استبقاء.

تتضمن أنواع الأحداث الافتراضية (نوع الحدث **)**  >  بعد اسمها في القائمة المنسدلة لتسهيل تحديدها، كما يمكنك أيضا رؤية نوع الحدث وإنشاءه من علامة التبويب إدارة **السجلاتاختراعات** > إدارة أنواع **الأحداث.**

يتطلب الاستبقاء المستند إلى الحدث إعدادات استبقاء:
  
- الاحتفاظ بالمحتوى.
    
- احذف المحتوى تلقائيا أو قم بتشغيل مراجعة الترتيب في نهاية فترة الاستبقاء.
  
يتم عادة استخدام الاستبقاء المستند إلى الحدث للمحتوى الذي تم الإعلان عنه كسجل، لذلك هذا هو الوقت المناسب للتحقق مما إذا كنت تحتاج أيضا إلى تحديد الخيار الذي يقوم بتحديد المحتوى [كسجل](records-management.md#records).

إذا كنت تستخدم نوع حدث موجود بدلا من إنشاء نوع حدث جديد، فاتخطي إلى الخطوة 3.

> [!NOTE]
> بعد اختيار نوع حدث وحفظ تسمية الاستبقاء، لا يمكن تغيير نوع الحدث.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>الخطوة 2: إنشاء نوع حدث جديد للتسمية

لإعدادات الاستبقاء، إذا حددت إنشاء نوع حدث **جديد**، أدخل اسما ووصفا لنوع الحدث. ثم حدد **التالي****، إرسال****، تم**.

العودة إلى **الصفحة تعريف إعدادات الاستبقاء**، بالنسبة إلى بدء فترة الاستبقاء استنادا إلى، استخدم القائمة المنسدلة لتحديد نوع الحدث الذي أنشأته.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>الخطوة 3: نشر تسميات الاستبقاء المستندة إلى الحدث أو تطبيقها التلقائي

تماما مثل أي تسمية استبقاء، تحتاج إلى نشر تسمية تستند إلى حدث أو تطبيقها تلقائيا، لكي يتم تطبيقها يدويا أو تلقائيا على المحتوى:
- [نشر تسميات الاستبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md)
- [تطبيق تسمية استبقاء على المحتوى تلقائيا](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>الخطوة 4: إدخال "معرّف الأصول"

بعد تطبيق تسمية مستندة إلى حدث على المحتوى، يمكنك إدخال "معرّف الأصول" لكل عنصر. على سبيل المثال، قد تستخدم مؤسستك:
  
- رموز المنتجات التي يمكنك استخدامها للاحتفاظ بالمحتوى لمنتج معين فقط.
    
- Project الرموز التي يمكنك استخدامها للاحتفاظ بالمحتوى لمشروع معين فقط.
    
- هويات الموظفين التي يمكنك استخدامها للاحتفاظ بالمحتوى لشخص معين فقط.
    
إن "معرّف الأصول" هو ببساطة خاصية مستند أخرى متوفرة في SharePoint OneDrive. قد تستخدم مؤسستك بالفعل خصائص مستندات ومستندات أخرى لتصنيف المحتوى. إذا كان الأمر كذلك، يمكنك أيضا استخدام هذه الخصائص والقيم عند إنشاء حدث — راجع الخطوة 6 التالية. النقطة الهامة هي أنه يجب استخدام تركيبة خاصية *:قيمة* في خصائص المستند لاقران هذا العنصر بنوع حدث.
  
![مربع نص لإدخال "معرّف الأصول".](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>الخطوة 5: إنشاء حدث

عند حدوث  >  مثيل معين لنوع الحدث هذا، مثل المنتج الذي يصل إلى نهاية العمر العمري، انتقل إلى صفحة إدارة **السجلاتاختراعات** في مركز التوافق في Microsoft 365، وحدد **+ إنشاء** لإنشاء حدث. يمكنك تشغيل الحدث عن طريق إنشائه، هنا.

![أنشئ حدثا لبدء تشغيل الاستبقاء لتسميات الاستبقاء المستندة إلى الحدث.](../media/create-event-records-management.png)

يتم دعم ما يصل إلى مليون حدث لكل مستأجر.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>الخطوة 6: اختيار نوع الحدث نفسه المستخدم بواسطة التسمية في الخطوة 2

عند إنشاء الحدث، اختر نوع الحدث نفسه المحدد في إعدادات تسمية الاستبقاء في الخطوة 2. على سبيل المثال، إذا قمت بتحديد  مدة حياة المنتج كنوع الحدث لإعدادات التسمية، **فحدد عمر** المنتج عند إنشاء الحدث. سيتم تشغيل فترة الاستبقاء الخاصة بالمحتوى الذي تم تطبيق تسميات استبقاء عليه فقط من نوع الحدث هذا.

![الخيار في إعدادات الحدث لاختيار نوع حدث.](../media/choose-event-type-records-management.png)

بدلا من ذلك، إذا كنت بحاجة إلى إنشاء حدث لتسميات استبقاء متعددة لها أنواع أحداث مختلفة، فحدد الخيار **اختيار تسميات** موجودة. بعد ذلك، حدد التسميات التي تم تكوينها لأنواع الأحداث التي تريد إقرانها بهذا الحدث.

### <a name="step-7-enter-keywords-or-query-for-exchange-asset-id-for-sharepoint-and-onedrive"></a>الخطوة 7: أدخل كلمات أساسية أو استعلاما Exchange وم id asset SharePoint OneDrive

يمكنك الآن تضييق نطاق المحتوى. بالنسبة Exchange، يمكنك القيام بذلك من خلال تحديد كلمات أساسية أو استعلام. بالنسبة SharePoint OneDrive المحتوى، يمكنك القيام بذلك من خلال تحديد "معرّف الأصول".

بالنسبة Exchange، استخدم الكلمات الأساسية أو استعلام يستخدم لغة استعلام الكلمة الأساسية (KQL). لمزيد من المعلومات حول بناء جملة الاستعلام، راجع مرجع بناء جملة لغة استعلام الكلمة [الأساسية (KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)). لمزيد من المعلومات حول الخصائص القابلة للبحث التي يمكنك استخدامها Exchange، راجع استعلامات الكلمات الأساسية وشروط البحث [للبحث في المحتوى](keyword-queries-and-search-conditions.md).

بالنسبة لمحددات الأصول، سيتم فرض الاستبقاء فقط على المحتوى باستخدام زوج *القيمة:الخاصية* المحددة. على سبيل المثال، إذا كنت تستخدم الخاصية Asset ID `ComplianceAssetID:<value>` ، أدخل في المربع لمعاينات الأصول الموضحة في الصورة التالية.

إذا لم يتم إدخال أحد محددات الأصول، يتم تطبيق نفس تاريخ الاستبقاء على كل المحتويات التي بها تسميات من نوع الحدث هذا.

من المحتمل أن تكون مؤسستك قد طبقت خصائص ومستندات أخرى على المستندات ذات الصلة بنوع الحدث هذا. على سبيل المثال، إذا كنت بحاجة إلى الكشف عن سجلات منتج معين، فقد يكون المعرف خليطا من الخاصية المخصصة ProductID والقيمة "XYZ". في هذه الحالة، ستدخل في `ProductID:XYZ` مربع "لمعانات الأصول" الموضحة في الصورة التالية.

وأخيرا، اختر تاريخ وقوع الحدث؛ يتم استخدام هذا التاريخ كبداية فترة الاستبقاء. بعد إنشاء حدث، يتم مزامنة تاريخ الحدث هذا مع كل المحتوى مع تسمية استبقاء لنوع الحدث هذا وم التعريف الأصل والكلمات الأساسية أو الاستعلامات. وكما هو حال أي تسمية استبقاء، قد تستغرق هذه المزامنة ما يصل إلى سبعة أيام.
  
![صفحة إعدادات الحدث.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

بعد إنشاء حدث، يتم تطبيق إعدادات الاستبقاء على المحتوى المسمى والمفهرس بالفعل. إذا تم إضافة تسمية الاستبقاء إلى محتوى جديد بعد إنشاء الحدث، فيجب إنشاء حدث جديد بنفس التفاصيل.

لا يلغي حذف حدث ما إعدادات الاستبقاء التي أصبحت الآن في وضع التنفيذ للمحتوى المسمى بالفعل. حاليا، لا يمكنك إلغاء الأحداث بعد تشغيلها.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>استخدام "البحث في المحتوى" للبحث عن كل المحتوى مع تسمية أو اسم محدد لمعرف الأصل

بعد تعيين تسميات الاستبقاء إلى المحتوى، يمكنك استخدام البحث في المحتوى للبحث عن كل المحتوى المصنف مع تسمية استبقاء معينة أو الذي يحتوي على محدد لمعرف الأصل:
  
- للعثور على كل المحتوى مع تسمية استبقاء معينة،  اختر شرط تسمية الاستبقاء، ثم أدخل اسم التسمية الكامل أو جزء من اسم التسمية واستخدم أحرف البدل. 
    
- للعثور على كل المحتوى الذي له محدد لمعرف الأصول، أدخل الخاصية **ComplianceAssetID** وقيمة، باستخدام التنسيق `ComplianceAssetID:<value>`. 
    
لمزيد من المعلومات، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث في المحتوى](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>أتمتة الأحداث باستخدام PowerShell

يمكنك استخدام برنامج PowerShell النصي لأتمتة الاستبقاء المستند إلى الأحداث من تطبيقات الأعمال. إن PowerShell cmdlets المتوفرة للاحتفاظ بالأحداث:
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

## <a name="automate-events-by-using-a-rest-api"></a>أتمتة الأحداث باستخدام API REST

يمكنك استخدام API REST لإنشاء الأحداث التي تقوم بتشغيل بداية وقت الاستبقاء تلقائيا.

API REST هي نقطة نهاية الخدمة التي تدعم مجموعات من عمليات HTTP (الأساليب)، التي توفر إمكانية الوصول إلى موارد الخدمة لإنشاء/استرداد/تحديث/حذف. لمزيد من المعلومات، راجع [مكونات طلب/استجابة ل API](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse) REST. باستخدام Microsoft 365 REST API، يمكن إنشاء الأحداث واستردادها باستخدام طريقتي POST و GET.

هناك خياران لاستخدام REST API:

- **تقوم Microsoft Power Automate أو تطبيق مماثل** بتشغيل تكرار حدث تلقائيا. إن Power Automate Microsoft هو أحد برامج التوصيل للاتصال بأنظمت أخرى، لذلك لا تحتاج إلى كتابة حل مخصص. لمزيد من المعلومات، راجع Power Automate [ويب](https://flow.microsoft.com/en-us/).

- **PowerShell أو عميل HTTP لاستدعاء REST API لإنشاء الأحداث باستخدام PowerShell** (الإصدار 6 أو الإصدارات الأحدث)، الذي هو جزء من حل مخصص.

قبل استخدام API REST، كمسؤول عام، تأكد من عنوان URL لاستخدامه في مكالمة حدث الاستبقاء. للقيام بذلك، يمكنك تشغيل مكالمة حدث استبقاء GET باستخدام عنوان URL ل API REST:

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

تحقق من رمز الاستجابة. إذا كان 302، فاحصل على عنوان URL المعاد توجيهه من الخاصية الموقع لرأس الاستجابة واستخدم عنوان URL `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` هذا بدلا من الإرشادات التالية.

يمكن تأكيد الأحداث التي يتم إنشاؤها تلقائيا من خلال عرضها في مركز التوافق في Microsoft 365 > **إدارة** >   **السجلاتEvents**.

### <a name="use-microsoft-power-automate-to-create-the-event"></a>استخدام microsoft Power Automate لإنشاء الحدث

إنشاء تدفق ينشئ حدثا باستخدام Microsoft 365 REST API:

![استخدام Flow لإنشاء حدث.](../media/automate-event-driven-retention-flow-1.png)

![استخدام التدفق لاستدعاء REST API.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>إنشاء حدث

نموذج التعليمات البرمجية لاستدعاء REST API:

- **الأسلوب**: POST
- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **رؤوس**: Key = Content-Type, Value = application/atom+xml
- **الجسم**:

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'?>
    
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'
    
    xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'
    
    xmlns='http://www.w3.org/2005/Atom'>
    
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />
    
    <updated>9/9/2017 10:50:00 PM</updated>
    
    <content type='application/xml'>
    
    <m:properties>
    
    <d:Name>Employee Termination </d:Name>
    
    <d:EventType>99e0ae64-a4b8-40bb-82ed-645895610f56</d:EventType>
    
    <d:SharePointAssetIdQuery>1234</d:SharePointAssetIdQuery>
    
    <d:EventDateTime>2018-12-01T00:00:00Z </d:EventDateTime>
    
    </m:properties>
    
    </content>
    
    </entry>
    ```

- **المصادقة**: أساسي
- **اسم** المستخدم: "Complianceuser"
- **كلمة** المرور: "Compliancepassword"


##### <a name="available-parameters"></a>المعلمات المتوفرة


|المعلمات|الوصف|ملاحظات|
|--- |--- |--- |
|<d:Name></d:Name>|توفير اسم فريد للحدث،|لا يمكن أن تحتوي على مسافات زائدة أو الأحرف التالية: ٪ * \ & < \> \| # ؟ , : ;|
|<d:EventType></d:EventType>|أدخل اسم نوع الحدث (أو Guid)،|مثال: "إنهاء الموظف". يجب أن يقترن نوع الحدث بتسمية استبقاء.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|أدخل "ComplianceAssetId:" + "معرّف الموظف"|مثال: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|تاريخ الحدث والوقت|التنسيق: yyyy-MM-ddTHH:mm:ssZ، مثال: 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف       |
| ----------------- | --------------------- |
| 302               | إعادة توجيه              |
| 201               | تم إنشاؤه               |
| 403               | فشل التفويض  |
| 401               | فشل المصادقة |

##### <a name="get-events-based-on-a-time-range"></a>الحصول على الأحداث استنادا إلى نطاق وقت

- **الطريقة**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **رؤوس**: Key = Content-Type, Value = application/atom+xml

- **المصادقة**: أساسي

- **اسم** المستخدم: "Complianceuser"

- **كلمة** المرور: "Compliancepassword"

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف                   |
| ----------------- | --------------------------------- |
| 200               | موافق، قائمة بالأحداث في atom+ xml |
| 404               | لم يتم العثور على                         |
| 302               | إعادة توجيه                          |
| 401               | فشل التفويض              |
| 403               | فشل المصادقة             |

##### <a name="get-an-event-by-id"></a>الحصول على حدث بواسطة الم ID

- **الطريقة**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **رؤوس**: Key = Content-Type, Value = application/atom+xml

- **المصادقة**: أساسي

- **اسم** المستخدم: "Complianceuser"

- **كلمة** المرور: "Compliancepassword"

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | حسنا، يحتوي النصي للاستجابة على الحدث في atom+xml |
| 404               | لم يتم العثور على                                            |
| 302               | إعادة توجيه                                             |
| 401               | فشل التفويض                                 |
| 403               | فشل المصادقة                                |

##### <a name="get-an-event-by-name"></a>الحصول على حدث حسب الاسم

- **الطريقة**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **رؤوس**: Key = Content-Type, Value = application/atom+xml

- **المصادقة**: أساسي

- **اسم** المستخدم: "Complianceuser"

- **كلمة** المرور: "Compliancepassword"

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | حسنا، يحتوي النصي للاستجابة على الحدث في atom+xml |
| 404               | لم يتم العثور على                                            |
| 302               | إعادة توجيه                                             |
| 401               | فشل التفويض                                 |
| 403               | فشل المصادقة                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>استخدام PowerShell أو أي عميل HTTP لإنشاء الحدث

يجب أن يكون PowerShell هو الإصدار 6 أو الإصدارات الأحدث.

في جلسة PowerShell، تشغيل البرنامج النصي التالي:

```powershell
param([string]$baseUri)

$userName = "UserName"

$password = "Password"

$securePassword = ConvertTo-SecureString $password -AsPlainText -Force

$credentials = New-Object System.Management.Automation.PSCredential($userName, $securePassword)

$EventName="EventByRESTPost-$(([Guid]::NewGuid()).ToString('N'))"

Write-Host "Start to create an event with name: $EventName"

$body = "<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'

xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'

xmlns='http://www.w3.org/2005/Atom'>

<category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />

<updated>7/14/2017 2:03:36 PM</updated>

<content type='application/xml'>

<m:properties>

<d:Name>$EventName</d:Name>

<d:EventType>e823b782-9a07-4e30-8091-034fc01f9347</d:EventType>

<d:SharePointAssetIdQuery>'ComplianceAssetId:123'</d:SharePointAssetIdQuery>

</m:properties>

</content>

</entry>"

$event = $null

try

{

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri "$baseUri/ComplianceRetentionEvent" -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

catch

{

$response = $_.Exception.Response

if($response.StatusCode -eq "Redirect")

{

$url = $response.Headers.Location

Write-Host "redirected to $url"

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri $url -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

}

$event | fl *
```
