---
title: تحديث سجلات DNS للاحتفاظ بموقع الويب الخاص بك مع موفر الاستضافة الحالي
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
- Adm_O365
- Adm_NonTOC
ms.custom:
- VSBFY23
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: تعرف على كيفية توجيه نسبة استخدام الشبكة إلى موقع ويب عام موجود مستضاف خارج Microsoft، إذا قمت بتعيين Microsoft لإدارة سجلات DNS لمجالك المخصص.
ms.openlocfilehash: 914c2374bd15d4a94769203142021db86c689427
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/30/2022
ms.locfileid: "67084136"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>تحديث سجلات DNS للاحتفاظ بموقع الويب الخاص بك مع موفر الاستضافة الحالي

 **إذا كنت تدير سجلات Microsoft لمجالك لدى موفر استضافة DNS**، فلا داعي للقلق بشأن الخطوات الواردة في هذا الموضوع. يبقى موقع الويب الخاص بك في مكانه ولا يزال بإمكان الأشخاص الوصول إليه. 
  
 **إذا كانت Microsoft تدير سجلات DNS**، لتوجيه نسبة استخدام الشبكة إلى موقع ويب عام موجود مستضاف خارج Microsoft، بعد إضافة مجالك إلى Microsoft، فقم بما يلي: 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>تحديث سجلات DNS في مركز مسؤولي Microsoft 365
1. في مركز الإدارة، انتقل إلى صفحة **"مجالات الإعدادات**\>".<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. في صفحة **المجالات** ، حدد المجال ثم اختر **سجلات DNS**.

1. حدد **+ إضافة سجل** وأدخل ما يلي: 
    
   - **للنوع** أدخل: **A (العنوان)**
    
   - بالنسبة **لاسم المضيف أو الاسم المستعار**، اكتب ما يلي: **@**
    
   - بالنسبة **لعنوان IP**، اكتب عنوان IP الثابت لموقع ويب حيث تتم استضافته حاليا (على سبيل المثال، 172.16.140.1). 
    
   يجب أن يكون عنوان IP  *ثابتا*  لموقع الويب، وليس عنوان IP  *ديناميكيا*  . تحقق من الموقع حيث تتم استضافة موقعك على ويب للتأكد من أنه يمكنك الحصول على عنوان IP ثابت لموقع ويب العام. 
    
1. حدد **حفظ**. 
    
بالإضافة إلى ذلك، يمكنك إنشاء سجل CNAME لمساعدة العملاء في العثور على موقعك على ويب.
  
1. حدد **+ إضافة سجل** وأدخل ما يلي: 
    
   - **للنوع** أدخل: **CNAME (الاسم المستعار)**
    
   - بالنسبة **لاسم المضيف أو الاسم المستعار**، اكتب ما يلي: **www**
    
   - بالنسبة **للنقاط المراد عنوانها**، اكتب اسم المجال المؤهل بالكامل (FQDN) لموقعك على ويب (على سبيل المثال، contoso.com). 
    
2. حدد **حفظ**. 
    
وأخيرا، قم بما يلي:
  
[تحديث سجلات NS لمجالك](../setup/add-domain.md) للإشارة إلى Microsoft. 
  
عند تحديث سجلات NS للإشارة إلى Microsoft، يتم إعداد مجالك بالكامل. سيتم توجيه البريد الإلكتروني إلى Microsoft، وستستمر نسبة استخدام الشبكة إلى عنوان موقعك على ويب في الانتقال إلى مضيف موقعك الحالي على ويب.
