---
title: إنشاء سجلات DNS Office 365 عند إدارة سجلات DNS
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEA150
ms.assetid: 0669bf14-414d-4f51-8231-6b710ce7980b
ROBOTS: NOINDEX
description: 'تعرف على كيفية إنشاء سجلات DNS Office 365 21Vianet عند إدارة سجلات DNS. '
monikerRange: o365-21vianet
ms.openlocfilehash: b1254ed341fb73f17f457798f14d01d89063f920
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63568403"
---
# <a name="create-dns-records-for-office-365-when-you-manage-your-dns-records"></a>إنشاء سجلات DNS Office 365 عند إدارة سجلات DNS

للحصول على إرشادات مفصلة حول كيفية إنشاء سجلات DNS ل Office 365 التي يتم تشغيلها بواسطة 21Vianet، بما في ذلك سجل MX المطلوب توجيه البريد، راجع إنشاء سجلات DNS لدى أي موفر استضافة [DNS Office 365](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). 
  
  
المزيد من الخيارات وبعض الأمور التي يجب أن تكون على علم بها:
      
-  إذا لم تكن تعرف موفر استضافة DNS أو جهة تسجيل المجالات لمجالك، فشاهد البحث عن جهة تسجيل المجالات أو [موفر استضافة DNS](../get-help-with-domains/find-your-domain-registrar.md). للحصول على أوصاف لما تقوم به سجلات DNS، راجع [أساسيات DNS](../get-help-with-domains/dns-basics.md).
    
-  لا تسمح لك بعض موفري استضافة DNS بإنشاء كل أنواع السجلات المطلوبة، مما يؤدي إلى فرض قيود على الخدمة عندما لا يدعم موفر الاستضافة [SRV أو CNAME أو TXT أو إعادة التوجيه](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). إذا كان الموفر لا يدعم سجلات SRV أو TXT أو CNAME، نوصي بنقل مجالك إلى موفر [](../get-help-with-domains/buy-a-domain-name.md) يدعم كل [أنواع السجلات المطلوبة](https://support.microsoft.com/office/dfbb03e3-08c1-4c4e-b2f0-891665b29b77). 
    
- لمعرفة سجلات DNS المطلوبة والعثور على القيم التي يجب استخدامها لكل سجل، بما في ذلك سجل MX للبريد الإلكتروني، راجع جمع المعلومات التي [تحتاج إليها لإنشاء سجلات DNS Office 365 DNS](../get-help-with-domains/information-for-dns-records.md). للحصول على أوصاف لما تقوم به سجلات DNS، راجع [أساسيات DNS](../get-help-with-domains/dns-basics.md).
