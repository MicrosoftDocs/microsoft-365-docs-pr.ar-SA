---
title: الإبلاغ عن رسائل البريد العشوائي وغير العشوائي والتصيد الاحتيالي إلى Microsoft
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
description: يمكن للمسؤولين التعرف على الطرق المختلفة للإبلاغ عن الرسائل الجيدة والسيئة وعناوين URL ومرفقات البريد الإلكتروني والمسؤولين إلى Microsoft للتحليل.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 071e6329e16ecfce0e55649869d93ff31dfc9664
ms.sourcegitcommit: 4a1efedd15146744511378a44a307d44b16f3fb5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66644013"
---
# <a name="report-items-to-microsoft"></a>الإبلاغ عن العناصر إلى Microsoft

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في مؤسسات Microsoft 365 التي لديها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online، تتوفر للمستخدمين والمسؤولين عدة طرق مختلفة للإبلاغ عن رسائل البريد الإلكتروني وعناوين URL ومرفقات البريد الإلكتروني إلى Microsoft. 

بالإضافة إلى ذلك، لدى مؤسسات Microsoft 365 مع مسؤولي Microsoft Defender لنقطة النهاية العديد من الأساليب لإعداد التقارير عن الملفات.

|الاسلوب|الوصف|
|---|---|
|[استخدم مدخل عمليات الإرسال لإرسال البريد العشوائي والتصيد الاحتيالي وعناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md)|أسلوب إعداد التقارير الموصى به للمسؤولين في المؤسسات التي تحتوي على علب بريد Exchange Online (غير متوفر في EOP مستقل).|
|[تمكين الوظيفة الإضافية "رسالة التقرير" أو الوظائف الإضافية "تصيد التقرير"](enable-the-report-message-add-in.md)|يعمل مع Outlook و Outlook على ويب (المعروف سابقا باسم Outlook Web App). <br/><br/> استنادا إلى اشتراكك، تتوفر الرسائل التي أبلغ عنها المستخدمون باستخدام الوظائف الإضافية في [مدخل مسؤول عمليات الإرسال](admin-submission.md) [ونتائج التحقيق والاستجابة التلقائية (AIR)](air-view-investigation-results.md) [وتقرير الرسائل التي أبلغ عنها المستخدم](view-email-security-reports.md#user-reported-messages-report) [والمستكشف](threat-explorer-views.md#email--submissions). <br/><br/> يمكنك تكوين الرسائل التي تم الإبلاغ عنها ليتم نسخها أو إعادة توجيهها إلى علبة بريد تحددها. لمزيد من المعلومات، راجع [نهج عمليات إرسال المستخدم](user-submission.md).
|[الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook](report-false-positives-and-false-negatives.md)|أرسل الإيجابيات الخاطئة (البريد الإلكتروني الجيد الذي تم حظره أو إرساله إلى مجلد غير هام) والسلبيات الخاطئة (البريد الإلكتروني غير المرغوب فيه أو التصيد الاحتيالي الذي تم تسليمه إلى علبة الوارد) إلى Exchange Online Protection (EOP) باستخدام ميزة "رسالة التقرير".|
|[استخدام قواعد تدفق البريد لمعرفة المستخدمين الذين يبلغون إلى Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|تعرف على كيفية إنشاء قاعدة تدفق بريد (تعرف أيضا باسم قاعدة النقل) التي تعلمك عندما يقوم المستخدمون بالإبلاغ عن الرسائل إلى Microsoft للتحليل.|
|[إرسال البرامج الضارة وغير الضارة إلى Microsoft للتحليل](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|استخدم موقع التحليل الذكي لمخاطر الأمان من Microsoft لإرسال المرفقات والملفات الأخرى.|

> [!NOTE]
> عند الإبلاغ عن كيان بريد إلكتروني إلى Microsoft، نقوم بعمل نسخة من كل شيء مقترن بالبريد الإلكتروني لتضمينه في مراجعات الخوارزمية المستمرة. تتضمن هذه النسخة محتوى البريد الإلكتروني ورؤوس البريد الإلكتروني والبيانات ذات الصلة حول توجيه البريد الإلكتروني. كما يتم تضمين المرفقات في الرسالة.
>
> تتعامل Microsoft مع ملاحظاتك كإذن من مؤسستك لتحليل جميع المعلومات الموضحة مسبقا والعمل على ضبط خوارزميات حماية الرسائل. نحن نحتفظ برسالتك في مراكز البيانات المدققة الآمنة لدينا في الولايات المتحدة الأمريكية حتى نحذف عمليات الإرسال الخاصة بك في وقت لا يتجاوز 30 يوما بعد تقديمها لنا. يمكن للموظفين في Microsoft قراءة الرسالة والمرفقات المرسلة، والتي لا يسمح بها عادة للبريد الإلكتروني في Office 365. ومع ذلك، لا يزال يتم التعامل مع بريدك الإلكتروني على أنه سري بينك وبين Microsoft، ولن نقدم عمليات الإرسال إلى أي جهة أخرى لقراءة البريد الإلكتروني أو مرفقاته لعملية المراجعة هذه.
