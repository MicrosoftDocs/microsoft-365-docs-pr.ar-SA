---
title: اختبار قواعد الحد من سطح الهجوم (ASR)
description: يوفر إرشادات لاختبار نشر قواعد تقليل مستوى الهجوم (ASR).
keywords: نشر قواعد تقليل مساحة الهجوم ونشر ASR وتمكين قواعد asr وتكوين ASR ونظام منع اقتحام المضيف وقواعد الحماية وقواعد مكافحة استغلالها وقواعد مكافحة استغلالها واستغلالها وقواعد منع الإصابة و Microsoft Defender ل Endpoint وتكوين قواعد ASR
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
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 85d1400f390d9666c39ef13ffb484d17cad4a4c8
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682185"
---
# <a name="step-2-test-asr-rules"></a>الخطوة 2: اختبار قواعد ASR

يساعدك اختبار قواعد تقليل مساحة الهجوم (ASR) على تحديد ما إذا كانت القواعد ستعيق عمليات خط العمل قبل تمكين أي قاعدة. من خلال البدء في مجموعة صغيرة خاضعة للتحكم، يمكنك الحد من الانقطاعات المحتملة للعمل عند توسيع النشر عبر مؤسستك.

ابدأ نشر قواعد تقليل مستوى الهجوم (ASR) مع الحلقة 1.

> [!div class="mx-imgBorder"]
> ![خطوات اختبار قواعد ASR](images/asr-rules-testing-steps.png)

## <a name="step-1-test-asr-rules-using-audit"></a>الخطوة 1: اختبار قواعد ASR باستخدام التدقيق

ابدأ مرحلة الاختبار من خلال تشغيل قواعد ASR مع القواعد التي تم تعيينها إلى تدقيق، بدءا من مستخدمي الأبطال أو الأجهزة في الحلقة 1. عادة ما تكون التوصية هي تمكين كل القواعد (في التدقيق) بحيث يمكنك تحديد القواعد التي يتم تشغيلها أثناء مرحلة الاختبار. تجدر الإشارة إلى أن القواعد التي يتم تعيينها إلى تدقيق لا تؤثر بشكل عام على وظائف الكيان أو الكيانات التي يتم تطبيق القاعدة عليها، ولكنها تنشئ أحداثا مسجلة للتقييم؛ لا يوجد أي تأثير على المستخدمين النهائيين.

### <a name="configure-asr-rules-using-mem"></a>تكوين قواعد ASR باستخدام MEM

يمكنك استخدام إدارة نقاط النهاية من Microsoft نقطة نهاية (MEM) لتكوين قواعد ASR مخصصة.

1. فتح [إدارة نقاط النهاية من Microsoft إدارة](https://endpoint.microsoft.com/#home)
2. انتقل إلى **الحد من سطح الأمان** >  في نقطة **النهاية**.
3. حدد **إنشاء نهج**.
4. في **النظام** الأساسي، حدد Windows 10 **واللاحقة**، وفي ملف **التعريف**، حدد **قواعد تقليل مساحة الهجوم**.
  
    > [!div class="mx-imgBorder"]
    > ![تكوين ملف تعريف قواعد ASR](images/asr-mem-create-profile.png)

5. انقر **فوق إنشاء**.
6. في علامة **التبويب أساسيات** في الجزء **إنشاء ملف** تعريف، في **الاسم** ، أضف اسما لنمطك. في **الوصف** ، أضف وصفا لن نهج قواعد ASR.
7. في علامة **التبويب إعدادات** التكوين، ضمن قواعد تقليل **مساحة** الهجوم، قم بتعيين كل القواعد إلى **وضع التدقيق**.

    > [!div class="mx-imgBorder"]
    > ![تعيين قواعد ASR إلى وضع التدقيق](images/asr-mem-configuration-settings.png)

    >[!Note]
    >هناك تباينات في بعض قوائم وضع قواعد ASR؛ _يوفر الحظر_ _والتمكين_ الوظائف نفسها.

8. [اختياري] في جزء **علامات النطاق** ، يمكنك إضافة معلومات العلامات إلى أجهزة معينة. يمكنك أيضا استخدام علامات النطاق والتحكم في الوصول المستندة إلى الدور للتأكد من أن المسؤولين المناسبين لديهم حق الوصول والرؤية إلى كائنات Intune الصحيحة. تعرف على المزيد: استخدم علامات النطاق والتحكم بالوصول المستند إلى الدور [(RBAC) ل IT الموزعة في Intune](/mem/intune/fundamentals/scope-tags).
9. في جزء **الواجبات** ، يمكنك نشر ملف التعريف أو "تعيينه" إلى المستخدم أو مجموعات الأجهزة. تعرف على المزيد: [تعيين ملفات تعريف الجهاز في Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. راجع الإعدادات في **الجزء مراجعة +** إنشاء. انقر **فوق** إنشاء لتطبيق القواعد.

   > [!div class="mx-imgBorder"]
   > ![تنشيط نهج قواعد ASR](images/asr-mem-review-create.png)

يتم سرد نهج تقليل مساحة الهجوم الجديد لقواعد ASR في قائمة أمان **نقطة النهاية | تقليل مساحة الهجوم**.

   > [!div class="mx-imgBorder"]
   > ![نهج قاعدة ASR المدرج](images/asr-mem-my-asr-rules.png)

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>الخطوة 2: فهم صفحة إعداد التقارير حول قواعد تقليل مساحة الهجوم في مدخل Microsoft 365 Defender

يتم العثور على صفحة إعداد التقارير لقواعد ASR في Microsoft 365 Defender مدخلReportsAttack  >  > **لسطح القواعد**. تحتوي هذه الصفحة على ثلاث علامات تبويب:

- الاكتشافات
- تكوين
- إضافة استثناءات

### <a name="detections-tab"></a>علامة التبويب "الكشف"

يوفر مخططا زمنيا لمدة 30 يوما للمراجعة والأحداث المحظورة التي تم الكشف عنها.

> [!div class="mx-imgBorder"]
> ![علامة التبويب "اكتشاف قواعد الحد من سطح الهجوم"](images/asr-defender365-01.png)

يوفر جزء قواعد تقليل مساحة الهجوم نظرة عامة على الأحداث المكتشفة على أساس كل قاعدة.

>[!Note]
>هناك بعض التباينات في تقارير قواعد ASR. تعمل Microsoft حاليا على تحديث سلوك تقارير قواعد ASR لتوفير تجربة متناسقة.

> [!div class="mx-imgBorder"]
> ![الكشف عن قواعد الحد من سطح الهجوم](images/asr-defender365-01b.png)

انقر **فوق عرض الاكتشافات** لفتح علامة **التبويب الكشف** .

> [!div class="mx-imgBorder"]
> ![الكشف عن قواعد الحد من سطح الهجوم](images/asr-defender365-reports-detections.png)

يوفر **جزء GroupBy** **وتصفية** الخيارات التالية:

ترجع **GroupBy** النتائج التي تم تعيينها إلى المجموعات التالية:

- بلا تجميع
- ملف تم اكتشافه
- التدقيق أو الحظر
- القاعدة
- تطبيق المصدر
- Device
- User
- Publisher

> [!div class="mx-imgBorder"]
> ![الكشف عن قواعد الحد من سطح الهجوم لتصفية GroupBy](images/asr-defender365-reports-detections.png)

**يفتح** عامل التصفية **صفحة التصفية** على القواعد، التي تمكنك من تحديد نطاق النتائج إلى قواعد ASR المحددة فقط:

> [!div class="mx-imgBorder"]
> ![تصفية الكشف عن قواعد الحد من سطح الهجوم على القواعد](images/asr-defender365-filter.png)

>[!Note]
>إذا كان لديك ترخيص Microsoft Microsoft 365 Security E5 أو A5 أو Windows E5 أو A5، يفتح الارتباط التالي تقارير Microsoft Defender 365 > تقليل مساحة [الهجوم > علامة](https://security.microsoft.com/asr?viewid=detections) التبويب الكشف عن المخاطر.

### <a name="configuration-tab"></a>علامة التبويب "تكوين"

القوائم – على أساس كل كمبيوتر – الحالة التجميعية لقواعد ASR: إيقاف، تدقيق، حظر.

> [!div class="mx-imgBorder"]
> ![علامة التبويب "تكوين" في قواعد الحد من سطح الهجوم](images/asr-defender365-configurations.png)

على علامة التبويب تكوينات، يمكنك التحقق – على أساس كل جهاز – من قواعد ASR التي يتم تمكينها، وفي أي وضع، عن طريق تحديد الجهاز الذي تريد مراجعة قواعد ASR له.

> [!div class="mx-imgBorder"]
> ![تمكين قواعد الحد من سطح الهجوم ووضعها](images/asr-defender365-configurations.settings.png)

يفتح **الارتباط بدء** استخدام إدارة نقاط النهاية من Microsoft، حيث يمكنك إنشاء نهج حماية نقطة نهاية ل ASR أو تعديله:

> [!div class="mx-imgBorder"]
> ![قواعد الحد من سطح الهجوم في MEM](images/asr-defender365-05b-mem1.png)

في Endpoint security | نظرة عامة، حدد **تقليل مساحة الهجوم**:

> [!div class="mx-imgBorder"]
> ![تقليل مساحة الهجوم في MEM](images/asr-defender365-05b-mem2.png)

أمان نقطة النهاية | يتم فتح جزء الحد من سطح الهجوم:

> [!div class="mx-imgBorder"]
> ![جزء Asr أمان نقطة النهاية](images/asr-defender365-05b-mem3.png)

>[!Note]
>إذا كان لديك ترخيص Microsoft Defender 365 E5 (أو Windows E5؟)، سيفتح هذا الارتباط Microsoft Defender 365 Reports > Attack surface > [علامة](https://security.microsoft.com/asr?viewid=configuration) التبويب تكوينات.

### <a name="add-exclusions"></a>إضافة استثناءات

توفر علامة التبويب هذه طريقة لتحديد الكيانات المكتشفة (على سبيل المثال، الإيجابيات الخاطئة) للاستبعاد. عند إضافة الاستثناءات، يوفر التقرير ملخصا عن التأثير المتوقع.

>[!Note]
> برنامج الحماية من الفيروسات من Microsoft Defender استثناءات AV من خلال قواعد ASR.  راجع [تكوين الاستثناءات والتحقق من صحتها استنادا إلى الملحق أو الاسم أو الموقع](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> ![أداة Asr الخاصة أمان نقطة النهاية](Images/asr-defender365-06d.png)

> [!Note]
>إذا كان لديك ترخيص Microsoft Defender 365 E5 (أو Windows E5؟)، فإن هذا الارتباط سيفتح Microsoft Defender 365 Reports > Attack surface [> علامة التبويب](https://security.microsoft.com/asr?viewid=exclusions) استثناءات.

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>استخدام PowerShell كطريقة بديلة لتمكين قواعد ASR

يمكنك استخدام PowerShell - كبديل ل MEM - لتمكين قواعد ASR في وضع التدقيق لعرض سجل التطبيقات التي كان سيتم حظرها إذا تم تمكين الميزة بالكامل. يمكنك أيضا الحصول على فكرة حول عدد المرات التي سيتم فيها إطلاق القواعد أثناء الاستخدام العادي.

لتمكين قاعدة تقليل مساحة الهجوم في وضع التدقيق، استخدم cmdlet التالي في PowerShell:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

أين `<rule ID>` تكون قيمة [GUID لقاعدة تقليل مساحة الهجوم](attack-surface-reduction-rules-reference.md).

لتمكين كل قواعد تقليل مساحة الهجوم المضافة في وضع التدقيق، استخدم cmdlet التالي في PowerShell:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> إذا كنت تريد التدقيق الكامل في كيفية عمل قواعد تقليل مساحة الهجوم في مؤسستك، ستحتاج إلى استخدام أداة إدارة لنشر هذا الإعداد على الأجهزة في الشبكة (الأجهزة).

يمكنك أيضا استخدام موفري خدمات تكوين إدارة أجهزة المحمول (MDM) أو Intune أو نهج المجموعة (CSPs) لتكوين الإعداد ونشره. تعرف على المزيد في مقالة قواعد الحد [من سطح](attack-surface-reduction.md) الهجوم الرئيسية.

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>استخدام Windows "مراجعة عارض الأحداث" كبديل لصفحة إعداد التقارير حول قواعد الحد من الهجمات في مدخل Microsoft 365 Defender الهجوم

لمراجعة التطبيقات التي كانت ستحظر، افتح "عارض الأحداث" وتصفية "لمعر 1121 الحدث" في سجل Microsoft-Windows-Windows Defender/التشغيلية. يسرد الجدول التالي كل أحداث حماية الشبكة.

"معرّف الحدث" | الوصف
-|-
 5007 | حدث عند تغيير الإعدادات
 1121 | حدث عند تشغيل قاعدة الحد من سطح الهجوم في وضع الحظر
 1122 | حدث عند تشغيل قاعدة تقليل مساحة الهجوم في وضع التدقيق

## <a name="additional-topics-in-this-deployment-collection"></a>مواضيع إضافية في مجموعة النشر هذه

[متطلبات نشر قواعد ASR](attack-surface-reduction-rules-deployment.md)

[الخطوة 1: تخطيط نشر قواعد ASR](attack-surface-reduction-rules-deployment-plan.md)

[الخطوة 3: تنفيذ قواعد ASR](attack-surface-reduction-rules-deployment-implement.md)

[الخطوة 4: تشغيل قواعد ASR](attack-surface-reduction-rules-deployment-operationalize.md)
