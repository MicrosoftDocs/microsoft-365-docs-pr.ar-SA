---
title: إدارة Microsoft 365 الهوية
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: تعرف على كيفية استخدام ميزات Microsoft 365 حوكمة الهوية.
ms.openlocfilehash: 35b2092412ddbeacd5d6962e110de1931b2d0f4b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569707"
---
# <a name="manage-microsoft-365-identity-governance"></a>إدارة Microsoft 365 الهوية

يتعلق حوكمة الهوية بحماية الوصول إلى الأصول الهامة ومراقبته وتدقيقه مع ضمان إنتاجية الموظفين. على سبيل المثال، باستخدام إدارة الهوية، يمكنك التأكد من أن المستخدمين المناسبين لديهم حق الوصول إلى الموارد الصحيحة وتحديد ما إذا كان هذا الوصول يتغير مع مرور الوقت.

لمزيد من المعلومات، راجع نظرة [عامة حول إدارة الهوية ل Azure Active Directory (Azure AD)](/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>إعداد مراجعات الوصول إلى Azure AD

تسمح لك مراجعات الوصول إلى Azure AD بمراجعة وصول المستخدم لضمان وصول الأشخاص المناسبين فقط. على سبيل المثال:

- عندما ينضم موظف جديد إلى مؤسستك، يجب أن تضمن حصوله على حق الوصول المناسب لكي يكون منتجا.
- مع انتقال هذا الموظف إلى فرق أو مواقع أو أقسام أخرى، يجب التأكد من إزالة إمكانية وصوله إلى الفرق أو المواقع أو الأقسام السابقة حسب الحاجة.
- عندما يغادر ذلك الموظف أو الضيف مؤسستك، ستحتاج إلى التأكد من إزالة حق الوصول الخاص به.

يكون هذا الأمر مهما بشكل خاص إذا كانت مؤسستك عرضة لتدقيقات الأمان لتحديد ما إذا كانت حسابات المستخدمين لديها إمكانية وصول كبيرة جدا، مما قد يؤدي إلى حدوث غرامة إذا كانت هناك مخالفة للأنظمة الصناعية أو الإقليمية.

لمزيد من المعلومات، راجع [نظرة عامة حول مراجعات Access](/azure/active-directory/governance/access-reviews-overview).

راجع هذه المقالات لتكوين أنواع مختلفة من مراجعات الوصول:

- [المجموعات والتطبيقات](/azure/active-directory/governance/create-access-review)
- [أدوار Azure AD](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [أدوار مورد Azure](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>إعداد إدارة استحقاق Azure AD

إدارة استحقاق Azure AD في Wiht، يمكنك إدارة الهوية والوصول إلى دورة الحياة على نطاق واسع من خلال أتمتة مهام سير عمل طلبات الوصول وواجبات الوصول والمراجعات وانتهاء الصلاحية.

يحتاج الموظفون إلى الوصول إلى مجموعات وتطبيقات ومواقع مختلفة لتنفيذ مهامهم. قد تكون إدارة هذا الوصول صعبة نظرا لتغيير المتطلبات أو إضافة تطبيقات جديدة أو يحتاج المستخدمون إلى حقوق وصول إضافية. عند التعاون في العمل مع مؤسسات أخرى، قد لا تعرف من يحتاج في المؤسسة الأخرى إلى الوصول إلى موارد مؤسستك، ولن يعرف المستخدمون الخارجيون التطبيقات أو المجموعات أو المواقع التي تستخدمها مؤسستك.

يمكن أن تساعدك إدارة استحقاق Azure AD على إدارة الوصول إلى المجموعات والتطبيقات SharePoint للمستخدمين الداخليين والخارجين بشكل أكثر فعالية.
 
لمزيد من المعلومات، راجع [نظرة عامة حول إدارة استحقاق Azure AD](/azure/active-directory/governance/entitlement-management-overview).