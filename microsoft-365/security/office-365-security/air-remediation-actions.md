---
title: إجراءات الإصلاح في Microsoft Defender Office 365
keywords: AIR، autoIR، Microsoft Defender ل Endpoint، تلقائي، تحقيق، استجابة، معالجة، تهديدات، متقدم، خطر، حماية
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: تعرف على إجراءات الإصلاح بعد إجراء تحقيق تلقائي في Microsoft Defender Office 365.
ms.date: 04/30/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5435c063234c2b803e172d6cdc06ff0b9bf417b2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568117"
---
# <a name="remediation-actions-in-microsoft-defender-for-office-365"></a>إجراءات الإصلاح في Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="remediation-actions"></a>إجراءات المعالجة

تتضمن ميزات الحماية من المخاطر في [Microsoft Defender Office 365](defender-for-office-365.md) إجراءات إصلاح معينة. يمكن أن تتضمن إجراءات الإصلاح هذه ما يلي:

- حذف رسائل البريد الإلكتروني أو المجموعات بشكل غير مهين
- حظر URL (وقت النقر)
- إيقاف تشغيل إعادة توجيه البريد الخارجي
- إيقاف تشغيل الوافت

في Microsoft Defender Office 365، لا يتم اتخاذ إجراءات المعالجة تلقائيا. بدلا من ذلك، يتم اتخاذ إجراءات الإصلاح فقط عند موافقة فريق عمليات الأمان في مؤسستك.

## <a name="threats-and-remediation-actions"></a>التهديدات والإجراءات الإصلاحية

يتضمن Microsoft Defender Office 365 إجراءات المعالجة لمعالجة التهديدات المختلفة. غالبا ما تؤدي عمليات التحقيق التلقائية إلى إجراء واحد أو أكثر من إجراءات الإصلاح لمراجعتها والموافقة عليها. في بعض الحالات، لا يؤدي إجراء تحقيق تلقائي إلى إجراء إصلاح معين. لمزيد من التحقق واتخاذ الإجراءات المناسبة، استخدم الإرشادات في الجدول التالي.

|الفئة|التهديدات/المخاطر|إجراء (إجراءات) الإصلاح|
|:---|:---|:---|
|البريد الإلكتروني|البرامج الضارة|حذف رسالة بريد إلكتروني/كتلة بشكل غير مهين <p> إذا احتوى أكثر من مجموعة من رسائل البريد الإلكتروني في مجموعة على برامج ضارة، فإن نظام المجموعة يعتبر ضارا.|
|البريد الإلكتروني|URL ضار <br> (تم الكشف عن عنوان URL ضار بواسطة [خزينة الارتباطات](safe-links.md)).)|حذف رسالة بريد إلكتروني/كتلة بشكل غير مهين <br> حظر URL (التحقق من وقت النقر) <p> يعتبر البريد الإلكتروني الذي يحتوي على عنوان URL ضار ضارا.|
|البريد الإلكتروني|التصيد الاحتيالي|حذف رسالة بريد إلكتروني/كتلة بشكل غير مهين <p> إذا احتوى أكثر من مجموعة من رسائل البريد الإلكتروني في مجموعة على محاولات تصيد احتيالي، فإن المجموعة بأكملها تعتبر محاولة تصيد احتيالي.|
|البريد الإلكتروني|تصيد احتيالي تم استغلاله <br> (تم تسليم رسائل البريد الإلكتروني ثم [تم التعثر عليها](zero-hour-auto-purge.md).)|حذف رسالة بريد إلكتروني/كتلة بشكل غير مهين <p> تتوفر التقارير لعرض الرسائل التي تم استغلالها. [تعرف على ما إذا كان ZAP قد نقل رسالة وال الأسئلة المفهمة](zero-hour-auto-purge.md#how-to-see-if-zap-moved-your-message).|
|البريد الإلكتروني|البريد الإلكتروني التصيد الاحتيالي [الذي تم تسجيله](enable-the-report-message-add-in.md) بواسطة مستخدم|[التحقيق التلقائي الذي يتم تشغيله بواسطة تقرير المستخدم](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|البريد الإلكتروني|الشذوذ في مستوى الصوت <br> (تتجاوز الكميات الأخيرة من البريد الإلكتروني الفترة السابقة من 7 إلى 10 أيام لمطابقة المعايير.)|لا يؤدي إجراء التحقيق التلقائي إلى اتخاذ إجراء محدد معلق. <p>لا يشكل الشذوذ في الحجم خطرا واضحا، بل هو مجرد إشارة إلى حجم بريد إلكتروني أكبر في الأيام الأخيرة مقارنة بالشهرين الماضيين من 7 إلى 10 أيام. <p>على الرغم من أن وجود كمية كبيرة من رسائل البريد الإلكتروني قد يشير إلى وجود مشاكل محتملة، إلا أن التأكيد مطلوب إما من حيث الأحكام الضارة أو المراجعة اليدوية لرسائل/مجموعات البريد الإلكتروني. راجع [البحث عن بريد إلكتروني مريب تم تسليمه](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered).|
|البريد الإلكتروني|لم يتم العثور على أي تهديدات <br> (لم يعثر النظام على أي تهديدات بالاستناد إلى الملفات أو عناوين URL أو تحليل الأحكام الصادرة عن مجموعات البريد الإلكتروني.)|لا يؤدي إجراء التحقيق التلقائي إلى اتخاذ إجراء محدد معلق. <p>لا تنعكس التهديدات التي [](zero-hour-auto-purge.md) يتم العثور عليها أو تم استغلالها بعد اكتمال التحقيق في نتائج التحقيق الرقمية، ولكن يمكن عرض مثل هذه التهديدات في "مستكشف [التهديدات](threat-explorer.md)".|
|User|قام مستخدم بالنقر فوق عنوان URL ضار <br> (انتقل مستخدم إلى صفحة تم العثور عليها لاحقا على أنها ضارة، أو تجاوز مستخدم صفحة تحذير ارتباطات [خزينة](safe-links.md#warning-pages-from-safe-links) للانتقال إلى صفحة ضارة.)|لا يؤدي إجراء التحقيق التلقائي إلى اتخاذ إجراء محدد معلق. <p> حظر URL (وقت النقر) <p> استخدم "مستكشف التهديدات [" لعرض بيانات حول عناوين URL والنقر فوق الأحكام](threat-explorer.md#view-phishing-url-and-click-verdict-data). <p> إذا كانت مؤسستك تستخدم [Microsoft Defender لنقطة](/windows/security/threat-protection/) النهاية، فنظر في التحقق من [المستخدم](/microsoft-365/security/defender-endpoint/investigate-user) لتحديد ما إذا كان حسابه قد تم اختراقه.|
|User|يرسل مستخدم البرامج الضارة/التصيد الاحتيالي|لا يؤدي إجراء التحقيق التلقائي إلى اتخاذ إجراء محدد معلق. <p> قد يقوم المستخدم بالإبلاغ عن البرامج الضارة/التصيد الاحتيالي، أو أن أحد الأشخاص قد ينتحل [من](anti-spoofing-protection.md) المستخدم كجزء من هجوم. استخدم ["مستكشف التهديدات](threat-explorer.md) " لعرض البريد الإلكتروني الذي يحتوي على [البرامج الضارة](threat-explorer-views.md#email--malware) أو [التصيد الاحتيالي والتعامل معه](threat-explorer-views.md#email--phish).|
|User|إعادة توجيه البريد الإلكتروني <br> (يتم تكوين قواعد إعادة توجيه علبة البريد، ويمكن استخدام chch لطرح البيانات.)|إزالة قاعدة إعادة توجيه <p> استخدم [تحليلات تدفق البريد](mail-flow-insights-v2.md)، بما في ذلك [](mfi-auto-forwarded-messages-report.md)تقرير الرسائل المرسلة بشكل تلقائي، لعرض تفاصيل أكثر تحديدا حول البريد الإلكتروني الذي تم إعادة توجيهه.|
|User|قواعد إرسال البريد الإلكتروني <br> (تم إعداد التكاتف لحساب المستخدم.)|إزالة قاعدة الحذف <p> إذا كانت مؤسستك تستخدم [Microsoft Defender ل Endpoint،](/windows/security/threat-protection/) فنظر [](/microsoft-365/security/defender-endpoint/investigate-user) في التحقق من المستخدم الذي يحصل على إذن التكفيح.|
|User|exfiltration البيانات <br> (قام مستخدم بانتهاك سياسات [DLP](../../compliance/dlp-learn-about-dlp.md) الخاصة بالبريد الإلكتروني أو مشاركة الملفات |لا يؤدي إجراء التحقيق التلقائي إلى اتخاذ إجراء محدد معلق. <p> [عرض تقارير DLP واتخاذ إجراء](../../compliance/view-the-dlp-reports.md).|
|User|إرسال بريد إلكتروني غير متجانس <br> (أرسل مستخدم مؤخرا بريدا إلكترونيا يزيد عن عدد الأيام ال 7 إلى 10 السابقة.)|لا يؤدي إجراء التحقيق التلقائي إلى اتخاذ إجراء محدد معلق. <p> لا يعد إرسال كمية كبيرة من البريد الإلكتروني ضارا بحد ذاته؛ من المحتمل أن يكون المستخدم قد أرسل بريدا إلكترونيا إلى مجموعة كبيرة من المستلمين لحدث ما. للتحقق [، استخدم تحليلات](mail-flow-insights-v2.md) تدفق البريد، بما في ذلك تقرير خريطة [تدفق](mfi-mail-flow-map-report.md) البريد لتحديد ما يحدث واتخاذ إجراء.|

## <a name="next-steps"></a>الخطوات التالية

- [عرض تفاصيل ونتائج التحقيق التلقائي في Microsoft Defender Office 365](air-view-investigation-results.md)
- [عرض إجراءات المعالجة المعلقة أو المكتملة بعد إجراء تحقيق تلقائي في Microsoft Defender Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [التعرف على التحقيق التلقائي في Microsoft Defender ل Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [تعرف على الإمكانات في Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
