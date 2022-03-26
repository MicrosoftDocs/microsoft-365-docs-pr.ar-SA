---
title: معالجة الإيجابيات الخاطئة أو السلبيات الخاطئة في Microsoft 365 Defender
description: هل فات شيء ما أو تم اكتشافه عن طريق الخطأ بواسطة AIR في Microsoft 365 Defender؟ تعرف على كيفية إرسال الإيجابيات الخاطئة أو السلبيات الخاطئة إلى Microsoft لتحليلها.
keywords: تلقائي، تحقيق، تنبيه، إصلاح، خطأ موجب، سالب خطأ
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 67246d7f7876457e6553818b469987a2b5a59eb0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569797"
---
# <a name="address-false-positives-or-false-negatives-in-microsoft-365-defender"></a>معالجة الإيجابيات الخاطئة أو السلبيات الخاطئة في Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**
- Microsoft 365 Defender

يمكن أن تحدث السلبيات أو الإيجابيات الخاطئة أحيانا مع أي حل للحماية من المخاطر. إذا [كانت قدرات](m365d-autoir.md) الاستجابة والتحريات التلقائية Microsoft 365 Defender أو اكتشفت خطأ ما، فهناك خطوات يمكن لفريق عمليات الأمان اتخاذها:

- [الإبلاغ عن خطأ موجب/سالب إلى Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis)
- [ضبط التنبيهات](#adjust-an-alert-to-prevent-false-positives-from-recurring) (إذا لزم الأمر)
- [التراجع عن إجراءات المعالجة التي تم اتخاذها على الأجهزة](#undo-a-remediation-action-that-was-taken-on-a-device)

تصف الأقسام التالية كيفية تنفيذ هذه المهام.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>الإبلاغ عن خطأ موجب/سالب إلى Microsoft لتحليله

|عنصر فات أو تم اكتشافه بشكل غير صحيح |الخدمة  |ما يجب فعله  |
|---------|---------|---------|
|- رسالة بريد إلكتروني <br/>- مرفق البريد الإلكتروني <br/>- عنوان URL في رسالة بريد إلكتروني<br/>- عنوان URL في Office ملف      |[Microsoft Defender Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)        |[إرسال البريد العشوائي والتصيد الاحتيالي عناوين URL والملفات المشتبه بها إلى Microsoft للمسح الضوئي](../office-365-security/admin-submission.md)         |
|ملف أو تطبيق على جهاز    |[Microsoft Defender لنقطة النهاية](/windows/security/threat-protection)         |[إرسال ملف إلى Microsoft لتحليل البرامج الضارة](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>ضبط تنبيه لمنع تكرار الإيجابيات الخاطئة

|السيناريو |الخدمة |ما يجب فعله |
|--------|--------|--------|
|- يتم تشغيل التنبيه باستخدام شرعي <br/>- التنبيه غير دقيق    |[Microsoft Defender لتطبيقات السحابة](/cloud-app-security)<br/> أو <br/>[الحماية من المخاطر في Azure](/azure/security/fundamentals/threat-detection)         |[إدارة التنبيهات في مدخل Defender for Cloud Apps](/cloud-app-security/managing-alerts)         |
|يتم التعامل مع ملف أو عنوان IP أو URL أو مجال كبرامج ضارة على جهاز، على الرغم من أنه آمن|[Microsoft Defender لنقطة النهاية](/windows/security/threat-protection) |[إنشاء مؤشر مخصص باستخدام إجراء "السماح"](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>التراجع عن إجراء إصلاحي تم اتخاذه على جهاز

إذا تم اتخاذ إجراء إصلاح على كيان (مثل جهاز أو رسالة بريد إلكتروني) ولم يكن الكيان المتأثر في الواقع يشكل خطرا، يمكن لفريق عمليات الأمان التراجع عن إجراء الإصلاح في [مركز الإجراءات](m365d-action-center.md).

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender المدخل ثم</a> سجل الدخول. 
2. في جزء التنقل، اختر **مركز الإجراءات**. 
3. على علامة **التبويب** محفوظات، حدد إجراء تريد التراجع عنه. يفتح جزء منتفطها.
4. في جزء منتحل، حدد **تراجع**.

> [!TIP]
> راجع [التراجع عن الإجراءات المكتملة](m365d-autoir-actions.md#undo-completed-actions).

## <a name="see-also"></a>راجع أيضًا

- [عرض تفاصيل ونتائج التحقيق التلقائي](m365d-autoir-results.md)
- [البحث الاستباقي عن التهديدات باستخدام الصيد المتقدم في Microsoft 365 Defender](advanced-hunting-overview.md)
