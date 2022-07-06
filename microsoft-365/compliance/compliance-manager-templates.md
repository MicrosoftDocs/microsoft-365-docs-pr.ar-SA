---
title: تعرف على قوالب التقييم في Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: فهم كيفية استخدام وإدارة القوالب لإنشاء التقييمات في Microsoft Purview Compliance Manager. إنشاء قوالب وتعديلها باستخدام ملف Excel منسق.
ms.openlocfilehash: ac4d3fb6f7a43aa642b9d8b343a68c9f38f29e25
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635634"
---
# <a name="learn-about-assessment-templates-in-compliance-manager"></a>التعرف على قوالب التقييم في Compliance Manager

**في هذه المقالة:** فهم **كيفية عمل القوالب** **وكيفية إدارتها** من صفحة قوالب التقييم. احصل على إرشادات **لإنشاء** قوالب جديدة **، وتوسيع القوالب** الموجودة **وتعديلها** ، **وتنسيق بيانات القالب باستخدام Excel**، وتصدير **تقارير** القوالب.

> [!IMPORTANT]
> تعتمد قوالب التقييم المتوفرة لمؤسستك على اتفاقية الترخيص الخاصة بك. [راجع التفاصيل](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-compliance-manager).

## <a name="templates-overview"></a>نظرة عامة على القوالب

القالب هو إطار من عناصر التحكم لإنشاء تقييم في Compliance Manager. يمكن أن تساعد مجموعتنا الشاملة من القوالب مؤسستك على الامتثال للمتطلبات الوطنية والإقليمية والمتطلبات الخاصة بالصناعة التي تحكم جمع البيانات واستخدامها. نشير إلى قوالب بنفس اسم المصادقة أو اللوائح الأساسية، مثل قالب القانون العام لحماية البيانات في الاتحاد الأوروبي وقالب ISO/IEC 27701:2019.

## <a name="template-versions-microsoft-and-universal"></a>إصدارات القالب: Microsoft و Universal

يمكن استخدام "إدارة التوافق" لتقييم أنواع مختلفة من المنتجات. تأتي جميع القوالب، باستثناء القالب الافتراضي ل [Microsoft Data Protection Baseline](compliance-manager-assessments.md#data-protection-baseline-default-assessment) ، في إصدارين:

1. إصدار ينطبق على منتج محدد مسبقا، مثل Microsoft 365، و
2. إصدار عالمي يمكن تصميمه ليناسب المنتجات الأخرى.

يتم تعميم التقييمات من القوالب العالمية بشكل أكبر ولكنها توفر تنوعا موسعا، لأنها يمكن أن تساعدك على تتبع امتثال مؤسستك بسهولة عبر منتجات متعددة.

تجدر الإشارة إلى أنه لا يمكن لعملاء مجتمع حكومة الولايات المتحدة (GCC) Moderate و GCC High و وزارة الدفاع (DoD) استخدام القوالب العالمية حاليا.

## <a name="template-availability-and-licensing"></a>توفر القالب والترخيص

هناك فئتان من القوالب في Compliance Manager: مضمنة ومتميزة.

1. يتم منح **القوالب المضمنة** بواسطة ترخيص Compliance Manager الخاص بك وتغطى اللوائح والمتطلبات الرئيسية. لمعرفة المزيد حول القوالب المتوفرة بموجب اتفاقية الترخيص، راجع [تفاصيل الترخيص](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).
2. يمكن الحصول على **قوالب Premium** لتغطية الاحتياجات والسيناريوهات الإضافية عن طريق شراء تراخيص القوالب.

عندما تبدأ في إنشاء التقييمات، سيتعقب Compliance Manager عدد القوالب النشطة حتى تتمكن من مراقبة استخدامك. لمعرفة المزيد، راجع [القوالب النشطة وغير النشطة](compliance-manager-templates.md#active-and-inactive-templates).

عرض [القائمة الكاملة للقوالب](compliance-manager-templates-list.md) المتوفرة في Compliance Manager.

### <a name="purchase-premium-template-licenses"></a>شراء تراخيص القوالب المتميزة

يمكن الحصول على تراخيص القوالب باستخدام أسلوب واحد أو أكثر من هذه الأساليب، اعتمادا على اتفاقية ترخيص Compliance Manager. بمجرد الانتهاء من عملية الشراء، يجب أن تصبح القوالب متوفرة في المستأجر الخاص بك في غضون 48 ساعة.

**متوسط تجاري ومتوسط في GCC**

يمكن للحسابات التجارية وحسابات GCC Moderate شراء تراخيص القوالب في مركز الإدارة ([تعرف على المزيد حول الاشتراكات والتراخيص والفوترة](/microsoft-365/commerce/)). حدد كمية التراخيص التي ترغب في شرائها وخطة الدفع الخاصة بك.

ارتباطات الشراء:

- [التجاريه](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/46E9BF2A-3C8D-4A69-A7E7-3DA04687636D)
- [GCC Moderate](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/3129986d-5f4b-413b-a34b-b706db5a7669)

يمكنك أيضا الحصول على تراخيص من خلال مشاركتك في [برنامج موفر حلول السحابة](https://partner.microsoft.com/membership/cloud-solution-provider) أو [الترخيص المجمع](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

**حسابات GCC High و DOD**

يجب على حسابات GCC High و DOD شراء تراخيص القوالب من خلال [الترخيص المجمع](https://www.microsoft.com/licensing/licensing-programs/licensing-programs).

### <a name="try-out-premium-templates"></a>تجربة القوالب المتميزة

لتجربة القوالب المتميزة قبل إجراء عملية شراء، يمكنك أيضا الحصول على إصدارات تجريبية من التراخيص. تعد التراخيص التجريبية مناسبة لما يصل إلى 25 قالبا لمدة 90 يوما. بمجرد الحصول على الترخيص التجريبي، يجب أن تصبح القوالب متوفرة في المستأجر الخاص بك في غضون 48 ساعة.

إذا كانت مؤسستك تملك ترخيصا تجاريا ل Compliance Manager، يمكنك معرفة كيفية بدء الإصدار التجريبي في [حول الإصدار التجريبي المجاني للتقييمات المتميزة ل Microsoft Purview Compliance Manager](compliance-easy-trials-compliance-manager-assessments.md).

إذا كانت مؤسستك ضمن ترخيص GCC أو DOD، فاختر رابط الإصدار التجريبي المناسب لمؤسستك:

- [GCC Moderate](https://admin.microsoft.com/Adminportal/Home?#/catalog/offer-details/compliance-manager-premium-assessment-add-on/87ed2908-0a8d-430a-9635-558ed42b581f)
- [GCC High](https://portal.office365.us/SubscriptionDetails?OfferId=e14362d7-2c11-4a43-9c92-59f1b499b96a)
- [وزاره الدفاع](https://portal.apps.mil/Commerce/Trial.aspx?OfferId=17e28290-7de6-41a9-af30-f6497396ab2e)

#### <a name="active-and-inactive-templates"></a>القوالب النشطة وغير النشطة

ستعرض القوالب حالة التنشيط إما نشطة أو غير نشطة:

- يعتبر القالب **نشطا** بمجرد إنشاء تقييم من هذا القالب.
- يعتبر القالب **غير نشط** إذا لم تكن مؤسستك تستخدمه للتقييم.

إذا قمت بربط أي تقييمات بقالب متميز تم شراؤه، فسيكون هذا القالب نشطا لمدة عام واحد. سيتم تجديد عملية الشراء تلقائيا ما لم تقم بالإلغاء.

#### <a name="activated-templates-counter"></a>عداد القوالب المنشطة

تحتوي صفحة التقييم وصفحة قوالب التقييم على عداد **قوالب تم تنشيطه** بالقرب من الأعلى. يعرض العداد عدد القوالب المستخدمة من الرقم المؤهل لاستخدامه وفقا لاتفاقية الترخيص الخاصة بك. يتم حساب استخدام القالب على مستوى الشهادة.

على سبيل المثال، إذا كان العداد يعرض 2/5، فهذا يعني أن مؤسستك قامت بتنشيط قالبين من بين 5 قوالب متوفرة للاستخدام.

إذا كان العداد يظهر 5/2، فهذا يشير إلى أن مؤسستك تتجاوز حدودها وتحتاج إلى شراء 3 قوالب متميزة قيد الاستخدام.

تحتوي القوالب لمنتج محدد مسبقا، مثل Microsoft 365، على ترخيص مشترك مع الإصدارات العالمية من نفس القالب. يمكنك هذا من استخدام نفس الشهادة الأساسية عبر أكثر من منتج واحد. سيتم حساب استخدام أي من الإصدارين أو كليهما من نفس القالب كقالب واحد تم تنشيطه فقط.

لمزيد من التفاصيل، راجع [إرشادات ترخيص Compliance Manager](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#compliance-manager).

## <a name="view-and-manage-templates"></a>عرض القوالب وإدارتها

تعرض صفحة قوالب التقييم في Compliance Manager قائمة بالقوالب والتفاصيل الرئيسية حولها. تتضمن القائمة قوالب يوفرها Compliance Manager بالإضافة إلى أي قوالب قامت مؤسستك بتعديلها أو إنشائها. يمكنك تطبيق عوامل التصفية للعثور على قالب يستند إلى الشهادة ونطاق المنتج والبلد والصناعة ومن أنشأه وما إذا كان القالب ممكنا لإنشاء التقييم.

حدد قالبا من صفه لإظهار صفحة التفاصيل الخاصة به. تحتوي هذه الصفحة على وصف للقالب ومعلومات إضافية حول تفاصيل المصادقة والنطاق وعناصر التحكم. من هذه الصفحة، يمكنك تحديد الأزرار المناسبة لإنشاء تقييم أو تصدير بيانات القالب إلى Excel أو تعديل القالب.

## <a name="create-an-assessment-template"></a>إنشاء قالب تقييم

لإنشاء قالب جديد خاص بك للتقييمات المخصصة في Compliance Manager، ستستخدم جدول بيانات Excel منسقا بشكل خاص لتجميع بيانات التحكم الضرورية. بعد إكمال جدول البيانات، ستقوم باستيراده إلى Compliance Manager. لمعرفة المزيد، راجع [إنشاء قالب تقييم](compliance-manager-templates-create.md).

## <a name="modify-an-assessment-template"></a>تعديل قالب تقييم

عند العمل مع التقييمات في Compliance Manager، قد تحتاج إلى تعديل قالب تقييم قمت بإنشائه. تشبه العملية عملية إنشاء القالب حيث ستقوم بتحميل ملف Excel منسق مع بيانات القالب. لمعرفة المزيد حول كيفية إجراء تغييرات وكيفية الاحتفاظ بالبيانات التي لا تزال ترغب في الاحتفاظ بها، راجع [تعديل قالب تقييم](compliance-manager-templates-modify.md).

## <a name="extend-an-assessment-template"></a>توسيع قالب تقييم

يوفر Compliance Manager خيار إضافة عناصر التحكم الخاصة بك وإجراءات التحسين إلى قالب موجود. تسمى هذه العملية توسيع قالب. لتوسيع قالب، ستستخدم إرشادات خاصة لإضافة بيانات القالب، اعتمادا على ما إذا كنت تقوم بتوسيع قوالب تقييم Microsoft أو قوالب التقييم العالمية. لمعرفة المزيد، راجع ["توسيع قالب تقييم](compliance-manager-templates-extend.md)".

## <a name="format-assessment-template-data-in-excel"></a>تنسيق بيانات قالب التقييم في Excel

عند إنشاء قوالب التقييم أو تعديلها أو توسيعها في Compliance Manager، ستعمل مع جداول بيانات Excel التي تستخدم تنسيقا ومخططا محددين. يجب اتباع هذه المواصفات حتى يتم استيراد الملفات بشكل صحيح. لمعرفة المزيد، راجع [تنسيق بيانات قالب التقييم في Excel](compliance-manager-templates-format-excel.md).

## <a name="export-a-template"></a>تصدير قالب

يمكنك تصدير ملف Excel يحتوي على كافة بيانات القالب. ستحتاج إلى تصدير قالب لتعديله، لأن هذا سيكون ملف Excel الذي تقوم بتحريره وتحميله في [عملية التعديل](compliance-manager-templates-modify.md). يمكنك أيضا تصدير قالب للرجوع إليه إذا كنت تريد استخدام بيانات منه أثناء إنشاء قالب مخصص جديد.

لتصدير القالب، انتقل إلى صفحة تفاصيل القالب وحدد الزر **"تصدير إلى Excel** ".

لاحظ أنه عند تصدير قالب قمت بتوسيعه من قالب Compliance Manager، سيحتوي الملف المصدر على السمات التي أضفتها إلى القالب فقط. لن يتضمن الملف الذي تم تصديره بيانات القالب الأصلية التي توفرها Microsoft. للحصول على مثل هذا التقرير، راجع إرشادات [تصدير تقرير تقييم](compliance-manager-assessments.md#export-an-assessment-report).
