---
title: تكوين قدرات خبراء المخاطر في Microsoft وإدارتها
ms.reviewer: ''
description: سجل في Microsoft Threats Experts لتكوينه وإدارته واستخدامه في عمليات الأمان اليومية الخاصة بك وعمل إدارة الأمان.
keywords: خبراء المخاطر في Microsoft، وخدمة تتبع التهديدات المدارة، وMTE، وخدمة التتبع المدارة من Microsoft
search.product: Windows 10
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dolmont
author: DulceMontemayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7661619ccb60bb55020a8e241c341b11fe45abd1
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487300"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities"></a>تكوين قدرات خبراء المخاطر في Microsoft وإدارتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>قبل البدء

> [!NOTE]
> ناقش متطلبات الأهلية مع موفر خدمة Microsoft التقنية وفريق الحساب قبل التقدم بطلب إلى خبراء المخاطر في Microsoft - خدمة تتبع المخاطر المدارة للإعلام بالهجوم المستهدف.

تأكد من نشر Defender لنقطة النهاية في بيئتك مع الأجهزة المسجلة، وليس فقط على إعداد المختبر.

إذا كنت عميل Defender لنقطة النهاية، فأنت بحاجة إلى التقدم بطلب **للحصول على خبراء المخاطر في Microsoft - إعلامات الهجوم المستهدف** للحصول على رؤى وتحليلات خاصة للمساعدة في تحديد التهديدات الأكثر أهمية، حتى تتمكن من الاستجابة لها بسرعة. اتصل بفريق حسابك أو ممثل Microsoft للاشتراك **في خبراء المخاطر في Microsoft - خبراء عند الطلب** للرجوع إلى خبراء التهديدات لدينا حول عمليات الكشف والخصوم ذات الصلة.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>تقدم بطلب للحصول على خبراء المخاطر في Microsoft - خدمة إعلامات الهجوم المستهدف

إذا كنت بالفعل عميل Defender لنقطة النهاية، يمكنك التطبيق من خلال مدخل Microsoft 365 Defender.

1. من جزء التنقل، انتقل إلى **الإعدادات > الميزات المتقدمة > العامة > خبراء المخاطر في Microsoft - إعلامات الهجوم المستهدف**.

2. انقر فوق **تطبيق**.

   :::image type="content" source="images/mte-collaboratewithmte.png" alt-text="إعدادات خبراء المخاطر في Microsoft" lightbox="images/mte-collaboratewithmte.png":::

3. أدخل اسمك وعنوان بريدك الإلكتروني حتى تتمكن Microsoft من العودة إليك على تطبيقك.

   :::image type="content" source="images/mte-apply.png" alt-text="الحقل &quot;الاسم&quot; في صفحة تطبيق خبراء المخاطر في Microsoft" lightbox="images/mte-apply.png":::

4. اقرأ [بيان الخصوصية](https://privacy.microsoft.com/privacystatement)، ثم انقر فوق **"إرسال** " عند الانتهاء. ستتلقى بريدا إلكترونيا ترحيبيا بمجرد الموافقة على طلبك.

   :::image type="content" source="images/mte-applicationconfirmation.png" alt-text="رسالة تأكيد تطبيق خبراء المخاطر في Microsoft" lightbox="images/mte-applicationconfirmation.png":::

عند الموافقة، ستتلقى رسالة بريد إلكتروني ترحيبية وسترى تغيير الزر **"تطبيق** " على زر التبديل "قيد التشغيل". في حالة رغبتك في إخراج نفسك من خدمة "إعلامات الهجوم المستهدف"، مرر زر التبديل "إيقاف التشغيل" وانقر فوق **"حفظ التفضيلات** " في أسفل الصفحة.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>حيث سترى إعلامات الهجوم المستهدف من خبراء المخاطر في Microsoft

يمكنك تلقي إعلام بالهجوم المستهدف من خبراء المخاطر في Microsoft من خلال الوسيطة التالية:

- صفحة **أحداث** مدخل Defender لنقطة النهاية
- لوحة معلومات **تنبيهات** Defender لنقطة النهاية
- [واجهة برمجة تطبيقات](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) تنبيه OData [وواجهة برمجة تطبيقات REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- جدول [DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) في التتبع المتقدم
- بريدك الإلكتروني، إذا اخترت تكوينه

لتلقي إعلامات الهجوم المستهدف عبر البريد الإلكتروني، قم بإنشاء قاعدة إعلام بالبريد الإلكتروني.

### <a name="create-an-email-notification-rule"></a>إنشاء قاعدة إعلام بالبريد الإلكتروني

يمكنك إنشاء قواعد لإرسال إعلامات البريد الإلكتروني لمستلمي الإعلامات. راجع  [تكوين إعلامات التنبيه](configure-email-notifications.md) لإنشاء إعلام بالبريد الإلكتروني أو تحريره أو حذفه أو استكشاف الأخطاء فيه وإصلاحها للحصول على التفاصيل.

## <a name="view-the-targeted-attack-notification"></a>عرض إعلام الهجوم المستهدف

ستبدأ في تلقي إعلام بالهجوم المستهدف من خبراء المخاطر في Microsoft في بريدك الإلكتروني بعد تكوين النظام لتلقي إعلام بالبريد الإلكتروني.

1. انقر فوق الارتباط في البريد الإلكتروني للانتقال إلى سياق التنبيه المقابل في لوحة المعلومات التي تم وضع علامة عليها مع **خبراء التهديد**.

2. من لوحة المعلومات، حدد نفس موضوع التنبيه الذي حصلت عليه من البريد الإلكتروني، لعرض التفاصيل.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>الاشتراك في خبراء المخاطر في Microsoft - الخبراء عند الطلب

يتوفر هذا كخدمة اشتراك. إذا كنت بالفعل عميل Defender لنقطة النهاية، يمكنك الاتصال بممثل Microsoft للاشتراك في خبراء المخاطر في Microsoft - Experts on Demand.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>استشارة خبير مخاطر Microsoft حول أنشطة الأمان عبر الإنترنت المشبوهة في مؤسستك

يمكنك الشراكة مع خبراء المخاطر في Microsoft الذين يمكن إشراكهم مباشرة من داخل مدخل Microsoft 365 Defender لاستجابتهم. يوفر الخبراء رؤى لفهم أفضل للتهديدات المعقدة، أو إعلامات الهجوم المستهدفة التي تحصل عليها، أو إذا كنت بحاجة إلى مزيد من المعلومات حول التنبيهات، أو جهاز يحتمل أن يكون معرضا للخطر، أو سياق التحليل الذكي للمخاطر الذي تراه على لوحة معلومات المدخل.

> [!NOTE]
>
> - لا يتم حاليا دعم استفسارات التنبيه المتعلقة ببيانات التحليل الذكي للمخاطر المخصصة لمؤسستك. راجع عمليات الأمان أو فريق الاستجابة للحوادث للحصول على التفاصيل.
> - تحتاج إلى الحصول على إذن **إدارة إعدادات الأمان** في مدخل Microsoft 365 Defender لتتمكن من إرسال استعلام "استشارة خبير التهديد".

1. انتقل إلى صفحة المدخل مع المعلومات ذات الصلة التي تريد التحقيق فيها، على سبيل المثال، صفحة **الحدث** . تأكد من عرض صفحة التنبيه أو الجهاز ذي الصلة قبل إرسال طلب تحقيق.

2. من القائمة العلوية اليسرى، انقر فوق **؟** رمز. ثم حدد **"استشارة خبير مخاطر**".

    :::image type="content" source="images/mte-eod-menu.png" alt-text="عنصر القائمة &quot;خبراء خبراء المخاطر في Microsoft عند الطلب&quot;" lightbox="images/mte-eod-menu.png":::

    يتم فتح شاشة منبثقة. تظهر الشاشة التالية عندما تكون في اشتراك تجريبي.

    :::image type="content" source="images/mte-eod.png" alt-text="صفحة خبراء خبراء المخاطر في Microsoft عند الطلب" lightbox="images/mte-eod.png":::

    تظهر الشاشة التالية عندما تكون في خبراء المخاطر في Microsoft كامل - اشتراك الخبراء عند الطلب.

    :::image type="content" source="images/mte-eod-fullsubscription.png" alt-text="صفحة الاشتراك الكامل خبراء المخاطر في Microsoft Experts on Demand" lightbox="images/mte-eod-fullsubscription.png":::

    يتم ملء حقل **موضوع الاستعلام** مسبقا بالارتباط إلى الصفحة ذات الصلة لطلب التحقيق الخاص بك. على سبيل المثال، ارتباط إلى صفحة تفاصيل الحادث أو التنبيه أو الجهاز التي كنت عليها عند تقديم الطلب.

3. في الحقل التالي، قم بتوفير معلومات كافية لإعطاء سياق خبراء المخاطر في Microsoft بما يكفي لبدء التحقيق.

4. أدخل عنوان البريد الإلكتروني الذي تريد استخدامه للتوافق مع خبراء المخاطر في Microsoft.

> [!NOTE]
> إذا كنت ترغب في تعقب حالة حالات الخبراء عند الطلب من خلال Microsoft Services Hub، فتواصل مع Customer Success Account Manager.

شاهد هذا الفيديو للحصول على نظرة عامة سريعة على مركز خدمات Microsoft.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-threat-experts---experts-on-demand"></a>عينة من مواضيع التحقيق التي يمكنك استشارتها مع خبراء المخاطر في Microsoft - الخبراء عند الطلب

### <a name="alert-information"></a>معلومات التنبيه

- نرى نوعا جديدا من التنبيه لثنائي حي خارج الأرض: [AlertID]. هل يمكنك إخبارنا بشيء أكثر حول هذا التنبيه وكيف يمكننا إجراء المزيد من التحقيق؟
- لقد لاحظنا هجومين متشابهين، يحاولان تنفيذ برامج PowerShell النصية الضارة ولكن إنشاء تنبيهات مختلفة. أحدهما هو "سطر أوامر PowerShell مريب" والآخر هو "تم الكشف عن ملف ضار بناء على الإشارة التي يوفرها O365". ما الفرق؟
- أتلقى تنبيها فرديا اليوم لعدد غير طبيعي من عمليات تسجيل الدخول الفاشلة من جهاز مستخدم رفيع المستوى. لا يمكنني العثور على أي دليل إضافي حول محاولات تسجيل الدخول هذه. كيف يمكن ل Defender لنقطة النهاية رؤية هذه المحاولات؟ ما نوع عمليات تسجيل الدخول التي تتم مراقبتها؟
- هل يمكنك إعطاء المزيد من السياق أو الرؤى حول هذا التنبيه: "تمت ملاحظة السلوك المشبوه من قبل أداة مساعدة النظام".

### <a name="possible-machine-compromise"></a>إمكانية اختراق الجهاز

- هل يمكنك المساعدة في الإجابة عن سبب ظهور "عملية غير معروفة تمت ملاحظتها؟" تظهر هذه الرسالة أو التنبيه بشكل متكرر على العديد من الأجهزة. نحن نقدر أي إدخال لتوضيح ما إذا كانت هذه الرسالة أو التنبيه مرتبطا بنشاط ضار.
- هل يمكنك المساعدة في التحقق من صحة حل وسط محتمل على النظام التالي في [date] بسلوكيات مماثلة للكشف السابق [اسم البرامج الضارة] عن البرامج الضارة على نفس النظام في [الشهر]؟

### <a name="threat-intelligence-details"></a>تفاصيل التحليل الذكي للمخاطر

- اكتشفنا رسالة بريد إلكتروني للتصيد الاحتيالي قامت بتسليم مستند Word ضار إلى مستخدم. تسبب مستند Word الضار في سلسلة من الأحداث المشبوهة، والتي أدت إلى تشغيل العديد من تنبيهات Defender لنقطة النهاية للبرامج الضارة [اسم البرامج الضارة]. هل لديك أي معلومات حول هذه البرامج الضارة؟ إذا كان الجواب نعم، هل يمكنك إرسال ارتباط إلي؟
- رأيت مؤخرا منشور [مرجع وسائل التواصل الاجتماعي، على سبيل المثال، Twitter أو المدونة] حول تهديد يستهدف صناعتي. هل يمكنك أن تساعدني على فهم الحماية التي يوفرها Defender لنقطة النهاية ضد ممثل التهديد هذا؟

### <a name="microsoft-threat-experts-alert-communications"></a>اتصالات التنبيه خبراء المخاطر في Microsoft

- هل يمكن لفريق الاستجابة للحوادث مساعدتنا في معالجة إعلام الهجوم المستهدف الذي تلقيناه؟
- تلقيت إعلام الهجوم المستهدف هذا من خبراء المخاطر في Microsoft. ليس لدينا فريق الاستجابة للحوادث الخاص بنا. ماذا يمكننا أن نفعل الآن، وكيف يمكننا احتواء الحادث؟
- تلقيت إعلاما بالهجوم المستهدف من خبراء المخاطر في Microsoft. ما هي البيانات التي يمكنك توفيرها لنا والتي يمكننا تمريرها إلى فريق الاستجابة للحوادث لدينا؟

  > [!NOTE]
  > خبراء المخاطر في Microsoft هي خدمة تتبع الأمان عبر الإنترنت مدارة وليست خدمة استجابة للحوادث. ومع ذلك، يمكنك التفاعل مع فريق الاستجابة للحوادث الخاص بك لمعالجة المشكلات التي تتطلب استجابة للحوادث. إذا لم يكن لديك فريق الاستجابة للحوادث الخاص بك وترغب في الحصول على مساعدة Microsoft، يمكنك التفاعل مع فريق الاستجابة لحوادث الأمان السيبراني CSS (CIRT). يمكنهم فتح تذكرة للمساعدة في معالجة استعلامك.

## <a name="scenario"></a>السيناريو

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>تلقي تقرير تقدم حول استعلام التتبع المدار

تختلف الاستجابة من خبراء المخاطر في Microsoft وفقا للاستعلام. سيراسلك تقرير التقدم عبر البريد الإلكتروني حول **استعلام خبير التهديد** في غضون يومين، لإبلاغ حالة التحقيق من الفئات التالية:

- هناك حاجة إلى مزيد من المعلومات لمتابعة التحقيق
- هناك حاجة إلى ملف أو عدة نماذج ملفات لتحديد السياق التقني
- يتطلب التحقيق المزيد من الوقت
- كانت المعلومات الأولية كافية لاختتام التحقيق

من الضروري الاستجابة بسرعة للحفاظ على تحرك التحقيق.

## <a name="related-topic"></a>الموضوع ذو الصلة

- [خبراء المخاطر في Microsoft عامة](microsoft-threat-experts.md)
- [نظرة عامة على خبراء المخاطر في Microsoft في Microsoft 365](/microsoft-365/security/mtp/microsoft-threat-experts)
