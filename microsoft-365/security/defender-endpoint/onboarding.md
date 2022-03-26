---
title: Onboard to the Microsoft Defender for Endpoint service
description: تعرف على كيفية وضع نقاط النهاية في خدمة Microsoft Defender for Endpoint
keywords: microsoft defender لنقطة النهاية، على اللوحة، النشر
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
- m365solution-endpointprotect
- m365solution-scenario
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 78f78208798635fb38381deaba3fa2f20e373bea
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63570187"
---
# <a name="onboard-to-the-microsoft-defender-for-endpoint-service"></a>Onboard to the Microsoft Defender for Endpoint service

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تعرف على المراحل المختلفة لنشر Microsoft Defender لنقطة النهاية وكيفية تكوين الإمكانات ضمن الحل.


هذه هي الخطوات التي يجب اتخاذها لنشر Defender لنقطة النهاية:

- الخطوة 1: نقاط نهاية الحافظة للخدمة
- الخطوة 2: تكوين القدرات

![رسم توضيحي لخطوات النشر](images/deployment-steps.png)



## <a name="step-1-onboard-endpoints-using-any-of-the-supported-management-tools"></a>الخطوة 1: نقاط نهاية الحافظة باستخدام أي من أدوات الإدارة المعتمدة

يوضح [موضوع نشر](deployment-strategy.md) الخطة الخطوات العامة التي تحتاج إلى اتخاذها لنشر Defender لنقطة النهاية.

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول عملية التوفر وتعرف على الأدوات والأساليب المتوفرة.


> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqr]

بعد تحديد البنية، ستحتاج إلى تحديد أسلوب النشر الذي يجب استخدامه. تؤثر أداة النشر التي تختارها على كيفية ا متن نقاط النهاية في الخدمة.

### <a name="onboarding-tool-options"></a>خيارات أدوات الboarding

يسرد الجدول التالي الأدوات المتوفرة استنادا إلى نقطة النهاية التي تحتاج إلى الاستناد إليها.

| نقطة النهاية     | خيارات الأدوات                       |
|--------------|------------------------------------------|
| **بالنسبة لنظام التشغيل**  |  [البرنامج النصي المحلي (ما يصل إلى 10 أجهزة)](configure-endpoints-script.md) <br>  [نهج المجموعة](configure-endpoints-gp.md) <br>  [إدارة نقاط النهاية من Microsoft/ Mobile Device Manager](configure-endpoints-mdm.md) <br> [Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md) <br> [برامج VDI النصية](configure-endpoints-vdi.md) <br> [التكامل مع Microsoft Defender for Cloud](azure-server-integration.md) |
| **macOS**    | [البرامج النصية المحلية](mac-install-manually.md) <br> [إدارة نقاط النهاية من Microsoft](mac-install-with-intune.md) <br> [JAMF Pro](mac-install-with-jamf.md) <br> [إدارة أجهزة المحمول](mac-install-with-other-mdm.md) |
| **Linux Server** | [برنامج نصي محلي](linux-install-manually.md) <br> [مهى](linux-install-with-puppet.md) <br> [غير قابل للطي](linux-install-with-ansible.md)|
| **iOS**      | [إدارة نقاط النهاية من Microsoft](ios-install.md)                                |
| **Android**  | [إدارة نقاط النهاية من Microsoft](android-intune.md)               | 


## <a name="step-2-configure-capabilities"></a>الخطوة 2: تكوين القدرات
بعد تهيئة نقاط النهاية، ستكوين القدرات. يسرد الجدول التالي المكونات التي يمكنك تكوينها. اختر المكونات التي تريد استخدامها وأزل المكونات التي لا تنطبق.

| الإمكانية | الوصف |
|-|-|
| [استجابة الكشف & نقطة النهاية (الكشف التلقائي والاستجابة على النقط النهائية)](overview-endpoint-detection-response.md) | توفر قدرات defender ل Endpoint الكشف عن تهديدات نقاط النهاية والرد عليها الكشف عن الهجمات المتقدمة التي تكون قريبة من الوقت الحقيقي و قابلة للتنفيذ. يمكن لمحللي الأمان إعطاء الأولوية للتنبيهات بفعالية، واكتساب الرؤية في النطاق الكامل للانتهاك، واتخاذ إجراءات الاستجابة للرد على التهديدات. |
| [إدارة & المخاطر (TVM)](next-gen-threat-and-vuln-mgt.md) | إدارة & المخاطر هي أحد مكونات Microsoft Defender ل Endpoint، وهي توفر لكل من مسؤولي الأمان وفرق عمليات الأمان قيمة فريدة، بما في ذلك: - في الوقت الحقيقي الكشف عن تهديدات نقاط النهاية والرد عليها (الكشف التلقائي والاستجابة على النقط النهائية ) نتائج تحليلات مرتبطة بنقاط الضعف في نقاط النهاية - سياق ثغرة الجهاز القيمة أثناء عمليات التحقيق في الأحداث - عمليات المعالجة المضمنة من خلال Microsoft Intune إدارة تكوين مركز النظام ل Microsoft.  |
| [حماية الجيل التالي (NGP)](microsoft-defender-antivirus-windows.md) | برنامج الحماية من الفيروسات من Microsoft Defender هو حل مضمن للحماية من البرامج الضارة يوفر حماية الجيل التالي لأجهزة سطح المكتب وأجهزة الكمبيوتر المحمولة الخوادم. برنامج الحماية من الفيروسات من Microsoft Defender ما يلي:<br> <br>-الحماية التي يتم توفيرها من السحابة للكشف الفوري عن التهديدات الجديدة والناشئة وحظرها. إلى جانب التعلم الآلي Graph الذكية، فإن الحماية التي يتم توفيرها من السحابة هي جزء من تقنيات الجيل التالي التي تعمل برنامج الحماية من الفيروسات من Microsoft Defender.<br> <br> - إجراء المسح الضوئي دائما باستخدام مراقبة متقدمة لملفات وسلوك عمليات وغيرها من الأمور التفحصية (المعروفة أيضا باسم "الحماية في الوقت الحقيقي").<br><br> - تحديثات الحماية المخصصة استنادا إلى التعلم الآلي وتحليل البيانات الكبيرة البشرية والآلية وأبحاث معمقة لمقاومة المخاطر. |
| [تقليل مساحة الهجوم (ASR)](overview-attack-surface-reduction.md) | تساعد إمكانات الحد من سطح الهجوم في Microsoft Defender for Endpoint على حماية الأجهزة والتطبيقات في المؤسسة من التهديدات الجديدة والناشئة. |
| [ميزة "& التلقائي" (AIR)](automated-investigations.md) | يستخدم Microsoft Defender ل Endpoint عمليات التحقق التلقائية لتقليل حجم التنبيهات التي تحتاج إلى التحقق بشكل فردي بشكل ملحوظ. تستفيد ميزة "الفحص التلقائي" من خوارزميات الفحص والعمليات المختلفة التي يستخدمها المحللون (مثل دفاتر التشغيل) لفحص التنبيهات واتخاذ إجراء المعالجة الفورية لحل الخروقات. هذا يقلل إلى حد كبير من حجم التنبيهات، مما يسمح لخبراء عمليات الأمان بالتركيز على تهديدات أكثر تعقيدا وغيرها من المبادرات ذات القيم العالية. |
| [خبراء المخاطر في Microsoft (MTE)](microsoft-threat-experts.md) | خبراء المخاطر في Microsoft هي خدمة صيد مدارة توفر مراكز عمليات الأمان (SOCs) مع عمليات مراقبة وتحليل على مستوى الخبراء لمساعدتها على ضمان عدم تفويت التهديدات الحرجة في بيئاتها الفريدة.      |

بعد تهيئة نقاط النهاية، ستكوين القدرات المختلفة مثل الكشف عن تهديدات نقاط النهاية والرد عليها وحماية الجيل التالي والحد من سطح الهجوم.

## <a name="example-deployments"></a>أمثلة على عمليات النشر

في دليل النشر هذا، سنرشدك خلال استخدام أدوات نشر لنقاط نهاية التهيئة وكيفية تكوين القدرات.

الأدوات في عمليات النشر على سبيل المثال هي:

- [الboarding باستخدام Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [الboarding باستخدام إدارة نقاط النهاية من Microsoft](onboarding-endpoint-manager.md)

باستخدام أدوات النشر المذكورة أعلاه، سيتم إرشادك بعد ذلك في تكوين قدرات Defender لنقطة النهاية التالية:

- الكشف عن نقطة النهاية وتكوين الاستجابة
- تكوين حماية الجيل التالي
- تكوين الحد من سطح الهجوم

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الboarding باستخدام Microsoft Endpoint Configuration Manager](onboarding-endpoint-configuration-manager.md)
- [الboarding باستخدام إدارة نقاط النهاية من Microsoft](onboarding-endpoint-manager.md)
- [أمان المستندات في Microsoft 365 E5](../office-365-security/safe-docs.md)
