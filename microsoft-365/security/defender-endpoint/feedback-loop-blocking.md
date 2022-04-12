---
title: حظر حلقة الملاحظات
description: يعد حظر حلقة الملاحظات، الذي يسمى أيضا الحماية السريعة، جزءا من قدرات الحظر السلوكي والاحتواء في Microsoft Defender لنقطة النهاية
keywords: الحظر السلوكي، والحماية السريعة، وحظر الملاحظات، Microsoft Defender لنقطة النهاية
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: f68345b97d49adce2f55cffd837ca17e5b028953
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787985"
---
# <a name="feedback-loop-blocking"></a>حظر حلقة الملاحظات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

## <a name="overview"></a>نظرة عامة

حظر حلقة الملاحظات، ويشار إليه أيضا باسم الحماية السريعة، هو أحد مكونات [قدرات الحظر السلوكي والاحتواء](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) في [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/). مع حظر حلقة الملاحظات، تكون الأجهزة في جميع أنحاء مؤسستك محمية بشكل أفضل من الهجمات. 

## <a name="how-feedback-loop-blocking-works"></a>كيفية عمل حظر حلقة الملاحظات

عند الكشف عن سلوك أو ملف مريب، على سبيل المثال بواسطة [برنامج الحماية من الفيروسات من Microsoft Defender](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)، يتم إرسال معلومات حول هذه البيانات الاصطناعية إلى مصنفات متعددة. يفحص محرك حلقة الحماية السريعة المعلومات ويربطها بإشارات أخرى للوصول إلى قرار بشأن ما إذا كان يجب حظر ملف. يتم التحقق من البيانات الاصطناعية وتصنيفها بسرعة. ينتج عنه حظر سريع للبرامج الضارة المؤكدة، ويحرك الحماية عبر النظام البنائي بأكمله. 

مع وجود حماية سريعة، يمكن إيقاف الهجوم على جهاز وأجهزة أخرى في المؤسسة وأجهزة في مؤسسات أخرى، في محاولة للهجوم لتوسيع موطئ قدمها.


## <a name="configuring-feedback-loop-blocking"></a>تكوين حظر حلقة الملاحظات

إذا كانت مؤسستك تستخدم Defender لنقطة النهاية، يتم تمكين حظر حلقة الملاحظات بشكل افتراضي. ومع ذلك، تحدث الحماية السريعة من خلال مجموعة من قدرات Defender لنقطة النهاية وميزات حماية التعلم الآلي ومشاركة الإشارات عبر خدمات أمان Microsoft. تأكد من تمكين الميزات والقدرات التالية ل Defender لنقطة النهاية وتكوينها:

- [Microsoft Defender لنقطة النهاية الأساسات](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [الأجهزة التي تم إلحاقها Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/onboard-configure)

- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [قواعد تقليل الأجزاء المعرضة للهجوم](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [حماية الجيل التالي](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (مكافحة الفيروسات)

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)

- [(مدونة) الحظر السلوكي والاحتواء: تحويل البصريات إلى حماية](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [موارد Microsoft Defender لنقطة النهاية مفيدة](/microsoft-365/security/defender-endpoint/helpful-resources)
