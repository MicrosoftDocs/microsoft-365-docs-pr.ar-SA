---
title: إعداد إدارة حقوق استخدام المعلومات (IRM) في SharePoint إدارة
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
description: تعرف على كيفية استخدام SharePoint Online IRM عبر Microsoft Azure Active Directory إدارة الحقوق (RMS) لحماية SharePoint ومكتبات المستندات.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.openlocfilehash: 8c0f60ad1a571ba13ba83e3e92c1b5aca6535bb1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566323"
---
# <a name="set-up-information-rights-management-irm-in-sharepoint-admin-center"></a>إعداد إدارة حقوق استخدام المعلومات (IRM) في SharePoint إدارة

ضمن SharePoint Online، يتم تطبيق حماية IRM على الملفات على مستوى القائمة والمكتبة. قبل أن تتمكن مؤسستك من استخدام حماية IRM، يجب أولا إعداد إدارة الحقوق. تعتمد إدارة حقوق المعلومات على خدمة Azure Rights Management من Azure Information Protection لتشفير قيود الاستخدام وتعيينها. تتضمن Microsoft 365 خطط Azure Rights Management، وليس كلها. لمعرفة المزيد، اقرأ [كيف Office تطبيقات وخدمات Azure Rights Management](/azure/information-protection/understand-explore/office-apps-services-support).
  
## <a name="turn-on-irm-service-using-sharepoint-admin-center"></a>تشغيل خدمة إدارة حقوق المعلومات (IRM) SharePoint مركز الإدارة

قبل أن تتمكن مؤسستك من حماية SharePoint ومكتباتك، يجب أولا تنشيط خدمة إدارة الحقوق لمنظمتك. للتعرف على كيفية [تنشيط Azure Rights Management](/information-protection/deploy-use/activate-service). يجب استخدام حساب عمل أو مدرسة له امتيازات المسؤول العام لتمكين خدمة إدارة الحقوق. وبخلاف ذلك، لن تتمكن من استخدام ميزات IRM مع SharePoint Online.
  
بعد تنشيط خدمة إدارة الحقوق، سجل الدخول إلى مركز إدارة SharePoint لإدارة حقوق المعلومات (IRM).
  
1. سجل الدخول كمسؤول عام أو SharePoint عام.
    
2. حدد أيقونة "تشغيل التطبيق![" أيقونة "شريط التطبيقات" في Office 365.](../media/e5aee650-c566-4100-aaad-4cc2355d909f.png) في الزاوية العلوية اليمنى **واختر المسؤول** لفتح مركز مسؤولي Microsoft 365. (إذا لم تشاهد لوحة المسؤول، فلا تملك أذونات المسؤول في مؤسستك.) 
    
3. في الجزء الأيسر، اختر **مراكز الإدارة SharePoint** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">مركز الإدارة</a>.
    
4. في الجزء الأيسر، اختر **إعدادات**، ثم اختر **صفحة الإعدادات الكلاسيكية**.
    
5. في المقطع **إدارة حقوق استخدام المعلومات (IRM)،** اختر **استخدام خدمة IRM** المحددة في تكوينك، ثم اختر **تحديث إدارة حقوق المعلومات (IRM)** الإعدادات. بعد تحديث إعدادات IRM، يمكن للأشخاص في مؤسستك بدء استخدام IRM في SharePoint ومكتبات المستندات. ومع ذلك، قد تستغرق الخيارات للقيام بذلك ما يصل إلى ساعة لكي تظهر في مكتبة الإعدادات وقائمة الإعدادات.
    
## <a name="irm-enable-sharepoint-document-libraries-and-lists"></a>تمكين إدارة SharePoint مكتبات المستندات والقوائم
<a name="__toc220831191"> </a>

بعد تحديث إعدادات IRM، يمكن لمالكي المواقع حماية SharePoint ومكتبات المستندات. لمزيد من المعلومات، راجع [تطبيق إدارة حقوق استخدام المعلومات على قائمة أو مكتبة](apply-irm-to-a-list-or-library.md).
  
عندما يمكن مالكو المواقع إدارة حقوق المعلومات (IRM) لقائمة أو مكتبة، يمكنهم حماية أنواع الملفات المعتمدة في تلك القائمة أو المكتبة. عند تمكين IRM لمكتبة، يتم تطبيق إدارة الحقوق على كل الملفات الموجودة في تلك المكتبة. عند تمكين إدارة حقوق المعلومات (IRM) لقائمة، تنطبق إدارة الحقوق فقط على الملفات المرفقة عناصر القائمة، وليس عناصر القائمة الفعلية.
  
عندما يقوم الأشخاص بتنزيل الملفات في قائمة أو مكتبة يتم تمكين IRM لها، يتم تشفير الملفات بحيث يمكن للأشخاص المخولا فقط عرضها. يحتوي كل ملف مدار بحقوق أيضا على ترخيص إصدار يفرض قيودا على الأشخاص الذين يعرضون الملف. تتضمن القيود النموذجية جعل الملف للقراءة فقط وتعطيل نسخ النص ومنع الأشخاص من حفظ نسخة محلية ومنع الأشخاص من طباعة الملف. تستخدم برامج العملاء التي يمكنها قراءة أنواع الملفات المعتمدة من IRM ترخيص الإصدار ضمن الملف المدار بحقوق لفرض هذه القيود. هذه هي الطريقة التي يحافظ بها الملف المدار بحقوق على حمايته حتى بعد تنزيله. لتمكين إدارة حقوق المعلومات (IRM) في قائمة أو مكتبة، راجع [تطبيق إدارة حقوق استخدام المعلومات على قائمة أو مكتبة](apply-irm-to-a-list-or-library.md).
  
لا يمكنك إنشاء مستندات أو تحريرها في مكتبة تم تمكينها بواسطة IRM باستخدام Office في مستعرض. بدلا من ذلك، يمكن لشخص واحد في كل مرة تنزيل الملفات المشفرة باستخدام IRM وتحريرها. استخدم تسجيل الدخول والتحقق لإدارة التأليف  *المشترك أو التأليف*  عبر مستخدمين متعددين. 
  
عندما تقوم بتنزيل ملف PDF من مكتبة محمية ب IRM، Microsoft 365 ملف PDF محمي. لن يتغير ملحق الملف، ولكن الملف محمي. لعرض هذا الملف، ستحتاج إلى عارض Azure Information Protection أو عميل Azure Information Protection الكامل أو تطبيق آخر يدعم عرض ملفات PDF المحمية. 
  
SharePoint Online تشفير أنواع الملفات التالية:
  
- PDF
    
- تنسيقات الملفات 97-2003 لبرامج Microsoft Office التالية: Word Excel PowerPoint
    
- يتم Office تنسيقات Open XML لبرامج Microsoft Office التالية: Word Excel وxml PowerPoint
    
- تنسيق XML Paper Specification (XPS)
 
> [!NOTE]
> لا يمكن تطبيق حماية إدارة حقوق المعلومات (IRM) على المستندات المحمية (مثل ملفات PDF الموقعة رقميا) SharePoint يجب فتح المستند عند التحميل. 

## <a name="next-steps"></a>الخطوات التالية
<a name="__toc220831191"> </a>

بعد تمكين إدارة حقوق المعلومات SharePoint Online، يمكنك بدء تطبيق إدارة الحقوق على القوائم والمكتبات. للحصول على معلومات، راجع [تطبيق إدارة حقوق استخدام المعلومات على قائمة أو مكتبة](apply-irm-to-a-list-or-library.md).
  
يدعم عميل المزامنة من OneDrive الجديد ل Windows الآن مزامنة مكتبات مستندات SharePoint ومواقع OneDrive المحمية من قبل إدارة حقوق المعلومات (IRM) (طالما لم يتم تعيين إعداد IRM للمكتبة لينتهي صلاحية حقوق الوصول إلى المستند). لمزيد من المعلومات، أو للبدء في نشر عميل المزامنة الجديد، راجع نشر عميل المزامنة من OneDrive [الجديد Windows](/onedrive/deploy-on-windows).
  
[Top of page](set-up-irm-in-sp-admin-center.md)