---
title: عرض إعدادات الأمان وتحريرها في Microsoft Defender für Unternehmen
description: تكوين نهج الأمان في Microsoft Defender für Unternehmen
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
ms.openlocfilehash: 3d6ef3a7bc3ae9b7556041cedc88df354421f885
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746481"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>عرض نهج الأمان وإعداداتك وتحريرها في Microsoft Defender für Unternehmen

> [!IMPORTANT]
> يتم طرح Microsoft Defender für Unternehmen [للعملاء Microsoft 365 Business Premium](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم معاينة Defender for Business باعتباره اشتراكا مستقلا، وسيتم طرحه تدريجيا للعملاء وشركاء تكنولوجيا المعلومات الذين [يقومون بالتسجيل هنا](https://aka.ms/mdb-preview) لطلبه. تتضمن المعاينة [مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بانتظام.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالنواتج/الخدمات التي تم إصدارها مسبقا والتي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المقدمة هنا. 

## <a name="overview"></a>نظرة عامة

بعد إلحاق أجهزة شركتك Microsoft Defender für Unternehmen، تكون خطوتك التالية هي عرض نهج الأمان وإعداداتك وتحريرها إذا لزم الأمر. تتضمن نهج الأمان التي يجب تكوينها ما يلي:

- **[نهج الحماية من الجيل التالي](#view-or-edit-your-next-generation-protection-policies)**، التي تحدد الحماية من الفيروسات والحماية من البرامج الضارة لأجهزة شركتك
- **[حماية جدار الحماية والقواعد](#view-or-edit-your-firewall-policies-and-custom-rules)**، التي تحدد نسبة استخدام الشبكة المسموح لها بالتدفق من أو إلى أجهزة شركتك
- **[تصفية محتوى الويب](#set-up-web-content-filtering)**، والتي تمنع الأشخاص من زيارة مواقع ويب معينة (URLs) استنادا إلى فئات، مثل محتوى البالغين أو المسؤولية القانونية.

في Defender for Business، يتم تطبيق نهج الأمان على الأجهزة من خلال [مجموعات الأجهزة](mdb-create-edit-device-groups.md#what-is-a-device-group). 

بالإضافة إلى نهج الأمان، يمكنك [عرض الإعدادات وتحريرها](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal)، مثل المنطقة الزمنية التي يجب استخدامها في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وما إذا كنت تريد تلقي ميزات المعاينة عند توفرها.

استخدم هذه المقالة كدليل لإدارة نهج الأمان وإعداداتك.

## <a name="what-to-do"></a>ما يجب فعله

1. [اختر مكان إدارة نهج الأمان والأجهزة](#choose-where-to-manage-security-policies-and-devices).

2. [عرض نهج الحماية من الجيل التالي أو تحريرها](#view-or-edit-your-next-generation-protection-policies).

3. [عرض نهج جدار الحماية والقواعد المخصصة أو تحريرها](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [إعداد تصفية محتوى ويب](#set-up-web-content-filtering).

5. [عرض إعدادات أخرى وتحريرها في مدخل Microsoft 365 Defender](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

6. [تابع إلى خطواتك التالية](#next-steps).

>
> **هل لديك دقيقة؟**
> يرجى الاطلاع <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">على استطلاعنا القصير حول Microsoft Defender für Unternehmen</a>. يسعدنا أن نستمع إليك!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>اختيار مكان إدارة نهج الأمان والأجهزة

يتميز Defender for Business [بعملية تكوين مبسطة](mdb-simplified-configuration.md) تساعد على تبسيط عملية الإعداد والتكوين. إذا قمت بتحديد عملية التكوين المبسطة، يمكنك عرض نهج الأمان الخاصة بك وإدارتها في مدخل Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). ومع ذلك، لا تقتصر على هذا الخيار. إذا كنت تستخدم Microsoft Endpoint Manager (والتي تتضمن Microsoft Intune)، يمكنك الاستمرار في استخدام Endpoint Manager.

يمكن أن يساعدك الجدول التالي في اختيار مكان إدارة نهج الأمان والأجهزة. <br/><br/>

| الخيار | الوصف |
|:---|:---|
| **استخدام مدخل Microsoft 365 Defender** (*مستحسن*) | يمكن أن يكون مدخل Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) هو متجرك الوحيد لإدارة أجهزة شركتك ونهج الأمان وإعدادات الأمان. يمكنك الوصول إلى نهج الأمان وإعداداتك، واستخدام [لوحة معلومات إدارة المخاطر & الثغرات](mdb-view-tvm-dashboard.md) الأمنية، [وعرض الحوادث وإدارتها](mdb-view-manage-incidents.md) كلها في مكان واحد. <br/><br/>إذا كنت تستخدم Microsoft Endpoint Manager، فإن الأجهزة التي قمت بإلحاقها ب Defender for Business ونهج الأمان الخاصة بك مرئية في Endpoint Manager. لمعرفة المزيد، راجع المقالات التالية:<br/><br/>- [الإعدادات الافتراضية ل Defender for Business Microsoft Endpoint Manager](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/><br/>- [جدار الحماية في Microsoft Defender für Unternehmen](mdb-firewall.md)   |
| **استخدام Microsoft Endpoint Manager** | إذا كانت شركتك تستخدم بالفعل Endpoint Manager (والتي تتضمن Microsoft Intune) لإدارة نهج الأمان، يمكنك الاستمرار في استخدام Endpoint Manager لإدارة الأجهزة ونهج الأمان. لمعرفة المزيد، راجع [إدارة أمان الجهاز باستخدام نهج أمان نقطة النهاية في Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>إذا قررت التبديل إلى [عملية التكوين المبسطة في Defender for Business](mdb-simplified-configuration.md)، فستتم مطالبتك بحذف أي نهج أمان موجودة في Endpoint Manager لتجنب [تعارضات النهج](mdb-troubleshooting.yml) لاحقا. |

> [!IMPORTANT]
> إذا كنت تدير نهج الأمان في مدخل Microsoft 365 Defender، يمكنك *عرض* هذه النهج في Endpoint Manager، المدرجة كنهج الحماية من الفيروسات أو جدار الحماية. عند عرض نهج جدار الحماية في Endpoint Manager، سترى نهجين مدرجين: نهج لحماية جدار الحماية، والآخر للقواعد المخصصة.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>عرض نهج الحماية من الجيل التالي أو تحريرها

استنادا إلى ما إذا كنت تستخدم مدخل Microsoft 365 Defender أو Microsoft Endpoint Manager لإدارة نهج الحماية من الجيل التالي، استخدم أحد الإجراءات في الجدول التالي: <br/><br/>

| المدخل | الاجراء |
|:---|:---|
| مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول. <br/><br/>2. في جزء التنقل، اختر **تكوين الجهاز**. يتم تنظيم النهج حسب نظام التشغيل ونوع النهج.<br/><br/>3. حدد علامة تبويب نظام التشغيل (مثل **Windows العملاء**).<br/><br/>4. قم بتوسيع **حماية الجيل التالي** لعرض قائمة النهج.<br/><br/>5. حدد نهجا لعرض مزيد من التفاصيل حول النهج. لإجراء تغييرات أو لمعرفة المزيد حول إعدادات النهج، راجع المقالات التالية: <br/>- [عرض نهج الجهاز أو تحريرها](mdb-view-edit-policies.md)<br/>- [فهم إعدادات تكوين الجيل التالي](mdb-next-gen-configuration-settings.md)  |
| مركز إدارة Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. انتقل إلى [https://endpoint.microsoft.com](https://endpoint.microsoft.com) وسجل الدخول. أنت الآن في مركز إدارة Microsoft Endpoint Manager.<br/><br/>2. حدد **أمان نقطة النهاية**.<br/><br/>3. حدد **برنامج الحماية من الفيروسات** لعرض النهج الخاصة بك في تلك الفئة. <br/><br/>للحصول على المساعدة في إدارة إعدادات الأمان في Microsoft Endpoint Manager، ابدأ [بإدارة أمان نقطة النهاية في Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>عرض نهج جدار الحماية والقواعد المخصصة أو تحريرها

استنادا إلى ما إذا كنت تستخدم مدخل Microsoft 365 Defender أو Microsoft Endpoint Manager لإدارة حماية جدار الحماية، استخدم أحد الإجراءات في الجدول التالي: <br/><br/>

| المدخل | الاجراء |
|:---|:---|
| مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول. <br/><br/>2. في جزء التنقل، اختر **تكوين الجهاز**. يتم تنظيم النهج حسب نظام التشغيل ونوع النهج.<br/><br/>3. حدد علامة تبويب نظام التشغيل (مثل **Windows العملاء**).<br/><br/>4. قم بتوسيع **جدار الحماية** لعرض قائمة النهج.<br/><br/>5. حدد نهجا لعرض مزيد من التفاصيل حول النهج. لإجراء تغييرات أو لمعرفة المزيد حول إعدادات النهج، راجع المقالات التالية: <br/>- [عرض نهج الجهاز أو تحريرها](mdb-view-edit-policies.md)<br/>- [إعدادات جدار الحماية](mdb-firewall.md)<br/>- [إدارة القواعد المخصصة لنهج جدار الحماية](mdb-custom-rules-firewall.md)  |
| مركز إدارة Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. انتقل إلى [https://endpoint.microsoft.com](https://endpoint.microsoft.com) وسجل الدخول. أنت الآن في مركز إدارة Microsoft Endpoint Manager.<br/><br/>2. حدد **أمان نقطة النهاية**.<br/><br/>3. حدد **جدار الحماية** لعرض النهج الخاصة بك في تلك الفئة. يتم سرد القواعد المخصصة التي تم تعريفها لحماية جدار الحماية كنهج منفصلة.<br/><br/>للحصول على المساعدة في إدارة إعدادات الأمان في Microsoft Endpoint Manager، ابدأ [بإدارة أمان نقطة النهاية في Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>إعداد تصفية محتوى ويب

تمكن تصفية محتوى الويب فريق الأمان من تعقب الوصول إلى مواقع الويب وتنظيمه استنادا إلى فئات المحتوى الخاصة به، مثل:

- محتوى البالغين: المواقع ذات الصلة بالهواة أو الوثب أو العري أو المواد الإباحية أو المواد الصريحة من الناحية الجنسية أو أعمال الجنس

- النطاق الترددي العالي: تنزيل المواقع أو مواقع مشاركة الصور أو مضيفي نظير إلى نظير

- المسؤولية القانونية: المواقع التي تتضمن صور إساءة معاملة الأطفال، أو الترويج للأنشطة غير القانونية، أو تعزيز المسؤولية القانونية أو خداع المدرسة، أو التي تعزز الأنشطة الضارة

- الترفيه: المواقع التي توفر غرف المحادثة المستندة إلى الويب أو الألعاب عبر الإنترنت أو البريد الإلكتروني المستند إلى الويب أو الشبكات الاجتماعية

- غير مصنف: المواقع التي لا تحتوي على محتوى أو المسجلة حديثا

ليست كل مواقع الويب في هذه الفئات ضارة، ولكنها قد تشكل مشكلة لشركتك بسبب لوائح التوافق أو استخدام النطاق الترددي أو مخاوف أخرى. بالإضافة إلى ذلك، يمكنك إنشاء نهج للتدقيق فقط للحصول على فهم أفضل لما إذا كان يجب على فريق الأمان حظر أي فئات لموقع ويب.

تتوفر تصفية محتوى الويب على مستعرضات الويب الرئيسية، مع الكتل التي يتم تنفيذها بواسطة Windows Defender SmartScreen (Microsoft Edge) وحماية الشبكة (Chrome وFirefox وFirefox وFireed و Opera). لمزيد من المعلومات، راجع [المتطلبات الأساسية لتصفية محتوى الويب](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>لإعداد تصفية محتوى ويب

1. في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، اختر **الإعدادات** >  **Web content filtering** > **+ Add policy**.

2. حدد اسما ووصفا لنهجك.

3. حدد فئات لحظرها. استخدم أيقونة التوسيع لتوسيع كل فئة أصل بالكامل وتحديد فئات محتوى ويب معينة.

   لإعداد نهج للتدقيق فقط لا يمنع أي مواقع ويب، لا تحدد أي فئات.

   لا تحدد **"غير مصنف".**

4. حدد نطاق النهج عن طريق تحديد مجموعات الأجهزة لتطبيق النهج. سيتم منع الأجهزة في مجموعات الأجهزة المحددة فقط من الوصول إلى مواقع الويب في الفئات المحددة.

5. راجع الملخص واحفظ النهج. قد يستغرق تحديث النهج ما يصل إلى ساعتين لتطبيقه على أجهزتك المحددة.

> [!TIP]
> لمعرفة المزيد حول تصفية محتوى ويب، راجع [تصفية محتوى ويب](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>عرض الإعدادات الأخرى وتحريرها في مدخل Microsoft 365 Defender

بالإضافة إلى نهج الأمان التي يتم تطبيقها على الأجهزة، هناك إعدادات أخرى يمكنك عرضها وتحريرها في Defender for Business. على سبيل المثال، يمكنك تحديد المنطقة الزمنية التي يجب استخدامها، ويمكنك إلحاق (أو إلغاء إلحاق) الأجهزة. 

> [!NOTE]
> قد ترى المزيد من الإعدادات في المستأجر أكثر مما هو مدرج في هذه المقالة. تسلط هذه المقالة الضوء على أهم الإعدادات التي يجب مراجعتها في Defender for Business.

### <a name="settings-to-review-for-defender-for-business"></a>الإعدادات المراجعة ل Defender for Business

يصف الجدول التالي الإعدادات لعرض (وإذا لزم الأمر، تحرير) في Defender for Business.

<br/><br/>

| الفئة | اعداد | الوصف |
|:---|:---|:---|
| **مركز الأمان** | **المنطقة الزمنية** | حدد المنطقة الزمنية التي سيتم استخدامها للتواريخ والأوقات المعروضة في الحوادث والتهديدات المكتشفة والتحقيق التلقائي & المعالجة. يمكنك إما استخدام التوقيت العالمي المتفق عليه أو المنطقة الزمنية المحلية (*مستحسن*).  |
| **Microsoft 365 Defender** | **حساب** | عرض التفاصيل، مثل مكان تخزين بياناتك ومعرف المستأجر ومعرف مؤسستك (المؤسسة). |
| **Microsoft 365 Defender**  | **ميزات المعاينة**  | قم بتشغيل ميزات المعاينة لتجربة الميزات القادمة والقدرات الجديدة. يمكنك أن تكون من بين أول من يقوم بمعاينة الميزات الجديدة وتقديم الملاحظات. |
| **النهايه**  | **إعلامات البريد الإلكتروني** | إعداد قواعد إعلام البريد الإلكتروني أو تحريرها. عند اكتشاف الثغرات الأمنية أو إنشاء تنبيه، سيتلقى المستلمون المحددون في قواعد إعلام البريد الإلكتروني رسالة بريد إلكتروني. [تعرف على المزيد حول إعلامات البريد الإلكتروني](mdb-email-notifications.md). |
| **النهايه**   | **إدارة** >  الأجهزة **الإلحاق** | إلحاق الأجهزة ب Defender for Business باستخدام برنامج نصي قابل للتنزيل. لمعرفة المزيد، راجع [إلحاق الأجهزة Microsoft Defender für Unternehmen](mdb-onboard-devices.md).   |  
| **النهايه**  |  **إدارة** >  الأجهزة **إيقاف الإلحاق** | إيقاف تشغيل (إزالة) الأجهزة من Defender for Business. عند إيقاف تشغيل جهاز، فإنه لم يعد يرسل البيانات إلى Defender for Business، ولكن يتم الاحتفاظ بالبيانات التي تم تلقيها قبل الإلحاق. لمعرفة المزيد، راجع ["إيقاف تشغيل الجهاز](mdb-onboard-devices.md#offboarding-a-device)".  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>الوصول إلى إعداداتك في مدخل Microsoft 365 Defender

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/))، وسجل الدخول.

2. حدد **الإعدادات**، ثم حدد فئة (مثل **مركز الأمان** **أو Microsoft 365 Defender** أو **نقاط النهاية**).

3. في قائمة الإعدادات، حدد عنصرا لعرضه أو تحريره.


## <a name="next-steps"></a>الخطوات التالية

تابع إلى مهمة واحدة أو أكثر من المهام التالية:

- [بدء استخدام Microsoft Defender für Unternehmen](mdb-get-started.md)
- [إدارة الأجهزة في Microsoft Defender für Unternehmen](mdb-manage-devices.md)
- [عرض الحوادث وإدارتها في Microsoft Defender für Unternehmen](mdb-view-manage-incidents.md)
- [عرض النهج أو تحريرها في Microsoft Defender für Unternehmen](mdb-view-edit-policies.md)
