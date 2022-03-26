---
title: تحديث سجلات DNS لإبقاء موقعك على ويب مع موفر الاستضافة الحالي
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: تعرف على كيفية توجيه حركة المرور إلى موقع ويب عام موجود مستضاف خارج Microsoft، إذا قمت بتعيين Microsoft لإدارة سجلات DNS لمجالك المخصص.
ms.openlocfilehash: 9bb12d4f73e8d95717ddd90492fb9cb97c73eec9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63567977"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>تحديث سجلات DNS لإبقاء موقعك على ويب مع موفر الاستضافة الحالي

 **إذا كنت تدير سجلات Microsoft لمجالك لدى موفر استضافة DNS**، فلا داعي للقلق بشأن الخطوات في هذا الموضوع. يبقى موقعك على ويب في المكان الذي يوجد فيه ويبقى بامكن للأشخاص الوصول إلى الموقع. 
  
 **إذا كانت Microsoft تدير سجلات DNS**، ل توجيه حركة المرور إلى موقع ويب عام موجود مستضاف خارج Microsoft، بعد إضافة مجالك إلى Microsoft، قم بما يلي: 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>تحديث سجلات DNS في مركز مسؤولي Microsoft 365
1. في مركز الإدارة، **انتقل إلى الإعدادات** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">المجالات</a>.

1. في صفحة **المجالات** ، حدد المجال ثم اختر **سجلات DNS**.

1. حدد **+ إضافة سجل** وأدخل ما يلي: 
    
   - لإدخال **النوع** : **أ (عنوان)**
    
   - بالنسبة **إلى اسم المضيف أو الاسم المستعار**، اكتب ما يلي: **@**
    
   - بالنسبة **إلى عنوان IP**، اكتب عنوان IP الثابت لموقعك على ويب حيث يستضيفه حاليا (على سبيل المثال، 172.16.140.1). 
    
   يجب أن يكون  *هذا عنوان*  IP ثابتا لموقع ويب،  *وليس عنوان IP*  ديناميكيا. تحقق من الموقع الذي يستضيف موقعك على ويب للتأكد من أنه يمكنك الحصول على عنوان IP ثابت لموقعك العام على ويب. 
    
1. حدد **حفظ**. 
    
بالإضافة إلى ذلك، يمكنك إنشاء سجل CNAME لمساعدة العملاء في العثور على موقعك على ويب.
  
1. حدد **+ إضافة سجل** وأدخل ما يلي: 
    
   - لإدخال **النوع** : **CNAME (الاسم المستعار)**
    
   - بالنسبة **إلى اسم المضيف أو الاسم المستعار**، اكتب ما يلي: **www**
    
   - **لنقاط العنوان،** اكتب اسم المجال المؤهل بالكامل (FQDN) لموقعك على ويب (على سبيل المثال، contoso.com). 
    
2. حدد **حفظ**. 
    
وأخيرا، يمكنك القيام بما يلي:
  
[قم بتحديث سجلات NS لمجالك](../setup/add-domain.md) لتشير إلى Microsoft. 
  
عند تحديث سجلات NS بحيث تشير إلى Microsoft، يتم إعداد مجالك. سيتم توجيه البريد الإلكتروني إلى Microsoft، وستستمر حركة المرور إلى عنوان موقعك على ويب في الانتقال إلى مضيف موقع ويب الحالي.
