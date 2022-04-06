---
title: الأجهزة المجهزة وتكوين Microsoft Defender لنقطة النهاية
description: يمكنك Windows 10 الأجهزة أو الخوادم أو الأجهزة غير Windows وتعرف على كيفية تشغيل اختبار الكشف.
keywords: التكهين، Microsoft Defender لنقطة النهاية، sccm، نهج المجموعة، mdm، البرنامج النصي المحلي، اختبار الكشف
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
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 350f5675d1426c354f1e2ac848d3a9d14f1ecc76
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469658"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>الأجهزة المجهزة وتكوين Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

نشر Microsoft Defender لنقطة النهاية عملية من خطوتين.

- الأجهزة المجهزة للخدمة
- تكوين إمكانات الخدمة

:::image type="content" source="images/deployment-steps.png" alt-text="عملية التهيئة والتهيئة" lightbox="images/deployment-steps.png":::

## <a name="onboard-devices-to-the-service"></a>الأجهزة المجهزة للخدمة
ستحتاج إلى الانتقال إلى قسم التكوين في مدخل Defender for Endpoint لترك أي من الأجهزة المعتمدة. استنادا إلى الجهاز، سيتم إرشادك بخطوات مناسبة والخيارات المتوفرة لأداة الإدارة والنشر المناسبة للجهاز. 

بشكل عام، للأجهزة المجهزة للخدمة:

- التحقق من أن الجهاز يفي [بالحد الأدنى من المتطلبات](minimum-requirements.md)
- استنادا إلى الجهاز، اتبع خطوات التكوين المتوفرة في قسم التهيئة في مدخل Defender for Endpoint
- استخدام أداة الإدارة المناسبة وطريقة النشر لأجهزتك
- تشغيل اختبار الكشف للتحقق من أن الأجهزة تم تشغيلها بشكل صحيح وإبلاغ الخدمة



## <a name="onboarding-and-configuration-tool-options"></a>خيارات أدوات التكوين والتكوين
يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى الاستناد إليها.

| نقطة النهاية     | خيارات الأدوات                       |
|--------------|------------------------------------------|
| **بالنسبة لنظام التشغيل**  |  [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة نقاط النهاية من Microsoft/Mobile إدارة الأجهزة](configure-endpoints-mdm.md) <br>   [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [برامج VDI النصية](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-azure-defender)  |
| **macOS**    | [البرامج النصية المحلية](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [الأجهزة إدارة الجهاز](mac-install-with-other-mdm.md) |
| **Linux Server** | [برنامج نصي محلي](linux-install-manually.md) <br> [مهى](linux-install-with-puppet.md) <br> [غير قابل للطي](linux-install-with-ansible.md)|
| **iOS**      | [إدارة نقاط النهاية من Microsoft](ios-install.md)               |
| **Android**  | [إدارة نقاط النهاية من Microsoft](android-intune.md)            | 


يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى الاستناد إليها.

## <a name="configure-capabilities-of-the-service"></a>تكوين إمكانات الخدمة
تعمل أجهزة التكوين على تمكين إمكانية الكشف عن تهديدات نقاط النهاية والرد عليها Micorosft Defender ل Endpoint بفعالية.

بعد تهيئة الأجهزة، ستحتاج بعد ذلك إلى تكوين القدرات الأخرى للخدمة. يسرد الجدول التالي القدرات التي يمكنك تكوينها للحصول على أفضل حماية بيئة.

| الإمكانية | الوصف |
|-|-|
| [تكوين إدارة & الضعف (TVM)](tvm-prerequisites.md) | إدارة & المخاطر هي أحد مكونات Microsoft Defender لنقطة النهاية، وتوفر لكل من مسؤولي الأمان وفرق عمليات الأمان قيمة فريدة، بما في ذلك: <br><br> - تحليلات الكشف عن تهديدات نقاط النهاية والرد عليها الوقت الكشف التلقائي والاستجابة على النقط النهائية المرتبطة بنقاط الضعف في نقاط النهاية. <br><br> - سياق ثغرة الجهاز التي لا تقدر بثمن أثناء عمليات التحقيق في الأحداث. <br><br> - عمليات الإصلاح المضمنة من خلال Microsoft Intune و Microsoft System Center Configuration Manager.  |
| [تكوين حماية الجيل التالي (NGP)](configure-microsoft-defender-antivirus-features.md) | برنامج الحماية من الفيروسات من Microsoft Defender هو حل مضمن للحماية من البرامج الضارة يوفر حماية الجيل التالي لأجهزة سطح المكتب وأجهزة الكمبيوتر المحمولة الخوادم. برنامج الحماية من الفيروسات من Microsoft Defender ما يلي:<br> <br>-الحماية التي يتم توفيرها من السحابة للكشف الفوري عن التهديدات الجديدة والناشئة وحظرها. إلى جانب التعلم الآلي Graph الذكية، فإن الحماية التي يتم توفيرها من السحابة هي جزء من تقنيات الجيل التالي التي تعمل برنامج الحماية من الفيروسات من Microsoft Defender.<br> <br> - إجراء المسح الضوئي دائما باستخدام مراقبة متقدمة لملفات وسلوك عمليات وغيرها من الأمور التفحصية (المعروفة أيضا باسم "الحماية في الوقت الحقيقي").<br><br> - تحديثات الحماية المخصصة استنادا إلى التعلم الآلي وتحليل البيانات الكبيرة البشرية والآلية وأبحاث معمقة لمقاومة المخاطر. |
| [تكوين تقليل مساحة الهجوم (ASR)](overview-attack-surface-reduction.md) | إمكانات تقليل مساحة الهجوم في Microsoft Defender لنقطة النهاية للمساعدة في حماية الأجهزة والتطبيقات في المؤسسة من التهديدات الجديدة والناشئة. |
| [تكوين قدرات & "المعالجة التلقائية" (AIR)](configure-automated-investigations-remediation.md) | Microsoft Defender لنقطة النهاية عمليات التحقق التلقائية لتقليل حجم التنبيهات التي تحتاج إلى التحقق بشكل فردي بشكل ملحوظ. تستفيد ميزة "الفحص التلقائي" من خوارزميات الفحص والعمليات المختلفة التي يستخدمها المحللون (مثل دفاتر التشغيل) لفحص التنبيهات واتخاذ إجراء المعالجة الفورية لحل الخروقات. هذا يقلل إلى حد كبير من حجم التنبيهات، مما يسمح لخبراء عمليات الأمان بالتركيز على تهديدات أكثر تعقيدا وغيرها من المبادرات ذات القيم العالية. |
| [تكوين خبراء المخاطر في Microsoft (MTE)](configure-microsoft-threat-experts.md) | خبراء المخاطر في Microsoft هي خدمة صيد مدارة توفر مراكز عمليات الأمان (SOCs) مع عمليات مراقبة وتحليل على مستوى الخبراء لمساعدتها على ضمان عدم تفويت التهديدات الحرجة في بيئاتها الفريدة.      |


## <a name="supported-capabilities-for-windows-devices"></a>الإمكانات المعتمدة Windows الأجهزة

|نظام التشغيل  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |Windows Server 2016<sup>[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**منع**    |         |         |         |         |         |
|قواعد تقليل مساحة الهجوم     |    Y     |   Y      |    Y     |    Y     |    Y     |
|التحكم في الجهاز     |     Y    |    N     |    N     |    N     |    N     |  
|جدار الحماية     |      Y   |    Y     |     Y    |    Y    |    Y   |
|حماية الشبكة     |      Y   |    Y     |     Y    |    Y    |    Y   |
|حماية الجيل التالي     |      Y   |    Y     |     Y    |    Y    |    Y   |
|الحماية من العبث     |        Y   |    Y     |     Y    |    Y    |    Y   |
|حماية ويب     |       Y   |    Y     |     Y    |    Y    |    Y   |
|||||||
|**الكشف**     |         |         |         |||
|الصيد المتقدم     |      Y   |    Y     |     Y    |    Y    |    Y   |
|مؤشرات ملفات مخصصة     |      Y   |    Y     |     Y    |    Y    |    Y   |
|مؤشرات الشبكة المخصصة     |      Y   |    Y     |     Y    |    Y    |    Y   |
|الكشف التلقائي والاستجابة على النقط النهائية حظر & السلبي     |      Y   |    Y     |     Y    |    Y    |    Y   |
|مستشعر الكشف عن استشعار     |      Y   |    Y     |     Y    |    Y    |    Y   |
|نقطة النهاية & جهاز الشبكة     |      Y   |    N     |     N    |    N    |    N   |
|||||||
|**الاستجابة**     |         |         |         |||
|الاستجابة التلقائية & (AIR)    |      Y   |    Y     |     Y    |    Y    |    Y   |
|قدرات استجابة الجهاز: عزل حزمة التحقيق، تجميعها، تشغيل فحص AV     |      Y   |    Y     |     Y    |    Y    |    Y   |
|قدرات استجابة الملفات: تجميع الملفات والتحليل العميق وحظر الملفات وعمليات إيقاف الملفات والحجر الصحي     |      Y   |    Y     |     Y    |    Y    |    Y   |
|الاستجابة المباشرة    |      Y   |    Y     |     Y    |    Y    |    Y   |

(<a id="fn1">1</a>) يشير إلى الحل الحديث الموحد Windows Server 2012 R2 و2016. لمزيد من المعلومات، راجع [Windows إلى خدمة Defender for Endpoint](configure-server-endpoints.md).

>[!NOTE]
>Windows 7 و8.1 Windows Server 2008 R2 دعم مستشعر الكشف التلقائي والاستجابة على النقط النهائية وAV باستخدام System Center Endpoint Protection (SCEP).
