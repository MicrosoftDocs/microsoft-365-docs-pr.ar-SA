---
title: نظرة عامة حول معالجة النموذج في Microsoft SharePoint Syntex
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
description: تعرف على كيفية استخدام "إنشاء المعلومات" لإنشاء نماذج لمعالجة النماذج في Microsoft SharePoint Syntex.
ms.openlocfilehash: d04de2fc71b0b393e560e354253be42053725416
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/12/2022
ms.locfileid: "63567490"
---
# <a name="form-processing-overview-in-microsoft-sharepoint-syntex"></a>نظرة عامة حول معالجة النموذج في Microsoft SharePoint Syntex

 ![منشئ AI.](../media/content-understanding/ai-builder.png)</br>

تستخدم SharePoint Syntex Microsoft Power Apps [AI Builder](/ai-builder/overview) معالجة النماذج لإنشاء نماذج SharePoint مكتبات المستندات.

يمكنك استخدام معالجة نماذج "منشئ المعلومات" لإنشاء نماذج ل AI تستخدم تقنية التعلم الآلي لتحديد أزواج قيم المفاتيح وبيانات الجدول واستخراجها من المستندات المنظمة أو شبه المنظمة، مثل النماذج والفواتير.

غالبا ما تتلقى المؤسسات فواتير بكمية كبيرة من مجموعة متنوعة من المصادر، مثل البريد والفاكس والبريد الإلكتروني وغير ذلك. قد تستغرق معالجة هذه المستندات وإد إدخالها يدويا في قاعدة بيانات وقتا طويلا. باستخدام AI لاستخراج النص وأزواج المفاتيح/القيم والجداول من المستندات، فإن معالجة النموذج أتمتة هذه العملية. 

> [!NOTE]
> راجع SharePoint Syntex [الاعتماد: دليل بدء العمل](./adoption-getstarted.md) للحصول على مزيد من المعلومات حول أمثلة سيناريوهات معالجة النموذج.

على سبيل المثال، يمكنك إنشاء نموذج لمعالجة النماذج يحدد كل مستندات أوامر الشراء التي يتم تحميلها إلى مكتبة المستندات. من كل أمر شراء، يمكنك بعد ذلك استخراج بيانات معينة مهمة بالنسبة لك وعرضها، مثل رقم أمر الشراء أو التاريخ أو *التكلفة الإجمالية*.

![طريقة عرض مكتبة Doc.](../media/content-understanding/doc-lib-done.png)</br>  

يمكنك استخدام ملفات نموذجية لتدريب النموذج الخاص بك وتحديد المعلومات التي سيتم استخراجها من النموذج. يتم تعلم تخطيط المستند من خلال تدريب النموذج الخاص بك. تحتاج فقط إلى خمسة مستندات نموذج للبدء. سيحلل "منشئ المعلومات الشخصية" ملفاتك كمثال اقترانات القيم الأساسية، كما يمكنك أيضا تحديد الملفات التي ربما لم يتم الكشف عنها يدويا.  يتيح لك منشئ المعلومات الشخصية اختبار دقة النموذج على ملفاتك النموذجية.

بعد تدريب النموذج ونشره، ينشئ النموذج Power Automate [جديد](/power-automate/getting-started). يتم تشغيل التدفق عند تحميل ملف إلى SharePoint المستندات وسيستخرج البيانات التي تم تعريفها في النموذج. سيتم عرض البيانات المستخرجة في أعمدة في طريقة عرض مكتبة المستندات الخاصة بالنموذج.

يحتاج Office 365 مسؤول إلى تمكين معالجة النماذج لمكتبة مستندات SharePoint لتمكين المستخدمين من إنشاء نموذج [لمعالجة](create-a-form-processing-model.md) النماذج فيها.[](./set-up-content-understanding.md) يمكنك تحديد المواقع أثناء الإعداد أو بعد الإعداد في إعدادات الإدارة.

### <a name="file-limitations"></a>قيود الملفات

عند استخدام نماذج معالجة النماذج، تأكد من ملاحظة المتطلبات والقيود [الخاصة باستخدام الملفات](/ai-builder/form-processing-model-requirements).

### <a name="multi-geo-environments"></a>بيئات متعددة الجغرافيا

عند إعداد SharePoint Syntex في Microsoft 365 [متعددة](../enterprise/microsoft-365-multi-geo.md) الجغرافيا، يمكنك فقط تكوينه لاستخدام معالجة النموذج في الموقع المركزي. إذا كنت تريد استخدام معالجة النموذج في موقع القمر الصناعي، فاتصل ب دعم Microsoft.






## <a name="see-also"></a>انظر أيضاً
  
[Power Automate الوثائق](/power-automate/)

[إنشاء نموذج لمعالجة النماذج](create-a-form-processing-model.md)

[نظرة عامة حول فهم المستند](document-understanding-overview.md)

[التدريب: تحسين أداء الأعمال باستخدام "منشئ AI"](/learn/paths/improve-business-performance-ai-builder/?source=learn)