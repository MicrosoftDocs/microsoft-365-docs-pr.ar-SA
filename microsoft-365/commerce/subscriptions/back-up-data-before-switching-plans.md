---
title: وضع البيانات في وضع الرجوع قبل تغيير الخطط
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
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
description: نسخ Outlook OneDrive Yammer والمحتوى SharePoint قبل Microsoft 365 التخطيط.
ms.date: 03/17/2021
ms.openlocfilehash: 57f897b353cfe61d5c9cae56c1d367d5e57a29ca
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569144"
---
# <a name="back-up-data-before-switching-microsoft-365-for-business-plans"></a>وضع البيانات في وضع "Microsoft 365" قبل تبديلها

إذا تم تبديل مستخدم إلى اشتراك آخر به خدمات ذات صلة بالبيانات أقل أو غادر مستخدم المؤسسة، يمكن تنزيل نسخة من بياناته المخزنة في Microsoft 365 قبل أن يتم تبديلها إلى الاشتراك الجديد.

إذا كنت تنقل مستخدما إلى اشتراك تتوفر فيه الخدمات نفسها أو أكثر، فلا تحتاج إلى الحصول على بيانات المستخدمين. راجع [نقل المستخدمين إلى اشتراك آخر](./move-users-different-subscription.md).
  
## <a name="save-a-copy-of-outlook-information"></a>حفظ نسخة من Outlook المعلومات

إذا كان Outlook، يمكنهم تصدير البريد الإلكتروني وجهات الاتصال والتقويم أو نسخها احتياطيا إلى ملف [pst](https://support.microsoft.com/office/14252b52-3075-4e9b-be4e-ff9ef1068f91). Outlook قبل تبديل خطتهم.
  
بعد الانتهاء من التبديل إلى الخطة الجديدة، يمكن للمستخدمين استيراد البريد الإلكتروني وجهات الاتصال والتقويم من ملف [pst. Outlook pst](https://support.microsoft.com/office/431a8e9a-f99f-4d5f-ae48-ded54b3440ac).
  
## <a name="save-files-stored-in-onedrive-for-business"></a>حفظ الملفات المخزنة في OneDrive for Business

قبل التبديل إلى اشتراك آخر، يمكن للمستخدمين تنزيل الملفات والمجلدات من [OneDrive أو SharePoint](https://support.microsoft.com/office/5c7397b7-19c7-4893-84fe-d02e8fa5df05) إلى موقع آخر، مثل مجلد على محرك الأقراص الثابت على الكمبيوتر، أو مشاركة ملف على شبكة المؤسسة.
  
## <a name="save-yammer-information"></a>حفظ Yammer المعلومات

يمكن للمسؤولين تصدير كل الرسائل والملاحظات والملفات والمواضيع والمستخدمين والمجموعات إلى .zip ملف. لمزيد من المعلومات، راجع [تصدير البيانات من Yammer Enterprise](/yammer/manage-security-and-compliance/export-yammer-enterprise-data). يمكن للمطورين استخدام [Yammer API](https://go.microsoft.com/fwlink/p/?linkid=842495) للقيام بذلك أيضا.
  
## <a name="how-to-save-sharepoint-information"></a>كيفية حفظ SharePoint المعلومات

إذا تم تبديل مستخدم من اشتراك SharePoint عبر الإنترنت إلى اشتراك ليس لديه، فإن لوحة SharePoint لن تظهر في قائمة Microsoft 365 الخاصة به.
  
ومع ذلك، طالما أن الاشتراك الجديد داخل نفس المؤسسة التي تم التبديل منها، سيبقى بإمكان المستخدمين الوصول إلى SharePoint الفريق. يمكنهم عرض دفاتر الملاحظات والمستندات والمهام والتقويمات وتحديثها باستخدام عنوان URL المباشر لموقع الفريق.
  
> [!TIP]
> نوصي المستخدمين الانتقال إلى موقع الفريق قبل تبديل اشتراكهم وحفظ عنوان URL كعلامة مرجعية أو مفضلة في المستعرض.
  
بشكل افتراضي، يكون عنوان URL لموقع الفريق على ويب في هذا النموذج:
  
```html
https://<orgDomain>/_layouts/15/start.aspx#/SitePages/Home.aspx
```

أين  _\<orgDomain\>_ يوجد عنوان URL الخاص المؤسسة.
  
على سبيل المثال، إذا كان مجال المؤسسة contoso.onmicrosoft.com، سيكون عنوان URL المباشر لموقع الفريق هو `https://contoso.onmicrosoft.com/_layouts/15/start.aspx#/SitePages/Home.aspx`.
  
وبالطبع، يمكن للمستخدمين أيضا تنزيل SharePoint عبر الإنترنت من موقع SharePoint إلى الكمبيوتر المحلي أو إلى موقع آخر في أي وقت.
