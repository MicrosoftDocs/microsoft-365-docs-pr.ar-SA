---
title: عرض حالة مزامنة الدليل في Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.openlocfilehash: 8f21985f8db3539e8dd1a839cc6cb499a425feeb
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095543"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>عرض حالة مزامنة الدليل في Microsoft 365

إذا قمت بدمج Active Directory محلي Domain Services (AD DS) مع Azure Active Directory (Azure AD) عن طريق مزامنة البيئة المحلية مع Microsoft 365، يمكنك أيضا التحقق من حالة المزامنة.
  
## <a name="view-directory-synchronization-status"></a>عرض حالة مزامنة الدليل

- سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) واختر **حالة DirSync** على الصفحة الرئيسية.
- بدلا من ذلك، يمكنك الانتقال إلى **المستخدمين النشطين**\>، وفي صفحة **"المستخدمون النشطون**"، اختر **"المزيد من** \> **مزامنة الدليل**". في جزء **"مزامنة الدليل** "، اختر **"الانتقال إلى إدارة DirSync**".

## <a name="information-on-the-manage-directory-synchronization-page"></a>معلومات حول صفحة إدارة مزامنة الدليل

يسرد الجدول التالي الميزات التي يمكنك الحصول على معلومات حولها على الصفحة.
  
إذا كانت هناك مشكلة في مزامنة الدليل، يتم سرد الأخطاء في هذه الصفحة أيضا. لمزيد من المعلومات حول الأخطاء المختلفة التي قد تواجهها، راجع [تحديد أخطاء مزامنة الدليل في Microsoft 365](identify-directory-synchronization-errors.md).
  
|البند|ما المقصود به|
|:-----|:-----|
|**المجالات التي تم التحقق منها** | عدد المجالات في مستأجر Microsoft 365 الذي قمت بالتحقق من ملكيتك له. |
|**لم يتم التحقق من المجالات** | المجالات التي أضفتها، ولكن لم يتم التحقق منها. |
|**تمكين مزامنة الدليل** |صواب أو خطأ. تحديد ما إذا كنت قد قمت بتمكين مزامنة الدليل. |
|**أحدث مزامنة دليل** | آخر مرة تم فيها تشغيل مزامنة الدليل. سيتم عرض تحذير وارتباط إلى أداة استكشاف الأخطاء وإصلاحها إذا كانت آخر مزامنة منذ أكثر من ثلاثة أيام. |
|**تمكين مزامنة كلمة المرور** | صواب أو خطأ. تحديد ما إذا كان لديك مزامنة تجزئة كلمة المرور بين مستأجرنا المحلي ومستأجر Microsoft 365 الخاص بك. |
|**مزامنة كلمة المرور الأخيرة** | آخر مرة تم فيها تشغيل مزامنة تجزئة كلمة المرور. سيتم عرض تحذير وارتباط إلى أداة استكشاف الأخطاء وإصلاحها إذا كانت آخر مزامنة منذ أكثر من ثلاثة أيام. |
|**إصدار عميل مزامنة الدليل** | يحتوي على ارتباط تنزيل إذا تم إصدار إصدار جديد من الاتصال Azure AD. |
|**حساب خدمة مزامنة الدليل** | يعرض اسم حساب خدمة مزامنة الدليل Microsoft 365. |
|||

## <a name="monitor-synchronization-health"></a>مراقبة حالة المزامنة

في هذا القسم، ستقوم بتثبيت عامل Azure AD الاتصال Health على كل من وحدات تحكم مجال AD DS المحلية لمراقبة البنية الأساسية للهوية وخدمات المزامنة التي يوفرها Azure AD الاتصال. يتم توفير معلومات المراقبة في مدخل Azure AD الاتصال Health، حيث يمكنك عرض التنبيهات ومراقبة الأداء وتحليلات الاستخدام ومعلومات أخرى.

يستند قرار التصميم الرئيسي لكيفية استخدام Azure AD الاتصال Health إلى كيفية استخدامك الاتصال Azure AD:

- إذا كنت تستخدم خيار **المصادقة المدارة**، فابدأ [باستخدام Azure AD الاتصال Health مع المزامنة](/azure/active-directory/connect-health/active-directory-aadconnect-health-sync) لفهم وتكوين Azure AD الاتصال Health.
- إذا كنت تقوم بمزامنة أسماء الحسابات والمجموعات فقط باستخدام **المصادقة الموحدة** مع خدمات الأمان المشترك لـ Active Directory (AD FS)، فابدأ [باستخدام Azure AD الاتصال Health مع AD FS](/azure/active-directory/connect-health/active-directory-aadconnect-health-adfs) لفهم وتكوين Azure AD الاتصال Health.

عند الاكتمال، سيكون لديك:

- عامل Azure AD الاتصال Health المثبت على خوادم موفر الهوية المحلية.
- يعرض مدخل Azure AD الاتصال Health الحالة الحالية للبنية الأساسية المحلية وأنشطة المزامنة مع مستأجر Azure AD لاشتراكك في Microsoft 365.