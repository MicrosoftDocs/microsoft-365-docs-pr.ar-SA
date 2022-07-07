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
ms.openlocfilehash: 5955f6b5c4e376f296dcdad2d54a627bbcce04c3
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/07/2022
ms.locfileid: "66685668"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة في Outlook

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> إذا كنت مسؤولا في مؤسسة Microsoft 365 مع علب بريد Exchange Online، نوصي باستخدام صفحة **عمليات الإرسال** في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [استخدام مدخل عمليات الإرسال لإرسال البريد العشوائي والتصيد الاحتيالي وعناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md).

في مؤسسات Microsoft 365 التي تحتوي على علب بريد في Exchange Online أو علب البريد المحلية باستخدام المصادقة الحديثة المختلطة، يمكنك إرسال إيجابيات خاطئة (بريد إلكتروني جيد تم حظره أو إرساله إلى مجلد غير هام) وسلبيات خاطئة (بريد إلكتروني غير مرغوب فيه أو تصيد احتيالي تم تسليمه إلى علبة الوارد) إلى Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- للحصول على أفضل تجربة إرسال للمستخدم، استخدم الوظيفة الإضافية "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي".

- تعمل الوظيفة الإضافية "رسالة التقرير" والوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" ل Outlook في جميع الأنظمة الأساسية (Outlook على ويب وiOS وAndroid وسطح المكتب).

- إذا كنت مسؤولا في مؤسسة بها علب بريد Exchange Online، فاستخدم مدخل عمليات الإرسال في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [استخدام مسؤول الإرسال لإرسال رسائل البريد العشوائي والتصيد الاحتيالي وعناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md).

- يمكنك التكوين لإرسال رسائل مباشرة إلى Microsoft أو علبة بريد تحددها أو كليهما. لمزيد من المعلومات، راجع [نهج عمليات إرسال المستخدم](user-submission.md).

- لمزيد من المعلومات حول كيفية الحصول على الوظيفة الإضافية "رسالة التقرير" أو الوظائف الإضافية "تصيد التقرير" وتمكينها، راجع [تمكين "رسالة التقرير" أو الوظائف الإضافية "الإبلاغ عن التصيد الاحتيالي](enable-the-report-message-add-in.md)".

- لمزيد من المعلومات حول الإبلاغ عن الرسائل إلى Microsoft، راجع ["إرسال تقارير عن الرسائل والملفات إلى Microsoft](report-junk-email-messages-to-microsoft.md)".

شاهد هذا الفيديو القصير لمعرفة كيفية استخدام Microsoft Defender لـ Office 365 للتحقق بسهولة من عمليات إرسال المستخدم لتحديد محتويات الرسالة، والاستجابة للإرسال من خلال تطبيق إجراء المعالجة المناسب. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBHof]

> [!IMPORTANT]
> لعرض الرسائل التي تم الإبلاغ عنها إلى Microsoft على علامة تبويب **الرسائل التي أبلغ عنها المستخدم** ، <https://security.microsoft.com/reportsubmission>لا توقف تشغيل تجربة إعداد التقارير المضمنة.

## <a name="use-the-report-message-feature"></a>استخدام ميزة "رسالة التقرير"

### <a name="report-junk-and-phishing-messages"></a>الإبلاغ عن رسائل البريد الإلكتروني غير الهام والتصيد الاحتيالي

بالنسبة للرسائل الموجودة في علبة الوارد أو أي مجلد بريد إلكتروني آخر باستثناء البريد الإلكتروني غير الهام، استخدم الطريقة التالية للإبلاغ عن رسائل البريد العشوائي والتصيد الاحتيالي:

1. حدد **المزيد من الإجراءات** التي يتم حذفها في الزاوية العلوية اليسرى من الرسالة المحددة، وحدد **"تقرير الرسالة"** من القائمة المنسدلة، ثم حدد **"غير هام"** أو **"تصيد احتيالي**".

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="أيقونة الإجراءات الإضافية" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="الخيار &quot;البريد غير الهام والتصيد الاحتيالي&quot; في جزء &quot;رسالة التقرير&quot;" lightbox="../../media/report-message-junk-phishing.png":::

2. سيتم إرسال الرسائل المحددة إلى Microsoft لتحليلها و:
   - يتم نقلها إلى مجلد البريد الإلكتروني غير الهام إذا تم الإبلاغ عنها كبريد عشوائي.
   - يتم حذفها إذا تم الإبلاغ عنها على أنها تصيد احتيالي.

### <a name="report-messages-that-are-not-junk"></a>الإبلاغ عن الرسائل غير الهامة

1. حدد علامات الحذف " **المزيد من الإجراءات** " في الزاوية العلوية اليسرى من الرسالة المحددة، وحدد **"تقرير الرسالة** " من القائمة المنسدلة، ثم حدد **"ليس غير هام**".

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="الأيقونة التي توفر المزيد من الإجراءات" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="الخيار &quot;ليس غير هام&quot; ضمن جزء &quot;رسالة التقرير&quot;" lightbox="../../media/report-message-not-junk.png":::

2. سيتم إرسال الرسالة المحددة إلى Microsoft لتحليلها ونقلها إلى علبة الوارد أو أي مجلد محدد آخر.

## <a name="view-and-review-reported-messages"></a>عرض الرسائل التي تم الإبلاغ عنها ومراجعتها

لمراجعة الرسائل التي يبلغها المستخدمون إلى Microsoft، تتوفر لديك هذه الخيارات:

- استخدم صفحة **عمليات الإرسال** في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع [عرض عمليات إرسال المستخدم إلى Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- إنشاء قاعدة تدفق بريد (تعرف أيضا باسم قاعدة النقل) لإرسال نسخ من الرسائل التي تم الإبلاغ عنها. للحصول على الإرشادات، راجع [استخدام قواعد تدفق البريد للاطلاع على المستخدمين الذين يقومون بالإبلاغ إلى Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
