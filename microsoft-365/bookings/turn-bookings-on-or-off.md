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
ms.openlocfilehash: a2ab25b3b187ba45dfe460991b91e77d70a2bb70
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715264"
---
# <a name="turn-microsoft-bookings-on-or-off"></a>تشغيل Microsoft Bookings أو إيقاف تشغيله

> [!NOTE]
> تساعدك هذه المقالة على التفاعل مع أحدث إصدار من Microsoft Bookings. سيتم إيقاف الإصدارات السابقة في الأشهر القادمة.

هذه المقالة مخصصة للمسؤولين. 

يمكن تشغيل Bookings أو إيقاف تشغيله لمؤسستك بأكملها أو لمستخدمين محددين. عند تشغيل Bookings للمستخدمين، يمكنهم إنشاء صفحة Bookings وإنشاء تقويم والسماح للأشخاص الآخرين بحجز الوقت معهم.

> [!NOTE]
> لا تتوفر عناصر تحكم المسؤول الموضحة في هذه الأقسام لعملاء Office 365 المشغلين بواسطة 21Vianet (الصين).

## <a name="turn-bookings-on-or-off-for-your-organization-using-the-microsoft-365-admin-center"></a>تشغيل Bookings أو إيقاف تشغيله لمؤسستك باستخدام مركز مسؤولي Microsoft 365

1. سجل الدخول إلى مركز مسؤولي Microsoft 365 كمسؤول عام.

2. في مركز الإدارة، انتقل إلى  **الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**إعدادات المؤسسة**</a>.

3. حدد خانة الاختيار **للسماح لمؤسستك باستخدام Bookings** لتمكين Bookings لمؤسستك أو تعطيلها.

   > [!NOTE]
   > سيؤدي إيقاف تشغيل Bookings إلى تعطيل جميع الوصول إلى الخدمة بما في ذلك إنشاء صفحات Bookings وإدارتها.

4. حدد **"حفظ التغييرات**".

### <a name="turn-bookings-on-or-off-for-your-organization-using-powershell"></a>تشغيل Bookings أو إيقاف تشغيلها لمؤسستك باستخدام PowerShell

لتشغيل Bookings أو إيقاف تشغيلها لمؤسستك باستخدام PowerShell cmdlet [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig)، [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) وتشغيل الأمر التالي:

```PowerShell
   Set-OrganizationConfig -BookingsEnabled $false
```

### <a name="granular-controls"></a>عناصر تحكم متعددة المستويات

استخدم الإعدادات أدناه للتحكم في الأشخاص الذين يمكنهم استخدام Bookings وتحديد المعلومات Bookings التي تتم مشاركتها وما إذا كان الموظفون بحاجة إلى الموافقة قبل إضافتهم إلى تقويم Booking.

:::image type="content" source="../media/control-access-sharing-bookings.png" alt-text="لقطة شاشة: الإعدادات التي تسمح لك بالتحكم في الأشخاص الذين يمكنهم استخدام Bookings، وتحديد المعلومات Bookings التي تتم مشاركتها وموافقة الموظفين":::

### <a name="block-bookings-from-outside-your-organization"></a>حظر الحجوزات من خارج مؤسستك

يمكنك إعداد Bookings حتى يتمكن الأشخاص في مؤسستك فقط من حجز المواعيد. يمكن فقط للمستخدمين في مؤسستك الذين سجلوا الدخول وتتم مصادقتهم حجز المواعيد.

### <a name="block-social-sharing-options"></a>حظر خيارات المشاركة الاجتماعية

يمكنك التحكم في كيفية مشاركة صفحات الحجز على الشبكات الاجتماعية. يتوفر هذا الإعداد في مركز مسؤولي Microsoft 365 ضمن إعدادات  -> **الإعدادات** ->  **Org** **Bookings**.

### <a name="block-sharing-staff-details-with-customers"></a>حظر مشاركة تفاصيل فريق العمل مع العملاء

لن يتم إرسال تفاصيل فريق العمل، مثل معلومات جهة الاتصال، إلى العملاء عبر البريد الإلكتروني أو أي اتصال آخر.

### <a name="require-staff-approvals-before-sharing-freebusy-information"></a>طلب موافقات الموظفين قبل مشاركة معلومات التوفر/الانشغال

يمكنك مطالبة الموظفين في مؤسستك بالاشتراك قبل مشاركة معلومات التوفر الخاصة بهم من خلال Bookings وقبل أن يتمكنوا من الحجز من خلال صفحة الحجز.

عند تمكين هذا الإعداد، سيتلقى الأشخاص الذين تمت إضافتهم كموظفون في تقويمات الحجز رسالة بريد إلكتروني تتضمن ارتباطا **للموافقة على الطلب/رفضه** .

## <a name="restrict-collection-of-customer-data"></a>تقييد جمع بيانات العميل

لأسباب تتعلق بالامتثال، قد لا ترغب في جمع بعض معلومات العملاء. إذا قمت بتحديد خانة اختيار لأي من هذه الخيارات، فلن يتم تضمين هذه الحقول في أي نماذج تظهر للعملاء أو العملاء.

:::image type="content" source="../media/restrict-collection-customer-data.png" alt-text="لقطة شاشة: حدد خانات الاختيار للمساعدة في منع العملاء من مشاركة البيانات الحساسة معك":::

### <a name="turn-bookings-on-or-off-for-individual-users"></a>تشغيل Bookings أو إيقاف تشغيلها للمستخدمين الفرديين

يمكنك تعطيل Bookings للمستخدمين الفرديين.

1. انتقل إلى مركز مسؤولي Microsoft 365، ثم حدد **المستخدمين النشطين للمستخدمين** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**النشطين**</a>.

1. حدد المستخدم المطلوب، ثم حدد **التراخيص والتطبيقات**.

1. قم بتوسيع **التطبيقات** ومسح خانة الاختيار Microsoft Bookings.

## <a name="allow-only-selected-users-to-create-bookings-calendars"></a>السماح للمستخدمين المحددين فقط بإنشاء تقويمات Bookings

باستخدام قيود النهج، يمكنك منع المستخدمين المرخصين من إنشاء تقويمات Bookings. يجب أولا تمكين Bookings لمؤسستك بأكملها. سيكون لدى جميع المستخدمين في مؤسستك تراخيص Bookings، ولكن يمكن فقط لهؤلاء المضمنين في النهج إنشاء تقويمات Bookings والتحكم الكامل في من يمكنه الوصول إلى التقويمات التي يقومون بإنشائها.

يمكن للمستخدمين المضمنين في هذا النهج إنشاء تقويمات Bookings جديدة ويمكن إضافتها كموظفون بأي سعة (بما في ذلك دور المسؤول) إلى تقويمات Bookings الموجودة. لن يتمكن المستخدمون غير المضمنين في هذا النهج من إنشاء تقويمات Bookings جديدة وسيتلقىون رسالة خطأ إذا حاولوا القيام بذلك.

ستحتاج إلى تشغيل الأوامر التالية باستخدام Exchange Online PowerShell. لمزيد من المعلومات حول تشغيل أوامر cmdlets Exchange Online، راجع [الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

> [!IMPORTANT]
> تفترض الخطوات أدناه أنه لم يتم إنشاء نهج أخرى لعلب بريد Outlook Web App (OWA) في مؤسستك.

1. إنشاء نهج علبة بريد جديد للمستخدمين الذين يجب السماح لهم بإنشاء تقويمات Bookings. (يسمح بإنشاء التقويم Bookings بشكل افتراضي بواسطة نهج علبة البريد الجديدة.)

   ```PowerShell
   New-OwaMailboxPolicy -Name "BookingsCreators"
   ```

   لمزيد من المعلومات، راجع [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy).

2. قم بتعيين هذا النهج للمستخدمين المعنيين عن طريق تشغيل هذا الأمر لكل مستخدم تريد منحه الإذن لإنشاء تقويمات Bookings.

   ```PowerShell
   Set-CASMailbox -Identity <someCreator@emailaddress> -OwaMailboxPolicy "BookingsCreators"
   ```

   لمزيد من المعلومات، راجع [Set-CASMailbox](/powershell/module/exchange/set-casmailbox).

3. اختياري: قم بتشغيل هذا الأمر إذا كنت تريد تعطيل Bookings لكافة المستخدمين الآخرين في مؤسستك.

   ```PowerShell
   Set-OwaMailboxPolicy "OwaMailboxPolicy-Default" -BookingsMailboxCreationEnabled:$false
   ```

   لمزيد من المعلومات، راجع [Set-OwaMailboxPolicy](/powershell/module/exchange/set-owamailboxpolicy).

لمزيد من المعلومات حول نهج علبة بريد OWA، راجع المواضيع التالية:

- [إنشاء نهج علبة بريد Outlook على ويب في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)

- [تطبيق نهج علبة بريد Outlook على ويب أو إزالته على علبة بريد في Exchange Online](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/create-outlook-web-app-mailbox-policy)
