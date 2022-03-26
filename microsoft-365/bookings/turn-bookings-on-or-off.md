---
title: تشغيل Microsoft Bookings أو إيقاف تشغيله
ms.author: kwekua
author: kwekuako
manager: scotv
audience: Admin
ms.topic: article
ms.service: bookings
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
ms.assetid: 5382dc07-aaa5-45c9-8767-502333b214ce
description: تعرف على كيفية الوصول إلى Microsoft Bookings في Microsoft 365.
ms.openlocfilehash: 3feacd756c141dd51edd7e987c1c4a2033524ae3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569414"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>تشغيل Microsoft Bookings أو إيقاف تشغيله

يمكن تشغيل الحجوزات أو إيقاف تشغيلها لمنظمتك بأكملها أو لمستخدمين معينين. عند تشغيل Bookings للمستخدمين، يمكنهم إنشاء صفحة Bookings وإنشاء تقويم والسماح للأشخاص الآخرين بالحجز معهم.

> [!NOTE]
> عناصر تحكم المسؤول الموضحة في هذه الأقسام غير متوفرة Office 365 التي يتم تشغيلها بواسطة عملاء 21Vianet (الصين).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>تشغيل Bookings أو إيقاف تشغيلها لمنظمتك باستخدام مركز مسؤولي Microsoft 365

1. سجل الدخول إلى مركز مسؤولي Microsoft 365 كمسؤول عام.

2. في مركز الإدارة،  **انتقل إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**المؤسسة**</a>.

3. حدد خانة الاختيار السماح **لمنظمتك باستخدام Bookings** لتمكين Bookings لم المؤسسة أو تعطيلها.

   > [!NOTE]
   > سيؤدي إيقاف تشغيل Bookings إلى تعطيل كل الوصول إلى الخدمة بما في ذلك إنشاء صفحات Bookings وإدارتها.

4. حدد **حفظ التغييرات**.

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>تشغيل Bookings أو إيقاف تشغيلها لمنظمتك باستخدام PowerShell

لتشغيل Bookings أو إيقاف تشغيله لمنظمتك باستخدام الأمر PowerShell cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig)، الاتصال إلى Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) وتشغيل الأمر التالي:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

استخدم الإعدادات أدناه للتحكم في الأشخاص الذين يمكنهم استخدام Bookings، وتحديد معلومات Bookings التي تمت مشاركتها وما إذا كان الموظفون بحاجة إلى الموافقة قبل إضافتهم إلى تقويم Booking.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="لقطة شاشة: الإعدادات تسمح لك بالتحكم في الأشخاص الذين يمكنهم استخدام Bookings، وحدد معلومات Bookings التي تمت مشاركتها وموافقة فريق العمل":::

### <a name="block-bookings-from-outside-your-organization"></a>حظر الحجوزات من خارج مؤسستك

يمكنك إعداد Bookings بحيث يمكن للأشخاص في مؤسستك فقط حجز المواعيد. يمكن فقط للمستخدمين في مؤسستك الذين وقعوا وصادقوا حجز المواعيد.

### <a name="block-social-sharing-options"></a>حظر خيارات المشاركة الاجتماعية

يمكنك التحكم في كيفية مشاركة صفحات الحجز على الشبكات الاجتماعية. يتوفر هذا الإعداد في مركز مسؤولي Microsoft 365 ضمن **الإعدادات** ->  **أوg settingsBookings** -> .

### <a name="block-sharing-staff-details-with-customers"></a>حظر مشاركة تفاصيل فريق العمل مع العملاء

لن يتم إرسال تفاصيل فريق العمل، مثل معلومات جهة الاتصال، إلى العملاء عبر البريد الإلكتروني أو أي اتصال آخر.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>طلب موافقات فريق العمل قبل مشاركة معلومات الشغل/الشغف

يمكنك أن تطلب من الموظفين في مؤسستك الاشتراك قبل مشاركة معلومات التوفر الخاصة بهم من خلال Bookings وقبل أن يكونوا قابلين للحجز من خلال صفحة الحجز.

عند تمكين هذا الإعداد، سيحصل الأشخاص الذين تم إضافتهم كالموظفين في تقويمات الحجز على بريد إلكتروني مع ارتباط إلى **الموافقة/رفض** الطلب.

## <a name="restrict-collection-of-customer-data"></a>تقييد تجميع بيانات العملاء

لأسباب تتعلق بالتوافق، قد لا ترغب في جمع بعض معلومات العملاء. إذا حددت خانة اختيار لأي من هذه الخيارات، فلن يتم تضمين هذه الحقول في أي نماذج تظهر لعملائك أو عملائك.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="لقطة شاشة: حدد خانات الاختيار للمساعدة في منع العملاء من مشاركة البيانات الحساسة معك":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>تشغيل Bookings أو إيقاف تشغيلها للمستخدمين الفرديين

يمكنك تعطيل Bookings لمستخدمين فرديين.

1. انتقل إلى مركز مسؤولي Microsoft 365، ثم حدد **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**النشطون**</a>.

1. حدد المستخدم المطلوب، ثم حدد **التراخيص والتطبيقات**.

1. قم **بتوسيع التطبيقات** ومسح خانة الاختيار ل Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>السماح للمستخدمين المحددين فقط بإنشاء تقويمات Bookings

باستخدام قيود النهج، يمكنك منع المستخدمين المرخص لهم من إنشاء تقويمات Bookings. يجب أولا تمكين Bookings لمنظمتك بأكملها. سيكون لدى جميع المستخدمين في مؤسستك تراخيص Bookings، ولكن يمكن فقط للمستخدمين المضمنين في النهج إنشاء تقويمات Bookings والتحكم الكامل في الأشخاص الذين يمكنهم الوصول إلى التقويمات التي ينشئونها.

يمكن للمستخدمين المضمنين في هذا النهج إنشاء تقويمات Bookings جديدة ويمكن إضافتها كالموظفين بأي سعة (بما في ذلك دور المسؤول) إلى تقويمات Bookings الموجودة. لن يتمكن المستخدمون غير المضمنين في هذا النهج من إنشاء تقويمات Bookings جديدة وسيتلقون رسالة خطأ إذا حاولوا القيام بذلك.

ستحتاج إلى تشغيل الأوامر التالية باستخدام Exchange Online PowerShell. لمزيد من المعلومات حول تشغيل Exchange Online cmdlets، راجع الاتصال Exchange Online [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> تفترض الخطوات أدناه أنه لم يتم إنشاء أي Outlook Web App أخرى في علبة بريد (OWA) في مؤسستك.

1. أنشئ نهج علبة بريد جديدة للمستخدمين الذين يجب السماح لهم بإنشاء تقويمات Bookings. (يسمح بشكل افتراضي بإنشاء تقويم Bookings بواسطة سياسات علبة البريد الجديدة.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   لمزيد من المعلومات، راجع [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. قم بتعيين هذا النهج إلى المستخدمين ذوي الصلة عن طريق تشغيل هذا الأمر لكل مستخدم تريد منحه الإذن لإنشاء تقويمات Bookings.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   لمزيد من المعلومات، راجع [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. اختياري: قم بتشغيل هذا الأمر إذا كنت تريد تعطيل Bookings لجميع المستخدمين الآخرين في مؤسستك.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   لمزيد من المعلومات، راجع [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

لمزيد من المعلومات حول سياسات علبة بريد OWA، راجع المواضيع التالية:

- [إنشاء نهج علبة بريد Outlook على ويب في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [تطبيق نهج علبة بريد Outlook على ويب علبة بريد أو إزالته على علبة بريد في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
