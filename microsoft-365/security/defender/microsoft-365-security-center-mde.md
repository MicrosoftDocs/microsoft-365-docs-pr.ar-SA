---
title: Microsoft Defender لنقطة النهاية في Microsoft 365 Defender
description: تعرف على التغييرات من مركز حماية Microsoft Defender إلى Microsoft 365 Defender
keywords: الشروع في العمل مع Microsoft 365 Defender، Microsoft Defender لـ Office 365، Microsoft Defender لنقطة النهاية، MDO، MDE، مدخل الأمان، مدخل أمان defender
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: bac70dd864e1ab72fae5fbefa2a8da12cce4f6e7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667219"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft Defender لنقطة النهاية في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>مرجع سريع

تسرد الصورة والجدول أدناه التغييرات في التنقل بين مركز حماية Microsoft Defender Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="المواقع الجديدة في مدخل Microsoft 365 Defender" lightbox="../../media/mde-m3d-security-center.png":::

| مركز حماية Microsoft Defender | Microsoft 365 Defender |
|---------|---------|
| لوحات <ul><li>عمليات الأمان</li><li>تحليلات التهديدات</li></ul>  |Home <ul><li>تحليلات المخاطر</li></ul>   |
| الأحداث | تنبيهات & الحوادث |
| بيانات الجهاز | بيانات الجهاز |
| قائمة انتظار التنبيهات | تنبيهات & الحوادث |
| التحقيقات التلقائية | مركز الصيانة |
| الصيد المتقدم | الصيد |
| التقارير | التقارير |
| الشركاء & واجهات برمجة التطبيقات | الشركاء & واجهات برمجة التطبيقات |
| إدارة الثغرات الأمنية & المخاطر | إدارة الثغرات الأمنية |
| التقييم والبرامج التعليمية | برامج تعليمية & التقييم |
| إدارة التكوين | إدارة التكوين |
| الإعدادات | الإعدادات | 

يجمع [Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) المحسن بين <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> قدرات الأمان التي تحمي تهديدات البريد الإلكتروني والتعاون والهوية والجهاز وتكتشفها وتتحقق فيها وتستجيب لها. يجمع هذا بين الوظائف من بوابات أمان Microsoft الحالية، بما في ذلك مركز حماية Microsoft Defender ومركز توافق & الأمان Office 365.

إذا كنت على دراية مركز حماية Microsoft Defender، فإن هذه المقالة تساعد على وصف بعض التغييرات والتحسينات في Microsoft 365 Defender. ومع ذلك، هناك بعض العناصر الجديدة والمحدثة التي يجب أن تكون على علم بها.

تاريخيا، كانت [مركز حماية Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) هي الصفحة الرئيسية Microsoft Defender لنقطة النهاية. وقد استخدمتها فرق أمان المؤسسة لمراقبة التنبيهات المتعلقة بنشاط التهديد المستمر المتقدم المحتمل أو خروقات البيانات والمساعدة في الاستجابة لها. للمساعدة في تقليل عدد المداخل، ستكون Microsoft 365 Defender هي الصفحة الرئيسية لمراقبة الأمان وإدارته عبر هويات Microsoft وبياناتها وأجهزتها وتطبيقاتها وبنيتك الأساسية.

تدعم Microsoft Defender لنقطة النهاية في Microsoft 365 Defender [منح حق الوصول إلى موفري خدمات الأمان المدارة (MSSPs)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) بنفس الطريقة التي [يتم بها منح حق الوصول في مركز حماية Microsoft Defender](mssp-access.md).

> [!IMPORTANT]
> يعتمد ما تراه في Microsoft 365 Defender على اشتراكاتك الحالية. على سبيل المثال، إذا لم يكن لديك ترخيص Microsoft Defender لـ Office 365، فلن يظهر المقطع "التعاون & البريد الإلكتروني".

> [!Note]
> Microsoft 365 Defender غير متوفر ل:
>- الولايات المتحدة سحابة القطاع الحكومي (سحابة القطاع الحكومي)
>- الولايات المتحدة سحابة القطاع الحكومي عالية (سحابة القطاع الحكومي عالية)
>- وزارة الدفاع الأمريكية
>- جميع المؤسسات الحكومية الأمريكية التي لها تراخيص تجارية

ألق نظرة على Microsoft 365 Defender في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

تعرف على المزيد حول المزايا: [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>ما الذي تم تغييره

هذا الجدول هو مرجع سريع للتغييرات بين مركز حماية Microsoft Defender Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>التنبيهات والإجراءات

| منطقه | وصف التغيير |
|---------|---------|
| [تنبيهات & الحوادث](incidents-overview.md)  | في Microsoft 365 Defender، يمكنك إدارة الحوادث والتنبيهات عبر جميع نقاط النهاية والبريد الإلكتروني والهويات. لقد قمنا بتقارب التجربة لمساعدتك في العثور على الأحداث ذات الصلة بسهولة أكبر. لمزيد من المعلومات، راجع [نظرة عامة على الحوادث](incidents-overview.md).   |
| [الصيد](advanced-hunting-overview.md)  |  يؤدي تعديل قواعد الكشف المخصصة التي تم إنشاؤها في Microsoft Defender لنقطة النهاية لتضمين جداول الهوية والبريد الإلكتروني إلى نقلها تلقائيا إلى Microsoft 365 Defender. ستظهر تنبيهاتها المقابلة أيضا في Microsoft 365 Defender. لمزيد من التفاصيل حول هذه التغييرات، اقرأ ["ترحيل قواعد الكشف المخصصة](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules)". <br><br>`DeviceAlertEvents` لا يتوفر جدول التتبع المتقدم في Microsoft 365 Defender. للاستعلام عن معلومات التنبيه الخاصة بالجهاز في Microsoft 365 Defender، يمكنك استخدام الجداول `AlertInfo` واحتواء `AlertEvidence` المزيد من المعلومات من مجموعة متنوعة من المصادر. قم بصياغة الاستعلام التالي المتعلق بالجهاز باتباع [استعلامات الكتابة دون DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[مركز الصيانة](m365d-action-center.md)    | يسرد الإجراءات المعلقة والمكتملة التي تم اتخاذها بعد التحقيقات التلقائية وإجراءات المعالجة. سابقا، أدرج مركز الإجراءات في مركز حماية Microsoft Defender الإجراءات المعلقة والمكتملة لإجراءات المعالجة المتخذة على الأجهزة فقط، بينما أدرجت التحقيقات التلقائية التنبيهات والحالة. في Microsoft 365 Defender المحسنة، يجمع مركز الصيانة إجراءات المعالجة والتحقيقات عبر البريد الإلكتروني والأجهزة والمستخدمين— كل ذلك في موقع واحد.  |
| [تحليلات المخاطر](threat-analytics.md) |  تم النقل إلى أعلى شريط التنقل لتسهيل الاكتشاف والاستخدام. يتضمن الآن معلومات التهديد لكل من نقاط النهاية والبريد الإلكتروني والتعاون.    |

### <a name="endpoints"></a>النهايه

| منطقه | وصف التغيير |
|---------|---------|
|البحث   |  يوجد شريط البحث في أعلى الصفحة. يتم توفير الاقتراحات أثناء الكتابة. يمكنك البحث عبر الكيانات التالية في Defender لنقطة النهاية و Defender for Identity: <br><br> - **الأجهزة** - مدعومة لكل من Defender لنقطة النهاية و Defender for Identity. يمكنك حتى استخدام عوامل تشغيل البحث، على سبيل المثال، يمكنك استخدام "يحتوي" للبحث عن جزء من اسم المضيف. <br><br> - **المستخدمون** - مدعوم لكل من Defender لنقطة النهاية و Defender for Identity. <br><br> - **الملفات وعناوين IP وعناوين URL** - نفس القدرات كما هو الحال في Defender لنقطة النهاية. <br> ملاحظة: عمليات البحث في عنوان IP وURL *مطابقة تماما ولا تظهر في صفحة نتائج البحث – فهي تؤدي مباشرة إلى صفحة الكيان.  <br><br> - **TVM** - نفس القدرات كما هو الحال في Defender لنقطة النهاية (الثغرات الأمنية والبرامج والتوصيات). <br><br>  تركز صفحة نتائج البحث المحسنة النتائج من جميع الكيانات.  |
|[لوحه القياده](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  هذه هي لوحة معلومات عمليات الأمان الخاصة بك. راجع نظرة عامة على عدد التنبيهات النشطة التي تم تشغيلها، والأجهزة المعرضة للخطر، والمستخدمين المعرضين للخطر، ومستوى خطورة التنبيهات والأجهزة والمستخدمين. يمكنك أيضا معرفة ما إذا كانت أي أجهزة بها مشكلات في جهاز الاستشعار، وحالة الخدمة العامة، وكيف تم الكشف عن أي تنبيهات لم يتم حلها. |
|بيانات الجهاز | لا توجد تغييرات. |
|[إدارة الثغرات الأمنية](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    تم تقصير الاسم لاحتواءه في جزء التنقل. إنه نفس المقطع إدارة المخاطر والثغرات الأمنية، مع كل الصفحات الموجودة أسفله.     |
| الشركاء وواجهات برمجة التطبيقات | لا توجد تغييرات. |
| التقييمات & البرامج التعليمية    |     قدرات اختبار وتعلم جديدة.     |
| إدارة التكوين   |  لا توجد تغييرات.  |

> [!NOTE]
> أصبح **التحقيق التلقائي والمعالجة** الآن جزءا من الحوادث. يمكنك مشاهدة أحداث التحقيق والمعالجة التلقائية في علامة التبويب **«Incident > Investigation** ».

> [!TIP]
> يتم البحث عن الجهاز من نقاط النهاية > البحث.

### <a name="access-and-reporting"></a>الوصول وإعداد التقارير

| منطقه | وصف التغيير |
|---------|---------|
| التقارير  | راجع تقارير حول نقاط النهاية والبريد الإلكتروني & التعاون، بما في ذلك الحماية من التهديدات وحماية الجهاز والامتثال والأجهزة المعرضة للخطر. |
| الصحه  |  يرتبط حاليا بالصفحة "Service health" في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com/). |
| الإعدادات |  إدارة الإعدادات الخاصة بك للتعاون في Microsoft 365 Defender ونقاط النهاية والبريد الإلكتروني & والهويات واكتشاف الجهاز.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 التنقل الأمني وإمكانياته

سيبدو شريط التنقل الأيمن أو شريط التشغيل السريع مألوفا. ومع ذلك، هناك بعض العناصر الجديدة والمحدثة في مدخل Microsoft 365 Defender. 

### <a name="incidents-and-alerts"></a>الحوادث والتنبيهات

يجمع بين إدارة الحوادث والتنبيهات عبر البريد الإلكتروني والأجهزة والهويات. توفر صفحة التنبيه سياقا كاملا للتنبيه من خلال الجمع بين إشارات الهجوم لإنشاء قصة مفصلة. تجمع تجربة جديدة وموحدة الآن معا عرضا متسقا للتنبيهات عبر أحمال العمل. يمكنك الفرز والتحقيق واتخاذ إجراء فعال بسرعة.

- [معرفة المزيد حول الحوادث](incidents-overview.md)
- [معرفة المزيد حول إدارة التنبيهات](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="شريط التشغيل السريع للتنبيهات والإجراءات في مدخل Microsoft 365 Defender" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>الصيد

ابحث بشكل استباقي عن التهديدات والبرامج الضارة والنشاط الضار عبر نقاط النهاية وعلب البريد Office 365 والمزيد باستخدام [استعلامات التتبع المتقدمة](advanced-hunting-overview.md). يمكن استخدام هذه الاستعلامات القوية لتحديد موقع مؤشرات التهديد والكيانات ومراجعتها لكل من التهديدات المعروفة والمحتملة.

يمكن إنشاء [قواعد الكشف المخصصة](custom-detection-rules.md) من استعلامات التتبع المتقدمة لمساعدتك على مشاهدة الأحداث التي قد تشير إلى نشاط الاختراق والأجهزة التي تم تكوينها بشكل خاطئ بشكل استباقي.


### <a name="action-center"></a>مركز الصيانة

يعرض لك مركز الصيانة التحقيقات التي تم إنشاؤها بواسطة قدرات التحقيق والاستجابة التلقائية. يمكن أن يساعد هذا الإصلاح التلقائي الذاتي في Microsoft 365 Defender فرق الأمان من خلال الاستجابة تلقائيا لأحداث معينة.

[تعرف على المزيد حول مركز الصيانة](m365d-action-center.md).

### <a name="threat-analytics"></a>تحليلات التهديدات

احصل على معلومات ذكية عن التهديدات من باحثين خبراء في أمان Microsoft. تساعد تحليلات المخاطر فرق الأمان على أن تكون أكثر كفاءة عند مواجهة التهديدات الناشئة. تتضمن Threat Analytics ما يلي:

- عمليات الكشف عن البريد الإلكتروني والتخفيف من المخاطر من Microsoft Defender لـ Office 365. هذا بالإضافة إلى بيانات نقطة النهاية المتوفرة بالفعل من Microsoft Defender لنقطة النهاية.
- عرض الحوادث المتعلقة بالتهديدات.
- تجربة محسنة لتحديد المعلومات القابلة للتنفيذ واستخدامها بسرعة في التقارير.

يمكنك الوصول إلى تحليلات التهديدات إما من شريط التنقل العلوي الأيمن في Microsoft 365 Defender، أو من بطاقة لوحة معلومات مخصصة تعرض أهم التهديدات لمؤسستك.

تعرف على المزيد حول كيفية [تعقب التهديدات الناشئة والاستجابة لها باستخدام تحليلات التهديدات](./threat-analytics.md).

### <a name="endpoints-section"></a>قسم نقاط النهاية

عرض أمان نقاط النهاية في مؤسستك وإدارتها. إذا كنت قد استخدمت مركز حماية Microsoft Defender، فستبدو مألوفة.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="شريط التشغيل السريع لنقاط النهاية في مدخل Microsoft 365 Defender" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>الوصول والتقارير

عرض التقارير وتغيير الإعدادات وتعديل أدوار المستخدمين.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="شريط التشغيل السريع ل Access و Reporting في مدخل Microsoft 365 Defender" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>اتصالات واجهة برمجة تطبيقات SIEM

إذا كنت تستخدم [Defender لواجهة برمجة تطبيقات SIEM لنقطة النهاية](../defender-endpoint/enable-siem-integration.md)، يمكنك الاستمرار في القيام بذلك. لقد أضفنا ارتباطات جديدة على حمولة واجهة برمجة التطبيقات التي تشير إلى صفحة التنبيه أو صفحة الحادث في مدخل الأمان Microsoft 365. تتضمن حقول واجهة برمجة التطبيقات الجديدة LinkToMTP و IncidentLinkToMTP. لمزيد من المعلومات، راجع [إعادة توجيه الحسابات من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>تنبيهات البريد الإلكتروني

يمكنك الاستمرار في استخدام تنبيهات البريد الإلكتروني ل Defender لنقطة النهاية. لقد أضفنا ارتباطات جديدة في رسائل البريد الإلكتروني التي تشير إلى صفحة التنبيه أو صفحة الحدث في Microsoft 365 Defender. لمزيد من المعلومات، راجع [إعادة توجيه الحسابات من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>موفرو خدمات الأمان المدارة (MSSP)

تسجيل الدخول إلى العديد من المستأجرين في وقت واحد في نفس جلسة الاستعراض غير معتمد حاليا في المدخل الموحد. يمكنك إلغاء الاشتراك في إعادة التوجيه التلقائي عن طريق [العودة إلى مدخل Microsoft Defender لنقطة النهاية السابق](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal)، للحفاظ على هذه الوظيفة حتى يتم حل المشكلة.

## <a name="related-information"></a>المعلومات ذات الصلة

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [إعادة توجيه الحسابات من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
