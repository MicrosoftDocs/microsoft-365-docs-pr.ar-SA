---
title: إصلاح المشاكل المتعلقة بمزامنة الدليل Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: يصف الأسباب الشائعة لمشكلات مزامنة الدليل في Office 365 ويوفر بعض الأساليب للمساعدة في استكشاف الأخطاء وإصلاحها وحلها.
ms.openlocfilehash: 248ccc888f047a57f474dfc55b501f4450cb116e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100996"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>إصلاح المشاكل المتعلقة بمزامنة الدليل Microsoft 365

باستخدام مزامنة الدليل، يمكنك الاستمرار في إدارة المستخدمين والمجموعات محليا ومزامنة الإضافات والحذف والتغييرات إلى السحابة. ولكن الإعداد معقد بعض الشيء وقد يكون من الصعب أحيانا تحديد مصدر المشاكل. لدينا موارد لمساعدتك في تحديد المشكلات المحتملة وإصلاحها.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>كيف أعمل تعرف ما إذا كان هناك خطأ ما؟

الإشارة الأولى إلى وجود خطأ ما هي عندما تشير لوحة حالة DirSync في مركز مسؤولي Microsoft 365 إلى وجود مشكلة.
  
ستتلقى أيضا بريدا (للبريد الإلكتروني البديل والبريد الإلكتروني للمسؤول) من Microsoft 365 يشير إلى أن المستأجر واجه أخطاء في مزامنة الدليل. للحصول على التفاصيل، راجع [تحديد أخطاء مزامنة الدليل في Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>كيف أعمل الحصول على أداة الاتصال Azure Active Directory؟

في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com)، انتقل إلى **المستخدمين النشطين للمستخدمين**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a> انقر فوق القائمة **"المزيد** " (ثلاث نقاط) وحدد **مزامنة الدليل**. 
  
اتبع [الإرشادات الموجودة في المعالج](set-up-directory-synchronization.md) لتنزيل الاتصال Azure AD. 
  
إذا كنت لا تزال تستخدم Azure Active Directory (Azure AD) Sync (DirSync)، ألق نظرة على [كيفية استكشاف أخطاء تثبيت أداة مزامنة Azure Active Directory وإصلاحها ورسائل خطأ معالج التكوين في Microsoft 365](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors) للحصول على معلومات حول متطلبات النظام لتثبيت dirsync والأذونات التي تحتاج إليها وكيفية استكشاف الأخطاء الشائعة وإصلاحها. 
  
للتحديث من Azure AD Sync إلى Azure AD الاتصال، راجع [إرشادات الترقية](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>حل الأسباب الشائعة لمشاكل مزامنة الدليل في Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>لا تظهر الكائنات المتزامنة أو تحدث عبر الإنترنت، أو أتلقى تقارير خطأ المزامنة من الخدمة.

- [مزامنة الهوية ومعدل مرونة سمة التكرار](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>لدي تنبيه في مركز الإدارة، أو أتلقى رسائل بريد إلكتروني مؤتمتة تفيد بأنه لم يكن هناك حدث مزامنة حديث
- [استكشاف مشاكل الاتصال في Azure AD Connect](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [حسابات الأداة Azure AD Connect وأذوناتها](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [مزامنة Azure AD Connect: كيفية إدارة حساب خدمة Azure AD](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [توقف مزامنة الدليل مع Azure Active Directory أو تلقي تنبيه بعدم تسجيل المزامنة لأكثر من يوم واحد](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>لا تتم مزامنة تجزئة كلمة المرور، أو أرى تنبيها في مركز الإدارة يفيد بعدم وجود مزامنة تجزئة كلمة مرور حديثة
- [تنفيذ مزامنة تجزئة كلمات المرور مع مزامنة Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>أرى تنبيها بأن الحصة النسبية للكائنات تجاوزت
- لدينا حصة نسبية مضمنة للكائن للمساعدة في حماية الخدمة. إذا كان لديك عدد كبير جدا من العناصر في الدليل تحتاج إلى المزامنة مع Microsoft 365، فسيتعين عليك [الاتصال بدعم منتجات الأعمال](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) لزيادة الحصة النسبية.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>أحتاج إلى معرفة السمات التي تتم مزامنتها
- يمكنك العثور على قائمة بجميع السمات التي تتم مزامنتها بين الموقع والسحابة [هنا](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>لا يمكنني إدارة الكائنات التي تمت مزامنتها مع السحابة أو إزالتها
- هل أنت مستعد لإدارة الكائنات في السحابة فقط؟ أم أن هناك كائنا تم حذفه محليا، ولكنه عالق في السحابة؟ ألق نظرة على هذه [الأخطاء المتعلقة باستكشاف الأخطاء وإصلاحها أثناء المزامنة](/azure/active-directory/hybrid/tshoot-connect-sync-errors) [ومقالة الدعم](/troubleshoot/azure/active-directory/cannot-manage-objects) للحصول على إرشادات حول كيفية حل هذه المشاكل.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>تلقيت رسالة خطأ تفيد بأن شركتي تجاوزت عدد العناصر التي يمكن مزامنتها
- يمكنك قراءة المزيد حول هذه المشكلة [هنا](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>موارد أخرى

- [برنامج نصي لإصلاح أسماء المستخدمين الأساسية المكررة](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [كيفية إعداد مجال غير قابل للتوجيه (مثل المجال المحلي. ) لمزامنة الدليل](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [برنامج نصي لحساب إجمالي الكائنات المتزامنة](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [استكشاف أخطاء AD FS 2.0 وإصلاحها](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [استخدام PowerShell لإصلاح سمات DisplayName الفارغة للمجموعات الممكنة للبريد](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [استخدام PowerShell لإصلاح UPN المكرر](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [استخدام PowerShell لإصلاح عناوين البريد الإلكتروني المكررة](https://go.microsoft.com/fwlink/p/?LinkId=396731)
