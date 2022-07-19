---
title: نظرة عامة على الأذونات في Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: magarlan, chrigreen
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على المزيد حول متطلبات أذونات Lighthouse.
ms.openlocfilehash: 0ccc47fd151fa681b0231b2f776de3d2c46c5784
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66857381"
---
# <a name="overview-of-permissions-in-microsoft-365-lighthouse"></a>نظرة عامة على الأذونات في Microsoft 365 Lighthouse

الوصول المفوض إلى مستأجري العملاء مطلوب لموفري الخدمات المدارة (MSPs) لاستخدام Microsoft 365 Lighthouse. تمنح امتيازات مسؤول متعددة المستويات (GDAP) موفري الخدمات الإدارية مستوى عاليا من التحكم والمرونة من خلال توفير وصول العملاء من خلال [أدوار Azure Active Directory (Azure AD) المضمنة](/azure/active-directory/roles/permissions-reference). يؤدي تعيين الأدوار الأقل امتيازا حسب المهمة من خلال GDAP إلى فنيي MSP إلى تقليل مخاطر الأمان لكل من MSPs والعملاء. لمزيد من المعلومات حول الأدوار الأقل امتيازا حسب المهمة، راجع [الأدوار الأقل امتيازا - مركز الشركاء](/partner-center/gdap-least-privileged-roles-by-task) [والأدوار المتميزة الأقل حسب المهمة في Azure Active Directory](/azure/active-directory/roles/delegate-by-task). لمزيد من المعلومات حول إعداد علاقة GDAP مع مستأجر عميل، راجع [الحصول على أذونات المسؤول متعددة المستويات لإدارة خدمة العميل - مركز الشركاء.](/partner-center/gdap-obtain-admin-permissions-to-manage-customer)

نوصي بتعيين أدوار لمجموعات من فنيي MSP استنادا إلى المهام التي تحتاج كل مجموعة إلى تنفيذها نيابة عن العميل. على سبيل المثال، قد يحتاج فنيو Service Desk فقط إلى قراءة بيانات مستأجر العميل أو إعادة تعيين كلمات مرور المستخدم. في المقابل، قد يحتاج مهندسو التصعيد إلى اتخاذ المزيد من الإجراءات التصحيحية لتحديث إعدادات أمان مستأجر العميل. من أفضل الممارسات تعيين أقل دور متساهل مطلوب لإكمال مهمة ما حتى يتم الحفاظ على أمان بيانات العميل والشركاء. نوصي باستخدام إدارة الهويات المتميزة (PIM) لتمكين الوصول ذي النطاق الزمني إلى دور المسؤول العام، إذا لزم الأمر. إن منح عدد كبير جدا من المستخدمين إمكانية الوصول العالمي يشكل خطرا أمنيا، ونوصي بالحد منه قدر الإمكان. لمزيد من المعلومات حول كيفية تمكين PIM، راجع [إعداد Azure AD PIM.](m365-lighthouse-configure-portal-security.md#set-up-azure-ad-privileged-identity-management-pim)

تصف الجداول في القسم التالي أدوار GDAP التي تمنح الإذن لقراءة بيانات العميل واتخاذ إجراء بشأن مستأجري العملاء في Lighthouse. راجع [الأذونات في مستأجر الشريك](#permissions-in-the-partner-tenant) في هذه المقالة للحصول على أدوار إضافية مطلوبة لإدارة كيانات Lighthouse (على سبيل المثال، العلامات وطلبات خدمة Lighthouse).

## <a name="example-msp-service-tiers-recommended-gdap-roles-and-permissions"></a>مثال على مستويات خدمة MSP، وأدوار GDAP الموصى بها، والأذونات

يسرد الجدول التالي أدوار GDAP الموصى بها لبعض مستويات خدمة MSP كمثال. 

|| مديرو الحسابات| فنيو Service Desk | مسؤولو النظام | مهندسو التصعيد|
|---|---|---|---|---|
| **أدوار GDAP الموصى بها** |<ul><li>مسؤول Helpdesk</li></ul> |<ul><li>قارئ الأمان<br>+</li><li>مسؤول Helpdesk</li></ul> |<ul><li>القارئ العمومي<br>+</li><li>مسؤول المستخدم<br>+</li><li>مسؤول المصادقة</li></ul> |<ul><li>القارئ العمومي<br>+</li><li>مسؤول المستخدم<br>+</li><li>مسؤول Intune<br>+</li><li>مسؤول الأمان</li></ul>|

يسرد الجدول التالي الإجراءات التي يمكن لمستويات خدمة MSP المثال تنفيذها على صفحات Lighthouse المختلفة كما تحددها أدوار GDAP المعينة (المشار إليها في الجدول السابق).

| صفحة Lighthouse | الإجراءات المسموح بها لمديري الحسابات| الإجراءات المسموح بها من قبل فنيي Service Desk |الإجراءات المسموح بها لمسؤولي النظام | الإجراءات المسموح بها لمهندسي التصعيد|
|---|---|---|---|---|
| Home  | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | 
| المستاجرين     | <ul><li>عرض قائمة المستأجرين</li><li>تحديث جهات اتصال العملاء وموقع الويب</li><li>عرض خطط النشر</li></ul>  | <ul><li>عرض قائمة المستأجرين</li><li>تحديث جهات اتصال العملاء وموقع الويب</li><li>عرض خطط النشر</li></ul>   |  <ul><li>عرض قائمة المستأجرين</li><li>تحديث جهات اتصال العملاء وموقع الويب</li><li>عرض خطط النشر</li><li>عرض استخدام خدمات Microsoft 365</li></ul> | <ul><li>عرض قائمة المستأجرين</li><li>تحديث جهات اتصال العملاء وموقع الويب</li><li>عرض خطط النشر</li><li>عرض استخدام خدمات Microsoft 365</li></ul>  |
| المستخدمون   | <ul><li>عرض بيانات مستوى المستأجر (غير الخاصة للمستخدم)</li><li>البحث في حسابات المستخدمين عبر المستأجرين</li><li>إعادة تعيين كلمة المرور لغير المسؤولين*</li></ul>  | <ul><li>عرض كافة البيانات الخاصة بكل مستخدم</li><li>البحث في حسابات المستخدمين عبر المستأجرين</li><li>إعادة تعيين كلمة المرور لغير المسؤولين*</li></ul>|  <ul><li>عرض كافة البيانات الخاصة بكل مستخدم</li><li>البحث في حسابات المستخدمين عبر المستأجرين</li><li>إعادة تعيين كلمة المرور لغير المسؤولين*</i><li>حظر تسجيل الدخول</li></ul>  | <ul><li>عرض كافة البيانات الخاصة بكل مستخدم</li><li>البحث في حسابات المستخدمين عبر المستأجرين</li><li>إعادة تعيين كلمة المرور لغير المسؤولين*</li><li>حظر تسجيل الدخول</li><li>تأكيد المستخدمين المخترقين</li><li>تجاهل المخاطر للمستخدمين</li></ul> |
| الاجهزه    | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li><li>مزامنة الجهاز</li><li>إعادة تشغيل الجهاز</li><li>جمع التشخيصات</li></ul>|
| إدارة المخاطر  | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li><li>تشغيل الفحص الكامل</li><li>تشغيل الفحص السريع</li><li>تحديث الحماية من الفيروسات</li><li>إعادة تشغيل الجهاز</li></ul>|
| خطوط الاساس    | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul>  | <ul><li>عرض كافة البيانات</li></ul> |
| Windows 365 | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> | <ul><li>عرض كافة البيانات</li></ul> |
| Estado de funcionamento dos serviços**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A |
| سجلات التدقيق**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;N/A |

*راجع [أذونات إعادة تعيين كلمة المرور](/azure/active-directory/roles/permissions-reference#password-reset-permissions) لجدول يسرد الأدوار المطلوبة لإعادة تعيين كلمات المرور لمسؤولي مستأجري العملاء.

**مطلوب أدوار وأذونات مختلفة لعرض سجلات Estado de funcionamento dos serviços والتدقيق. لمزيد من المعلومات، راجع [الأذونات في مستأجر الشريك](#permissions-in-the-partner-tenant).

> [!NOTE]
> إذا تلقيت رسالة في Lighthouse تفيد بأنه ليس لديك الإذن لعرض المعلومات أو تحريرها، يتم تعيين دور ليس لديك الأذونات المناسبة لتنفيذ الإجراء. ستحتاج إلى التواصل مع مسؤول في مستأجر شريكك يمكنه تعيين الدور المناسب للإجراء الذي تحاول تنفيذه.

## <a name="delegated-admin-privileges-dap-in-lighthouse"></a>امتيازات مسؤول المفوضة (DAP) في Lighthouse

سيقوم GDAP في النهاية باستبدال DAP كأسلوب أساسي لتكوين الوصول المفوض لمستأجري العملاء. ومع ذلك، إذا لم يتم إعداد GDAP، فقد يستمر فنيو MSP في الوصول إلى Lighthouse باستخدام وكيل Helpdesk أو أدوار عامل مسؤول الممنوحة من خلال DAP. بالنسبة للعملاء الذين يتعايشون مع GDAP وDAP، فإن الأدوار الممنوحة لفنيي MSP من خلال GDAP لها الأسبقية. لمزيد من المعلومات حول إهمال GDAP أو DAP، راجع [الأسئلة المتداولة حول GDAP](/partner-center/gdap-faq) أو [إعلانات مركز الشركاء](/partner-center/announcements/2022-march#15) للتواريخ والجداول الزمنية.

بالنسبة للعملاء الذين لديهم DAP وبدون GDAP، يمنح دور عامل مسؤول أذونات لعرض جميع بيانات المستأجر واتخاذ أي إجراء في Lighthouse (انظر أدناه للإجراءات الأخرى التي تتطلب أيضا دورا في المستأجر الشريك).

يمنح دور عامل Helpdesk أذونات لعرض جميع بيانات المستأجر واتخاذ إجراءات محدودة في Lighthouse، مثل إعادة تعيين كلمات مرور المستخدم، وحظر عمليات تسجيل دخول المستخدم، وتحديث معلومات جهات اتصال العملاء ومواقع الويب.

نظرا للأذونات الواسعة الممنوحة للمستخدمين الشركاء الذين لديهم أدوار DAP، نوصي باعتماد GDAP في أقرب وقت ممكن. 

## <a name="permissions-in-the-partner-tenant"></a>الأذونات في مستأجر الشريك

بالنسبة إلى إجراءات معينة في Lighthouse، يلزم تعيينات الأدوار في مستأجر الشريك. يسرد الجدول التالي أدوار مستأجر الشريك والأذونات المقترنة بها.

| أدوار مستأجر الشريك | الأذونات |
|--|--|
| المسؤول العام لمستأجر الشريك | <ul><li>التسجيل للحصول على Lighthouse في مركز مسؤولي Microsoft 365.</li><li>اقبل تعديلات عقد الشريك أثناء تجربة التشغيل الأول.</li><li>تنشيط المستأجر وإلغاء تنشيطه.</li><li>إنشاء علامات وتحديثها وحذفها.</li><li>تعيين العلامات وإزالتها من مستأجر العميل.</li><li>مراجعة سجلات التدقيق</li></ul> |
| عضو مستأجر شريك له دور Azure AD واحد على الأقل تم تعيينه مع مجموعة الخصائص التالية:<br>**microsoft.office365.supportTickets/allEntities/allTasks**<br>(للحصول على قائمة كاملة بالأدوار Azure AD، راجع [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference).) | إنشاء طلبات خدمة Lighthouse. |
| عضو مستأجر شريك يفي *بكل* من المتطلبات التالية: <ul><li>له دور Azure AD واحد على الأقل تم تعيينه مع مجموعة الخصائص التالية:<br>**microsoft.office365.serviceHealth/allEntities/allTasks**<br>(للحصول على قائمة كاملة بالأدوار Azure AD، راجع [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference).)</li><li>لديه دور مفوض DAP واحد على الأقل معين (عامل مسؤول أو وكيل Helpdesk)</li></ul> | عرض معلومات حماية الخدمة. |

## <a name="related-content"></a>المحتويات ذات الصلة

[متطلبات Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (مقالة)  
[الأسئلة المتداولة حول امتيازات الإدارة المفوضة (DAP)](/partner-center/dap-faq) (مقالة)  
[عرض أدوار Azure Active Directory في Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (مقال)  
[تعيين الأدوار والأذونات للمستخدمين](/partner-center/permissions-overview) (مقالة)  
[نظرة عامة على Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (مقال)  
[التسجيل في Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (مقالة)  
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)
