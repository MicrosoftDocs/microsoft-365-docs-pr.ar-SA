---
title: إعداد Microsoft 365 Business Standard بمجال جديد أو موجود
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- BEA160
description: عند شراء Microsoft 365 Business Standard، يتوفر لديك خيار استخدام مجال تملكه، أو شراء مجال أثناء التسجيل.
ms.openlocfilehash: d5504edaff4c9d406d218d8ab8333b6d50af406e
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66573880"
---
# <a name="set-up-microsoft-365-business-standard-with-a-new-or-existing-domain"></a>إعداد Microsoft 365 Business Standard بمجال جديد أو موجود

عند شراء Microsoft 365 Business Standard، يتوفر لديك خيار إضافة مجال تملكه، أو شراء مجال. تحقق من [التسجيل للحصول على اشتراك Microsoft 365 Business Standard](../simplified-signup/signup-business-standard.md).

في هذه المقالة، سنرشدك خلال خطوات إضافة مجال موجود تملكه بالفعل أو شراء مجال جديد. إذا اشتريت مجالا جديدا عند التسجيل، يتم إعداد مجالك بالكامل ويمكنك الانتقال إلى [إضافة مستخدمين وتعيين التراخيص](#add-users-and-assign-licenses).

> [!Tip]
> إذا كان لديك اشتراك Microsoft 365 Business Premium، فالرجاء مراجعة [إعداد Microsoft 365 Business Premium](../../business-premium/m365bp-setup.md).

## <a name="set-up-microsoft-365-for-business"></a>إعداد Microsoft 365 للأعمال

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ]

## <a name="before-you-begin"></a>قبل البدء

لإضافة المجالات أو تعديلها أو إزالتها، يجب أن تكون مسؤولا عاما. لمزيد من المعلومات، راجع ["حول أدوار المسؤول](../add-users/about-admin-roles.md)".

> [!IMPORTANT]
> يصبح الشخص الذي يقوم بالتسجيل للحصول على Microsoft 365 للأعمال (عادة مالك الشركة) المسؤول التقني للمؤسسة تلقائيا. يمكنك إضافة أشخاص آخرين كمسؤولين إذا كنت تريد المساعدة في إدارة خدمات Microsoft 365. اطلع على [تعيين أدوار المسؤولين](../add-users/assign-admin-roles.md) للحصول على مزيد من المعلومات.

## <a name="watch-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>شاهد: إضافة مجال موجود إلى اشتراكك في Microsoft 365 Business Standard

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu]

## <a name="steps-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>الخطوات: إضافة مجال موجود إلى اشتراكك في Microsoft 365 Business Standard

1. من صفحة **كيفية تسجيل الدخول** في Microsoft 365 Business Standard التسجيل، اختر **إنشاء حساب بريد إلكتروني جديد للأعمال (متقدم).**

2. في صفحة **"تثبيت تطبيقات Office** "، يمكنك بشكل اختياري تثبيت التطبيقات على الكمبيوتر الخاص بك.

3. في الخطوة **"إضافة مجال** "، أدخل اسم المجال الذي تريد استخدامه (مثل contoso.com).

    > [!IMPORTANT]
    > إذا اشتريت مجالا أثناء التسجيل، فلن ترى خطوة **إضافة مجال** هنا. انتقل إلى [إضافة مستخدمين](#add-users-and-assign-licenses) بدلا من ذلك.

4. اتبع الخطوات [لإنشاء سجلات DNS لدى أي موفر استضافة DNS Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) يتحقق من ملكيتك للمجال. إذا كنت تعرف مضيف المجال، فراجع أيضا [إضافة مجال إلى Microsoft 365](/microsoft-365/admin/setup/add-domain).

    إذا كان موفر الاستضافة هو GoDaddy أو مضيف آخر ممكن [مع اتصال المجال](/office365/admin/get-help-with-domains/domain-connect)، فإن العملية سهلة وستتم مطالبتك تلقائيا بتسجيل الدخول والسماح ل Microsoft بالمصادقة بالنيابة عنك.

    ![في صفحة تأكيد الوصول إلى GoDaddy، حدد Authorize.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين التراخيص

يمكنك إضافة مستخدمين الآن، ولكن يمكنك أيضا [إضافة مستخدمين لاحقا](../add-users/add-users.md) في مركز الإدارة.

يتم تعيين ترخيص Microsoft 365 Business Standard تلقائيا إلى أي مستخدمين تضيفهم.

1. إذا كان اشتراكك في Microsoft 365 Business Standard يحتوي على مستخدمين موجودين، فستحصل على خيار تعيين تراخيص لهم الآن. امضي قدما وأضف التراخيص إليها أيضا.

2. بعد إضافة المستخدمين، ستحصل أيضا على خيار لمشاركة بيانات الاعتماد مع المستخدمين الجدد الذين أضفتها. يمكنك اختيار طباعتها أو إرسالها بالبريد الإلكتروني أو تنزيلها.

## <a name="connect-your-domain"></a>توصيل مجالك
  
لإعداد الخدمات، يجب تحديث السجلات لدى مضيف DNS أو جهة تسجيل المجالات.
  
1. يكشف معالج الإعداد عادة عن جهة التسجيل ويمنحك ارتباطا إلى إرشادات مفصلة خطوة بخطوة لتحديث سجلات NS في موقع جهة التسجيل على ويب. إذا لم يحدث ذلك، [فقم بتغيير خوادم الأسماء لإعداد Office 365 مع أي جهة تسجيل مجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md).

    - إذا كان لديك سجلات DNS موجودة، على سبيل المثال موقع ويب موجود، ولكن تم تمكين مضيف DNS [للاتصال بالمجال](/office365/admin/get-help-with-domains/domain-connect)، فاختر **إضافة سجلات بالنيابة عني**. في الصفحة **"اختيار خدمات الإنترنت**"، اقبل كل الإعدادات الافتراضية، واختر **"التالي**"، واختر **"تخويل"** على صفحة مضيف DNS.
    - إذا كان لديك سجلات DNS موجودة مع مضيفي DNS آخرين (غير ممكنين للاتصال بالمجال)، فسترغب في إدارة سجلات DNS الخاصة بك للتأكد من بقاء الخدمات الموجودة متصلة. راجع [أساسيات المجال](/office365/admin/get-help-with-domains/dns-basics) للحصول على مزيد من المعلومات.

2. اتبع الخطوات الواردة في المعالج وسيتم إعداد البريد الإلكتروني والخدمات الأخرى لك.

    عند اكتمال عملية التسجيل، سيتم توجيهك إلى مركز الإدارة، حيث ستتبع معالجا لتثبيت تطبيقات Office، وإضافة مجالك، وإضافة مستخدمين، وتعيين التراخيص. بعد إكمال الإعداد الأولي، يمكنك استخدام صفحة **الإعداد** في مركز الإدارة لمتابعة إعداد الخدمات التي تأتي مع اشتراكاتك وتكوينها.

    لمزيد من المعلومات حول معالج الإعداد وصفحة **إعداد** مركز الإدارة، راجع [الفرق بين معالج الإعداد وصفحة الإعداد](o365-setup-wizard-and-setup-page.md).

## <a name="watch-set-up-business-email-with-a-new-domain"></a>شاهد: إعداد البريد الإلكتروني للأعمال باستخدام مجال جديد

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>الخطوات: إعداد البريد الإلكتروني للأعمال باستخدام مجال جديد

1. من صفحة **كيفية تسجيل الدخول** في Microsoft 365 Business Standard التسجيل، اختر **إنشاء حساب بريد إلكتروني جديد للأعمال (متقدم).**

2. اتبع الخطوات لشراء مجال جديد وأدخل اسم المجال الذي تريد استخدامه (مثل contoso.com). بعد الانتهاء من شراء مجالك، يمكنك [إضافة مستخدمين وتراخيص](../add-users/add-users.md) وتثبيت تطبيقات Office في مركز الإدارة.

## <a name="finish-setting-up"></a>إنهاء الإعداد

اتبع الخطوات أدناه لإعداد Outlook وTeams وOneDrive وموقع الويب الخاص بك.

### <a name="step-set-up-outlook-for-email"></a>الخطوة: إعداد Outlook للبريد الإلكتروني

1. في قائمة البدء في Windows، ابحث عن Outlook وحدده.

    (إذا كنت تستخدم جهاز Mac، فافتح Outlook من شريط الأدوات أو حدد موقعه باستخدام "الباحث".)

    إذا قمت بتثبيت Outlook للتو، فحدد **"التالي**" في صفحة الترحيب.

2. اختر **"إضافة حساب لمعلومات** \> **الملف**\>".

3. أدخل عنوان بريدك الإلكتروني في Microsoft وحدد **Connect**.

## <a name="watch-set-up-outlook-for-email"></a>مشاهدة: إعداد Outlook للبريد الإلكتروني

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
المزيد في [إعداد Outlook للبريد الإلكتروني](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>استيراد البريد الإلكتروني

إذا كنت تستخدم Outlook مع حساب بريد إلكتروني آخر، يمكنك استيراد البريد الإلكتروني والتقويم وجهات الاتصال السابقة إلى حساب Microsoft الجديد.
  
1. **تصدير بريدك الإلكتروني القديم**

    في Outlook، اختر **File** \> **Open &amp; Export** \> **Import/Export**.

    حدد **"تصدير إلى ملف"** ثم اتبع الخطوات لتصدير ملف بيانات Outlook (pst.) وأي مجلدات فرعية.

2. **استيراد البريد الإلكتروني القديم**

    في Outlook، اختر **"فتح ملف** \> **&amp; تصدير** \> **استيراد/تصدير**" مرة أخرى.

    هذه المرة، حدد **"استيراد" من برنامج أو ملف آخر** واتبع الخطوات لاستيراد ملف النسخ الاحتياطي الذي أنشأته عند تصدير بريدك الإلكتروني القديم.

## <a name="watch-import-and-redirect-email"></a>المراقبة: استيراد البريد الإلكتروني وإعادة توجيهه

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
المزيد عند [استيراد البريد الإلكتروني باستخدام Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

يمكنك أيضا استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> لاستيراد البريد الإلكتروني للجميع. لمزيد من المعلومات، راجع [ترحيل حسابات بريد إلكتروني متعددة](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>إعداد Microsoft Teams وOneDrive للأعمال

حدد أيقونة سحابة OneDrive من شريط المهام واتبع الخطوات لنقل ملفاتك إلى مجلد OneDrive for Business الجديد. حدد **"التالي** " لإعداد Microsoft Teams.

1. افتح Microsoft Teams، وحدد أيقونة ملف التعريف الخاص بك، ثم **أضف حساب العمل أو المؤسسة التعليمية**. اتبع الخطوات لإضافة حسابك الجديد إلى Teams.

## <a name="use-a-public-website"></a>استخدام موقع ويب عام

لا يتضمن Microsoft 365 موقعا عاما على ويب لأعمالك. إذا كنت تريد إعداد واحد، ففكر في استخدام شريك Microsoft، مثل GoDaddy أو WIX.
  
1. من مركز الإدارة، انتقل إلى **الموارد**، ثم حدد **موقع ويب عام**.

2. حدد **"معرفة المزيد** " ضمن أحد الخيارات، ثم قم بالتسجيل مع شريك موقع ويب واستخدم أدواته لإعداد موقعك وتصميمه.

## <a name="watch-create-your-business-website"></a>شاهد: إنشاء موقع ويب الأعمال

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>دعوة المستخدمين للانضمام إلى اشتراكك والمؤسسة

بمجرد إعداد مؤسستك، يمكنك دعوة مستخدمين آخرين للانضمام إلى اشتراكك في Microsoft 365 Business. سيحصلون على حق الوصول إلى جميع ميزات الاشتراك.

[دعوة المستخدمين إلى اشتراكي](../simplified-signup/admin-invite-business-standard.md)

دع المستخدمين يعرفون أنه يمكنهم اتباع الخطوات الواردة في المقالات أدناه للانضمام إلى مؤسستك والاشتراك.

- [قبول دعوة بالبريد الإلكتروني](../simplified-signup/user-invite-business-standard.md)

- [قبول دعوة بالبريد الإلكتروني باستخدام حساب Outlook أو Yahoo أو Gmail أو حساب آخر (مستخدم)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>المواضيع ذات الصلة

[ترحيل البيانات إلى اشتراكي في Microsoft 365 Business Standard](../simplified-signup/migrate-data-business-standard.md)
