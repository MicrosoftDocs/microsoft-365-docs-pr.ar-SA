---
title: إعلامات العزل (إعلامات البريد العشوائي للمستخدم النهائي) في Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين التعرف على إعلامات البريد العشوائي للمستخدم النهائي للرسائل المعزولة في Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: c1688e4a56787c9593aae7006a05d52b16558647
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393469"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>استخدام إعلامات العزل لإصدار الرسائل المعزولة والإبلاغ بها

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في المؤسسات Microsoft 365 التي تحتوي على علب بريد في Exchange Online أو مؤسسات Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online، يحتفظ العزل برسائل قد تكون خطرة أو غير مرغوب فيها. لمزيد من المعلومات، راجع [الرسائل المعزولة في EOP](quarantine-email-messages.md).

تحدد _نهج العزل_ ما يسمح للمستخدمين بالقيام به للرسائل المعزولة استنادا إلى سبب عزل الرسالة (للميزات المدعومة). لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md). تتحكم نهج العزل أيضا في ما إذا كان المستلمون المتأثرون (بما في ذلك علب البريد المشتركة) يتلقون _إعلامات عزل دورية_ حول رسائل العزل الخاصة بهم. تعد إعلامات العزل بديلا لإعلامات البريد العشوائي للمستخدم النهائي لجميع ميزات الحماية المدعومة (وليس فقط أحكام نهج مكافحة البريد العشوائي).

لا يتم تشغيل إعلامات العزل في إعلامات العزل المضمنة المسماة AdminOnlyAccessPolicy أو DefaultFullAccessPolicy. يتم تشغيل إعلامات العزل في نهج العزل المضمن المسمى NotificationEnabledPolicy [إذا كانت مؤسستك تملكه](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). وإلا، لتشغيل إعلامات العزل في نهج العزل، تحتاج إلى [إنشاء نهج عزل جديد وتكوينه](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

بالإضافة إلى ذلك، للسماح بخيار "حظر المرسل" في إعلامات العزل للعمل بشكل صحيح، يجب تمكين المستخدمين ل Powershell البعيد. للحصول على الإرشادات، راجع [تمكين الوصول إلى Exchange Online PowerShell أو تعطيله](/powershell/exchange/disable-access-to-exchange-online-powershell).

يمكن للمسؤولين أيضا استخدام الإعدادات العمومية في نهج العزل لتخصيص اسم العرض الخاص بالمرسل ونص إخلاء المسؤولية بلغات مختلفة وشعار الشركة المستخدم في إعلامات العزل. للحصول على الإرشادات، راجع [تكوين إعدادات إعلام العزل العمومي](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

بالنسبة إلى علب البريد المشتركة، يتم دعم إعلامات العزل فقط للمستخدمين الذين تم منحهم إذن FullAccess إلى علبة البريد المشتركة. لمزيد من المعلومات، راجع [استخدام EAC لتحرير تفويض علبة البريد المشتركة](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> بشكل افتراضي، تتوفر الرسائل التي يتم عزلها على أنها تصيد احتيالي عالي الثقة أو برامج ضارة أو قواعد تدفق البريد (المعروفة أيضا بقواعد النقل) أو خزينة نهج المرفقات في Defender لـ Office 365 فقط للمسؤولين (بشكل افتراضي، يتم استخدام نهج العزل AdminOnlyAccessPolicy). لمزيد من المعلومات، راجع [إدارة الرسائل والملفات المعزولة كمسؤول في EOP](manage-quarantined-messages-and-files.md).
>
> حاليا، إعلامات العزل غير معتمدة للمجموعات.

عندما تتلقى إعلام عزل، تتوفر المعلومات التالية دائما لكل رسالة تم عزلها:

- **المرسل**: اسم الإرسال وعنوان البريد الإلكتروني للرسالة المعزولة.
- **الموضوع**: نص سطر الموضوع للرسالة المعزولة.
- **التاريخ**: التاريخ والوقت (في UTC) الذي تم عزل الرسالة فيه.

تعتمد الإجراءات المتوفرة في إعلام العزل على سبب عزل الرسالة والأذونات التي تم تعيينها بواسطة نهج العزل المقترن. لمزيد من المعلومات، راجع [تفاصيل إذن نهج العزل](quarantine-policies.md#quarantine-policy-permission-details).

بشكل افتراضي، تتوفر الإجراءات التالية في إعلام العزل للرسائل التي تم عزلها باعتبارها بريدا عشوائيا أو بريدا عشوائيا عالي الثقة أو مجمعا:

- **حظر المرسل**: انقر فوق هذا الارتباط لإضافة المرسل إلى قائمة المرسلين المحظورين في علبة البريد _._ لمزيد من المعلومات، راجع ["حظر مرسل البريد](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4)".
- **الإصدار**: يمكنك تحرير الرسالة هنا دون الانتقال إلى **العزل** في مدخل Microsoft 365 Defender.
- **مراجعة**: انقر فوق هذا الارتباط للانتقال إلى **العزل** في مدخل Microsoft 365 Defender، حيث يمكنك (اعتمادا على سبب عزل الرسالة) عرض الرسائل المعزولة أو تحريرها أو حذفها أو الإبلاغ بها. لمزيد من المعلومات، راجع [البحث عن الرسائل المعزولة وتحريرها كمستخدم في EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="مثال على إعلام العزل" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> لا يزال بإمكان المرسل المحظور إرسال بريد إليك. سيتم نقل أي رسائل من هذا المرسل تقوم بنقلها إلى علبة بريدك على الفور إلى مجلد البريد الإلكتروني غير الهام. ستنتقل الرسائل المستقبلية من هذا المرسل إلى مجلد البريد الإلكتروني غير الهام أو إلى العزل. إذا كنت ترغب في حذف هذه الرسائل عند الوصول بدلا من ربعها، فاستخدم [قواعد تدفق البريد](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (المعروفة أيضا بقواعد النقل) لحذف الرسائل عند الوصول.
