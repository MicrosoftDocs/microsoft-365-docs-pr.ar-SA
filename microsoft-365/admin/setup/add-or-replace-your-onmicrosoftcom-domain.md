---
title: إضافة مجال احتياطي onmicrosoft.com واستبداله في Microsoft 365
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
ms.assetid: ''
description: تعرف على كيفية إنشاء مجال onmicrosoft.com جديد وجعله مجالك الاحتياطي الجديد.
ms.openlocfilehash: 66f5562b4a2ba46f662a54ff33d953c4e617ce3a
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67087298"
---
# <a name="add-and-replace-your-onmicrosoftcom-fallback-domain-in-microsoft-365"></a>إضافة مجال احتياطي onmicrosoft.com واستبداله في Microsoft 365

عند التسجيل للحصول على Microsoft 365، توفر Microsoft *مجالا onmicrosoft.com* - **مجالك الاحتياطي** - في حال لم تكن تملك مجالا، أو لا تريد توصيله ب Microsoft 365 (على سبيل المثال، tailspintoys.onmicrosoft.com). يتم استخدام مجالك الاحتياطي بشكل افتراضي في:

- أسماء المستخدمين وعناوين البريد الإلكتروني
- فرق Microsoft 365 & مجموعات الأسماء المستعارة للبريد الإلكتروني
- نقل تبعية المجال التلقائية

وهو بمثابة عنوان توجيه بريد إلكتروني افتراضي لبيئة Microsoft 365. عند إعداد مستخدم باستخدام علبة بريد، يتم توجيه البريد الإلكتروني إلى المجال الاحتياطي.  حتى إذا تم استخدام مجال مخصص (على سبيل المثال، tailspintoys.com)، إذا تم حذف هذا المجال المخصص من بيئة Microsoft 365، يضمن المجال الاحتياطي توجيه البريد الإلكتروني للمستخدم بنجاح.

يمكنك تغيير مجالك الاحتياطي في مركز مسؤولي Microsoft 365. تشمل الأسباب الشائعة التي تجعل العملاء يغيرون مجالهم الاحتياطي ما يلي:

- عدم معرفة اسم الشركة الذي يجب استخدامه عند التسجيل لأول مرة في Microsoft 365. الآن بعد أن عرفوا اسم الشركة، يريدون أن يكون لمستخدميهم أسماء حسابات تسجيل الدخول المناسبة. 
- يريدون تغيير شكل عناوين URL الخاصة بهم في SharePoint عند إنشاء موقع جديد. يتم إنشاء عناوين URL ل SharePoint في بيئة Microsoft 365 استنادا إلى اسم المجال الاحتياطي. إذا لم تستخدم اسم الشركة الصحيح عند التسجيل لأول مرة، فستستمر عناوين URL ل SharePoint لمواقعك في استخدام هذا الاسم عند إنشاء مواقع SharePoint جديدة. 


بينما يمكنك إضافة مجالات onmicrosoft.com إضافية، يمكن استخدام مجال onmicrosoft.com واحد فقط كمجال احتياطي. تصف الخطوات الواردة في هذه المقالة كيفية:
- إنشاء مجال onmicrosoft.com جديد
- تعيينه كمجال احتياطي

> [!NOTE]
> أنت مقيد بمجموع خمسة مجالات onmicrosoft.com في بيئة Microsoft 365. بمجرد إضافتها، لا يمكن إزالتها. 
  
## <a name="before-you-begin"></a>قبل البدء

لإضافة مجالات أو تعديلها أو إزالتها، **يجب أن** تكون **مسؤول اسم المجال** أو **المسؤول العام** [لخطة عمل أو مؤسسة](https://products.office.com/business/office). تؤثر هذه التغييرات على المستأجر بأكمله؛ لن يتمكن *المسؤولون المخصصون* أو *المستخدمون العاديون* من إجراء هذه التغييرات.


## <a name="add-a-new-onmicrosoftcom-domain"></a>إضافة مجال onmicrosoft.com جديد

1. في مركز مسؤولي Microsoft 365، حدد **"إعدادات"**، ثم حدد **"المجالات**".
2. حدد مجالك الافتراضي onmicrosoft.com.

    ![صفحة المجالات.](../../media/onmicrosoft-domains.png)
  
3. في صفحة خصائص المجال، في قسم **"حول هذا المجال** "، حدد **"Add onmicrosoft domain**".

    ![حول صفحة المجالات هذه.](../../media/add-onmicrosoft-domain-link.png)

4. في صفحة **"إضافة مجال onmicrosoft** "، في مربع **اسم المجال** ، اكتب اسم مجال onmicrosoft.com الجديد. 

    ![Screenshot of Add onmicrosoft domain page.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > تأكد من التحقق من التدقيق الإملائي ودقة اسم المجال الذي أدخلته. أنت مقيد بخمسة مجالات onmicrosoft.com، ولا يمكن حذفها حاليا بمجرد إنشائها.     

5. حدد **إضافة مجال**. عند الإضافة بنجاح، سترى رسالة تفيد بذلك. 
    
    ![لقطة شاشة للمجال تمت إضافته بنجاح.](../../media/domain-added.png)



## <a name="make-your-new-onmicrosoftcom-domain-your-fallback-domain"></a>جعل مجال onmicrosoft.com الجديد مجالك الاحتياطي


> [!NOTE]
> قبل تغيير مجالك الاحتياطي إلى مجال onmicrosoft.com جديد، قد ترغب في تغيير مجال SharePoint onmicrosoft.com. لن يؤدي إنشاء مجال onmicrosoft إضافي واستخدامه كمجال احتياطي إلى إعادة تسمية SharePoint Online. ستبقى عناوين URL ل SharePoint وOneDrive الحالية كما هي.  يمكنك تغيير مجال .onmicrosoft SharePoint من خلال خطوات PowerShell المتوفرة في [معاينة إعادة تسمية مجال SharePoint](/sharepoint/change-your-sharepoint-domain-name) (المتوفرة حاليا لأي مستأجر لديه أقل من 1000 موقع).

بعد إنشاء مجال onmicrosoft.com الجديد، قم بما يلي لتغييره إلى مجالك الاحتياطي.

1. في مركز مسؤولي Microsoft 365، حدد **"إعدادات"**، ثم حدد **"المجالات**". 

2. حدد مجال onmicrosoft.com الجديد الذي أنشأته.

    ![حدد مجالات.](../../media/onmicrosoft-domains-added.png) 

3. في صفحة خاصية المجال، حدد **"إنشاء مجال احتياطي**".
 
    ![لقطة شاشة لتحديد مجال احتياطي جديد.](../../media/new-fallback.png) 

4. سيتم عرض رسالة على الصفحة تفيد بأن مجالك الاحتياطي قد تغير إلى المجال الجديد.

    ![تمت إضافة مجال احتياطي جديد بنجاح.](../../media/fallback-success.png) 

## <a name="related-content"></a>المحتويات ذات الصلة

[الأسئلة المتداولة حول المجالات](domains-faq.yml) (مقالة)</br>
[ما هو المجال؟](../get-help-with-domains/what-is-a-domain.md) (مقالة)</br>
[شراء اسم مجال في Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (مقال)</br>
[إضافة سجلات DNS لتوصيل مجالك](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (مقالة)</br>
[تغيير خوادم الأسماء لإعداد Microsoft 365 مع أي جهة تسجيل مجالات](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (مقالة)
