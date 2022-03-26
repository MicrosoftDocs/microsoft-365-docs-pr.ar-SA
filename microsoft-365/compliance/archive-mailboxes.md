---
title: التعرف على علب بريد الأرشيف Microsoft 365 التوافق
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: تعرف على علب بريد الأرشيف لتوفير مساحة تخزين إضافية لعلب البريد.
ms.openlocfilehash: a863df7be1b73d6a50d818bca5948f3017e3d373
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/27/2022
ms.locfileid: "63570936"
---
# <a name="learn-about-archive-mailboxes"></a>التعرف على علب بريد الأرشيف

توفر أرشفة علبة البريد في Microsoft 365 (تسمى أيضا الأرشفة في *مكان) للمستخدمين* مساحة تخزين إضافية لعلبة البريد. بعد تشغيل علب بريد الأرشيف، تصبح علبة البريد الحالية الخاصة بالمستخدم علبة البريد الأساسية  الخاصة به، كما يتم إنشاء علبة بريد إضافية تسمى *علبة بريد الأرشيف*. تعتبر علب البريد علب البريد الخاصة بالمستخدم لميزات التوافق مثل البحث في المحتوى من مركز التوافق في Microsoft 365 والاستبقاء Microsoft 365 والدعاوى القضائية.

يمكن للمستخدمين الوصول إلى الرسائل وتخزينها في علب بريد الأرشيف الخاصة بهم باستخدام Outlook Outlook على ويب. يمكن للمستخدمين أيضا نقل الرسائل أو نسخها بين علبة البريد الأساسية الخاصة بهم علبة بريد الأرشيف الخاصة بهم. يمكنهم أيضا استرداد العناصر المحذوفة من مجلد العناصر القابلة لاستردادها في علبة بريد الأرشيف الخاصة بهم باستخدام أداة استرداد العناصر المحذوفة.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>إدارة علب بريد الأرشيف باستخدام إدارة سجلات المراسلة (MRM)

يمكن أيضا نقل الرسائل إلى علبة بريد الأرشيف عن طريق نهج استبقاء Exchange [الافتراضي من إدارة](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) سجلات المراسلة (MRM). يتم تعيين هذا النهج الافتراضي تلقائيا إلى كل علبة بريد ويتبع ما يلي:

  - نقل العناصر التي يزيد عمرها عن عامين أو أكثر من علبة البريد الأساسية الخاصة بالمستخدم إلى علبة بريد الأرشيف الخاصة به.

  - نقل العناصر التي يزيد حجمها عن 14 يوما أو أكثر من مجلد العناصر القابلة لاستردادها في علبة بريد المستخدم الأساسية إلى مجلد العناصر القابلة لاستردادها في علبة بريد الأرشيف.

يمكنك تخصيص نهج MRM الخاص بالمنظمة باستخدام [علامات الاستبقاء](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). للحصول على تكوين على سبيل المثال، راجع [إعداد نهج الحذف والأرشيف لعلب البريد في مؤسستك](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

> [!NOTE]
> يمكن ل MRM، Microsoft 365 مثل سياسات الاستبقاء وتسميات الاستبقاء، حذف رسائل البريد الإلكتروني تلقائيا بعد فترة زمنية محددة. كتقنية قديمة Microsoft 365 الاستبقاء، تستمر MRM في العمل جنبا إلى جنب مع سياسات الاستبقاء وتسميات الاستبقاء من Microsoft 365 التوافق. لمزيد من المعلومات، راجع استخدام سياسات الاستبقاء [وتسميات الاستبقاء بدلا من الميزات القديمة](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>أرشفة التوسع التلقائي 

بعد تمكين علبة بريد الأرشيف الخاصة بالمستخدم، تتوفر مساحة تخزين إضافية تصل إلى 100 غيغابايت. إذا كان المستخدمون بحاجة إلى مساحة تخزين إضافية، فمكن أرشفة التوسع التلقائي لتوفير مساحة تخزين إضافية تصل إلى 1.5 تي TB في علب بريد الأرشيف. لمزيد من المعلومات، راجع [التعرف على أرشفة التوسع التلقائي](autoexpanding-archiving.md).

## <a name="licensing"></a>الترخيص

للحصول على قائمة بالتراخيص Outlook التي تدعم علب بريد الأرشيف، راجع مراجع In-Place الأرشفة في Outlook متطلبات ترخيص Exchange [الإضافية](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>الخطوات التالية

راجع [تمكين علب بريد الأرشيف في مركز التوافق](enable-archive-mailboxes.md).