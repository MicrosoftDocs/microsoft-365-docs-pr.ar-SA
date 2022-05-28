---
title: استبقاء البيانات Microsoft Defender لـ Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.technology: mdo
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Microsoft Defender لـ Office 365 معلومات استبقاء البيانات، عمليات الكشف عن Real-Time/مستكشف البيانات
ms.openlocfilehash: 9cab47358890b47796a42e48b690818d65e20527
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772785"
---
# <a name="data-retention-information-for-microsoft-defender-for-office-365"></a>معلومات استبقاء البيانات Microsoft Defender لـ Office 365

بشكل افتراضي، يتم الاحتفاظ بالبيانات عبر الميزات المختلفة لمدة 30 يوما كحد أقصى. ومع ذلك، بالنسبة لبعض الميزات، يمكنك تحديد فترة الاستبقاء استنادا إلى النهج. راجع الجدول التالي لفترات الاستبقاء المختلفة لكل ميزة.

> [!NOTE]
> تأتي Microsoft Defender لـ Office 365 في نوعين مختلفين من الخطط. يمكنك معرفة ما إذا كان لديك **الخطة 1** إذا كان لديك "الكشف في الوقت الحقيقي"، والخطة **2**، إذا كان لديك مستكشف المخاطر. تؤثر الخطة التي لديك على الأدوات التي ستراها، لذا تأكد من أنك على دراية بخطتك أثناء تعلمك.

## <a name="defender-for-office-365-plan-1"></a>Microsoft Defender للخطة 1 من Office 365

|ميزه|فترة الاستبقاء|
|---|---|
|تفاصيل بيانات تعريف التنبيه (Microsoft Defender لتنبيهات Office) | 90 يوما |
|تفاصيل بيانات تعريف الكيان (رسائل البريد الإلكتروني) | 30 يوماً |
|تفاصيل تنبيه النشاط (سجلات التدقيق) | 7 أيام |
|صفحة كيان البريد الإلكتروني | 30 يوماً |
|العزل | 30 يوما (يمكن تكوينها بحد أقصى يصل إلى 30 يوما) |
|التقارير | 90 يوما (لكافة البيانات المجمعة) <br>30 يوما (لكافة المعلومات المفصلة باستثناء ما يلي) <br> 10 أيام (لتفاصيل تقرير حالة الحماية من التهديدات وتفاصيل تقرير البريد المخادعة) <br> 7 أيام (لتفاصيل تقرير حماية عنوان URL) <br>
|الطلبات | 30 يوماً |
|اكتشافات مستكشف التهديدات/ Real-Time | 30 يوماً |

## <a name="defender-for-office-365-plan-2"></a>Microsoft Defender للخطة 2 من Office 365

Defender لـ Office 365 قدرات الخطة 1، بالإضافة إلى:

|ميزه|فترة الاستبقاء|
|---|---|
|مركز الصيانة | 180 يوما، 30 يوما (Office مركز الصيانة)   |
|التتبع المتقدم | 30 يوماً |
|AIR (التحقيق التلقائي والاستجابة) | 60 يوما (لبيانات تعريف التحقيقات)<br> 30 يوما (لبيانات تعريف البريد الإلكتروني)  |
|بيانات محاكاة الهجوم | 18 شهرا |
|حملات | 30 يوماً |
|الأحداث | 30 يوماً|
|الاصلاح | 30 يوماً |
|تحليلات التهديدات | 30 يوماً |
|متعقب المخاطر | 30 يوماً |
