---
title: إضافة مجال إلى Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- business_assist
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: استخدم معالج الإعداد لإضافة مجالك Microsoft 365 في مركز مسؤولي Microsoft 365 عن طريق إضافة سجل DNS لدى مضيف DNS.
ms.openlocfilehash: fa809486b968c4bc0f8c74e466285ee2ce9ac895
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567519"
---
# <a name="add-a-domain-to-microsoft-365"></a>إضافة مجال إلى Microsoft 365

 **[تحقق من الأسئلة الشائعة](domains-faq.yml)** حول المجالات إذا لم تعثر على ما تبحث عنه. 
  
## <a name="before-you-begin"></a>قبل البدء

لإضافة مجالات أو تعديلها أو إزالتها، يجب أن  تكون مسؤول اسم  المجال أو المسؤول **العام** لخطة [عمل أو مؤسسة](https://products.office.com/business/office). تؤثر هذه التغييرات على المستأجر بكامله؛ *لن يتمكن المسؤولون* *المخصصون* أو المستخدمون العاديون من إجراء هذه التغييرات.

> [!TIP]
> إذا كنت بحاجة إلى مساعدة بشأن الخطوات في هذا الموضوع، فنظر [في العمل مع أحد متخصصي Microsoft small business](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام "المساعدة في العمل"، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى المتخصصين في الشركات الصغيرة بينما تنمو أعمالك، من التكهين إلى الاستخدام اليومي.

## <a name="watch-add-a-domain"></a>شاهد: إضافة مجال

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

قد تحتاج شركتك إلى أسماء مجالات متعددة لأغراض مختلفة. على سبيل المثال، قد ترغب في إضافة هجاء مختلف لاسم شركتك لأن العملاء يستخدمونه بالفعل وفشلت اتصالاتهم في الوصول لك.

1. في مركز مسؤولي Microsoft 365، اختر <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**إعداد**</a>.
1. ضمن **إعداد مجالك المخصص،** حدد **ViewManageAdd** >  >  **المجال**.
1. أدخل اسم المجال الجديد الذي تريد إضافته، ثم حدد **التالي**.
1. سجل الدخول إلى جهة تسجيل المجالات، ثم حدد **التالي**.
1. اختر الخدمات لمجالك الجديد.
1. حدد **NextAuthorizeNext** >  > ، ثم **إنهاء**. لقد تم إضافة مجالك الجديد.

## <a name="add-a-domain"></a>إضافة مجال

اتبع هذه الخطوات لإضافة مجال أو إعداده أو متابعة إعداده. 

::: moniker range="o365-worldwide"

1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. انتقل إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. انتقل إلى **صفحة الإعدادات** >  **Domains**. 

3. حدد **إضافة مجال**.
    
4. أدخل اسم المجال الذي تريد إضافته، ثم حدد **التالي**.
    
5. اختر الطريقة التي تريد من خلالها التحقق من أنك تملك المجال.
    
    1. إذا كانت جهة تسجيل المجالات تستخدم [المجال الاتصال](#domain-connect-registrars-integrating-with-microsoft-365)، فستعمل [Microsoft على](../get-help-with-domains/domain-connect.md) إعداد سجلاتك تلقائيا من خلال تسجيل الدخول إلى جهة تسجيل المجالات وتأكيد الاتصال Microsoft 365. سيتم إرجاعك إلى مركز الإدارة، ثم تتحقق Microsoft من مجالك تلقائيا.
    2. يمكنك استخدام سجل TXT للتحقق من مجالك. حدد هذا وحدد **التالي** لرؤية إرشادات حول كيفية إضافة سجل DNS هذا إلى موقع جهة التسجيل على الويب. قد يستغرق هذا الأمر ما يصل إلى 30 دقيقة للتحقق بعد إضافة السجل. 
    3. يمكنك إضافة ملف نصي إلى موقع مجالك على ويب. حدد الملف .txt من معالج الإعداد، ثم قم بتحميل الملف إلى مجلد المستوى الأعلى لموقعك على ويب. يجب أن يبدو المسار إلى الملف مماثلا ل: `http://mydomain.com/ms39978200.txt`. سنؤكد أنك تملك المجال من خلال العثور على الملف على موقعك على ويب.
    
6. اختر الطريقة التي تريد بها إجراء تغييرات DNS المطلوبة لكي تستخدم Microsoft مجالك.
    
    1. اختر إضافة **سجلات DNS** لي إذا كانت جهة تسجيل المجالات تدعم [المجال الاتصال](#domain-connect-registrars-integrating-with-microsoft-365)، وسوف [تقوم Microsoft بإعداد](../get-help-with-domains/domain-connect.md) سجلاتك تلقائيا من خلال أن تقوم بتسجيل الدخول إلى جهة التسجيل وتأكيد الاتصال Microsoft 365.
    2. اختر **سأضيف سجلات DNS** بنفسي إذا كنت تريد إرفاق خدمات Microsoft 365 معينة فقط إلى مجالك أو إذا كنت تريد تخطي هذا في الوقت الحالي وفعل ذلك لاحقا. **اختر هذا الخيار إذا كنت تعرف بالضبط ما تقوم به.**

7. إذا اخترت إضافة سجلات *DNS* بنفسك، فحدد التالي  وسترى صفحة تحتوي على كل السجلات التي تحتاج إلى إضافتها إلى موقع ويب جهة التسجيل لإعداد مجالك. 

    إذا لم يتعرف المدخل على جهة التسجيل، يمكنك [اتباع هذه الإرشادات العامة.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
    
    إذا لم تكن تعرف موفر استضافة DNS أو جهة تسجيل المجالات لمجالك، فشاهد البحث عن جهة تسجيل المجالات أو [موفر استضافة DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    إذا كنت تريد الانتظار حتى وقت لاحق، فقم إما ب إلغاء تحديد كل الخدمات وانقر فوق متابعة، أو في خطوة اتصال المجال السابقة،  اختر خيارات إضافية وحدد تخطي **هذا في الوقت الحالي**.
    
8. حدد **إنهاء** - لقد انتهيت!

## <a name="add-or-edit-custom-dns-records"></a>إضافة سجلات DNS المخصصة أو تحريرها

اتبع الخطوات أدناه لإضافة سجل مخصص لموقع ويب أو خدمة جهة خارجية.

1. سجل الدخول إلى مركز إدارة Microsoft في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. انتقل إلى **صفحة الإعدادات**  >  **Domains**.

3. في صفحة **المجالات** ، حدد مجالا. 
    
4. ضمن **إعدادات DNS،** حدد **سجلات مخصصة**؛ ثم حدد **سجل مخصص جديد**.

5. حدد نوع سجل DNS الذي تريد إضافته وا اكتب معلومات السجل الجديد.
    
6. حدد **حفظ**.

## <a name="registrars-with-domain-connect"></a>المسجلون الذين الاتصال

[تتيح الاتصال](https://www.domainconnect.org/) المجالات التي تم تمكينها لك إضافة مجالك Microsoft 365 عملية من ثلاث خطوات تستغرق دقائق. 
  
في المعالج، سنؤكد فقط أنك تملك المجال، ثم نقوم بإعداد سجلات مجالك تلقائيا، بحيث يصل البريد الإلكتروني إلى Microsoft 365 وخدمات Microsoft 365 الأخرى، مثل Teams، للعمل مع مجالك.
  
> [!NOTE]
> تأكد من تعطيل أي حجب منبثق في المستعرض قبل بدء معالج الإعداد.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>المجالات الاتصال المجالات المتكاملة مع Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer أو WildWestDomains (بائعو GoDaddy الذين يستخدمون استضافة SecureServer DNS)
    - أمثلة:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>ماذا يحدث لبريدي الإلكتروني وعلى موقع الويب الخاص بي؟

بعد الانتهاء من الإعداد، يتم تحديث سجل MX لمجالك بحيث يشير إلى Microsoft 365 وسيبدأ تشغيل كل رسائل البريد الإلكتروني لمجالك Microsoft 365. تأكد من أنك أضفت مستخدمين ثم قمت بإعداد علب البريد في Microsoft 365 لكل شخص يحصل على البريد الإلكتروني على مجالك!
  
إذا كان لديك موقع ويب تستخدمه مع شركتك، فإنه سيبقى يعمل في مكان وجوده. لا تؤثر الاتصال إعداد المجال على موقعك على ويب.

### <a name="add-an-onmicrosoftcom-domain"></a>إضافة مجال onmicrosoft.com آخر

يمكن Microsoft 365 يمكن أن يكون لدى كل مؤسسة ما يصل إلى onmicrosoft.com مجالات.

> [!NOTE]
> يجب أن تكون المسؤول العام أو مسؤول اسم المجال لإضافة مجال.
> لن يؤدي إنشاء مجال .onmicrosoft إضافي واستخدامه كافتراضي إلى إعادة تسمية SharePoint Online. بإجراء تغييرات على مجال .onmicrosoft SharePoint، ستحتاج إلى استخدام معاينة إعادة تسمية مجال [SharePoint](/sharepoint/change-your-sharepoint-domain-name) (متوفر حاليا لأي مستأجر يقل عدد مواقعه عن 1000).
> إذا كنت تستخدم خدمات البريد Microsoft 365، فإن إزالة مجال .onmicrosoft الأولي غير معتمد.


لإضافة مجال onmicrosoft.com:

1. انتقل إلى مركز إدارة Microsoft **، الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.

2. على علامة **التبويب نظرة** عامة، حدد **إضافة onmicrosoft.com مجال**.

يمكنك تعيين أي مجال تملكه كمجالك الافتراضي.

## <a name="related-content"></a>المحتوى ذي الصلة

[الأسئلة الشائعة حول المجالات](domains-faq.yml) (مقالة)</br>
[ما هو المجال؟](../get-help-with-domains/what-is-a-domain.md) (article)</br>
[شراء اسم مجال في Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (مقالة)</br>
[إضافة سجلات DNS لتوصيل مجالك](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (مقالة)</br>
[تغيير أسماء الخدمات لإعداد Microsoft 365 مع أي جهة تسجيل مجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (مقالة)
