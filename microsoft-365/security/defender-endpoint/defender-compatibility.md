---
title: توافق حل الحماية من الفيروسات مع Defender for Endpoint
description: تعرف على كيفية عمل Windows Defender مع Microsoft Defender ل Endpoint. تعرف أيضا على كيفية عمل Defender for Endpoint عند استخدام عميل مكافحة البرامج الضارة من جهة خارجية.
keywords: توافق windows defender، defender، Microsoft Defender ل Endpoint، defender لنقطة النهاية، برنامج الحماية من الفيروسات، mde
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: conceptual
ms.date: 05/06/2021
ms.technology: mde
ms.openlocfilehash: a8384ed28e8c65871f61241dc522461390106be0
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570158"
---
# <a name="antivirus-solution-compatibility-with-microsoft-defender-for-endpoint"></a>توافق حل برنامج الحماية من الفيروسات مع Microsoft Defender ل Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-defendercompat-abovefoldlink)

يعتمد عامل Microsoft Defender لنقطة النهاية على برنامج الحماية من الفيروسات من Microsoft Defender لبعض الإمكانات مثل فحص الملفات.

> [!IMPORTANT]
> لا يلتزم Defender for Endpoint بإعدادات برنامج الحماية من الفيروسات من Microsoft Defender الاستثناءات.

يجب تكوين تحديثات معلومات الأمان على أجهزة Defender لنقطة النهاية سواء كانت برنامج الحماية من الفيروسات من Microsoft Defender هي مكافحة البرامج الضارة النشطة أم لا. لمزيد من المعلومات، [راجع إدارة برنامج الحماية من الفيروسات من Microsoft Defender الأساسية وتطبيق الأساسات](manage-updates-baselines-microsoft-defender-antivirus.md).

إذا كان أحد الأجهزة التي تم تشغيلها محميا بواسطة عميل مكافحة البرامج الضارة من جهة خارجية، برنامج الحماية من الفيروسات من Microsoft Defender في نقطة النهاية هذه في الوضع السلبي.

برنامج الحماية من الفيروسات من Microsoft Defender متابعة تلقي التحديثات، *mspeng.exe* العملية كخدمة قيد التشغيل. ولكنها لن تقوم بإجراء عمليات فحص ولا تحل محل عميل مكافحة البرامج الضارة الذي يعمل من جهة خارجية.

سيتم برنامج الحماية من الفيروسات من Microsoft Defender واجهة المستخدم. لن يتمكن المستخدمون على الجهاز من استخدام برنامج الحماية من الفيروسات من Microsoft Defender لإجراء عمليات فحص عند الطلب أو تكوين معظم الخيارات.

لمزيد من المعلومات، راجع الموضوع برنامج الحماية من الفيروسات من Microsoft Defender [و Defender لنقطة النهاية](microsoft-defender-antivirus-compatibility.md).
