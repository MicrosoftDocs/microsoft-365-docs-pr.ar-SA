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
description: اكتشف خطوات الإعداد Microsoft 365 Business Premium، بما في ذلك إضافة مجال ومستخدمين وإعداد سياسات الأمان والمزيد.
ms.openlocfilehash: b4d12d34e535a58c952a752fca63af6f67e30a61
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575632"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>إعداد Microsoft 365 Business Premium في معالج الإعداد

## <a name="watch-overview-of-microsoft-365-setup"></a>شاهد: نظرة عامة Microsoft 365 الإعداد

شاهد هذا الفيديو للحصول على نظرة عامة Microsoft 365 Business Premium الإعداد.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>شاهد: إعداد Microsoft 365 Business Premium

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. سجل <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">الدخول إلى مركز مسؤولي Microsoft 365</a>، وحدد **الانتقال إلى الإعداد**. سيبدأ معالج الإعداد.
1. بعد اكتمال الإعداد، ارجع إلى مركز إدارة Microsoft. في مركز الإدارة، يمكنك متابعة إعداد ميزات مثل Windows 10 و DLP وما إلى ذلك في **صفحة** الإعداد.

## <a name="add-your-domain-users-and-set-up-policies"></a>إضافة مجالك والمستخدمين، إعداد السياسات

عند شراء Microsoft 365 Business Premium، يكون لديك خيار استخدام مجال تملكه، أو شراء مجال أثناء [التسجيل](../admin-overview/sign-up-for-office-365.md).

- إذا اشتريت مجالا جديدا عند تسجيل الدخول، تم إعداد مجالك، كما يمكنك الانتقال إلى إضافة مستخدمين [وتعيين تراخيص](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>إضافة مجالك ل تخصيص تسجيل الدخول

1. سجل [الدخول مركز مسؤولي Microsoft 365 باستخدام](https://admin.microsoft.com) بيانات اعتماد المسؤول العام. 

2. اختر **الانتقال إلى الإعداد** لبدء تشغيل المعالج.

    ![حدد الانتقال إلى الإعداد.](../../media/gotosetupinadmincenter.png)

3. في **صفحة تثبيت التطبيقات Office**، يمكنك تثبيت التطبيقات بشكل اختياري على الكمبيوتر الخاص بك.
    
4. في الخطوة **إضافة مجال** ، أدخل اسم المجال الذي تريد استخدامه (مثل contoso.com).

    > [!IMPORTANT]
    > إذا اشتريت مجالا أثناء التسجيل، لن ترى إضافة **خطوة مجال** هنا. انتقل إلى [إضافة مستخدمين بدلا](#add-users-and-assign-licenses) من ذلك.

    ![لقطة شاشة لصفحة تخصيص تسجيل الدخول.](../../media/adddomain.png)

    
4. اتبع الخطوات في المعالج لإنشاء [سجلات DNS لدى أي موفر استضافة DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) Microsoft 365 يتحقق من أنك تملك المجال. إذا كنت تعرف مضيف المجال، فشاهد [أيضا إضافة](/microsoft-365/admin/setup/add-domain) مجال Microsoft 365.

    إذا كان موفر الاستضافة الخاص بك هو GoDaddy أو مضيف آخر [](/office365/admin/get-help-with-domains/domain-connect)تم تمكينه باستخدام اتصال المجال، فإن العملية سهلة وستطلب منك تلقائيا تسجيل الدخول وتمكين Microsoft من المصادقة بالنيابة عنك.

    ![في صفحة تأكيد الوصول إلى GoDaddy، حدد تخويل.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين تراخيص

يمكنك إضافة مستخدمين في المعالج، ولكن يمكنك أيضا إضافة مستخدمين [لاحقا في مركز](../add-users/add-users.md) الإدارة. بالإضافة إلى ذلك، إذا كان لديك وحدة تحكم مجال محلية، يمكنك إضافة مستخدمين باستخدام [Azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>إضافة مستخدمين في المعالج

يتم تلقائيا تعيين ترخيص Microsoft 365 Business Premium المستخدمين الذين تضيفهم إلى المعالج.

![لقطة شاشة للصفحة "إضافة مستخدمين جدد" في المعالج.](../../media/addnewuserspage.png)

1. إذا كان Microsoft 365 Business Premium الاشتراك الخاص بك به مستخدمين موجودين (على سبيل المثال، إذا استخدمت Azure AD الاتصال)، يمكنك الحصول على خيار لتعيين التراخيص لهم الآن. يمكنك المضي قدما وإضافة التراخيص إليها أيضا.

2. بعد إضافة المستخدمين، ستحصل أيضا على خيار لمشاركة بيانات الاعتماد مع المستخدمين الجدد الذين أضفتها. يمكنك اختيار طباعتها أو مراسلتها عبر البريد الإلكتروني أو تنزيلها.

### <a name="connect-your-domain"></a>الاتصال مجالك

> [!NOTE]
> إذا اخترت استخدام مجال onmicrosoft. أو استخدمت Azure AD الاتصال لإعداد المستخدمين، لن ترى هذه الخطوة.
  
لإعداد الخدمات، يجب تحديث بعض السجلات لدى جهة تسجيل المجالات أو مضيف DNS.
  
1. يكشف معالج الإعداد عادة عن جهة التسجيل ويمنحك ارتباط إلى إرشادات مفصلة خطوة بخطوة لتحديث سجلات NS في موقع جهة التسجيل على الويب. وإذا لم يحدث ذلك، فغير أسماء الخدمات [لإعداد Microsoft 365 جهة تسجيل المجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - إذا كان لديك سجلات DNS موجودة، على سبيل المثال موقع ويب موجود، ولكن مضيف DNS تم تمكينه للاتصال المجال، فاختر **إضافة سجلات لي**.[](/office365/admin/get-help-with-domains/domain-connect) في الصفحة **اختيار الخدمات** عبر الإنترنت، اقبل كل الإعدادات الافتراضية، واختر التالي، واختر **تخويل** على صفحة مضيف DNS.
    - إذا كان لديك سجلات DNS موجودة مع مضيفي DNS آخرين (غير ممكن للاتصال بالمجال)، فسوف تحتاج إلى إدارة سجلات DNS الخاصة بك للتأكد من أن الخدمات الموجودة تبقى متصلة. لمزيد [من المعلومات، راجع أساسيات](/office365/admin/get-help-with-domains/dns-basics) المجال.

        ![صفحة تنشيط السجلات.](../../media/activaterecords.png)

2. اتبع الخطوات الواردة في المعالج، وسوف يتم إعداد البريد الإلكتروني والخدمات الأخرى لك.

### <a name="protect-your-organization"></a>حماية مؤسستك 

يتم تطبيق السياسات التي تقوم بإعدادها في المعالج تلقائيا على مجموعة [أمان](/office365/admin/create-groups/compare-groups#security-groups) تسمى *كافة المستخدمين*. يمكنك أيضا إنشاء مجموعات إضافية لتعيين سياسات لها في مركز الإدارة.

1. في "**زيادة الحماية** من التهديدات الإلكترونية المتقدمة"، من المستحسن قبول الإعدادات الافتراضية [Office 365 ملفات](../../security/office-365-security/defender-for-office-365.md) الفحص المتقدم للحماية من المخاطر والربط في Office التطبيقات.

    ![لقطة شاشة لصفحة "زيادة الحماية".](../../media/increasetreatprotection.png)


2. في **الصفحة** منع تسريب البيانات الحساسة، اقبل الإعدادات الافتراضية التي يجب تشغيلها في Office 365 منع فقدان البيانات (DLP) لتعقب البيانات الحساسة في تطبيقات Office ومنع المشاركة العرضية لهذه البيانات خارج مؤسستك.

3. في الصفحة **حماية البيانات في Office** الجوال، اترك إدارة تطبيقات الأجهزة المحمولة قيد تشغيلها، ثم قم بتوسيع الإعدادات ومراجعتها، ثم حدد إنشاء نهج إدارة **تطبيقات الأجهزة المحمولة**.

    ![لقطة شاشة لحماية البيانات في Office لصفحة الأجهزة المحمولة.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>أجهزة Windows 10 آمنة

على الجانب الأيسر من التنقل، حدد **إعداد**، ثم ضمن تسجيل الدخول **والأمان،** اختر تأمين Windows 10 الكمبيوتر. اختر **عرض** للبدء. راجع [تأمين أجهزة الكمبيوتر Windows 10 للحصول](secure-win-10-pcs.md) على الإرشادات الكاملة.

## <a name="deploy-office-365-client-apps"></a>نشر Office 365 العميل

إذا اخترت تثبيت تطبيقات Office تلقائيا أثناء الإعداد، سيتم تثبيت التطبيقات على أجهزة Windows 10 بمجرد تسجيل المستخدمين الدخول إلى Azure AD من أجهزة Windows الخاصة بهم، باستخدام بيانات اعتماد العمل الخاصة بهم.

لتثبيت الأجهزة Office الأجهزة المحمولة التي تعمل بنظام التشغيل iOS أو Android، راجع إعداد الأجهزة المحمولة [Microsoft 365 Business Premium المستخدمين](set-up-mobile-devices.md).

يمكنك أيضا تثبيت Office بشكل فردي. راجع [تثبيت Office على كمبيوتر شخصي أو Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) للحصول على الإرشادات.

## <a name="related-content"></a>المحتوى ذي الصلة

[Microsoft 365 الفيديو التدريبية للأعمال](../../business-video/index.yml) (صفحة الارتباط)
