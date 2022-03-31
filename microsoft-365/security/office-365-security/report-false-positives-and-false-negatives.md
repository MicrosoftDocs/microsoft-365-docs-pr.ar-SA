---
title: الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: تعرف على كيفية الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook باستخدام ميزة "رسالة التقرير".
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e5539525b6d752223c4895fc62ff49a90768a5b5
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63578205"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> إذا كنت مسؤول في مؤسسة Microsoft 365 بها علب بريد Exchange Online، فإننا ننصحك باستخدام صفحة "الواجبات المرسلة" في Microsoft 365 Defender المدخل. لمزيد من المعلومات، راجع [استخدام مدخل](admin-submission.md) عمليات الإرسال لإرسال ملفات البريد العشوائي والتصيد الاحتيالي عناوين URL والملفات المشتبه بها إلى Microsoft.

في مؤسسات Microsoft 365 التي بها علب بريد في علب بريد Exchange Online أو علب بريد المحلية باستخدام المصادقة الحديثة المختلطة، يمكنك إرسال إيجابيات خاطئة (بريد إلكتروني جيد تم حظره أو إرساله إلى مجلد غير هام) وسلبيات خاطئة (بريد إلكتروني غير مرغوب فيه أو تصيد احتيالي تم تسليمه إلى علبة الوارد) إلى Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- للحصول على أفضل تجربة إرسال للمستخدم، استخدم الوظائف الإضافية "رسالة التقرير" أو "الإبلاغ عن التصيد الاحتيالي".

- تعمل الوظائف الإضافية "رسالة التقرير" والرسالة الإضافية "الإبلاغ عن التصيد الاحتيالي" Outlook في كل الأنظمة الأساسية (Outlook على ويب و iOS وAndroid وسطح المكتب).

- إذا كنت أحد المسؤولين في مؤسسة Exchange Online علب البريد، فاستخدم مدخل الواجبات المرسلة في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [استخدام إرسال المسؤول لإرسال](admin-submission.md) ملفات البريد العشوائي والتصيد الاحتيالي عناوين URL والملفات المشتبه بها إلى Microsoft.

- يمكنك تكوين لإرسال الرسائل مباشرة إلى Microsoft أو علبة بريد تحددها أو كليهما. لمزيد من المعلومات، راجع [سياسات إرسال المستخدم.](user-submission.md)

- لمزيد من المعلومات حول كيفية الحصول على "رسالة التقرير" أو الوظائف الإضافية "الإبلاغ عن التصيد الاحتيالي" وتمكينها، راجع تمكين "رسالة التقرير" أو الوظائف الإضافية "الإبلاغ عن التصيد [الاحتيالي](enable-the-report-message-add-in.md)".

- لمزيد من المعلومات حول إرسال رسائل إلى Microsoft، راجع [الإبلاغ عن الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md).

### <a name="turn-off-the-built-in-reporting-experience"></a>إيقاف تشغيل تجربة إعداد التقارير المضمنة

لا نوصي باستخدام تجربة إعداد التقارير المضمنة في Outlook لأنه لا يمكن استخدام نهج [إرسال المستخدم](./user-submission.md). نوصي باستخدام الوظائف الإضافية "الإبلاغ عن رسالة" أو "الإبلاغ عن التصيد الاحتيالي" بدلا من ذلك.

يجب عليك تعيين الأذونات لكي تتمكن من تشغيل cmdlet هذا. للعثور على الأذونات المطلوبة لتشغيل أي cmdlet أو معلمة في مؤسستك، راجع البحث عن الأذونات المطلوبة لتشغيل أي Exchange [cmdlet](/powershell/exchange/find-exchange-cmdlet-permissions).

قم بتشغيل الأمر PowerShell التالي لتعطيل تجربة إعداد التقارير المضمنة في Outlook على ويب:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```


## <a name="use-the-report-message-feature"></a>استخدام ميزة "رسالة التقرير"

### <a name="report-junk-and-phishing-messages"></a>الإبلاغ عن رسائل البريد الإلكتروني غير الهام والتصيد الاحتيالي

للرسائل في علبة الوارد أو أي مجلد بريد إلكتروني آخر باستثناء البريد الإلكتروني غير الهام، استخدم الطريقة التالية للتقارير حول رسائل البريد العشوائي والتصيد الاحتيالي:

1. حدد المزيد **من** الإجراءات في الزاوية العلوية اليسرى من الرسالة المحددة، وحدد الإبلاغ عن رسالة من القائمة  المنسدلة، **ثم حدد البريد** الإلكتروني غير الهام أو **التصيد الاحتيالي**.

   ![رسالة التقرير - مزيد من الإجراءات.](../../media/report-message-more-actions.png)

   ![رسالة التقرير - البريد الإلكتروني غير الهام والتصيد الاحتيالي.](../../media/report-message-junk-phishing.png)

2. سيتم إرسال الرسائل المحددة إلى Microsoft لتحليلها و:
   - تم نقلها إلى مجلد البريد الإلكتروني غير الهام إذا تم إرسال التقارير عنها كبريد عشوائي.
   - محذوف إذا تم إعلامه بالتصيد الاحتيالي.

### <a name="report-messages-that-are-not-junk"></a>الإبلاغ عن الرسائل غير المرغوب فيها

1. حدد المزيد **من** الإجراءات في الزاوية العلوية اليسرى من الرسالة المحددة، وحدد الإبلاغ عن رسالة من القائمة  المنسدلة، ثم حدد **ليس غير هام**.

   ![رسالة التقرير - مزيد من الإجراءات.](../../media/report-message-more-actions.png)

   ![رسالة التقرير - ليست غير هام.](../../media/report-message-not-junk.png)

2. سيتم إرسال الرسالة المحددة إلى Microsoft لتحليلها، كما سيتم نقلها إلى علبة الوارد أو أي مجلد محدد آخر.

## <a name="view-and-review-reported-messages"></a>عرض الرسائل التي تم إرسالها ومراجعتها

لمراجعة الرسائل التي يقوم المستخدمون بلتقاريرها إلى Microsoft، تتوفر لديك هذه الخيارات:

- استخدم **صفحة** الواجبات المرسلة في Microsoft 365 Defender المدخل. لمزيد من المعلومات، راجع [عرض إرسالات المستخدمين إلى Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- إنشاء قاعدة تدفق بريد (تعرف أيضا باسم قاعدة النقل) لإرسال نسخ من الرسائل التي تم إرسالها. للحصول على الإرشادات، راجع [استخدام قواعد تدفق البريد لمعرفة ما يقوم المستخدمون بالإبلاغ عنه إلى Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
