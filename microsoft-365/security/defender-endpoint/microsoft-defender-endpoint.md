---
title: Microsoft Defender for Endpoint
description: Microsoft Defender لنقطة النهاية هو نظام أساسي لأمان نقطة نهاية المؤسسة يساعد على الدفاع ضد التهديدات المستمرة المتقدمة.
keywords: مقدمة إلى Microsoft Defender لنقطة النهاية، مقدمة إلى Microsoft Defender لنقطة النهاية، والأمن السيبراني، والتهديدات المستمرة المتقدمة، وأمان المؤسسة، والمستشعر السلوكي للجهاز، وأمان السحابة، والتحليلات، والتحليل الذكي للمخاطر، وتقليل الأجزاء المعرضة للهجوم، وحماية الجيل التالي، والتحقيق الآلي والمعالجة، وخبراء التهديد من Microsoft، والنتيجة الآمنة، والتتبع المتقدم، Microsoft 365 Defender، وتتبع التهديدات الإلكترونية
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: high
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.custom: intro-overview
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c9fe313994e7468004e17df05b1ec4d7c3cf7a6b
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65367926"
---
# <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender لنقطة النهاية هو نظام أساسي لأمان نقطة نهاية المؤسسة مصمم لمساعدة شبكات المؤسسة على منع التهديدات المتقدمة واكتشافها والتحقيق فيها والاستجابة لها.

> [!TIP]
> يتوفر Microsoft Defender لنقطة النهاية في خطتين، Defender لنقطة النهاية الخطة 1 والخطة 2. تتوفر الآن وظيفة إدارة الثغرات الأمنية في Microsoft Defender إضافية جديدة للخطة 2.
>
> لمزيد من المعلومات حول الميزات والقدرات المضمنة في كل خطة، بما في ذلك الوظيفة الإضافية الجديدة لإدارة الثغرات الأمنية في Defender، راجع [مقارنة خطط Microsoft Defender لنقطة النهاية](defender-endpoint-plan-1-2.md).

<p><p>

شاهد الفيديو التالي لمعرفة المزيد حول Defender لنقطة النهاية:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

يستخدم Defender لنقطة النهاية المجموعة التالية من التكنولوجيا المضمنة في Windows 10 وخدمة السحابة القوية من Microsoft:

- **أجهزة الاستشعار السلوكية لنقطة النهاية**: مضمنة في Windows 10، تجمع أجهزة الاستشعار هذه الإشارات السلوكية وتعالجها من نظام التشغيل وترسل بيانات المستشعر هذه إلى مثيل السحابة الخاص والمعزول Microsoft Defender لنقطة النهاية.

- **تحليلات أمان السحابة**: تتم ترجمة الاستفادة من البيانات الضخمة وتعلم الأجهزة وبصريات Microsoft الفريدة عبر النظام البنائي Windows والمنتجات السحابية للمؤسسات (مثل Office 365) والأصول عبر الإنترنت والإشارات السلوكية إلى رؤى واكتشافات واستجابات موصى بها للتهديدات المتقدمة.

- **التحليل الذكي للمخاطر**: تم إنشاؤه بواسطة متتبعي Microsoft، وفرق الأمان، وزيادة التحليل الذكي للمخاطر الذي يوفره الشركاء، ويمكن التحليل الذكي للمخاطر Defender لنقطة النهاية من تحديد أدوات المهاجم وتقنياته وإجراءاته، وإنشاء تنبيهات عند ملاحظتها في بيانات المستشعر المجمعة.

<center><h2>Microsoft Defender لنقطة النهاية</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/logo-mdvm.png" alt="Vulnerability Management"> <br><b> Core Defender Vulnerability Management</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>تقليل الأجزاء المعرضة للهجوم</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>حماية الجيل التالي</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>الكشف عن نقطة النهاية والاستجابة لها</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>التحقيق التلقائي والمعالجة</b></a></center></td>
<td><center><a href="#mte"><img src="images/mte-icon.png" alt="Microsoft Threat Experts"><br> <b>خبراء المخاطر في Microsoft</b></a></center></td>
</tr>
<tr>
<td colspan="7">
<a href="#apis"><center><b>التكوين والإدارة المركزيان، واجهات برمجة التطبيقات</a></b></center></td>
</tr>
<tr>
<td colspan="7"><a href="#mtp"><center><b>Microsoft 365 Defender</a></center></b></td>
</tr>
</table>
<br>

<p></p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vnC4?rel=0]

> [!TIP]
> - تعرف على أحدث التحسينات في Defender لنقطة النهاية: [ما الجديد في Microsoft Defender لنقطة النهاية](whats-new-in-microsoft-defender-endpoint.md).
> - أظهرت Microsoft Defender لنقطة النهاية البصريات الرائدة في الصناعة وقدرات الكشف في تقييم MITRE الأخير. قراءة: [Insights من التقييم المستند إلى MITRE ATT&CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).


> [!IMPORTANT]
> قد تختلف القدرات على الأنظمة الأساسية غير Windows عن تلك الخاصة Windows. لمزيد من المعلومات حول القدرات المتوفرة للأنظمة الأساسية غير Windows، راجع [Microsoft Defender لنقطة النهاية للأنظمة الأساسية غير Windows](/microsoft-365/security/defender-endpoint/non-windows).

<a name="tvm"></a>

**[Core Defender Vulnerability Management](../defender-vulnerability-management/defender-vulnerability-management.md)**

تستخدم قدرات إدارة الثغرات الأمنية الأساسية المضمنة نهجا حديثا يستند إلى المخاطر لاكتشاف نقاط الضعف في نقطة النهاية والتكوينات الخاطئة وتقييمها وتحديد أولوياتها ومعالجتها. لتعزيز قدرتك على تقييم وضعك الأمني وتقليل المخاطر، تتوفر وظيفة إضافية جديدة لإدارة الثغرات الأمنية في Defender للخطة 2.

لمزيد من المعلومات حول إمكانيات إدارة الثغرات الأمنية المختلفة المتوفرة لك، راجع [مقارنة عروض إدارة الثغرات الأمنية في Microsoft Defender](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md).

<a name="asr"></a>

**[قواعد تقليل الأجزاء المعرضة للهجوم](overview-attack-surface-reduction.md)**

توفر مجموعة تقليل الأجزاء المعرضة للهجوم من القدرات خط الدفاع الأول في المكدس. من خلال ضمان تعيين إعدادات التكوين بشكل صحيح وتطبيق تقنيات التخفيف من الاستغلال، تقاوم القدرات الهجمات واستغلالها. تتضمن هذه المجموعة من القدرات أيضا [حماية الشبكة](network-protection.md) [وحماية الويب](web-protection-overview.md)، والتي تنظم الوصول إلى عناوين IP والمجالات وعناوين URL الضارة.

<a name="ngp"></a>

**[حماية الجيل التالي](next-generation-protection.md)**

لزيادة تعزيز محيط الأمان لشبكتك، تستخدم Microsoft Defender لنقطة النهاية حماية الجيل التالي المصممة لالتقاط جميع أنواع التهديدات الناشئة.

<a name="edr"></a>

**[الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md)**

يتم وضع قدرات الكشف عن نقطة النهاية والاستجابة لها للكشف عن التهديدات المتقدمة التي قد تكون تجاوزت أول ركيزتين أمنيتين والتحقيق فيها والاستجابة لها. يوفر [التتبع المتقدم](advanced-hunting-overview.md) أداة تتبع المخاطر المستندة إلى الاستعلام التي تتيح لك العثور على الاختراقات بشكل استباقي وإنشاء عمليات كشف مخصصة.

<a name="ai"></a>

**[التحقيق التلقائي والمعالجة](automated-investigations.md)**

إلى جانب القدرة على الاستجابة السريعة للهجمات المتقدمة، يوفر Microsoft Defender لنقطة النهاية قدرات التحقيق والمعالجة التلقائية التي تساعد على تقليل حجم التنبيهات في دقائق على نطاق واسع.

<a name="ss"></a>

**[Microsoft Secure Score للأجهزة](tvm-microsoft-secure-score-devices.md)**

يتضمن Defender لنقطة النهاية نقاط أمان Microsoft للأجهزة لمساعدتك على تقييم حالة الأمان لشبكة المؤسسة ديناميكيا، وتحديد الأنظمة غير المحمية، واتخاذ الإجراءات الموصى بها لتحسين الأمان العام لمؤسستك.

<a name="mte"></a>

**[خبراء المخاطر في Microsoft](microsoft-threat-experts.md)**

توفر خدمة تتبع التهديدات المدارة الجديدة في Microsoft Defender لنقطة النهاية التتبع الاستباقي وتحديد الأولويات والسياق الإضافي والرؤى التي تمكن مراكز عمليات الأمان (SOCs) من تحديد التهديدات والاستجابة لها بسرعة ودقة.

> [!IMPORTANT]
> يحتاج عملاء Defender لنقطة النهاية إلى التقدم بطلب لخدمة تتبع التهديدات المدارة خبراء المخاطر في Microsoft للحصول على إعلامات استباقية بالهجوم المستهدف والتعاون مع الخبراء عند الطلب. الخبراء عند الطلب هي خدمة إضافية. يتم تضمين إعلامات الهجوم المستهدف دائما بعد قبولك في خبراء المخاطر في Microsoft خدمة تتبع التهديدات المدارة.
>
> إذا لم تكن مسجلا بعد وترغب في تجربة فوائده، فانتقل إلى **الإعدادات** \> **الميزات** \> المتقدمة **العامة** \> **خبراء المخاطر في Microsoft** لتطبيقها. بمجرد قبولك، ستحصل على مزايا إعلامات الهجوم المستهدف، وستبدأ تجربة لمدة 90 يوما من الخبراء عند الطلب. اتصل بممثل Microsoft للحصول على اشتراك الخبراء عند الطلب الكامل.

<a name="apis"></a>

**[التكوين والإدارة المركزيان، واجهات برمجة التطبيقات](management-apis.md)**

دمج Microsoft Defender لنقطة النهاية في مهام سير العمل الموجودة.

<a name="mtp"></a>

**[التكامل مع حلول Microsoft](threat-protection-integration.md)**

يتكامل Defender لنقطة النهاية مباشرة مع حلول Microsoft المختلفة، بما في ذلك:

- Microsoft Defender للسحابة
- Microsoft Sentinel
- Intune
- Microsoft Defender for Cloud Apps
- Microsoft Defender للهوية
- Microsoft Defender for Office
- Skype for Business

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

من خلال Microsoft 365 Defender و Defender for Endpoint وحلول أمان Microsoft المختلفة، يمكنك تشكيل مجموعة دفاع موحدة لما قبل الخرق وما بعده تتكامل أصلا عبر نقطة النهاية والهوية والبريد الإلكتروني والتطبيقات للكشف عن الهجمات المتطورة ومنعها والتحقيق فيها والاستجابة لها تلقائيا.


## <a name="training-for-security-analysts"></a>تدريب لمحللين أمنيين

باستخدام مسار التعلم هذا من Microsoft Learn، يمكنك فهم Defender لنقطة النهاية وكيف يمكن أن يساعد في منع التهديدات واكتشافها والتحقيق فيها والاستجابة لها عبر نقاط نهاية مؤسستك - أجهزتك وأنظمتك.

|التدريب:|الكشف عن الهجمات الإلكترونية والاستجابة لها باستخدام Microsoft 365 Defender|
|---|---|
|![أيقونة التدريب Microsoft 365 Defender.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Defender لنقطة النهاية هو حل أمان نقطة النهاية الذي يوفر إدارة الثغرات الأمنية وحماية نقطة النهاية الكشف عن تهديدات نقاط النهاية والرد عليها والحماية من التهديدات المتنقلة والخدمات المدارة في نظام أساسي واحد وموحد.<p> 2 ساعة و25 دقيقة - مسار التعليم - 9 وحدات نمطية|

> [!div class="nextstepaction"]
> [بدء >](/learn/paths/defender-endpoint-fundamentals/)
