---
title: النسخ الاحتياطي للبيانات قبل تغيير الخطط
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
description: النسخ الاحتياطي لمحتوى Outlook OneDrive Yammer SharePoint قبل تغيير خطط Microsoft 365.
ms.date: 03/17/2021
ms.openlocfilehash: fd5239deb88fbf9b87df7e62d85a3d2cc18e1df7
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102493"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>النسخ الاحتياطي للبيانات قبل تبديل Microsoft 365 لخطط الأعمال

إذا تم تبديل مستخدم إلى اشتراك آخر يحتوي على خدمات أقل متعلقة بالبيانات أو ترك مستخدم المؤسسة، يمكن تنزيل نسخة من بياناته المخزنة في Microsoft 365 قبل التبديل إلى الاشتراك الجديد.

إذا كنت تنقل مستخدما إلى اشتراك لديه نفس الخدمات أو أكثر، فلن تحتاج إلى إجراء نسخ احتياطي لبيانات المستخدم. راجع [نقل المستخدمين إلى اشتراك مختلف](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>حفظ نسخة من معلومات Outlook

إذا كان لدى المستخدمين Outlook، يمكنهم [تصدير البريد الإلكتروني وجهات الاتصال والتقويم أو نسخها احتياطيا إلى ملف pst. Outlook](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91) قبل تبديل خطتهم.
  
بعد الانتهاء من التبديل إلى الخطة الجديدة، يمكن للمستخدمين [استيراد البريد الإلكتروني وجهات الاتصال والتقويم من ملف pst. Outlook](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>حفظ الملفات المخزنة في OneDrive for Business

قبل التبديل إلى اشتراك مختلف، يمكن للمستخدمين [تنزيل الملفات والمجلدات من OneDrive أو SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) إلى موقع آخر، مثل مجلد على محرك الأقراص الثابتة للكمبيوتر، أو مشاركة ملف على شبكة المؤسسة.
  
## <a name="save-yammer-information"></a>حفظ معلومات Yammer

يمكن للمسؤولين تصدير كل الرسائل والملاحظات والملفات والموضوعات والمستخدمين والمجموعات إلى ملف .zip. لمزيد من المعلومات، راجع [تصدير البيانات من Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). يمكن للمطورين استخدام [واجهة برمجة تطبيقات Yammer](https://go.microsoft.com/fwlink/p/?linkid=842495) للقيام بذلك أيضا.
  
## <a name="how-to-save-sharepoint-information"></a>كيفية حفظ معلومات SharePoint

إذا تم تبديل مستخدم من اشتراك يحتوي على SharePoint Online إلى اشتراك لا يحتوي عليه، فلن تظهر لوحة **SharePoint** في قائمة Microsoft 365 الخاصة به.
  
ومع ذلك، طالما أن الاشتراك الجديد داخل نفس المؤسسة مثل الاشتراك الذي تم التبديل منه، فسيظل المستخدمون قادرين على الوصول إلى موقع فريق SharePoint. يمكنهم عرض دفاتر الملاحظات والمستندات والمهام والتقويمات وتحديثها باستخدام عنوان URL المباشر لموقع الفريق.
  
> [!TIP]
> نوصي المستخدمين بالانتقال إلى موقع الفريق قبل تبديل اشتراكهم وحفظ عنوان URL كمفضلة أو إشارة مرجعية في مستعرضهم.
  
بشكل افتراضي، يكون عنوان URL لموقع الفريق على ويب في هذا النموذج:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

أين  _\<orgDomain\>_ هو عنوان URL الخاص بالمؤسسة.
  
على سبيل المثال، إذا كان مجال المؤسسة contoso.onmicrosoft.com، فسيكون `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`عنوان URL المباشر لموقع الفريق .
  
وبالطبع، يمكن للمستخدمين أيضا تنزيل مستندات SharePoint Online من موقع فريق SharePoint إلى الكمبيوتر المحلي أو إلى موقع آخر في أي وقت.
