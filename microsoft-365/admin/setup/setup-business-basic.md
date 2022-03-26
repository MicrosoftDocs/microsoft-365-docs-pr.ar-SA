---
title: إعداد Microsoft 365 Business Basic
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
search.appverid:
- MET150
- MOE150
- BEA160
description: تعرف على كيفية إعداد اشتراكك في Microsoft 365 Business Basic.
ms.openlocfilehash: e7c616936f045bc4266c24b65342451ffeff43ef
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63569298"
---
# <a name="set-up-microsoft-365-business-basic"></a>إعداد Microsoft 365 Business Basic

## <a name="watch-set-up-microsoft-365-business-basic"></a>شاهد: إعداد Microsoft 365 Business Basic

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

إذا وجدت هذا الفيديو مفيدا، فتحقق من سلسلة التدريب الكاملة للشركات الصغيرة وتلك الجديدة [Microsoft 365.](../../business-video/index.yml)

## <a name="add-your-domain-to-personalize-sign-in"></a>إضافة مجالك ل تخصيص تسجيل الدخول

عند شراء Microsoft 365 Business Basic، يكون لديك خيار استخدام مجال تملكه، أو شراء مجال أثناء التسجيل.

- إذا اشتريت مجالا جديدا عند تسجيل الدخول، تم إعداد مجالك، كما يمكنك الانتقال إلى إضافة مستخدمين [وتعيين تراخيص](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. اختر **الانتقال إلى الإعداد** لبدء تشغيل المعالج.
    
3. في الخطوة **إضافة مجال** ، أدخل اسم المجال الذي تريد استخدامه (مثل contoso.com).

    > [!IMPORTANT]
    > إذا اشتريت مجالا أثناء التسجيل، لن ترى إضافة **خطوة مجال** هنا. انتقل إلى [إضافة مستخدمين بدلا](#add-users-and-assign-licenses) من ذلك.

    
4. اتبع الخطوات في المعالج لإنشاء [سجلات DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) لدى أي موفر استضافة DNS Office 365 يتحقق من أنك تملك المجال. إذا كنت تعرف مضيف المجال، فشاهد [أيضا إضافة](/microsoft-365/admin/setup/add-domain) مجال Microsoft 365.

    إذا كان موفر الاستضافة الخاص بك هو GoDaddy أو مضيف آخر [](/office365/admin/get-help-with-domains/domain-connect)تم تمكينه باستخدام اتصال المجال، فإن العملية سهلة وستطلب منك تلقائيا تسجيل الدخول وتمكين Microsoft من المصادقة بالنيابة عنك.

    ![في صفحة تأكيد الوصول إلى GoDaddy، حدد تخويل.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين تراخيص

يمكنك إضافة مستخدمين في المعالج، ولكن يمكنك أيضا إضافة مستخدمين [لاحقا في مركز](../add-users/add-users.md) الإدارة. بالإضافة إلى ذلك، إذا كان لديك وحدة تحكم مجال محلية، يمكنك إضافة مستخدمين باستخدام [Azure AD الاتصال](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>إضافة مستخدمين في المعالج

يتم تلقائيا تعيين ترخيص Microsoft 365 Business Basic المستخدمين الذين تضيفهم إلى المعالج.

1. إذا كان Microsoft 365 Business Basic اشتراكك فيه مستخدمين موجودين (على سبيل المثال، إذا استخدمت Azure AD الاتصال)، يمكنك الحصول على خيار لتعيين التراخيص لهم الآن. يمكنك المضي قدما وإضافة التراخيص إليها أيضا.

2. بعد إضافة المستخدمين، ستحصل أيضا على خيار لمشاركة بيانات الاعتماد مع المستخدمين الجدد الذين أضفتها. يمكنك اختيار طباعتها أو مراسلتها عبر البريد الإلكتروني أو تنزيلها.

## <a name="connect-your-domain"></a>الاتصال مجالك

> [!NOTE]
> إذا اخترت استخدام مجال onmicrosoft. أو استخدمت Azure AD الاتصال لإعداد المستخدمين، لن ترى هذه الخطوة.
  
لإعداد الخدمات، يجب تحديث بعض السجلات لدى جهة تسجيل المجالات أو مضيف DNS.
  
1. يكشف معالج الإعداد عادة عن جهة التسجيل ويمنحك ارتباط إلى إرشادات مفصلة خطوة بخطوة لتحديث سجلات NS في موقع جهة التسجيل على الويب. وإذا لم يحدث ذلك، فغير أسماء الخدمات لإعداد [Office 365 جهة تسجيل المجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - إذا كان لديك سجلات DNS موجودة، على سبيل المثال موقع ويب موجود، ولكن مضيف DNS تم تمكينه للاتصال المجال، فاختر **إضافة سجلات لي**.[](/office365/admin/get-help-with-domains/domain-connect) في الصفحة **اختيار الخدمات** عبر الإنترنت، اقبل كل الإعدادات الافتراضية، واختر التالي، واختر **تخويل** على صفحة مضيف DNS.
    - إذا كان لديك سجلات DNS موجودة مع مضيفي DNS آخرين (غير ممكن للاتصال بالمجال)، فسوف تحتاج إلى إدارة سجلات DNS الخاصة بك للتأكد من أن الخدمات الموجودة تبقى متصلة. لمزيد [من المعلومات، راجع أساسيات](/office365/admin/get-help-with-domains/dns-basics) المجال.

2. اتبع الخطوات الواردة في المعالج، وسوف يتم إعداد البريد الإلكتروني والخدمات الأخرى لك.

    عند اكتمال عملية التسجيل، سيتم توجيهك إلى مركز الإدارة، حيث يمكنك إضافة مستخدمين وتعيين تراخيص. بعد إكمال الإعداد الأولي، يمكنك استخدام صفحة الإعداد في مركز  الإدارة لمواصلة إعداد الخدمات التي تأتي مع اشتراكاتك وتكوينها.

    لمزيد من المعلومات حول معالج الإعداد وصفحة إعداد مركز الإدارة، راجع الفرق بين معالج [الإعداد وصفحة الإعداد](o365-setup-wizard-and-setup-page.md).