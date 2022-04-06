---
title: تمكين ميزات الحماية برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها
description: تمكين الحماية المستندة إلى السلوك، والورعية، وفي الوقت الحقيقي في Microsoft Defender AV.
keywords: أسلوب أسلوبي، تعلم آلي، مراقبة السلوك، الحماية في الوقت الحقيقي، تشغيل دائم، برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، defender
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
ms.openlocfilehash: f949623b7d0647d71f4c665ed2016ee14a765e5f
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/14/2022
ms.locfileid: "63583225"
---
# <a name="configure-behavioral-heuristic-and-real-time-protection"></a>تكوين الحماية السلوكية، والحماية التحليلية، والحماية في الوقت الحقيقي


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

برنامج الحماية من الفيروسات من Microsoft Defender العديد من الطرق لتوفير الحماية من المخاطر:

- حماية السحابة للكشف الفوري عن التهديدات الجديدة والناشئة وحظرها
- الفحص المستمر، باستخدام مراقبة سلوك الملفات و العملية وغيرها من عمليات البحث (المعروفة أيضا باسم "الحماية في الوقت الحقيقي")
- تحديثات الحماية المخصصة استنادا إلى التعلم الآلي وتحليل البيانات الكبيرة البشرية والآلية وبحث معمق لمقاومة المخاطر

يمكنك تكوين كيفية استخدام برنامج الحماية من الفيروسات من Microsoft Defender هذه الأساليب مع نهج المجموعة وإدارة تكوين مركز النظام و PowerShell cmdlets Windows أدوات الإدارة (WMI).

يتناول هذا القسم تكوين المسح الضوئي دائما، بما في ذلك كيفية الكشف عن التطبيقات التي تعتبر غير آمنة وحظرها، ولكن قد لا يتم الكشف عنها كبرامج ضارة.

راجع [استخدام الجيل التالي برنامج الحماية من الفيروسات من Microsoft Defender من خلال الحماية السحابية](cloud-protection-microsoft-defender-antivirus.md) لمعرفة كيفية تمكين برنامج الحماية من الفيروسات من Microsoft Defender السحابة.

## <a name="in-this-section"></a>في هذا القسم

| الموضوع|الوصف |
|---|---|
| [الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)| الكشف عن التطبيقات التي قد تكون غير مرغوب فيها في شبكتك وحظرها، مثل البرامج الضارة وتعديلات المستعرض و شريط الأدوات وتطبيقات الحماية من الفيروسات غير المرغوب فيها أو الزائفة |
| [تمكين قدرات الحماية برنامج الحماية من الفيروسات من Microsoft Defender وتكوينها](configure-real-time-protection-microsoft-defender-antivirus.md)|تمكين الحماية في الوقت الحقيقي وميزات المتابعة وميزات المراقبة الأخرى برنامج الحماية من الفيروسات من Microsoft Defender الوقت الحقيقي وتكوينها |
