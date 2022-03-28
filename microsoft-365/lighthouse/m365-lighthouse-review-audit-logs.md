---
title: مراجعة سجلات التدقيق
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية مراجعة سجلات التدقيق.
ms.openlocfilehash: e16f6eb83d1fdc9f5aea2fdc6463959cc07e5650
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63574739"
---
# <a name="review-audit-logs"></a>مراجعة سجلات التدقيق

Microsoft 365 سجلات تدقيق "المنارة" إجراءات السجلات التي تقوم بإنشاء تغيير في "المنارة" أو Microsoft 365 أخرى. يمكنك إنشاء كل الإجراءات وتحريرها وحذفها وتعيينها وتحريرها عن بعد لإنشاء أحداث التدقيق التي يمكنك مراجعتها. بشكل افتراضي، يتم تمكين التدقيق لجميع العملاء. لا يمكن تعطيله.

## <a name="before-you-begin"></a>قبل البدء

لعرض سجلات التدقيق، يجب أن يكون لديك أحد الأذونات التالية:

- دور Azure Active Directory (Azure AD) - المسؤول العام للمستأجر الشريك

- دور مركز شركاء Microsoft - وكيل الإدارة

## <a name="review-audit-logs"></a>مراجعة سجلات التدقيق

1. في جزء التنقل الأيسر في المنارة، حدد **سجلات التدقيق**.

    > [!NOTE]
    > قد يستغرق الأمر ما يصل إلى ساعة واحدة لرؤية السجلات الجديدة. انتقل إلى الخدمة الخاصة بها لرؤية التغييرات الأخيرة.

2. تصفية السجلات، حسب الحاجة، باستخدام الخيارات التالية:

    - **نطاق التاريخ** - الشهر أو الأسبوع أو اليوم السابق.
    - **المستأجرون** - علامات المستأجر أو أسماء مستأجري العملاء.
    - **النشاط** - Microsoft 365 نوع النشاط الذي يتطابق مع الإجراء الذي تم اتخاذه. لمزيد من المعلومات، راجع [جدول الأنشطة](#activities) .
    - **تم البدء ب** - روبوت Who الإجراء.

3. حدد سجلا من القائمة لرؤية التفاصيل الكاملة، بما في ذلك **النصي لطلب** .

    لتصدير بيانات السجل إلى ملف قيم مفصولة ب فاصلة (.csv)، حدد **تصدير**.

## <a name="activities"></a>الأنشطة

يسرد الجدول التالي الأنشطة التي تم التقاطها في سجلات تدقيق "المنارة". تخضع القائمة للتغيير مع إنشاء إجراءات جديدة. يمكنك استخدام النشاط المدرج في سجل التدقيق لمعرفة الإجراء الذي تم اتخاذه.<br><br>

| اسم النشاط | المنطقة في المنارة | الإجراء الذي تم اتخاذه | الخدمة التي تم التأثير عليها |
|--|--|--|--|
| **تطبيق** أو **نشر** | المستأجرون | تطبيق خطة نشر | Azure AD، إدارة نقاط النهاية من Microsoft (MEM) |
| **تعيينTag** | المستأجرون | تطبيق علامة من عميل | منارة |
| **تغييرDeploymentStatus أو** **تعيين** | المستأجرون | تحديث حالة خطة الإجراء لخطة النشر | منارة |
| **managedTenantOperations** | المستأجرون | عرض معلومات حول خطة نشر | Azure AD |
| **offboardTenant** | المستأجرون | إلغاء تنشيط عميل | منارة |
| **resetTenantOnboardingStatus** | المستأجرون | تفاعل عميل | منارة |
| **tenantTags** | المستأجرون | إنشاء علامة أو حذفها | منارة |
| **tenantCustomizedInformation** | المستأجرون | إنشاء موقع ويب أو معلومات جهة اتصال للعميل أو تحديثها أو حذفها | منارة |
| **unassignTag** | المستأجرون | إزالة علامة من عميل | منارة |
| **التحقق من صحة** | المستأجرون | اختبار خطة نشر | Azure AD |
| **blockUserSignin** | المستخدمون | حظر تسجيل الدخول | Azure AD |
| **confirmUsersCompromised** | المستخدمون | تأكيد اختراق مستخدم | Azure AD |
| **تجاهلUsersRisk** | المستخدمون | تجاهل مخاطر المستخدم | Azure AD |
| **resetUserPassword** | المستخدمون | إعادة تعيين كلمة المرور | Azure AD |
| **getConditionalAccessPolicies** | المستخدمون | عرض سياسات CA التي تتطلب MFA | Azure AD |
| **getTenantIDToTenantNameMap** | المستخدمون | البحث عن الم IDS | Azure AD |
| **getUsers** | المستخدمون | البحث عن المستخدمين | Azure AD |
| **getUsersWithoutMfa** | المستخدمون | عرض المستخدمين غير المسجلين ل MFA | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | المستخدمون | عرض المستخدمين غير المسجلين في SSPR | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | المستخدمون | تمكين المصادقة متعددة العوامل (MFA) باستخدام إعدادات الأمان الافتراضية | Azure AD |
|**getCompliancePolicyInfo** | الأجهزة | عرض نهج | MEM
|**getDeviceCompliancePolicyStates** | الأجهزة | عرض ولايات النهج | MEM
|**getDeviceCompliancePolicySettingStates** | الأجهزة | عرض الإعدادات غير المتوافقة | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | الأجهزة | عرض الأجهزة غير المتوافقة | MEM
|**getTenantsDeviceCompliancePolicies** | الأجهزة | مقارنة السياسات | MEM
| **restartDevice** | الأجهزة | إعادة التشغيل | MEM |
| **syncDevice** | الأجهزة | مزامنة | MEM |
| **rebootNow** | إدارة المخاطر | إعادة التشغيل | MEM |
| **reprovision** | Windows 365 | إعادة محاولة توفير | Windows 365 |
| **getDeviceUserInfo** | إدارة المخاطر | عرض معلومات مستخدم الجهاز المدار  | MEM |
| **getManagedDevice** أو **remoteActionAudits** أو **deviceActionResults** | إدارة المخاطر | عرض معلومات الجهاز المدار  | MEM |
| **windowsDefenderScanFull** | إدارة المخاطر | فحص كامل | MEM |
| **windowsDefenderScan** | إدارة المخاطر | المسح السريع | MEM |
| **windowsDefenderUpdateSignatures** | إدارة المخاطر | تحديث برنامج الحماية من الفيروسات | MEM |

## <a name="next-steps"></a>الخطوات التالية

إذا كنت بحاجة إلى مزيد من المعلومات، فاستخدم Microsoft Graph API للوصول إلى المزيد من أحداث التدقيق. لمزيد من المعلومات، راجع نظرة عامة حول إدارة المستأجرين [المتعددين باستخدام Microsoft 365 API المنارة](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>المحتوى ذي الصلة

[Microsoft 365 الأسئلة الشائعة حول المنارة](m365-lighthouse-faq.yml) (مقالة)
