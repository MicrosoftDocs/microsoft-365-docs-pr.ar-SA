---
title: نظرة عامة على معالجة النماذج في Microsoft SharePoint Syntex
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
description: تعرف على كيفية استخدام الذكاء الاصطناعي Build لإنشاء نماذج معالجة النماذج في Microsoft SharePoint Syntex.
ms.openlocfilehash: 7b9ff8b8a1014dfb47aa7061caf31599e497c18a
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463176"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>نظرة عامة على معالجة النماذج في Microsoft SharePoint Syntex

 ![الذكاء الاصطناعي Builder.](../media/content-understanding/ai-builder.png)</br>

يستخدم Microsoft SharePoint Syntex معالجة نماذج Microsoft Power Apps [الذكاء الاصطناعي Builder](/ai-builder/overview) لإنشاء نماذج داخل مكتبات المستندات SharePoint.

يمكنك استخدام معالجة نماذج الذكاء الاصطناعي Builder لإنشاء نماذج الذكاء الاصطناعي تستخدم تقنية التعلم الآلي لتحديد واستخراج أزواج قيم المفاتيح وبيانات الجدول من المستندات المنظمة أو شبه المنظمة، مثل النماذج والفواتير.

غالبا ما تتلقى المؤسسات الفواتير بكميات كبيرة من مصادر مختلفة، مثل البريد والفاكس والبريد الإلكتروني. قد تستغرق معالجة هذه المستندات وإدخالها يدويا في قاعدة بيانات وقتا طويلا. باستخدام الذكاء الاصطناعي لاستخراج النص وأزواج المفاتيح/القيم والجداول من المستندات، فإن معالجة النماذج تشغل هذه العملية تلقائيا. 

> [!NOTE]
> راجع [اعتماد SharePoint Syntex: دليل بدء الاستخدام للحصول على](./adoption-getstarted.md) مزيد من المعلومات حول أمثلة سيناريو معالجة النموذج.

على سبيل المثال، يمكنك إنشاء نموذج معالجة نموذج يحدد كافة مستندات أوامر الشراء التي يتم تحميلها إلى مكتبة المستندات. من كل أمر شراء، يمكنك بعد ذلك استخراج وعرض بيانات معينة مهمة بالنسبة لك، مثل *رقم أمر الشراء* أو *التاريخ* أو *التكلفة الإجمالية*.

![طريقة عرض مكتبة المستندات.](../media/content-understanding/doc-lib-done.png)</br>  

يمكنك استخدام أمثلة الملفات لتدريب النموذج الخاص بك وتحديد المعلومات التي سيتم استخراجها من النموذج الخاص بك. يتم تعلم تخطيط المستند من خلال تدريب النموذج الخاص بك. تحتاج فقط إلى خمسة مستندات نموذجية للبدء. سيقوم الذكاء الاصطناعي Builder بتحليل ملفات المثال الخاصة بك لأزواج قيم المفاتيح، ويمكنك أيضا تحديد تلك التي ربما لم يتم الكشف عنها يدويا.  يتيح لك الذكاء الاصطناعي builder اختبار دقة النموذج الخاص بك على ملفات المثال.

بعد تدريب النموذج ونشره، ينشئ نموذجك [تدفقا Power Automate](/power-automate/getting-started). يتم تشغيل التدفق عند تحميل ملف إلى مكتبة مستندات SharePoint وسيستخرج البيانات التي تم تحديدها في النموذج. سيتم عرض البيانات المستخرجة في أعمدة في طريقة عرض مكتبة مستندات النموذج.

يحتاج مسؤول Office 365 إلى [تمكين معالجة النماذج](./set-up-content-understanding.md) لمكتبة مستندات SharePoint ليتمكن المستخدمون من [إنشاء نموذج معالجة نموذج](create-a-form-processing-model.md) فيها. يمكنك تحديد المواقع أثناء الإعداد، أو بعد الإعداد في إعدادات الإدارة.

## <a name="file-limitations"></a>قيود الملف

عند استخدام نماذج معالجة النماذج، تأكد من ملاحظة [متطلبات استخدام الملفات وقيودها](/ai-builder/form-processing-model-requirements).

## <a name="supported-languages"></a>اللغات المدعومة

تدعم معالجة النماذج المستندات بأكثر من 73 لغة. للحصول على قائمة اللغات، راجع [دعم لغة معالجة النموذج](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support).

## <a name="multi-geo-environments"></a>بيئات جغرافية متعددة

عند إعداد SharePoint Syntex في [بيئة Microsoft 365 متعددة المناطق الجغرافية](../enterprise/microsoft-365-multi-geo.md)، يمكنك تكوينه فقط لاستخدام معالجة النموذج في الموقع المركزي. إذا كنت تريد استخدام معالجة النماذج في موقع قمر صناعي، فاتصل بدعم Microsoft.

## <a name="custom-environments"></a>بيئات مخصصة

إذا كنت تستخدم بيئة مخصصة (بدلا من البيئة الافتراضية) لمعالجة Power Platform، فهناك متطلبات إعداد إضافية. لمزيد من المعلومات، راجع [بيئات Power Platform المخصصة](set-up-content-understanding.md#requirements).


## <a name="see-also"></a>راجع أيضًا
  
[وثائق Power Automate](/power-automate/)

[إنشاء نموذج لمعالجة النماذج](create-a-form-processing-model.md)

[نظرة عامة على فهم المستند](document-understanding-overview.md)

[تدريب: تحسين أداء الأعمال باستخدام الذكاء الاصطناعي Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)