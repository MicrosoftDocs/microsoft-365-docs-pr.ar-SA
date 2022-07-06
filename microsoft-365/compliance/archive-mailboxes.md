---
title: التعرف على علب بريد الأرشيف ل Microsoft Purview
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
ms.openlocfilehash: 57de7c7791615e8587222de992588f1923348059
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621238"
---
# <a name="learn-about-archive-mailboxes"></a>التعرّف على علب بريد الأرشيف

توفر أرشفة علبة البريد في Microsoft 365 (تسمى أيضا *الأرشفة الموضعية*) للمستخدمين مساحة تخزين إضافية لعلب البريد. بعد تشغيل علب بريد الأرشيف، تصبح علبة البريد الحالية للمستخدم *علبة البريد الأساسية* ويتم إنشاء علبة بريد إضافية تسمى *علبة بريد الأرشيف*. تعتبر علبة البريد علبة بريد المستخدم لميزات التوافق مثل البحث في المحتوى من مدخل التوافق في Microsoft Purview واستبقاء Microsoft 365 و"احتجاز التقاضي".

يمكن للمستخدمين الوصول إلى الرسائل وتخزينها في علب بريد الأرشيف الخاصة بهم باستخدام Outlook Outlook على ويب. يمكن للمستخدمين أيضا نقل الرسائل أو نسخها بين علبة البريد الأساسية وعلبة بريد الأرشيف الخاصة بهم. يمكنهم أيضا استرداد العناصر المحذوفة من مجلد العناصر القابلة للاسترداد في علبة بريد الأرشيف الخاصة بهم باستخدام أداة استرداد العناصر المحذوفة.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>إدارة علب بريد الأرشيف باستخدام إدارة سجلات المراسلة (MRM)

يمكن أيضا نقل الرسائل إلى علبة بريد الأرشيف بواسطة [نهج استبقاء Exchange الافتراضي](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) من إدارة سجلات المراسلة (MRM). يتم تعيين هذا النهج الافتراضي تلقائيا إلى كل علبة بريد ويقوم بالتالي:

  - نقل العناصر التي يزيد عمرها عن عامين أو أكثر من علبة البريد الأساسية للمستخدم إلى علبة بريد الأرشيف الخاصة به.

  - نقل العناصر التي يبلغ عمرها 14 يوما أو أكثر من مجلد "العناصر القابلة للاسترداد" في علبة البريد الأساسية للمستخدم إلى مجلد "العناصر القابلة للاسترداد" في علبة بريد الأرشيف الخاصة به.

يمكنك تخصيص نهج MRM الخاص بمؤسستك باستخدام [علامات الاستبقاء](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). للحصول على مثال على التكوين، راجع [إعداد نهج الأرشيف والحذف لعلب البريد في مؤسستك](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

> [!NOTE]
> يمكن ل MRM، مثل نهج الاستبقاء وتسميات الاستبقاء في Microsoft 365، حذف رسائل البريد الإلكتروني تلقائيا بعد فترة محددة. كتقنية أقدم من استبقاء Microsoft 365، يستمر MRM في العمل جنبا إلى جنب مع نهج الاستبقاء وتسميات الاستبقاء من Microsoft Purview. لمزيد من المعلومات، راجع [استخدام نهج الاستبقاء وتسميات الاستبقاء بدلا من الميزات القديمة](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>الأرشفة ذات التوسيع التلقائي 

بعد تمكين علبة بريد الأرشيف الخاصة بالمستخدم، يتوفر ما يصل إلى 100 غيغابايت من مساحة التخزين الإضافية. إذا احتاج المستخدمون إلى مساحة تخزين إضافية، فتمكن من التوسيع التلقائي للأرشفة لتوفير ما يصل إلى 1.5 تيرابايت من مساحة التخزين الإضافية في علب بريد الأرشيف. لمزيد من المعلومات، راجع [التعرف على التوسيع التلقائي للأرشفة](autoexpanding-archiving.md).

## <a name="licensing"></a>الترخيص

للحصول على قائمة بتراخيص Outlook التي تدعم علب بريد الأرشيف، راجع المراجع إلى In-Place متطلبات [ترخيص Outlook لميزات Exchange](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>الخطوات التالية

راجع [تمكين علب بريد الأرشيف في مدخل التوافق في Microsoft Purview](enable-archive-mailboxes.md).
