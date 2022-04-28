---
title: نشر Windows 10 Enterprise لشركة Contoso
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
description: فهم كيفية استخدام شركة Contoso Microsoft Endpoint Configuration Manager لنشر الترقيات الموضعية Windows 10 Enterprise.
ms.openlocfilehash: 082c60de614c5a125a1fd2af6ba9d187f21ca39e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095345"
---
# <a name="windows-10-enterprise-deployment-for-contoso"></a>نشر Windows 10 Enterprise لشركة Contoso

قبل الإطلاق الواسع Microsoft 365 للمؤسسة، كان لدى Contoso أجهزة كمبيوتر وأجهزة متوافقة مع Windows تعمل بمزيج من Windows 7 (10٪)، Windows 8.1 (65٪)، Windows 10 (25٪). أرادت شركة Contoso ترقية أجهزة الكمبيوتر الخاصة بها Windows 10 Enterprise الاستفادة من الأمان المتقدم وخفض النفقات العامة على تكنولوجيا المعلومات من عمليات النشر التلقائية للتحديثات. 

بعد تقييم البنية الأساسية واحتياجات الأعمال، حددت شركة Contoso هذه المتطلبات الرئيسية للنشر:

- يجب تشغيل أكبر عدد ممكن من أجهزة الكمبيوتر والأجهزة Windows 10 Enterprise
- يستفيد إطلاق الترقيات الموضعية من البنية الأساسية الحالية Configuration Manager
- التحكم في إصدارات Windows 10 Enterprise للنشر والتحديثات التي يتم إجراؤها من خلال الحلقات
- يجب أن تبقى أجهزة الكمبيوتر الشخصية والأجهزة محدثة بأقل تكاليف إدارية في تكنولوجيا المعلومات وبأدنى تأثير على المستخدمين النهائيين

يتم تعريف التحديث على أنه الإصدار المدعوم من Windows 10 Enterprise التي تلبي احتياجات أعمال Contoso، والتي يمكن أن تختلف عن وجود جميع أجهزة الكمبيوتر المتوافقة مع Windows التي تقوم بتشغيل أحدث إصدار من Windows 10 Enterprise.

## <a name="deployment-tools"></a>أدوات النشر

قبل وأثناء الترقيات الموضعية Windows 10 Enterprise، استخدمت شركة Contoso الحلول التالية Windows Analytics:

- جاهزية الترقية  

  يجمع بيانات النظام والتطبيق وبرامج التشغيل للتحليل، ثم يحدد مشكلات التوافق التي يمكن أن تحظر الترقية وتصلح المشاكل المقترحة معروفة لدى Microsoft.

- تحديث التوافق  

  يعرض لك حالة أجهزتك فيما يتعلق بالتحديثات Windows بحيث يمكنك التأكد من أنها على التحديثات الأحدث حسب الاقتضاء.

- حالة الجهاز  

  تحديد الأجهزة التي تتعطل بشكل متكرر، وبالتالي قد تحتاج إلى إعادة إنشائها أو استبدالها وبرامج تشغيل الأجهزة التي تتسبب في تعطل الجهاز، مع اقتراحات للإصدارات البديلة من برامج التشغيل هذه التي قد تقلل من عدد الأعطال. يوفر إعلاما Windows حماية البيانات التكوينات الخاطئة التي ترسل مطالبات إلى المستخدمين النهائيين.
 
لدى Contoso بنية أساسية موجودة Configuration Manager (الفرع الحالي). Configuration Manager المقاييس للبيئات الكبيرة ويوفر تحكما واسعا في التثبيت والتحديثات والإعدادات. كما أن لديها ميزات مضمنة لتسهيل نشر وإدارة Windows 10 Enterprise.

## <a name="planning-process"></a>عملية التخطيط

استخدمت شركة Contoso جاهزية الترقية في Windows Analytics لتحديد مجموعة التطبيقات المثبتة وتوافقها مع Windows 10 Enterprise.

## <a name="deployment-process"></a>عملية التوزيع

لإكمال نشر الترقية الموضعية Windows 10 Enterprise، نفذت شركة Contoso العملية التالية، والتي تتضمن توصيات أفضل الممارسات من Microsoft:

1. ذاكرة التخزين المؤقت النظير الممكنة Configuration Manager.
2. تم إنشاء حزم Windows مخصصة استنادا إلى صور من مركز خدمات الترخيص المجمع.
3. تستخدم Configuration Manager لنشر حزم Windows إلى نقاط التوزيع عبر شبكتها ونشر البنيات إلى مجموعات التشغيل المرحلي الثلاث للتحقق من الصحة والتوزيع.
4. تم إجراء تقييم لنجاح أجهزة الكمبيوتر والأجهزة في حلقات التشغيل المرحلي الثلاث للتحقق من الصحة والنشر باستخدام حلول توافق "حماية الجهاز وتحديثه" في Windows Analytics.
5. استنادا إلى معلومات Windows Analytics، حددت شركة Contoso إصدار Windows 10 Enterprise للنشر إلى مجموعة النشر الواسعة.
6. قم بتشغيل تسلسلات مهام النشر Configuration Manager لنشر حزمة Windows المحددة إلى مجموعة النشر الواسعة.
7. أجهزة الكمبيوتر والأجهزة المراقبة في مجموعة النشر الواسعة باستخدام حلول توافق حماية الجهاز وتحديثه لمعالجة المشكلات.

فيما يلي ترقية Contoso الموضعية وبنية نشر التحديثات المستمرة.

![البنية الأساسية لنشر Windows 10 Enterprise Contoso.](../media/contoso-win10/contoso-win10-fig1.png)

تتكون هذه البنية الأساسية من:

- Configuration Manager، والتي:
  - الحصول على صور لحزم Windows 10 Enterprise من مركز الترخيص المجمع من Microsoft في شبكة Microsoft.
  - هي نقطة الإدارة المركزية لحزم التوزيع.
- نقاط التوزيع الإقليمية الموجودة عادة في المكاتب المركزية الإقليمية لشركة Contoso.
- Windows أجهزة الكمبيوتر والأجهزة في مواقع مختلفة تتلقى حزم النشر وتثبتها للترقية الموضعية أو التحديثات الجارية استنادا إلى عضوية المجموعة.

## <a name="next-step"></a>الخطوة التالية

تعرف على كيفية الاستفادة من البنية الأساسية Configuration Manager لشركة Contoso [لنشر Microsoft 365 Apps for enterprise الحالية والحفاظ عليها](contoso-o365pp.md) عبر مؤسستها. 

## <a name="see-also"></a>راجع أيضًا

[Windows 10 Enterprise](/windows/deployment/)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[اختبار إرشادات المختبر](m365-enterprise-test-lab-guides.md)