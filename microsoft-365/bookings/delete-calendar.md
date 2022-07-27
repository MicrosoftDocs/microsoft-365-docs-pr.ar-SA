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
ms.openlocfilehash: 57ad1ea0e7857a1d7af4f98d196a67f27f743dd0
ms.sourcegitcommit: 13a1199fbfeb329da77ce87b2781d5cc77e4a201
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/27/2022
ms.locfileid: "67037545"
---
# <a name="delete-a-booking-calendar-in-bookings"></a>حذف تقويم الحجز في Bookings

تشرح هذه المقالة كيفية حذف تقويم حجز غير مرغوب فيه. يمكنك حذف تقويم الحجز في مركز مسؤولي Microsoft 365 أو يمكنك استخدام PowerShell. تقويم Bookings هو علبة بريد في Exchange Online لذلك يمكنك حذف حساب المستخدم المطابق لحذف تقويم الحجز.

> [!IMPORTANT]
> يجب حذف كافة تقويمات الحجز التي أنشأتها في عام 2017 أو قبله باستخدام إرشادات PowerShell حول هذا الموضوع. يمكن حذف كافة تقويمات الحجز التي تم إنشاؤها في عام 2018 أو بعده في مركز مسؤولي Microsoft 365.

تقويم الحجز هو المكان الذي يتم فيه تخزين جميع المعلومات ذات الصلة حول تقويم الحجز وبياناته، بما في ذلك:

- معلومات العمل والشعار وساعات العمل المضافة عند إنشاء تقويم الحجز
- إضافة الموظفين والخدمات ذات الصلة عند إنشاء تقويم الحجز
- تمت إضافة كل الحجوزات ومواعيد الإجازة إلى تقويم الحجز بمجرد إنشائه.

> [!WARNING]
> بمجرد حذف تقويم الحجز، يتم أيضا حذف هذه المعلومات الإضافية بشكل دائم ولا يمكن استردادها.

## <a name="delete-a-booking-calendar-in-the-microsoft-365-admin-center"></a>حذف تقويم حجز في مركز مسؤولي Microsoft 365

1. انتقل إلى مركز مسؤولي Microsoft 365.

1. في مركز مسؤول، حدد **"المستخدمون**".

   ![صورة لواجهة مستخدم المستخدمين في مركز مسؤولي Microsoft 365.](../media/bookings-admin-center-users.png)

1. في صفحة **"المستخدمون النشطون** "، اختر اسم تقويم الحجز الذي تريد حذفه ثم حدد **"حذف مستخدم**".

   ![صورة لحذف واجهة مستخدم المستخدم في مركز مسؤولي Microsoft 365.](../media/bookings-delete-user.png)

## <a name="delete-a-booking-calendar-using-exchange-online-powershell"></a>حذف تقويم حجز باستخدام Exchange Online PowerShell

راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell-v2) للحصول على المتطلبات الأساسية والإرشادات اللازمة للاتصال Exchange Online PowerShell.

لتنفيذ هذه الخطوات، يجب أن تستخدم نافذة أوامر Microsoft PowerShell نشطة قمت بتشغيلها عن طريق اختيار الخيار "تشغيل كمسؤول".

1. في نافذة PowerShell، قم بتحميل الوحدة النمطية EXO V2 عن طريق تشغيل الأمر التالي:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

   > [!NOTE]
   > إذا قمت بالفعل [بتثبيت الوحدة النمطية EXO V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module)، فسيعمل الأمر السابق كما هو مكتوب.
   
2. يستخدم الأمر الذي تحتاج إلى تشغيله بناء الجملة التالي:

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName <UPN> 
   ```

   - _\<UPN\>_ هو حسابك بتنسيق اسم المستخدم الأساسي (على سبيل المثال، `john@contoso.com`).

3. عند مطالبتك، قم بتسجيل الدخول باستخدام بيانات اعتماد مسؤول المستأجر إلى مستأجر Microsoft 365 الذي يستضيف تقويم الحجز الذي تريد حذفه بشكل دائم.

4. بمجرد الانتهاء من معالجة هذا الأمر، أدخل الأمر التالي للحصول على قائمة بعلب بريد الحجز في المستأجر الخاص بك:

   ```powershell
   Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

5. اكتب الأمر التالي:

   ```powershell
   remove-mailbox [BookingCalendarToDelete]
   ```

   > [!IMPORTANT]
   > كن حذرا لكتابة الاسم الدقيق لاسم علبة بريد الحجز المستعار الذي تريد حذفه نهائيا.

6. للتحقق من حذف التقويم، أدخل الأمر التالي:

   ```powershell
    Get-EXOMailbox -RecipientTypeDetails SchedulingMailbox
   ```

   لن يظهر التقويم المحذوفة في الإخراج.
