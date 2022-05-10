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
ms.openlocfilehash: 65a3c2088974398abb6ddbeb205cfb66541629e2
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285095"
---
# <a name="start-retention-when-an-event-occurs"></a>بدء الاستبقاء عند وقوع حدث

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

عند الاحتفاظ بالمحتوى، غالبا ما تستند فترة الاستبقاء إلى عمر المحتوى. على سبيل المثال، يمكنك الاحتفاظ بالمستندات لمدة سبع سنوات بعد إنشائها ثم حذفها. ولكن عند تكوين [تسميات الاستبقاء](retention.md#retention-labels)، يمكنك أيضا إنشاء فترة استبقاء استنادا إلى وقت حدوث نوع معين من الأحداث. يشغل الحدث بداية فترة الاستبقاء، ويتم فرض إجراءات استبقاء التسمية على جميع المحتويات التي تم تطبيق تسمية استبقاء عليها لهذا النوع من الأحداث.
  
أمثلة لاستخدام الاستبقاء المستند إلى الحدث:
  
- **الموظفون الذين يغادرون المؤسسة** لنفترض أنه يجب الاحتفاظ بسجلات الموظفين لمدة 10 سنوات من وقت مغادرة الموظف للمؤسسة. بعد انقضاء 10 سنوات، يجب التخلص من جميع المستندات المتعلقة بتوظيف هذا الموظف وأدائه وإنهائه. الحدث الذي يشغل فترة الاستبقاء لمدة 10 سنوات هو الموظف الذي يغادر المؤسسة. 
    
- **انتهاء صلاحية العقد** لنفترض أنه يجب الاحتفاظ بكافة السجلات المتعلقة بالعقود لمدة خمس سنوات من وقت انتهاء صلاحية العقد. الحدث الذي يشغل فترة الاستبقاء لمدة خمس سنوات هو انتهاء صلاحية العقد. 
    
- **مدة بقاء المنتج** قد تكون لدى مؤسستك متطلبات استبقاء ذات صلة بتاريخ التصنيع الأخير لمنتجات المحتوى مثل المواصفات التقنية. في هذه الحالة، يكون تاريخ التصنيع الأخير هو الحدث الذي يشغل فترة الاستبقاء. 
    
يستخدم الاستبقاء المستند إلى الحدث عادة كجزء من عملية إدارة السجلات. وهذا يعني ما يلي:
  
- تقوم تسميات الاستبقاء المستندة إلى الأحداث أيضا بوضع علامة على العناصر كسجل، كجزء من حل إدارة السجلات. لمزيد من المعلومات، راجع ["التعرف على إدارة السجلات](records-management.md)".

- يتم الاحتفاظ بالمستند الذي تم الإعلان عنه كسجل ولكن لم يحدث مشغل الحدث فيه بعد إلى أجل غير مسمى (لا يمكن حذف السجلات بشكل دائم)، حتى يقوم حدث بتشغيل فترة استبقاء هذا المستند.
    
- عادة ما تؤدي تسميات الاستبقاء المستندة إلى الأحداث إلى مراجعة الترتيب في نهاية فترة الاستبقاء، بحيث يمكن لمدير السجلات مراجعة المحتوى والتخلص منه يدويا. لمزيد من المعلومات، راجع [ترتيب المحتوى](disposition.md).
    

تحتوي تسمية الاستبقاء المستندة إلى حدث على نفس إمكانيات أي تسمية استبقاء في Microsoft 365. لمزيد من المعلومات، راجع [التعرف على نهج الاستبقاء وتسميات الاستبقاء](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>فهم العلاقة بين أنواع الأحداث والتسميات والأحداث ومعرف الأصول

لاستخدام الاستبقاء المستند إلى الحدث بنجاح، من المهم فهم العلاقة بين أنواع الأحداث وتسميات الاستبقاء والأحداث ومعرف الأصول كما هو موضح في الرسومات التخطيطية والتفسير التالي: 
  
![الرسم التخطيطي 1 من 2: نوع الحدث والتسميات والأحداث ومعرف الأصول.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![الرسم التخطيطي 2 من 2: نوع الحدث والتسميات والأحداث ومعرف الأصول.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. يمكنك إنشاء تسميات استبقاء لأنواع مختلفة من المحتوى ثم إقرانها بنوع من الأحداث. على سبيل المثال، ترتبط تسميات الاستبقاء لأنواع مختلفة من ملفات المنتجات والسجلات بنوع حدث يسمى "مدة بقاء المنتج" لأنه يجب الاحتفاظ بهذه السجلات لمدة 10 سنوات من الوقت الذي يصل فيه المنتج إلى نهاية عمره الافتراضي.
    
2. يطبق المستخدمون (عادة مديرو السجلات) تسميات الاستبقاء هذه على المحتوى و(للمستندات الموجودة في SharePoint OneDrive) أدخل معرف أصل لكل عنصر. في هذا المثال، معرف الأصل هو اسم منتج أو تعليمة برمجية تستخدمها المؤسسة. ثم يتم تعيين تسمية استبقاء لكل سجل من سجلات المنتج، ويحتوي كل سجل على خاصية تحتوي على معرف أصل. يمثل الرسم التخطيطي **كل المحتوى لكافة** سجلات المنتجات في مؤسسة، ويحمل كل عنصر معرف أصل المنتج الذي يكون سجله. 
    
3. مدة بقاء المنتج هي نوع الحدث؛ منتج معين يصل إلى نهاية العمر الافتراضي هو حدث. عند حدوث حدث من هذا النوع من الأحداث، في هذه الحالة، عندما يصل المنتج إلى نهاية عمره الافتراضي، يمكنك إنشاء حدث يحدد:
    
   - معرف أصل (للمستندات SharePoint والمستندات OneDrive)
    
   - الكلمات الأساسية (للعناصر Exchange). في هذا المثال، تستخدم المؤسسة رمز منتج في الرسائل التي تحتوي على سجلات المنتجات، بحيث تكون الكلمة الأساسية لعناصر Exchange وظيفيا مثل معرف الأصل SharePoint والمستندات OneDrive.
    
   - تاريخ وقوع الحدث. يتم استخدام هذا التاريخ كبداية لفترة الاستبقاء. يمكن أن يكون هذا التاريخ هو التاريخ الحالي أو الماضي أو التاريخ المستقبلي.

4. بعد إنشاء حدث، تتم مزامنة تاريخ الحدث هذا مع كافة المحتويات التي تحتوي على تسمية استبقاء لنوع الحدث هذا وتحتوي على معرف الأصل أو الكلمة الأساسية المحددة. مثل أي تسمية استبقاء، يمكن أن تستغرق هذه المزامنة ما يصل إلى سبعة أيام. في الرسم التخطيطي السابق، يتم تشغيل فترة الاستبقاء لكافة العناصر الدائرة باللون الأحمر بواسطة هذا الحدث. بمعنى آخر، عندما يصل هذا المنتج إلى نهاية عمره الافتراضي، يشغل هذا الحدث فترة الاستبقاء لسجلات هذا المنتج.

من المهم أن نفهم أنه إذا لم تحدد معرف أصل أو كلمات أساسية لحدث ما، فإن **كل المحتوى** الذي يحتوي على تسمية استبقاء لنوع الحدث هذا سيكون له فترة استبقاء يتم تشغيلها بواسطة الحدث. وهذا يعني أنه في الرسم التخطيطي السابق، سيبدأ الاحتفاظ بكافة المحتويات. قد لا يكون هذا ما تنوي القيام به.

وأخيرا، تذكر أن كل تسمية استبقاء لها إعدادات الاستبقاء الخاصة بها. في هذا المثال، تحدد جميعها 10 سنوات، ولكن من الممكن لحدث ما تشغيل تسميات الاستبقاء حيث يكون لكل تسمية فترة استبقاء مختلفة.
  
## <a name="how-to-set-up-event-driven-retention"></a>كيفية إعداد الاستبقاء المستند إلى الحدث

سير عمل عالي المستوى للاستبقاء المستند إلى الحدث:
  
![رسم تخطيطي لسير العمل لإعداد الاستبقاء المستند إلى الحدث.](../media/event-based-retention-process.png)
  
> [!TIP]
> راجع [استخدام تسميات الاستبقاء لإدارة دورة حياة المستندات المخزنة في SharePoint](auto-apply-retention-labels-scenario.md) لسيناريو مفصل حول استخدام الخصائص المدارة في SharePoint لتطبيق تسميات الاستبقاء تلقائيا وتنفيذ الاستبقاء المستند إلى الحدث.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>الخطوة 1: إنشاء تسمية تستند فترة استبقاءها إلى حدث

لإنشاء تسمية الاستبقاء وتكوينها، راجع إرشادات [إنشاء تسميات استبقاء لإدارة السجلات](file-plan-manager.md#create-retention-labels) ، أو [كيفية إنشاء تسميات استبقاء لإدارة دورة حياة البيانات](create-retention-labels-data-lifecycle-management.md). ولكن خاصة بالاحتفاظ المستند إلى الحدث، في الصفحة **"تعريف إعدادات الاستبقاء** " عند إنشاء تسمية الاستبقاء، بعد **بدء فترة الاستبقاء استنادا إلى**، حدد أحد أنواع الأحداث الافتراضية من القائمة المنسدلة، أو أنشئ نوع الحدث الخاص بك عن طريق تحديد **"إنشاء نوع حدث جديد**":

![إنشاء نوع حدث جديد لتسمية استبقاء.](../media/SPRetention6.png)

نوع الحدث هو ببساطة وصف عام لحدث تريد إقرانه بتسمية استبقاء.

تحتوي أنواع الأحداث الافتراضية **على (نوع الحدث)** بعد اسمها في القائمة المنسدلة لتسهيل التعرف عليها، ويمكنك أيضا رؤية نوع الحدث وإنشاءه من علامة التبويب **"سجلات** **managementEvents** > " > **إدارة أنواع الأحداث**.

يتطلب الاستبقاء المستند إلى الحدث إعدادات الاستبقاء التي:
  
- الاحتفاظ بالمحتوى.
    
- احذف المحتوى تلقائيا أو قم بتشغيل مراجعة الترتيب في نهاية فترة الاستبقاء.
  
عادة ما يتم استخدام الاستبقاء المستند إلى الحدث للمحتوى الذي تم الإعلان عنه كسجل، لذلك هذا هو الوقت المناسب للتحقق مما إذا كنت بحاجة أيضا إلى تحديد الخيار الذي يضع علامة على المحتوى [كسجل](records-management.md#records).

إذا كنت تستخدم نوع حدث موجود بدلا من إنشاء نوع حدث جديد، فانتقل إلى الخطوة 3.

> [!NOTE]
> بعد اختيار نوع حدث وحفظ تسمية الاستبقاء، لا يمكن تغيير نوع الحدث.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>الخطوة 2: إنشاء نوع حدث جديد للتسمية

بالنسبة لإعدادات الاستبقاء، إذا حددت **"إنشاء نوع حدث جديد**"، أدخل اسما ووصفا لنوع الحدث. ثم حدد **"التالي**" و" **إرسال**" و" **تم**".

مرة أخرى في الصفحة **"تعريف إعدادات الاستبقاء** "، **لبدء فترة الاستبقاء استنادا إلى**، استخدم القائمة المنسدلة لتحديد نوع الحدث الذي قمت بإنشائه.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>الخطوة 3: نشر تسميات الاستبقاء المستندة إلى الحدث أو تطبيقها تلقائيا

تماما مثل أي تسمية استبقاء، تحتاج إلى نشر تسمية مستندة إلى الحدث أو تطبيقها تلقائيا، ليتم تطبيقها يدويا أو تلقائيا على المحتوى:
- [نشر تسميات الاستبقاء وتطبيقها في التطبيقات](create-apply-retention-labels.md)
- [تطبيق تسمية استبقاء على المحتوى تلقائيا](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>الخطوة 4: إدخال معرف أصل

بعد تطبيق تسمية مستندة إلى الحدث على المحتوى، يمكنك إدخال معرف أصل لكل عنصر. على سبيل المثال، قد تستخدم مؤسستك:
  
- رموز المنتجات التي يمكنك استخدامها للاحتفاظ بالمحتوى لمنتج معين فقط.
    
- Project التعليمات البرمجية التي يمكنك استخدامها للاحتفاظ بالمحتوى لمشروع معين فقط.
    
- معرفات الموظفين التي يمكنك استخدامها للاحتفاظ بالمحتوى لشخص معين فقط.
    
معرف الأصل هو ببساطة خاصية مستند أخرى متوفرة في SharePoint OneDrive. قد تستخدم مؤسستك بالفعل خصائص ومعرفات مستندات أخرى لتصنيف المحتوى. إذا كان الأمر كذلك، يمكنك أيضا استخدام هذه الخصائص والقيم عند إنشاء حدث— راجع الخطوة 6 التالية. النقطة المهمة هي أنه يجب عليك استخدام مجموعة *خصائص:قيمة* في خصائص المستند لإقران هذا العنصر بنوع حدث.
  
![مربع نص لإدخال معرف أصل.](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>الخطوة 5: إنشاء حدث

عند حدوث مثيل معين من هذا النوع من الأحداث، مثل وصول منتج إلى نهاية عمره الافتراضي، انتقل إلى صفحة **إدارة** >  **السجلات** في مدخل توافق Microsoft Purview، وحدد **+ Create** لإنشاء حدث. يمكنك تشغيل الحدث عن طريق إنشائه، هنا.

![إنشاء حدث لتشغيل بدء الاستبقاء لتسميات الاستبقاء المستندة إلى الحدث.](../media/create-event-records-management.png)

يتم دعم ما يصل إلى مليون حدث لكل مستأجر.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>الخطوة 6: اختر نوع الحدث نفسه المستخدم بواسطة التسمية في الخطوة 2

عند إنشاء الحدث، اختر نوع الحدث نفسه المحدد في إعدادات تسمية الاستبقاء في الخطوة 2. على سبيل المثال، إذا حددت **"مدة بقاء المنتج"** كنوع الحدث لإعدادات التسمية، فحدد **"مدة بقاء المنتج"** عند إنشاء الحدث. سيتم تشغيل فترة الاستبقاء الخاصة به فقط مع تسميات الاستبقاء المطبقة عليه من نوع الحدث هذا.

![الخيار في إعدادات الحدث لاختيار نوع حدث.](../media/choose-event-type-records-management.png)

بدلا من ذلك، إذا كنت بحاجة إلى إنشاء حدث لتسميات استبقاء متعددة تحتوي على أنواع أحداث مختلفة، فحدد الخيار **"اختيار التسميات الموجودة** ". ثم حدد التسميات التي تم تكوينها لأنواع الأحداث التي تريد إقرانها بهذا الحدث.

### <a name="step-7-enter-keywords-or-query-for-exchange-asset-id-for-sharepoint-and-onedrive"></a>الخطوة 7: أدخل الكلمات الأساسية أو الاستعلام عن Exchange ومعرف الأصل SharePoint OneDrive

الآن يمكنك تضييق نطاق المحتوى. بالنسبة Exchange المحتوى، يمكنك القيام بذلك عن طريق تحديد كلمات أساسية أو استعلام. بالنسبة SharePoint والمحتوى OneDrive، يمكنك القيام بذلك عن طريق تحديد معرفات الأصول.

بالنسبة لعناصر Exchange، استخدم الكلمات الأساسية أو استعلام يستخدم لغة استعلام الكلمات الأساسية (KQL). لمزيد من المعلومات حول بناء جملة الاستعلام، راجع [مرجع بناء جملة لغة استعلام الكلمات الأساسية (KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)). لمزيد من المعلومات حول الخصائص القابلة للبحث التي يمكنك استخدامها Exchange، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md).

بالنسبة لمعرفات الأصول، سيتم فرض الاستبقاء فقط على المحتوى ذي الخاصية المحددة *:زوج القيمة* . على سبيل المثال، إذا كنت تستخدم خاصية "معرف الأصل"، أدخل `ComplianceAssetID:<value>` مربع معرفات الأصول المعروضة في الصورة التالية.

إذا لم يتم إدخال معرف أصل، يتم تطبيق نفس تاريخ الاستبقاء على كل المحتويات التي تحتوي على تسميات من نوع الحدث هذا.

قد تكون مؤسستك قد طبقت خصائص ومعرفات أخرى على المستندات المتعلقة بنوع الحدث هذا. على سبيل المثال، إذا كنت بحاجة إلى الكشف عن سجلات منتج معين، فقد يكون المعرف مزيجا من معرف الخاصية المخصصة وقيمة "XYZ". في هذه الحالة، يمكنك إدخال `ProductID:XYZ` مربع معرفات الأصول المعروضة في الصورة التالية.

وأخيرا، اختر تاريخ وقوع الحدث؛ يتم استخدام هذا التاريخ كبداية لفترة الاستبقاء. بعد إنشاء حدث، تتم مزامنة تاريخ الحدث هذا مع كل المحتوى مع تسمية استبقاء لنوع الحدث ومعرف الأصل والكلمات الأساسية أو الاستعلامات. كما هو الحال مع أي تسمية استبقاء، يمكن أن تستغرق هذه المزامنة ما يصل إلى سبعة أيام.
  
![صفحة إعدادات الحدث.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

بعد إنشاء حدث، تكون إعدادات الاستبقاء سارية المفعول للمحتوى الذي تمت تسميته ومفهرسته بالفعل. إذا تمت إضافة تسمية الاستبقاء إلى محتوى جديد بعد إنشاء الحدث، يجب إنشاء حدث جديد بنفس التفاصيل.

لا يؤدي حذف حدث إلى إلغاء إعدادات الاستبقاء التي أصبحت سارية الآن للمحتوى الذي تمت تسميته بالفعل. حاليا، لا يمكنك إلغاء الأحداث بعد تشغيلها.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>استخدام البحث عن المحتوى للبحث عن المحتوى بالكامل باستخدام تسمية معينة أو معرف أصل معين

بعد تعيين تسميات الاستبقاء إلى المحتوى، يمكنك استخدام البحث عن المحتوى للعثور على كافة المحتويات المصنفة مع تسمية استبقاء معينة أو التي تحتوي على معرف أصل معين:
  
- للبحث عن كافة المحتويات التي تحتوي على تسمية استبقاء معينة، اختر شرط **تسمية الاستبقاء** ، ثم أدخل اسم التسمية الكامل أو جزء من اسم التسمية واستخدم حرف بدل. 
    
- للبحث عن كافة المحتويات ذات معرف أصل معين، أدخل الخاصية **ComplianceAssetID** وقيمة، باستخدام التنسيق `ComplianceAssetID:<value>`. 
    
لمزيد من المعلومات، راجع [استعلامات الكلمات الأساسية وشروط البحث في البحث عن المحتوى](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>أتمتة الأحداث باستخدام PowerShell

يمكنك استخدام برنامج نصي PowerShell لأتمتة الاستبقاء المستند إلى الحدث من تطبيقات عملك. أوامر PowerShell cmdlets المتوفرة للاستبقاء المستند إلى الحدث:
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

## <a name="automate-events-by-using-a-rest-api"></a>أتمتة الأحداث باستخدام واجهة برمجة تطبيقات REST

يمكنك استخدام واجهة برمجة تطبيقات REST لإنشاء الأحداث التي تشغل بداية وقت الاستبقاء تلقائيا.

واجهة برمجة تطبيقات REST هي نقطة نهاية خدمة تدعم مجموعات من عمليات HTTP (الأساليب)، والتي توفر الوصول إلى موارد الخدمة لإنشاء/استرداد/تحديث/حذف. لمزيد من المعلومات، راجع [مكونات طلب/استجابة واجهة برمجة تطبيقات REST](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). باستخدام واجهة برمجة تطبيقات REST Microsoft 365، يمكن إنشاء الأحداث واستردادها باستخدام أساليب POST و GET.

هناك خياران لاستخدام واجهة برمجة تطبيقات REST:

- **Power Automate Microsoft أو تطبيقا مشابها** لتشغيل حدوث حدث تلقائيا. Microsoft Power Automate هو منسق للاتصال بأنظمة أخرى، لذلك لا تحتاج إلى كتابة حل مخصص. لمزيد من المعلومات، راجع [موقع ويب Power Automate](https://flow.microsoft.com/en-us/).

- **PowerShell أو عميل HTTP لاستدعاء واجهة برمجة تطبيقات REST** لإنشاء الأحداث باستخدام PowerShell (الإصدار 6 أو أحدث)، والذي يعد جزءا من حل مخصص.

قبل استخدام واجهة برمجة تطبيقات REST، كمسؤول عام، قم بتأكيد عنوان URL لاستخدامه لاستدعاء حدث الاستبقاء. للقيام بذلك، قم بتشغيل استدعاء حدث استبقاء GET باستخدام عنوان URL لواجهة برمجة تطبيقات REST:

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

تحقق من رمز الاستجابة. إذا كان 302، فاحصل على عنوان URL المعاد توجيهه من خاصية الموقع لرأس الاستجابة واستخدم عنوان URL هذا بدلا من `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` الإرشادات التالية.

يمكن تأكيد الأحداث التي يتم إنشاؤها تلقائيا من خلال عرضها في مدخل توافق Microsoft Purview > **Records** **managementEvents** >  .

### <a name="use-microsoft-power-automate-to-create-the-event"></a>استخدام Microsoft Power Automate لإنشاء الحدث

إنشاء تدفق يقوم بإنشاء حدث باستخدام واجهة برمجة تطبيقات REST Microsoft 365:

![استخدام Flow لإنشاء حدث.](../media/automate-event-driven-retention-flow-1.png)

![استخدام التدفق لاستدعاء واجهة برمجة تطبيقات REST.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>إنشاء حدث

نموذج التعليمات البرمجية لاستدعاء واجهة برمجة تطبيقات REST:

- **الأسلوب**: POST
- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **الرؤوس**: Key = Content-Type, Value = application/atom+xml
- **النص الأساسي**:

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
- **اسم المستخدم**: "Complianceuser"
- **كلمة المرور**: "Compliancepassword"


##### <a name="available-parameters"></a>المعلمات المتوفرة


|معلمات|الوصف|ملاحظات|
|--- |--- |--- |
|<d:Name></d:Name>|توفير اسم فريد للحدث،|لا يمكن أن تحتوي على مسافات زائدة أو الأحرف التالية: ٪ * \ & < \> \| # ؟ , : ;|
|<d:EventType></d:EventType>|أدخل اسم نوع الحدث (أو Guid)،|مثال: "إنهاء الموظف". يجب أن يقترن نوع الحدث بتسمية استبقاء.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|أدخل "ComplianceAssetId:" + معرف الموظف|مثال: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|تاريخ الحدث ووقته|التنسيق: yyyy-MM-ddTHH:mm:ssZ، مثال: 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف       |
| ----------------- | --------------------- |
| 302               | اعاده توجيه              |
| 201               | انشاء               |
| 403               | فشل التخويل  |
| 401               | فشل المصادقة |

##### <a name="get-events-based-on-a-time-range"></a>الحصول على الأحداث استنادا إلى نطاق زمني

- **الأسلوب**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **الرؤوس**: Key = Content-Type, Value = application/atom+xml

- **المصادقة**: أساسي

- **اسم المستخدم**: "Complianceuser"

- **كلمة المرور**: "Compliancepassword"

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف                   |
| ----------------- | --------------------------------- |
| 200               | حسنا، قائمة بالأحداث في atom+ xml |
| 404               | لم يتم العثور على                         |
| 302               | اعاده توجيه                          |
| 401               | فشل التخويل              |
| 403               | فشل المصادقة             |

##### <a name="get-an-event-by-id"></a>الحصول على حدث حسب المعرف

- **الأسلوب**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **الرؤوس**: Key = Content-Type, Value = application/atom+xml

- **المصادقة**: أساسي

- **اسم المستخدم**: "Complianceuser"

- **كلمة المرور**: "Compliancepassword"

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | حسنا، يحتوي نص الاستجابة على الحدث في atom+xml |
| 404               | لم يتم العثور على                                            |
| 302               | اعاده توجيه                                             |
| 401               | فشل التخويل                                 |
| 403               | فشل المصادقة                                |

##### <a name="get-an-event-by-name"></a>الحصول على حدث بالاسم

- **الأسلوب**: GET

- **URL**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **الرؤوس**: Key = Content-Type, Value = application/atom+xml

- **المصادقة**: أساسي

- **اسم المستخدم**: "Complianceuser"

- **كلمة المرور**: "Compliancepassword"

###### <a name="response-codes"></a>رموز الاستجابة

| رمز الاستجابة | الوصف                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | حسنا، يحتوي نص الاستجابة على الحدث في atom+xml |
| 404               | لم يتم العثور على                                            |
| 302               | اعاده توجيه                                             |
| 401               | فشل التخويل                                 |
| 403               | فشل المصادقة                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>استخدام PowerShell أو أي عميل HTTP لإنشاء الحدث

يجب أن يكون PowerShell الإصدار 6 أو أحدث.

في جلسة عمل PowerShell، قم بتشغيل البرنامج النصي التالي:

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
