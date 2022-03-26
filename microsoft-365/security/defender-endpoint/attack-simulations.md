---
title: تجربة Microsoft Defender لنقطة النهاية من خلال هجمات محاكاة
description: يمكنك تشغيل عمليات محاكاة سيناريو الهجوم المتوفرة لتجربة كيف يمكن ل Microsoft Defender ل Endpoint الكشف عن الخروقات وتحريها والاستجابة لها.
keywords: اختبار، سيناريو، هجوم، محاكاة، محاكاة، diy، Microsoft Defender ل Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/20/2018
ms.technology: mde
ms.openlocfilehash: da02e1391b7624dc3e091ca1024a68c5756227a2
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/25/2021
ms.locfileid: "63573340"
---
# <a name="experience-microsoft-defender-for-endpoint-through-simulated-attacks"></a>تجربة Microsoft Defender لنقطة النهاية من خلال هجمات محاكاة 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-abovefoldlink)

> [!TIP]
>
> - تعرف على التحسينات الأخيرة في Microsoft Defender لنقطة النهاية: ما [الجديد في Defender for Endpoint؟](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/15/whats-new-in-windows-defender-atp/).
> - أظهر Defender ل Endpoint قدرات الكشف والبصريات الرائدة في تقييم MITRE الأخير. اقرأ: [Insights من تقييم MITRE ATT&المستند إلى CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

قد ترغب في تجربة Defender for Endpoint قبل أن تقوم بتكوين أكثر من بضع أجهزة للخدمة. للقيام بذلك، يمكنك تشغيل عمليات محاكاة هجوم خاضعة للتحكم على بعض أجهزة الاختبار. بعد تشغيل الهجمات المحاكاة، يمكنك مراجعة كيفية عرض Defender for Endpoint للنشاط الضار واستكشاف كيفية تمكينه للاستجابة الفعالة.

## <a name="before-you-begin"></a>قبل البدء

لتشغيل أي من عمليات المحاكاة المتوفرة، تحتاج إلى جهاز واحد [على الأقل تم تشغيله](onboard-configure.md).

اقرأ مستند المعاينة الذي تم توفيره مع كل سيناريو هجوم. يتضمن كل مستند نظام التشغيل ومتطلبات التطبيق بالإضافة إلى إرشادات مفصلة خاصة بسيناريوهات الهجمات.

## <a name="run-a-simulation"></a>تشغيل محاكاة

1. في **تقييم نقاط** \> **النهاية&** \> البرامج التعليمية & عمليات المحاكاة، حدد أي من سيناريوهات الهجوم المتوفرة التي تريد محاكاتها:
   - **السيناريو 1: المستند** ينسدل إلى الخلف - يحاكي تسليم مستند استدراج تم تصميمه من الناحية الاجتماعية. يتم تشغيل المستند لخلفية تم صياغةها بشكل خاص تمنح المهاجمين التحكم.
   - **السيناريو 2: برنامج PowerShell** النصي في هجوم بدون ملفات - يحاكي هجوم بدون ملفات يعتمد على PowerShell، مع عرض تقليل مساحة الهجوم واكتشاف تعلم الجهاز لنشاط الذاكرة الضارة.
   - **السيناريو 3: الاستجابة** التلقائية للحوادث - يقوم بتشغيل التحقيق التلقائي، الذي يتعقب تلقائيا عمليات خرق المحتوى ويرد عليها لمقياس سعة الاستجابة للحوادث.

2. قم بتنزيل مستند المعاينة المناظر الذي تم توفيره مع السيناريو المحدد وقراءته.

3. قم بتنزيل ملف المحاكاة أو انسخ برنامج المحاكاة النصي من خلال الانتقال إلى **تقييم & البرامج** \> التعليمية & **المحاكاة**. يمكنك اختيار تنزيل الملف أو البرنامج النصي على جهاز الاختبار ولكنه ليس إلزاميا.

4. تشغيل ملف المحاكاة أو البرنامج النصي على جهاز الاختبار كما هو مرشاد في مستند المعاينة.

> [!NOTE]
> تحاكي ملفات المحاكاة أو البرامج النصية نشاط الهجوم ولكنها في الواقع غير ضارة ولن تؤذي جهاز الاختبار أو تؤذيه.
>
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-attacksimulations-belowfoldlink)

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الأجهزة المجهزة](onboard-configure.md)
- [أجهزة Windows](configure-endpoints.md)
