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
ms.openlocfilehash: c630bba8bafad8bcbf9749e7a4d08ae1e86f4d68
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882209"
---
# <a name="create-a-content-center-in-microsoft-sharepoint-syntex"></a>إنشاء مركز محتوى في Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CPSF]

</br>

لإنشاء نماذج فهم المستندات وإدارتها، تحتاج أولا إلى مركز محتوى. مركز المحتوى هو واجهة إنشاء النموذج ويحتوي أيضا على معلومات حول مكتبات المستندات التي تم تطبيق النماذج المنشورة عليها.

   ![حدد مكتبة مستندات.](../media/content-understanding/content-center-page.png)

يمكنك إنشاء مركز محتوى افتراضي أثناء [الإعداد](set-up-content-understanding.md). ولكن يمكن لمسؤول SharePoint أيضا اختيار إنشاء مراكز إضافية حسب الحاجة. على الرغم من أن مركز محتوى واحد قد يكون جيدا للبيئات التي تريد إظهار جميع أنشطة النموذج لها، فقد ترغب في الحصول على مراكز إضافية لأقسام متعددة داخل مؤسستك، والتي قد يكون لها احتياجات ومتطلبات أذونات مختلفة لنماذجها.

بالإضافة إلى ذلك، إذا كنت تريد تجربة SharePoint Syntex، يمكنك إنشاء مركز محتوى باستخدام الإرشادات الواردة في هذه المقالة دون شراء التراخيص. يمكن للمستخدمين غير المرخصين إنشاء نماذج لفهم المستندات ولكن لا يمكنهم تطبيقها على مكتبة مستندات.

> [!NOTE]
> في [Microsoft 365 بيئة متعددة المناطق الجغرافية](../enterprise/microsoft-365-multi-geo.md)، إذا كان لديك مركز محتوى افتراضي واحد في موقعك المركزي، يمكنك فقط توفير مجموعة من أنشطة النموذج من داخل هذا الموقع. لا يمكنك حاليا الحصول على مجموعة من أنشطة النموذج عبر حدود المزرعة في بيئة متعددة المناطق الجغرافية. 

## <a name="create-a-content-center"></a>إنشاء مركز محتوى

يمكن لمسؤول SharePoint إنشاء موقع مركز محتوى كما يقوم [بإنشاء أي موقع SharePoint آخر](/sharepoint/create-site-collection) من خلال لوحة توفير موقع مركز الإدارة.

لإنشاء مركز محتوى جديد:

1. على مركز مسؤولي Microsoft 365، انتقل إلى <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">مركز إدارة SharePoint > **المواقع النشطة**</a>.

2. في صفحة **"المواقع النشطة** "، انقر فوق **"إنشاء**"، ثم حدد **"خيارات أخرى**".

3. في القائمة **"اختيار قالب** "، حدد **"مركز المحتويات**".

4. بالنسبة إلى الموقع الجديد، قم بتوفير **اسم الموقع** **والمسؤول الأساسي** **ولغة**.</br>

   > [!NOTE] 
   > يمكنك تحديد موقع مركز محتوى لعرضه بأي من اللغات المتوفرة، ولكن لاحظ أنه يمكن حاليا إنشاء نماذج لملفات اللغة الإنجليزية فقط. لاحظ أيضا أنه مثل قوالب المواقع الأخرى، لا يمكن تحرير لغة الموقع الافتراضية بعد إنشاء الموقع.

5. حدد **"Finished**".
 
بعد إنشاء موقع مركز محتوى، سترى أنه مدرج على <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**المواقع النشطة**</a> في مركز إدارة SharePoint. 

### <a name="give-access-to-additional-users"></a>منح حق الوصول إلى مستخدمين إضافيين
 
بعد إنشاء الموقع، يمكنك منح مستخدمين إضافيين حق الوصول إلى الموقع من خلال [نموذج أذونات الموقع SharePoint](/sharepoint/modern-experience-sharing-permissions) القياسي.

### <a name="roll-up-of-models-in-the-default-content-center"></a>إظهار النماذج في مركز المحتوى الافتراضي

في SharePoint Syntex، أول مركز محتوى تم إنشاؤه أثناء الإعداد هو *مركز المحتوى الافتراضي*. إذا تم إنشاء مراكز المحتويات اللاحقة، يتم عرض نماذجها في طريقة عرض مركز المحتوى الافتراضية.

![لقطة شاشة لمكتبة النماذج في مركز المحتوى الافتراضي.](../media/content-understanding/model-library-default-content-center.png)

تجمع مكتبة **النماذج** في طريقة عرض مركز المحتوى الافتراضية النماذج التي تم إنشاؤها حسب مركز المحتوى للحصول على عرض ملخص لكافة نماذج فهم المستندات ونماذج معالجة النماذج التي تم إنشاؤها.

> [!NOTE]
> لا يمكنك تغيير مركز المحتوى الافتراضي المعين. إنه دائما أول مركز محتوى يتم إنشاؤه أثناء الإعداد. 

## <a name="see-also"></a>راجع أيضًا

[إنشاء مصنف](create-a-classifier.md)

[إنشاء مستخرج](create-an-extractor.md)

[إنشاء مركز محتوى](create-a-content-center.md)

[نظرة عامة على فهم المستند](document-understanding-overview.md)

[إنشاء نموذج معالجة نموذج](create-a-form-processing-model.md)

[تطبيق نموذج](apply-a-model.md)