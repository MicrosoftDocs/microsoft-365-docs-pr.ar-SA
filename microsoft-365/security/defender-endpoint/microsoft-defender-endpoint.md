---
title: Microsoft Defender لنقطة النهاية
description: Microsoft Defender ل Endpoint هو نظام أساسي لأمن نقطة نهاية المؤسسة يساعد على الدفاع ضد التهديدات الثابتة المتقدمة.
keywords: مقدمة حول Microsoft Defender ل Endpoint، مقدمة حول Microsoft Defender لنقطة النهاية، الأمان عبر الإنترنت، التهديدات الثابتة المتقدمة، أمان المؤسسة، أداة الاستشعار السلوكية الآلية، الأمان السحابي، التحليلات، المعلومات المتعلقة بالتهجم، الحد من سطح الهجوم، حماية الجيل التالي، التحقيق التلقائي والتحلي، خبراء المخاطر من Microsoft، نقاط آمنة، عمليات البحث المتقدمة، Microsoft 365 Defender، مكافحة التهديدات الإلكترونية
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
ms.openlocfilehash: c4308c203093d2170cc1a6316db824ee9935363f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63583209"
---
# <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft Defender ل Endpoint هو نظام أساسي لأمن نقطة نهاية المؤسسة تم تصميمه لمساعدة شبكات المؤسسات على منع التهديدات المتقدمة والكشف عنها والتحقق منها والاستجابة لها.

> [!TIP]
> قريبا، سيتوفر Microsoft Defender لنقطة النهاية في خطتين. تصف هذه المقالة الميزات والإمكانات المضمنة في Microsoft Defender لخطة نقطة النهاية 2. [تعرف على المزيد حول Microsoft Defender لخطة نقطة النهاية 1 الخطة 2](defender-endpoint-plan-1-2.md).
> 

<p><p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wDob]

يستخدم Defender for Endpoint مجموعة التقنيات التالية المضمنة في Windows 10 والخدمات السحابية القوية من Microsoft:

- أدوات الاستشعار السلوكية لنقطة **النهاية: تقوم** أدوات الاستشعار هذه، المضمنة في Windows 10، بتجميع الإشارات السلوكية من نظام التشغيل وترسل بيانات المستشعر هذه إلى مثيل Microsoft Defender لنقطة النهاية الخاص والمعزول والسحابي.

- تحليلات أمان السحابة **: الاستفادة** من البيانات الكبيرة وتعلم الأجهزة وبصريات Microsoft الفريدة عبر النظام البيئي ل Windows ومنتجات السحابة الخاصة بالمؤسسات (مثل Office 365) والأصول عبر الإنترنت، تتم ترجمة الإشارات السلوكية إلى تحليلات واكتشافات واستجابات مستحسنة للتهديدات المتقدمة.

- المعلومات المتعلقة بالخطر **: التي** يتم إنشاؤها بواسطة صائدي Microsoft وفرق الأمان وزيادة المعلومات المتعلقة بالخطر التي يوفرها الشركاء، تمكن المعلومات المتعلقة بخطر المخاطر Defender for Endpoint من تحديد أدوات وتقنيات وإجراءات المهاجمين، كما تمكنهم من إنشاء تنبيهات عند ملاحظتها في بيانات المستشعر المجمعة.

<center><h2>Microsoft Defender لنقطة النهاية</center></h2>
<table>
<tr>
<td><a href="#tvm"><center><img src="images/TVM_icon.png" alt="Threat & Vulnerability Management"> <br><b>إدارة & المخاطر</b></center></a></td>
<td><a href="#asr"><center><img src="images/asr-icon.png" alt="Attack surface reduction"><br><b>الحد من سطح الهجوم</b></center></a></td>
<td><center><a href="#ngp"><img src="images/ngp-icon.png" alt="Next-generation protection"><br> <b>حماية الجيل التالي</b></a></center></td>
<td><center><a href="#edr"><img src="images/edr-icon.png" alt="Endpoint detection and response"><br> <b>الكشف عن نقطة النهاية والاستجابة لها</b></a></center></td>
<td><center><a href="#ai"><img src="images/air-icon.png" alt="Automated investigation and remediation"><br> <b>المعالجة والتحري التلقائي</b></a></center></td>
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
>
> - تعرف على التحسينات الأخيرة في Defender for Endpoint: ما [الجديد في Microsoft Defender لنقطة النهاية](whats-new-in-microsoft-defender-endpoint.md).
> - أظهر Microsoft Defender ل Endpoint قدرات الكشف والبصريات الرائدة في تقييم MITRE الأخير. اقرأ: [Insights من تقييم MITRE ATT&المستند إلى CK](https://cloudblogs.microsoft.com/microsoftsecure/2018/12/03/insights-from-the-mitre-attack-based-evaluation-of-windows-defender-atp/).

<a name="tvm"></a>

**[إدارة & المخاطر](next-gen-threat-and-vuln-mgt.md)**

تستخدم هذه الإمكانية المضمنة نهجا مستندا إلى المخاطر يقوم على تغيير اللعبة لاكتشاف نقاط الضعف والتضمينات الخاطئة وتحديد أولوياتها وتصفية نقاط النهاية.

<a name="asr"></a>

**[الحد من سطح الهجوم](overview-attack-surface-reduction.md)**

توفر مجموعة إمكانات تقليل مساحة الهجوم خط الدفاع الأول في المكدس. ومن خلال ضمان تعيين إعدادات التكوين بشكل صحيح وتطبيق أساليب التخفيف من المخاطر، تقاوم الإمكانات الهجمات واستغلالها. تتضمن مجموعة الإمكانات [هذه أيضا حماية](network-protection.md) الشبكة [وحماية](web-protection-overview.md) الويب، التي تنظم الوصول إلى عناوين IP والمجالات وعناوين URL الضارة.

<a name="ngp"></a>

**[حماية الجيل التالي](next-generation-protection.md)**

لمزيد من تعزيز محيط الأمان للشبكة، يستخدم Microsoft Defender ل Endpoint حماية الجيل التالي المصممة لالتقاط جميع أنواع التهديدات الناشئة.

<a name="edr"></a>

**[الكشف عن نقطة النهاية والاستجابة لها](overview-endpoint-detection-response.md)**

يتم وضع قدرات الكشف عن نقاط النهاية والاستجابة لها في مكانها للكشف عن التهديدات المتقدمة التي قد تكون جعلتها تنهي أول عمودين من أعمدة الأمان والاستجابة لها والاستجابة لها. [يوفر الصيد المتقدم](advanced-hunting-overview.md) أداة بحث عن تهديدات تستند إلى استعلام تتيح لك العثور على الخروقات بشكل استباقي وإنشاء عمليات كشف مخصصة.

<a name="ai"></a>

**[المعالجة والتحري التلقائي](automated-investigations.md)**

بالتزامن مع القدرة على الاستجابة بسرعة للهجمات المتقدمة، يوفر Microsoft Defender ل Endpoint إمكانات المعالجة والتدقيق التلقائي التي تساعد على تقليل حجم التنبيهات بالدقائق على نطاق واسع.

<a name="ss"></a>

**[Microsoft Secure Score للأجهزة](tvm-microsoft-secure-score-devices.md)**

يتضمن Defender for Endpoint Microsoft Secure Score للأجهزة لمساعدتك على تقييم حالة الأمان لشبكة المؤسسة بشكل ديناميكي، وتحديد الأنظمة غير المحمية، واتخاذ الإجراءات الموصى بها لتحسين الأمان العام لمؤسستك.

<a name="mte"></a>

**[خبراء المخاطر في Microsoft](microsoft-threat-experts.md)**

توفر خدمة البحث عن المخاطر المدارة الجديدة في Microsoft Defender ل Endpoint إمكانية الاصطلاح الاستباقي وتحديد الأولويات وسياق إضافي ورؤى إضافية تمكن مراكز عمليات الأمان (SOCs) من التعرف على التهديدات والاستجابة لها بسرعة ودقة.

> [!IMPORTANT]
> يحتاج Defender لعملاء Endpoint إلى التقدم بطلب للحصول على خدمة البحث عن خبراء المخاطر في Microsoft المخاطر المدارة للحصول على إعلامات استباقية حول الهجمات المستهدفة والتعاون مع الخبراء عند الطلب. الخبراء عند الطلب هي خدمة الوظائف الإضافية. يتم دائما تضمين إعلامات الهجمات المستهدفة بعد أن يتم قبولك في خدمة خبراء المخاطر في Microsoft المخاطر المدارة.
>
> إذا لم تكن مسجلا بعد وتحب  \>  \>  \> تجربة مزاياه، فاذهب إلى الإعدادات الميزات المتقدمة العامة **خبراء المخاطر في Microsoft لتطبيقها**. بمجرد قبولك، ستحصل على مزايا إعلامات الهجمات المستهدفة، وستبدأ تجربة لمدة 90 يوما من الخبراء عند الطلب. اتصل بممثل Microsoft للحصول على اشتراك خبراء عند الطلب الكامل.

<a name="apis"></a>

**[التكوين والإدارة المركزيان، واجهات برمجة التطبيقات](management-apis.md)**

ادمج Microsoft Defender ل Endpoint في مهام سير العمل الموجودة.

<a name="mtp"></a>

**[التكامل مع حلول Microsoft](threat-protection-integration.md)**

يتكامل Defender for Endpoint مباشرة مع حلول Microsoft المختلفة، بما في ذلك:

- Microsoft Defender for Cloud
- Microsoft Sentinel
- Intune
- Microsoft Defender لتطبيقات السحابة
- Microsoft Defender for Identity
- Microsoft Defender Office
- Skype for Business

**[Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)**

باستخدام Microsoft 365 Defender، يشكل Defender for Endpoint وحلول أمان Microsoft المتنوعة مجموعة موحدة من برامج الدفاع الخاصة بالمؤسسات قبل الخرق وبعده تتكامل بشكل أصلي عبر نقاط النهاية والهوية والبريد الإلكتروني والتطبيقات للكشف عن الهجمات المعقدة ومنعها التحقيق فيها والرد عليها تلقائيا.


## <a name="training-for-security-analysts"></a>تدريب لمحللين الأمان

باستخدام مسار التعلم هذا من Microsoft Learn، يمكنك فهم Defender for Endpoint وكيفية المساعدة في منع التهديدات والكشف عنها والتحقق منها والاستجابة لها عبر نقاط النهاية في مؤسستك – أجهزتك وأنظمتك.

|التدريب:|الكشف عن الهجمات الإلكترونية والاستجابة لها باستخدام Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender التدريب.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|إن Defender ل Endpoint هو حل أمان لنقطة النهاية يوفر إدارة الثغرات الأمنية وحماية نقاط النهاية الكشف عن تهديدات نقاط النهاية والرد عليها والدفاع عن تهديدات الأجهزة المحمولة والخدمات المدارة في نظام أساسي واحد موحد.<p> 2 ساعة و25 دقيقة - Learning - 9 وحدات|

> [!div class="nextstepaction"]
> [ابدأ >](/learn/paths/defender-endpoint-fundamentals/)
