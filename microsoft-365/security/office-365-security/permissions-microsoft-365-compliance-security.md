---
title: الأذونات في مركز التوافق في Microsoft 365 ومركز الأمان
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: باستخدام مركز Microsoft 365 أو مركز التوافق في Microsoft 365، يمكنك إدارة الأذونات مركزيا لكل المهام ذات الصلة بالامن أو التوافق.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cc2808ffe5d0acd3a5c3c3a6252503ee5e2cf94e
ms.sourcegitcommit: e8f5d88f0fe54620308d3bec05263568f9da2931
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/03/2021
ms.locfileid: "63566131"
---
# <a name="permissions-in-the-microsoft-365-compliance-center-and-microsoft-365-security-center"></a>الأذونات في مركز التوافق في Microsoft 365 Microsoft 365 الأمان

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

تحتاج مؤسستك إلى إدارة سيناريوهات التوافق والأمان التي تمتد عبر Microsoft 365 الخدمات. وستحتاج إلى المرونة اللازمة لإعطاء المسؤول المناسب أذونات للأشخاص المناسبين في مجموعة "المعلومات" في مؤسستك. باستخدام مركز Microsoft 365 أو مركز التوافق في Microsoft 365، يمكنك إدارة الأذونات مركزيا لكل المهام ذات الصلة بالامن أو التوافق.

بعد أن يضيف المسؤول العام المستخدمين إلى أدوار المسؤولين هذه، سيكون بإمكان هذا المسؤول الوصول إلى الميزات والبيانات التي تمتد عبر كل الخدمات في Microsoft 365، مثل مركز أمان Microsoft 365 و مركز التوافق في Microsoft 365 و Azure و Office 365 و Enterprise Mobility + Security.

## <a name="what-the-microsoft-365-roles-are"></a>ما هي Microsoft 365 الأدوار

الأدوار التي تظهر في مركز التوافق في Microsoft 365 Microsoft 365 هي أدوار Azure Active Directory. تم تصميم هذه الأدوار لتتواءم مع الوظائف المهمة في مجموعة "المعلومات" في مؤسستك، مما يسهل منح الشخص كل الأذونات الضرورية إنجاز مهامه.

****

|الدور|الوصف|
|---|---|
|**المسؤول العام**|الوصول إلى جميع الميزات الإدارية في Microsoft 365 الخدمات. يمكن للمسؤولين العامين فقط تعيين أدوار المسؤولين الآخرين. لمزيد من المعلومات، راجع [المسؤول العام / مسؤول الشركة](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**مسؤول بيانات التوافق**|تعقب بيانات مؤسستك عبر Microsoft 365، وتأكد من أنها محمية، واحصل على تحليلات حول أي مشاكل للمساعدة في الحد من المخاطر. لمزيد من المعلومات، راجع [مسؤول بيانات التوافق](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**مسؤول التوافق**|ساعد مؤسستك على البقاء متوافقا مع أي متطلبات تنظيمية، وإدارة حالات eDiscovery، والحفاظ على سياسات إدارة البيانات عبر Microsoft 365 والهويات والتطبيقات. لمزيد من المعلومات، راجع [مسؤول التوافق](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**عامل تشغيل الأمان**|عرض التهديدات النشطة التي تواجه المستخدمين والأجهزة والمحتوى Microsoft 365 والرد عليها. لمزيد من المعلومات، راجع [عامل تشغيل الأمان](/azure/active-directory/roles/permissions-reference#security-operator).|
|**قارئ الأمان**|يمكنك عرض التهديدات النشطة Microsoft 365 المستخدمين والأجهزة والمحتوى الخاص بك، ولكن (على عكس عامل تشغيل الأمان) ليس لديهم الأذونات اللازمة للاستجابة من خلال اتخاذ إجراء ما. لمزيد من المعلومات، راجع [قارئ الأمان](/azure/active-directory/roles/permissions-reference#security-reader).|
|**مسؤول الأمان**|يمكنك التحكم في الأمان العام في مؤسستك من خلال إدارة سياسات الأمان ومراجعة تحليلات الأمان والتقارير عبر منتجات Microsoft 365، والبقاء على مستوى السرعة على مستوى المخاطر. لمزيد من المعلومات، راجع [مسؤول الأمان](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**القارئ العام**|إصدار القراءة فقط من **دور المسؤول** العام. عرض كل الإعدادات والمعلومات الإدارية عبر Microsoft 365. لمزيد من المعلومات، راجع [القارئ العام](/azure/active-directory/roles/permissions-reference#global-reader).|
|

## <a name="global-administrators-can-manage-roles-in-azure-active-directory"></a>يمكن للمسؤولين العامين إدارة الأدوار في Azure Active Directory

في مركز التوافق في Microsoft 365 Microsoft 365، عند تحديد دور، يمكنك عرض الواجبات الخاصة به. ولكن لإدارة هذه الواجبات، تحتاج إلى الانتقال إلى Azure Active Directory.

لمزيد من المعلومات، راجع [عرض أدوار المسؤولين وتعيينها في Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

![ارتباط لإدارة الأذونات في Azure Active Directory](../../media/permissions-manage-in-azure-ad-link.png)

## <a name="managing-roles-in-a-service-instead-of-azure-active-directory"></a>إدارة الأدوار في خدمة بدلا من Azure Active Directory

تظهر أيضا الأدوار التي تظهر في مركز التوافق في Microsoft 365 Microsoft 365 في الخدمات حيث لديهم أذونات. على سبيل المثال، يمكنك رؤية هذه الأدوار في مركز & الأمان.

![الأدوار في مركز & الأمان](../../media/m365-roles-in-o365-scc.png)

للحصول على معلومات حول كيفية استخدام هذه الأدوار في مركز & الأمان، راجع الأذونات في [مركز التوافق & الأمان](permissions-in-the-security-and-compliance-center.md).

### <a name="breaking-inheritance"></a>قطع التوريث

من المهم أن تدرك أنك عندما تدير هذه الأدوار في Azure Active Directory، تقوم بذلك مركزيا **لجميع Microsoft 365** الخدمات. ومع ذلك، عندما تدير دورا في خدمة معينة، مثل مركز & الأمان، تقوم بإدارة الدور **لهذه** الخدمة المحددة فقط. تتجاوز الواجبات والأذونات لدور في الخدمة أي أذونات تم منحها لدور Azure Active Directory.

قد يكون هذا مفيدا. على سبيل المثال، إذا تم تعيين شخص إلى دور مسؤول الأمان، فلا يكون لديه الأذونات لإدارة الأحداث. ولكن يمكنك استخدام الأذونات في Microsoft Defender ل Endpoint ل منحهم الإذن المحدد لإدارة الحوادث في تلك الخدمة.

## <a name="where-to-find-role-information-for-each-microsoft-365-service"></a>مكان العثور على معلومات الدور لكل Microsoft 365 الخدمة

من خلال تعيين مستخدم إلى أحد أدوار مسؤول Microsoft 365 الأمان أو التوافق، تمنح هذا المستخدم أذونات لنطاق من Microsoft 365 الخدمات. استخدم الارتباطات أدناه للحصول على مزيد من المعلومات حول الأذونات المحددة لدور في كل خدمة.

****

|Microsoft 365 الخدمة|معلومات الدور|
|---|---|
|أدوار المسؤولين في Office 365 Microsoft 365 لخطط الأعمال|[Microsoft 365 المسؤولين](../../admin/add-users/about-admin-roles.md)|
|Azure Active Directory (Azure AD) و Azure AD Identity Protection|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Defender for Identity|[مجموعات دور Microsoft Defender for Identity](/azure-advanced-threat-protection/atp-role-groups)|
|Azure Information Protection|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|إدارة التوافق|[إدارة التوافق](../../compliance/compliance-manager-setup.md#set-user-permissions-and-assign-roles)|
|Exchange Online|[Exchange الوصول المستند إلى الدور](/exchange/permissions-exo/permissions-exo)|
|Intune|[التحكم بالوصول المستند إلى الدور في Intune](/intune/role-based-access-control)|
|سطح المكتب المدار|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Cloud App Security|[عنصر تحكم الوصول المستند إلى الدور](/cloud-app-security/manage-admins)|
|مركز & الأمان|[Microsoft 365 المسؤولين](permissions-in-the-security-and-compliance-center.md)|
|إدارة الهويات المتميزة|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|نقاط آمنة|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|SharePoint Online|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) <p> [حول دور SharePoint في Office 365](/sharepoint/sharepoint-admin-role)|
|Teams/Skype for Business|[أدوار مسؤول Azure AD](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Defender لنقطة النهاية|[عنصر تحكم الوصول المستند إلى الدور في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/windows-defender-atp/rbac-windows-defender-advanced-threat-protection)|
|

## <a name="coming-soon"></a>قريباً

ما زلنا نعمل على الأذونات في مركز التوافق في Microsoft 365 Microsoft 365 الأمان. على سبيل المثال، نحن نعمل حاليا على دعم القدرة على:

- يمكنك إدارة الأدوار في مركز التوافق في Microsoft 365 Microsoft 365، بدلا من الذهاب إلى Azure Active Directory.
- يمكنك تخصيص الأدوار عن طريق إضافة أذونات معينة أو إزالتها.
- إنشاء أدوار مخصصة باستخدام الأذونات التي تختارها.