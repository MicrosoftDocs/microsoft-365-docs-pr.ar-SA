---
title: إضافة مستخدمين وتعيين التراخيص في Microsoft 365
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- VSBFY23
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- MET150
description: تعرف على كيفية منح كل عضو في الفريق حساب مستخدم حتى يتمكن من الحصول على تراخيص Microsoft 365 وبيانات اعتماد تسجيل الدخول وعلب بريد Microsoft 365.
ms.date: 07/01/2020
ms.openlocfilehash: afcb3d0b3db8dbdbbd6cf870c1c148c73562c889
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084730"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>إضافة مستخدمين وتعيين التراخيص في الوقت نفسه

اطلع على [تعليمات Microsoft 365 للشركات الصغيرة](https://go.microsoft.com/fwlink/?linkid=2197659) على YouTube.

يحتاج كل من الأشخاص في فريقك إلى حساب مستخدم قبل أن يتمكنوا من تسجيل الدخول والوصول إلى [Microsoft 365 للأعمال](https://www.microsoft.com/microsoft-365/business). أسهل طريقة لإضافة حسابات المستخدمين هي إضافتها واحدة في كل مرة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>. بعد تنفيذ هذه الخطوة، يكون لدى المستخدمين تراخيص Microsoft 365 وبيانات اعتماد تسجيل الدخول وعلب بريد Microsoft 365.

> [!TIP]
> إذا كنت بحاجة إلى مساعدة في الخطوات الواردة في هذا الموضوع، ففكر في [العمل مع أحد متخصصي الشركات الصغيرة من Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام مساعد الأعمال، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى خبراء الشركات الصغيرة أثناء تنمية أعمالك، بدءا من الإلحاق إلى الاستخدام اليومي.

## <a name="before-you-begin"></a>قبل البدء

يجب أن تكون مسؤولا عموميا أو ترخيصا أو مسؤول مستخدم لإضافة مستخدمين وتعيين تراخيص. لمزيد من المعلومات، راجع [حول أدوار المسؤولين](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>شاهد: إضافة مستخدمين في طريقة عرض لوحة المعلومات

اطلع على هذا الفيديو وغيره على [قناتنا على YouTube](https://go.microsoft.com/fwlink/?linkid=2198205).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> تظهر الخطوات المستخدمة في الفيديو نقطة بداية مختلفة لإضافة مستخدمين، ولكن الخطوات المتبقية هي نفس الإجراء التالي.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>إضافة مستخدمين واحدا تلو الآخر في طريقة عرض لوحة المعلومات

:::image type="content" source="../../media/classic-admin-center.png" alt-text="لقطة شاشة: طريقة عرض لوحة معلومات مركز مسؤول":::

::: moniker range="o365-worldwide"

1. الانتقال إلى مركز الإدارة في <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. انتقل إلى **المستخدمين النشطين** > ، وحدد **"إضافة مستخدم**".
3. في جزء **"إعداد الأساسيات** "، املأ معلومات المستخدم الأساسية، ثم حدد **"التالي**".
    - **اسم** املأ الاسم الأول واسم العائلة واسم العرض واسم المستخدم.
    - **المجال** اختر المجال لحساب المستخدم. على سبيل المثال، إذا كان اسم المستخدم هو Jakob، وكان المجال contoso.com، فسيسجل دخوله باستخدام jakob@contoso.com.
    - **إعدادات كلمة المرور** اختر استخدام كلمة المرور التي تم إنشاؤها تلقائيا أو لإنشاء كلمة مرور قوية خاصة بك للمستخدم.
    - يجب على المستخدم تغيير كلمة المرور الخاصة به بعد 90 يوما. أو يمكنك اختيار **مطالبة هذا المستخدم بتغيير كلمة المرور الخاصة به عند تسجيل الدخول لأول مرة**.
    - اختر ما إذا كنت تريد إرسال كلمة المرور بالبريد الإلكتروني عند إضافة المستخدم.
4. في جزء **تعيين تراخيص المنتجات** ، حدد الموقع والترخيص المناسب للمستخدم. إذا لم يكن لديك أي تراخيص متوفرة، فلا يزال بإمكانك إضافة مستخدم وشراء تراخيص إضافية. قم بتوسيع **التطبيقات** وتحديد التطبيقات أو إلغاء تحديدها للحد من التطبيقات التي يملك المستخدم ترخيصا لها. حدد **التالي**.
5. في جزء **الإعدادات الاختيارية** ، قم بتوسيع **Roles** لجعل هذا المستخدم مسؤولا. قم بتوسيع **معلومات ملف التعريف** لإضافة معلومات إضافية حول المستخدم.
6. حدد **"التالي**"، راجع إعدادات المستخدم الجديد، وقم بإجراء أي تغييرات تريدها، ثم حدد **"إنهاء الإضافة**"، ثم **"إغلاق**".

## <a name="add-a-user-in-the-admin-simplified-view"></a>إضافة مستخدم في طريقة العرض المبسطة للمسؤول

إذا كنت ترى هذه الصفحة في مركز الإدارة، فأنت في **طريقة العرض المبسطة للمسؤول**. اتبع الخطوات أدناه لإضافة مستخدم.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="لقطة شاشة: طريقة عرض مركز الإدارة المبسطة":::

::: moniker range="o365-worldwide"

1. الانتقال إلى مركز الإدارة في <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. حدد **إنشاء حساب لشخص آخر**.
3. في صفحة **"إضافة حساب مستخدم** "، قم بتعبئة الاسم الأول واسم العائلة واسم العرض واسم المستخدم الذي سيستخدمانه لتسجيل الدخول.
4. أضف عنوان البريد الإلكتروني للمستخدم في **ما يصل إلى 5 عناوين بريد إلكتروني...** مربع نص. سيؤدي ذلك إلى التأكد من حصول المستخدم الجديد على المعلومات التي يحتاجها لتسجيل الدخول إلى خدمات Microsoft 365.
5. حدد **إضافة مستخدم** **وتنزيل معلومات تسجيل الدخول** إذا كنت تريد حفظ هذه المعلومات.

## <a name="add-multiple-users-at-the-same-time"></a>إضافة عدة مستخدمين في الوقت نفسه

يمكنك استخدام أي من الأساليب التالية لإضافة عدة مستخدمين في الوقت نفسه:

- **استخدم جدول بيانات لإضافة أشخاص بشكل مجمع.** راجع [إضافة عدة مستخدمين في الوقت نفسه](../../enterprise/add-several-users-at-the-same-time.md).
- **أتمتة إضافة الحسابات وتعيين التراخيص.** راجع [إنشاء حسابات المستخدمين باستخدام Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). اختر هذا الأسلوب إذا كنت على دراية بالفعل باستخدام أوامر cmdlets Windows PowerShell.
- **هل تستخدم ActiveDirectory؟** [إعداد مزامنة الدليل ل Microsoft 365](../../enterprise/set-up-directory-synchronization.md). استخدم أداة الاتصال Azure AD لنسخ حسابات مستخدمي Active Directory (وعناصر Active Directory الأخرى) في Microsoft 365. تضيف المزامنة حسابات المستخدمين فقط. يجب تعيين تراخيص للمستخدمين الذين تمت مزامنتهم قبل أن يتمكنوا من استخدام البريد الإلكتروني وتطبيقات Office الأخرى.
- **هل تقوم بالترحيل من Exchange؟** راجع [طرق ترحيل حسابات بريد إلكتروني متعددة إلى Office 365](/Exchange/mailbox-migration/mailbox-migration). عند ترحيل علب بريد متعددة إلى Microsoft 365 باستخدام أسلوب Exchange الكلي أو المرحلي أو المختلط، يمكنك إضافة مستخدمين تلقائيا كجزء من الترحيل. يضيف الترحيل حسابات المستخدمين فقط. يجب تعيين تراخيص للمستخدمين قبل أن يتمكنوا من استخدام البريد الإلكتروني وتطبيقات Office الأخرى. إذا لم تقم بتعيين ترخيص لمستخدم، يتم تعطيل علبة البريد الخاصة به بعد فترة سماح مدتها 30 يوما. تعرف على كيفية [تعيين تراخيص للمستخدمين](../manage/assign-licenses-to-users.md) في مركز مسؤولي Microsoft 365.

## <a name="next-steps"></a>الخطوات التالية

بعد إضافة مستخدم، تتلقى إعلاما بالبريد الإلكتروني من Microsoft. يحتوي البريد الإلكتروني على معرف المستخدم وكلمة المرور للشخص حتى يتمكنوا من تسجيل الدخول إلى Microsoft 365. استخدم العملية العادية لتوصيل كلمات مرور جديدة. شارك [دليل التشغيل السريع للموظف](../setup/employee-quick-setup.md) مع المستخدمين الجدد لإعداد أشياء، مثل كيفية [تنزيل تطبيقات Office وتثبيتها على كمبيوتر شخصي أو Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) وكيفية [إعداد تطبيقات Office والبريد الإلكتروني على جهاز محمول](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>المحتويات ذات الصلة

[إضافة موظف جديد إلى Microsoft 365](add-new-employee.md) (مقال)\
[إضافة عدة مستخدمين في الوقت نفسه إلى Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (مقال)\
[استعادة مستخدم في Microsoft 365](restore-user.md) (مقال)\
[تعيين تراخيص للمستخدمين](../manage/assign-licenses-to-users.md) (مقالة)\
[حذف مستخدم من مؤسستك](delete-a-user.md) (مقالة)
