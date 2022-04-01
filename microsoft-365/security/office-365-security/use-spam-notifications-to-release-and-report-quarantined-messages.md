---
title: إعلامات الفحص (إعلامات البريد العشوائي للمستخدم النهائي) في Microsoft 365
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
ms.openlocfilehash: 706303e7bdab7297fbc1dd353238db3542c28177
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465828"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>استخدام إعلامات الفحص للافراج عن الرسائل المعزولة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender لـ Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في Microsoft 365 المؤسسات التي بها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online، يحتفظ الفحص بالرسائل الخطيرة أو غير المرغوب فيها. لمزيد من المعلومات، راجع [الرسائل المعزولة في EOP](quarantine-email-messages.md).

_تحدد سياسات الفحص_ ما يسمح للمستخدمين به للرسائل المعزولة استنادا إلى سبب عزل الرسالة (للميزات المعتمدة). لمزيد من المعلومات، راجع [سياسات الفحص](quarantine-policies.md). تتحكم أيضا إجراءات الفحص في ما إذا كان المستلمون المتأثرون (بما في ذلك علب البريد المشتركة) سيتلقون إعلامات الفحص _الدورية حول_ رسائلهم المعزولة. إعلامات الفحص هي البديل عن إعلامات البريد العشوائي للمستخدم النهائي لكل ميزات الحماية المعتمدة (وليس فقط أحكام نهج مكافحة البريد العشوائي).

لا يتم تشغيل إعلامات الفحص في إعلامات الفحص المضمنة المسماة AdminOnlyAccessPolicy أو DefaultFullAccessPolicy. يتم تشغيل إعلامات الفحص في نهج الفحص المضمن المسمى NotificationEnabledPolicy [إذا كانت مؤسستك مضمنة فيه](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). وبخلاف ذلك، ول تشغيل إعلامات الفحص في نهج الفحص، ستحتاج إلى إنشاء نهج عزل جديد [وتكوينه](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

بالإضافة إلى ذلك، للسماح بخيار "حظر المرسل" في إعلامات الفحص بالعمل بشكل صحيح، يجب تمكين المستخدمين ل Powershell البعيد. للحصول على الإرشادات، راجع تمكين الوصول إلى Exchange Online [PowerShell أو تعطيله](/powershell/exchange/disable-access-to-exchange-online-powershell).

يمكن للمسؤولين أيضا استخدام الإعدادات العامة في سياسات الفحص لتخصيص اسم العرض للمرسل ونص إخلاء المسؤولية بلغات مختلفة وشعار الشركة المستخدم في إعلامات الفحص. للحصول على الإرشادات، راجع [تكوين إعدادات إعلامات الفحص العام](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

بالنسبة لعلب البريد المشتركة، تكون إعلامات الفحص معتمدة فقط للمستخدمين الذين تم منحهم إذن FullAccess لعلبة البريد المشتركة. لمزيد من المعلومات، راجع [استخدام EAC لتحرير إرسال علبة البريد المشتركة](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> بشكل افتراضي، تتوفر الرسائل التي يتم فحصها على أنها تصيد احتيالي عالي الثقة أو برامج ضارة أو قواعد تدفق البريد (تعرف أيضا بقواعد النقل) أو نهج مرفقات خزينة في Defender لـ Office 365 فقط للمسؤولين (بشكل افتراضي، يتم استخدام نهج الفحص AdminOnlyAccessPolicy). لمزيد من المعلومات، راجع [إدارة الرسائل والملفات المعزولة كمسؤول في EOP](manage-quarantined-messages-and-files.md).
>
> حاليا، إعلامات الفحص غير معتمدة للمجموعات أو رسائل التصيد الاحتيالي عالية الثقة. 

عندما تتلقى إعلاما بالفحص، تتوفر المعلومات التالية دائما لكل رسالة معزولة:

- **المرسل**: اسم المرسل وعنوان البريد الإلكتروني للرسالة التي تم فحصها.
- **الموضوع**: نص سطر الموضوع للرسالة المعزولة.
- **التاريخ**: التاريخ والوقت (في UTC) الذي تم فيه فحص الرسالة.

تعتمد الإجراءات المتوفرة في إعلام الفحص على سبب عزل الرسالة والأذونات المعينة بواسطة نهج الفحص المقترن. لمزيد من المعلومات، راجع [تفاصيل أذونات نهج الفحص](quarantine-policies.md#quarantine-policy-permission-details).

بشكل افتراضي، تتوفر الإجراءات التالية في إعلام الفحص للرسائل التي تم فحصها كبريد عشوائي أو بريد عشوائي عالي الثقة أو مجمعة:

- **حظر المرسل**: انقر فوق هذا الارتباط لإضافة المرسل إلى قائمة المرسلون المحظورون في _علبة بريدك_ . لمزيد من المعلومات، راجع [حظر مرسل بريد](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **الإصدار**: يمكنك إصدار الرسالة هنا دون الذهاب إلى **"** الفحص" في Microsoft 365 Defender المدخل.
- **مراجعة**: انقر فوق هذا الارتباط الانتقال إلى  "الفحص" في مدخل Microsoft 365 Defender، حيث يمكنك (استنادا إلى سبب عزل الرسالة) عرض الرسائل المعزولة أو تحريرها أو حذفها أو الإبلاغ عنها. لمزيد من المعلومات، راجع [البحث عن الرسائل المعزولة وإطلاقها كمستخدم في EOP](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="مثال إعلام الفحص" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> ما زال با الممكن أن يرسل إليك المرسل المحظور بريدا. سيتم نقل أي رسائل أرسلها هذا المرسل إلى علبة البريد على الفور إلى مجلد البريد الإلكتروني غير الهام. سترسل الرسائل المستقبلية من هذا المرسل إلى مجلد البريد الإلكتروني غير الهام أو إلى الفحص. إذا كنت تريد حذف هذه الرسائل عند الوصول بدلا من إجرائها، فاستخدم قواعد تدفق [البريد (المعروفة](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) أيضا بقواعد النقل) لحذف الرسائل عند الوصول.
