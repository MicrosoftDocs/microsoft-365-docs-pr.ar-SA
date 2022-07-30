---
title: أجهزة التجهيز وتكوين Microsoft Defender لنقطة النهاية
description: إلحاق Windows 10 الأجهزة والخوادم والأجهزة غير التي تعمل بنظام Windows وتعلم كيفية تشغيل اختبار الكشف.
keywords: الإلحاق، Microsoft Defender لنقطة النهاية الإلحاق، sccm، نهج المجموعة، mdm، البرنامج النصي المحلي، اختبار الكشف
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
ms.openlocfilehash: f52dd982c9a418af9184389e8e83e6077326ee80
ms.sourcegitcommit: e4882e3c66166ea7b834ad2e8fafeab42293e07d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67099981"
---
# <a name="onboard-devices-and-configure-microsoft-defender-for-endpoint-capabilities"></a>أجهزة التجهيز وتكوين Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-onboardconfigure-abovefoldlink)

نشر Microsoft Defender لنقطة النهاية عملية من خطوتين.

- إلحاق الأجهزة للخدمة
- تكوين قدرات الخدمة

:::image type="content" source="images/deployment-steps.png" alt-text="عملية الإلحاق والتكوين" lightbox="images/deployment-steps.png":::

## <a name="role-based-access-control"></a>عنصر تحكم الوصول المستند إلى الدور

نوصي باستخدام إدارة الهويات المتميزة لإدارة أدوارك لتوفير تدقيق إضافي والتحكم ومراجعة صلاحية الوصول للمستخدمين الذين لديهم أذونات الدليل.

يدعم Defender لنقطة النهاية طريقتين لإدارة الأذونات:

- **إدارة الأذونات الأساسية**: تعيين الأذونات إما للوصول الكامل أو للقراءة فقط. يمكن للمستخدمين الذين لديهم أدوار مسؤول عمومي أو مسؤول أمان في Azure Active Directory (Azure AD) الوصول الكامل. دور قارئ الأمان لديه حق الوصول للقراءة فقط ولا يمنح حق الوصول لعرض مخزون الأجهزة/الأجهزة.

- **التحكم في الوصول استنادا إلى الدور (RBAC):** تعيين الأذونات الدقيقة عن طريق تحديد الأدوار، وتعيين Azure AD مجموعات المستخدمين للأدوار، ومنح مجموعات المستخدمين حق الوصول إلى مجموعات الأجهزة. لمزيد من المعلومات. راجع [إدارة الوصول إلى المدخل باستخدام التحكم في الوصول استنادا إلى الدور](rbac.md).

نوصي بالاستفادة من التحكم في الوصول استنادا إلى الدور للتأكد من أن المستخدمين الذين لديهم مبررات عمل فقط يمكنهم الوصول إلى Defender لنقطة النهاية.

## <a name="onboard-devices-to-the-service"></a>إلحاق الأجهزة للخدمة
ستحتاج إلى الانتقال إلى قسم الإلحاق في مدخل Defender لنقطة النهاية لإلحاق أي من الأجهزة المدعومة. اعتمادا على الجهاز، سيتم إرشادك بالخطوات المناسبة وتوفير خيارات أداة الإدارة والتوزيع المناسبة للجهاز. 

لإلحاق الأجهزة للخدمة:

- تحقق من أن الجهاز يفي [بالحد الأدنى من المتطلبات](minimum-requirements.md)
- اعتمادا على الجهاز، اتبع خطوات التكوين المتوفرة في قسم الإلحاق في مدخل Defender لنقطة النهاية
- استخدام أداة الإدارة المناسبة وطريقة النشر لأجهزتك
- تشغيل اختبار الكشف للتحقق من أن الأجهزة تم إلحاقها بشكل صحيح وإعداد التقارير إلى الخدمة

توفر هذه المقالة معلومات حول أساليب الإلحاق المطبقة على إصدارات Windows Client وServer.

## <a name="onboarding-and-configuration-tool-options"></a>خيارات أداة الإعداد والتكوين
يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى إلحاقها.

| نقطه النهايه     | خيارات الأدوات                       |
|--------------|------------------------------------------|
| **عميل Windows**  |     [إدارة الجهاز الجوال / Microsoft Intune](configure-endpoints-mdm.md) <br> [نهج المجموعة](configure-endpoints-gp.md) <br> [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>[البرامج النصية ل VDI](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **Windows Server**  | [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [البرامج النصية ل VDI](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)  |
| **macOS**    | [البرامج النصية المحلية](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [إدارة الجهاز الجوال](mac-install-with-other-mdm.md) |
| **Linux Server** | [البرنامج النصي المحلي](linux-install-manually.md) <br> [دميه](linux-install-with-puppet.md) <br> [Ansible](linux-install-with-ansible.md) <br> [التكامل مع Microsoft Defender for Cloud](configure-server-endpoints.md#integration-with-microsoft-defender-for-cloud)     |
| **دائره الرقابه الداخليه**      | [إدارة نقاط النهاية من Microsoft](ios-install.md)           |
| **الروبوت**  | [إدارة نقاط النهاية من Microsoft](android-intune.md)            | 


> [!NOTE]
> بالنسبة للأجهزة التي لا تتم إدارتها بواسطة إدارة نقاط النهاية Microsoft (إما Microsoft Intune أو نقطة نهاية Microsoft Configuration Manager)، يمكنك استخدام إدارة الأمان Microsoft Defender لنقطة النهاية  لتلقي تكوينات الأمان ل Microsoft Defender مباشرة من إدارة نقاط النهاية.

يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى إلحاقها.

## <a name="configure-capabilities-of-the-service"></a>تكوين قدرات الخدمة
تمكن أجهزة الإلحاق بشكل فعال إمكانية الكشف عن نقطة النهاية والاستجابة Microsoft Defender لنقطة النهاية.

بعد إلحاق الأجهزة، ستحتاج بعد ذلك إلى تكوين القدرات الأخرى للخدمة. يسرد الجدول التالي القدرات التي يمكنك تكوينها للحصول على أفضل حماية للبيئة الخاصة بك.

| تمكن | الوصف |
|-|-|
| [تكوين إدارة الثغرات الأمنية & المخاطر (TVM)](tvm-prerequisites.md) | تعد إدارة الثغرات الأمنية & المخاطر أحد مكونات Microsoft Defender لنقطة النهاية، وتوفر لمسؤولي الأمان وفرق عمليات الأمان قيمة فريدة، بما في ذلك: <br><br> - نتائج تحليلات الكشف عن نقاط النهاية والاستجابة لها (EDR) في الوقت الحقيقي المرتبطة بنقاط الضعف في نقطة النهاية. <br><br> - سياق الثغرة الأمنية للجهاز لا يقدر بثمن في أثناء التحقيقات في الحوادث. <br><br> - عمليات المعالجة المضمنة من خلال Microsoft Intune وMicrosoft System Center Configuration Manager.  |
| [تكوين حماية الجيل التالي (NGP)](configure-microsoft-defender-antivirus-features.md) | برنامج الحماية من الفيروسات من Microsoft Defender هو حل مضمن لمكافحة البرامج الضارة يوفر حماية الجيل التالي لأجهزة سطح المكتب وأجهزة الكمبيوتر المحمولة والخوادم. يتضمن برنامج الحماية من الفيروسات من Microsoft Defender ما يلي:<br> <br>-الحماية المقدمة من السحابة للكشف شبه الفوري ومنع التهديدات الجديدة والناشئة. جنبا إلى جنب مع التعلم الآلي و Intelligent Security Graph، تعد الحماية المقدمة من السحابة جزءا من تقنيات الجيل التالي التي تدعم برنامج الحماية من الفيروسات من Microsoft Defender.<br> <br> - المسح الضوئي دائما باستخدام مراقبة متقدمة لسلوك الملفات والعمليات وغيرها من الأساليب الاستباقية (المعروفة أيضا باسم "الحماية في الوقت الحقيقي").<br><br> - تحديثات الحماية المخصصة المستندة إلى التعلم الآلي وتحليل البيانات الضخمة البشرية والآلية والبحث المتعمق في مقاومة التهديدات. |
| [تكوين تقليل الأجزاء المعرضة للهجوم (ASR)](overview-attack-surface-reduction.md) | تساعد قدرات تقليل الأجزاء المعرضة للهجوم في Microsoft Defender لنقطة النهاية على حماية الأجهزة والتطبيقات في المؤسسة من التهديدات الجديدة والناشئة. |
| [تكوين قدرات المعالجة & التحقيق التلقائي (AIR)](configure-automated-investigations-remediation.md) | تستخدم Microsoft Defender لنقطة النهاية التحقيقات التلقائية لتقليل حجم التنبيهات التي تحتاج إلى التحقيق بشكل فردي بشكل كبير. تستفيد ميزة التحقيق التلقائي من خوارزميات الفحص المختلفة والعمليات التي يستخدمها المحللون (مثل أدلة المبادئ) لفحص التنبيهات واتخاذ إجراءات المعالجة الفورية لحل الخروقات. وهذا يقلل بشكل كبير من حجم التنبيه، ما يسمح لخبراء عمليات الأمان بالتركيز على التهديدات الأكثر تعقيدا والمبادرات الأخرى عالية القيمة. |
| [تكوين قدرات خبراء المخاطر في Microsoft (MTE)](configure-microsoft-threat-experts.md) | خبراء المخاطر في Microsoft هي خدمة تتبع مدارة توفر لمراكز عمليات الأمان (SOCs) مراقبة وتحليل على مستوى الخبراء لمساعدتهم على ضمان عدم تفويت التهديدات الحرجة في بيئاتهم الفريدة.      |


## <a name="supported-capabilities-for-windows-devices"></a>القدرات المدعومة لأجهزة Windows

|نظام التشغيل  |Windows 10 & 11  |Windows Server 2012 R2 <sup>[[1](#fn1)]<sup></sup>  |Windows Server 2016<sup>[[1](#fn1)]<sup></sup>   |Windows Server 2019 & 2022|Windows Server 1803+|
|---------|---------|---------|---------|---------|---------|
|**منع**    |         |         |         |         |         |
|قواعد تقليل الأجزاء المعرضة للهجوم     |    Y     |   Y      |    Y     |    Y     |    Y     |
|التحكم في الجهاز     |     Y    |    N     |    N     |    N     |    N     |  
|جدار حمايه     |      Y   |    Y     |     Y    |    Y    |    Y   |
|حماية الشبكة     |      Y   |    Y     |     Y    |    Y    |    Y   |
|حماية الجيل التالي     |      Y   |    Y     |     Y    |    Y    |    Y   |
|الحماية من العبث بالبيانات     |        Y   |    Y     |     Y    |    Y    |    Y   |
|حماية الويب     |       Y   |    Y     |     Y    |    Y    |    Y   |
|||||||
|**الكشف**     |         |         |         |||
|التتبع المتقدم     |      Y   |    Y     |     Y    |    Y    |    Y   |
|مؤشرات الملفات المخصصة     |      Y   |    Y     |     Y    |    Y    |    Y   |
|مؤشرات الشبكة المخصصة     |      Y   |    Y     |     Y    |    Y    |    Y   |
|وضع حظر EDR & الخامل     |      Y   |    Y     |     Y    |    Y    |    Y   |
|أداة استشعار الكشف عن المعنى     |      Y   |    Y     |     Y    |    Y    |    Y   |
|نقطة النهاية & اكتشاف جهاز الشبكة     |      Y   |    N     |     N    |    N    |    N   |
|||||||
|**استجابه**     |         |         |         |||
|استجابة & التحقيق التلقائي (AIR)    |      Y   |    Y     |     Y    |    Y    |    Y   |
|قدرات استجابة الجهاز: العزل، وجمع حزمة التحقيق، وتشغيل فحص AV     |      Y   |    Y     |     Y    |    Y    |    Y   |
|قدرات استجابة الملف: جمع الملفات والتحليل العميق وملف الحظر وعمليات الإيقاف والعزل     |      Y   |    Y     |     Y    |    Y    |    Y   |
|الاستجابة المباشرة    |      Y   |    Y     |     Y    |    Y    |    Y   |

(<a id="fn1">1</a>) يشير إلى الحل الحديث الموحد ل Windows Server 2012 R2 و2016. لمزيد من المعلومات، راجع [إلحاق خوادم Windows بخدمة Defender لنقطة النهاية](configure-server-endpoints.md).

>[!NOTE]
>يتضمن Windows 7 و8.1 وWindows Server 2008 R2 دعما لأداة استشعار EDR وAV باستخدام System Center Endpoint Protection (SCEP).
