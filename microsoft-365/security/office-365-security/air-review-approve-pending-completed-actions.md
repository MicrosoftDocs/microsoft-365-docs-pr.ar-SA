---
title: مراجعة إجراءات الإصلاح وإدارتها في Microsoft Defender Office 365
keywords: AIR، autoIR، Microsoft Defender ل Endpoint، تلقائي، تحقيق، استجابة، معالجة، تهديدات، متقدم، خطر، حماية
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: تعرف على إجراءات المعالجة في قدرات الاستجابة والتحريات التلقائية في Microsoft Defender Office 365 الخطة 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: 35e9293fa83b86fb80c1c907fbf3a0769e323503
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567821"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>مراجعة إجراءات الإصلاح وإدارتها في Office 365

**ينطبق على**
- [Microsoft Defender Office 365 2](defender-for-office-365.md)

بما أنه يتم إجراء عمليات تحقيق تلقائية & البريد الإلكتروني، فإن محتوى التعاون يؤدي إلى اتخاذ قرار، مثل ضار أو مريب، يتم إنشاء إجراءات إصلاح معينة. في Microsoft Defender Office 365، يمكن أن تتضمن إجراءات المعالجة ما يلي:

- حذف رسائل البريد الإلكتروني أو المجموعات بشكل تلقائي
- إيقاف تشغيل إعادة توجيه البريد الخارجي

لا يتم اتخاذ إجراءات الإصلاح هذه إلا إذا وافق عليها فريق عمليات الأمان ونهاية الوقت. نوصي بمراجعة أي إجراءات معلقة وموافقتها في أسرع وقت ممكن بحيث تكتمل عمليات التحقيق التلقائية في الوقت المناسب. في بعض الحالات، يمكنك إعادة النظر في الإجراءات التي تم إرسالها.  يجب أن تكون جزءا من دور & البحث قبل اتخاذ أي إجراءات.

## <a name="approve-or-reject-pending-actions"></a>الموافقة على الإجراءات المعلقة (أو رفضها)

هناك أربع طرق مختلفة للعثور على إجراءات التحقيق التلقائية واتخاذها:

- [قائمة انتظار الأحداث](https://security.microsoft.com/incidents)
- التحقيق بحد ذاته (يتم الوصول إليه عبر "حادث" أو "تنبيه")
- [مركز الإجراءات](https://security.microsoft.com/action-center/pending)
- [قائمة انتظار التحقيق والوساطة](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>قائمة انتظار الأحداث

1. في مدخل Microsoft 365 Defender ، <https://security.microsoft.com>انتقل إلى صفحة الأحداث في أحداث  **& تنبيهات** \> **الأحداث**. الانتقال مباشرة إلى صفحة " **الأحداث** "، استخدم <https://security.microsoft.com/incidents>.
2. في صفحة **الأحداث** ، حدد اسم حادث لفتح صفحة التلخيص الخاصة به.
3. حدد علامة **التبويب دليل والاستجابة** .
4. حدد عنصر في القائمة. يفتح جزءه الجانبي.
5. في الجزء الجانبي، اتخاذ إجراءات الموافقة أو الرفض.

## <a name="action-center"></a>مركز الإجراءات

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى صفحة **مركز** الإجراءات عن طريق تحديد **مركز الإجراءات**. الانتقال مباشرة إلى صفحة **مركز الإجراءات** ، استخدم <https://security.microsoft.com/action-center/pending>.
2. في **صفحة مركز الإجراءات**، تحقق من تحديد علامة  التبويب معلق، ثم راجع قائمة الإجراءات التي تنتظر الموافقة.
   - حدد **فتح صفحة التحقيق** لعرض مزيد من التفاصيل حول التحقيق.
   - حدد **موافقة** لبدء إجراء معلق.
   - حدد **رفض** لمنع اتخاذ إجراء معلق.

## <a name="investigation-and-remediation-investigations-queue"></a>قائمة انتظار التحقيق والوساطة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى صفحة التحقيق **في** التهديدات في **البريد الإلكتروني & التعاون** \> **في العمل**. الانتقال مباشرة إلى صفحة التحقيق **في التهديدات** ، استخدم <https://security.microsoft.com/airinvestigation>.
2. في صفحة **التحقيق في التهديدات** ، ابحث عن عنصر من القائمة التي تكون الحالة فيها **قيد الانتظار**.
3. انقر ![فوق فتح في أيقونة نافذة جديدة.](../../media/m365-cc-sc-open-icon.png) **فتح في نافذة جديدة** في وقت القائمة (بين **الم ID** و **"الحالة"**).
4. في الصفحة التي يتم فتحها، اتخاذ إجراءات الموافقة أو الرفض.

## <a name="change-or-undo-one-remediation-action"></a>تغيير إجراء إصلاحي واحد أو التراجع عنه

هناك طريقتان مختلفتان لإعادة النظر في الإجراءات التي تم إرسالها:

- من [خلال مركز الإجراءات الموحد](https://security.microsoft.com/action-center).
- على الرغم [Office مركز الإجراءات](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>تغيير مركز الإجراءات الموحد أو التراجع عنه

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى مركز الإجراءات الموحد عن طريق تحديد **مركز الإجراءات**. للذهاب مباشرة إلى مركز الإجراءات الموحد، استخدم <https://security.microsoft.com/action-center/>.
2. في **صفحة مركز الإجراءات** ، حدد علامة **التبويب محفوظات** ، ثم حدد الإجراء الذي تريد تغييره أو التراجع عنه.
3. في الجزء على الجانب الأيسر من الشاشة، حدد الإجراء **المناسب (الانتقال** إلى علبة الوارد أو الانتقال إلى البريد غير الهام أو الانتقال إلى العناصر المحذوفة أو الحذف الناعم أو **الحذف الثابت**). 

## <a name="change-or-undo-through-the-office-action-center"></a>تغيير مركز Office أو التراجع عنه

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى مركز Office الإلكتروني في **مركز** \> & **مراجعة** \> **التعاون**. للذهاب مباشرة إلى مركز Office، استخدم <https://security.microsoft.com/threatincidents>.
2. في صفحة **مركز الإجراءات** ، حدد المعالجة المناسبة.
3. في اللوحة الجانبية، انقر فوق إدخال إرسالات البريد وانتظر حتى يتم تحميل القائمة.
4. انتظر حتى يتم تمكين الزر إجراء في الأعلى وحدد الزر إجراء لتغيير نوع الإجراء.
5. سينشئ ذلك الإجراءات المناسبة.

## <a name="next-steps"></a>الخطوات التالية

- [استخدام "مستكشف التهديدات"](threat-explorer.md)
- [المسؤول/الإجراءات اليدوية](remediate-malicious-email-delivered-office-365.md)
- [كيفية الإبلاغ عن الإيجابيات/السلبيات الخاطئة في قدرات الاستجابة والتحريات التلقائية](air-report-false-positives-negatives.md)

## <a name="see-also"></a>راجع أيضًا

- [عرض تفاصيل ونتائج التحقيق التلقائي في Office 365](air-view-investigation-results.md)
