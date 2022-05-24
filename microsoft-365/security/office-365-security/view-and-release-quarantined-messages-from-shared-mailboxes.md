---
title: عرض الرسائل المعزولة وتحريرها من علب البريد المشتركة
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: يمكن للمستخدمين معرفة كيفية عرض الرسائل المعزولة التي تم إرسالها إلى علب البريد المشتركة التي لديهم أذونات إليها والعمل عليها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2613d3b8be200db3a9107355a27b0dd79ce537d3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647317"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>عرض الرسائل المعزولة وتحريرها من علب البريد المشتركة

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**ينطبق على:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

يمكن للمستخدمين إدارة الرسائل المعزولة حيث هم أحد المستلمين كما هو موضح في [البحث عن الرسائل المعزولة وإصدارها كمستخدم في EOP](find-and-release-quarantined-messages-as-a-user.md). ولكن ماذا عن **علب البريد المشتركة** حيث يملك المستخدم أذونات "الوصول الكامل" و"إرسال باسم" أو "إرسال نيابة عن" إلى علبة البريد كما هو موضح في [علب البريد المشتركة في Exchange Online](/exchange/collaboration-exo/shared-mailboxes)؟

في السابق، كانت قدرة المستخدمين على إدارة الرسائل المعزولة المرسلة إلى علبة بريد مشتركة تتطلب من المسؤولين ترك التعيين التلقائي ممكنا لعل البريد المشترك (يتم تمكينه بشكل افتراضي عندما يمنح المسؤول المستخدم حق الوصول إلى علبة بريد أخرى). ومع ذلك، قد يتأثر الأداء بسبب محاولة Outlook فتح _كل_ علب البريد التي يملك المستخدم حق الوصول إليها، وذلك استنادا إلى حجم علب البريد التي يملك المستخدم حق الوصول إليها وعددها. لهذا السبب، يختار العديد من المسؤولين [إزالة التعيين التلقائي لعلب البريد المشتركة](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

الآن، لم يعد التعيين التلقائي مطلوبا للمستخدمين لإدارة الرسائل المعزولة التي تم إرسالها إلى علب البريد المشتركة. إنه يعمل فقط. هناك طريقتان مختلفتان للوصول إلى الرسائل المعزولة التي تم إرسالها إلى علبة بريد مشتركة:

- إذا قام المسؤول بتكوين [نهج العزل](quarantine-policies.md) للسماح بإعلامات العزل (المعروفة سابقا باسم إعلامات البريد العشوائي للمستخدم النهائي)، يمكن لأي مستخدم لديه حق الوصول إلى إعلامات العزل في علبة البريد المشتركة النقر فوق الزر **"مراجعة"** في الإعلام للانتقال إلى العزل في مدخل Microsoft 365 Defender. لاحظ أن هذا الأسلوب يسمح فقط للمستخدمين بإدارة الرسائل المعزولة التي تم إرسالها إلى علبة البريد المشتركة. لا يمكن للمستخدمين إدارة رسائل العزل الخاصة بهم في هذا السياق.
- يمكن للمستخدم [الانتقال إلى العزل في مدخل Microsoft 365 Defender](find-and-release-quarantined-messages-as-a-user.md) والنقر فوق **"تصفية"** لتصفية النتائج حسب **عنوان المستلم** (عنوان البريد الإلكتروني لعل البريد المشترك). في صفحة **العزل** الرئيسية، يمكنك النقر فوق العمود **"المستلم"** للفرز حسب الرسائل التي تم إرسالها إلى علبة البريد المشتركة.

## <a name="things-to-keep-in-mind"></a>أشياء يجب وضعها في الاعتبار

- تحدد _نهج العزل_ ما يسمح للمستخدمين بالقيام به أو عدم القيام به للرسائل المعزولة استنادا إلى سبب عزل الرسالة (للميزات المدعومة). تفرض نهج العزل الافتراضية القدرات التاريخية التي تسمح للمستلمين بعرض الرسائل والعمل عليها. يمكن للمسؤولين إنشاء وتطبيق نهج العزل المخصصة التي تحدد قدرات أقل تقييدا أو أكثر تقييدا للمستخدمين. لمزيد من المعلومات، راجع [نهج العزل](quarantine-policies.md).

- يقرر المستخدم الأول الذي يعمل على الرسالة المعزولة قدر الرسالة لكل من يستخدم علبة البريد المشتركة. على سبيل المثال، إذا تم الوصول إلى علبة بريد مشتركة من قبل 10 مستخدمين، وقرر مستخدم حذف رسالة العزل، يتم حذف الرسالة لجميع المستخدمين العشرة. وبالمثل، إذا قرر مستخدم تحرير الرسالة، يتم إصدارها إلى علبة البريد المشتركة ويمكن لجميع المستخدمين الآخرين في علبة البريد المشتركة الوصول إليها.

- حاليا، لا يتوفر الزر **"حظر المرسل"** في القائمة المنبثقة " **تفاصيل** " للرسائل المعزولة التي تم إرسالها إلى علبة البريد المشتركة.

- فيما يتعلق بعمليات العزل لعلب البريد المشتركة، إذا كنت تستخدم مجموعات أمان متداخلة لمنح حق الوصول إلى علبة بريد مشتركة، فلا نوصي بأكثر من مستويين من المجموعات المتداخلة. على سبيل المثال، المجموعة A هي عضو في المجموعة B، وهي عضو في المجموعة C. لتعيين أذونات إلى علبة بريد مشتركة، لا تقم بإضافة المستخدم إلى المجموعة A ثم قم بتعيين المجموعة C إلى علبة البريد المشتركة.  

- لإدارة الرسائل المعزولة لعلبة البريد المشتركة في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)، سيحتاج المستخدم النهائي إلى استخدام [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage) cmdlet مع عنوان البريد الإلكتروني لعلب البريد المشترك لقيمة المعلمة _RecipientAddress_ لتحديد الرسائل. على سبيل المثال:

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```

  بعد ذلك، يمكن للمستخدم النهائي تحديد رسالة تم عزلها من القائمة لعرضها أو اتخاذ إجراء بشأنها.

  يعرض هذا المثال كافة الرسائل المعزولة التي تم إرسالها إلى علبة البريد المشتركة، ثم يحرر الرسالة الأولى في القائمة من العزل (الرسالة الأولى في القائمة هي 0 والثانية هي 1 وهكذا).

  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```

  للحصول على معلومات مفصلة حول بناء الجملة والمعلمة، راجع المواضيع التالية:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [معاينة-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
