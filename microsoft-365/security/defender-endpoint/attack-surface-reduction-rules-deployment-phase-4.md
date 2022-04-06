---
title: مرحلة نشر قواعد ASR 4 - التشغيل
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
ms.openlocfilehash: b668519b84037000610fa3fe76ec5462b9657b3d
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/02/2022
ms.locfileid: "63583755"
---
# <a name="asr-rules-deployment-phase-4-operationalize"></a>مرحلة نشر قواعد ASR 4: التشغيل

بعد نشر قواعد ASR بشكل كامل، من المهم أن يكون لديك عمليات في مكانها لمراقبة الأنشطة ذات الصلة ب ASR والاستجابة لها.

## <a name="manage-false-positives"></a>إدارة الإيجابيات الخاطئة

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

[نظرة عامة حول نشر قواعد ASR](attack-surface-reduction-rules-deployment.md)

[المرحلة 1: الخطة](attack-surface-reduction-rules-deployment-phase-1.md)

[المرحلة 2: الاختبار](attack-surface-reduction-rules-deployment-phase-2.md)

[المرحلة 4: التشغيل](attack-surface-reduction-rules-deployment-phase-4.md)
