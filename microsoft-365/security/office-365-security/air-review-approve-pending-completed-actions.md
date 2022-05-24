---
title: مراجعة إجراءات المعالجة وإدارتها في Microsoft Defender لـ Office 365
keywords: AIR، و autoIR، Microsoft Defender لنقطة النهاية، وأتمتة، والتحقيق، والاستجابة، والمعالجة، والتهديدات، والمتقدمة، والتهديدات، والحماية
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
description: تعرف على إجراءات المعالجة في قدرات التحقيق والاستجابة التلقائية في Microsoft Defender لـ Office 365 الخطة 2.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: aaa444a2bada254aeed83540aee361ed806ab0a0
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649110"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>مراجعة إجراءات المعالجة وإدارتها في Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على**
- [Microsoft Defender لـ Office 365 الخطة 2](defender-for-office-365.md)

نظرا لأن التحقيقات التلقائية على البريد الإلكتروني & محتوى التعاون تؤدي إلى أحكام، مثل *الضارة* أو *المشبوهة*، يتم إنشاء إجراءات معالجة معينة. في Microsoft Defender لـ Office 365، يمكن أن تتضمن إجراءات المعالجة ما يلي:

- حذف مبدئي لرسائل البريد الإلكتروني أو المجموعات
- إيقاف تشغيل إعادة توجيه البريد الخارجي

لا يتم اتخاذ إجراءات المعالجة هذه إلا إذا وافق عليها فريق عمليات الأمان وحتى يوافق عليها. نوصي بمراجعة أي إجراءات معلقة والموافقة عليها في أقرب وقت ممكن بحيث تكتمل تحقيقاتك التلقائية في الوقت المناسب. في بعض الحالات، يمكنك إعادة النظر في الإجراءات المرسلة.  يجب أن تكون جزءا من البحث & دور الإزالة قبل اتخاذ أي إجراءات.

## <a name="approve-or-reject-pending-actions"></a>الموافقة على (أو رفض) الإجراءات المعلقة

هناك أربع طرق مختلفة للعثور على إجراءات التحقيق التلقائي واتخاذها:

- [قائمة انتظار الأحداث](https://security.microsoft.com/incidents)
- التحقيق نفسه (يتم الوصول إليه عبر الحدث أو من تنبيه)
- [مركز الصيانة](https://security.microsoft.com/action-center/pending)
- [قائمة انتظار تحقيقات التحقيق والمعالجة](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>قائمة انتظار الأحداث

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى صفحة **الحوادث** في **الحوادث & التنبيهات** \> **الحوادث**. للانتقال مباشرة إلى صفحة **الحوادث** ، استخدم <https://security.microsoft.com/incidents>.
2. في صفحة **الحوادث** ، حدد اسم الحدث لفتح صفحة الملخص الخاصة به.
3. حدد علامة التبويب **"دليل" و"استجابة** ".
4. حدد عنصرا في القائمة. يفتح الجزء الجانبي الخاص به.
5. في الجزء الجانبي، قم بالموافقة على الإجراءات أو رفضها.

## <a name="action-center"></a>مركز الصيانة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى صفحة **مركز الصيانة** عن طريق تحديد **مركز الصيانة**. للانتقال مباشرة إلى صفحة **مركز الصيانة** ، استخدم <https://security.microsoft.com/action-center/pending>.
2. في صفحة **مركز الصيانة** ، تحقق من تحديد علامة التبويب **"معلق** "، ثم راجع قائمة الإجراءات التي تنتظر الموافقة.
   - حدد **صفحة فتح التحقيق** لعرض مزيد من التفاصيل حول التحقيق.
   - حدد **"موافقة** " لبدء إجراء معلق.
   - حدد **"رفض** " لمنع اتخاذ إجراء معلق.

## <a name="investigation-and-remediation-investigations-queue"></a>قائمة انتظار تحقيقات التحقيق والمعالجة

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى صفحة **التحقيق في التهديدات** في **Email & collaboration** \> **Investigations**. للانتقال مباشرة إلى صفحة **التحقيق في التهديدات** ، استخدم <https://security.microsoft.com/airinvestigation>.
2. في صفحة **التحقيق في التهديدات** ، ابحث عن عنصر من القائمة وحالته **معلقة**.
3. انقر فوق ![أيقونة "فتح في نافذة جديدة".](../../media/m365-cc-sc-open-icon.png) **فتح في نافذة جديدة** في وقت القائمة (بين **المعرف** **والحالة**).
4. في الصفحة التي تفتح، قم بالموافقة على الإجراءات أو رفضها.

## <a name="change-or-undo-one-remediation-action"></a>تغيير إجراء معالجة واحد أو التراجع عنه

هناك طريقتان مختلفتان لإعادة النظر في الإجراءات المرسلة:

- من خلال [مركز الصيانة الموحد](https://security.microsoft.com/action-center).
- على الرغم من [Office مركز الصيانة](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>التغيير أو التراجع من خلال مركز الصيانة الموحد

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى مركز الصيانة الموحد عن طريق تحديد **مركز الصيانة**. للانتقال مباشرة إلى مركز الصيانة الموحد، استخدم <https://security.microsoft.com/action-center/>.
2. في صفحة **مركز الصيانة** ، حدد علامة التبويب " **محفوظات** "، ثم حدد الإجراء الذي تريد تغييره أو التراجع عنه.
3. في الجزء الموجود على الجانب الأيسر من الشاشة، حدد الإجراء المناسب (**الانتقال إلى علبة الوارد** أو **الانتقال إلى البريد غير الهام** أو **الانتقال إلى العناصر المحذوفة** أو **الحذف المبدئي** أو **الحذف الثابت**).

## <a name="change-or-undo-through-the-office-action-center"></a>تغيير مركز الصيانة Office أو التراجع عنه

1. في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى مركز الصيانة Office في **مركز إجراء** **مراجعة** \> التعاون \> **& البريد الإلكتروني**. للانتقال مباشرة إلى مركز الصيانة Office، استخدم <https://security.microsoft.com/threatincidents>.
2. في صفحة **مركز الصيانة** ، حدد المعالجة المناسبة.
3. في اللوحة الجانبية، انقر فوق إدخال عمليات إرسال البريد وانتظر حتى يتم تحميل القائمة.
4. انتظر حتى يتم تمكين الزر "إجراء" في الأعلى وحدد الزر "إجراء" لتغيير نوع الإجراء.
5. سيؤدي ذلك إلى إنشاء الإجراءات المناسبة.

## <a name="next-steps"></a>الخطوات التالية

- [استخدام مستكشف المخاطر](threat-explorer.md)
- [مسؤول /الإجراءات اليدوية](remediate-malicious-email-delivered-office-365.md)
- [كيفية الإبلاغ عن الإيجابيات/السلبيات الخاطئة في قدرات التحقيق والاستجابة التلقائية](air-report-false-positives-negatives.md)

## <a name="see-also"></a>راجع أيضًا

- [عرض تفاصيل ونتائج التحقيق التلقائي في Office 365](air-view-investigation-results.md)
