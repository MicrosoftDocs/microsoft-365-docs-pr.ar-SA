---
title: تكوين Microsoft Defender لنقطة النهاية على ميزات iOS
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على ميزات iOS.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، ios، تكوين، ميزات، ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c52fac7c5680d8e5f814098410dc2e1993328d2f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476896"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>تكوين Microsoft Defender لنقطة النهاية على ميزات iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> سيستخدم Defender for Endpoint على نظام iOS VPN لتوفير ميزة حماية ويب. هذه ليست VPN عادية وهي VPN محلية/ذاتية التكرار لا تأخذ حركة المرور خارج الجهاز.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>الوصول الشرطي باستخدام Defender for Endpoint على iOS

Microsoft Defender لنقطة النهاية على نظام iOS مع Microsoft Intune يعمل Azure Active Directory على تمكين فرض توافق الأجهزة ونهج الوصول الشرطي استنادا إلى درجة مخاطر الجهاز. Defender for Endpoint هو حل الدفاع عن المخاطر عبر الأجهزة المحمولة (MTD) الذي يمكنك نشره للاستفادة من هذه الإمكانية عبر Intune.

لمزيد من المعلومات حول كيفية إعداد الوصول الشرطي باستخدام Defender لنقطة النهاية على iOS، راجع [Defender for Endpoint و Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>الكشف عن التسلل من قبل Microsoft Defender لنقطة النهاية

Microsoft Defender لنقطة النهاية على إمكانية الكشف عن الأجهزة غير المدارة والمدارة التي تم إلغاء إلغاء جنونها. إذا تم الكشف عن وجود جهاز تم إلغاء غلقه، سيتم إرسال تنبيه عالي المخاطر إلى مدخل Microsoft 365 Defender وإذا تم إعداد "الوصول الشرطي" استنادا إلى درجة مخاطر الجهاز، سيتم حظر الجهاز من الوصول إلى بيانات الشركة.

## <a name="web-protection-and-vpn"></a>Web Protection و VPN

بشكل افتراضي، يتضمن Defender for Endpoint على نظام iOS ميزة حماية الويب ويمكنها. [تساعد حماية](web-protection-overview.md) الويب على حماية الأجهزة من تهديدات الويب وحماية المستخدمين من هجمات التصيد الاحتيالي. تجدر الإشارة إلى أن مؤشرات مكافحة التصيد الاحتيالي والمؤشرات المخصصة (عنوان URL وعناوين IP) معتمدة كجزء من حماية ويب. تصفية محتوى ويب غير معتمدة حاليا على نظام iOS.

يستخدم Defender ل Endpoint على iOS VPN من أجل توفير هذه الإمكانية. تجدر الإشارة إلى أن هذه VPN محلية وبخلاف VPN التقليدية، لا يتم إرسال حركة مرور الشبكة خارج الجهاز.

على الرغم من تمكينه بشكل افتراضي، قد تكون هناك بعض الحالات التي تتطلب منك تعطيل VPN. على سبيل المثال، تريد تشغيل بعض التطبيقات التي لا تعمل عند تكوين VPN. في مثل هذه الحالات، يمكنك اختيار تعطيل VPN من التطبيق على الجهاز باتباع الخطوات أدناه:

1. على جهاز iOS، **افتح تطبيق الإعدادات**، وانقر فوق **عام** ثم على VPN أو اضغط **عليه**.
1. انقر فوق الزر "i" أو اضغط عليه Microsoft Defender لنقطة النهاية.
1. قم بتبدل الاتصال **عند الطلب** لتعطيل VPN.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="الزر &quot;تبديل&quot; الخاص بخيار &quot;الاتصال VPN عند الطلب&quot;" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> لن تكون حماية الويب متوفرة عند تعطيل VPN. لإعادة تمكين حماية الويب، افتح Microsoft Defender لنقطة النهاية على الجهاز وانقر فوق **بدء VPN** أو اضغط عليه.

## <a name="co-existence-of-multiple-vpn-profiles"></a>الوجود المشترك لملفات تعريف VPN متعددة

لا يدعم Apple iOS العديد من الشبكات VPN على مستوى الجهاز لكي تكون نشطة في الوقت نفسه. على الرغم من أن ملفات تعريف VPN المتعددة يمكن أن تكون موجودة على الجهاز، إلا أن VPN واحد فقط يمكن أن يكون نشطا في كل مرة.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>تكوين Microsoft Defender لنقطة النهاية المخاطر في نهج حماية التطبيق (MAM)

Microsoft Defender لنقطة النهاية تكوين رسائل لإرسال إشارات التهديد التي سيتم استخدامها في "سياسات حماية التطبيقات" (APP، المعروفة أيضا باسم MAM) على iOS/iPadOS. باستخدام هذه الإمكانية، يمكنك استخدام Microsoft Defender لنقطة النهاية لحماية الوصول إلى بيانات الشركة من الأجهزة غير المشتركة أيضا.

الخطوات اللازمة لإعداد سياسات حماية التطبيقات باستخدام Microsoft Defender لنقطة النهاية هي كما يلي:

1. قم بإعداد الاتصال من إدارة نقاط النهاية من Microsoft المستأجر Microsoft Defender لنقطة النهاية. في [مركز إدارة إدارة نقطة نهاية Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) \>  \>، انتقل إلى موصلات **إدارة المستأجر** والرموز المميزة Microsoft Defender لنقطة النهاية (ضمن النظام الأساسي المتقاطع) \> أو وحدة أمان نقطة **النهاية Microsoft Defender لنقطة النهاية** (ضمن إعداد) ثم قم تشغيل رموز تبديل ضمن **نهج حماية الإعدادات ل iOS**.
1. حدد حفظ. من المفترض أن **ترى حالة الاتصال** تم تعيينها الآن إلى **تم التمكين**.
1. إنشاء نهج حماية التطبيق:  \> بعد اكتمال Microsoft Defender لنقطة النهاية الموصل، انتقل إلى تطبيقات **حماية التطبيقات** نهج التطبيق (ضمن نهج) لإنشاء نهج جديد أو تحديث نهج موجود.
1. حدد النظام الأساسي **والتطبيقات وحماية البيانات وإعدادات متطلبات Access** التي تتطلبها مؤسستك لنصك.
1. ضمن **شروط جهاز الإطلاق** \> **الشرطي**، ستجد الإعداد **الحد الأقصى المسموح به لمستوى تهديدات الجهاز**. يجب تكوين هذا إلى منخفض أو متوسط أو عال أو آمن. الإجراءات المتوفرة لك هي **حظر الوصول أو** **مسح البيانات**. قد ترى مربع حوار معلوماتي للتأكد من إعداد الموصل قبل أن يتم تطبيق هذا الإعداد. إذا تم إعداد الموصل بالفعل، فقد تتجاهل مربع الحوار هذا.
1. يمكنك إنهاء الواجبات وحفظ النهج.

لمزيد من التفاصيل حول MAM أو نهج حماية التطبيق، راجع إعدادات نهج [حماية تطبيق iOS](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>نشر Microsoft Defender لنقطة النهاية MAM أو على الأجهزة غير التي تم نشرها

Microsoft Defender لنقطة النهاية على نظام iOS سيناريو نهج حماية التطبيقات وهو متوفر في متجر تطبيقات Apple.

يجب على المستخدمين تثبيت أحدث إصدار من التطبيق مباشرة من متجر تطبيقات Apple.

## <a name="privacy-controls"></a>عناصر تحكم الخصوصية

> [!IMPORTANT]
> عناصر تحكم الخصوصية Microsoft Defender لنقطة النهاية على نظام iOS في المعاينة. تتعلق المعلومات التالية بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

### <a name="configure-privacy-in-phish-alert-report"></a>تكوين الخصوصية في تقرير تنبيه التصيد الاحتيالي

يمكن للعملاء الآن تمكين التحكم بالخصوصية في تقرير التصيد الاحتيالي المرسل بواسطة Microsoft Defender لنقطة النهاية على نظام iOS. سيضمن ذلك عدم إرسال اسم المجال كجزء من تنبيه التصيد الاحتيالي عند اكتشاف موقع ويب تصيد احتيالي وحظره من قبل Microsoft Defender لنقطة النهاية.

استخدم الخطوات التالية لتمكين الخصوصية وليس تجميع اسم المجال كجزء من تقرير تنبيه التصيد الاحتيالي.

1. في [إدارة نقاط النهاية من Microsoft مركز الإدارة واذهب](https://go.microsoft.com/fwlink/?linkid=2109431) إلى سياسات تكوين **تطبيقات** **AppsAddManaged** >  >  >  **الأجهزة**.
1. قم امنح النهج اسما، النظام الأساسي > **iOS/iPadOS**، وحدد نوع ملف التعريف.
1. حدد **Microsoft Defender لنقطة النهاية** ك التطبيق الهدف.
1. في الإعدادات، حدد **استخدام** مصمم التكوين وأضف **DefenderExcludeURLInReport** كمفتاح ونوع القيمة **كقيمة منطقية**
   - لتمكين الخصوصية وليس تجميع اسم المجال، أدخل القيمة ك `true` وتعيين هذا النهج للمستخدمين. بشكل افتراضي، يتم تعيين هذه القيمة إلى `false`.
   - بالنسبة للمستخدمين الذين تم `true`تعيين المفتاح لديهم ك ، لن يحتوي تنبيه التصيد الاحتيالي على معلومات اسم المجال عند الكشف عن موقع ضار وحظره بواسطة Defender for Endpoint.
1. انقر **فوق التالي** ثم قم بتعيين ملف التعريف هذا إلى الأجهزة/المستخدمين المستهدفين.

لن يؤثر تشغيل عناصر التحكم في الخصوصية أعلاه أو إيقاف تشغيلها على التحقق من توافق الجهاز أو الوصول الشرطي.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>تكوين نهج التوافق ضد الأجهزة التي تم إلغاء تأمينها

لحماية بيانات الشركة من الوصول إليها على أجهزة iOS التي تم إلغاء تأمينها، نوصي بإعداد نهج التوافق التالي على Intune.

> [!NOTE]
> الكشف عن التسلل من قبل أحد Microsoft Defender لنقطة النهاية على نظام iOS. ومع ذلك، نوصي بإعداد هذا النهج كطبقة إضافية من الدفاع ضد سيناريوهات فُر من السجان.

اتبع الخطوات أدناه لإنشاء نهج توافق ضد الأجهزة التي تم إلغاء تأمينها.

1. في [إدارة نقاط النهاية من Microsoft إدارة الأجهزة،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **نهج DevicesCompliance** ->  **إنشاء** ->  **نهج**. حدد "iOS/iPadOS" كنقر فوق **إنشاء**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-policy.png" alt-text="علامة التبويب &quot;إنشاء نهج&quot;" lightbox="images/ios-jb-policy.png":::

2. حدد اسما النهج، على سبيل المثال "نهج التوافق للانهاء من السجان".
3. في صفحة إعدادات التوافق، انقر لتوسيع **المقطع حالة** الجهاز وانقر فوق **الحقل حظر** الأجهزة التي تم **إلغاء تأمينها** .

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-settings.png" alt-text="علامة التبويب &quot;إعدادات التوافق&quot;" lightbox="images/ios-jb-settings.png":::

4. في المقطع **إجراءات لعدم التوافق** ، حدد الإجراءات وفقا لمتطلباتك وحدد **التالي**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-actions.png" alt-text="علامة التبويب &quot;إجراءات لعدم التوافق&quot;" lightbox="images/ios-jb-actions.png":::

5. في المقطع **الواجبات** ، حدد مجموعات المستخدمين التي تريد تضمينها لهذا النهج، ثم حدد **التالي**.
6. في المقطع **مراجعة+إنشاء** ، تحقق من صحة كل المعلومات التي تم إدخالها، ثم حدد **إنشاء**.

## <a name="configure-custom-indicators"></a>تكوين مؤشرات مخصصة

يمكن Defender for Endpoint على نظام iOS المسؤولين من تكوين المؤشرات المخصصة على أجهزة iOS أيضا. لمزيد من المعلومات حول كيفية تكوين المؤشرات المخصصة، راجع [إدارة المؤشرات](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> يدعم Defender ل Endpoint على نظام iOS إنشاء مؤشرات مخصصة فقط عناوين IP وعناوين URL/المجالات.

## <a name="configure-option-to-send-in-app-feedback"></a>الخيار "تكوين" لإرسال الملاحظات داخل التطبيق 

أصبح لدى العملاء الآن خيار تكوين القدرة على إرسال بيانات الملاحظات إلى Microsoft ضمن تطبيق Defender for Endpoint. تساعد بيانات الملاحظات Microsoft على تحسين المنتجات وإصلاح المشاكل.

> [!NOTE]
> بالنسبة لعملاء السحابة في الولايات المتحدة، يتم تعطيل تجميع بيانات **الملاحظات بشكل** افتراضي. 

استخدم الخطوات التالية لتكوين الخيار لإرسال بيانات الملاحظات إلى Microsoft:

1. في [إدارة نقاط النهاية من Microsoft مركز الإدارة واذهب](https://go.microsoft.com/fwlink/?linkid=2109431) إلى سياسات تكوين **تطبيقات** **AppsAddManaged** >  >  >  **الأجهزة**.
1. قم امنح النهج اسما، النظام الأساسي > **iOS/iPadOS**، وحدد نوع ملف التعريف.
1. حدد **Microsoft Defender لنقطة النهاية** ك التطبيق الهدف.
1. في الإعدادات، حدد **استخدام مصمم التكوين** وأضف **DefenderSendFeedback** كمفتاح ونوع القيمة ك **Boolean**
   - لإزالة قدرة المستخدمين النهائيين على تقديم الملاحظات، قم بتعيين القيمة ك `false` وتعيين هذا النهج للمستخدمين. بشكل افتراضي، يتم تعيين هذه القيمة إلى `true`. بالنسبة لعملاء الحكومة الأمريكية، يتم تعيين القيمة الافتراضية إلى "خطأ".
   - للمستخدمين الذين تم `true`تعيين المفتاح لديهم ك ، سيكون هناك خيار لإرسال بيانات الملاحظات إلى Microsoft ضمن التطبيق (القائمة > تعليمات & ملاحظاتك > إرسال ملاحظات إلى Microsoft)
1. انقر **فوق التالي** ثم قم بتعيين ملف التعريف هذا إلى الأجهزة/المستخدمين المستهدفين.


## <a name="report-unsafe-site"></a>الإبلاغ عن موقع غير آمن

تقوم مواقع التصيد الاحتيالي على الويب بانتحال مواقع الويب الموثوق بها بغرض الحصول على معلوماتك الشخصية أو المالية. تفضل بزيارة [صفحة تقديم ملاحظات](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) حول حماية الشبكة إذا كنت تريد الإبلاغ عن موقع ويب قد يكون موقع تصيد احتيالي.
