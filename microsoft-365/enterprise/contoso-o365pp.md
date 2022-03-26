---
title: Microsoft 365 Apps for enterprise نشر Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-modern-desktop
- Strat_O365_Enterprise
ms.custom: ''
description: فهم كيفية استخدام Contoso Microsoft Endpoint Configuration Manager لنشر Microsoft 365 Apps for enterprise.
ms.openlocfilehash: 6442deb0c6b7dce83a997bab28aa1c9cc85e8564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566271"
---
# <a name="microsoft-365-apps-for-enterprise-deployment-for-contoso"></a>Microsoft 365 Apps for enterprise نشر Contoso

ترقية Contoso لأجهزة الكمبيوتر الشخصية الخاصة بهم Windows 10 Enterprise Microsoft 365 Apps for enterprise لتمكين تعاون أكثر فعالية، والأمان الأفضل، وتجربة سطح مكتب أكثر حداثة. بعد تقييم البنية الأساسية واحتياجات الأعمال، حدد Contoso هذه المتطلبات الأساسية للنشر:

- يجب تشغيل كل أجهزة الكمبيوتر Microsoft 365 Apps for enterprise.
- يجب أن يستخدم النشر أدوات الإدارة والبنية الأساسية الموجودة عند الإمكان.
- يجب أن يدعم النشر لغات متعددة وبنى موجودة على أجهزة المستخدمين.
- يجب أن تبقى أجهزة الكمبيوتر الشخصية م عصرية وآمنة بأقل تكاليف إدارية لاتمتة المعلومات وأدنى تأثير على المستخدمين.

## <a name="deployment-tools"></a>أدوات النشر

استنادا إلى متطلباتهم، اختار Contoso نشر Windows 10 Enterprise Microsoft 365 Apps for enterprise من خلال إدارة التكوين (الفرع الحالي). مقياس إدارة التكوين للبيئات الكبيرة ويوفر تحكما واسعا في التثبيت والتحديثات والإعدادات. كما أنه يتضمن ميزات مضمنة لتسهيل عملية نشر Office وإدارتها، بما في ذلك:

- ذاكرة التخزين المؤقت للنظير، التي يمكن أن تساعد في سعة الشبكة المحدودة عند النشر على الأجهزة في المواقع البعيدة.
- لوحة Office إدارة العملاء، مما يسهل نشر Office التحديثات ومراقبتها، كما تمنح المسؤولين إمكانية الوصول إلى أحدث ميزات النشر والإدارة.
- نشر حزمة اللغة الذكية، بما في ذلك النشر التلقائي للغة نظام التشغيل نفسها.
- أسلوب مدعم بالكامل وسهل الاستخدام لإزالة الإصدارات الموجودة من Office من عميل أثناء النشر.

بالإضافة إلى إدارة التكوين، استخدم Contoso مجموعة أدوات الجهوزية ل Office الوظائف الإضافية و [VBA](/deployoffice/readiness-toolkit-application-compatibility-microsoft-365-apps)، وهي أداة مجانية من Microsoft، لتقييم مشاكل التوافق مع وحدات ماكرو Office الوظائف الإضافية الخاصة بها.

## <a name="managing-deployment-and-updates"></a>إدارة النشر والتحديثات

Microsoft 365 Apps for enterprise نموذج إصدار جديد: Office كخدمة. يسهل نموذج الخدمة البقاء على أحدث الميزات مع الميزات الجديدة. ولكنه يتطلب في أغلب الأحيان من أقسام قسم المعلومات تغيير طريقة نشرها واختبار الإصدارات الجديدة. لتقليل مشاكل التوافق وضمان تحديث أجهزة الكمبيوتر الخاصة بها، تم نشر Contoso Windows Office على مرحلتين:

- أولا، تم نشر Microsoft 365 Apps for enterprise على مجموعة صغيرة من الأجهزة التمثيلية عبر المؤسسة. تم استخدام مجموعة التجربة هذه لاختبار التطبيقات وا الوظائف الإضافية والأجهزة مع Microsoft 365 Apps for enterprise.
- بعد أربعة أشهر، وبعد معالجة جميع المشاكل الهامة في التطبيقات وا الوظائف الإضافية والأجهزة في مجموعة التجربة، نشر Contoso Microsoft 365 Apps for enterprise على باقي الأجهزة في المؤسسة (المجموعة العريضة).

بدلا من إدارة التحديثات Office باستخدام "إدارة التكوين"، تمكن Contoso من التحديثات التلقائية من السحابة. تعمل التحديثات المستندة إلى السحابة على تقليل النفقات الإدارية فوق الحد مع التأكد من أن الأجهزة تبقى محدثة.

اتبع Contoso النهج نفسه على المرحلة لتحديثات الميزات كما كانت تستخدم لنشر Office: تم تلقي الأجهزة في مجموعة الإصدار التجريبي لتحديثات الميزات قبل أربعة أشهر من الأجهزة في باقي المؤسسة (المجموعة العريضة). لتمكين هذا Office، استخدم Contoso قناتين [مستحسنتين للتحديث](/DeployOffice/overview-update-channels):

- Semi-Annual Enterprise Channel (Preview) للحصول على تحديثات لمجموعة الإصدار التجريبي
- Semi-Annual Enterprise Channel لتحديثات المجموعة العريضة

نظرا لأن Semi-Annual Enterprise Channel (Preview) تصدر إصدارا من Microsoft 365 Apps for enterprise قبل أربعة أشهر من تحديث Semi-Annual Enterprise، فإن Contoso لديه الوقت للتحقق من صحة التحديثات دون الحاجة إلى إدارتها.

## <a name="deployment-process"></a>عملية النشر

لإكمال عملية نشر Office، نفذ Contoso العملية التالية، التي تتضمن توصيات أفضل الممارسات من Microsoft:

1. قبل النشر، استخدم Contoso مجموعة أدوات الجهوزية ل Office الإضافية و VBA لاختبار تطبيقاتها Office الإضافية لتقييم توافقها مع Microsoft 365 Apps for enterprise.
1. في إدارة التكوين، تم تمكين ذاكرة التخزين المؤقت للنظير على أجهزة العميل الخاصة بهم، مما يساعد في سعة الشبكة المحدودة عند النشر على أجهزة العميل في المواقع البعيدة. 
1. تعرف شركة Contoso مجموعتين من مجموعات النشر كمجموعات أجهزة في "إدارة التكوين": مجموعة تجريبية ومجموعة واسعة. تم استخدام المجموعة التجريبية، التي تضمنت مجموعة صغيرة من الأجهزة التمثيلية عبر المؤسسة، لاختبار إضافي للتطبيقات وا الوظائف الإضافية والأجهزة مع Windows 10 Enterprise Microsoft 365 Apps for enterprise.
1. حيث تم إنشاء حزم نشر Office باستخدام لوحة Office إدارة العملاء ومعالج Office 365 المثبت، وكلاهما جزء من وحدة تحكم "إدارة التكوين". حيث تم Microsoft 365 Apps for enterprise حزمتين، واحدة لمجموعة الإصدار التجريبي على Semi-Annual Enterprise Channel (Preview) والحزمة الخاصة بالمجموعة العريضة على Semi-Annual Enterprise Channel.
2. تتضمن Office حزم اللغات الإنجليزية والفرنسية والألمانية. إذا كان الجهاز يتطلب لغة لم يتم تضمينها في حزمة Office، يتم تنزيل حزمة اللغة هذه تلقائيا من شبكة تسليم Office المحتويات (CDN).
3. استخدموا الميزة المضمنة في حزمة Office لإزالة كل إصدارات MSI الموجودة من Office قبل تثبيت Microsoft 365 Apps for enterprise.
4. في إدارة التكوين، تم نشر Windows وحزم Office نقاط التوزيع عبر الشبكة. بعد ذلك، تم إدارة تسلسل مهام نشر إدارة التكوين لنشر حزمة Microsoft 365 Apps for enterprise التجريبية إلى مجموعة التجربة.
5. بعد معالجة مشاكل التوافق مع مجموعة الإصدار التجريبي، كان Contoso يدير تسلسل المهام لنشر Microsoft 365 Apps for enterprise المجموعة العريضة.

نظرا لأن Contoso اختار تحديث الأجهزة تلقائيا من السحابة، لم تكن هناك حاجة لإدارة العملية في إدارة التكوين. يتم تحديث أجهزتهم تلقائيا من السحابة استنادا إلى قناة التحديث التي تم تعريفها في النشر الأولي.

إليك بنية نشر Microsoft 365 Apps for enterprise تثبيت Contoso والتحديثات المستمرة.

![البنية الأساسية لنشر Contoso Microsoft 365 Apps for enterprise.](../media/contoso-o365pp/contoso-o365pp-fig1.png)
 
## <a name="next-step"></a>الخطوة التالية

تعرف على كيفية استخدام Contoso [Microsoft Intune](contoso-mdm.md) Microsoft 365 للمؤسسات لإدارة أجهزتها والتطبيقات التي يتم تشغيلها عبر المؤسسة.

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 Apps for enterprise](/deployoffice/deployment-guide-microsoft-365-apps)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[أدلة الاختبار المعملية](m365-enterprise-test-lab-guides.md)