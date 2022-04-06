---
title: الإبلاغ عن رسائل البريد العشوائي والبريد غير العشوائي ورسائل التصيد الاحتيالي إلى Microsoft
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: يمكن للمسؤولين التعرف على الطرق المختلفة التي يمكن من خلالها الإبلاغ عن الرسائل والملفات الجيدة والسيئة إلى Microsoft لتحليلها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f7818b15d97d8d7ee33005927ff899e9f5ff5a06
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682714"
---
# <a name="report-messages-and-files-to-microsoft"></a>الإبلاغ عن الرسائل والملفات إلى Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في Microsoft 365 المؤسسات التي لديها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، لدى كل من المستخدمين المسؤولين العديد من الطرق المختلفة للإبلاغ عن رسائل البريد الإلكتروني والملفات إلى Microsoft.

|الأسلوب|الوصف|
|---|---|
|[استخدام مدخل عمليات الإرسال لإرسال رسائل البريد العشوائي والتصيد الاحتيالي عناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md)|أسلوب إعداد التقارير الموصى به للمسؤولين في المؤسسات التي Exchange Online علب بريد (غير متوفرة في EOP مستقل).|
|[تمكين رسالة التقرير أو الوظائف الإضافية "الإبلاغ عن التصيد الاحتيالي"](enable-the-report-message-add-in.md)|يعمل مع Outlook Outlook على ويب (المعروف سابقا باسم Outlook Web App). <p> استنادا إلى اشتراكك، تتوفر الرسائل التي قام المستخدمون بلتقارير بشأنها باستخدام الوظائف الإضافية [](admin-submission.md)في مدخل عمليات إرسال المسؤول ونتائج الردود والتحريات [التلقائية (AIR)](air-view-investigation-results.md) تقرير الرسائل التي تم الإبلاغ عنها من قبل [المستخدم](threat-explorer-views.md#email--submissions) والمستكشف.[](view-email-security-reports.md#user-reported-messages-report) <p> يمكنك تكوين الرسائل التي تم إعدادها لنسخها أو إعادة توجيهها إلى علبة بريد تحددها. لمزيد من المعلومات، راجع [سياسات إرسال المستخدم.](user-submission.md)
|[الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook](report-false-positives-and-false-negatives.md)|إرسال إيجابيات خاطئة (بريد إلكتروني جيد تم حظره أو إرساله إلى مجلد غير هام) وسلبيات خاطئة (بريد إلكتروني غير مرغوب فيه أو تصيد احتيالي تم تسليمه إلى علبة الوارد) إلى Exchange Online Protection (EOP) باستخدام ميزة "رسالة التقرير".|
|[استخدام قواعد تدفق البريد لمعرفة ما يقوم المستخدمون بالإبلاغ عنه إلى Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|تعرف على كيفية إنشاء قاعدة تدفق بريد (تعرف أيضا باسم قاعدة نقل) تعلمك عندما يقوم المستخدمون بلتقارير الرسائل إلى Microsoft لتحليلها.|
|[إرسال البرامج الضارة وغير الضارة إلى Microsoft لتحليلها](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|استخدم التحليل الذكي لمخاطر الأمان من Microsoft لإرسال المرفقات والملفات الأخرى.|

> [!NOTE]
> توجد البيانات من الواجبات المرسلة إلى Microsoft في Office 365 التوافق في مراكز بيانات أمريكا الشمالية. يراجع المحللون في فريق الهندسة البيانات للمساعدة على تحسين فعالية عوامل التصفية. تعتبر عملية الإرسال ملاحظات للمساعدة على تحسين عوامل التصفية، كما يتم الاحتفاظ بها لفترة 30 يوما. بعد ذلك، يتم حذفه.
