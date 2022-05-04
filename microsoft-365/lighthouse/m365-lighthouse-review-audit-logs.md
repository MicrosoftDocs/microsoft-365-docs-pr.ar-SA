---
title: مراجعة سجلات التدقيق في Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية مراجعة سجلات التدقيق.
ms.openlocfilehash: 59e45f33b1c6708b4743605bda6ac4c93499bf59
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188757"
---
# <a name="review-audit-logs-in-microsoft-365-lighthouse"></a>مراجعة سجلات التدقيق في Microsoft 365 Lighthouse

Microsoft 365 سجلات تدقيق Lighthouse تسجل الإجراءات التي تولد تغييرا في Lighthouse أو خدمات Microsoft 365 الأخرى. قم بإنشاء جميع الإجراءات وتحريرها وحذفها وتعيينها والإجراءات عن بعد لإنشاء أحداث تدقيق يمكنك مراجعتها. بشكل افتراضي، يتم تمكين التدقيق لجميع العملاء. لا يمكن تعطيله.

## <a name="before-you-begin"></a>قبل البدء

لعرض سجلات التدقيق، يجب أن يكون لديك أحد الأذونات التالية:

- دور Azure Active Directory (Azure AD) - المسؤول العام لمستأجر الشريك

- دور مركز شركاء Microsoft - وكيل المسؤول

## <a name="review-audit-logs"></a>مراجعة سجلات التدقيق

1. في جزء التنقل الأيمن في Lighthouse، حدد **سجلات التدقيق**.

    > [!NOTE]
    > قد يستغرق الأمر ما يصل إلى ساعة واحدة لمشاهدة السجلات الجديدة. انتقل إلى الخدمة المعنية للاطلاع على أحدث التغييرات.

2. قم بتصفية السجلات، حسب الحاجة، باستخدام الخيارات التالية:

    - **نطاق التاريخ** - الشهر أو الأسبوع أو اليوم السابق.
    - **المستأجرون** - علامات المستأجر أو أسماء مستأجري العميل.
    - **النشاط** - Microsoft 365 نوع النشاط الذي يتوافق مع الإجراء المتخذ. لمزيد من المعلومات، راجع جدول ["الأنشطة](#activities) ".
    - **تم البدء من قبل** - روبوت Who بدء الإجراء.

3. حدد سجلا من القائمة للاطلاع على التفاصيل الكاملة، بما في ذلك النص الأساسي **للطلب** .

    لتصدير بيانات السجل إلى ملف قيم مفصولة بفواصل (.csv)، حدد **"تصدير**".

## <a name="activities"></a>الانشطه

يسرد الجدول التالي الأنشطة التي تم التقاطها داخل سجلات تدقيق Lighthouse. تخضع القائمة للتغيير عند إنشاء إجراءات جديدة. يمكنك استخدام النشاط المدرج في سجل التدقيق لمعرفة الإجراء الذي تم بدؤه.<br><br>

| اسم النشاط | منطقة في المنارة | تم بدء الإجراء | الخدمة المتأثرة |
|--|--|--|--|
| **تطبيق** أو **نشر** | المستاجرين | تطبيق خطة نشر | Azure AD، إدارة نقاط النهاية من Microsoft (MEM) |
| **تعيين علامة تعريف** | المستاجرين | تطبيق علامة من عميل | المناره |
| **changeDeploymentStatus** أو **تعيين** | المستاجرين | تحديث حالة خطة العمل لخطة التوزيع | المناره |
| **عمليات التشغيل المدارة** | المستاجرين | عرض معلومات حول خطة نشر | Azure AD |
| **OffboardTenant** | المستاجرين | تعطيل عميل | المناره |
| **resetTenantOnboardingStatus** | المستاجرين | تفاعلي مع عميل | المناره |
| **tenantTags** | المستاجرين | إنشاء علامة أو حذفها | المناره |
| **tenantCustomizedInformation** | المستاجرين | إنشاء موقع ويب عميل أو معلومات جهة اتصال أو تحديثها أو حذفها | المناره |
| **إلغاء تعيين علامة تعريف** | المستاجرين | إزالة علامة من عميل | المناره |
| **التحقق** | المستاجرين | اختبار خطة نشر | Azure AD |
| **blockUserSignin** | المستخدمون | حظر تسجيل الدخول | Azure AD |
| **تأكيد عدم المعالجة** | المستخدمون | تأكيد اختراق مستخدم | Azure AD |
| **dismissUsersRisk** | المستخدمون | تجاهل مخاطر المستخدم | Azure AD |
| **إعادة تعيينUserPassword** | المستخدمون | إعادة تعيين كلمة المرور | Azure AD |
| **getConditionalAccessPolicies** | المستخدمون | عرض نهج CA التي تتطلب المصادقة متعددة العوامل | Azure AD |
| **getTenantIDToTenantNameMap** | المستخدمون | البحث عن المعرف | Azure AD |
| **getUsers** | المستخدمون | بحث عن المستخدمين | Azure AD |
| **getUsersWithoutMfa** | المستخدمون | عرض المستخدمين غير المسجلين للحصول على المصادقة متعددة العوامل | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | المستخدمون | عرض المستخدمين غير المسجلين ل SSPR | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | المستخدمون | تمكين المصادقة متعددة العوامل (MFA) باستخدام إعدادات الأمان الافتراضية | Azure AD |
|**getCompliancePolicyInfo** | الاجهزه | عرض نهج | MEM
|**getDeviceCompliancePolicyStates** | الاجهزه | عرض حالات النهج | MEM
|**getDeviceCompliancePolicySettingStates** | الاجهزه | عرض الإعدادات غير المتوافقة | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | الاجهزه | عرض الأجهزة غير المتوافقة | MEM
|**getTenantsDeviceCompliancePolicies** | الاجهزه | مقارنة النهج | MEM
| **إعادة تشغيل جهاز** | الاجهزه | اعاده تشغيل | MEM |
| **syncDevice** | الاجهزه | مزامنه | MEM |
| **إعادة التشغيل** | إدارة المخاطر | اعاده تمهيد | MEM |
| **إعادة التوفير** | Windows 365 | إعادة محاولة التوفير | Windows 365 |
| **getDeviceUserInfo** | إدارة المخاطر | عرض معلومات مستخدم الجهاز المدار  | MEM |
| **getManagedDevice** أو **remoteActionAudits** أو **deviceActionResults** | إدارة المخاطر | عرض معلومات الجهاز المدار  | MEM |
| **windowsDefenderScanFull** | إدارة المخاطر | فحص كامل | MEM |
| **windowsDefenderScan** | إدارة المخاطر | فحص سريع | MEM |
| **windowsDefenderUpdateSignatures** | إدارة المخاطر | تحديث برنامج الحماية من الفيروسات | MEM |

## <a name="next-steps"></a>الخطوات التالية

استخدم Microsoft Graph API للوصول إلى المزيد من أحداث التدقيق، إذا لزم الأمر. لمزيد من المعلومات، راجع [نظرة عامة على الإدارة متعددة المستأجرين باستخدام واجهة برمجة تطبيقات lighthouse Microsoft 365](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>المحتويات ذات الصلة

[الأسئلة المتداولة حول Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (مقالة)\
[عرض أدوار Azure Active Directory في Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (مقالة)