---
title: Microsoft Defender لنقطة النهاية في Microsoft 365 Defender
description: تعرف على التغييرات من مركز حماية Microsoft Defender إلى Microsoft 365 Defender
keywords: بدء العمل باستخدام Microsoft 365 Defender، Microsoft Defender لـ Office 365، Microsoft Defender لنقطة النهاية، MDO، MDE، مدخل الأمان، مدخل أمان defender
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
ms.openlocfilehash: f50a6750c3f5cd39e68a39cf000ff60e4fec8ef2
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568683"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft Defender لنقطة النهاية في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>مرجع سريع

تسرد الصورة الجدول أدناه التغييرات في التنقل بين مركز حماية Microsoft Defender Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="المواقع الجديدة في مدخل Microsoft 365 Defender" lightbox="../../media/mde-m3d-security-center.png":::

| مركز حماية Microsoft Defender | Microsoft 365 Defender |
|---------|---------|
| لوحات المعلومات <ul><li>عمليات الأمان</li><li>Threat Analytics</li></ul>  |Home <ul><li>تحليل المخاطر</li></ul>   |
| الأحداث | الأحداث & تنبيهات |
| بيانات الجهاز | بيانات الجهاز |
| قائمة انتظار التنبيهات | الأحداث & تنبيهات |
| عمليات التحقيق التلقائية | مركز الإجراءات |
| الصيد المتقدم | الصيد |
| التقارير | التقارير |
| الشركاء & واجهات برمجة التطبيقات | الشركاء & واجهات برمجة التطبيقات |
| إدارة & المخاطر | إدارة الثغرات |
| التقييم والبرامج التعليمية | تقييم & التعليمية |
| إدارة التكوين | إدارة التكوين |
| الإعدادات | الإعدادات | 

تجمع [Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> المحسنة في بين قدرات الأمان التي تحمي البريد الإلكتروني والتعاون والهوية وتهديدات الأجهزة وتكشف عنها وتتحقق من وجودها وتستجيب لها. يجمع ذلك بين الوظائف من مداخل أمان Microsoft الموجودة، بما في ذلك مركز حماية Microsoft Defender ومركز Office 365 الأمان & التوافق.

إذا كنت معتادا على مركز حماية Microsoft Defender، فإن هذه المقالة تساعد على وصف بعض التغييرات والتحسينات في Microsoft 365 Defender. ومع ذلك، هناك بعض العناصر الجديدة والمحدثة التي يجب أن تكون على علم بها.

من الناحية التاريخية[، مركز حماية Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) الصفحة الرئيسية Microsoft Defender لنقطة النهاية. وقد استخدمته فرق أمان المؤسسة لمراقبة التنبيهات المتعلقة بنشاط تهديدات ثابتة أو اختراقات البيانات المحتملة ومساعدتها على الاستجابة لها. للمساعدة في تقليل عدد المداخل، Microsoft 365 Defender تكون الصفحة الرئيسية لمراقبة الأمان وإدارته عبر هويات Microsoft والبيانات والأجهزة والتطبيقات والبنية الأساسية.

Microsoft Defender لنقطة النهاية في Microsoft 365 Defender منح حق الوصول إلى موفري خدمات الأمان المدارة [(MSSPs)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) بالطريقة نفسها التي يتم بها منح حق الوصول [في](mssp-access.md) مركز حماية Microsoft Defender.

> [!IMPORTANT]
> يعتمد ما تراه في Microsoft 365 Defender اشتراكاتك الحالية. على سبيل المثال، إذا لم يكن لديك ترخيص Microsoft Defender لـ Office 365، لن يظهر & البريد الإلكتروني والتعاون.

> [!Note]
> Microsoft 365 Defender غير متوفر ل:
>- الولايات سحابة القطاع الحكومي (سحابة القطاع الحكومي)
>- US سحابة القطاع الحكومي High (سحابة القطاع الحكومي High)
>- وزارة الدفاع الأمريكية
>- جميع المؤسسات الحكومية الأمريكية التي لها تراخيص تجارية

أطلع على Microsoft 365 Defender في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

Mer informasjon حول الفوائد: [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>ما الذي تم تغييره

هذا الجدول هو مرجع سريع للتغييرات بين مركز حماية Microsoft Defender Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>التنبيهات والإجراءات

| المنطقة | وصف التغيير |
|---------|---------|
| [الأحداث & تنبيهات](incidents-overview.md)  | في Microsoft 365 Defender، يمكنك إدارة الأحداث والتنبيهات عبر كل نقاط النهاية والبريد الإلكتروني والهويات. لقد تعرفنا على التجربة لمساعدتك في العثور على الأحداث ذات الصلة بسهولة أكبر. لمزيد من المعلومات، راجع [نظرة عامة حول الأحداث](incidents-overview.md).   |
| [الصيد](advanced-hunting-overview.md)  |  يؤدي تعديل قواعد الكشف المخصصة التي تم إنشاؤها في Microsoft Defender لنقطة النهاية إلى تضمين جداول الهوية والبريد الإلكتروني إلى نقلها تلقائيا إلى Microsoft 365 Defender. ستظهر تنبيهاتهم المقابلة أيضا في Microsoft 365 Defender. لمزيد من التفاصيل حول هذه التغييرات، اقرأ [ترحيل قواعد الكشف المخصصة](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>لا `DeviceAlertEvents` يتوفر جدول الصيد المتقدم في Microsoft 365 Defender. للاستعلام عن `AlertInfo` `AlertEvidence` معلومات التنبيه الخاصة بجهاز معين في Microsoft 365 Defender، يمكنك استخدام الجداول و لاحتواء مزيد من المعلومات من مجموعة متنوعة من المصادر. قم بصياغة الاستعلام التالي المتعلق بال جهاز باتباع [استعلامات الكتابة بدون DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[مركز الإجراءات](m365d-action-center.md)    | تسرد الإجراءات المعلقة والمكتملة التي تم اتخاذها بعد عمليات التحقيق التلقائية والإجراءات الإصلاحية. في السابق، كان مركز الإجراءات في مركز حماية Microsoft Defender سرد الإجراءات المعلقة والمكتملة الخاصة ب إجراءات المعالجة التي تم اتخاذها على الأجهزة فقط، في حين أدرجت عمليات التحقيق التلقائية التنبيهات الحالة والتنبيهات. في Microsoft 365 Defender المحسنة، يجمع مركز الإجراءات معا إجراءات المعالجة والتباحثات عبر البريد الإلكتروني والأجهزة والمستخدمين— كل ذلك في موقع واحد.  |
| [تحليل المخاطر](threat-analytics.md) |  تم نقلها إلى أعلى شريط التنقل لتسهيل اكتشافها واستخدامها. يتضمن الآن معلومات المخاطر لكل من نقاط النهاية والبريد الإلكتروني والتعاون.    |

### <a name="endpoints"></a>نقاط النهاية

| المنطقة | وصف التغيير |
|---------|---------|
|البحث   |  يقع شريط البحث في أعلى الصفحة. يتم توفير الاقتراحات بينما تكتب. يمكنك البحث عبر الوحدات التالية في Defender for Endpoint و Defender for Identity: <br><br> - **الأجهزة** - معتمدة لكل من Defender for Endpoint و Defender for Identity. يمكنك حتى استخدام عوامل تشغيل البحث، على سبيل المثال، يمكنك استخدام "يحتوي على" للبحث عن جزء من اسم المضيف. <br><br> - **المستخدمون** - مدعوم لكل من Defender for Endpoint و Defender for Identity. <br><br> - **الملفات، عناوين الإنترنت، عناوين URL** - القدرات نفسها الموجودة في Defender for Endpoint. <br> ملاحظة: *عمليات البحث في عنوان IP وURL متطابقة تماما ولا تظهر في صفحة نتائج البحث ، فهي تؤدي مباشرة إلى صفحة الكيان.  <br><br> - **TVM** - القدرات نفسها كما في Defender for Endpoint (نقاط الضعف والبرامج والتوصيات). <br><br>  تمركز صفحة نتائج البحث المحسنة النتائج من جميع الكيانات.  |
|[لوحة المعلومات](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  هذه هي لوحة معلومات عمليات الأمان. راجع نظرة عامة حول عدد التنبيهات النشطة التي تم تشغيلها، والأجهزة المعرضة للمخاطر، والمستخدمين المعرضين للمخاطر، ومستوى الخطورة للتنبيهات والأجهزة والمستخدمين. يمكنك أيضا معرفة ما إذا كانت هناك أي أجهزة لديها مشاكل في المستشعر، وعلى حالة الخدمة بشكل عام، وكيفية اكتشاف أي تنبيهات لم يتم حلها. |
|بيانات الجهاز | لا توجد تغييرات. |
|[إدارة الثغرات](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    تم تقصير الاسم لاحتواء جزء التنقل. إنه نفس مقطع إدارة المخاطر والثغرات الأمنية، مع كل الصفحات الموجودة أسفله.     |
| الشركاء و واجهات برمجة التطبيقات | لا توجد تغييرات. |
| التقييمات & التعليمية    |     قدرات اختبار وتعلم جديدة.     |
| إدارة التكوين   |  لا توجد تغييرات.  |

> [!NOTE]
> **أصبح الآن التحقيق التلقائي والوساطة** جزءا من الأحداث. يمكنك الاطلاع على أحداث الإصلاح والتحري التلقائي في علامة التبويب > **التحقيق** .

> [!TIP]
> يتم البحث عن الجهاز من نقاط النهاية > البحث.

### <a name="access-and-reporting"></a>الوصول وإعداد التقارير

| المنطقة | وصف التغيير |
|---------|---------|
| التقارير  | راجع تقارير نقاط النهاية والبريد الإلكتروني & التعاون، بما في ذلك الحماية من المخاطر وحماية الجهاز والتوافق والأجهزة المعرضة للتأثر. |
| الصحة  |  يقوم حاليا بالربط بصفحة "Estado de funcionamento dos serviços" في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com/). |
| الإعدادات |  يمكنك إدارة الإعدادات Microsoft 365 Defender نقاط النهاية والبريد الإلكتروني & والتعاون والهويات واكتشاف الجهاز.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 التنقل والأمان وإمكانياته

سيبدو شريط التنقل الأيسر أو شريط تشغيل سريع مألوفا. ومع ذلك، هناك بعض العناصر الجديدة والمحدثة في Microsoft 365 Defender المدخل. 

### <a name="incidents-and-alerts"></a>الأحداث والتنبيهات

تجمع إدارة الأحداث والتنبيهات عبر البريد الإلكتروني والأجهزة والهويات. توفر صفحة التنبيه سياقا كاملا للتنبيه من خلال دمج إشارات الهجوم لإنشاء قصة مفصلة. تجمع الآن التجربة الموحدة الجديدة معا طريقة عرض متناسقة للتنبيهات عبر أحمال العمل. يمكنك إجراء الفرز بسرعة، والتحري، واتخاذ إجراء فعال.

- [Mer informasjon حول الأحداث](incidents-overview.md)
- [Mer informasjon حول إدارة التنبيهات](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="شريط &quot;التنبيهات والإجراءات&quot; السريع في مدخل Microsoft 365 Defender" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>الصيد

ابحث بشكل استباقي عن التهديدات والبرامج الضارة و النشاط الضار عبر نقاط النهاية Office 365 علب البريد والمزيد باستخدام استعلامات الصيد [المتقدمة](advanced-hunting-overview.md). يمكن استخدام هذه الاستعلامات القوية لتحديد موقع مؤشرات التهديدات والكيانات ومراجعتها لكل من التهديدات المعروفة والمحتملة.

[يمكن إنشاء قواعد الكشف](custom-detection-rules.md) المخصصة من استعلامات البحث المتقدمة لمساعدتك على المراقبة الاستباقية للأحداث التي قد تكون حالة من نشاط الخرق والأجهزة التي تم تكوينها بشكل خاطئ.


### <a name="action-center"></a>مركز الإجراءات

يعرض لك مركز الإجراءات عمليات البحث التي تم إنشاؤها بواسطة قدرات الاستجابة والتحريات التلقائية. يمكن أن يساعد هذا الاختبار التلقائي Microsoft 365 Defender فرق الأمان من خلال الاستجابة تلقائيا إلى أحداث معينة.

[Mer informasjon حول مركز الإجراءات](m365d-action-center.md).

### <a name="threat-analytics"></a>Threat Analytics

احصل على معلومات عن المخاطر من الباحثين الخبراء في مجال الأمان في Microsoft. تساعد تحليلات المخاطر فرق الأمان على أن تكون أكثر فعالية عند مواجهة التهديدات الناشئة. تتضمن تحليلات المخاطر ما يلي:

- عمليات الكشف وتخفيف المخاطر المتعلقة بالبريد الإلكتروني Microsoft Defender لـ Office 365. هذا بالإضافة إلى بيانات نقطة النهاية المتوفرة بالفعل من Microsoft Defender لنقطة النهاية.
- طريقة عرض الأحداث ذات الصلة بالتهديات.
- تجربة محسنة لتحديد المعلومات القابلة للتنفيذ واستخدامها بسرعة في التقارير.

يمكنك الوصول إلى تحليلات التهديدات إما من شريط التنقل العلوي الأيمن في Microsoft 365 Defender، أو من بطاقة لوحة معلومات مخصصة تعرض التهديدات الرئيسية لمنظمتك.

Mer informasjon حول كيفية تعقب التهديدات الناشئة والاستجابة [لها باستخدام تحليلات المخاطر](./threat-analytics.md).

### <a name="endpoints-section"></a>مقطع نقاط النهاية

عرض أمان نقاط النهاية وإدارته في مؤسستك. إذا كنت قد استخدمت مركز حماية Microsoft Defender، ستبدو مألوفة.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="شريط تشغيل نقاط النهاية السريع في مدخل Microsoft 365 Defender" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>الوصول والتقارير

عرض التقارير وتغيير الإعدادات وتعديل أدوار المستخدمين.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="شريط تشغيل سريع للوصول وإعداد التقارير في مدخل Microsoft 365 Defender" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>اتصالات SIEM API

إذا كنت تستخدم [API ل Defender for Endpoint SIEM](../defender-endpoint/enable-siem-integration.md)، يمكنك متابعة القيام بذلك. لقد أضفنا ارتباطات جديدة على حمولة API التي تشير إلى صفحة التنبيه أو صفحة الحادث في مدخل Microsoft 365 الأمان. تتضمن حقول API الجديدة LinkToMTP و IncidentLinkToMTP. لمزيد من المعلومات، راجع إعادة توجيه الحسابات [من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>تنبيهات البريد الإلكتروني

يمكنك الاستمرار في استخدام تنبيهات البريد الإلكتروني ل Defender لنقطة النهاية. لقد أضفنا ارتباطات جديدة في رسائل البريد الإلكتروني التي تشير إلى صفحة التنبيه أو صفحة الحادث في Microsoft 365 Defender. لمزيد من المعلومات، راجع إعادة توجيه الحسابات [من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>موفرو خدمات الأمان المدارة (MSSP)

إن تسجيل الدخول إلى مستأجرين متعددين في الوقت نفسه في جلسة الاستعراض نفسها غير معتمد حاليا في المدخل الموحد. يمكنك إلغاء الاشتراك في إعادة التوجيه التلقائي عن طريق العودة إلى [](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal)مدخل Microsoft Defender لنقطة النهاية السابق، للحفاظ على هذه الوظيفة حتى يتم حل المشكلة.

## <a name="related-information"></a>المعلومات ذات الصلة

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [إعادة توجيه الحسابات من Microsoft Defender لنقطة النهاية إلى Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
