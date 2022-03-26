---
title: تشغيل مشروع Microsoft 365 Defender التجريبي
description: يمكنك تشغيل مشروع Microsoft 365 Defender الإنتاج لتحديد فوائد Microsoft 365 Defender بفعالية.
keywords: Microsoft 365 Defender، قم بتشغيل مشروع تجريبي Microsoft 365 Defender، Microsoft 365 Defender في الإنتاج، Microsoft 365 Defender  مشروع تجريبي، أمان عبر الإنترنت، تهديدات ثابتة متقدمة، أمان المؤسسة، الأجهزة، الجهاز، الهوية، المستخدمون، البيانات، التطبيقات، الحوادث، التحقيق التلقائي وا الإصلاح، الصيد المتقدم
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fd84ef93d679be6e1e42f823dcac1f2d5181f1e9
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63573839"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>تشغيل مشروع Microsoft 365 Defender التجريبي 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender


يساعدك هذا الدليل على تشغيل مشروع تجريبي من خلال توفير نقاط لضمان أن لديك خطة منظمة بشكل جيد، وإرشادك عبر استخدام ميزة محاكاة الهجمات، وأخيرا اختتم التجربة باستخدام أدوات أخذ المفاتيح لكي تعكس النتائج وتوثقها.

![المراحل في تشغيل Microsoft 365 Defender تجريبي](../../media/pilotphases.png)


يساعدك تشغيل التجربة على تحديد الفائدة من استخدام Microsoft 365 Defender. قبل تمكين Microsoft 365 Defender في بيئة الإنتاج وبدء حالات الاستخدام، من الأفضل التخطيط لتحديد المهام التي يجب إنجازها لمشروعك التجريبي وتحديد معايير النجاح. 


## <a name="how-to-use-this-pilot-playbook"></a>كيفية استخدام دفتر التشغيل التجريبي هذا

يوفر هذا الدليل نظرة عامة Microsoft 365 Defender الإرشادات خطوة بخطوة حول كيفية إعداد مشروعك التجريبي. 

Microsoft 365 Defender مجموعة موحدة من الدفاع الخاص بالمؤسسات قبل الخرق وبعده تقوم بتنسيق الحماية والكشف والمنع والتحري والاستجابة عبر نقاط النهاية والهويات والبريد الإلكتروني والتطبيقات لتوفير حماية متكاملة من الهجمات المعقدة. وهو يقوم بذلك من خلال دمج الإمكانات التالية وتنسقها في حل أمان واحد:

- Microsoft Defender لنقطة النهاية (نقاط النهاية)
- Microsoft Defender Office 365 (بريد إلكتروني)
- Microsoft Defender for Identity (identity)
- Microsoft Cloud App Security (التطبيقات)

![صورة of_Microsoft 365 Defender للمستخدمين، Microsoft Defender for Identity، لنقاط النهاية Microsoft Defender ل Endpoint، لتطبيقات السحابة، Microsoft Cloud App Security، والبيانات، Microsoft Defender Office 365](../../media/mtp/m365pillars.png)

باستخدام حل Microsoft 365 Defender المتكامل، يمكن لمحترفي الأمان دمج إشارات التهديدات التي تشير إلى أن Microsoft Defender ل Endpoint و Microsoft Defender ل Office 365 و Microsoft Defender for Identity و Microsoft Cloud App Security  وحدد النطاق الكامل للتهديد وتأثيره، وكيفية دخوله إلى البيئة، وما تأثر به، وكيفية تأثيره حاليا على المؤسسة. Microsoft 365 Defender الإجراء التلقائي لمنع الهجوم أو إيقافه والتئام علب البريد ونقاط النهاية وهويات المستخدمين المتأثرة أو إيقافها. راجع Microsoft 365 Defender [العامة للحصول](microsoft-365-defender.md) على التفاصيل.

يختلف المخطط الزمني النموذجي التالي استنادا إلى وجود الموارد المناسبة في بيئتك. قد تحتاج بعض عمليات الكشف ومهمات سير العمل إلى وقت تعلم أكثر من الوقت الآخر.

![نموذج مخطط زمني في تشغيل Microsoft 365 Defender تجريبي](../../media/phase-diagrams/pilot-phases.png)

> [!IMPORTANT]
> للحصول على أفضل النتائج، اتبع إرشادات التجربة قدر الإمكان.

### <a name="pilot-playbook-phases"></a>مراحل دفتر التشغيل التجريبي

هناك أربع مراحل في تشغيل Microsoft 365 Defender تجريبي:

|المرحلة | الوصف |
|:-------|:-----|
| [التخطيط](m365d-pilot-plan.md)<br> ~ يوم واحد| تعرف على ما تحتاج إلى التفكير فيه قبل تشغيل مشروع Microsoft 365 Defender التجريبي: <br><br>- النطاق <br> - استخدام الحالات <br>- المتطلبات <br>- خطة الاختبار <br> - معايير النجاح <br> - بطاقة الأداء 
| [التحضير](m365d-evaluation.md) <br>~2 يوما|  يمكنك Microsoft 365 مركز الأمان لإعداد بيئة Microsoft 365 Defender التجريبية. سيتم إرشادك إلى:<br><br>- تحديد المساهمين والبحث عن تسجيل الخروج للطيار <br> - اعتبارات البيئة <br>- Access <br>- إعداد Azure Active Directory <br> - ترتيب التكوين <br> - التسجيل للحصول على Microsoft 365 E5 تجريبي <br> - تكوين المجال <br>- تعيين Microsoft 365 E5 جديدة <br> - إكمال معالج الإعداد في المدخل|
| [محاكاة الهجمات](m365d-pilot-simulate.md) <br>~2 يوما| لمحاكاة هجوم، سيتم إرشادك إلى:<br><br>- التحقق من متطلبات بيئة الاختبار <br>- تشغيل المحاكاة <br>- التحقق من حادث <br>- حل الحادث 
| [إغلاق وملخص](m365d-pilot-close.md) <br>~ يوم واحد| عندما تصل إلى نهاية العملية، سيتم إرشادك إلى:<br><br>- الانتقال عبر الإخراج النهائي<br>- تقديم الإخراج إلى المساهمين <br>- تقديم الملاحظات <br>- اتخاذ الخطوات التالية 

## <a name="next-step"></a>الخطوة التالية

|[مرحلة التخطيط](m365d-pilot-plan.md) | تخطيط مشروع Microsoft 365 Defender التجريبي 
|:-------|:-----|
