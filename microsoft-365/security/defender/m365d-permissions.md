---
title: إدارة الوصول Microsoft 365 Defender البيانات في مدخل Microsoft 365 Defender
description: تعرف على كيفية إدارة الأذونات للبيانات في Microsoft 365 Defender
keywords: الوصول، الأذونات، Microsoft 365 Defender، M365، الأمان، MCAS، أمان التطبيقات على السحابة، Microsoft Defender لنقطة النهاية، النطاق، RBAC
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 8e9cacf3fb7d74acc210ac0b77ed5e68c7a93961
ms.sourcegitcommit: 2c3b737e71038f843ef9e9ff4d5b99d6110b8ec5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/28/2022
ms.locfileid: "63573851"
---
# <a name="manage-access-to-microsoft-365-defender-with-azure-active-directory-global-roles"></a>إدارة الوصول إلى Microsoft 365 Defender باستخدام أدوار Azure Active Directory العامة

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

هناك طريقتان لإدارة الوصول إلى Microsoft 365 Defender:
- **أدوار Azure Active Directory (AD) العامة**
- **الوصول إلى الدور المخصص**

يمكن للحسابات المعينة أدوار **Azure Active Directory (AD)** العامة التالية الوصول إلى Microsoft 365 Defender والبيانات:
- المسؤول العام
- مسؤول الأمان
- عامل تشغيل الأمان
- القارئ العام
- قارئ الأمان

لمراجعة الحسابات بهذه الأدوار، [استعرض الأذونات في Microsoft 365 Defender المدخل](https://security.microsoft.com/permissions).

**الوصول إلى** الدور المخصص هو إمكانية جديدة في Microsoft 365 Defender ويسمح لك بإدارة الوصول إلى بيانات ومهام وإمكانيات معينة في Microsoft 365 Defender. توفر الأدوار المخصصة المزيد من التحكم مقارنة بأدوار Azure AD العالمية، مما يوفر للمستخدمين إمكانية الوصول التي يحتاجون إليها فقط بأدوار أقل تهانيا الضرورية.  يمكن إنشاء أدوار مخصصة بالإضافة إلى أدوار Azure AD العالمية. [تعرف على المزيد حول الأدوار المخصصة](custom-roles.md).

> [!NOTE]
> تنطبق هذه المقالة فقط على إدارة أدوار Azure Active Directory العامة. لمزيد من المعلومات حول استخدام عنصر تحكم وصول مخصص مستند إلى الدور، راجع [الأدوار المخصصة للتحكم بالوصول المستند إلى الدور](custom-roles.md)

## <a name="access-to-functionality"></a>الوصول إلى الوظائف
يتم تحديد الوصول إلى وظائف معينة من خلال دور [Azure AD](/azure/active-directory/roles/permissions-reference). اتصل بمسؤول عام إذا كنت بحاجة إلى الوصول إلى وظائف معينة تتطلب تعيين دور جديد لك أو لمجموعة المستخدمين.

### <a name="approve-pending-automated-tasks"></a>الموافقة على المهام التلقائية المعلقة
[يمكن أن تتخذ](m365d-autoir-actions.md) المعالجة والتحري التلقائي إجراءات بشأن رسائل البريد الإلكتروني وقواعد إعادة توجيه الرسائل والملفات آليات الاستمرار وغيرها من الإجراءات التي تم العثور عليها أثناء عمليات البحث. للموافقة على الإجراءات المعلقة أو رفضها التي تتطلب موافقة صريحة، يجب تعيين أدوار معينة في Microsoft 365. لمعرفة المزيد، راجع أذونات [مركز الإجراءات](m365d-action-center.md#required-permissions-for-action-center-tasks).

## <a name="access-to-data"></a>الوصول إلى البيانات
يمكن التحكم Microsoft 365 Defender الوصول إلى البيانات باستخدام النطاق المعين لمجموعات المستخدمين في Microsoft Defender لمراقبة الوصول المستند إلى دور نقطة النهاية (RBAC). إذا لم يتم تحديد نطاق وصولك إلى مجموعة معينة من الأجهزة في "نقطة النهاية ل Defender"، سيكون لديك حق الوصول الكامل إلى البيانات في Microsoft 365 Defender. ومع ذلك، بمجرد تحديد نطاق حسابك، لن ترى سوى بيانات حول الأجهزة الموجودة في نطاقك.

على سبيل المثال، إذا كنت تنتمي إلى مجموعة مستخدم واحدة فقط مع دور Microsoft Defender لنقطة النهاية ولم يتم منح مجموعة المستخدمين هذه حق الوصول إلى أجهزة المبيعات فقط، سترى فقط بيانات حول أجهزة المبيعات في Microsoft 365 Defender. [تعرف على المزيد حول إعدادات RBAC في Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/rbac)

### <a name="microsoft-defender-for-cloud-apps-access-controls"></a>عناصر تحكم الوصول إلى Microsoft Defender for Cloud Apps
أثناء المعاينة، Microsoft 365 Defender فرض عناصر التحكم بالوصول استنادا إلى إعدادات Defender for Cloud Apps. لا يتأثر Microsoft 365 Defender الوصول إلى البيانات بهذه الإعدادات.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أدوار مخصصة في التحكم بالوصول المستند إلى الدور Microsoft 365 Defender](custom-roles.md)
- [أدوار Azure AD المضمنة](/azure/active-directory/roles/permissions-reference)
- [Microsoft Defender ل Endpoint RBAC](/windows/security/threat-protection/microsoft-defender-atp/rbac)
- [أدوار Defender for Cloud Apps](/cloud-app-security/manage-admins)
