---
title: اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR)
description: يوفر إرشادات لاختبار نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR).
keywords: نشر قواعد تقليل الأجزاء المعرضة للهجوم، ونشر ASR، وتمكين قواعد asr، وتكوين ASR، ونظام منع الاختراق المضيف، وقواعد الحماية، وقواعد مكافحة الاستغلال، وقواعد مكافحة الاستغلال، وقواعد الاستغلال، وقواعد منع العدوى، Microsoft Defender لنقطة النهاية، وتكوين قواعد ASR
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- M365-security-compliance
- m365solution-asr-rules
ms.date: 1/18/2022
ms.openlocfilehash: d224da7f03d93769c3bd37f10af9b888c630c441
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969869"
---
# <a name="test-attack-surface-reduction-asr-rules"></a>اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR)

يساعدك اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR) على تحديد ما إذا كانت القواعد ستؤدي إلى تعطيل عمليات خط العمل قبل تمكين أي قاعدة. من خلال البدء بمجموعة صغيرة خاضعة للتحكم، يمكنك الحد من انقطاعات العمل المحتملة أثناء توسيع النشر عبر مؤسستك.

ابدأ نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR) مع الحلقة 1.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-testing-steps.png" alt-text="خطوات اختبار قواعد ASR" lightbox="images/asr-rules-testing-steps.png":::
  
## <a name="step-1-test-asr-rules-using-audit"></a>الخطوة 1: اختبار قواعد ASR باستخدام التدقيق

ابدأ مرحلة الاختبار عن طريق تشغيل قواعد ASR مع القواعد المعينة للتدقيق، بدءا من المستخدمين أو الأجهزة البطلة في الحلقة 1. عادة ما تكون التوصية هي تمكين جميع القواعد (في التدقيق) بحيث يمكنك تحديد القواعد التي يتم تشغيلها أثناء مرحلة الاختبار. لاحظ أن القواعد التي تم تعيينها إلى التدقيق لا تؤثر بشكل عام على وظائف الكيان أو الكيانات التي يتم تطبيق القاعدة عليها ولكنها تنشئ أحداثا مسجلة للتقييم؛ لا يوجد أي تأثير على المستخدمين النهائيين.

### <a name="configure-asr-rules-using-mem"></a>تكوين قواعد ASR باستخدام MEM

يمكنك استخدام أمان نقطة نهاية Microsoft إدارة نقاط النهاية (MEM) لتكوين قواعد ASR المخصصة.

1. افتح [مركز إدارة Microsoft إدارة نقاط النهاية](https://endpoint.microsoft.com/#home).
2. انتقل إلى **تقليل الأجزاء المعرضة للهجوم** **الأمني** >  لنقطة النهاية.
3. حدد **إنشاء نهج**.
4. في **النظام الأساسي**، حدد **Windows 10 والإي وقت لاحق**، وفي **ملف التعريف**، حدد **قواعد تقليل الأجزاء المعرضة للهجوم**.
  
    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-create-profile.png" alt-text="صفحة إنشاء ملف التعريف لقواعد ASR" lightbox="images/asr-mem-create-profile.png":::

5. انقر فوق **"إنشاء**".
6. في علامة التبويب **"Basics** " في جزء **"Create profile** "، في **"Name"** ، أضف اسما للنهج الخاص بك. في **الوصف** ، أضف وصفا لنهج قواعد ASR.
7. في علامة التبويب **إعدادات التكوين** ، ضمن **قواعد تقليل الأجزاء المعرضة للهجوم**، قم بتعيين كافة القواعد إلى **وضع التدقيق**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-configuration-settings.png" alt-text="تكوين قواعد ASR إلى وضع التدقيق" lightbox="images/asr-mem-configuration-settings.png":::

    >[!Note]
    >هناك تباينات في بعض قوائم وضع قواعد ASR؛ يوفر _المحظور_ _والممكن_ نفس الوظيفة.

8. [اختياري] في جزء **علامات النطاق** ، يمكنك إضافة معلومات العلامة إلى أجهزة معينة. يمكنك أيضا استخدام علامات النطاق والتحكم في الوصول المستندة إلى الدور للتأكد من أن المسؤولين المناسبين لديهم حق الوصول والرؤية إلى كائنات Intune الصحيحة. تعرف على المزيد: [استخدم التحكم في الوصول استنادا إلى الدور (RBAC) وعلامات النطاق ل تكنولوجيا المعلومات الموزعة في Intune](/mem/intune/fundamentals/scope-tags).
9. في جزء **"الواجبات** "، يمكنك نشر ملف التعريف أو "تعيينه" إلى مجموعات المستخدمين أو الأجهزة. تعرف على المزيد: [تعيين ملفات تعريف الأجهزة في Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. راجع الإعدادات في جزء **Review + create** . انقر فوق **"إنشاء** " لتطبيق القواعد.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-review-create.png" alt-text="صفحة إنشاء ملف التعريف" lightbox="images/asr-mem-review-create.png":::

يتم سرد نهج تقليل الأجزاء المعرضة للهجوم الجديد لقواعد ASR في **أمان نقطة النهاية | تقليل الأجزاء المعرضة للهجوم**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-my-asr-rules.png" alt-text=" صفحة تقليل الأجزاء المعرضة للهجوم" lightbox="images/asr-mem-my-asr-rules.png":::

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>الخطوة 2: فهم صفحة الإبلاغ عن قواعد تقليل الأجزاء المعرضة للهجوم في مدخل Microsoft 365 Defender

تم العثور على صفحة إعداد تقارير قواعد ASR في **مدخل Microsoft 365 Defender** > **تقارير** > **قواعد تقليل الأجزاء المعرضة للهجوم**. تحتوي هذه الصفحة على ثلاث علامات تبويب:

- المكتشفه
- التكوين
- إضافة استثناءات

### <a name="detections-tab"></a>علامة التبويب "الكشف"

يوفر مخططا زمنيا لمدة 30 يوما للتدقيق المكتشف والأحداث المحظورة.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01.png" alt-text="علامة التبويب &quot;الكشف عن قواعد تقليل الأجزاء المعرضة للهجوم&quot;" lightbox="images/asr-defender365-01.png":::

يوفر جزء قواعد تقليل الأجزاء المعرضة للهجوم نظرة عامة على الأحداث المكتشفة على أساس كل قاعدة.

>[!Note]
>هناك بعض التباينات في تقارير قواعد ASR. تقوم Microsoft بتحديث سلوك تقارير قواعد ASR لتوفير تجربة متسقة.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01b.png" alt-text="صفحة قواعد تقليل الأجزاء المعرضة للهجوم" lightbox="images/asr-defender365-01b.png"::: 

انقر فوق **"عرض عمليات الكشف**" لفتح علامة التبويب "**الكشف".**

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="اكتشاف قواعد تقليل الأجزاء المعرضة للهجوم" lightbox="images/asr-defender365-reports-detections.png":::

يوفر **جزء GroupBy** **وعامل التصفية** الخيارات التالية:

يقوم **GroupBy بإرجاع** النتائج المعينة إلى المجموعات التالية:

- لا يوجد تجميع
- الملف المكتشف
- التدقيق أو الحظر
- القاعده
- تطبيق المصدر
- Device
- User
- Publisher

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="تقوم قواعد تقليل الأجزاء المعرضة للهجوم بالكشف عن عامل تصفية GroupBy" lightbox="images/asr-defender365-reports-detections.png":::

يفتح **عامل التصفية** صفحة **"تصفية على القواعد**"، والتي تمكنك من تحديد نطاق النتائج إلى قواعد ASR المحددة فقط:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-filter.png" alt-text="تصفية قواعد تقليل الأجزاء المعرضة للهجوم على القواعد" lightbox="images/asr-defender365-filter.png":::

>[!Note]
>إذا كان لديك ترخيص Microsoft Microsoft 365 Security E5 أو A5 أو Windows E5 أو A5، يفتح الارتباط التالي تقارير Microsoft Defender 365 > [تقليل الأجزاء المعرضة للهجوم](https://security.microsoft.com/asr?viewid=detections) > علامة التبويب "الكشف".

### <a name="configuration-tab"></a>علامة التبويب "تكوين"

القوائم - على أساس كل كمبيوتر - الحالة الإجمالية لقواعد ASR: إيقاف التشغيل والتدقيق والحظر.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.png" alt-text="علامة التبويب تكوين قواعد تقليل الأجزاء المعرضة للهجوم وإدخال في صفحتها" lightbox="images/asr-defender365-configurations.png":::

في علامة التبويب "تكوينات"، يمكنك التحقق، على أساس كل جهاز، من قواعد ASR التي تم تمكينها، وفي أي وضع، عن طريق تحديد الجهاز الذي تريد مراجعة قواعد ASR له.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.settings.png" alt-text="تمكين قواعد تقليل الأجزاء المعرضة للهجوم ووضعها" lightbox="images/asr-defender365-configurations.settings.png":::

يفتح ارتباط **بدء الاستخدام** مركز إدارة Microsoft إدارة نقاط النهاية، حيث يمكنك إنشاء نهج حماية نقطة النهاية ل ASR أو تعديله:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem1.png" alt-text="عنصر قائمة أمان *Endpoint على صفحة Overview" lightbox="images/asr-defender365-05b-mem1.png":::

في | أمان نقطة النهاية نظرة عامة، حدد **تقليل الأجزاء المعرضة للهجوم**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem2.png" alt-text="تقليل الأجزاء المعرضة للهجوم في MEM" lightbox="images/asr-defender365-05b-mem2.png":::

| أمان نقطة النهاية يفتح جزء تقليل الأجزاء المعرضة للهجوم:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem3.png" alt-text="جزء تقليل الأجزاء المعرضة لهجوم أمان نقطة النهاية" lightbox="images/asr-defender365-05b-mem3.png":::

>[!Note]
>إذا كان لديك ترخيص Microsoft Defender 365 E5 (أو Windows E5؟)، فسيفتح هذا الارتباط تقارير Microsoft Defender 365 > علامة تبويب الأجزاء المعرضة للهجوم > علامة التبويب [تكوينات](https://security.microsoft.com/asr?viewid=configuration) .

### <a name="add-exclusions"></a>إضافة استثناءات

توفر علامة التبويب هذه طريقة لتحديد الكيانات المكتشفة (على سبيل المثال، الإيجابيات الخاطئة) للاستبعاد. عند إضافة الاستثناءات، يوفر التقرير ملخصا للتأثير المتوقع.

>[!Note]
> يتم احترام استثناءات Microsoft Defender Antivirus AV من خلال قواعد ASR.  راجع [تكوين الاستثناءات والتحقق من صحتها استنادا إلى الملحق أو الاسم أو الموقع](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="Images/asr-defender365-06d.png" alt-text="الجزء الخاص باستثناء الملف المكتشف" lightbox="Images/asr-defender365-06d.png":::

> [!Note]
>إذا كان لديك ترخيص Microsoft Defender 365 E5 (أو Windows E5؟)، فسيفتح هذا الارتباط تقارير Microsoft Defender 365 > علامة التبويب "تقليل الأجزاء المعرضة للهجوم" > علامة التبويب ["استثناءات](https://security.microsoft.com/asr?viewid=exclusions) ".

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>استخدام PowerShell كطريقة بديلة لتمكين قواعد ASR

يمكنك استخدام PowerShell - كبديل ل MEM - لتمكين قواعد ASR في وضع التدقيق لعرض سجل التطبيقات التي كان سيتم حظرها إذا تم تمكين الميزة بالكامل. يمكنك أيضا الحصول على فكرة عن عدد المرات التي سيتم فيها تشغيل القواعد أثناء الاستخدام العادي.

لتمكين قاعدة تقليل الأجزاء المعرضة للهجوم في وضع التدقيق، استخدم PowerShell cmdlet التالية:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

أين `<rule ID>` توجد [قيمة GUID لقاعدة تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md).

لتمكين جميع قواعد تقليل الأجزاء المعرضة للهجوم المضافة في وضع التدقيق، استخدم أمر Cmdlet PowerShell التالي:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> إذا كنت تريد التدقيق الكامل في كيفية عمل قواعد تقليل الأجزاء المعرضة للهجوم في مؤسستك، فستحتاج إلى استخدام أداة إدارة لنشر هذا الإعداد على الأجهزة في شبكتك(شبكاتك).

يمكنك أيضا استخدام موفري خدمة تكوين نهج المجموعة أو Intune أو إدارة أجهزة المحمول (MDM) لتكوين الإعداد وتوزيعه. تعرف على المزيد في [مقالة قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction.md) الرئيسي.

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>استخدام Windows عارض الأحداث Review كبديل لصفحة الإبلاغ عن قواعد تقليل الأجزاء المعرضة للهجوم في مدخل Microsoft 365 Defender

لمراجعة التطبيقات التي كان سيتم حظرها، افتح عارض الأحداث وقم بالتصفية لمعرف الحدث 1121 في سجل Microsoft-Windows-Windows Defender/Operational. يسرد الجدول التالي كافة أحداث حماية الشبكة.

معرف الحدث | الوصف
-|-
 5007 | حدث عند تغيير الإعدادات
 1121 | حدث عند تشغيل قاعدة تقليل الأجزاء المعرضة للهجوم في وضع الحظر
 1122 | حدث عند تشغيل قاعدة تقليل الأجزاء المعرضة للهجوم في وضع التدقيق

## <a name="additional-topics-in-this-deployment-collection"></a>مواضيع إضافية في مجموعة النشر هذه

[نظرة عامة على دليل نشر قواعد الحد من سطح الهجوم (ASR)](attack-surface-reduction-rules-deployment.md)

[تخطيط نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[تمكين قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-implement.md)

[تشغيل قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

[مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md)
