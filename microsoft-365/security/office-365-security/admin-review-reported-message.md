---
title: مراجعة المسؤول للرسائل التي تم التقارير عنها
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
ms.custom: ''
description: تعرف على كيفية مراجعة الرسائل التي تم تقديم التقارير بشأنها، ثم تقديم ملاحظات إلى المستخدمين.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2cb979260bde62903e97a4726083924101b8711a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63573948"
---
# <a name="admin-review-for-reported-messages"></a>مراجعة المسؤول للرسائل التي تم التقارير عنها

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

في Microsoft 365 المؤسسات التي Exchange Online علب بريدها و Microsoft Defender ل Office 365، يمكن للمسؤولين الآن إرسال الرسائل الم وقوالبها مرة أخرى إلى المستخدمين النهائيين بعد مراجعة الرسائل التي تم الإبلاغ عنها. يمكن تخصيص القوالب لمنظمتك واستنادا إلى قرار المسؤول أيضا.

تم تصميم هذه الميزة لتعطي ملاحظات للمستخدمين ولكنها لا تغير الأحكام الواردة في الرسائل في النظام. لمساعدة Microsoft على تحديث عوامل التصفية وتحسينها، ستحتاج إلى إرسال الرسائل لتحليلها باستخدام [إرسال المسؤول](admin-submission.md).

لن تتمكن من وضع علامة على نتائج المراجعة وإعلام المستخدمين بها إلا إذا تم إبلاغهم عن الرسالة كإيجابيات خاطئة أو [كسلبيات خاطئة](report-false-positives-and-false-negatives.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- يمكنك فتح Microsoft 365 Defender في <https://security.microsoft.com>. الانتقال مباشرة إلى صفحة **"الواجبات** المرسلة"، استخدم <https://security.microsoft.com/reportsubmission>.

- لتعديل تكوين إرسالات المستخدم، يجب أن تكون عضوا في إحدى مجموعات الدور التالية:
  - إدارة المؤسسة أو مسؤول الأمان في [Microsoft 365 Defender الإلكتروني](permissions-microsoft-365-security-center.md).
  - إدارة المؤسسة في [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- ستحتاج أيضا إلى الوصول إلى Exchange Online PowerShell. إذا لم يكن للحساب الذي تحاول استخدامه حق الوصول إلى Exchange Online PowerShell، ستتلقى رسالة خطأ تقول تحديد عنوان بريد إلكتروني في *مجالك*. لمزيد من المعلومات حول تمكين الوصول إلى Exchange Online PowerShell أو تعطيله، راجع المواضيع التالية:
  - [تمكين الوصول إلى Exchange Online PowerShell أو تعطيله](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [قواعد وصول العميل في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="notify-users-from-within-the-portal"></a>إعلام المستخدمين من داخل المدخل

1. في Microsoft 365 Defender في <https://security.microsoft.com>، انتقل إلى صفحة **الواجبات** المرسلة في **البريد الإلكتروني & إرسالات** \> **التعاون**. الانتقال مباشرة إلى صفحة **"الواجبات** المرسلة"، استخدم <https://security.microsoft.com/reportsubmission>.

2. انقر **فوق الرسائل التي أبلغ عنها المستخدم**، ثم حدد الرسالة التي تريد وضع علامة عليها وإعلامها.

3. حدد **المنسدل وضع علامة باسم** وإعلام، **ثم حدد لا** توجد أي تهديدات يتم العثور عليها أو التصيد الاحتيالي أو البريد **غير الهام**.

   > [!div class="mx-imgBorder"]
   > ![إرسال رسائل من المدخل.](../../media/admin-review-send-message-from-portal.png)

سيتم وضع علامة على الرسالة التي تم إبلاغها كسلبية خطأ أو موجبة خطأ، وسترسل رسالة بريد إلكتروني تلقائيا من داخل المدخل لإعلام المستخدم الذي أبلغ عن الرسالة.

## <a name="customize-the-messages-used-to-notify-users"></a>تخصيص الرسائل المستخدمة لإعلام المستخدمين

1. في Microsoft 365 Defender     <https://security.microsoft.com>على ، انتقل إلى صفحة إرسالات المستخدم في البريد الإلكتروني **&** \> \> \> سياسات التعاون & قواعد المخاطر قام المستخدم ب إعداد إعدادات الرسالة في **القسم** "أخرى". الانتقال مباشرة إلى صفحة **إرسالات** المستخدم، استخدم <https://security.microsoft.com/userSubmissionsReportMessage>.

2. في صفحة  إرسالات المستخدم، إذا كنت تريد تحديد اسم عرض المرسل، فحدد خانة الاختيار تحديد عنوان البريد الإلكتروني **Office 365** لاستخدامه كمرسل ضمن المقطع إعلامات البريد الإلكتروني لنتائج مراجعة  المسؤول، وأدخل الاسم الذي تريد استخدامه. عنوان البريد الإلكتروني الذي سيكون مرئيا في Outlook وستذهب جميع الردود إلى هناك.

3. إذا كنت تريد تخصيص أي من القوالب، انقر فوق تخصيص إعلام **البريد الإلكتروني** في أسفل الصفحة. في طريقة العرض التي يتم فتحها، يمكنك تخصيص ما يلي فقط:

    - التصيد الاحتيالي
    - غير هام
    - لم يتم العثور على أي تهديدات
    - تاشيير

    > [!div class="mx-imgBorder"]
    > ![تخصيص الرسائل المرسلة إلى المستخدمين.](../../media/admin-review-customize-message.png)

4. عند الانتهاء، انقر فوق **حفظ**. لمسح هذه القيم، انقر فوق **تجاهل** على صفحة **إرسالات** المستخدم.
