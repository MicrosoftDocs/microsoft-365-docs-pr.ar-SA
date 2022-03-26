---
title: تقييم Microsoft 365 Defender
description: قم بإعداد Microsoft 365 Defender تجريبية أو تجربة تجربة حل الأمان المصمم لحماية الأجهزة والهوية والبيانات والتطبيقات في مؤسستك.
keywords: Microsoft 365 Defender، جرب Microsoft 365 Defender، Microsoft 365 Defender، Microsoft 365 Defender التقييم، Microsoft 365 Defender  طيار، أمان الإنترنت، تهديدات ثابتة متقدمة، أمان المؤسسة، الأجهزة، الجهاز، الهوية، المستخدمون، البيانات، التطبيقات، الأحداث، التحقيق التلقائي وا الإصلاح، الصيد المتقدم
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
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1c260588b80d8325567b74148a7a62586cfbc707
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/16/2021
ms.locfileid: "63571589"
---
# <a name="create-a-microsoft-365-defender-trial-lab-or-pilot-environment"></a>إنشاء Microsoft 365 Defender تجريبية أو بيئة تجريبية 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender


يساعدك هذا الدليل على العمل عبر إعداد بيئة معملية مع المستخدمين والمجموعات، ثم يرشدك خلال تكوين القدرات في Microsoft 365 Defender بحيث يمكنك تقليد هجوم خطر والحصول على نتيجة تجريبية ذات معنى. 

الغرض من إنشاء بيئة تجريبية أو معمل تجريبي هذا هو توضيح القدرات الشاملة Microsoft 365 Defender الإصدار التجريبي. اختبر كيف يكشف حل الأمان الذكي هذا عن التهديدات المتقدمة التي تواجه مؤسستك ويمنعها ويحقق فيها تلقائيا ويستجيب لها. 


سيتم إرشادك عبر الخطوات لبدء Microsoft 365 Defender التقييم استنادا إلى مسارات النشر الموصى بها. الهدف هو مساعدتك في إعداد حل الأمان إما في بيئة معمل باستخدام حساب تجريبي أو في بيئة تجريبية في الإنتاج مع ترخيص كامل. يمكن أن يساعدك إعداد بيئة الإصدار التجريبي أو المعمل التجريبي على تقديم حالات استخدام عمليات الأمان لصانعي القرار في مؤسستك. عندما تنجز عمليات محاكاة الهجمات وتقتنع بالنتائج، يمكنك نشرها بالكامل وتشغيلها في مؤسستك بمساعدة محترفي المبيعات التقنية من Microsoft أو الخبراء في مؤسستك. 

سيساعدك هذا الدليل على:
- إعداد خادم المعمل وأجهزة الكمبيوتر
- تكوين Active Directory مع المستخدمين والمجموعات
- قم بإعداد Microsoft Defender for Identity و Microsoft Defender Office 365 و Microsoft Defender ل Endpoint و Microsoft Cloud App Security
- إعداد سياسات محلية للخادم وأجهزة الكمبيوتر
- يحاكي هجوم خطر لإنشاء حادث اختبار أو تنبيه في Microsoft 365 Defender

>[!IMPORTANT]
>للحصول على أفضل النتائج، اتبع إرشادات إعداد المعمل قدر الإمكان.


## <a name="deployment-phases"></a>مراحل النشر

هناك ثلاث مراحل لإنشاء بيئة Microsoft 365 Defender تجريبية.

![مراحل النشر: الإعداد والإعداد واللوح](../../media/evaluation-guide-phases.png)

|المرحلة | الوصف | 
|:-------|:-----|
|[المرحلة 1: التحضير](prepare-m365d-eval.md)| تعرف على ما تحتاج إلى التفكير فيه عند نشر Microsoft 365 Defender في معمل تجريبي أو بيئة تجريبية: <br><br>- الممساهمين وتوقيع الخروج <br> - اعتبارات البيئة <br>- Access <br>- إعداد Azure Active Directory <br> - ترتيب التكوين
|[المرحلة الثانية: الإعداد](setup-m365deval.md)|  قم بالخطوات الأولية للوصول Microsoft 365 مركز الأمان لإعداد بيئة Microsoft 365 Defender الإصدار التجريبي أو الاختبار. سيتم إرشادك إلى:<br><br>- التسجيل للحصول على Microsoft 365 E5 تجريبي <br>  - تكوين المجال<br>- تعيين Microsoft 365 E5 جديدة<br>- إكمال معالج الإعداد في المدخل|
|[المرحلة 3: تكوين & Onboard](config-m365d-eval.md) | تكوين كل عمود Microsoft 365 Defender ونقاط نهاية التهيئة. سيتم إرشادك إلى:<br><br>- تكوين Microsoft Defender Office 365<br>- تكوين Microsoft Cloud App Security<br>- تكوين Microsoft Defender for Identity<br>- تكوين Microsoft Defender لنقطة النهاية


بعد إكمال هذا الدليل، كنت ستتعرف على المساهمين المعنيين والموافقات المطلوبة، والحصول على أذونات الوصول الصحيحة، والتسليل التجريبي، وتكوين المجالات وكل عمود من أعمدة Microsoft 365 Defender، وستتعين نقاط النهاية إلى الخدمة.

## <a name="key-capabilities"></a>الإمكانات الأساسية

على الرغم Microsoft 365 Defender يوفر العديد من الإمكانات، فإن الغرض الأساسي من دليل النشر هذا هو بدء استخدام أجهزة الالتحاق. بالإضافة إلى الالإضافة، فإن هذه الإرشادات ستطلق عليك الإمكانات التالية.


الإمكانية | الوصف 
:---|:---
Microsoft Defender Office 365 | يساعد على حماية Office 365 بالكامل من تهديدات اليوم
Microsoft Defender for Identity | تحديد التهديدات على الهويات المساسة والإجراءات الضارة ل insider والكشف عنها.
Microsoft Cloud App Security | يوفر رؤية غنية، والتحكم في تنقل البيانات، والكشف عن الهجمات الإلكترونية عبر الخدمات السحابية.
Microsoft Defender لنقطة النهاية | يمنع قدرات الاستجابة للتهديدات المتقدمة ويكشف عنها ويوفرها مع أمان شامل لنقاط النهاية.


## <a name="in-scope"></a>في النطاق

المهام التالية في نطاق هذا الدليل:
-   إعداد Azure Active Directory
-   إعداد Microsoft 365 Defender
    -   التسجيل للحصول على Microsoft 365 E5 تجريبي أو استخدام الترخيص الكامل إذا كنت تقوم بتشغيل إصدار تجريبي
    -   تكوين المجال
    -   تعيين Microsoft 365 E5 جديدة
    -   إكمال معالج الإعداد داخل المدخل
-   تكوين كل Microsoft 365 Defender استنادا إلى أفضل الممارسات
    -   Microsoft Defender Office 365
    -   Microsoft Defender for Identity
    -   Microsoft Cloud App Security
    -   Microsoft Defender لنقطة النهاية

## <a name="out-of-scope"></a>خارج النطاق

ما يلي خارج نطاق دليل النشر هذا:

-   تكوين حلول  الأطراف الخارجية التي قد تتكامل مع Microsoft 365 Defender
-   اختبار الاختراق في بيئة الإنتاج

## <a name="next-step"></a>الخطوة التالية
[المرحلة 1: التحضير](prepare-m365d-eval.md) 
<br> تحضير بيئة Microsoft 365 Defender التجريبية أو التجريبية
