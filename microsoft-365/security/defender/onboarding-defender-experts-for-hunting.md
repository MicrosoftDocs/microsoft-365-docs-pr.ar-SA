---
title: كيفية الاشتراك في خبراء Microsoft Defender للتتبع
ms.reviewer: ''
description: إذا كنت جديدا على Microsoft 365 Defender و Defender Experts for Hunting، فهذه هي الطريقة التي تشترك بها
keywords: خدمة تتبع التهديدات المدارة، وتتبع التهديدات المدارة، وخدمة الكشف والاستجابة المدارة (MDR)، وMTE، خبراء المخاطر في Microsoft، وMTE-TAN، وإخطار الهجوم المستهدف، وإعلامات خبراء الدفاع، وإعلامات هجوم نقطة النهاية، وخبراء Microsoft Defender للتتبع، وتتبع التهديدات وتحليلها.
search.product: Windows 10
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: vpattnaik
author: vpattnai
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: aab1c0661ce039e6a9fb561c2e93f71e2c5847d6
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67171646"
---
# <a name="start-using-microsoft-defender-experts-for-hunting"></a>بدء استخدام خبراء Microsoft Defender للتتبع

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="onboarding"></a>الإلحاق

إذا كنت جديدا على Microsoft 365 Defender وخبراء Defender للتتبع:  

1. عند تلقي بريدك الإلكتروني الترحيبي، حدد **"تسجيل الدخول إلى Microsoft 365 Defender**".
2. سجل الدخول إذا كان لديك حساب Microsoft بالفعل. إذا لم يكن هناك أي شيء، ف قم بإنشاء واحد.
3. ستساعدك الجولة السريعة Microsoft 365 Defender على التعرف على مجموعة الأمان ومكان وجود الإمكانات ومدى أهميتها. حدد **القيام بجولة سريعة**.  
4. اقرأ الأوصاف المختصر حول ماهية خدمة خبراء Microsoft Defender والقدرات التي توفرها. حدد **التالي**. سترى صفحة الترحيب:

![لقطة شاشة لصفحة الترحيب Microsoft 365 Defender مع بطاقة لخدمة Defender Experts for Hunting.](../../media/mte/defenderexperts/start-using-defender-experts-for-hunting.png)

## <a name="receive-defender-experts-notifications"></a>تلقي إعلامات خبراء Defender

تتضمن خدمة Defender Experts Notifications ما يلي:
- مراقبة التهديدات وتحليلها، ما يقلل من وقت الوداع والمخاطر التي تتعرض لها شركتك
- الذكاء الاصطناعي المدرب على التتبع لاكتشاف الهجمات المعروفة والتهديدات الناشئة واستهدافها 
- تحديد المخاطر الأكثر صلة، مما يساعد SOCs على زيادة فعاليتها إلى أقصى حد 
- المساعدة في تحديد نطاق الاختراقات والسياق بقدر ما يمكن تسليمه بسرعة لتمكين استجابة SOC السريعة 

راجع لقطة الشاشة التالية لمشاهدة نموذج إعلام Defender Experts:

![لقطة شاشة لإشعار خبراء Defender في Microsoft 365 Defender. يتضمن إعلام Defender Expert عنوانا يصف التهديد أو النشاط الذي تمت ملاحظته، وملخصا تنفيذيا، وقائمة بالتوصيات.](../../media/mte/defenderexperts/receive-defender-experts-notification.png)

### <a name="where-youll-find-defender-experts-notifications"></a>حيث ستجد إشعارات خبراء Defender

يمكنك تلقي إشعارات خبراء Defender من خبراء Defender من خلال الوسائط التالية: 

- صفحة [أحداث](https://security.microsoft.com/incidents?tid=f839b112-d9d7-4d27-9bf6-94542403f21c) مدخل Microsoft 365 Defender
- صفحة [تنبيهات](https://security.microsoft.com/alerts?tid=f839b112-d9d7-4d27-9bf6-94542403f21c) مدخل Microsoft 365 Defender
- [واجهة برمجة تطبيقات](../../security/defender-endpoint/get-alerts.md) تنبيه OData [وواجهة برمجة تطبيقات REST](../defender-endpoint/configure-siem.md)
- جدول [DeviceAlertEvents](../../security/defender-endpoint/advanced-hunting-devicealertevents-table.md) في التتبع المتقدم

### <a name="filter-to-view-just-the-defender-experts-notifications"></a>تصفية لعرض إعلامات خبراء Defender فقط

يمكنك تصفية الحوادث والتنبيهات إذا كنت تريد فقط رؤية إشعارات خبراء Defender من بين العديد من التنبيهات. للقيام بذلك:

1. في قائمة التنقل، انتقل إلى **Incidents & alerts Incidents** >  > حدد أيقونة ![Filter.](../../media/mte/defenderexperts/filter.png)
2. قم بالتمرير لأسفل وصولا إلى حقل **العلامات** > حدد خانة الاختيار **Defender Experts** .
3. حدد **Apply**.

### <a name="collaborate-with-experts-on-demand"></a>التعاون مع الخبراء عند الطلب

> [!NOTE]
> يتم تضمين الخبراء عند الطلب في اشتراك Defender Experts for Hunting مع تخصيصات شهرية. ومع ذلك، فهي ليست خدمة استجابة لحوادث الأمان. يهدف إلى توفير فهم أفضل للتهديدات المعقدة التي تؤثر على مؤسستك. شارك مع فريق الاستجابة للحوادث الأمنية لمعالجة مشكلات الاستجابة العاجلة لحوادث الأمان. إذا لم يكن لديك فريق الاستجابة لحوادث الأمان الخاصة بك وترغب في الحصول على مساعدة Microsoft، ف قم بإنشاء طلب دعم في [Premier Services Hub](/services-hub/).

حدد **Ask Defender Experts** مباشرة داخل مدخل أمان Microsoft 365 للحصول على استجابات سريعة ودقيقة لجميع أسئلة تتبع التهديدات. يمكن للخبراء توفير رؤى لفهم التهديدات المعقدة التي قد تواجهها مؤسستك بشكل أفضل. يمكن للخبراء عند الطلب المساعدة في: 

- جمع معلومات إضافية حول التنبيهات والحوادث، بما في ذلك الأسباب الجذرية والنطاق
- اكتساب الوضوح في الأجهزة أو التنبيهات أو الحوادث المشبوهة واتخاذ الخطوات التالية إذا واجهت مهاجما متقدما
- تحديد المخاطر والحماية المتاحة المتعلقة بالجهات الفاعلة في التهديدات أو الحملات أو تقنيات المهاجمين الناشئين

يتوفر خيار **Ask Defender Experts** في عدة أماكن في جميع أنحاء المدخل:

- ***قائمة إجراءات صفحة الجهاز***

![لقطة شاشة لخيار القائمة Ask Defender Experts في قائمة إجراء صفحة الجهاز في مدخل Microsoft 365 Defender.](../../media/mte/defenderexperts/device-page-actions-menu.png)

- ***القائمة المنبثقة لصفحة مخزون الجهاز***

![لقطة شاشة لخيار القائمة Ask Defender Experts في القائمة المنبثقة لصفحة مخزون الجهاز في مدخل Microsoft 365 Defender.](../../media/mte/defenderexperts/device-inventory-flyout-menu.png)

- ***القائمة المنبثقة لصفحة التنبيهات***

![لقطة شاشة لخيار القائمة «Ask Defender Experts» في القائمة المنبثقة لصفحة «Alerts» في مدخل Microsoft 365 Defender.](../../media/mte/defenderexperts/alerts-flyout-menu.png)

- ***قائمة إجراءات صفحة الأحداث***

![لقطة شاشة لخيار القائمة Ask Defender Experts في قائمة إجراءات صفحة «Incidents» في مدخل Microsoft 365 Defender.](../../media/mte/defenderexperts/incidents-page-actions-menu.png)

> [!NOTE]
> إذا كنت ترغب في تعقب حالة حالات الخبراء عند الطلب من خلال Microsoft Services Hub، فتواصل مع Customer Success Account Manager. شاهد هذا [الفيديو](https://www.microsoft.com/videoplayer/embed/RE4pk9f) للحصول على نظرة عامة سريعة على مركز خدمات Microsoft.

## <a name="sample-questions-you-can-ask-from-defender-experts"></a>أسئلة نموذجية يمكنك طرحها من خبراء Defender

### <a name="alert-information"></a>معلومات التنبيه

- رأينا نوعا جديدا من التنبيه ثنائيا للحياة خارج الأرض. يمكننا توفير معرف التنبيه. هل يمكنك إخبارنا بالمزيد عن هذا التنبيه وما إذا كان مرتبطا بأي حادث وكيف يمكننا التحقيق فيه بشكل أكبر؟
- لقد لاحظنا هجومين متشابهين، يحاول كلاهما تنفيذ برامج PowerShell النصية الضارة ولكنهما ينشئان تنبيهات مختلفة. أحدهما هو "سطر أوامر PowerShell مريب" والآخر هو "تم الكشف عن ملف ضار بناء على الإشارة التي يوفرها O365". ما الفرق؟
- تلقينا تنبيها فرديا اليوم حول عدد غير طبيعي من عمليات تسجيل الدخول الفاشلة من جهاز مستخدم رفيع المستوى. لا يمكننا العثور على أي دليل إضافي لهذه المحاولات. كيف يمكن Microsoft 365 Defender رؤية هذه المحاولات؟ ما نوع تسجيلات الدخول التي تتم مراقبتها؟
- هل يمكنك إعطاء المزيد من السياق أو التحليلات حول التنبيه وأي حوادث ذات صلة، "تمت ملاحظة السلوك المشبوه من قبل أداة مساعدة النظام"؟
- لاحظت تنبيها بعنوان "إنشاء قاعدة إعادة التوجيه/إعادة التوجيه". أعتقد أن النشاط غير آمن. هل يمكنك إعلامي بسبب تلقيي تنبيها؟

### <a name="possible-device-compromise"></a>اختراق محتمل للجهاز

- هل يمكنك المساعدة في شرح سبب ظهور رسالة أو تنبيه "تمت ملاحظة عملية غير معروفة" على العديد من الأجهزة في مؤسستنا؟ نحن نقدر أي مدخلات لتوضيح ما إذا كانت هذه الرسالة أو التنبيه مرتبطا بنشاط أو أحداث ضارة.
- هل يمكنك المساعدة في التحقق من صحة حل وسط محتمل على النظام التالي، التتبع من الأسبوع الماضي؟ إنه يعمل بشكل مماثل للكشف السابق عن البرامج الضارة على نفس النظام منذ ستة أشهر.

### <a name="threat-intelligence-details"></a>تفاصيل التحليل الذكي للمخاطر

- اكتشفنا رسالة بريد إلكتروني للتصيد الاحتيالي قامت بتسليم مستند Word ضار إلى مستخدم. تسبب المستند في سلسلة من الأحداث المشبوهة، ما أدى إلى تشغيل تنبيهات متعددة لعائلة برامج ضارة معينة. هل لديك أي معلومات حول هذه البرامج الضارة؟ إذا كان الجواب نعم، هل يمكنك إرسال ارتباط إلينا؟
- لقد رأينا مؤخرا منشور مدونة حول تهديد يستهدف صناعتنا. هل يمكنك مساعدتنا على فهم الحماية التي يوفرها Microsoft 365 Defender ضد هذا العامل من المخاطر؟
- لقد لاحظنا مؤخرا حملة تصيد احتيالي تم إجراؤها ضد مؤسستنا. هل يمكنك إخبارنا ما إذا كان هذا مستهدفا على وجه التحديد لشركتنا أو عموديا؟

### <a name="microsoft-defender-experts-for-hunting-alert-communications"></a>Microsoft Defender Experts لاتصالات تنبيه التتبع

- هل يمكن لفريق الاستجابة للحوادث مساعدتنا في معالجة إعلام الهجوم المستهدف الذي تلقيناه؟
- تلقينا هذا إعلام خبراء Defender من خبراء Microsoft Defender للتتبع. ليس لدينا فريق الاستجابة للحوادث الخاص بنا. ماذا يمكننا أن نفعل الآن، وكيف يمكننا احتواء الحادث؟
- تلقينا إعلام Defender Experts من خبراء Microsoft Defender للتتبع. ما هي البيانات التي يمكنك توفيرها لنا والتي يمكننا تمريرها إلى فريق الاستجابة للحوادث لدينا؟

### <a name="next-step"></a>الخطوة التالية

- [فهم تقرير Defender Experts for Hunting في Microsoft 365 Defender](defender-experts-report.md)
