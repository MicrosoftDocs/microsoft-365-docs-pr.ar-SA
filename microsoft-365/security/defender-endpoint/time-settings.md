---
title: Microsoft 365 Defender المنطقة الزمنية
description: استخدم المعلومات المضمنة هنا لتكوين Microsoft 365 Defender المنطقة الزمنية وعرض معلومات الترخيص.
keywords: الإعدادات، Microsoft Defender، المعلومات الخاصة بخطر الإنترنت، Microsoft Defender لنقطة النهاية، المنطقة الزمنية، utc، الوقت المحلي، الترخيص
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4353bbfc0ce11c4a767ca599ecb23a1ab4f77a56
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/25/2022
ms.locfileid: "63572369"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender المنطقة الزمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

استخدم قائمة **المنطقة الزمنية** ![أيقونة إعدادات المنطقة الزمنية1.](images/atp-time-zone.png) لتكوين المنطقة الزمنية وعرض معلومات الترخيص.

## <a name="time-zone-settings"></a>إعدادات المنطقة الزمنية

يعتبر جانب الوقت مهما في تقييم الهجمات الإلكترونية الفعلية والمتصورة وتحليلها.

تعتمد التحريات عبر الإنترنت في أغلب الأحيان على الطوابع الزمنية لتكاتف تسلسل الأحداث معا. من المهم أن يعكس النظام إعدادات المنطقة الزمنية الصحيحة.

يمكن أن يعرض Microsoft Defender لنقطة النهاية إما الوقت العالمي المنسق (UTC) أو الوقت المحلي.

يظهر إعداد المنطقة الزمنية الحالية في إعدادات Microsoft Defender. يمكنك تغيير المنطقة الزمنية المعروضة **في القائمة** المنطقة الزمنية ضمن الإعدادات > **الأمان**.

### <a name="utc-time-zone"></a>المنطقة الزمنية UTC

يستخدم Microsoft Defender ل Endpoint وقت UTC بشكل افتراضي.

سيعرض تعيين المنطقة الزمنية ل Microsoft Defender لنقطة النهاية إلى UTC جميع الamps الزمنية للنظام (التنبيهات والأحداث وغيرها) في UTC لجميع المستخدمين. يمكن أن يساعد ذلك محللي الأمان الذين يعملون في مواقع مختلفة حول العالم على استخدام الطوابع الزمنية نفسها أثناء التحقق من الأحداث.

### <a name="local-time-zone"></a>المنطقة الزمنية المحلية

يمكنك أن تختار أن يستخدم Microsoft Defender لنقطة النهاية إعدادات المنطقة الزمنية المحلية. سيتم عرض كل التنبيهات والأحداث باستخدام المنطقة الزمنية المحلية.

يتم أخذ المنطقة الزمنية المحلية من الإعدادات الإقليمية لجهازك. إذا قمت بتغيير الإعدادات الإقليمية، فإن المنطقة الزمنية ل Microsoft Defender لنقطة النهاية ستتغير أيضا. يعني اختيار هذا الإعداد أنه سيتم محاذاة الamps الزمنية المعروضة في Microsoft Defender لنقطة النهاية مع الوقت المحلي لجميع مستخدمي Microsoft Defender لنقطة النهاية. سيشاهد الآن المحللون الموجودون في مواقع عالمية مختلفة تنبيهات نقطة النهاية ل Microsoft Defender وفقا لإعداداتهم الإقليمية.

قد يكون اختيار استخدام الوقت المحلي مفيدا إذا كان المحللون موجودين في موقع واحد. في هذه الحالة، قد يكون من الأسهل ربط الأحداث بالتوقيت المحلي، على سبيل المثال، عندما ينقر مستخدم محلي فوق ارتباط بريد إلكتروني مريب.

### <a name="set-the-time-zone"></a>تعيين المنطقة الزمنية

يتم تعيين المنطقة الزمنية ل Microsoft Defender لنقطة النهاية بشكل افتراضي إلى UTC. كما أن تعيين المنطقة الزمنية يغير الأوقات لكل طرق عرض Microsoft Defender لنقطة النهاية.

لتعيين المنطقة الزمنية:

1. انقر فوق **الإعدادات** [في Microsoft 365 Defender](https://security.microsoft.com/) ![إعدادات المنطقة الزمنية للمدخل3.](images/atp-time-zone.png).
2. حدد **مركز الأمان**.
3. حدد **المنطقة الزمنية** ثم قم بتعيين المنطقة الزمنية إلى UTC أو المنطقة الزمنية المحلية.

### <a name="regional-settings"></a>الإعدادات الإقليمية

لتطبيق تنسيقات تاريخ مختلفة ل Microsoft Defender لنقطة النهاية، استخدم الإعدادات الإقليمية ل Internet Explorer (IE) Microsoft Edge (Edge). إذا كنت تستخدم مستعرضا آخر مثل Google Chrome، فاتبع الخطوات المطلوبة لتغيير إعدادات الوقت والتاريخ لهذا المستعرض. 

#### <a name="internet-explorer-ie-and-microsoft-edge"></a>Internet Explorer (IE) Microsoft Edge

تستخدم IE Microsoft Edge **إعدادات** المنطقة التي تم تكوينها في **الخيار** الساعات واللغة والمنطقة في لوحة التحكم. 

#### <a name="known-issues-with-regional-formats"></a>المشاكل المعروفة في التنسيقات الإقليمية

##### <a name="date-and-time-formats"></a>تنسيقات التاريخ والوقت

هناك بعض المشاكل المعروفة في تنسيقات التاريخ والوقت. إذا قمت بتكوين الإعدادات الإقليمية لأي شيء آخر غير التنسيقات المعتمدة، فقد لا يعكس المدخل إعداداتك بشكل صحيح.

يتم دعم تنسيقات التاريخ والوقت التالية:

- تنسيق التاريخ MM/dd/yyyy
- تنسيق التاريخ dd/MM/yyyy
- تنسيق الوقت hh:mm:ss (تنسيق 12 ساعة)

تنسيقات التاريخ والوقت التالية غير معتمدة حاليا:

- تنسيق التاريخ yyyy-MM-dd
- تنسيق التاريخ dd-MMM-yy
- تنسيق التاريخ dd/MM/yy
- تنسيق التاريخ MM/dd/yy
- تنسيق التاريخ باستخدام yy. سيتم عرض yyyy فقط.
- تنسيق الوقت HH:mm:ss (تنسيق 24 ساعة)

##### <a name="decimal-symbol-used-in-numbers"></a>الرمز العشري المستخدم في الأرقام

يكون الرمز العشري المستخدم دائما نقطة، حتى لو تم تحديد فاصلة في إعدادات تنسيق الأرقام في **إعدادات** المنطقة. على سبيل المثال، يتم عرض 15,5K ك 15,5K.
