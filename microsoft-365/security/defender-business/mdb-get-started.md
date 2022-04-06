---
title: بدء استخدام مدخل Microsoft 365 Defender
description: تعرف على كيفية البدء باستخدام مدخل Microsoft 365 Defender. تعرف على كيفية التنقل في المدخل، وعرض حالة الأمان الحالية والتوصيات
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
ms.openlocfilehash: c5a940676eab6ae3a07c526ecb1bd910ed8751fe
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667131"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>بدء استخدام مدخل Microsoft 365 Defender

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business [للعملاء Microsoft 365 Business Premium](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم معاينة Defender for Business باعتباره اشتراكا مستقلا، وسيتم طرحه تدريجيا للعملاء وشركاء تكنولوجيا المعلومات الذين [يقومون بالتسجيل هنا](https://aka.ms/mdb-preview) لطلبه. تتضمن المعاينة [مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بانتظام.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالنواتج/الخدمات التي تم إصدارها مسبقا والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المقدمة هنا. 

بعد التسجيل للحصول على Microsoft Defender for Business، ستحتاج إلى التعرف على مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). تتضمن هذه المقالة الأقسام التالية:

- [كيفية التنقل في مدخل Microsoft 365 Defender](#navigate-the-microsoft-365-defender-portal)

- [Learning الوحدات النمطية حول الحوادث وإجراءات الاستجابة](#complete-a-learning-module-about-incidents-and-response-actions) 

- [الخطوات التالية](#next-steps)

>
> **هل لديك دقيقة؟**
> يرجى الاطلاع <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">على استطلاعنا القصير حول Microsoft Defender for Business</a>. يسعدنا أن نستمع إليك!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>التنقل في مدخل Microsoft 365 Defender

مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) هو متجرك الوحيد لاستخدام وإدارة Microsoft Defender for Business. يتضمن شعار ترحيب و وسائل شرح لمساعدتك على البدء، وبطاقات تعرض المعلومات ذات الصلة، وشريط تنقل لمنحك إمكانية الوصول السهل إلى الميزات والقدرات المختلفة.
 
خذ لحظة للتعرف على مدخل Microsoft 365 Defender الخاص بك.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="مدخل Microsoft 365 Defender":::

### <a name="use-the-navigation-bar"></a>استخدام شريط التنقل

استخدم شريط التنقل على الجانب الأيمن من الشاشة للوصول إلى الحوادث وعرض التقارير وإدارة نهج الأمان. يصف الجدول التالي العناصر التي ستراها في شريط التنقل.

| البند | الوصف |
|:---|:---|
| **Home** | ينقلك إلى صفحتك الرئيسية في Microsoft 365 Defender. تتضمن الصفحة الرئيسية بطاقات تسلط الضوء على أي تهديدات نشطة تم اكتشافها، بالإضافة إلى توصيات للمساعدة في تأمين بيانات شركتك وأجهزتها. <br/><br/>التوصيات مضمنة في Defender for Business يمكن أن توفر الوقت والجهد لفريق الأمان. تستند التوصيات إلى أفضل ممارسات الصناعة. لمعرفة المزيد حول التوصيات، راجع [توصيات الأمان - إدارة المخاطر والثغرات الأمنية](../defender-endpoint/tvm-security-recommendation.md). |
| **الأحداث** | يأخذك إلى قائمة الحوادث الأخيرة. عند تشغيل التنبيهات، يتم إنشاء الحوادث. يمكن أن يتضمن الحادث تنبيهات متعددة. تأكد من مراجعة الحوادث بانتظام. <br/><br/>لمعرفة المزيد حول الحوادث، راجع [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md).|
| **مركز الصيانة** | ينقلك إلى قائمة إجراءات الاستجابة، بما في ذلك الإجراءات المكتملة أو المعلقة. <br/>- حدد علامة التبويب " **المحفوظات** " للاطلاع على الإجراءات التي تم اتخاذها. يتم اتخاذ بعض الإجراءات تلقائيا؛ يتم أخذ الآخرين يدويا أو إكمالهم بعد الموافقة عليهم. <br/>- حدد علامة التبويب **"معلق** " لعرض الإجراءات التي تتطلب الموافقة للمتابعة. <br/><br/>لمعرفة المزيد حول مركز الصيانة، راجع [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md). |
| **تحليلات المخاطر** | يأخذك إلى عرض التهديدات الحالية، ويوفر لك نظرة سريعة على مشهد التهديد الخاص بك. تتضمن تحليلات التهديدات أيضا تقارير ومعلومات من باحثي أمان Microsoft. <br/><br/>لمعرفة المزيد حول تحليلات التهديدات، راجع [تعقب التهديدات الناشئة والاستجابة لها من خلال تحليلات التهديدات](../defender-endpoint/threat-analytics.md). |
| **درجة الأمان** | يوفر لك تمثيلا لموضع أمان شركتك ويقدم اقتراحات لتحسينه.<br/><br/>لمعرفة المزيد حول درجة الأمان، راجع [نقاط أمان Microsoft للأجهزة](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **مركز Learning** | يوفر الوصول إلى التدريب على الأمان والموارد الأخرى من خلال مسارات التعلم المضمنة في اشتراكك. يمكنك التصفية حسب المنتج ومستوى المهارة والدور والمزيد. يمكن أن يساعد مركز Learning فريق الأمان على زيادة ميزات الأمان & القدرات في Defender for Business والمزيد من عروض Microsoft، مثل [Microsoft Defender لنقطة النهاية](../defender-endpoint/microsoft-defender-endpoint.md) [Microsoft Defender لـ Office 365](../office-365-security/defender-for-office-365.md).  |
| **النهايه** >  **البحث** | يمكنك من البحث عن جهاز واحد أو أكثر تم إلحاقه Microsoft Defender for Business. |
| **النهايه** >  **مخزون الجهاز** | يمكنك من البحث عن جهاز واحد أو أكثر تم إلحاقه Microsoft Defender for Business. |
| **النهايه** >  **إدارة الثغرات الأمنية** | يوفر لك لوحة معلومات، وتوصيات، وأنشطة المعالجة، ومخزون البرامج، وقائمة بنقاط الضعف المحتملة داخل شركتك. |
| **النهايه** >  **الدروس** | يوفر الوصول إلى المعاينات والمحاكاة لمساعدتك على معرفة المزيد حول كيفية عمل ميزات الحماية من التهديدات. <br/><br/>حدد رابط **قراءة المعاينة** قبل محاولة الحصول على ملف المحاكاة لكل برنامج تعليمي. تتطلب بعض عمليات المحاكاة تطبيقات Office، مثل Microsoft Word، لقراءة المعاينة. |
| **النهايه** >  **تكوين الجهاز** | يسرد نهج الأمان الخاصة بك حسب نظام التشغيل والنوع. <br/><br/>لمعرفة المزيد حول نهج الأمان، راجع [عرض النهج أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md). |
| **التقارير** | سرد تقارير الأمان المتوفرة. تمكنك هذه التقارير من رؤية اتجاهات الأمان الخاصة بك، وعرض تفاصيل حول عمليات الكشف عن التهديدات والتنبيهات، ومعرفة المزيد عن الأجهزة المعرضة للخطر في شركتك. |
| **الصحه** | يمكنك من عرض حالة حماية الخدمة والتخطيط للتغييرات القادمة. <br/>- حدد **Service health** لعرض الحالة الصحية لخدمات Microsoft 365 المضمنة في اشتراك شركتك. <br/>- حدد **مركز الرسائل** للتعرف على التغييرات المخطط لها وما يجب توقعه.  |
| **الأذونات & الأدوار** | يمكنك من تعيين أذونات للأشخاص في شركتك الذين سيديرون أمانك وعرض الحوادث والتقارير في مدخل Microsoft 365 Defender. يمكنك أيضا من إعداد مجموعات الأجهزة وإدارتها لإلحاق أجهزة شركتك وتعيين نهج الحماية من التهديدات.  |
| **الإعدادات** | يمكنك من تحرير إعدادات مدخل Microsoft 365 Defender Microsoft Defender for Business. على سبيل المثال، يمكنك إلحاق (أو إلغاء الإلحاق) وأجهزة شركتك (يشار إليها أيضا بنقاط النهاية). يمكنك أيضا تحديد قواعد، مثل قواعد منع التنبيه، وإعداد مؤشرات لحظر ملفات أو عمليات معينة أو السماح بها.  |
| **المزيد من الموارد** | انتقل إلى المداخل الأخرى، مثل Azure Active Directory. ضع في اعتبارك أن مدخل Microsoft 365 Defender يجب أن يلبي احتياجاتك دون الحاجة إلى الانتقال إلى المداخل الأخرى. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>إكمال وحدة تعليمية حول الحوادث وإجراءات الاستجابة

راجع وحدة التعلم، [الكشف عن مشكلات الأمان والاستجابة لها](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/)، للحصول على نظرة عامة على الحوادث وإجراءات الاستجابة. ستتعرف على قائمة انتظار الأحداث والتنبيهات وإجراءات الاستجابة التي يمكنك اتخاذها. ستساعدك هذه الدورة التدريبية على البدء في العمل على الحوادث في Defender for Business.

> [!NOTE]
> على الرغم من أن وحدة التعلم ([الكشف عن مشكلات الأمان والاستجابة](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) لها) مخصصة بالفعل Microsoft Defender لنقطة النهاية، فإن المفاهيم الأساسية والتدفق العام مشابهان لما ستراه في Defender for Business.

## <a name="next-steps"></a>الخطوات التالية

الآن بعد أن أصبح لديك نظرة عامة على Defender for Business، جرب واحدة أو أكثر من المهام التالية:

- [جرب البرامج التعليمية والمحاكاة في Microsoft Defender for Business](mdb-tutorials.md)

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)

- [عرض الحوادث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [الاستجابة للتهديدات وتخفيفها في Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [مراجعة إجراءات المعالجة في مركز الصيانة](mdb-review-remediation-actions.md)

- [عرض النهج أو تحريرها في Microsoft Defender for Business](mdb-view-edit-policies.md)