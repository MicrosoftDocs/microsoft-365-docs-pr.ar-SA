---
title: القصر والحصول على الوظائف الإضافية من المتجر
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: تعرف على اللوائح التنظيمية العامة لحماية البيانات (GDPR) التي تحكم البيانات الشخصية للقصر.
ms.openlocfilehash: 84a1ecc9eb5d29ae1c2e4597b8299430cc3de038
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63567683"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>القصر والحصول على الوظائف الإضافية من المتجر

القانون العام لحماية البيانات (GDPR) هو لائحة الاتحاد الأوروبي التي تصبح فعالة في 25 مايو 2018. وهو يمنح المستخدمين حقوق وحماية بياناتهم. أحد جوانب القانون العام لحماية البيانات (GDPR) هو أنه لا يمكن للقصر إرسال بياناتهم الشخصية إلى الأطراف التي لم يوافق عليها أحد الوالدين أو الوصي. يعتمد العمر المحدد المحدد كقاصر على المنطقة التي يوجد فيها الشخص.
  
تتضمن المناطق التي تتضمن لوائح قانونية حول موافقة الوالدين الولايات المتحدة وكوريا الجنوبية والمملكة المتحدة والاتحاد الأوروبي. بالنسبة إلى هذه المناطق، سيتم حظر القاصر (عبر Azure Active Directory) من الحصول على أي من الوظائف الإضافية Office الجديدة من المتجر وتشغيل الوظائف الإضافية التي تم الحصول عليها مسبقا. بالنسبة للبلدان التي لا توجد فيها لوائح قانونية، لن تكون هناك قيود على التنزيل.
  
يتم تحديد المستخدم كقاصر استنادا إلى البيانات المحددة في Azure Active Directory. مسؤول المؤسسة مسؤول عن الإعلان عن فئة العمر القانوني وموافقة الوالدين لذلك المستخدم.
  
إذا وافق الوالد/الوصي على قاصر باستخدام خدمة معينة، يمكن لمسؤول المؤسسة استخدام النشر المركزي لنشر هذه الوظائف الإضافية لجميع القصر الذين لديهم موافقة.
  
لتكون متوافقا مع GDPR للقصر، يجب التأكد من نشر أحد Office التالية في مؤسستك/مؤسستك.
 
 **بالنسبة إلى Word Excel PowerPoint و Project**: 

|**النظام الأساسي** <br/> |**رقم النسخة** <br/> |
|:-----|:-----|
|Microsoft 365 Apps for enterprise (القناة الحالية)  <br/> |9001.2138   <br/> |
|Microsoft 365 Apps for enterprise (قناة المؤسسة نصف السنوية)  <br/> |8431.2159  <br/> |
|Office 2016 for Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 for Mac  <br/> |16.11.18020200  <br/> |
|Office للويب  <br/> |N/A  <br/> |
   
 **بالنسبة Outlook**: 
  
|**النظام الأساسي** <br/> |**رقم النسخة** <br/> |
|:-----|:-----|
|Outlook 2016 Windows (MSI)  <br/> |إنشاء بلا TBD  <br/> |
|Outlook 2016 Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 for Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook المحمول ل iOS  <br/> |2.75.0  <br/> |
|Outlook المحمول لنظام التشغيل Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |N/A  <br/> |

 **Office 2013**
  
سيدعم كل من word Excel و PowerPoint 2013 for Windows نفس عمليات التحقق من القصر إذا تم تمكين مكتبة مصادقة Active Directory (ADAL). هناك خياران للتوافق، كما هو موضح بعد ذلك.
  
- **تمكين ADAL**. تشرح هذه المقالة كيفية تمكين ADAL Office 2013: استخدام Microsoft 365 الحديثة مع Office [العملاء](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>تحتاج أيضا إلى تعيين مفاتيح التسجيل لتمكين ADAL كما هو موضح في تمكين المصادقة الحديثة Office [2013 على Windows الأجهزة](../security-and-compliance/enable-modern-authentication.md).<br/>بالإضافة إلى ذلك، ستحتاج إلى تثبيت تحديثات شهر أبريل التالية Office 2013:
    
  - [وصف تحديث الأمان ل Office 2013: 10 أبريل 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [تحديث 3 أبريل 2018 Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **عدم تمكين ADAL**. إذا تعذر عليك تمكين ADAL في Office 2013، فإن توصيتنا هي استخدام "نهج المجموعة" إيقاف تشغيل المتجر Office العملاء. توجد هنا معلومات حول كيفية إيقاف تشغيل التطبيق Office [الإعدادات.](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15))

## <a name="related-articles"></a>المقالات ذات الصلة

[استخدام الوظائف الإضافية في مركز الإدارة](./manage-deployment-of-add-ins.md)

[إدارة الوظائف الإضافية في مركز الإدارة](./manage-addins-in-the-admin-center.md)
