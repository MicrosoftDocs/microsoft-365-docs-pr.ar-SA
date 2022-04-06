---
title: Microsoft 365 Defender المنطقة الزمنية
description: استخدم المعلومات المضمنة هنا لتكوين Microsoft 365 Defender المنطقة الزمنية وعرض معلومات الترخيص.
keywords: الإعدادات، Microsoft Defender، معلومات الأمن الإلكتروني، Microsoft Defender لنقطة النهاية، المنطقة الزمنية، utc، الوقت المحلي، الترخيص
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
ms.openlocfilehash: adf693bded45dcb44abd8d1e7892e5edc7b65585
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467148"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender المنطقة الزمنية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

استخدم **قائمة المنطقة** الزمنية لتكوين المنطقة الزمنية وعرض معلومات الترخيص.
:::image type="content" source="images/atp-time-zone.png" alt-text="إعدادات المنطقة الزمنية-1" lightbox="images/atp-time-zone.png":::

## <a name="time-zone-settings"></a>إعدادات المنطقة الزمنية

يعتبر جانب الوقت مهما في تقييم الهجمات الإلكترونية الفعلية والمتصورة وتحليلها.

تعتمد التحريات عبر الإنترنت في أغلب الأحيان على الطوابع الزمنية لتكاتف تسلسل الأحداث معا. من المهم أن يعكس النظام إعدادات المنطقة الزمنية الصحيحة.

Microsoft Defender لنقطة النهاية عرض الوقت العالمي المنسق (UTC) أو الوقت المحلي.

يظهر إعداد المنطقة الزمنية الحالية في قائمة Microsoft Defender لنقطة النهاية الزمنية. يمكنك تغيير المنطقة الزمنية المعروضة في **قائمة المنطقة** الزمنية.

:::image type="content" source="images/atp-time-zone-menu.png" alt-text="إعدادات المنطقة الزمنية-2" lightbox="images/atp-time-zone-menu.png":::

### <a name="utc-time-zone"></a>المنطقة الزمنية UTC

Microsoft Defender لنقطة النهاية استخدام وقت UTC بشكل افتراضي.

سيعرض Microsoft Defender لنقطة النهاية المنطقة الزمنية ل UTC جميع الamps الزمنية للنظام (التنبيهات والأحداث وغيرها) في UTC لجميع المستخدمين. يمكن أن يساعد ذلك محللي الأمان الذين يعملون في مواقع مختلفة حول العالم على استخدام الطوابع الزمنية نفسها أثناء التحقق من الأحداث.

### <a name="local-time-zone"></a>المنطقة الزمنية المحلية

يمكنك اختيار استخدام Microsoft Defender لنقطة النهاية المنطقة الزمنية المحلية. سيتم عرض كل التنبيهات والأحداث باستخدام المنطقة الزمنية المحلية.

يتم أخذ المنطقة الزمنية المحلية من الإعدادات الإقليمية لجهازك. إذا قمت بتغيير الإعدادات الإقليمية، Microsoft Defender لنقطة النهاية المنطقة الزمنية أيضا. يعني اختيار هذا الإعداد أن الamps الزمنية المعروضة في Microsoft Defender لنقطة النهاية سيتم محاذاتها مع الوقت المحلي لجميع المستخدمين Microsoft Defender لنقطة النهاية المستخدمين. سيشاهد الآن المحللون الموجودون في مواقع عالمية مختلفة Microsoft Defender لنقطة النهاية التنبيهات وفقا لإعداداتهم الإقليمية.

قد يكون اختيار استخدام الوقت المحلي مفيدا إذا كان المحللون موجودين في موقع واحد. في هذه الحالة، قد يكون من الأسهل ربط الأحداث بالتوقيت المحلي، على سبيل المثال، عندما ينقر مستخدم محلي فوق ارتباط بريد إلكتروني مريب.

### <a name="set-the-time-zone"></a>تعيين المنطقة الزمنية

يتم Microsoft Defender لنقطة النهاية المنطقة الزمنية بشكل افتراضي إلى UTC. كما أن تعيين المنطقة الزمنية يغير الأوقات لكل Microsoft Defender لنقطة النهاية العرض.

لتعيين المنطقة الزمنية:

1. انقر فوق **قائمة المنطقة** الزمنية.
   :::image type="content" source="images/atp-time-zone.png" alt-text="إعدادات المنطقة الزمنية-3" lightbox="images/atp-time-zone.png":::
1. حدد مؤشر **المنطقة الزمنية UTC** .
1. حدد **المنطقة الزمنية UTC** أو المنطقة الزمنية المحلية، على سبيل المثال -7:00.

### <a name="regional-settings"></a>الإعدادات الإقليمية

لتطبيق تنسيقات تاريخ مختلفة Microsoft Defender لنقطة النهاية، استخدم الإعدادات الإقليمية ل Internet Explorer (IE) Microsoft Edge (Edge). إذا كنت تستخدم مستعرضا آخر مثل Google Chrome، فاتبع الخطوات المطلوبة لتغيير إعدادات الوقت والتاريخ لهذا المستعرض. 

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
