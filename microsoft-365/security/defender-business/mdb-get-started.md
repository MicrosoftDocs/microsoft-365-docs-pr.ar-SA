---
title: بدء استخدام مدخل Microsoft 365 Defender
description: تعرف على كيفية بدء استخدام Microsoft 365 Defender الإلكتروني. تعرف على كيفية التنقل في المدخل، وعرض حالة الأمان الحالية والتوصيات
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 3e46ee70c1c745c336d049f039de04282c5848d8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63580008"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>بدء استخدام مدخل Microsoft 365 Defender

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

بعد أن قمت بالتوقيع للحصول على Microsoft Defender for Business، سترغب في التعرف على مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). تتضمن هذه المقالة المقاطع التالية:

- [كيفية التنقل في Microsoft 365 Defender المدخل](#navigate-the-microsoft-365-defender-portal)

- [Learning النمطية حول الأحداث والإجراءات الخاصة بالاستجابة](#complete-a-learning-module-about-incidents-and-response-actions) 

- [الخطوات التالية](#next-steps)

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>التنقل في Microsoft 365 Defender المدخل

إن Microsoft 365 Defender الإلكتروني ([https://security.microsoft.com](https://security.microsoft.com)) هو متجرك الوحيد لاستخدام Microsoft Defender for Business وإدارته. ويتضمن شعار ترحيب و وسائل الاستدعاء لمساعدتك على بدء الاستخدام وبطاقات أسطح المعلومات ذات الصلة و شريط تنقل ليمنحك إمكانية الوصول السهل إلى الميزات والإمكانات المختلفة.
 
اغتنم بعض الوقت للتعرف على مدخل Microsoft 365 Defender الخاص بك.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Microsoft 365 Defender المدخل":::

### <a name="use-the-navigation-bar"></a>استخدام شريط التنقل

استخدم شريط التنقل على الجانب الأيمن من الشاشة للوصول إلى الأحداث وعرض التقارير وإدارة سياسات الأمان. يصف الجدول التالي العناصر التي ستشاهدها في شريط التنقل.

| عنصر | الوصف |
|:---|:---|
| **Home** | يأخذك إلى الصفحة الرئيسية في Microsoft 365 Defender. تتضمن الصفحة الرئيسية بطاقات تسلط الضوء على أي تهديدات نشطة تم الكشف عنها، إلى جانب توصيات للمساعدة في تأمين بيانات الشركة وأجهزتها. <br/><br/>التوصيات في Defender for Business توفير وقت فريق الأمان وجهده. التوصيات تستند إلى أفضل الممارسات الصناعية. لمعرفة المزيد حول التوصيات، راجع توصيات الأمان [-](../defender-endpoint/tvm-security-recommendation.md) إدارة المخاطر والثغرات الأمنية. |
| **الأحداث** | يأخذك إلى قائمة الأحداث الأخيرة. عند تشغيل التنبيهات، يتم إنشاء أحداث. يمكن أن يتضمن الحادث تنبيهات متعددة. تأكد من مراجعة أحداثك بشكل منتظم. <br/><br/>لمعرفة المزيد حول الأحداث، راجع [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md).|
| **مركز الإجراءات** | يأخذك إلى قائمة إجراءات الاستجابة، بما في ذلك الإجراءات المكتملة أو المعلقة. <br/>- حدد علامة **التبويب** محفوظات لرؤية الإجراءات التي تم اتخاذها. يتم اتخاذ بعض الإجراءات تلقائيا؛ يتم أخذ الآخرين يدويا أو إكمالهم بعد الموافقة عليهم. <br/>- حدد علامة **التبويب معلق** لعرض الإجراءات التي تتطلب الموافقة للمتابعة. <br/><br/>لمعرفة المزيد حول مركز الإجراءات، راجع [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md). |
| **تحليل المخاطر** | يأخذك إلى عرض التهديدات الحالية، ويوفر لك نظرة سريعة على مشهد التهديدات. تتضمن تحليلات المخاطر أيضا تقارير ومعلومات من الباحثين في مجال الأمان من Microsoft. <br/><br/>لمعرفة المزيد حول تحليلات التهديدات، راجع تعقب التهديدات الناشئة والاستجابة [لها من خلال تحليلات التهديدات](../defender-endpoint/threat-analytics.md). |
| **نقاط آمنة** | يوفر لك تمثيلا لموضع الأمان الخاص بالشركة ويقدم اقتراحات لتحسينه.<br/><br/>لمعرفة المزيد حول "نقاط آمنة"، راجع [Microsoft Secure Score للأجهزة](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Learning الموزع** | يوفر إمكانية الوصول إلى التدريب على الأمان وموارد أخرى من خلال مسارات التعلم المضمنة في اشتراكك. يمكنك التصفية حسب المنتج ومستوى المهارة ودوره والمزيد. يمكن Learning مركز الأمان لمساعدة فريق الأمان على تعزيز ميزات الأمان & في Defender for Business والمزيد من عروض Microsoft، مثل [Microsoft Defender ل Endpoint](../defender-endpoint/microsoft-defender-endpoint.md) و [Microsoft Defender Office 365](../office-365-security/defender-for-office-365.md).  |
| **نقاط النهاية** >  **البحث** | تمكنك من البحث عن جهاز واحد أو أكثر تم اجهزته في Microsoft Defender for Business. |
| **نقاط النهاية** >  **مخزون الجهاز** | تمكنك من البحث عن جهاز واحد أو أكثر تم اجهزته في Microsoft Defender for Business. |
| **نقاط النهاية** >  **إدارة الثغرات** | يوفر لك لوحة معلومات وتوصيات وأنشطة إصلاح ومخزون برامج وقائمة بنقاط الضعف المحتملة داخل شركتك. |
| **نقاط النهاية** >  **البرامج التعليمية** | يوفر إمكانية الوصول إلى عمليات المعاينة والمحاكاة لمساعدتك على معرفة المزيد حول كيفية عمل ميزات الحماية من المخاطر. <br/><br/>حدد الارتباط **قراءة المعاينة** قبل محاولة الحصول على ملف محاكاة لكل برنامج تعليمي. تتطلب بعض عمليات المحاكاة Office، مثل Microsoft Word، لقراءة المعاينة. |
| **نقاط النهاية** >  **تكوين الجهاز** | تسرد سياسات الأمان حسب نظام التشغيل ونوعه. <br/><br/>لمعرفة المزيد حول سياسات الأمان، راجع [عرض أو تحرير السياسات في Microsoft Defender for Business](mdb-view-edit-policies.md). |
| **التقارير** | يسرد تقارير الأمان المتوفرة. تمكنك هذه التقارير من الاطلاع على اتجاهات الأمان، وعرض التفاصيل حول الكشف عن المخاطر والتنبيهات، ومعرفة المزيد حول الأجهزة المعرضة للخطر في شركتك. |
| **الصحة** | تمكنك من عرض حالة حالة الخدمة الخاصة بك وخطط التغييرات القادمة. <br/>- حدد **حالة الخدمة** لعرض حالة Microsoft 365 الخدمات المضمنة في اشتراك شركتك. <br/>- حدد **مركز الرسائل** للتعرف على التغييرات المخطط لها وما يجب توقعه.  |
| **الأذونات & الأدوار** | يمكنك من تعيين الأذونات للأشخاص في شركتك الذين سيديرون الأمان وعرض الأحداث والتقارير في Microsoft 365 Defender المدخل. يمكنك أيضا من إعداد مجموعات الأجهزة وإدارتها لتكين أجهزة شركتك وتعيين سياسات الحماية من المخاطر.  |
| **الإعدادات** | تمكنك من تحرير الإعدادات لمدخل Microsoft 365 Defender و Microsoft Defender for Business. على سبيل المثال، يمكنك الألواح (أو إيقاف التشغيل) وأجهزة شركتك (يشار إليها أيضا بنقاط النهاية). يمكنك أيضا تعريف القواعد، مثل قواعد منع التنبيهات، فضلا عن إعداد المؤشرات لحظر ملفات أو عمليات معينة أو السماح بها.  |
| **موارد إضافية** | انتقل إلى مداخل أخرى، مثل Azure Active Directory. ضع في اعتبارك أن Microsoft 365 Defender المدخل يجب أن يلبي احتياجاتك دون أن تطلب منك الانتقال إلى مداخل أخرى. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>إكمال وحدة تعليمية حول الأحداث والإجراءات الخاصة بالاستجابة

راجع الوحدة النمطية [التعليمية، الكشف](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) عن مشاكل الأمان والاستجابة لها، للحصول على نظرة عامة حول الأحداث والإجراءات المتعلقة بالاستجابة لها. ستتعرف على قائمة انتظار الأحداث والتنبيهات والإجراءات التي يمكنك اتخاذها. ستساعدك هذه الدورة التدريبية على بدء العمل على أحداث في Defender for Business.

> [!NOTE]
> على الرغم من أن الوحدة النمطية [التعليمية (الكشف](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) عن مشاكل الأمان والاستجابة لها) هي في الواقع ل Microsoft Defender ل Endpoint، فإن المفاهيم الأساسية والتدفق العام مماثلان لما ستشاهده في Defender for Business.

## <a name="next-steps"></a>الخطوات التالية

الآن وبعد أن أصبح لديك نظرة عامة حول Defender for Business، جرب واحدة أو أكثر من المهام التالية:

- [تجربة البرامج التعليمية والمحاكاة في Microsoft Defender for Business](mdb-tutorials.md)

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الإجراءات](mdb-review-remediation-actions.md)

- [عرض أو تحرير السياسات في Microsoft Defender for Business](mdb-view-edit-policies.md)