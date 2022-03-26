---
title: إصلاح المشاكل المتعلقة بمزامنة الدليل Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: يصف الأسباب الشائعة للمشاكل المتعلقة بمزامنة الدليل في Office 365 ويوفر بعض الطرق للمساعدة في استكشاف الأخطاء وإصلاحها وحلها.
ms.openlocfilehash: dba6626ead648928186f8fbeac646a2b52206bc0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568989"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>إصلاح المشاكل المتعلقة بمزامنة الدليل Microsoft 365

باستخدام مزامنة الدليل، يمكنك الاستمرار في إدارة المستخدمين والمجموعات المحلية ومزامنة الإضافات والحذف والتغييرات إلى السحابة. ولكن الإعداد معقد بعض الشيء وقد يكون من الصعب أحيانا تحديد مصدر المشاكل. لدينا موارد لمساعدتك في تحديد المشاكل المحتملة وإصلاحها.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>كيف يمكنني معرفة ما إذا كان هناك خطأ ما؟

الإشارة الأولى إلى وجود خطأ ما هي عندما تشير اللوحة حالة DirSync في مركز مسؤولي Microsoft 365 إلى وجود مشكلة.
  
ستتلقى أيضا بريدا إلكترونيا (للبريد الإلكتروني البديل وبريدك الإلكتروني للمسؤول) من Microsoft 365 يشير إلى أن المستأجر واجه أخطاء في مزامنة الدليل. للحصول على التفاصيل، راجع [تحديد أخطاء](identify-directory-synchronization-errors.md) مزامنة الدليل في Microsoft 365.
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>كيف يمكنني الحصول على أداة Azure Active Directory الاتصال؟

في [مركز مسؤولي Microsoft 365،](https://admin.microsoft.com) انتقل إلى **المستخدمون** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**النشطون**</a>. انقر فوق **القائمة المزيد** (ثلاث نقاط) وحدد **مزامنة الدليل**. 
  
اتبع الإرشادات [الموجودة في المعالج](set-up-directory-synchronization.md) لتنزيل Azure AD الاتصال. 
  
إذا كنت لا تزال تستخدم Azure Active Directory (Azure AD) Sync (DirSync)، فاطلع على كيفية استكشاف أخطاء تثبيت أداة مزامنة [Azure Active Directory](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors) ومعالج التكوين وإصلاحها في Microsoft 365 للحصول على معلومات حول متطلبات النظام لتثبيت dirsync والأذونات التي تحتاج إليها وكيفية استكشاف الأخطاء الشائعة وإصلاحها. 
  
للتحديث من Azure AD Sync إلى Azure AD الاتصال، راجع [إرشادات الترقية](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>حل الأسباب الشائعة للمشاكل المتعلقة بمزامنة الدليل في Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>لا تظهر العناصر المتزامنة أو يتم تحديثها عبر الإنترنت، أو أتلقى تقارير خطأ المزامنة من الخدمة.

- [مزامنة الهوية ومعدل مرونة سمة التكرار](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>لدي تنبيه في مركز الإدارة، أو أتلقى رسائل بريد إلكتروني تلقائية بأنه لم يكن هناك حدث مزامنة حديث
- [استكشاف مشاكل الاتصال في Azure AD Connect](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [حسابات الأداة Azure AD Connect وأذوناتها](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [مزامنة Azure AD Connect: كيفية إدارة حساب خدمة Azure AD](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [توقف مزامنة الدليل مع Azure Active Directory أو تلقي تنبيه بعدم تسجيل المزامنة لأكثر من يوم واحد](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>لا تتزامن كلمات المرور، أو أرى تنبيها في مركز الإدارة بأنه لم يتم إجراء مزامنة حديثة لكلمة المرور
- [تنفيذ مزامنة تجزئة كلمات المرور مع مزامنة Azure AD Connect](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>أرى تنبيها بتجاوز الحصة النسبية للكائن
- لدينا حصة النسبية المضمنة للكائنات للمساعدة في حماية الخدمة. إذا كان لديك عدد كبير جدا من العناصر في الدليل تحتاج إلى مزامنتها Microsoft 365، حتاج إلى الاتصال ب دعم منتجات الأعمال [](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) لزيادة الحصة النسبية.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>أحتاج إلى معرفة السمات التي يتم مزامنتها
- يمكنك العثور على قائمة بكل السمات التي تتم مزامنتها بين السحابة داخل الموقع [والسحابة هنا](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>لا يمكنني إدارة الكائنات التي كانت متزامنة مع السحابة أو إزالتها
- هل أنت جاهز لإدارة العناصر في السحابة فقط؟ أو هل هناك كائن تم حذفه في الموقع، ولكنه عالق في السحابة؟ أطلع على مقالة [](/azure/active-directory/hybrid/tshoot-connect-sync-errors) استكشاف الأخطاء أثناء المزامنة والدعم هذه للحصول على إرشادات حول [](/troubleshoot/azure/active-directory/cannot-manage-objects) كيفية حل هذه المشاكل.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>تلقيت رسالة خطأ بأن شركتي تجاوزت عدد العناصر التي يمكن مزامنتها
- يمكنك قراءة المزيد حول هذه المشكلة [هنا](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>موارد أخرى

- [برنامج نصي لإصلاح الأسماء الأساسية المتكررة للمستخدم](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [كيفية إعداد مجال غير قابل التوجيه (مثل المجال المحلي.) لمزامنة الدليل](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [برنامج نصي لإحصاء إجمالي العناصر المتزامنة](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [استكشاف الأخطاء في AD FS 2.0 وإصلاحها](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [استخدام PowerShell لإصلاح سمات DisplayName الفارغة للمجموعات التي تم تمكين البريد لها](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [استخدام PowerShell لإصلاح UPN المكرر](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [استخدام PowerShell لإصلاح عناوين البريد الإلكتروني المكررة](https://go.microsoft.com/fwlink/p/?LinkId=396731)
