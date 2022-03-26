---
title: إنشاء مركز محتوى في Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.custom: admindeeplinkSPO
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: تعرف على كيفية إنشاء مركز محتوى في Microsoft SharePoint Syntex.
ms.openlocfilehash: 0bab102ae440b8cf2c797458e7602c61794d0d06
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568922"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>إنشاء مركز محتوى في Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

لإنشاء نماذج فهم المستندات وإدارتها، ستحتاج أولا إلى مركز محتوى. مركز المحتوى هو واجهة إنشاء النماذج ويحتوي أيضا على معلومات حول نماذج مكتبات المستندات المنشورة التي تم تطبيقها عليها.

   ![حدد مكتبة في أحد المواد.](../media/content-understanding/content-center-page.png)

يمكنك إنشاء مركز محتوى افتراضي أثناء [الإعداد](set-up-content-understanding.md). ولكن يمكن SharePoint مسؤول آخر أيضا اختيار إنشاء مراكز إضافية حسب الحاجة. على الرغم من أن مركز المحتوى الواحد قد يكون جيدا للبيئات التي تريد أن يتم فيها طرح كل نشاط النموذج، فقد تحتاج إلى مراكز إضافية لأقسام متعددة داخل مؤسستك، والتي قد يكون لها احتياجات ومتطلبات أذونات مختلفة لنماذجها.

بالإضافة إلى ذلك، إذا كنت تريد تجربة SharePoint Syntex، يمكنك إنشاء مركز محتويات باستخدام الإرشادات الواردة في هذه المقالة بدون شراء التراخيص. يمكن للمستخدمين غير مرخصين إنشاء نماذج لفهم المستندات ولكن لا يمكنهم تطبيقها على مكتبة مستندات.

> [!NOTE]
> في Microsoft 365 [متعددة](../enterprise/microsoft-365-multi-geo.md) الجغرافيا، إذا كان لديك مركز محتوى افتراضي واحد في موقعك المركزي، يمكنك فقط توفير مجموعة من نشاط النموذج من داخل هذا الموقع. لا يمكنك حاليا الحصول على مجموعة من أنشطة النموذج عبر حدود المزرعة في بيئة Multi-Geo. 

## <a name="create-a-content-center"></a>إنشاء مركز محتوى

يستطيع SharePoint إنشاء موقع مركز محتوى كما لو كان ينشئ أي موقع SharePoint من خلال [](/sharepoint/create-site-collection) لوحة توفير موقع مركز الإدارة.

لإنشاء مركز محتوى جديد:

1. على مركز مسؤولي Microsoft 365، انتقل إلى SharePoint <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">إدارة > **مواقع نشطة**</a>.

2. في صفحة **المواقع النشطة** ، انقر فوق **إنشاء**، ثم حدد **خيارات أخرى**.

3. في القائمة **اختيار قالب** ، حدد **مركز المحتويات**.

4. بالنسبة إلى الموقع الجديد، يجب توفير اسم **الموقع** والمسؤول **الأساسي** **واللغة**.</br>

   > [!NOTE] 
   > يمكنك تحديد موقع مركز محتويات للعارض بأي من اللغات المتوفرة، ولكن لاحظ أنه يمكن إنشاء النماذج حاليا للملفات الإنجليزية فقط. لاحظ أيضا أنه مثل قوالب الموقع الأخرى، لا يمكن تحرير لغة الموقع الافتراضية بعد إنشاء الموقع.

5. حدد **تم الانتهاء**.
 
بعد إنشاء موقع مركز المحتوى، ستشاهده مدرجا على المواقع <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank"></a> النشطة في SharePoint الإدارة. 

### <a name="give-access-to-additional-users"></a>منح حق الوصول إلى مستخدمين إضافيين
 
بعد إنشاء الموقع، يمكنك منح مستخدمين إضافيين حق الوصول إلى الموقع من خلال نموذج [SharePoint أذونات الموقع القياسي](/sharepoint/modern-experience-sharing-permissions).

### <a name="roll-up-of-models-in-the-default-content-center"></a>طرح نماذج في مركز المحتوى الافتراضي

في SharePoint Syntex، مركز المحتوى الأول الذي تم إنشاؤه أثناء الإعداد هو *مركز المحتوى الافتراضي*. إذا تم إنشاء مراكز محتويات لاحقة، يتم عرض نماذجها في طريقة عرض مركز المحتوى الافتراضية.

![لقطة شاشة لمكتبة النماذج في مركز المحتوى الافتراضي.](../media/content-understanding/model-library-default-content-center.png)

تقوم **مكتبة النماذج** في طريقة عرض مركز المحتوى الافتراضية بضم النماذج التي تم إنشاؤها حسب مركز المحتوى للحصول على طريقة عرض ملخص لكل نماذج فهم المستندات ونماذج معالجة النماذج التي تم إنشاؤها.

> [!NOTE]
> لا يمكنك تغيير مركز المحتوى الافتراضي المعين. إنه دائما أول مركز محتوى يتم إنشاؤه أثناء الإعداد. 

## <a name="see-also"></a>انظر أيضاً
[إنشاء تصنيف](create-a-classifier.md)

[إنشاء مستخرج](create-an-extractor.md)

[إنشاء مركز محتوى](create-a-content-center.md)

[نظرة عامة حول فهم المستند](document-understanding-overview.md)

[إنشاء نموذج لمعالجة النماذج](create-a-form-processing-model.md)

[تطبيق نموذج](apply-a-model.md)