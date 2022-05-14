---
title: تكوين فترة المهلة برنامج الحماية من الفيروسات من Microsoft Defender كتلة السحابة
description: يمكنك تكوين المدة التي سيحظر فيها برنامج الحماية من الفيروسات من Microsoft Defender تشغيل ملف أثناء انتظار تحديد السحابة.
keywords: برنامج الحماية من الفيروسات من Microsoft Defender، ومكافحة البرامج الضارة، والأمان، والمدافع، والسحابة، والمهلة، والكتلة، والنقطة، والثواني
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
ms.openlocfilehash: 0ad46ff70ed2542ebed423a02eba6cc0810a99ca
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418751"
---
# <a name="configure-the-cloud-block-timeout-period"></a>تكوين الفترة الزمنية لحظر السحابة

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

عندما يعثر برنامج الحماية من الفيروسات من Microsoft Defender على ملف مريب، يمكنه منع تشغيل الملف أثناء الاستعلام عن [خدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

الفترة الافتراضية لحظر [الملف هي](configure-block-at-first-sight-microsoft-defender-antivirus.md) 10 ثوان. إذا كنت مسؤول أمان، يمكنك تحديد المزيد من الوقت للانتظار قبل السماح بتشغيل الملف. يمكن أن يساعد تمديد فترة مهلة كتلة السحابة في ضمان وجود وقت كاف لتلقي تحديد مناسب من خدمة السحابة برنامج الحماية من الفيروسات من Microsoft Defender.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>المتطلبات الأساسية لاستخدام مهلة كتلة السحابة الموسعة

يجب تمكين [الحظر من النظرة الأولى](configure-block-at-first-sight-microsoft-defender-antivirus.md) والمتطلبات الأساسية قبل أن تتمكن من تحديد فترة مهلة ممتدة.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>تحديد فترة المهلة الموسعة باستخدام إدارة نقاط النهاية من Microsoft

يمكنك تحديد فترة مهلة كتلة السحابة مع [نهج أمان نقطة النهاية في إدارة نقاط النهاية من Microsoft](/mem/intune/protect/endpoint-security-policy).

1. انتقل إلى مركز إدارة إدارة نقاط النهاية ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)) وسجل الدخول.

2. حدد **أمان نقطة النهاية**، ثم ضمن **"إدارة**"، اختر **"الحماية من الفيروسات**".

3. حدد (أو أنشئ) نهج الحماية من الفيروسات.

4. في قسم **إعدادات التكوين** ، قم بتوسيع **حماية السحابة**. بعد ذلك، في **المربع برنامج الحماية من الفيروسات من Microsoft Defender المهلة الموسعة بالثوان**، حدد المزيد من الوقت، بالثوان، من ثانية إلى 50 ثانية. تتم إضافة كل ما تحدده إلى الثوان العشر الافتراضية.

5. (هذه الخطوة اختيارية) قم بإجراء أي تغييرات أخرى على نهج الحماية من الفيروسات. (هل تحتاج إلى مساعدة؟ راجع [الإعدادات لنهج برنامج الحماية من الفيروسات من Microsoft Defender في Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows).)

6. اختر **"التالي**"، وإنهاء تكوين النهج الخاص بك.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>تحديد فترة المهلة الموسعة باستخدام نهج المجموعة

يمكنك استخدام نهج المجموعة لتحديد مهلة موسعة لعمليات التحقق من السحابة.

1. على كمبيوتر إدارة نهج المجموعة، افتح [وحدة تحكم إدارة نهج المجموعة](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. انقر بزر الماوس الأيمن فوق الكائن نهج المجموعة الذي تريد تكوينه ثم حدد **"تحرير**".

3. في **نهج المجموعة Management Editor**، انتقل إلى **تكوين الكمبيوتر**، ثم حدد **القوالب الإدارية**.

3. توسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> **MpEngine**.

4. انقر نقرا **مزدوجا فوق تكوين فحص السحابة الموسعة** وتأكد من تمكين الخيار. 

   حدد مقدار الوقت الإضافي لمنع تشغيل الملف أثناء انتظار تحديد السحابة. حدد الوقت الإضافي، بالثوان، من ثانية إلى 50 ثانية. تتم إضافة كل ما تحدده إلى الثوان العشر الافتراضية.

5. حدد **موافق**.

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على نظام التشغيل macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج برنامج الحماية من الفيروسات في macOS لبرنامج الحماية من الفيروسات من Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender for Endpoint على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender for Endpoint على ميزات iOS](ios-configure-features.md) 
