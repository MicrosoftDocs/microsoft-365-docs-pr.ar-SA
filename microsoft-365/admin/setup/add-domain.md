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
- VSBFY23
- adminvideo
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
description: استخدم معالج الإعداد لإضافة مجالك إلى Microsoft 365 في مركز مسؤولي Microsoft 365 عن طريق إضافة سجل DNS لدى مضيف DNS.
ms.openlocfilehash: 13699b4a565c0762baa6f383330ed2e87517ac6d
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67087342"
---
# <a name="add-a-domain-to-microsoft-365"></a>إضافة مجال إلى Microsoft 365

 **[تحقق من الأسئلة المتداولة حول المجالات](domains-faq.yml)** إذا لم تعثر على ما تبحث عنه.

اطلع على [تعليمات Microsoft 365 للشركات الصغيرة](https://go.microsoft.com/fwlink/?linkid=2197659) على YouTube.
  
## <a name="before-you-begin"></a>قبل البدء

لإضافة مجالات أو تعديلها أو إزالتها، **يجب أن** تكون **مسؤول اسم المجال** أو **المسؤول العام** [لخطة عمل أو مؤسسة](https://products.office.com/business/office). تؤثر هذه التغييرات على المستأجر بأكمله؛ لن يتمكن *المسؤولون المخصصون* أو *المستخدمون العاديون* من إجراء هذه التغييرات.

> [!TIP]
> إذا كنت بحاجة إلى مساعدة في الخطوات الواردة في هذا الموضوع، ففكر في [العمل مع أحد متخصصي الشركات الصغيرة من Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). باستخدام مساعد الأعمال، يمكنك أنت وموظفيك الوصول على مدار الساعة إلى خبراء الشركات الصغيرة أثناء تنمية أعمالك، بدءا من الإلحاق إلى الاستخدام اليومي.

## <a name="watch-add-a-domain"></a>شاهد: إضافة مجال

اطلع على هذا الفيديو وغيره على [قناتنا على YouTube](https://go.microsoft.com/fwlink/?linkid=2198213).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

قد تحتاج شركتك إلى أسماء مجالات متعددة لأغراض مختلفة. على سبيل المثال، قد تحتاج إلى إضافة هجاء مختلف لاسم شركتك لأن العملاء يستخدمونه بالفعل وفشلت اتصالاتهم في الوصول إليك.

1. في مركز مسؤولي Microsoft 365، اختر <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**"إعداد**</a>".
1. ضمن **إعداد المجال المخصص**، حدد **View** > **Manage** > **Add domain**.
1. أدخل اسم المجال الجديد الذي تريد إضافته، ثم حدد **"التالي**".
1. سجل الدخول إلى جهة تسجيل المجالات، ثم حدد **"التالي**".
1. اختر الخدمات لمجالك الجديد.
1. حدد **"التخويل** >  **التالي** > "، ثم **"إنهاء**". تمت إضافة مجالك الجديد.

## <a name="add-a-domain"></a>إضافة مجال

اتبع هذه الخطوات لإضافة مجال أو إعداده أو متابعة إعداده. 

::: moniker range="o365-worldwide"

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. الانتقال إلى مركز الإدارة في <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. انتقل إلى صفحة **"مجالات الإعدادات** > ". 

3. حدد **إضافة مجال**.
    
4. أدخل اسم المجال الذي تريد إضافته، ثم حدد **"التالي**".
    
5. اختر الطريقة التي تريد بها التحقق من ملكيتك للمجال.
    
    1. إذا كانت جهة تسجيل المجالات تستخدم [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365)، [فستقسوم Microsoft بإعداد سجلاتك تلقائيا](../get-help-with-domains/domain-connect.md) من خلال تسجيل الدخول إلى جهة تسجيل المجالات وتأكيد الاتصال ب Microsoft 365. سيتم إرجاعك إلى مركز الإدارة وستتحقق Microsoft بعد ذلك من مجالك تلقائيا.
    2. يمكنك استخدام سجل TXT للتحقق من مجالك. حدد هذا الخيار وحدد **"التالي** " للاطلاع على إرشادات حول كيفية إضافة سجل DNS هذا إلى موقع جهة التسجيل على ويب. قد يستغرق ذلك ما يصل إلى 30 دقيقة للتحقق بعد إضافة السجل. 
    3. يمكنك إضافة ملف نصي إلى موقع مجالك على ويب. حدد الملف .txt وقم بتنزيله من معالج الإعداد، ثم قم بتحميل الملف إلى مجلد المستوى الأعلى لموقع ويب. يجب أن يبدو مسار الملف مشابها ل: `http://mydomain.com/ms39978200.txt`. سنؤكد ملكيتك للمجال من خلال العثور على الملف على موقعك على ويب.
    
6. اختر الطريقة التي تريد بها إجراء تغييرات DNS المطلوبة لكي تستخدم Microsoft مجالك.
    
    1. اختر **إضافة سجلات DNS لي** إذا كانت جهة التسجيل تدعم [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365)، [وستقوم Microsoft بإعداد سجلاتك تلقائيا](../get-help-with-domains/domain-connect.md) عن طريق جعلك تسجل دخولك إلى جهة التسجيل الخاصة بك وتأكد من الاتصال ب Microsoft 365.
    2. اختر **أنني سأضيف سجلات DNS بنفسي** إذا كنت تريد إرفاق خدمات Microsoft 365 معينة فقط بمجالك أو إذا كنت تريد تخطي هذا في الوقت الحالي وقم بذلك لاحقا. **حدد هذا الخيار إذا كنت تعرف بالضبط ما تقوم به.**

7. إذا اخترت *إضافة سجلات DNS بنفسك*  ، فحدد **"التالي** " وسترى صفحة تتضمن كل السجلات التي تحتاج إلى إضافتها إلى موقع ويب جهات التسجيل لإعداد مجالك. 

    إذا لم يتعرف المدخل على جهة التسجيل الخاصة بك، يمكنك [اتباع هذه الإرشادات العامة.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
    
    إذا كنت لا تعرف موفر استضافة DNS أو جهة تسجيل المجالات لمجالك، فراجع [البحث عن جهة تسجيل المجالات أو موفر استضافة DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    إذا كنت تريد الانتظار في وقت لاحق، إما إلغاء تحديد كافة الخدمات والنقر فوق **"متابعة**"، أو في خطوة اتصال المجال السابقة، اختر **"المزيد من الخيارات** " وحدد **"تخطي" في الوقت الحالي**.
    
8. حدد **إنهاء** - لقد انتهيت!

## <a name="add-or-edit-custom-dns-records"></a>إضافة سجلات DNS المخصصة أو تحريرها

اتبع الخطوات أدناه لإضافة سجل مخصص لموقع ويب أو خدمة جهة خارجية.

1. سجل الدخول إلى مركز إدارة Microsoft في <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. انتقل إلى صفحة **"مجالات الإعدادات**  > ".

3. في صفحة **"المجالات"** ، حدد مجالا. 
    
4. ضمن **إعدادات DNS**، حدد **سجلات مخصصة**؛ ثم حدد **سجلا مخصصا جديدا**.

5. حدد نوع سجل DNS الذي تريد إضافته واكتب معلومات السجل الجديد.
    
6. حدد **حفظ**.

## <a name="registrars-with-domain-connect"></a>جهات تسجيل المجالات التي لها اتصال بالمجال

تتيح لك جهات تسجيل المجالات الممكنة ل [Domain Connect](https://www.domainconnect.org/) إضافة مجالك إلى Microsoft 365 في عملية مكونة من ثلاث خطوات تستغرق دقائق. 
  
في المعالج، سنؤكد فقط أنك تملك المجال، ثم نقوم بإعداد سجلات مجالك تلقائيا، لذلك يتم إرسال البريد الإلكتروني إلى Microsoft 365 وخدمات Microsoft 365 الأخرى، مثل Teams، للعمل مع مجالك.
  
> [!NOTE]
> تأكد من تعطيل أي أدوات حظر منبثقة في المستعرض قبل بدء تشغيل معالج الإعداد.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>تكامل جهات تسجيل Domain Connect مع Microsoft 365

- [1&amp;1 IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [بلورة سحابية](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer أو WildWestDomains (بائعو GoDaddy باستخدام استضافة SecureServer DNS)
    - امثله:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>ماذا يحدث للبريد الإلكتروني وموقعي على الويب؟

بعد الانتهاء من الإعداد، يتم تحديث سجل MX لمجالك للإشارة إلى Microsoft 365 وستبدأ كل رسائل البريد الإلكتروني لمجالك في التوفر إلى Microsoft 365. تأكد من إضافة مستخدمين وإعداد علب البريد في Microsoft 365 لكل شخص يتلقى بريدا إلكترونيا على مجالك!
  
إذا كان لديك موقع ويب تستخدمه مع شركتك، فسيستمر في العمل في مكانه. لا تؤثر خطوات إعداد Domain Connect على موقعك على ويب.

### <a name="add-an-onmicrosoftcom-domain"></a>إضافة مجال onmicrosoft.com

يمكن أن يكون لكل مؤسسة من مؤسسة Microsoft 365 ما يصل إلى خمسة مجالات onmicrosoft.com.

> [!NOTE]
> يجب أن تكون مسؤولا عموميا أو مسؤول اسم المجال لإضافة مجال.
> لن يؤدي إنشاء مجال onmicrosoft إضافي واستخدامه كافتراضي إلى إعادة تسمية SharePoint Online. لإجراء تغييرات على مجال .onmicrosoft SharePoint، ستحتاج إلى استخدام [معاينة إعادة تسمية مجال SharePoint](/sharepoint/change-your-sharepoint-domain-name) (متوفر حاليا لأي مستأجر لديه أقل من 1000 موقع).
> إذا كنت تستخدم خدمات البريد في Microsoft 365، فإن إزالة مجال .onmicrosoft الأولي غير معتمد.


لإضافة مجال onmicrosoft.com:

1. في مركز مسؤولي Microsoft 365، حدد **"إعدادات"**، ثم حدد **"المجالات**".

2. حدد مجال *.onmicrosoft.com* موجود.

    ![صفحة المجالات.](../../media/onmicrosoft-domains.png)
  

3. في علامة التبويب **"نظرة عامة** "، حدد **"إضافة onmicrosoft.com المجال**".

    ![لقطة شاشة لخصائص المجال.](../../media/add-onmicrosoft-domain-link.png)

4. في صفحة **"Add onmicrosoft domain** "، في مربع **اسم المجال** ، أدخل اسم مجال onmicrosoft.com الجديد. 

    ![لقطة شاشة لمجال Add onmicrosoft.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > تأكد من التحقق من التدقيق الإملائي ودقة اسم المجال الذي أدخلته. أنت مقيد بخمسة مجالات onmicrosoft.com، ولا يمكن حذفها حاليا بمجرد إنشائها.     

5. حدد **إضافة مجال**. عند الإضافة بنجاح، سترى رسالة تفيد بذلك. 
    
    ![لقطة شاشة للمجال تمت إضافته بنجاح.](../../media/domain-added.png)

يمكنك تعيين أي مجال تملكه كمجال افتراضي. 

لمزيد من التفاصيل حول كيفية إضافة مجال onmicrosoft.com، راجع [إضافة مجال onmicrosoft.com أو استبداله](add-or-replace-your-onmicrosoftcom-domain.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[الأسئلة المتداولة حول المجالات](domains-faq.yml) (مقالة)</br>
[ما هو المجال؟](../get-help-with-domains/what-is-a-domain.md) (مقالة)</br>
[شراء اسم مجال في Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (مقال)</br>
[إضافة سجلات DNS لتوصيل مجالك](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (مقالة)</br>
[تغيير خوادم الأسماء لإعداد Microsoft 365 مع أي جهة تسجيل مجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (مقالة)
