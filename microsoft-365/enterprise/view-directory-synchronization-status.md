---
title: عرض حالة مزامنة الدليل في Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: في هذه المقالة، تعرف على كيفية التحقق من حالة مزامنة الدليل في Office 365.
ms.openlocfilehash: 0cc5b5244c5809d3f1b13b15b200bd8cea585c7c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63576927"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>عرض حالة مزامنة الدليل في Microsoft 365

إذا قمت بدمج خدمات مجال Active Directory المحلية (AD DS) مع Azure Active Directory (Azure AD) من خلال مزامنة البيئة المحلية مع Microsoft 365، يمكنك أيضا التحقق من حالة المزامنة.
  
## <a name="view-directory-synchronization-status"></a>عرض حالة مزامنة الدليل

- سجل [الدخول إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) واختر **حالة DirSync** على الصفحة الرئيسية.
- بدلا من ذلك، يمكنك **الانتقال إلى** \> المستخدمون **النشطون**، وفي صفحة  المستخدمون النشطون، اختر **المزيد** \> **من مزامنة الدليل**. في جزء **مزامنة الدليل** ، اختر **الانتقال إلى إدارة DirSync**.

## <a name="information-on-the-manage-directory-synchronization-page"></a>معلومات على صفحة إدارة مزامنة الدليل

يسرد الجدول التالي الميزات التي يمكنك الحصول على معلومات حولها على الصفحة.
  
إذا كانت هناك مشكلة في مزامنة الدليل، يتم سرد الأخطاء في هذه الصفحة أيضا. لمزيد من المعلومات حول الأخطاء المختلفة التي قد تواجهها، راجع تحديد أخطاء مزامنة الدليل [في](identify-directory-synchronization-errors.md) Microsoft 365.
  
|عنصر|ما هي|
|:-----|:-----|
|**المجالات التي تم التحقق منها** | عدد المجالات في Microsoft 365 المستأجر الذي قمت بالتحقق منه بنفسك. |
|**المجالات غير المتحقق منها** | المجالات التي أضفتها، ولكن لم يتم التحقق منها. |
|**تمكين مزامنة الدليل** |True أو False. يحدد ما إذا قمت بتمكين مزامنة الدليل أم لا. |
|**أحدث مزامنة دليل** | آخر مرة تم فيها العمل على مزامنة الدليل. سيتم عرض تحذير وربط إلى أداة استكشاف الأخطاء وإصلاحها إذا كانت آخر مزامنة منذ أكثر من ثلاثة أيام. |
|**تمكين مزامنة كلمة المرور** | True أو False. تحدد هذه الخاصية ما إذا كان لديك مزامنة كلمة مرور بين المستأجر Microsoft 365 المحلية. |
|**مزامنة كلمة المرور الأخيرة** | آخر مرة تم فيها استخدام مزامنة كلمة المرور المتزامنة. سيتم عرض تحذير وربط إلى أداة استكشاف الأخطاء وإصلاحها إذا كانت آخر مزامنة منذ أكثر من ثلاثة أيام. |
|**إصدار عميل مزامنة الدليل** | يحتوي على ارتباط تنزيل إذا تم إصدار إصدار جديد من Azure AD الاتصال إصداره. |
|**حساب خدمة مزامنة الدليل** | يعرض اسم حساب خدمة مزامنة Microsoft 365 الدليل. |
|||

## <a name="monitor-synchronization-health"></a>مراقبة حالة المزامنة

في هذا القسم، سيتم تثبيت عامل حماية Azure AD الاتصال على كل وحدة من وحدات تحكم مجال AD DS المحلية لمراقبة البنية الأساسية لهويتك وخدمات المزامنة التي يوفرها Azure AD الاتصال. تتوفر معلومات المراقبة في مدخل Azure AD الاتصال Health، حيث يمكنك عرض التنبيهات ومراقبة الأداء وتحليلات الاستخدام ومعلومات أخرى.

يستند قرار التصميم الرئيسي الخاص بكيفية استخدام Azure AD الاتصال Health إلى كيفية استخدام Azure AD الاتصال:

- إذا كنت تستخدم خيار المصادقة  المدارة، فابدأ باستخدام [Azure AD الاتصال مع](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) المزامنة لفهم Azure AD وتكوينه الاتصال Health.
- إذا كنت تعمل على مزامنة أسماء الحسابات والمجموعات فقط باستخدام المصادقة الخارجية مع خدمات  اتحاد Active Directory (AD FS)، فابدأ باستخدام [Azure AD الاتصال Health مع AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) لفهم Azure AD الاتصال Health وتكوينه.

عند الانتهاء، سيكون لديك:

- تم تثبيت عامل الاتصال Azure AD على خوادم موفري الهوية المحليين.
- يعرض مدخل Azure AD الاتصال الحالة الحالية للبنية الأساسية المحلية وأنشطة المزامنة مع مستأجر Azure AD لاشتراكك في Microsoft 365.