---
title: تشغيل قواعد تقليل الأجزاء المعرضة للهجوم (ASR)
description: يوفر إرشادات لتفعيل نشر قواعد تقليل الأجزاء المعرضة للهجوم.
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
ms.date: 1/18/2022
ms.openlocfilehash: 708d929376c029ba5ce448c93fd6c455a78ebec8
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602867"
---
# <a name="operationalize-attack-surface-reduction-asr-rules"></a>تشغيل قواعد تقليل الأجزاء المعرضة للهجوم (ASR)

بعد نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR) بشكل كامل، من الضروري أن يكون لديك عمليات قيد التشغيل لمراقبة الأنشطة المتعلقة ب ASR والاستجابة لها.

## <a name="managing-false-positives"></a>إدارة الإيجابيات الخاطئة

يمكن أن تحدث الإيجابيات/السلبيات الخاطئة مع أي حل للحماية من التهديدات. النتائج الإيجابية الخاطئة هي الحالات التي يتم فيها الكشف عن كيان (مثل ملف أو عملية) وتحديده على أنه ضار، على الرغم من أن الكيان ليس في الواقع تهديدا. وعلى النقيض من ذلك، فإن السالب الخاطئ هو كيان لم يتم اكتشافه كتهديد ولكنه ضار. لمزيد من المعلومات حول الإيجابيات الخاطئة والسلبيات الخاطئة، راجع: [معالجة الإيجابيات/السلبيات الخاطئة في Microsoft Defender لنقطة النهاية](defender-endpoint-false-positives-negatives.md)

## <a name="keeping-up-with-reports"></a>مواكبة التقارير

تعد المراجعة المتناسقة والمنتظمة للتقارير جانبا أساسيا للحفاظ على نشر قواعد ASR الخاصة بك ومواكبة التهديدات الناشئة حديثا. يجب أن يكون لدى مؤسستك مراجعات مجدولة لأحداث قواعد ASR على إيقاع سيبقى محدثا مع الأحداث المبلغ عنها لقواعد ASR. اعتمادا على حجم مؤسستك، قد تكون المراجعات مراقبة يومية أو كل ساعة أو مستمرة.

## <a name="hunting"></a>الصيد

واحدة من أقوى ميزات [Microsoft 365 Defender](https://security.microsoft.com) هي التتبع المتقدم. إذا لم تكن على دراية بالتتبع المتقدم، فراجع: [البحث بشكل استباقي عن التهديدات باستخدام التتبع المتقدم](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting2.png" alt-text="صفحة Advanced Hunting في مدخل Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting2.png":::

التتبع المتقدم هو أداة تتبع المخاطر المستندة إلى الاستعلام (Kusto Query Language) التي تتيح لك استكشاف ما يصل إلى 30 يوما من البيانات الملتقطة (البسيطة) التي يجمعها Microsoft Defender ATP Endpoint Detection and Response (EDR) من جميع أجهزتك. من خلال التتبع المتقدم، يمكنك فحص الأحداث بشكل استباقي من أجل تحديد المؤشرات والكيانات المثيرة للاهتمام. يسهل الوصول المرن إلى البيانات التتبع غير المقيد لكل من التهديدات المعروفة والمحتملة.

من خلال التتبع المتقدم، من الممكن استخراج معلومات قواعد ASR وإنشاء التقارير والحصول على معلومات متعمقة حول سياق تدقيق قاعدة ASR معين أو حدث حظر.

 يمكنك الاستعلام عن أحداث قواعد ASR من جدول DeviceEvents في قسم التتبع المتقدم من مدخل Microsoft 365 Defender. على سبيل المثال، يمكن لاستعلام بسيط مثل الاستعلام أدناه الإبلاغ عن جميع الأحداث التي تحتوي على قواعد ASR كمصدر بيانات، لآخر 30 يوما، وسيقوم بتلخيصها حسب عدد ActionType، وأنه في هذه الحالة سيكون الاسم الرمزي الفعلي لقاعدة ASR.

يتم تقييد أحداث ASR الموضحة في مدخل التتبع المتقدم للعمليات الفريدة التي تتم مشاهدتها كل ساعة. وقت حدث ASR هو المرة الأولى التي يتم فيها رؤية الحدث في غضون تلك الساعة.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting3.png" alt-text="سطر أوامر استعلام التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting3.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4.png" alt-text="نتائج استعلام التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4.png":::

يوضح ما سبق أنه تم تسجيل 187 حدثا ل AsrLsassCredentialTheft:

- 102 for Blocked
- 85 للتدقيق
- حدثان ل AsrOfficeChildProcess (1 للتدقيق و1 للكتلة)
- 8 أحداث ل AsrPsexecWmiChildProcessAudited

إذا كنت تريد التركيز على قاعدة AsrOfficeChildProcess والحصول على تفاصيل حول الملفات والعمليات الفعلية المتضمنة، فقم بتغيير عامل التصفية ل ActionType واستبدل سطر التلخيص بإسقاط للحقول المطلوبة (في هذه الحالة هي DeviceName و FileName و FolderPath وما إلى ذلك).

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting4b.png" alt-text="مثال يركز على استعلام التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting4b.png":::

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-advanced-hunting5b.png" alt-text="نتائج استعلام التتبع المتقدم المركز عليه في مدخل Microsoft 365 Defender" lightbox="images/asr-defender365-advanced-hunting5b.png":::

الفائدة الحقيقية من التتبع المتقدم هو أنه يمكنك تشكيل الاستعلامات بما يرضيك. من خلال تشكيل الاستعلام الخاص بك، يمكنك رؤية القصة الدقيقة لما كان يحدث، بغض النظر عما إذا كنت تريد تحديد شيء ما على جهاز فردي، أو تريد استخراج رؤى من بيئتك بأكملها.

لمزيد من المعلومات حول خيارات التتبع، راجع: [إزالة الغموض عن قواعد تقليل الأجزاء المعرضة للهجوم - الجزء 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968).

## <a name="topics-in-this-deployment-collection"></a>مواضيع في مجموعة النشر هذه

[نظرة عامة على دليل نشر قواعد الحد من سطح الهجوم (ASR)](attack-surface-reduction-rules-deployment.md)

[تخطيط نشر قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[اختبار قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-test.md)

[تمكين قواعد تقليل الأجزاء المعرضة للهجوم (ASR)](attack-surface-reduction-rules-deployment-implement.md)

[مرجع قواعد تقليل الأجزاء المعرضة للهجوم](attack-surface-reduction-rules-reference.md)
