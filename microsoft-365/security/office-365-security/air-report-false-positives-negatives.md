---
title: كيفية الإبلاغ عن الإيجابيات الخاطئة أو السلبيات الخاطئة بعد إجراء تحقيق تلقائي في Microsoft Defender Office 365
description: هل حدث خطأ ما أو تم اكتشافه عن طريق AIR في Microsoft Defender Office 365؟ تعرف على كيفية إرسال الإيجابيات الخاطئة أو السلبيات الخاطئة إلى Microsoft لتحليلها.
keywords: تلقائي، تحقيق، تنبيه، مشغل، إجراء، معالجة، خطأ موجب، سالب خطأ
search.appverid: met150
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
ms.prod: m365-security
ms.date: 01/29/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.topic: how-to
ms.custom:
- autoir
ms.technology: mdo
ms.openlocfilehash: 4b1de0e19cbf241936aa02f957cdd0920f2a580a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682472"
---
# <a name="how-to-report-false-positivesnegatives-in-automated-investigation-and-response-capabilities"></a>كيفية الإبلاغ عن الإيجابيات/السلبيات الخاطئة في قدرات الاستجابة والتحريات التلقائية

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

إذا [فاتت قدرات الاستجابة (AIR)](automated-investigation-response-office.md) Office 365 أو اكتشفت خطأ ما، فهناك خطوات يمكن لفريق عمليات الأمان اتخاذها لإصلاح ذلك. تتضمن هذه الإجراءات ما يلي:

- [الإبلاغ عن خطأ موجب/سالب ل Microsoft](#report-a-false-positivenegative-to-microsoft-for-analysis)؛
- [ضبط التنبيهات](#adjust-an-alert-to-prevent-false-positives-from-recurring) (إذا لزم الأمر)؛ و
- [التراجع عن إجراءات الإصلاح التي تم اتخاذها](#undo-a-remediation-action).

استخدم هذه المقالة كدليل.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>الإبلاغ عن خطأ موجب/سالب إلى Microsoft لتحليله

إذا فات AIR في Microsoft Defender for Office 365 رسالة بريد إلكتروني أو مرفق بريد إلكتروني أو عنوان URL في رسالة بريد إلكتروني أو عنوان URL في ملف Office، يمكنك إرسال رسائل البريد العشوائي والتصيد الاحتيالي عناوين URL والملفات المشتبه بها إلى [Microsoft لمسح Office 365](admin-submission.md) ضوئيا.

يمكنك أيضا [إرسال ملف إلى Microsoft لتحليل البرامج الضارة](https://www.microsoft.com/wdsi/filesubmission).

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>ضبط تنبيه لمنع تكرار الإيجابيات الخاطئة

إذا تم تشغيل تنبيه باستخدام شرعي، أو إذا كان التنبيه غير دقيق، يمكنك إدارة التنبيهات في مدخل [Defender for Cloud Apps](/cloud-app-security/managing-alerts).

إذا كانت مؤسستك تستخدم [Microsoft Defender لنقطة](/windows/security/threat-protection) النهاية بالإضافة إلى Office 365، وكان يتم التعامل مع ملف أو عنوان IP أو URL أو مجال كبرامج ضارة على جهاز، على الرغم من أنه آمن، يمكنك إنشاء مؤشر مخصص باستخدام إجراء ["السماح" لجهازك](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators).

## <a name="undo-a-remediation-action"></a>التراجع عن إجراء إصلاحي

في معظم الحالات، إذا تم اتخاذ إجراء إصلاح على رسالة بريد إلكتروني أو مرفق بريد إلكتروني أو URL، وكان العنصر في الواقع لا يشكل خطرا، يمكن لفريق عمليات الأمان التراجع عن إجراء الإصلاح واتخاذ خطوات لمنع تكرار الإيجابيات الخاطئة. يمكنك إما استخدام "مستكشف [التهديدات](#undo-an-action-using-threat-explorer) " أو علامة التبويب ["إجراءات" للحصول على تحقيق](#undo-an-action-in-the-action-center) للتراجع عن إجراء ما.

> [!IMPORTANT]
> تأكد من أن لديك الأذونات اللازمة قبل محاولة تنفيذ المهام التالية.

### <a name="undo-an-action-using-threat-explorer"></a>التراجع عن إجراء باستخدام "مستكشف التهديدات"

باستخدام "مستكشف التهديدات"، يمكن لفريق عمليات الأمان العثور على رسالة بريد إلكتروني متأثرة بما تم اتخاذه من إجراء والتراجع عن الإجراء.

|السيناريو|خيارات التراجع|التعرف على المزيد|
|---|---|---|
|تم توجيه رسالة بريد إلكتروني إلى مجلد البريد الإلكتروني غير الهام الخاص بالمستخدم|<ul><li>نقل الرسالة إلى مجلد "العناصر المحذوفة" الخاص بالمستخدم</li><li>نقل الرسالة إلى علبة وارد المستخدم</li><li>حذف الرسالة</li></ul>|[البحث عن البريد الإلكتروني الضار الذي تم تسليمه في Office 365](investigate-malicious-email-that-was-delivered.md)|
|تم فحص رسالة بريد إلكتروني أو ملف|<ul><li>تحرير البريد الإلكتروني أو الملف</li><li> حذف البريد الإلكتروني أو الملف</li></ul>|[إدارة الرسائل المعزولة كمسؤول](manage-quarantined-messages-and-files.md)|

### <a name="undo-an-action-in-the-action-center"></a>التراجع عن إجراء في مركز الإجراءات

في مركز الإجراءات، يمكنك رؤية إجراءات الإصلاح التي تم اتخاذها والتراجع عن الإجراء المحتمل.

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى مركز الإجراءات عن طريق تحديد **مركز الإجراءات**. للذهاب مباشرة إلى مركز الإجراءات، استخدم <https://security.microsoft.com/action-center/>.
2. في مركز الإجراءات، حدد علامة **التبويب محفوظات** لعرض قائمة الإجراءات المكتملة.
3. حدد أحد العناصر. يفتح جزء منتفطها.
4. في جزء منتحل، حدد **تراجع**. (الإجراءات التي يمكن التراجع عنها فقط هي التي سيكون لها زر **تراجع** .)

## <a name="see-also"></a>راجع أيضًا

- [Microsoft Defender Office 365](defender-for-office-365.md)
- [عمليات التحقيق التلقائية في Microsoft Defender Office 365](office-365-air.md)
