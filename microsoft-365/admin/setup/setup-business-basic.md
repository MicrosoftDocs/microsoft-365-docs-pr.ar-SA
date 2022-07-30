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
- VSBFY23
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
- BEA160
description: تعرف على كيفية إعداد اشتراكك في Microsoft 365 Business Basic.
ms.openlocfilehash: 4ec614051eef61c51597da160b3030c6ba8aad07
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084840"
---
# <a name="set-up-microsoft-365-business-basic"></a>إعداد Microsoft 365 Business Basic

## <a name="watch-set-up-microsoft-365-business-basic"></a>المراقبة: إعداد Microsoft 365 Business Basic

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

إذا وجدت هذا الفيديو مفيدا، فراجع [سلسلة التدريب الكاملة للشركات الصغيرة وتلك الجديدة على Microsoft 365](../../business-video/index.yml).

## <a name="add-your-domain-to-personalize-sign-in"></a>إضافة مجالك لتخصيص تسجيل الدخول

عند شراء Microsoft 365 Business Basic، يتوفر لديك خيار استخدام مجال تملكه، أو شراء مجال أثناء التسجيل.

- إذا اشتريت مجالا جديدا عند التسجيل، يتم إعداد مجالك بالكامل ويمكنك الانتقال إلى [إضافة مستخدمين وتعيين التراخيص](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. اختر **"انتقال" للإعداد** لبدء تشغيل المعالج.
    
3. في الخطوة **"إضافة مجال** "، أدخل اسم المجال الذي تريد استخدامه (مثل contoso.com).

    > [!IMPORTANT]
    > إذا اشتريت مجالا أثناء التسجيل، فلن ترى خطوة **إضافة مجال** هنا. انتقل إلى [إضافة مستخدمين](#add-users-and-assign-licenses) بدلا من ذلك.

    
4. اتبع الخطوات الواردة في المعالج [لإنشاء سجلات DNS لدى أي موفر استضافة DNS Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) يتحقق من ملكيتك للمجال. إذا كنت تعرف مضيف المجال، فراجع أيضا [إضافة مجال إلى Microsoft 365](/microsoft-365/admin/setup/add-domain).

    إذا كان موفر الاستضافة هو GoDaddy أو مضيف آخر ممكن [مع اتصال المجال](/office365/admin/get-help-with-domains/domain-connect)، فإن العملية سهلة وستتم مطالبتك تلقائيا بتسجيل الدخول والسماح ل Microsoft بالمصادقة بالنيابة عنك.

    ![في صفحة تأكيد الوصول إلى GoDaddy، حدد Authorize.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>إضافة مستخدمين وتعيين التراخيص

يمكنك إضافة مستخدمين في المعالج، ولكن يمكنك أيضا [إضافة مستخدمين لاحقا](../add-users/add-users.md) في مركز الإدارة. بالإضافة إلى ذلك، إذا كان لديك وحدة تحكم مجال محلية، يمكنك إضافة مستخدمين باستخدام [Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>إضافة مستخدمين في المعالج

يتم تعيين ترخيص Microsoft 365 Business Basic تلقائيا إلى أي مستخدمين تضيفهم في المعالج.

1. إذا كان اشتراكك في Microsoft 365 Business Basic يحتوي على مستخدمين موجودين (على سبيل المثال، إذا استخدمت Azure AD Connect)، فستحصل على خيار لتعيين تراخيص لهم الآن. امضي قدما وأضف التراخيص إليها أيضا.

2. بعد إضافة المستخدمين، ستحصل أيضا على خيار لمشاركة بيانات الاعتماد مع المستخدمين الجدد الذين أضفتها. يمكنك اختيار طباعتها أو إرسالها بالبريد الإلكتروني أو تنزيلها.

## <a name="connect-your-domain"></a>توصيل مجالك

> [!NOTE]
> إذا اخترت استخدام مجال .onmicrosoft، أو استخدمت Azure AD Connect لإعداد المستخدمين، فلن ترى هذه الخطوة.
  
لإعداد الخدمات، يجب تحديث بعض السجلات لدى مضيف DNS أو جهة تسجيل المجالات.
  
1. يكشف معالج الإعداد عادة عن جهة التسجيل ويمنحك ارتباطا إلى إرشادات مفصلة خطوة بخطوة لتحديث سجلات NS في موقع جهة التسجيل على ويب. إذا لم يحدث ذلك، [فقم بتغيير خوادم الأسماء لإعداد Office 365 مع أي جهة تسجيل مجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - إذا كان لديك سجلات DNS موجودة، على سبيل المثال موقع ويب موجود، ولكن تم تمكين مضيف DNS [للاتصال بالمجال](/office365/admin/get-help-with-domains/domain-connect)، فاختر **إضافة سجلات بالنيابة عني**. في الصفحة **"اختيار خدمات الإنترنت**"، اقبل كل الإعدادات الافتراضية، واختر **"التالي**"، واختر **"تخويل"** على صفحة مضيف DNS.
    - إذا كان لديك سجلات DNS موجودة مع مضيفي DNS آخرين (غير ممكنين للاتصال بالمجال)، فسترغب في إدارة سجلات DNS الخاصة بك للتأكد من بقاء الخدمات الموجودة متصلة. راجع [أساسيات المجال](/office365/admin/get-help-with-domains/dns-basics) للحصول على مزيد من المعلومات.

2. اتبع الخطوات الواردة في المعالج وسيتم إعداد البريد الإلكتروني والخدمات الأخرى لك.

    عند اكتمال عملية التسجيل، سيتم توجيهك إلى مركز الإدارة، حيث يمكنك إضافة مستخدمين وتعيين التراخيص. بعد إكمال الإعداد الأولي، يمكنك استخدام صفحة **الإعداد** في مركز الإدارة لمتابعة إعداد الخدمات التي تأتي مع اشتراكاتك وتكوينها.

    لمزيد من المعلومات حول معالج الإعداد وصفحة **إعداد** مركز الإدارة، راجع [الفرق بين معالج الإعداد وصفحة الإعداد](o365-setup-wizard-and-setup-page.md).