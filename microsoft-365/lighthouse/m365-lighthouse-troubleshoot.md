---
title: استكشاف أخطاء رسائل الخطأ ومشاكلها في Microsoft 365 Lighthouse وإصلاحها
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: troubleshooting
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، احصل على المساعدة في استكشاف أخطاء رسائل الخطأ والمشاكل وإصلاحها.
ms.openlocfilehash: 3ee2190732fdd7c9022edaa172bd45909807225c
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188867"
---
# <a name="troubleshoot-error-messages-and-problems-in-microsoft-365-lighthouse"></a>استكشاف أخطاء رسائل الخطأ ومشاكلها في Microsoft 365 Lighthouse وإصلاحها

تصف هذه المقالة رسائل الخطأ والمشاكل التي قد تواجهها أثناء استخدام Microsoft 365 Lighthouse وتوفر خطوات استكشاف الأخطاء وإصلاحها التي يمكنك اتخاذها لحلها.

## <a name="partner-onboarding"></a>إلحاق الشريك

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>رسالة عند محاولة الوصول إلى Lighthouse: "Microsoft 365 Lighthouse لا يدعم الموفرين غير المباشرين في هذا الوقت، يجب أن تكون بائعا غير مباشر أو شريك فاتورة مباشر لاستخدام هذه الخدمة"

**يسبب:** لقد حاولت الوصول إلى Lighthouse كشريك فاتورة غير مباشر. في هذا الوقت، لا تدعم Lighthouse إلا البائعين غير المباشرين وشركاء الفواتير المباشرة.

**القرار:** للحصول على قائمة كاملة بالمؤهلات والمتطلبات، راجع [متطلبات Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). إذا لم تكن موفرا غير مباشر وكنت تعتقد أنك تلقيت هذه الرسالة عن طريق الخطأ، فاتصل بالدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>رسالة عند محاولة الوصول إلى Lighthouse: "يجب أن تكون بائعا غير مباشر أو شريك فاتورة مباشرة لاستخدام هذه الخدمة"

**يسبب:** لقد حاولت الوصول إلى Lighthouse ولم تكن شريك Microsoft. يجب أن تكون مسجلا في برنامج Cloud Solution Provider (CSP) كموزع غير مباشر أو شريك فاتورة مباشرة لاستخدام Lighthouse.

**القرار:** للحصول على قائمة كاملة بالمؤهلات والمتطلبات، راجع [متطلبات Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). إذا كنت مؤهلا للوصول إلى Lighthouse وكنت تعتقد أنك تلقيت هذه الرسالة عن خطأ، فاتصل بالدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>رسالة عند تسجيل الدخول إلى Lighthouse: "قبول تعديل الشريك"

**يسبب:** لقد حاولت الوصول إلى Lighthouse قبل أن يقوم مسؤول عمومي في مستأجر الشريك بتوقيع تعديل الشريك.

**القرار:** يجب على المسؤول العام تسجيل الدخول إلى Lighthouse وقبول تعديل الشريك قبل أن تتمكن من الوصول إلى Lighthouse والعمل فيه. إذا استمر الخطأ بعد توقيع المسؤول العمومي على التعديل، فاتصل بالدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>إلحاق مستأجر العميل  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>يعرض مستأجرو العملاء حالة أخرى غير "نشطة" في قائمة المستأجرين  

**يسبب:** لا يفي مستأجرو العملاء بالمعايير التالية:

- يجب أن يكون قد تم إعداد الوصول المفوض لموفر الخدمة المدارة (MSP) لكي يتمكن من إدارة مستأجر العميل*
- يجب أن يكون لديك ترخيص Microsoft 365 Business Premium أو Microsoft 365 E3 أو Windows 365 Business أو Microsoft Defender for Business واحد على الأقل
- يجب ألا يكون لديك أكثر من 1000 مستخدم مرخص 

**القرار:** يصف الجدول التالي حالات المستأجر المختلفة التي تتطلب إجراء ويشرح كيفية حلها.

*مطلوب امتيازات المسؤول المفوض (DAP) لإلحاق العملاء إلى Lighthouse. نوصي أيضا بإنشاء امتيازات المسؤول المفوض متعدد المستويات (GDAP) مع عملائك لتمكين الوصول المفوض بشكل أكثر أمانا. في حين أن DAP وGDAP يتعايشان، فإن GDAP سيكون له الأسبقية للعملاء حيث يوجد كلا النموذجين. قريبا، سيتمكن العملاء الذين يعانون من GDAP فقط (وبدون DAP) من الإلحاق ب Lighthouse.

| حاله | الوصف | القرار |
|--|--|--|
| نشطه | تم إلحاق المستأجر بطلب من موفر الخدمات المشتركة (MSP) ولم يعد تتم إدارته في Lighthouse. | تحتاج إلى إعادة تنشيط المستأجر. في صفحة **المستأجرين** ، حدد النقاط الثلاث (المزيد من الإجراءات) إلى جانب المستأجر الذي تريد إعادة تنشيطه، ثم حدد **"تنشيط المستأجر**". قد يستغرق ظهور بيانات العميل الأولية في Lighthouse من 24 إلى 48 ساعة. |
| غير مؤهل - لم يتم إعداد DAP أو GDAP | ليس لديك امتيازات مسؤول DAP أو GDAP تم إعدادها مع المستأجر، وهو مطلوب من Lighthouse. | إعداد امتيازات مسؤول DAP أو GDAP في مركز شركاء Microsoft. |
| غير مؤهل - الترخيص المطلوب مفقود | المستأجر يفتقد ترخيصا مطلوبا. إنهم بحاجة إلى ترخيص Microsoft 365 Business Premium أو Microsoft 365 E3 أو Microsoft Defender for Business واحد على الأقل. | تأكد من تعيين ترخيص Microsoft 365 Business Premium أو Microsoft 365 E3 أو Windows 365 Business أو Microsoft Defender for Business واحد على الأقل للمستأجر. |
| غير مؤهل - تم تجاوز عدد المستخدمين | المستأجر لديه أكثر من 1000 مستخدم مرخص كحد أقصى يسمح به Lighthouse. | تحقق من أن المستأجر ليس لديه أكثر من 1000 مستخدم مرخص. |
| غير مؤهل - فشل التحقق الجغرافي | أنت والعملاء لا تقيمون في نفس المنطقة الجغرافية، والتي تتطلبها Lighthouse. | تحقق من وجود العميل في منطقتك الجغرافية. إذا لم يكن الأمر كذلك، فلا يمكنك إدارة المستأجر في Lighthouse. |
| قيد المعالجة | اكتشفت Lighthouse المستأجر ولكنها لا تزال قيد الإعداد. | السماح ل Lighthouse 48 ساعة بإكمال إلحاق المستأجر. |

إذا تأكدت من أن مستأجر العميل يفي بمعايير الإلحاق وأنه لا يزال غير **نشط في** Lighthouse، فاتصل بالدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>الوصول والأذونات

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>الرسالة عند محاولة الوصول إلى Lighthouse: "غير مخول" أو "امتيازات غير كافية" أو "تقييد الوصول: عدم كفاية الأذونات أو نقصها يتسبب في تقييد الوصول" 

**يسبب:** لا تنتمي إلى مجموعة الأمان الصحيحة في Azure AD، أو لم يتم تعيين الدور الصحيح لك في مركز الشركاء لتتمكن من الوصول إلى Lighthouse.

**القرار:** تأكد من أن مسؤولا من مستأجر شريكك لديه الأذونات المناسبة قد عينك إلى مجموعة أمان GDAP الصحيحة في Azure AD وعين لك الدور الصحيح في مركز الشركاء. ضع في اعتبارك أيضا أن بعض الإجراءات في Lighthouse تتطلب منك أن تكون مسؤولا عموميا. لمعرفة المزيد حول أدوار GDAP وما يمكن أن يفعله كل دور، راجع [نظرة عامة على الأذونات في Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). للحصول على وصف مفصل لجميع الأدوار والأذونات المضمنة Azure AD ل GDAP، راجع [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference).

بالنسبة للعملاء الذين تربطهم علاقات DAP، سيحتاج المسؤول الشريك إلى تعيينك إما إلى وكيل المسؤول أو دور وكيل Helpdesk في مركز الشركاء. للحصول على وصف مفصل لكافة أدوار وأذونات مركز الشركاء، راجع [تعيين الأدوار والأذونات للمستخدمين](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>لا أرى بيانات كاملة في مناطق معينة من Lighthouse، أو لا يمكنني تنفيذ مهام معينة، أو لا يمكنني الوصول إلى مستأجرين معينين

**يسبب:** لديك وصول محدود إلى GDAP استنادا إلى الأدوار المعينة لمجموعة أمان Azure AD التي أنت فيها.

**القرار:** تأكد من أن مسؤولا من مستأجر شريكك لديه الأذونات المناسبة قد عينك إلى مجموعة أمان GDAP الصحيحة في Azure AD. ضع في اعتبارك أيضا أن بعض الإجراءات في Lighthouse تتطلب منك أن تكون مسؤولا عموميا. لمعرفة المزيد حول أدوار GDAP وما يمكن أن يفعله كل دور، راجع [نظرة عامة على الأذونات في Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md). للحصول على وصف مفصل لجميع الأدوار والأذونات المضمنة Azure AD ل GDAP، راجع [Azure AD الأدوار المضمنة](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>إدارة مستأجري العملاء  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>لا يعرض مستأجر العميل أي بيانات في Lighthouse

**يسبب:** أنت تحاول عرض البيانات في Lighthouse قبل اكتمال إلحاق المستأجر.

**القرار:** قد يستغرق ظهور بيانات العميل الأولية في Lighthouse من 24 إلى 48 ساعة. إذا مر أكثر من 48 ساعة منذ أن قمت بإلحاق المستأجر ولا تزال غير قادر على عرض بيانات المستأجر أو تحميلها، أو إذا لم تتمكن من عرض البيانات التي كنت قد تمكنت منها مسبقا أو تحميلها، فاتصل بالدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). كن مستعدا لتوفير سجلات الشبكة ذات الصلة وقائمة بأي خيارات قد تكون تم تعديلها.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>لا يتم تحديث بيانات مستأجر العميل بعد إجراء تغييرات في مستأجر العميل

**يسبب:** قد تستغرق التغييرات التي تجريها داخل مستأجر العميل ما يصل إلى 4 ساعات للمزامنة مع بيانات مستأجر العميل في Lighthouse.

**القرار:** إذا مر أكثر من 4 ساعات ولم يتم تحديث بيانات مستأجر العميل في Lighthouse، فاتصل بقسم الدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). كن مستعدا لتوفير معلومات مستأجر العميل.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>رسالة عند تطبيق خط أساسي على مستأجر عميل: "حدث خطأ في العملية"  

**يسبب:** لم تكمل بنجاح تكوين Microsoft Intune داخل مستأجر العميل.

**القرار:** تحقق من إكمال خطوات التكوين الأساسية ل Intune داخل مستأجر العميل. إذا استمرت المشكلة بعد التحقق من اكتمال تكوين Intune لمستأجر العميل، فاتصل بالدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>لا يمكن الوصول إلى بيانات مستأجر الشريك في Lighthouse

**السبب**: يدعم Lighthouse عرض المستأجرين *العملاء* وإدارتهم فقط. ولا يدعم حاليا عرض المستأجرين *الشركاء* وإدارتهم.

**القرار:** استمر في استخدام أي أسلوب كنت تستخدمه لعرض مستأجر الشريك وإدارته.

## <a name="device-and-threat-management"></a>إدارة الأجهزة والتهديدات 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>لا أرى أي بيانات مستأجر عميل على صفحات توافق الجهاز وإدارة التهديدات في Lighthouse

**السبب 1:** لم يكتمل مستأجر العميل من الإلحاق ب Intune. لن تتوفر بيانات مستأجر العميل على صفحات توافق الجهاز أو إدارة المخاطر في Lighthouse حتى يكتمل مستأجر العميل من الإلحاق ب Intune.

**القرار:** تحقق من أن مستأجر العميل الذي تحاول عرض البيانات له قد أكمل الإلحاق إلى Intune. بمجرد اكتمال الإلحاق في Intune، اسمح بمرور 4 ساعات لكي تظهر بيانات الجهاز في Lighthouse.

**السبب 2:** تم إلحاق مستأجر العميل مؤخرا إلى Lighthouse ولا تزال البيانات قيد التحميل في Lighthouse.

**القرار:** بمجرد إلحاق مستأجر عميل إلى Lighthouse، اسمح بظهور بيانات العميل الأولية من 24 إلى 48 ساعة.

**السبب 3:** جهاز مستأجر العميل جديد وبيانات الجهاز لا تزال قيد التحميل في Lighthouse.

**القرار:** عند إضافة جهاز مستأجر، اسمح بظهور بيانات الجهاز في Lighthouse لمدة 4 ساعات.

إذا كانت البيانات لا تزال لا تظهر على صفحات توافق الجهاز وإدارة المخاطر بعد اتباع إرشادات الحل، فاتصل بقسم الدعم. لمزيد من المعلومات، راجع [الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[المشاكل المعروفة في Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (مقالة)\
[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)\
[الحصول على التعليمات والدعم Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (مقالة)
