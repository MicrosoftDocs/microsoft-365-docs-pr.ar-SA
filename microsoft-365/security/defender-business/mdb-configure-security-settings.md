---
title: عرض إعدادات الأمان وتحريرها في Microsoft Defender for Business
description: تكوين سياسات الأمان في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 54592b20b5b6471d26c4673492566451ae5ec0de
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63572104"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>عرض إعدادات ونهج الأمان وتحريرها في Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

## <a name="overview"></a>نظرة عامة

بعد أن قمت بضبط أجهزة شركتك في Microsoft Defender for Business، تكون الخطوة التالية هي عرض سياسات الأمان والإعدادات وتحريرها إذا لزم الأمر. تتضمن سياسات الأمان ما يلي:

- **[سياسات حماية الجيل التالي](#view-or-edit-your-next-generation-protection-policies)**، التي تحدد الحماية من الفيروسات والحماية من البرامج الضارة للأجهزة الخاصة بالشركة

- **[حماية جدار الحماية وقواعده](#view-or-edit-your-firewall-policies-and-custom-rules)**، التي تحدد حركة مرور الشبكة المسموح بتدفقها إلى أجهزة الشركة أو منها

- **[تصفية محتوى ويب](#set-up-web-content-filtering)**، مما يمنع الأشخاص من زيارة مواقع ويب معينة (عناوين URL) استنادا إلى فئات، مثل محتوى البالغين أو المسؤولية القانونية.

في Defender for Business، يتم تطبيق سياسات الأمان على الأجهزة من خلال [مجموعات الأجهزة](mdb-create-edit-device-groups.md#what-is-a-device-group). 

بالإضافة إلى سياسات الأمان، يمكنك عرض الإعدادات وتحريرها، مثل المنطقة الزمنية التي يجب استخدامها في مدخل Microsoft 365 Defender ([](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal)[https://security.microsoft.com](https://security.microsoft.com))، وما إذا كنت تريد تلقي ميزات المعاينة عندما تصبح متوفرة.

استخدم هذه المقالة كدليل لإدارة سياسات الأمان وإعداداتك.

## <a name="what-to-do"></a>ما يجب فعله

1. [اختر المكان الذي يمكنك فيه إدارة سياسات الأمان والأجهزة](#choose-where-to-manage-security-policies-and-devices).

2. [عرض سياسات حماية الجيل التالي أو تحريرها](#view-or-edit-your-next-generation-protection-policies).

3. [عرض سياسات جدار الحماية والقواعد المخصصة أو تحريرها](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [إعداد تصفية محتوى الويب](#set-up-web-content-filtering).

5. [عرض الإعدادات الأخرى وتحريرها في Microsoft 365 Defender المدخل](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

6. [تابع إلى الخطوات التالية](#next-steps).

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>اختيار مكان إدارة سياسات الأمان والأجهزة

يتميز Defender for Business [بعملية تكوين مبسطة](mdb-simplified-configuration.md) تساعد على تبسيط عملية الإعداد والتكوين. إذا حددت عملية التكوين المبسطة، يمكنك عرض سياسات الأمان وإدارتها في مدخل Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). ومع ذلك، لست مقتصرا على هذا الخيار. إذا كنت تستخدم إدارة نقاط النهاية من Microsoft (الذي يتضمن Microsoft Intune)، يمكنك الاستمرار في استخدام إدارة نقاط النهاية.

يمكن أن يساعدك الجدول التالي في اختيار مكان إدارة سياسات الأمان والأجهزة. <br/><br/>

| الخيار | الوصف |
|:---|:---|
| **استخدام Microsoft 365 Defender (***مستحسن*) | يمكن Microsoft 365 Defender المدخل ([https://security.microsoft.com/](https://security.microsoft.com/)) الخاص بك في مكان واحد لإدارة أجهزة الشركة ونهج الأمان وإعدادات الأمان. يمكنك الوصول إلى سياسات الأمان وإعداداتك[، واستخدام](mdb-view-tvm-dashboard.md) لوحة معلومات إدارة & الثغرات، وعرض الأحداث وإدارتها كلها في مكان واحد[](mdb-view-manage-incidents.md). <br/><br/>إذا كنت تستخدم إدارة نقاط النهاية من Microsoft، فإن الأجهزة التي قمت ب متنها إلى Defender for Business ونهج الأمان الخاصة بك مرئية في إدارة نقاط النهاية. لمعرفة المزيد، راجع المقالات التالية:<br/><br/>- [الإعدادات الافتراضية ل Defender for Business إدارة نقاط النهاية من Microsoft](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/><br/>- [جدار الحماية في Microsoft Defender for Business](mdb-firewall.md)   |
| **استخدام إدارة نقاط النهاية من Microsoft** | إذا كانت شركتك تستخدم إدارة نقاط النهاية (التي تتضمن Microsoft Intune) لإدارة سياسات الأمان، يمكنك الاستمرار في استخدام إدارة نقاط النهاية لإدارة الأجهزة ونهج الأمان. لمعرفة المزيد، راجع [إدارة أمان الجهاز باستخدام سياسات أمان نقاط النهاية في Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>إذا قررت التبديل إلى عملية التكوين المبسطة في [Defender for Business](mdb-simplified-configuration.md)، فسوف يتم مطالبتك بحذف أي نهج أمان موجودة في إدارة نقاط النهاية لتجنب تعارضات النهج في [وقت لاحق.](mdb-troubleshooting.yml) |

> [!IMPORTANT]
> إذا كنت تدير سياسات الأمان في مدخل Microsoft 365 Defender، يمكنك عرض هذه إدارة نقاط النهاية، المدرجة كنهج الحماية من الفيروسات أو جدار الحماية. عند عرض نهج جدار الحماية في إدارة نقاط النهاية، سترى نهجين مدرجين: نهج لحماية جدار الحماية، وآخر للقواعد المخصصة.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>عرض سياسات حماية الجيل التالي أو تحريرها

استنادا إلى ما إذا كنت تستخدم Microsoft 365 Defender أو إدارة نقاط النهاية من Microsoft لإدارة سياسات حماية الجيل التالي، استخدم أحد الإجراءات في الجدول التالي: <br/><br/>

| المدخل | الإجراء |
|:---|:---|
| Microsoft 365 Defender المدخل ([https://security.microsoft.com](https://security.microsoft.com)) | 1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول. <br/><br/>2. في جزء التنقل، اختر **تكوين الجهاز**. يتم تنظيم النهج حسب نظام التشغيل ونوع النهج.<br/><br/>3. حدد علامة تبويب نظام التشغيل (مثل Windows **العملاء**).<br/><br/>4. قم **بتوسيع حماية الجيل التالي** لعرض قائمة سياساتك.<br/><br/>5. حدد نهج لعرض مزيد من التفاصيل حول النهج. بإجراء تغييرات أو لمعرفة المزيد حول إعدادات النهج، راجع المقالات التالية: <br/>- [عرض سياسات الجهاز أو تحريرها](mdb-view-edit-policies.md)<br/>- [فهم إعدادات تكوين الجيل التالي](mdb-next-gen-configuration-settings.md)  |
| إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. انتقل إلى [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ثم سجل الدخول. أنت الآن في مركز إدارة إدارة نقاط النهاية من Microsoft.<br/><br/>2. حدد **أمان نقطة النهاية**.<br/><br/>3. حدد **برنامج الحماية من** الفيروسات لعرض سياساتك في هذه الفئة. <br/><br/>للحصول على المساعدة في إدارة إعدادات الأمان في إدارة نقاط النهاية من Microsoft، ابدأ بإدارة أمان نقطة النهاية [في Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>عرض سياسات جدار الحماية والقواعد المخصصة أو تحريرها

استنادا إلى ما إذا كنت تستخدم Microsoft 365 Defender أو إدارة نقاط النهاية من Microsoft لإدارة حماية جدار الحماية، استخدم أحد الإجراءات في الجدول التالي: <br/><br/>

| المدخل | الإجراء |
|:---|:---|
| Microsoft 365 Defender المدخل ([https://security.microsoft.com](https://security.microsoft.com)) | 1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول. <br/><br/>2. في جزء التنقل، اختر **تكوين الجهاز**. يتم تنظيم النهج حسب نظام التشغيل ونوع النهج.<br/><br/>3. حدد علامة تبويب نظام التشغيل (مثل Windows **العملاء**).<br/><br/>4. قم **بتوسيع جدار** الحماية لعرض قائمة سياساتك.<br/><br/>5. حدد نهج لعرض مزيد من التفاصيل حول النهج. بإجراء تغييرات أو لمعرفة المزيد حول إعدادات النهج، راجع المقالات التالية: <br/>- [عرض سياسات الجهاز أو تحريرها](mdb-view-edit-policies.md)<br/>- [إعدادات جدار الحماية](mdb-firewall.md)<br/>- [إدارة القواعد المخصصة لنهج جدار الحماية](mdb-custom-rules-firewall.md)  |
| إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. انتقل إلى [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ثم سجل الدخول. أنت الآن في مركز إدارة إدارة نقاط النهاية من Microsoft.<br/><br/>2. حدد **أمان نقطة النهاية**.<br/><br/>3. حدد **جدار الحماية** لعرض سياساتك في هذه الفئة. يتم سرد القواعد المخصصة المعرفة لحماية جدار الحماية كنهج منفصلة.<br/><br/>للحصول على المساعدة في إدارة إعدادات الأمان في إدارة نقاط النهاية من Microsoft، ابدأ بإدارة أمان نقطة النهاية [في Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>إعداد تصفية محتوى الويب

تمكن تصفية محتوى ويب فريق الأمان من تعقب إمكانية الوصول إلى مواقع الويب وتنظيمها استنادا إلى فئات المحتوى الخاصة بها، مثل:

- محتوى البالغين: المواقع ذات الصلة بالمجامع أو الجماع أو العري أو المواد الإباحية أو المواد الصريحة جنسيا أو العنف

- نطاق ترددي عال: تنزيل المواقع أو مواقع مشاركة الصور أو مضيفي النظير إلى النظير

- المسؤولية القانونية: المواقع التي تتضمن صور إساءة معاملة الأطفال، أو الترويج لأنشطة غير قانونية، أو تعزيز الانتحال أو الغش في المدرسة، أو التي تعزز الأنشطة الضارة

- الترفيه: المواقع التي توفر غرف محادثة مستندة إلى الويب أو الألعاب عبر الإنترنت أو البريد الإلكتروني المستند إلى الويب أو الشبكات الاجتماعية

- غير تصنيف: المواقع التي ليس لها محتوى أو المواقع المسجلة حديثا

لا تكون كل مواقع الويب الموجودة في هذه الفئات ضارة، ولكنها قد تسبب مشاكل للشركة بسبب لوائح التوافق أو استخدام النطاق الترددي أو مشاكل أخرى. بالإضافة إلى ذلك، يمكنك إنشاء نهج للتدقيق فقط للحصول على فهم أفضل حول ما إذا كان يجب على فريق الأمان حظر أي فئات موقع ويب.

تتوفر تصفية محتوى ويب على مستعرضات الويب الرئيسية، مع الكتل التي يتم تنفيذها بواسطة Windows Defender SmartScreen (Microsoft Edge) وحماية الشبكة (Chrome وFirefox وSواهم وأوبرا). لمزيد من المعلومات، راجع [المتطلبات الأساسية لتصفية محتوى الويب](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>لإعداد تصفية محتوى الويب

1. في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)**)، اختر الإعدادات** >  **تصفية المحتوىWeb** > **+ إضافة نهج**.

2. حدد اسما ووصفا لن نهجك.

3. حدد الفئات التي تريد حظرها. استخدم أيقونة التوسع لتوسيع كل فئة أصل بالكامل وتحديد فئات محتوى ويب معينة.

   لإعداد نهج التدقيق فقط الذي لا يمنع أي مواقع ويب، لا تحدد أي فئات.

   لا تحدد **غير محدد**.

4. حدد نطاق النهج عن طريق تحديد مجموعات الأجهزة لتطبيق النهج. سيتم منع الأجهزة الموجودة في مجموعات الأجهزة المحددة فقط من الوصول إلى مواقع الويب في الفئات المحددة.

5. راجع الملخص واحفظ النهج. قد يستغرق تحديث النهج ساعتين تقريبا لتطبيقه على أجهزتك المحددة.

> [!TIP]
> لمعرفة المزيد حول تصفية محتوى الويب، راجع [تصفية محتوى ويب](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>عرض الإعدادات الأخرى وتحريرها في مدخل Microsoft 365 Defender

بالإضافة إلى سياسات الأمان المطبقة على الأجهزة، هناك إعدادات أخرى يمكنك عرضها وتحريرها في Defender for Business. على سبيل المثال، يمكنك تحديد المنطقة الزمنية التي يجب استخدامها، كما يمكنك تشغيل الأجهزة (أو إيقاف تشغيلها). 

> [!NOTE]
> قد ترى إعدادات في المستأجر أكبر من تلك المذكورة في هذه المقالة. تسلط هذه المقالة الضوء على أهم الإعدادات التي يجب مراجعتها في Defender for Business.

### <a name="settings-to-review-for-defender-for-business"></a>الإعدادات مراجعة ل Defender for Business

يصف الجدول التالي الإعدادات التي تريد عرضها (والتحرير إذا لزم الأمر) في Defender for Business.

<br/><br/>

| الفئة | الإعداد | الوصف |
|:---|:---|:---|
| **مركز الأمان** | **المنطقة الزمنية** | حدد المنطقة الزمنية التي سيتم استخدامها في التواريخ والأزمنة المعروضة في الأحداث، والتهديدات المكتشفة، والتحري التلقائي & المعالجة. يمكنك إما استخدام UTC أو المنطقة الزمنية المحلية (*مستحسن*).  |
| **Microsoft 365 Defender** | **الحساب** | اشاهد التفاصيل، مثل مكان تخزين بياناتك وم ID المستأجر وم ID الخاص بك للمؤسسة (المؤسسة). |
| **Microsoft 365 Defender**  | **ميزات المعاينة**  | قم تشغيل ميزات المعاينة لتجرب الميزات القادمة والإمكانات الجديدة. يمكنك أن تكون من بين أول من يمكنه معاينة الميزات الجديدة وتقديم الملاحظات. |
| **نقاط النهاية**  | **إعلامات البريد الإلكتروني** | إعداد قواعد إعلام البريد الإلكتروني أو تحريرها. عند اكتشاف نقاط الضعف أو إنشاء تنبيه، سيتلقى المستلمون المحددون في قواعد إعلام البريد الإلكتروني رسالة بريد إلكتروني. [تعرف على المزيد حول إعلامات البريد الإلكتروني](mdb-email-notifications.md). |
| **نقاط النهاية**   | **إدارة الأجهزة** >  **الboarding** | الأجهزة المجهزة ل Defender for Business باستخدام برنامج نصي قابل للتنزيل. لمعرفة المزيد، راجع [الأجهزة المجهزة على Microsoft Defender for Business](mdb-onboard-devices.md).   |  
| **نقاط النهاية**  |  **إدارة الأجهزة** >  **إيقاف التشغيل** | أجهزة Offboard (إزالة) من Defender for Business. عند إيقاف تشغيل جهاز، لن يرسل البيانات إلى Defender for Business، ولكن يتم الاحتفاظ بالبيانات التي تم تلقيها قبل إيقاف التشغيل. لمعرفة المزيد، راجع [إيقاف تشغيل جهاز](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>الوصول إلى الإعدادات في مدخل Microsoft 365 Defender

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/))، ثم سجل الدخول.

2. حدد **الإعدادات**، ثم حدد فئة (مثل مركز الأمان أو **Microsoft 365 Defender أو** **نقاط النهاية**).

3. في قائمة الإعدادات، حدد عنصر لعرضه أو تحريره.


## <a name="next-steps"></a>الخطوات التالية

تابع إلى واحدة أو أكثر من المهام التالية:

- [بدء استخدام Microsoft Defender for Business](mdb-get-started.md)

- [إدارة الأجهزة في Microsoft Defender for Business](mdb-manage-devices.md)

- [عرض الأحداث وإدارتها في Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [عرض أو تحرير السياسات في Microsoft Defender for Business](mdb-view-edit-policies.md)
