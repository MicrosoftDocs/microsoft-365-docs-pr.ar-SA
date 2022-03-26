---
title: تكوين الفترة الزمنية برنامج الحماية من الفيروسات من Microsoft Defender مجموعة النظراء
description: يمكنك تكوين المدة التي برنامج الحماية من الفيروسات من Microsoft Defender من تشغيل ملف أثناء انتظار تحديد السحابة.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، مكافحة البرامج الضارة، الأمان، defender، السحابة، فتره، الحظر، الفترة، الثواني
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection: M365-security-compliance
ms.openlocfilehash: 1acd1a95ddc3aa679f0e5f1295e14cf33b4f97a0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570222"
---
# <a name="configure-the-cloud-block-timeout-period"></a>تكوين الفترة الزمنية لحظر السحابة

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

عندما برنامج الحماية من الفيروسات من Microsoft Defender عن ملف مريب، يمكن أن يمنعه من التشغيل أثناء الاستعلام عن برنامج الحماية من الفيروسات من Microsoft Defender [السحابة](cloud-protection-microsoft-defender-antivirus.md).

الفترة الافتراضية التي [يتم فيها حظر](configure-block-at-first-sight-microsoft-defender-antivirus.md) الملف هي 10 ثوان. إذا كنت مسؤول أمان، يمكنك تحديد المزيد من الوقت للانتظار قبل السماح بتشغيل الملف. يمكن أن يساعد تمديد فترة مدد الكتلة السحابية على ضمان وجود وقت كاف لتلقي التحديد المناسب من الخدمة السحابية برنامج الحماية من الفيروسات من Microsoft Defender السحابية.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>المتطلبات الأساسية لاستخدام مدد حظر السحابة الموسعة

[يجب تمكين الحظر من](configure-block-at-first-sight-microsoft-defender-antivirus.md) النظرة الأولى ولمتطلباته الأساسية قبل أن تتمكن من تحديد فترة ممتدة.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>تحديد فترة مدد مدد زمنية باستخدام إدارة نقاط النهاية من Microsoft

يمكنك تحديد الفترة الزمنية لحظر السحابة باستخدام نهج [أمان](/mem/intune/protect/endpoint-security-policy) نقطة النهاية في إدارة نقاط النهاية من Microsoft.

1. انتقل إلى إدارة نقاط النهاية إدارة ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)) ثم سجل الدخول.

2. حدد **أمان نقطة النهاية**، ثم ضمن **إدارة**، اختر **برنامج الحماية من الفيروسات**.

3. حدد (أو أنشئ) نهج مكافحة الفيروسات.

4. في المقطع **إعدادات التكوين** ، قم بتوسيع **الحماية السحابية**. بعد ذلك، **في المربع برنامج الحماية من الفيروسات من Microsoft Defender** 2010 بالثواني، حدد الوقت أكثر، بالثواني، من ثانية واحدة إلى 50 ثانية. يضاف كل ما تحدده إلى الثواني ال 10 الافتراضية.

5. (هذه الخطوة اختيارية) قم بإجراء أي تغييرات أخرى على نهج الحماية من الفيروسات. (هل تحتاج إلى مساعدة؟ راجع [الإعدادات للحصول على برنامج الحماية من الفيروسات من Microsoft Defender في Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows).)

6. اختر **التالي**، ثم قم بالانتهاء من تكوين النهج.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>تحديد الفترة الزمنية الموسعة باستخدام "نهج المجموعة"

يمكنك استخدام "نهج المجموعة" لتحديد فترة ممتدة للتحقق من السحابة.

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. انقر ب الماوس الأيمن فوق كائن نهج المجموعة الذي تريد تكوينه، ثم حدد **تحرير**.

3. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر**، ثم حدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **MpEngine**.

4. انقر نقرا **مزدوجا فوق تكوين التحقق من السحابة الموسعة** وتأكد من تمكين الخيار. 

   حدد مقدار الوقت الإضافي لمنع تشغيل الملف أثناء انتظار تحديد السحابة. حدد الوقت الإضافي، بالثواني، من ثانية واحدة إلى 50 ثانية. يضاف كل ما تحدده إلى الثواني ال 10 الافتراضية.

5. حدد **موافق**.

 
