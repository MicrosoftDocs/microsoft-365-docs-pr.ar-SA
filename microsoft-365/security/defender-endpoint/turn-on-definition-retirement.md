---
title: تشغيل إيقاف التعريف برنامج الحماية من الفيروسات من Microsoft Defender
description: تشغيل إيقاف التعريف برنامج الحماية من الفيروسات من Microsoft Defender.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، defender، تقاعد التعريف
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: dd9cd313dec962547acef85c6da326d3b6e5c58f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63578223"
---
# <a name="turn-on-definition-retirement"></a>تشغيل إيقاف التعريف

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

يمكنك تكوين تقاعد التعريف باستخدام "نهج المجموعة". يتحقق تقاعد التعريف لمعرفة ما إذا كان الكمبيوتر لديه تحديثات الأمان المطلوبة الضرورية لحمايتها من ثغرة أمنية معينة. إذا لم يكن النظام عرضة للاستغلال الذي كشفه تعريف، فإن هذا التعريف "متقاعد". إذا تم ازاله كل معلومات الأمان لبروتوكول معين، لن يتم تحليل هذا البروتوكول بعد الآن. يساعد تمكين هذه الميزة على تحسين الأداء. على جهاز كمبيوتر محدث مع كل تحديثات الأمان الأخيرة، لن يكون لحماية الشبكة أي تأثير على أداء الشبكة.

## <a name="use-group-policy-to-configure-definition-retirement"></a>استخدام "نهج المجموعة" لتكوين تقاعد التعريف

1. في نقطة نهاية إدارة نهج المجموعة، افتح وحدة [التحكم في إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. انتقل إلى **قوالب تكوين** \> الكمبيوتر  **الإدارية** **Windows** \> مكونات برنامج الحماية من الفيروسات من Microsoft Defender \> \> فحص الشبكة.

3. حدد **تشغيل إيقاف تشغيل التعريف**. بشكل افتراضي، يتم تمكين هذا النهج. إذا تم **تعيين لم يتم تكوينه**، يتم تمكين تقاعد التعريف.

4. لتحرير النهج، حدد **ارتباط إعداد نهج** التحرير.

5. حدد **تمكين**، ثم حدد **موافق**.

6. نشر كائن نهج المجموعة المحدث. راجع [وحدة تحكم إدارة نهج المجموعة](/windows/win32/srvnodes/group-policy).

> [!TIP]
> هل تستخدم "كائنات نهج المجموعة" في الموقع؟ تعرف على كيفية ترجمتها في السحابة. [قم بتحليل كائنات نهج المجموعة](/mem/intune/configuration/group-policy-analytics) في الموقع باستخدام تحليلات نهج المجموعة في إدارة نقاط النهاية من Microsoft - معاينة.
