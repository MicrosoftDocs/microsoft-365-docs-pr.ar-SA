---
title: إعداد Microsoft 365 Business Premium
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: اكتشف خطوات الإعداد Microsoft 365 Business Premium، بما في ذلك إضافة مجال ومستخدمين وإعداد نهج الأمان والمزيد.
ms.openlocfilehash: 69d158d7193a2f07c6b4c23557474f1458e2fb51
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935884"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>إعداد Microsoft 365 Business Premium في معالج الإعداد

## <a name="watch-overview-of-microsoft-365-setup"></a>المراقبة: نظرة عامة على إعداد Microsoft 365

شاهد هذا الفيديو للحصول على نظرة عامة حول إعداد Microsoft 365 Business Premium.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>المراقبة: إعداد Microsoft 365 Business Premium

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. سجل الدخول إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>، وحدد **"Go" للإعداد**. سيبدأ معالج الإعداد.
1. بعد اكتمال الإعداد، ارجع إلى مركز إدارة Microsoft. في مركز الإدارة، يمكنك متابعة إعداد ميزات مثل نهج Windows 10 وDLP وما إلى ذلك على صفحة **الإعداد**.

## <a name="add-your-domain-users-and-set-up-policies"></a>إضافة المجال والمستخدمين وإعداد النهج

عند شراء Microsoft 365 Business Premium، يتوفر لديك خيار استخدام مجال تملكه، أو شراء مجال أثناء [التسجيل](../admin-overview/sign-up-for-office-365.md).

- إذا اشتريت مجالا جديدا عند التسجيل، يتم إعداد مجالك بالكامل ويمكنك الانتقال إلى [إضافة مستخدمين وتعيين التراخيص](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>إضافة مجالك لتخصيص تسجيل الدخول

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات اعتماد المسؤول العمومي. 

2. اختر **"انتقال" للإعداد** لبدء تشغيل المعالج.

    ![حدد Go للإعداد.](../../media/gotosetupinadmincenter.png)

3. في صفحة **تثبيت تطبيقات Office**، يمكنك بشكل اختياري تثبيت التطبيقات على الكمبيوتر الخاص بك.
    
4. في الخطوة **"إضافة مجال** "، أدخل اسم المجال الذي تريد استخدامه (مثل contoso.com).

    > [!IMPORTANT]
    > إذا اشتريت مجالا أثناء التسجيل، فلن ترى خطوة **إضافة مجال** هنا. انتقل إلى [إضافة مستخدمين](#add-users-and-assign-licenses) بدلا من ذلك.

    ![لقطة شاشة لصفحة Personalize your sign-in.](../../media/adddomain.png)

    
4. اتبع الخطوات الواردة في المعالج [لإنشاء سجلات DNS لدى أي موفر استضافة DNS Microsoft 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) يتحقق من ملكيتك للمجال. إذا كنت تعرف مضيف المجال، فراجع أيضا [إضافة مجال إلى Microsoft 365](/microsoft-365/admin/setup/add-domain).

    إذا كان موفر الاستضافة هو GoDaddy أو مضيف آخر ممكن [مع اتصال المجال](/office365/admin/get-help-with-domains/domain-connect)، فإن العملية سهلة وستتم مطالبتك تلقائيا بتسجيل الدخول والسماح ل Microsoft بالمصادقة بالنيابة عنك.

    ![في صفحة تأكيد الوصول إلى GoDaddy، حدد Authorize.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين التراخيص

يمكنك إضافة مستخدمين في المعالج، ولكن يمكنك أيضا [إضافة مستخدمين لاحقا](../add-users/add-users.md) في مركز الإدارة. بالإضافة إلى ذلك، إذا كان لديك وحدة تحكم مجال محلية، يمكنك إضافة مستخدمين باستخدام [الاتصال Azure AD](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>إضافة مستخدمين في المعالج

يتم تعيين ترخيص Microsoft 365 Business Premium تلقائيا إلى أي مستخدمين تضيفهم في المعالج.

![لقطة شاشة لصفحة إضافة مستخدمين جدد في المعالج.](../../media/addnewuserspage.png)

1. إذا كان اشتراكك في Microsoft 365 Business Premium يحتوي على مستخدمين موجودين (على سبيل المثال، إذا استخدمت الاتصال Azure AD)، فستحصل على خيار لتعيين التراخيص لهم الآن. امضي قدما وأضف التراخيص إليها أيضا.

2. بعد إضافة المستخدمين، ستحصل أيضا على خيار لمشاركة بيانات الاعتماد مع المستخدمين الجدد الذين أضفتها. يمكنك اختيار طباعتها أو إرسالها بالبريد الإلكتروني أو تنزيلها.

### <a name="connect-your-domain"></a>الاتصال مجالك

> [!NOTE]
> إذا اخترت استخدام مجال .onmicrosoft، أو استخدمت Azure AD الاتصال لإعداد المستخدمين، فلن ترى هذه الخطوة.
  
لإعداد الخدمات، يجب تحديث بعض السجلات لدى مضيف DNS أو جهة تسجيل المجالات.
  
1. يكشف معالج الإعداد عادة عن جهة التسجيل ويمنحك ارتباطا إلى إرشادات مفصلة خطوة بخطوة لتحديث سجلات NS في موقع جهة التسجيل على ويب. إذا لم يحدث ذلك، [فقم بتغيير خوادم الأسماء لإعداد Microsoft 365 مع أي جهة تسجيل مجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - إذا كان لديك سجلات DNS موجودة، على سبيل المثال موقع ويب موجود، ولكن تم تمكين مضيف DNS [للاتصال بالمجال](/office365/admin/get-help-with-domains/domain-connect)، فاختر **إضافة سجلات بالنيابة عني**. في الصفحة **"اختيار خدمات الإنترنت**"، اقبل كل الإعدادات الافتراضية، واختر **"التالي**"، واختر **"تخويل"** على صفحة مضيف DNS.
    - إذا كان لديك سجلات DNS موجودة مع مضيفي DNS آخرين (غير ممكنين للاتصال بالمجال)، فسترغب في إدارة سجلات DNS الخاصة بك للتأكد من بقاء الخدمات الموجودة متصلة. راجع [أساسيات المجال](/office365/admin/get-help-with-domains/dns-basics) للحصول على مزيد من المعلومات.

        ![تنشيط صفحة السجلات.](../../media/activaterecords.png)

2. اتبع الخطوات الواردة في المعالج وسيتم إعداد البريد الإلكتروني والخدمات الأخرى لك.

### <a name="protect-your-organization"></a>حماية مؤسستك 

يتم تطبيق النهج التي قمت بإعدادها في المعالج تلقائيا على [مجموعة أمان](/office365/admin/create-groups/compare-groups#security-groups) تسمى *"كافة المستخدمين*". يمكنك أيضا إنشاء مجموعات إضافية لتعيين النهج إليها في مركز الإدارة.

1. حول **زيادة الحماية من التهديدات الإلكترونية المتقدمة**، يوصى بقبول الإعدادات الافتراضية للسماح [Office 365 Advanc Threat Protection](../../security/office-365-security/defender-for-office-365.md) بفحص الملفات والارتباطات في تطبيقات Office.

    ![لقطة شاشة لصفحة زيادة الحماية.](../../media/increasetreatprotection.png)


2. في صفحة **منع تسرب البيانات الحساسة**، اقبل الإعدادات الافتراضية لتشغيل Microsoft Purview Data Loss Prevention لتعقب البيانات الحساسة في تطبيقات Office ومنع المشاركة العرضية لهذه البيانات خارج مؤسستك.

3. في صفحة **حماية البيانات في Office للأجهزة المحمولة**، اترك إدارة تطبيقات الأجهزة المحمولة قيد التشغيل، وقم بتوسيع الإعدادات ومراجعتها، ثم حدد **إنشاء نهج إدارة تطبيقات الأجهزة المحمولة**.

    ![لقطة شاشة لحماية البيانات في Office لصفحة الجوال.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>أجهزة كمبيوتر Windows 10 آمنة

في جزء التنقل الأيمن، حدد **"إعداد**"، ثم ضمن **"تسجيل الدخول والأمان**"، اختر **"تأمين أجهزة الكمبيوتر Windows 10**". اختر **"عرض** " لبدء الاستخدام. اطلع على [تأمين أجهزة الكمبيوتر Windows 10](secure-win-10-pcs.md) للحصول على إرشادات كاملة.

## <a name="deploy-office-365-client-apps"></a>نشر تطبيقات عميل Office 365

إذا اخترت تثبيت تطبيقات Office تلقائيا أثناء الإعداد، فسيتم تثبيت التطبيقات على أجهزة Windows 10 بمجرد قيام المستخدمين بتسجيل الدخول إلى Azure AD من أجهزة Windows الخاصة بهم، باستخدام بيانات اعتماد العمل الخاصة بهم.

لتثبيت Office على الأجهزة المحمولة التي تعمل بنظام التشغيل iOS أو Android، راجع [إعداد الأجهزة المحمولة لمستخدمي Microsoft 365 Business Premium](set-up-mobile-devices.md).

يمكنك أيضا تثبيت Office بشكل فردي. راجع [تثبيت Office على كمبيوتر شخصي أو Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) للحصول على الإرشادات.

## <a name="related-content"></a>المحتويات ذات الصلة

[مقاطع فيديو Microsoft 365 للتدريب على الأعمال](../../business-video/index.yml) (صفحة الارتباط)
