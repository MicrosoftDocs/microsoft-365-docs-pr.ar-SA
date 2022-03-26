---
title: إنشاء مجموعة أمان أو تحريرها أو حذفها في مركز مسؤولي Microsoft 365
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: تعرف على كيفية إنشاء مجموعة أمان أو تحريرها أو حذفها.
ms.openlocfilehash: 3f054842abc5111c654b8da02afc418c36f7db11
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63567344"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>إنشاء مجموعة أمان أو تحريرها أو حذفها في مركز مسؤولي Microsoft 365

في صفحة Microsoft 365 المجموعات، يمكنك  إنشاء مجموعات من حسابات المستخدمين التي يمكنك استخدامها لتعيين الأذونات نفسها لها في SharePoint Online و CRM Online. على سبيل المثال، يمكن للمسؤول إنشاء مجموعة أمان لمنح مجموعة معينة من الأشخاص حق الوصول إلى SharePoint ويب. لا تملك أذونات إنشاء مجموعات أمان أو تحريرها أو حذفها إلا للمسؤولين العامين والمسؤولين عن إدارة المستخدمين؛ لمزيد من المعلومات حول أدوار المسؤولين، راجع [تعيين أدوار المسؤولين](../add-users/assign-admin-roles.md). 
  
هناك أيضا مجموعات في [Exchange Online و SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) يمكنك استخدامها لإرسال بريد إلكتروني أو تعيين أذونات إلى مجموعة من المستخدمين، ومجموعات في [Exchange Online و SharePoint Online](#groups-in-exchange-online-and-sharepoint-online) تمنح المستخدمين حقوق الوصول والوصول إلى المواقع ومجموعات المواقع. 
  
> [!IMPORTANT]
>  هل تخطط لاستخدام علب بريد الموقع؟ يمكن لجميع المستخدمين الذين يضافون إلى موقع SharePoint عبر مجموعة أمان بدلا من إضافتهم بشكل فردي استخدام علبة بريد الموقع فقط من SharePoint. لن يتمكن هؤلاء المستخدمون من الوصول إلى علبة بريد الموقع من Outlook. لمزيد من المعلومات، راجع [استخدام Microsoft 365 بدلا من علب بريد الموقع](https://support.microsoft.com/office/737d6b1f-67cc-41fe-8db8-f2d09dd1673b). 
  
## <a name="manage-security-groups-in-the-admin-center"></a>إدارة مجموعات الأمان في مركز الإدارة

### <a name="add-a-security-group"></a>إضافة مجموعة أمان

1. في مركز مسؤولي Microsoft 365، انتقل إلى **صفحة** <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GroupsGroups</a> > .
  
2. في صفحة **المجموعات** ، حدد **إضافة مجموعة**.
    
3. في الصفحة **اختيار نوع مجموعة** ، اختر **الأمان**. 
    
4. اتبع الخطوات لإكمال إنشاء المجموعة. 
 
### <a name="add-members-to-a-security-group"></a>إضافة أعضاء إلى مجموعة أمان
    
1. حدد اسم مجموعة الأمان على صفحة **المجموعات** ، وعلى علامة **التبويب أعضاء،** حدد **عرض الكل وإدارة الأعضاء**. 
    
2. في جزء المجموعة، حدد **إضافة** أعضاء واختر الشخص من القائمة أو اكتب اسم الشخص الذي تريد إضافته في المربع بحث، ثم حدد **حفظ**.
    
    لإزالة الأعضاء، حدد X بجانب اسمهم. 
  
### <a name="edit-a-security-group"></a>تحرير مجموعة أمان

1. في مركز الإدارة، انتقل إلى صفحة **مجموعات** \> المجموعات.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. في صفحة **المجموعات** ، حدد اسم المجموعة. 
    
3. في جزء الإعدادات، حدد علامة **التبويب عام** أو علامة **التبويب أعضاء لتحرير** تفاصيل المجموعة أو الأعضاء.

### <a name="delete-a-security-group"></a>حذف مجموعة أمان

1. في مركز الإدارة، انتقل إلى **صفحة** <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GroupsGroups</a> > .
    
2. في صفحة **المجموعات** ، حدد اسم المجموعة. 
    
3. حدد **حذف المجموعة** (أيقونة الوزتين)، ثم أكد عن طريق تحديد **حذف**.
    
    حدد **إغلاق** بمجرد حذف المجموعة. 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>المجموعات في Exchange Online SharePoint Online

إذا كنت تريد إنشاء مجموعات من المستخدمين بحيث يمكنك إرسال البريد الإلكتروني إليهم جميعا في الوقت نفسه، يمكنك القيام بذلك في مركز إدارة Exchange عن طريق الذهاب إلى **المسؤول** \>  \> Exchange **المستلمين**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a> بعد ذلك، حدد **NewAdd**![.](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png)، وحدد نوع المجموعة التي تريد إنشاؤها: 
  
- **مجموعة التوزيع**: يتم استخدامها لتوزيع الرسائل على مجموعة من المستخدمين. تسمى  *أيضا مجموعة توزيع* تمكين البريد، أو قائمة  *توزيع*. لمزيد من المعلومات، راجع [إدارة مجموعات التوزيع](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups).
    
- **مجموعة الأمان**: يمكن استخدامها لتوزيع الرسائل على مجموعة من المستخدمين، أو لمنح أذونات الوصول إلى الموارد. تسمى هذه المجموعة أيضا مجموعة أمان تم *تمكين البريد لها*. لمزيد من المعلومات، راجع إدارة مجموعات الأمان التي تم [تمكين البريد لها](/Exchange/recipients/mail-enabled-security-groups).
    
- **مجموعة توزيع** ديناميكية: نوع مجموعة توزيع يتم إعادة حساب قائمة المستلمين الخاصة بها في كل مرة ترسل فيها رسالة استنادا إلى عوامل التصفية والشروط التي تحددها. لمزيد من المعلومات، راجع [إدارة مجموعات التوزيع الديناميكية](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups).
    
بعد إنشاء مجموعات توزيع ومجموعات أمان تمكين البريد في مركز إدارة Exchange، تظهر <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>أسماءها وقوائم المستخدمين الخاصة بها على **صفحة مجموعات** الأمان. يمكنك حذف هذه المجموعات في الموقعين، ولكن يمكنك تحريرها فقط في Exchange الإدارة. لا تظهر مجموعات التوزيع الديناميكية على صفحة **مجموعات** الأمان. 
  
 SharePoint المجموعات تلقائيا عند إنشاء مجموعة مواقع ويب. تستخدم المجموعات الافتراضية مستويات الأذونات الافتراضية في SharePoint تسمى أحيانا أدوار SharePoint لمنح المستخدمين الحقوق والوصول. لمزيد من المعلومات، راجع [المجموعات SharePoint الافتراضية في SharePoint Online](/sharepoint/default-sharepoint-groups).
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>كيف تختلف مجموعة الأمان عن مجموعات الأمان التي أنشئها في SharePoint؟

يمكن استخدام مجموعات الأمان مع SharePoint Exchange وMDM Windows والمزيد. يتم التعرف على مجموعة الأمان SharePoint التي تقوم SharePoint مجموعة المواقع.
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>هل يجب استخدام مجموعات الأمان لمنظمتي لتكون آمنة؟

لا. هذه طريقة واحدة أخرى يمكنك من خلالها إدارة الأمان لمنظمتك. يمكنك دائما منح أذونات المستخدم والوصول إلى المواقع بشكل فردي. ولكن باستخدام مجموعات الأمان، يمكنك بسهولة إدارة مجموعات أكبر من المستخدمين.
  
## <a name="can-i-send-email-to-a-security-group"></a>هل يمكنني إرسال بريد إلكتروني إلى مجموعة أمان؟

نعم. ولكن إذا كنت تريد استخدام المجموعات للبريد الإلكتروني والتعاون، نوصي بإنشاء مجموعة Microsoft 365 [بدلا من ذلك](../create-groups/create-groups.md). 

## <a name="related-content"></a>المحتوى ذي الصلة

[إنشاء مجموعة في مركز مسؤولي Microsoft 365](../create-groups/create-groups.md) (مقالة)\
[شرح Microsoft 365 المجموعات للمستخدمين](../create-groups/explain-groups-knowledge-worker.md) (مقالة)\
[إدارة مجموعة في مركز مسؤولي Microsoft 365](../create-groups/manage-groups.md) (مقالة)