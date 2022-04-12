---
title: تمكين ميزات حماية برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها
description: تمكين الحماية المستندة إلى السلوك والاستعلامية وفي الوقت الحقيقي في Microsoft Defender AV.
keywords: استيائية، تعلم آلي، مراقبة السلوك، الحماية في الوقت الحقيقي، دائما، برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، Defender
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 59754ac5186b87045e8126114fd7342f5aa9532c
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788843"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender 

**منصات**
- بالنسبة لنظام التشغيل

تستخدم برنامج الحماية من الفيروسات من Microsoft Defender عدة طرق لتوفير الحماية من التهديدات:

- حماية السحابة للكشف شبه الفوري عن التهديدات الجديدة والناشئة ومنعها
- المسح الضوئي دائما، باستخدام مراقبة سلوك الملفات والعمليات وغيرها من الأساليب الاستباقية (المعروفة أيضا باسم "الحماية في الوقت الحقيقي")
- تحديثات الحماية المخصصة المستندة إلى التعلم الآلي وتحليل البيانات الضخمة البشرية والآلية والبحث المتعمق في مقاومة التهديدات

يمكنك تكوين كيفية استخدام برنامج الحماية من الفيروسات من Microsoft Defender لهذه الأساليب مع نهج المجموعة وإدارة تكوين مركز النظام وPowerShell cmdlets وأداة إدارة Windows (WMI).

يغطي هذا القسم التكوين للمسح الضوئي دائما، بما في ذلك كيفية الكشف عن التطبيقات التي تعتبر غير آمنة وحظرها، ولكن قد لا يتم اكتشافها على أنها برامج ضارة.

راجع [استخدام تقنيات برنامج الحماية من الفيروسات من Microsoft Defender الجيل التالي من خلال حماية السحابة](cloud-protection-microsoft-defender-antivirus.md) لكيفية تمكين برنامج الحماية من الفيروسات من Microsoft Defender حماية السحابة وتكوينها.

## <a name="in-this-section"></a>في هذا القسم

| الموضوع|الوصف |
|---|---|
| [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| الكشف عن التطبيقات التي قد تكون غير مرغوب فيها في شبكتك وحظرها، مثل البرامج الضارة، وتعديلات المستعرض وأشرطة الأدوات، وتطبيقات الحماية من الفيروسات المخادقة أو المزيفة |
| [تمكين قدرات الحماية برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|تمكين وتكوين الحماية في الوقت الحقيقي، والاستعلامات، وغيرها من ميزات مراقبة برنامج الحماية من الفيروسات من Microsoft Defender دائما |

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
