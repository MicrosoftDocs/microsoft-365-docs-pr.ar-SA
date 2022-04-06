---
title: تكوين قدرات خبراء المخاطر في Microsoft وإدارتها
ms.reviewer: ''
description: سجل في Microsoft Threats Experts لتكوينه وإدارته واستخدامه في عمليات الأمان اليومية وعمل إدارة الأمان.
keywords: خبراء المخاطر في Microsoft، خدمة البحث عن المخاطر المدارة، MTE، خدمة الصيد المدارة من Microsoft
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
ms.openlocfilehash: 152c0c54138841d9159c7230fc043307979e4546
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471792"
---
# <a name="configure-and-manage-microsoft-threat-experts-capabilities"></a>تكوين قدرات خبراء المخاطر في Microsoft وإدارتها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="before-you-begin"></a>قبل البدء

> [!NOTE]
> مناقشة متطلبات الأهلية مع موفر خدمة Microsoft التقنية وفريق الحساب قبل أن تطبق على خبراء المخاطر في Microsoft - خدمة البحث عن التهديدات المدارة في إعلامات الهجمات المستهدفة.

تأكد من نشر Defender for Endpoint في بيئتك مع الأجهزة التي تم تسجيلها، وليس فقط على إعداد المعمل.

إذا كنت عميل Defender for Endpoint، يجب أن تطبق على **خبراء المخاطر في Microsoft -** إعلامات الهجمات المستهدفة للحصول على تحليلات وتحليلات خاصة للمساعدة في تحديد التهديدات الأكثر أهمية، حتى تتمكن من الاستجابة لها بسرعة. اتصل بفريق حسابك أو بممثل Microsoft للاشتراك في خبراء المخاطر في Microsoft **-** الخبراء عند الطلب للتشاور مع خبرائنا في التهديدات بشأن الكشفات ذات الصلة والمشتركين.

## <a name="apply-for-microsoft-threat-experts---targeted-attack-notifications-service"></a>تطبيق على خبراء المخاطر في Microsoft - خدمة إعلامات الهجمات المستهدفة

إذا كنت عميل Defender for Endpoint بالفعل، يمكنك التطبيق من خلال Microsoft 365 Defender المدخل.

1. من جزء التنقل، انتقل إلى الإعدادات > **عام > الميزات المتقدمة > خبراء المخاطر في Microsoft - إعلامات الهجمات المستهدفة**.

2. انقر فوق **تطبيق**.

   :::image type="content" source="images/mte-collaboratewithmte.png" alt-text="إعدادات خبراء المخاطر في Microsoft" lightbox="images/mte-collaboratewithmte.png":::

3. أدخل اسمك وعنوان بريدك الإلكتروني حتى تتمكن Microsoft من الرجوع إليك على التطبيق.

   :::image type="content" source="images/mte-apply.png" alt-text="الحقل &quot;الاسم&quot; على صفحة خبراء المخاطر في Microsoft التطبيق" lightbox="images/mte-apply.png":::

4. اقرأ [بيان الخصوصية،](https://privacy.microsoft.com/privacystatement) ثم انقر فوق **إرسال** عندما تنتهي. ستتلقى رسالة بريد إلكتروني ترحيبية بمجرد الموافقة على طلبك.

   :::image type="content" source="images/mte-applicationconfirmation.png" alt-text="رسالة خبراء المخاطر في Microsoft تأكيد التطبيق" lightbox="images/mte-applicationconfirmation.png":::

عند القبول، ستتلقى رسالة بريد إلكتروني ترحيبية وسترى الزر تطبيق  يتغير إلى زر تبديل "تشغيل". في حال أردت أن تخرق نفسك من خدمة إعلامات الهجمات المستهدفة، مرر زر "إيقاف التشغيل" وانقر فوق  حفظ التفضيلات في أسفل الصفحة.

## <a name="where-youll-see-the-targeted-attack-notifications-from-microsoft-threat-experts"></a>المكان الذي سترى فيه إعلامات الهجمات المستهدفة من خبراء المخاطر في Microsoft

يمكنك تلقي إعلام بالهجوم المستهدف من خبراء المخاطر في Microsoft الوسط التالي:

- صفحة "أحداث" في مدخل "Defender for **Endpoint** "
- لوحة معلومات تنبيهات مدخل Defender for **Endpoint**
- API لتنبيه [](/windows/security/threat-protection/microsoft-defender-atp/get-alerts) OData وPI [(API) REST](/windows/security/threat-protection/microsoft-defender-atp/pull-alerts-using-rest-api)
- [DeviceAlertEvents](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-devicealertevents-table) table في عملية الصيد المتقدمة
- بريدك الإلكتروني، إذا اخترت تكوينه

لتلقي إعلامات الهجمات المستهدفة عبر البريد الإلكتروني، أنشئ قاعدة إعلام بالبريد الإلكتروني.

### <a name="create-an-email-notification-rule"></a>إنشاء قاعدة إعلام بالبريد الإلكتروني

يمكنك إنشاء قواعد لإرسال إعلامات البريد الإلكتروني لمستلمي الإعلامات. راجع  [تكوين إعلامات التنبيهات](configure-email-notifications.md) لإنشاء إعلام البريد الإلكتروني أو تحريره أو حذفه أو استكشاف الأخطاء فيه وإصلاحها، للحصول على التفاصيل.

## <a name="view-the-targeted-attack-notification"></a>عرض إعلام الهجوم المستهدف

ستبدأ في تلقي إعلام بالهجمة المستهدفة من خبراء المخاطر في Microsoft البريد الإلكتروني بعد تكوين النظام لتلقي إعلام بالبريد الإلكتروني.

1. انقر فوق الارتباط في البريد الإلكتروني للذهاب إلى سياق التنبيه المقابل في لوحة المعلومات التي تم وضع علامة عليها مع **خبراء التهديدات**.

2. من لوحة المعلومات، حدد موضوع التنبيه نفسه الذي تلقيته من البريد الإلكتروني، لعرض التفاصيل.

## <a name="subscribe-to-microsoft-threat-experts---experts-on-demand"></a>الاشتراك في خبراء المخاطر في Microsoft - الخبراء عند الطلب

يتوفر ذلك كخدمة اشتراك. إذا كنت عميل Defender for Endpoint بالفعل، يمكنك الاتصال بممثل Microsoft للاشتراك في خبراء المخاطر في Microsoft - الخبراء عند الطلب.

## <a name="consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization"></a>استشر أحد خبراء المخاطر في Microsoft حول أنشطة الأمن الإلكتروني المريبة في مؤسستك

يمكنك المشاركة مع خبراء المخاطر في Microsoft الأشخاص الذين يمكنهم المشاركة مباشرة من Microsoft 365 Defender المدخل للحصول على استجابة دقيقة وفي الوقت المناسب. يوفر الخبراء تحليلات لفهم التهديدات المعقدة بشكل أفضل، أو إعلامات الهجمات المستهدفة التي تحصل عليها، أو إذا كنت بحاجة إلى مزيد من المعلومات حول التنبيهات، أو جهاز يحتمل أن يكون قد تعرض للخطر، أو سياق المعلومات المتعلقة بخطر ما الذي تراه على لوحة معلومات المدخل.

> [!NOTE]
>
> - تنبيهات الاستعلامات المتعلقة بالبيانات المخصصة لذكاء المخاطر في مؤسستك غير معتمدة حاليا. راجع عمليات الأمان أو فريق الاستجابة للحوادث للحصول على التفاصيل.
> - يجب أن يكون لديك إذن  إدارة إعدادات الأمان في مدخل Microsoft 365 Defender لكي تتمكن من إرسال استفسار "استشارة خبير في التهديدات".

1. انتقل إلى صفحة المدخل مع المعلومات ذات الصلة التي تريد التحقق فيها، على سبيل المثال، **صفحة الحادث.** تأكد من عرض صفحة التنبيه أو الجهاز ذي الصلة قبل إرسال طلب التحقيق.

2. من القائمة العلوية اليسرى، انقر فوق **؟** أيقونة. بعد ذلك، حدد **استشارة خبير في التهديدات**.

    :::image type="content" source="images/mte-eod-menu.png" alt-text="عنصر خبراء المخاطر في Microsoft القائمة &quot;خبراء عند الطلب&quot;" lightbox="images/mte-eod-menu.png":::

    يتم فتح شاشة منتحلة. تظهر الشاشة التالية عندما تكون في اشتراك تجريبي.

    :::image type="content" source="images/mte-eod.png" alt-text="صفحة خبراء المخاطر في Microsoft عند الطلب" lightbox="images/mte-eod.png":::

    تظهر الشاشة التالية عندما تكون في وضع ملء خبراء المخاطر في Microsoft - اشتراك الخبراء عند الطلب.

    :::image type="content" source="images/mte-eod-fullsubscription.png" alt-text="صفحة خبراء المخاطر في Microsoft الاشتراك الكامل ل &quot;خبراء عند الطلب&quot;" lightbox="images/mte-eod-fullsubscription.png":::

    يتم **ملء حقل موضوع** الاستعلام مسبقا بالارتباط إلى الصفحة ذات الصلة لطلب التحقيق. على سبيل المثال، ارتباط إلى صفحة تفاصيل الحادث أو التنبيه أو الجهاز التي كنت فيها عند تقديم الطلب.

3. في الحقل التالي، يمكنك توفير معلومات كافية خبراء المخاطر في Microsoft سياق كاف لبدء التحقيق.

4. أدخل عنوان البريد الإلكتروني الذي تريد استخدامه للتوافق مع خبراء المخاطر في Microsoft.

> [!NOTE]
> إذا كنت ترغب في تعقب حالة حالات الخبراء عند الطلب من خلال مركز خدمات Microsoft، فصل إلى إدارة حساب نجاح العملاء.

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول مركز خدمات Microsoft.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4pk9f]

## <a name="sample-investigation-topics-that-you-can-consult-with-microsoft-threat-experts---experts-on-demand"></a>نماذج لمواضيع التحقيق التي يمكنك استشارة خبراء المخاطر في Microsoft - الخبراء عند الطلب

### <a name="alert-information"></a>معلومات التنبيه

- نحن نشاهد نوع تنبيه جديدا ل ثنائي يعيش خارج الأرض: [AlertID]. هل يمكنك إخبارنا بمزيد من المعلومات حول هذا التنبيه وكيف يمكننا إجراء المزيد من الاستقصاءات؟
- لقد لاحظنا هجومين مماثلين، يحاولان تنفيذ برامج PowerShell النصية الضارة ولكن مع إنشاء تنبيهات مختلفة. أحدهما "سطر أوامر PowerShell مريب" والآخر هو "تم الكشف عن ملف ضار بالاستناد إلى إشارة مقدمة من O365". ما الفرق؟
- أتلقى تنبيها فرديا اليوم لعدد غير طبيعي من عمليات تسجيل الدخول الفاشلة من جهاز مستخدم ملف تعريف عال. لا يمكنني العثور على أي دليل آخر حول محاولات تسجيل الدخول هذه. كيف يمكن ل Defender for Endpoint الاطلاع على هذه المحاولات؟ ما هو نوع تسجيل الدخول الذي يتم مراقبته؟
- هل يمكنك تقديم المزيد من السياق أو الرؤى حول هذا التنبيه: "تم ملاحظة سلوك مريب بواسطة أداة مساعدة النظام".

### <a name="possible-machine-compromise"></a>اختراق محتمل للجهاز

- هل يمكنك المساعدة في الإجابة عن سبب ملاحظة "عملية غير معروفة؟" تظهر هذه الرسالة أو التنبيه بشكل متكرر على العديد من الأجهزة. نحن نقدر أي إدخال لتوضيح ما إذا كانت هذه الرسالة أو التنبيه مرتبطا بنشاط ضار.
- هل يمكنك المساعدة في التحقق من وجود اختراق محتمل على النظام التالي في [التاريخ] مع سلوكيات مماثلة للكشف السابق عن البرامج الضارة [اسم البرامج الضارة] على النظام نفسه في [الشهر]؟

### <a name="threat-intelligence-details"></a>تفاصيل المعلومات الاستخبارية للتهديدات

- اكتشفنا رسالة بريد إلكتروني تصيد احتيالي تم من خلالها تسليم مستند Word ضار إلى مستخدم. تسبب مستند Word الضار في سلسلة من الأحداث المريبة، مما أدى إلى تشغيل تنبيهات متعددة ل Defender for Endpoint للبرامج الضارة [اسم البرامج الضارة]. هل لديك أي معلومات حول هذه البرامج الضارة؟ إذا كانت الإجابة نعم، هل يمكنك إرسال ارتباط إلي؟
- لقد شاهدت مؤخرا منشور [مرجع الوسائط الاجتماعية، على سبيل المثال، Twitter أو المدونة] حول خطر يستهدف مجالي. هل يمكنك مساعدتي في فهم الحماية التي يوفرها Defender for Endpoint ضد هذا الممثل الذي يشكل تهديدات؟

### <a name="microsoft-threat-experts-alert-communications"></a>خبراء المخاطر في Microsoft تنبيهات البريد الإلكتروني

- هل يمكن لفريق الاستجابة للحوادث مساعدتنا على معالجة إعلام الهجوم المستهدف الذي تلقيناه؟
- تلقيت إعلام الهجوم المستهدف هذا من خبراء المخاطر في Microsoft. ليس لدينا فريق الاستجابة للحوادث. ماذا يمكننا أن نفعل الآن، وكيف يمكننا احتواء الحادث؟
- تلقيت إعلام هجوم مستهدف من خبراء المخاطر في Microsoft. ما هي البيانات التي يمكنك توفيرها لنا التي يمكننا نقلها إلى فريق الاستجابة للحوادث؟

  > [!NOTE]
  > خبراء المخاطر في Microsoft خدمة تعقب الأمان الإلكتروني المدارة وليس خدمة استجابة للحوادث. ومع ذلك، يمكنك التفاعل مع فريق الاستجابة للحوادث لمعالجة المشاكل التي تتطلب استجابة للحوادث. إذا لم يكن لديك فريق الاستجابة للحوادث الخاص بك وتحب مساعدة Microsoft، يمكنك التفاعل مع فريق الاستجابة لحوادث الأمن الإلكتروني (CSS) (CIRT). يمكنهم فتح تذكرة للمساعدة في معالجة استفسارك.

## <a name="scenario"></a>السيناريو

### <a name="receive-a-progress-report-about-your-managed-hunting-inquiry"></a>تلقي تقرير تقدم حول استفسار الصيد المدار

تختلف استجابة خبراء المخاطر في Microsoft وفقا لاستعلامك. سيرسلون إليك تقريرا حول التقدم عبر البريد الإلكتروني حول **استشارتك لاستعلام** خبير في التهديدات في غضون يومين، لتوصيل حالة التحقيق من الفئات التالية:

- هناك حاجة إلى مزيد من المعلومات لمواصلة التحقيق
- هناك حاجة إلى ملف أو عدة نماذج ملفات لتحديد السياق التقني
- يتطلب التحقيق مزيدا من الوقت
- كانت المعلومات الأولية كافية لنهي التحقيق

من المهم الاستجابة بسرعة لإبقاء التحقيق متحركا.

## <a name="related-topic"></a>موضوع ذو صلة

- [خبراء المخاطر في Microsoft عامة](microsoft-threat-experts.md)
- [خبراء المخاطر في Microsoft في Microsoft 365 عامة](/microsoft-365/security/mtp/microsoft-threat-experts)
