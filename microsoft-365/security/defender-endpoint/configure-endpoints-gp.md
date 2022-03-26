---
title: أجهزة Windows إلى Microsoft Defender ل Endpoint عبر نهج المجموعة
description: استخدم "نهج المجموعة" لنشر حزمة التكوين على Windows الأجهزة بحيث يتم تهيئةها للخدمة.
keywords: تكوين الأجهزة باستخدام نهج المجموعة، وإدارة الأجهزة، وتكوين Microsoft Defender للأجهزة Endpoint، وتهيئة Microsoft Defender للأجهزة Endpoint، ون نهج المجموعة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.date: 12/07/2021
ms.technology: mde
ms.openlocfilehash: 3b20242247e33f8550ce4d153c2f2618c64d7007
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570160"
---
# <a name="onboard-windows-devices-using-group-policy"></a>أجهزة Windows باستخدام "نهج المجموعة" 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

[!include[Prerelease information](../../includes/prerelease.md)]

**ينطبق على:**

- نهج المجموعة
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsgp-abovefoldlink)

> [!NOTE]
> لاستخدام تحديثات نهج المجموعة (GP) لنشر الحزمة، يجب أن تكون على Windows Server 2008 R2 أو إصدار أحدث.
>
> بالنسبة Windows Server 2019 و Windows Server 2022، قد تحتاج إلى استبدال NT AUTHORITY\Well-Known-System-Account بملف NT AUTHORITY\SYSTEM لملف XML الذي ينشئه تفضيلات نهج المجموعة.

> [!NOTE]
> إذا كنت تستخدم حل Microsoft Defender الجديد والموحد لنقطة النهاية ل Windows Server 2012 R2 و2016، فالرجاء التأكد من أنك تستخدم أحدث ملفات ADMX في متجرك المركزي للوصول إلى خيارات نهج نقطة النهاية من Microsoft Defender الصحيحة. الرجاء الرجوع [إلى كيفية إنشاء](/troubleshoot/windows-client/group-policy/create-and-manage-central-store) المتجر المركزي للقالب الإدارية لنهة المجموعة وإدارته في Windows وتنزيل أحدث الملفات لاستخدامها **مع** Windows 10.

اطلع على [ملف PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) [أو Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) لرؤية المسارات المختلفة في نشر Defender لنقطة النهاية.

1. افتح ملف حزمة تكوين GP (`WindowsDefenderATPOnboardingPackage.zip`) الذي قمت بتنزيلها من معالج إعداد الخدمة. يمكنك أيضا الحصول على الحزمة من مدخل Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">:</a>

    1. في جزء التنقل **، حدد الإعدادات** >  **EndpointsDevice** >  **managementOnboarding**  > .

    1. حدد نظام التشغيل.

    1. في الحقل **أسلوب النشر** ، حدد **نهج المجموعة**.

    1. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

2. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك مجلد يسمى *اختياريParamsPolicy* والملف *WindowsDefenderATPOnboardingScript.cmd*.

3. لإنشاء نهج نهج المجموعة الجديد، افتح وحدة تحكم إدارة نهج  [المجموعة (](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)GPMC)، وانقر بز الماوس الأيمن فوق كائنات نهج المجموعة التي تريد تكوينها وانقر فوق **جديد**. أدخل اسم "مجموعة العناصر" الجديدة في مربع الحوار الذي يتم عرضه وانقر فوق **موافق**.

4. افتح وحدة [تحكم إدارة نهج](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) المجموعة (GPMC)، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

5. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**، ثم **التفضيلات**، ثم إعدادات **لوحة التحكم**.

6. انقر بز الماوس الأيمن فوق **المهام المجدولة**، وأشير إلى **جديد**، ثم انقر فوق مهمة فورية (على الأقل **Windows 7)**.

7. في نافذة **المهمة** التي تفتح، انتقل إلى علامة **التبويب عام** . ضمن **خيارات الأمان،** انقر **فوق تغيير المستخدم أو المجموعة** وا اكتب النظام، ثم انقر **فوق التحقق من الأسماء** ثم **موافق**. يظهر NT AUTHORITY\SYSTEM ك حساب المستخدم الذي سيتم تشغيل المهمة عليه.

8. حدد **تشغيل ما إذا كان المستخدم قد سجل دخوله** أم لا وحدد خانة الاختيار **تشغيل بأعلى** امتيازات.

9. في الحقل الاسم، اكتب اسما مناسبا للمهمة المجدولة (على سبيل المثال، Defender لنشر نقطة النهاية).

10. انتقل إلى علامة **التبويب** إجراءات وحدد **جديد...** تأكد من **تحديد بدء** برنامج في **حقل** الإجراء. أدخل مسار UNC، باستخدام اسم المجال المؤهل بالكامل (FQDN) الخاص بخادم الملفات (FQDN) لملف *WindowsDefenderATPOnboardingScript.cmd* المشترك.

11. حدد **موافق** وأغلق أي نوافذ GPMC مفتوحة.

12. لربط "مجموعة وحدات المجموعة" بوحدة تنظيم (OU)، انقر بز الماوس الأيمن وحدد ربط "مجموعة" **موجودة**. في مربع الحوار الذي يتم عرضه، حدد كائن نهج المجموعة الذي تريد ربطه. انقر فوق **موافق**.

> [!TIP]
> بعد تشغيل الجهاز، يمكنك اختيار تشغيل اختبار الكشف للتحقق من أن الجهاز مدرج بشكل صحيح في الخدمة. للحصول على مزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Defender لنقطة النهاية تم تعيينه حديثا](run-detection-test.md).

## <a name="additional-defender-for-endpoint-configuration-settings"></a>إعدادات تكوين إضافية ل Defender لنقطة النهاية

لكل جهاز، يمكنك تحديد ما إذا كان يمكن تجميع عينات من الجهاز عند تقديم طلب عبر Microsoft 365 Defender لإرسال ملف لتحليله بعمق.

يمكنك استخدام نهج المجموعة (GP) لتكوين الإعدادات، مثل إعدادات المشاركة العينة المستخدمة في ميزة التحليل العميق.

### <a name="configure-sample-collection-settings"></a>تكوين إعدادات المجموعة العينة

1. على جهاز إدارة GP، انسخ الملفات التالية من حزمة التكوين:

    - نسخ _AtpConfiguration.admx_ إلى _C:\\Windows\\ PolicyDefinitions_

    - نسخ _AtpConfiguration.adml_ إلى _C:\\Windows\\ PolicyDefinitionsen-US\\_

    إذا كنت تستخدم متجرا [مركزيا ل القوالب الإدارية لنسخ](https://support.microsoft.com/help/3087759/how-to-create-and-manage-the-central-store-for-group-policy-administra) نهج المجموعة، انسخ الملفات التالية من حزمة التكوين:

    - نسخ _AtpConfiguration.admx_ إلى _\\\<forest.root\>\\\\SysVolPoliciesPolicyDefinitions\\\<forest.root\>\\\\_

    - نسخ _AtpConfiguration.adml_ إلى _\\\<forest.root\>\\\\SysVolPoliciesPolicyDefinitionsen-US\\\<forest.root\>\\\\\\_

2. افتح وحدة [تحكم إدارة نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11)، وانقر بضغطة زر الماوس الأيمن فوق "نهج المجموعة" الذي تريد تكوينه، ثم انقر فوق **تحرير**.

3. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**.

4. انقر **فوق "سياسات**"، ثم **فوق قوالب إدارية**.

5. انقر **Windows مكونات ثم** انقر فوق **Windows Defender ATP**.

6. اختر تمكين المشاركة العينة من أجهزتك أو تعطيلها.

> [!NOTE]
> إذا لم تقوم بتعيين قيمة، فقيمة افتراضية هي تمكين مجموعة العينة.

## <a name="other-recommended-configuration-settings"></a>إعدادات التكوين المستحسنة الأخرى

### <a name="update-endpoint-protection-configuration"></a>تحديث تكوين حماية نقطة النهاية

بعد تكوين البرنامج النصي لتهيئة التهيئة، تابع تحرير نهج المجموعة نفسه لإضافة تكوينات حماية نقطة النهاية. قم بإجراء عمليات تحرير نهج المجموعة من نظام يعمل Windows 10 أو Server 2019 أو Windows 11 أو Windows Server 2022 لضمان حصولك على جميع برنامج الحماية من الفيروسات من Microsoft Defender المطلوبة. قد تحتاج إلى إغلاق كائن نهج المجموعة وإعادة فتحه لتسجيل إعدادات تكوين Defender ATP.

تقع كل السياسات ضمن `Computer Configuration\Policies\Administrative Templates`.

**موقع النهج:** \Windows Components\Windows Defender ATP

النهج|الإعداد
---|---
Enable\Disable Sample collection|تم التمكين - تم التحقق من "تمكين مجموعة العينة على الأجهزة"

<br>

**موقع النهج:** \Windows مكونات\برنامج الحماية من الفيروسات من Microsoft Defender

النهج|الإعداد
---|---
تكوين الكشف للتطبيقات التي يحتمل أن تكون غير مرغوب فيها|Enabled, Block

<br>

**موقع النهج:** \Windows المكونات\برنامج الحماية من الفيروسات من Microsoft Defender\الخرائط

النهج|الإعداد
---|---
الانضمام إلى Microsoft MAPS|الخرائط المتقدمة التي تم تمكينها
إرسال نماذج الملفات عند الحاجة إلى إجراء المزيد من التحليلات | تمكين، إرسال عينات آمنة

<br>

**موقع النهج:** \Windows المكونات\برنامج الحماية من الفيروسات من Microsoft Defender\الحماية في الوقت الحقيقي

النهج|الإعداد
---|---
إيقاف تشغيل الحماية في الوقت الحقيقي|معطل
تشغيل مراقبة السلوك|تم التمكين
فحص جميع الملفات والمرفقات التي تم تنزيلها|تم التمكين
مراقبة نشاط الملف والبرنامج على الكمبيوتر|تم التمكين

<br>

**موقع النهج:** \Windows المكونات\برنامج الحماية من الفيروسات من Microsoft Defender\المسح الضوئي

تقوم هذه الإعدادات بتكوين عمليات فحص دورية لنقطة النهاية. نوصي بإجراء فحص سريع أسبوعيا، مع السماح بالأداء.

النهج|الإعداد
---|---
التحقق من أحدث المعلومات الأمنية عن الفيروسات وبرامج التجسس قبل تشغيل فحص مجدول |تم التمكين

<br>

**موقع النهج:** \Windows المكونات\برنامج الحماية من الفيروسات من Microsoft Defender\الحماية من مخاطر الهجمات من Microsoft Defender\تقليل سطح الهجوم

الحصول على القائمة الحالية لقواعد الحد من الهجمات من نشر قواعد تقليل مساحة الهجوم [الخطوة 3: تنفيذ قواعد ASR](attack-surface-reduction-rules-deployment-implement.md). للحصول على تفاصيل إضافية لكل قواعد، راجع مرجع قواعد [الحد من سطح الهجوم](attack-surface-reduction-rules-reference.md)

1. افتح نهج **"تصغير مساحة الهجوم** ".

1. حدد **تمكين**.

1. حدد الزر **إظهار** .

1. أضف كل GUID في **الحقل اسم القيمة** بقيمة 2.

   سيتم إعداد كل منها للتدقيق فقط.

   ![صورة لتكوين تقليل مساحة الهجوم.](images/asr-guid.png)

النهج|الموقع|الإعداد
---|---|---
تكوين الوصول إلى المجلدات الخاضعة للتحكم| \Windows Components\برنامج الحماية من الفيروسات من Microsoft Defender\الحماية من مخاطر الهجمات من Microsoft Defender\التحكم بالوصول إلى المجلدات| تم التمكين، وضع التدقيق

## <a name="run-a-detection-test-to-verify-onboarding"></a>تشغيل اختبار الكشف للتحقق من ال

بعد تشغيل الجهاز، يمكنك أن تختار تشغيل اختبار الكشف للتحقق من أن الجهاز مواد بشكل صحيح للخدمة. لمزيد من المعلومات، راجع [تشغيل اختبار الكشف على جهاز Microsoft Defender ل Endpoint](run-detection-test.md) تم تشغيله حديثا.

## <a name="offboard-devices-using-group-policy"></a>أجهزة إيقاف التشغيل باستخدام "نهج المجموعة"

لأسباب تتعلق الأمان، ستنتهي صلاحية الحزمة المستخدمة في أجهزة Offboard بعد 30 يوما من تاريخ تنزيلها. سيتم رفض حزم إيقاف التشغيل منتهية الصلاحية المرسلة إلى جهاز. عند تنزيل حزمة إيقاف التشغيل، سيتم إعلامك بتاريخ انتهاء صلاحية الحزم، كما سيتم تضمينها في اسم الحزمة.

> [!NOTE]
> يجب عدم نشر سياسات التكئب أو إيقاف التشغيل على الجهاز نفسه في الوقت نفسه، وإلا سيتسبب ذلك في حدوث تضاربات لا يمكن التنبؤ بها.

1. احصل على حزمة إيقاف التشغيل من مدخل Microsoft 365 Defender<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">:</a>

    1. في جزء التنقل **، حدد الإعدادات** >  **EndpointsDevice** >  **managementOffboarding** > .

    1. حدد نظام التشغيل.
    
    1. في الحقل **أسلوب النشر** ، حدد **نهج المجموعة**.

    1. انقر **فوق تنزيل الحزمة** واحفظ .zip الملف.

2. استخراج محتويات الملف .zip إلى موقع مشترك للقراءة فقط يمكن الوصول إليه من قبل الجهاز. يجب أن يكون لديك ملف *يسمى WindowsDefenderATPOffboardingScript_valid_until_YYYY MM-DD.cmd*.

3. افتح وحدة [تحكم إدارة نهج](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) المجموعة (GPMC)، وانقر بز الماوس الأيمن فوق كائن نهج المجموعة (GPO) الذي تريد تكوينه وانقر فوق **تحرير**.

4. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر، ثم** **التفضيلات**، ثم إعدادات **لوحة التحكم**.

5. انقر **بضغطة زر الماوس الأيمن فوق المهام المجدولة**، وأشير إلى **جديد**، ثم انقر فوق **مهمة فورية**.

6. في نافذة **المهمة** التي تفتح، انتقل إلى علامة **التبويب عام** . اختر حساب مستخدم النظام المحلي (BUILTIN\SYSTEM) ضمن **خيارات الأمان**.

7. حدد **تشغيل سواء قام المستخدم بتسجيل الدخول أم** لا وحدد خانة  الاختيار تشغيل بأعلى امتيازات.

8. في الحقل الاسم، اكتب اسما مناسبا للمهمة المجدولة (على سبيل المثال، Defender لنشر نقطة النهاية).

9. انتقل إلى علامة **التبويب إجراءات** وحدد **جديد...**. تأكد من **تحديد بدء** برنامج في **حقل** الإجراء. أدخل مسار UNC، باستخدام اسم المجال المؤهل بالكامل (FQDN) الخاص بخادم الملفات المشترك *WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd* .

10. حدد **موافق** وأغلق أي نوافذ GPMC مفتوحة.

> [!IMPORTANT]
> يؤدي إيقاف التشغيل إلى إيقاف الجهاز عن إرسال بيانات المستشعر إلى المدخل ولكن سيتم الاحتفاظ بالبيانات من الجهاز، بما في ذلك الإشارة إلى أي تنبيهات لديه لمدة تصل إلى 6 أشهر.

## <a name="monitor-device-configuration"></a>مراقبة تكوين الجهاز

باستخدام "نهج المجموعة"، لا يوجد خيار لمراقبة نشر النهج على الأجهزة. يمكن القيام بالمراقبة مباشرة على المدخل، أو باستخدام أدوات النشر المختلفة.

## <a name="monitor-devices-using-the-portal"></a>مراقبة الأجهزة باستخدام المدخل

1. انتقل إلى مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender.</a>
2. انقر **فوق مخزون الأجهزة**.
3. تحقق من ظهور الأجهزة.

> [!NOTE]
> قد يستغرق ظهور الأجهزة على قائمة **الأجهزة عدة أيام**. يشمل ذلك الوقت الذي يستغرقه توزيع السياسات على الجهاز والوقت الذي يستغرقه تسجيل دخول المستخدم والوقت الذي تستغرقه نقطة النهاية لبدء إعداد التقارير.

## <a name="setup-defender-av-policies"></a>سياسات Setup Defender AV

إنشاء نهج مجموعة جديد أو تجميع هذه الإعدادات مع النهج الأخرى. يعتمد ذلك على بيئة العملاء وكيفية تقديمهم للخدمة من خلال استهداف وحدات تنظيمية مختلفة.

1. بعد اختيار GP، أو إنشاء واحد جديد، قم بتحرير GP.

2. استعرض بحثا **عن تكوين الكمبيوتر** >  **قوالبAdministrative** >  >  **Windows مكونات** >  >  برنامج الحماية من الفيروسات من Microsoft Defender **الحماية في الوقت الحقيقي**.

    :::image type="content" source="images/realtime-protect.png" alt-text="الحماية في الوقت الحقيقي.":::

1. في المجلد "عزل"، قم بتكوين إزالة العناصر من مجلد "الفحص".

    :::image type="content" source="images/removal-items-quarantine1.png" alt-text="إزالة مجلد عزل العناصر.":::

    :::image type="content" source="images/config-removal-items-quarantine2.png" alt-text="عزل إزالة المؤتمرات.":::

4. في مجلد المسح الضوئي، قم بتكوين إعدادات الفحص.

    :::image type="content" source="images/gpo-scans.png" alt-text="عمليات فحص gpo.":::

### <a name="monitor-all-files-in-real-time-protection"></a>مراقبة جميع الملفات في الحماية في الوقت الحقيقي

استعرض بحثا **عن القوالب** \> الإدارية **لنهج** \>  \> تكوين **الكمبيوتر Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **في الوقت الحقيقي**.

 بما أن قيمة "مسح الملفات الواردة وال الصادرة" (افتراضيا) هي 0، يتغير نهج المجموعة الخاص ب "تكوين المراقبة لنشاط البرنامج والملفات الواردة وال الصادرة" لإعداد الإعداد "ثنائي الاتجاه (كامل عند الوصول)" إلى معطل.

:::image type="content" source="images/config-monitor-incoming-outgoing-file-act.png" alt-text="تكوين مراقبة لنشاط الملف الصادر الوارد.":::

### <a name="configure-windows-defender-smartscreen-settings"></a>تكوين إعدادات smartScreen Windows Defender

1. استعرض بحثا **عن القوالب** \> الإدارية **لنهج** \>  \> تكوين **الكمبيوتر Windows مكونات Windows** \> **SmartScreen** \> **Defender**.

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="config windows defender smart screen explorer.":::
 
2. استعرض إلى **تكوين الكمبيوتر** >  **قوالبAdministrative** >  >  **Windows مكونات** >  Windows **Defender SmartScreen** >  **Microsoft Edge**.

    :::image type="content" source="images/config-windows-def-smartscr-explorer.png" alt-text="config windows defender smart screen Edge.":::

### <a name="configure-potentially-unwanted-applications"></a>تكوين التطبيقات التي يحتمل أن تكون غير مرغوب فيها

استعرض بحثا **عن القوالب** \> الإدارية **لنهج** \>  \> تكوين **الكمبيوتر Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \> **.**

:::image type="content" source="images/config-potential-unwanted-apps.png" alt-text="اخلط التطبيق المحتمل غير المرغوب فيه.":::

:::image type="content" source="images/config-potential-unwanted-apps2.png" alt-text="إمكانية عقد المؤتمرات.":::

### <a name="configure-cloud-deliver-protection-and-send-samples-automatically"></a>تكوين حماية تسليم السحابة وإرسال عينات تلقائيا

استعرض بحثا **عن القوالب** \> الإدارية **لنهج** \>  \> تكوين **الكمبيوتر Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **الخرائط**.

:::image type="content" source="images/gpo-maps1.png" alt-text="الخرائط.":::

:::image type="content" source="images/gpo-maps-block-atfirst-sight.png" alt-text="من النظرة الأولى.":::

:::image type="content" source="images/gpo-maps-join-ms-maps.png" alt-text="الانضمام إلى خرائط microsoft.":::

:::image type="content" source="images/send-file-sample-further-analysis-require.png" alt-text="إرسال عينة ملف عند الحاجة إلى إجراء المزيد من التحليلات.":::

> [!NOTE]
> سيوفر **الخيار إرسال كل** العينات أكبر عدد من تحليل الثنائيات/البرامج النصية/المستندات التي تزيد من وضعية الأمان.
يحد **الخيار إرسال عينات** آمنة من نوع الثنائيات/البرامج النصية/المستندات التي يتم تحليلها، كما يقلل من وضعية الأمان. 

لمزيد من المعلومات، راجع تشغيل الحماية [السحابية في](enable-cloud-protection-microsoft-defender-antivirus.md) برنامج الحماية من الفيروسات من Microsoft Defender والحماية السحابية [ونموذج الإرسال في برنامج الحماية من الفيروسات من Microsoft Defender.](cloud-protection-microsoft-antivirus-sample-submission.md)

### <a name="check-for-signature-update"></a>التحقق من تحديث التوقيع

استعرض بحثا **عن القوالب** \> الإدارية **لنهج** \>  \> تكوين **الكمبيوتر Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **معلومات الأمان**.

:::image type="content" source="images/signature-update-1.png" alt-text="تحديث التوقيع.":::

:::image type="content" source="images/signature-update-2.png" alt-text="تحديث تعريف التوقيع.":::

### <a name="configure-cloud-deliver-timeout-and-protection-level"></a>تكوين 2010 مستوى 2016 للتسليم السحابي والحماية

استعرض بحثا **عن القوالب** \> الإدارية **لنهج** \>  \> تكوين **الكمبيوتر Windows مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **MpEngine**.
عند تكوين نهج مستوى الحماية السحابية إلى نهج  برنامج الحماية من الفيروسات من Microsoft Defender الافتراضي، سيؤدي ذلك إلى تعطيل النهج. هذا هو المطلوب لتعيين مستوى الحماية إلى windows الافتراضي.

:::image type="content" source="images/config-extended-cloud-check.png" alt-text="التحقق من السحابة الموسعة في المؤتمرات.":::

:::image type="content" source="images/cloud-protection-level.png" alt-text="مستوى الحماية السحابية في المؤتمرات.":::

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows الأجهزة باستخدام أدوات إدارة أجهزة المحمول](configure-endpoints-mdm.md)
- [أجهزة Windows باستخدام برنامج نصي محلي](configure-endpoints-script.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
- [تشغيل اختبار الكشف على Microsoft Defender للأجهزة التي تم تشغيلها حديثا في نقطة النهاية](run-detection-test.md)
- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](troubleshoot-onboarding.md)
