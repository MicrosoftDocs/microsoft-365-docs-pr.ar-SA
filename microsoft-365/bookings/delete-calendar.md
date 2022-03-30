---
title: حذف تقويم حجز
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.localizationpriority: medium
ms.assetid: 8c3a913c-2247-4519-894d-b6263eeb9920
description: استخدم مركز مسؤولي Microsoft 365 أو Windows PowerShell لحذف تقويمات Bookings.
ms.openlocfilehash: 48556951382b95316ffdb9e07c1c561758276ded
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63576989"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>حذف تقويم حجز في Bookings

تشرح هذه المقالة كيفية حذف تقويم حجز غير مرغوب فيه. يمكنك حذف تقويم الحجز في مركز مسؤولي Microsoft 365 أو يمكنك استخدام PowerShell. إن تقويم Bookings هو علبة بريد في Exchange Online بحيث تحذف حساب المستخدم المناظر لحذف تقويم الحجز.

> [!IMPORTANT]
> يجب حذف كل تقويمات الحجز التي أنشأتها في 2017 أو قبلها باستخدام إرشادات PowerShell حول هذا الموضوع. يمكن حذف كل تقويمات الحجز التي تم إنشاؤها في 2018 أو بعد ذلك في مركز مسؤولي Microsoft 365.

إن تقويم الحجز هو المكان الذي يتم فيه تخزين كل المعلومات ذات الصلة حول تقويم الحجز وبياناته، بما في ذلك:

- معلومات العمل والشعار وساعات العمل المضافة عند إنشاء تقويم الحجز
- فريق العمل والخدمات ذات الصلة التي تم إضافتها عند إنشاء تقويم الحجز
- تضاف كل الحجوزات ومواعيد المواعيد الخاصة بالمواعيد إلى تقويم الحجز بعد إنشائه.

> [!WARNING]
> بمجرد حذف تقويم الحجز، يتم أيضا حذف هذه المعلومات الإضافية بشكل دائم ولا يمكن استردادها.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>حذف تقويم حجز في مركز مسؤولي Microsoft 365

1. انتقل إلى مركز مسؤولي Microsoft 365.

1. في مركز الإدارة، حدد **المستخدمون**.

   ![صورة واجهة مستخدم المستخدمين في مركز مسؤولي Microsoft 365.](../media/bookings-admin-center-users.png)

1. في صفحة **المستخدمون** النشطون، اختر أسماء المستخدمين الذين تريد حذفهم، ثم حدد **حذف مستخدم**.

   ![صورة لحذف واجهة مستخدم المستخدم في مركز مسؤولي Microsoft 365.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>حذف تقويم حجز باستخدام Exchange Online PowerShell

راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell-v2) للحصول على المتطلبات الأساسية والإرشادات للاتصال Exchange Online PowerShell.

لتنفيذ هذه الخطوات، يجب أن تستخدم نافذة أوامر Microsoft PowerShell نشطة قمت بتشغيلها عن طريق تحديد الخيار "تشغيل كمسؤول".

1. في نافذة PowerShell، قم بتحميل الوحدة النمطية EXO V2 عن طريق تشغيل الأمر التالي:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > إذا قمت مسبقا بتثبيت [الوحدة النمطية EXO V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module)، فإن الأمر السابق يعمل كما هو مكتوب.
   
2. يستخدم الأمر الذي تحتاج إلى تشغيله بناء الجملة التالي:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ هو حسابك بتنسيق الاسم الأساسي للمستخدم (على سبيل المثال، `john@contoso.com`).

3. عندما يتم مطالبتك بذلك، سجل دخولك باستخدام بيانات اعتماد مسؤول المستأجر Microsoft 365 المستأجر الذي يستضيف تقويم الحجز الذي تريد حذفه نهائيا.

4. بمجرد أن يتم هذا الأمر من المعالجة، أدخل الأمر التالي للحصول على قائمة لعلب بريد الحجز في المستأجر:

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. اكتب الأمر التالي:

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > يجب توخي الحذر عند كتابة الاسم الدقيق لاسم علبة بريد الحجز المستعار الذي تريد حذفه نهائيا.

6. للتحقق من حذف التقويم، أدخل الأمر التالي:

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   لن يظهر التقويم المحذوف في الإخراج.
