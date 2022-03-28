---
title: تشغيل نشر قواعد الحد من الهجمات على سطح الهجوم (ASR)
description: يوفر إرشادات حول تشغيل نشر قواعد تقليل مساحة الهجوم.
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
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: 3229cd0a98714819009e7d50baab0872f3a67c43
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63575971"
---
# <a name="step-4-operationalize-asr-rules"></a>الخطوة 4: تشغيل قواعد ASR

بعد نشر قواعد الحد من الهجمات (ASR) بشكل كامل، من المهم أن تكون لديك عمليات في مكانها لمراقبة الأنشطة ذات الصلة ب ASR والاستجابة لها.

## <a name="managing-false-positives"></a>إدارة الإيجابيات الخاطئة

يمكن أن تحدث الإيجابيات/السلبيات الخاطئة مع أي حل للحماية من المخاطر. إن الإيجابيات الخاطئة هي الحالات التي يتم فيها الكشف عن كيان (مثل ملف أو عملية) وتعرف على أنه ضار، على الرغم من أن الكيان لا يشكل في الواقع خطرا. في المقابل، السلبية الخاطئة هي كيان لم يتم اكتشافه كخطر ولكنه ضار. لمزيد من المعلومات حول الإيجابيات الخاطئة والسلبيات الخاطئة، راجع: معالجة الإيجابيات [/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>متابعة التقارير

تشكل المراجعة المنتظمة والمتناسقة للتقارير أحد الجوانب الأساسية للمحافظة على نشر قواعد ASR وإبقاء على اطلاع على التهديدات الناشئة حديثا. يجب أن يكون لدى مؤسستك مراجعات مجدولة للأحداث الخاصة بقواعد ASR في تكاثف يبقى محدثا مع الأحداث التي يتم فيها التقارير بقواعد ASR. استنادا إلى حجم مؤسستك، قد تكون المراجعات مراقبة يومية أو كل ساعة أو مراقبة مستمرة.

## <a name="hunting"></a>الصيد

إحدى أكثر ميزات [Microsoft 365 Defender هي البحث](https://security.microsoft.com) المتقدم. إذا لم تكن ملما بالصيد المتقدم، فاطلع على: البحث بشكل استباقي عن [التهديدات باستخدام الصيد المتقدم](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender البحث المتقدم](images/asr-defender365-advanced-hunting2.png)

إن الصيد المتقدم هو أداة بحث عن تهديدات تستند إلى استعلام (لغة استعلام Kusto) تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات التي تم التقاطها (الخام) والتي يجمعها Microsoft Defender ATP Endpoint detection and Response (الكشف التلقائي والاستجابة على النقط النهائية) من جميع الأجهزة. من خلال البحث المتقدم، يمكنك فحص الأحداث بشكل استباقي لتحديد موقع المؤشرات والكيانات المثيرة للاهتمام. يسهل الوصول المرن إلى البيانات عمليات البحث غير المقيدة لكل من التهديدات المعروفة والمحتملة.

من خلال البحث المتقدم، من الممكن استخراج معلومات قواعد ASR وإنشاء التقارير والحصول على معلومات معمقة حول سياق حدث حظر أو تدقيق قاعدة ASR معينة.

 يمكنك الاستعلام عن أحداث قواعد ASR من الجدول DeviceEvents في قسم الصيد المتقدم Microsoft 365 Defender المدخل. على سبيل المثال، يمكن للاستعلام البسيط مثل الاستعلام أدناه الإبلاغ عن كل الأحداث التي تتضمن قواعد ASR كمصدر بيانات، خلال آخر 30 يوما، وتلخيصها حسب عدد الإجراءات، حيث سيكون في هذه الحالة اسم الرمز الفعلي لقاعدة ASR.

يتم كبح أحداث ASR التي تظهر في مدخل الصيد المتقدم للعمليات الفريدة التي تظهر كل ساعة. وقت حدث ASR هو المرة الأولى التي يتم فيها رؤية الحدث في غضون تلك الساعة.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender الأمر "استعلام بحث متقدم"](images/asr-defender365-advanced-hunting3.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender نتائج استعلام البحث المتقدم](images/asr-defender365-advanced-hunting4.png)

يوضح ما ذكر أعلاه أنه تم تسجيل 187 حدثا ل AsrLsasCredentialTheft:

- 102 للحظر
- 85 للتدقيق
- حدثان ل AsrOfficeChildProcess (1 للتدقيق و1 للحظر)
- 8 أحداث ل AsrPsexecWmiChildProcessAudited

إذا كنت تريد التركيز على قاعدة AsrOfficeChildProcess والحصول على تفاصيل حول الملفات والعمليات الفعلية المضرورة، فغير عامل التصفية ل ActionType واستبدل سطر التلخيص مع عرض الحقول المطلوب (في هذه الحالة هي DeviceName و FileName و FolderPath وغير ذلك).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender استعلام البحث المتقدم](images/asr-defender365-advanced-hunting4b.png)

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender نتائج استعلام البحث المتقدم](images/asr-defender365-advanced-hunting5b.png)

الفائدة الحقيقية للصيد المتقدم هي أنه يمكنك تشكيل الاستعلامات على نحو يعجبك. من خلال تشكيل الاستعلام، يمكنك رؤية القصة الدقيقة لما كان يحدث، بغض النظر عما إذا كنت تريد تثبيت شيء ما على جهاز فردي، أو كنت تريد استخراج نتائج تحليلات من بيئتك بأكملها.

لمزيد من المعلومات حول خيارات الصيد، راجع: إزالة الغموض عن قواعد تقليل مساحة [الهجوم - الجزء 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>مواضيع في مجموعة النشر هذه

[متطلبات نشر قواعد ASR](attack-surface-reduction-rules-deployment.md)

[الخطوة 1: تخطيط نشر قواعد ASR](attack-surface-reduction-rules-deployment-plan.md)

[الخطوة 2: اختبار قواعد ASR](attack-surface-reduction-rules-deployment-test.md)

[الخطوة 3: تنفيذ قواعد ASR](attack-surface-reduction-rules-deployment-implement.md)
