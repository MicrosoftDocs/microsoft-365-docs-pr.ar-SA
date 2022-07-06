---
title: إعداد إدارة حقوق المعلومات (IRM) في مركز إدارة SharePoint
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 239ce6eb-4e81-42db-bf86-a01362fed65c
description: تعرف على كيفية استخدام SharePoint Online IRM من خلال Microsoft Azure Active Directory خدمات إدارة الحقوق (RMS) لحماية قوائم SharePoint ومكتبات المستندات.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: af8f19fe455c1aca1d6b7aab045a9aea5b5efee5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632036"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>إعداد إدارة حقوق المعلومات (IRM) في مركز إدارة SharePoint

ضمن SharePoint Online، يتم تطبيق حماية IRM على الملفات على مستوى القائمة والمكتبة. قبل أن تتمكن مؤسستك من استخدام حماية IRM، يجب عليك أولا إعداد إدارة الحقوق. تعتمد IRM على خدمة Azure Rights Management من Azure حماية البيانات لتشفير قيود الاستخدام وتعيينها. تتضمن بعض خطط Microsoft 365 Azure Rights Management، ولكن ليس كلها. لمعرفة المزيد، اقرأ [كيف تدعم تطبيقات Office وخدماته Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>تشغيل خدمة IRM باستخدام مركز إدارة SharePoint

قبل أن تتمكن مؤسستك من حماية قوائم ومكتبات SharePoint من IRM، يجب أولا تنشيط خدمة "إدارة الحقوق" لمؤسستك. لمعرفة كيفية الاطلاع [على تنشيط Azure Rights Management](/information-protection/deploy-use/activate-service). يجب استخدام حساب العمل أو المؤسسة التعليمية الذي لديه امتيازات المسؤول العمومي لتمكين خدمة إدارة الحقوق. وإلا، فلن تتمكن من استخدام ميزات IRM مع SharePoint Online.
  
بعد تنشيط خدمة إدارة الحقوق، سجل الدخول إلى مركز إدارة SharePoint لتشغيل IRM.
  
1. سجل دخولك كمسؤول عام أو مسؤول SharePoint.
    
2. حدد أيقونة ![مشغل التطبيق أيقونة مشغل التطبيق في Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) في الزاوية العلوية اليمنى واختر **مسؤول** لفتح مركز مسؤولي Microsoft 365. (إذا لم تتمكن من رؤية اللوحة مسؤول، فليس لديك أذونات المسؤول في مؤسستك.) 
    
3. في الجزء الأيمن، اختر **مسؤول مركز** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">إدارة SharePoint</a>.
    
4. في الجزء الأيمن، اختر **الإعدادات**، ثم اختر **صفحة الإعدادات الكلاسيكية**.
    
5. في قسم **إدارة حقوق استخدام المعلومات (IRM)،** اختر **استخدام خدمة IRM المحددة في التكوين**، ثم اختر **تحديث إعدادات IRM**. بعد تحديث إعدادات IRM، يمكن للأشخاص في مؤسستك البدء في استخدام IRM في قوائم SharePoint ومكتبات المستندات الخاصة بهم. ومع ذلك، قد تستغرق الخيارات المراد تنفيذها ما يصل إلى ساعة للظهور في إعدادات المكتبة وإعدادات القائمة.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>مكتبات مستندات SharePoint وقوائمها التي تدعم IRM
<a name="__toc220831191"> </a>

بعد تحديث إعدادات IRM، يمكن لمالكي المواقع حماية قوائم SharePoint ومكتبات المستندات الخاصة بهم من IRM. لمزيد من المعلومات، راجع [تطبيق إدارة حقوق استخدام المعلومات على قائمة أو مكتبة](apply-irm-to-a-list-or-library.md).
  
عندما يقوم مالكو الموقع بتمكين IRM لقائمة أو مكتبة، يمكنهم حماية أي أنواع ملفات معتمدة في تلك القائمة أو المكتبة. عند تمكين IRM لمكتبة، تنطبق إدارة الحقوق على كافة الملفات الموجودة في تلك المكتبة. عند تمكين IRM لقائمة، تنطبق إدارة الحقوق فقط على الملفات المرفقة لعناصر القائمة، وليس عناصر القائمة الفعلية.
  
عندما يقوم الأشخاص بتنزيل الملفات في قائمة أو مكتبة ممكنة بواسطة IRM، يتم تشفير الملفات بحيث يمكن للأشخاص المخولين فقط عرضها. يحتوي كل ملف مدار بحقوق أيضا على ترخيص إصدار يفرض قيودا على الأشخاص الذين يعرضون الملف. تتضمن القيود النموذجية جعل الملف للقراءة فقط، وتعطيل نسخ النص، ومنع الأشخاص من حفظ نسخة محلية، ومنع الأشخاص من طباعة الملف. تستخدم برامج العميل التي يمكنها قراءة أنواع الملفات المدعومة من IRM ترخيص الإصدار داخل الملف المدار بحقوق لفرض هذه القيود. هذه هي الطريقة التي يحتفظ بها الملف المدار بحقوق بحمايته حتى بعد تنزيله. لتمكين IRM في قائمة أو مكتبة، راجع [تطبيق إدارة حقوق المعلومات على قائمة أو مكتبة](apply-irm-to-a-list-or-library.md).
  
لا يمكنك إنشاء مستندات أو تحريرها في مكتبة ممكنة بواسطة إدارة حقوق المعلومات (IRM) باستخدام Office في مستعرض. بدلا من ذلك، يمكن لشخص واحد في كل مرة تنزيل الملفات المشفرة ب IRM وتحريرها. استخدم تسجيل الدخول والإيداع لإدارة  *التأليف المشترك* أو التأليف عبر عدة مستخدمين. 
  
عند تنزيل ملف PDF من مكتبة محمية بواسطة IRM، ينشئ Microsoft 365 ملف PDF محميا. لن يتغير ملحق الملف، ولكن الملف محمي. لعرض هذا الملف، ستحتاج إلى عارض حماية البيانات Azure أو عميل حماية البيانات Azure الكامل أو تطبيق آخر يدعم عرض ملفات PDF المحمية.
  
يدعم SharePoint Online تشفير أنواع الملفات التالية:
  
- PDF
    
- تنسيقات الملفات 97-2003 لبرامج Microsoft Office التالية: Word وExcel وPowerPoint
    
- تنسيقات Office Open XML لبرامج Microsoft Office التالية: Word وExcel وPowerPoint
    
- تنسيق XML Paper Specification (XPS)
 
> [!NOTE]
> لا يمكن تطبيق حماية IRM على المستندات المحمية (مثل ملفات PDF الموقعة رقميا) حيث يحتاج SharePoint إلى فتح المستند عند التحميل. 

## <a name="next-steps"></a>الخطوات التالية
<a name="__toc220831191"> </a>

بمجرد تمكين IRM ل SharePoint Online، يمكنك البدء في تطبيق إدارة الحقوق على القوائم والمكتبات. للحصول على معلومات، راجع [تطبيق إدارة حقوق المعلومات على قائمة أو مكتبة](apply-irm-to-a-list-or-library.md).
  
يدعم عميل المزامنة من OneDrive الجديد لنظام التشغيل Windows الآن مزامنة مكتبات مستندات SharePoint المحمية بواسطة IRM ومواقع OneDrive (طالما لم يتم تعيين إعداد IRM للمكتبة إلى حقوق الوصول إلى المستندات التي تنتهي صلاحيتها). لمزيد من المعلومات، أو للبدء في نشر عميل المزامنة الجديد، راجع [نشر عميل المزامنة من OneDrive الجديد لنظام التشغيل Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)
