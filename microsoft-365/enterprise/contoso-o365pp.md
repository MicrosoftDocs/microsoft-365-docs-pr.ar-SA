---
title: نشر Microsoft 365 Apps for enterprise لشركة Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: فهم كيفية استخدام Contoso Microsoft Endpoint Configuration Manager لنشر Microsoft 365 Apps for enterprise.
ms.openlocfilehash: 8b6fb639083145c728870156d848b75897483d25
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096535"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>نشر Microsoft 365 Apps for enterprise لشركة Contoso

قامت شركة Contoso بترقية أجهزة الكمبيوتر الخاصة بها إلى Windows 10 Enterprise Microsoft 365 Apps for enterprise لتمكين تعاون أكثر فعالية وأمانا أفضل وتجربة سطح مكتب أكثر حداثة. بعد تقييم البنية الأساسية واحتياجات الأعمال، حددت شركة Contoso هذه المتطلبات الرئيسية للنشر:

- يجب تشغيل جميع أجهزة الكمبيوتر Microsoft 365 Apps for enterprise.
- يجب أن يستخدم النشر أدوات الإدارة والبنية الأساسية الحالية عندما يكون ذلك ممكنا.
- يجب أن يدعم النشر لغات متعددة وبنى موجودة على أجهزة المستخدمين.
- يجب أن تظل أجهزة الكمبيوتر محدثة وآمنة مع الحد الأدنى من التكاليف الإدارية لت تكنولوجيا المعلومات والحد الأدنى من التأثير على المستخدمين.

## <a name="deployment-tools"></a>أدوات النشر

استنادا إلى متطلباتها، اختارت Contoso نشر Windows 10 Enterprise Microsoft 365 Apps for enterprise من خلال Configuration Manager (الفرع الحالي). Configuration Manager المقاييس للبيئات الكبيرة ويوفر تحكما واسعا في التثبيت والتحديثات والإعدادات. كما أن لديها ميزات مضمنة لتسهيل نشر Office وإدارتها، بما في ذلك:

- ذاكرة التخزين المؤقت النظيرة، والتي يمكن أن تساعد في سعة شبكة محدودة عند النشر على الأجهزة في المواقع البعيدة.
- لوحة معلومات Office Client Management، والتي تسهل نشر Office التحديثات ومراقبتها وتمنح المسؤولين إمكانية الوصول إلى أحدث ميزات النشر والإدارة.
- نشر حزمة اللغة الذكية، بما في ذلك نشر نفس اللغة تلقائيا مثل نظام التشغيل.
- أسلوب معتمد بالكامل وسهل الاستخدام لإزالة الإصدارات الموجودة من Office من عميل أثناء النشر.

بالإضافة إلى Configuration Manager، استخدمت Contoso [مجموعة أدوات الجاهزية للوظائف الإضافية Office وVBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps)، وهي أداة مجانية من Microsoft، لتقييم مشكلات التوافق مع وحدات الماكرو والوظائف الإضافية Office الخاصة بها.

## <a name="managing-deployment-and-updates"></a>إدارة النشر والتحديثات

يحتوي Microsoft 365 Apps for enterprise على نموذج إصدار جديد: Office كخدمة. يسهل نموذج الخدمة البقاء على اطلاع بالميزات الجديدة. ولكنه غالبا ما يتطلب من أقسام تكنولوجيا المعلومات تغيير كيفية توزيع الإصدارات الجديدة واختبارها. لتقليل مشكلات التوافق وضمان تحديث أجهزة الكمبيوتر الخاصة بها، نشرت شركة Contoso Windows Office على مرحلتين:

- أولا، نشروا Microsoft 365 Apps for enterprise على مجموعة صغيرة من الأجهزة التمثيلية عبر المؤسسة. تم استخدام هذه المجموعة التجريبية لاختبار التطبيقات والوظائف الإضافية والأجهزة باستخدام Microsoft 365 Apps for enterprise.
- بعد أربعة أشهر، بعد معالجة جميع المشكلات الحرجة مع التطبيقات والوظائف الإضافية والأجهزة في مجموعة الإصدار التجريبي، نشرت شركة Contoso Microsoft 365 Apps for enterprise إلى بقية الأجهزة في المؤسسة (المجموعة الواسعة).

بدلا من إدارة تحديثات Office باستخدام Configuration Manager، مكنت Contoso التحديثات التلقائية من السحابة. تقلل التحديثات المستندة إلى السحابة من النفقات الإدارية مع التأكد من أن الأجهزة تبقى محدثة.

اتبعت شركة Contoso نفس النهج المكون من مرحلتين لتحديثات الميزات التي استخدمتها لنشر Office: تلقت الأجهزة في مجموعة الإصدار التجريبي تحديثات الميزات قبل أربعة أشهر من الأجهزة الموجودة في بقية المؤسسة (المجموعة الواسعة). لتمكين هذا Office، استخدمت شركة Contoso [قناتي تحديث](/DeployOffice/overview-update-channels) موصى بهما:

- Semi-Annual قناة المؤسسة (معاينة) لتحديثات المجموعة التجريبية
- Semi-Annual قناة المؤسسة لتحديثات المجموعة الواسعة

نظرا لأن Semi-Annual Enterprise Channel (Preview) يصدر إصدارا من Microsoft 365 Apps for enterprise أربعة أشهر قبل Semi-Annual Enterprise Channel، فإن Contoso لديها الوقت للتحقق من صحة التحديثات دون الحاجة إلى إدارتها.

## <a name="deployment-process"></a>عملية التوزيع

لإكمال نشر Office، نفذت شركة Contoso العملية التالية، والتي تتضمن توصيات أفضل الممارسات من Microsoft:

1. قبل التوزيع، استخدمت Contoso مجموعة أدوات الجاهزية للوظيفة الإضافية Office وVBA لاختبار تطبيقاتها ووظائفها الإضافية Office لتقييم توافقها مع Microsoft 365 Apps for enterprise.
1. في Configuration Manager، قاموا بتمكين ذاكرة التخزين المؤقت النظير على أجهزة العميل الخاصة بهم، ما يساعد في سعة شبكة محدودة عند النشر على أجهزة العميل في المواقع البعيدة. 
1. قامت شركة Contoso بتعريف مجموعتي نشر كمجموعات أجهزة في Configuration Manager: مجموعة تجريبية ومجموعة واسعة. تم استخدام مجموعة الإصدار التجريبي، التي تضمنت مجموعة صغيرة من الأجهزة التمثيلية عبر المؤسسة، لاختبار إضافي للتطبيقات والوظائف الإضافية والأجهزة باستخدام Windows 10 Enterprise Microsoft 365 Apps for enterprise.
1. لقد قاموا بإنشاء حزم نشر Office باستخدام لوحة معلومات Office Client Management ومعالج مثبت Office 365، اللذين يشكلان جزءا من وحدة التحكم Configuration Manager. لقد قاموا بإنشاء حزمتين Microsoft 365 Apps for enterprise، واحدة للمجموعة التجريبية على قناة المؤسسة Semi-Annual (معاينة) والأخرى للمجموعة الواسعة على قناة المؤسسة Semi-Annual.
2. تتضمن كل حزمة Office حزم اللغات الإنجليزية والفرنسية والألمانية. إذا تطلب أحد الأجهزة لغة لم يتم تضمينها في حزمة Office، يتم تنزيل حزمة اللغة هذه تلقائيا من شبكة تسليم المحتوى Office (CDN).
3. استخدموا الميزة المضمنة في حزمة Office لإزالة كافة إصدارات MSI الموجودة من Office تلقائيا قبل تثبيت Microsoft 365 Apps for enterprise.
4. في Configuration Manager، قاموا بنشر Windows وحزم Office إلى نقاط التوزيع عبر شبكتهم. ثم قاموا بتشغيل تسلسل مهام النشر Configuration Manager لنشر حزمة Microsoft 365 Apps for enterprise التجريبية إلى مجموعة الإصدار التجريبي.
5. بعد معالجة مشكلات التوافق مع مجموعة الإصدار التجريبي، قامت شركة Contoso بتشغيل تسلسل المهام لتوزيع حزمة Microsoft 365 Apps for enterprise إلى المجموعة الواسعة.

نظرا لأن Contoso اختارت تحديث الأجهزة تلقائيا من السحابة، لم تكن هناك حاجة لإدارة العملية في Configuration Manager. يتم تحديث أجهزتهم تلقائيا مباشرة من السحابة استنادا إلى قناة التحديث التي تم تعريفها في النشر الأولي.

فيما يلي تثبيت Microsoft 365 Apps for enterprise Contoso وبنية نشر التحديثات المستمرة.

![البنية الأساسية لتوزيع Contoso Microsoft 365 Apps for enterprise.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>الخطوة التالية

تعرف على كيفية استخدام شركة Contoso [Microsoft Intune](contoso-mdm.md) في Microsoft 365 للمؤسسة لإدارة أجهزتها والتطبيقات التي تشغلها عبر المؤسسة.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 Apps for enterprise](/deployoffice/deployment-guide-microsoft-365-apps)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[اختبار إرشادات المختبر](m365-enterprise-test-lab-guides.md)