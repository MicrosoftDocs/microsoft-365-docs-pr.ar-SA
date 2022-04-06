---
title: تتبع الرسائل في مدخل Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: يمكن للمسؤولين استخدام ارتباط تتبع الرسائل في مدخل Microsoft 365 Defender لمعرفة ما حدث للرسائل.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d09470e37c066202d49d7d79788c12853ed42e21
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679731"
---
# <a name="message-trace-in-the-microsoft-365-defender-portal"></a>تتبع الرسائل في مدخل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تتبع الرسائل بعد رسائل البريد الإلكتروني أثناء تنقلها عبر Exchange Online الخاصة بك. يمكنك تحديد ما إذا تم تلقي رسالة أو رفضها أو تأجيلها أو تسليمها بواسطة الخدمة. كما تعرض الإجراءات التي تم اتخاذها على الرسالة قبل أن تصل إلى وضعها النهائي.

يمكنك استخدام المعلومات من تتبع الرسائل للإجابة بفاعلية على أسئلة المستخدم حول ما حدث للرسائل، استكشاف مشاكل تدفق البريد وإصلاحها، والتحقق من صحة تغييرات النهج.

> [!NOTE]
> تتبع الرسائل في Microsoft 365 Defender هو مجرد تمرير إلى تتبع الرسائل في Exchange الإدارة. لمزيد من المعلومات، راجع [تتبع الرسائل في مركز إدارة Exchange الحديث](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يجب أن تكون عضوا في مجموعات دور إدارة المؤسسة أو إدارة  التوافق أو **مكتب** المساعدة في Exchange Online تتبع الرسائل. لمزيد من المعلومات، راجع [الأذونات في Exchange Online](/exchange/permissions-exo/permissions-exo).

  **ملاحظات**: تمنح العضوية في دور Azure Active Directory المناظر في مركز مسؤولي Microsoft 365 المستخدمين الأذونات والأذونات المطلوبة للميزات الأخرى في Microsoft 365. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

- يعتمد الحد الأقصى لعدد الرسائل التي يتم عرضها في نتائج تتبع الرسائل على نوع التقرير الذي حددته (راجع المقطع [اختيار](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac#choose-report-type) نوع التقرير للحصول على التفاصيل). يرجع [الأمر Get-HistoricalSearch cmdlet](/powershell/module/exchange/get-historicalsearch) في Exchange Online PowerShell أو EOP PowerShell مستقل كل الرسائل في النتائج.

## <a name="open-message-trace"></a>فتح تتبع الرسائل

في مدخل Microsoft 365 Defender، <https://security.microsoft.com>انتقل إلى البريد الإلكتروني & **إلى Exchange** \> **تتبع الرسائل**. الانتقال مباشرة إلى صفحة تتبع الرسائل، استخدم <https://admin.exchange.microsoft.com/#/messagetrace>.

في هذه المرحلة، يتم فتح تتبع الرسائل في EAC. لمزيد من المعلومات، راجع [تتبع الرسائل في مركز إدارة Exchange الحديث](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
