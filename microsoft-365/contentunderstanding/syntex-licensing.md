---
title: ترخيص SharePoint Syntex
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: high
description: تعرف على ترخيص SharePoint Syntex
ms.openlocfilehash: 31b10c0107bf871f827244889ac7ec77f7958e1f
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787485"
---
# <a name="licensing-for-sharepoint-syntex"></a>ترخيص SharePoint Syntex

لاستخدام SharePoint Syntex، يجب أن يكون لكل مستخدم Syntex ترخيص له. إذا قمت بإلغاء تراخيص SharePoint Syntex في تاريخ مستقبلي (أو تنتهي صلاحية الإصدار التجريبي)، فلن يتمكن المستخدمون من إنشاء نماذج فهم المستندات أو نماذج معالجة النماذج أو نشرها أو تشغيلها. بالإضافة إلى ذلك، لن تتوفر تقارير مخزن المصطلحات واستيراد تصنيف SKOS ودفع نوع المحتوى. لن يتم حذف أي نماذج أو محتوى أو بيانات تعريف ولن يتم تغيير أذونات الموقع.
 
> [!NOTE] 
> SharePoint Syntex هو ترخيص وظيفة إضافية ويتطلب من المستخدمين أيضا الحصول على ترخيص ل Microsoft 365.
 
## <a name="tasks-requiring-a-license"></a>المهام التي تتطلب ترخيصا
 
تتطلب المهام التالية [ترخيصا SharePoint Syntex](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex) للمستخدم الذي يقوم بتنفيذها:
 
- تطبيق نموذج فهم المستند على مكتبة. (يمكن منح المستخدمين غير المرخصين حق الوصول إلى مركز محتوى ويمكنهم إنشاء نماذج لفهم المستندات هناك ولكن لا يمكنهم تطبيقها على مكتبة مستندات.)
- إنشاء نموذج معالجة نموذج عبر نقطة الإدخال في مكتبة
- تحميل المحتوى إلى مكتبة حيث تم تطبيق نموذج فهم المستند أو معالجة النموذج
- تشغيل نموذج فهم المستند عند الطلب
- استخدام خدمات التصنيف المتميزة. (تتضمن خدمات التصنيف المتميزة استيراد مجموعة المصطلحات المستندة إلى SKOS، ودفع أنواع محتويات المؤسسة إلى المواقع المرتبطة بالمركز، وتقارير مخزن المصطلحات.)

يمكن منح المستخدمين غير المرخصين حق الوصول إلى مركز محتوى ويمكنهم إنشاء نماذج لفهم المستندات هناك ولكن لا يمكنهم تطبيقها على مكتبة مستندات.
 
## <a name="cost-of-training-and-running-models"></a>تكلفة التدريب وتشغيل النماذج
 
يتم تضمين تكلفة تدريب وتشغيل نماذج فهم المستندات في تكلفة ترخيص SharePoint Syntex. ومع ذلك، تستخدم نماذج معالجة النماذج سعة الذكاء الاصطناعي Builder، لكل من التدريب ومعالجة وقت التشغيل. يجب تخصيص السعة لبيئة Power Apps حيث ستستخدم الذكاء الاصطناعي Builder.

لكل ترخيص SharePoint Syntex، يتم تخصيص 3500 الذكاء الاصطناعي رصيد منشئ لكل ترخيص، لكل شهر مجمع على مستوى المستأجر، مع تخصيص 1 مليون رصيد كحد أقصى شهريا. يتم تجديد هذا التخصيص كل شهر لكل ترخيص SharePoint Syntex نشط. (لا يتم ترحيل الأرصدة غير المستخدمة من شهر إلى شهر.) 

يمكنك تقدير سعة الذكاء الاصطناعي Builder المناسبة لك باستخدام [حاسبة الذكاء الاصطناعي Builder](https://powerapps.microsoft.com/ai-builder-calculator).

إذا كنت تخطط لاستخدام بيئة Power Platform مخصصة، يجب [تخصيص الأرصدة لتلك البيئة](/power-platform/admin/capacity-add-on).

انتقل إلى [مركز إدارة Power Platform](https://admin.powerplatform.microsoft.com/resources/capacity) للتحقق من رصيدك واستخدامك.
  
## <a name="additional-term-store-features"></a>ميزات مخزن المصطلحات الإضافية
 
يتميز الاشتراك في SharePoint Syntex بميزات مخزن المصطلحات الإضافية التالية:
 
- استيراد مجموعة المصطلحات المستندة إلى SKOS
- دفع أنواع محتويات المؤسسة إلى موقع مركز، والذي يضيفها أيضا إلى المواقع المقترنة وأي قوائم أو مكتبات تم إنشاؤها حديثا
- توفر تقارير مخزن المصطلحات رؤى حول مجموعات المصطلحات المنشورة واستخدامها عبر المستأجر


## <a name="see-also"></a>راجع أيضًا

[نظرة عامة على الترخيص ل Microsoft Power Platform](/power-platform/admin/pricing-billing-skus)

[الأسئلة المتداولة حول ترخيص Power Apps وPower Automate](/power-platform/admin/powerapps-flow-licensing-faq)
