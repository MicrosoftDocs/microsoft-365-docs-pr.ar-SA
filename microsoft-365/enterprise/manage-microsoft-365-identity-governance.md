---
title: إدارة إدارة الهوية Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية استخدام ميزات إدارة الهوية Microsoft 365.
ms.openlocfilehash: f4fcfed9fcb978e40c3bf7c0e7a35eb717fee343
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091160"
---
# <a name="manage-microsoft-365-identity-governance"></a>إدارة إدارة الهوية Microsoft 365

حوكمة الهوية هي كل شيء عن حماية ومراقبة وتدقيق الوصول إلى الأصول الهامة مع ضمان إنتاجية الموظفين. على سبيل المثال، باستخدام حوكمة الهوية، يمكنك التأكد من أن المستخدمين المناسبين لديهم حق الوصول إلى الموارد الصحيحة وتحديد ما إذا كان هذا الوصول يتغير بمرور الوقت.

لمزيد من المعلومات، راجع هذه [النظرة العامة حول حوكمة الهوية ل Azure Active Directory (Azure AD).](/azure/active-directory/governance/identity-governance-overview)

## <a name="set-up-azure-ad-access-reviews"></a>إعداد مراجعات صلاحية الوصول إلى Azure AD

تسمح لك مراجعات صلاحية الوصول إلى Azure AD بمراجعة وصول المستخدم لضمان استمرار وصول الأشخاص المناسبين فقط. على سبيل المثال:

- عندما ينضم موظف جديد إلى مؤسستك، تحتاج إلى التأكد من أن لديه حق الوصول المناسب ليكون منتجا.
- مع انتقال هذا الموظف إلى فرق أو مواقع أو أقسام أخرى، تحتاج إلى التأكد من إزالة وصولهم إلى الفرق أو المواقع أو الأقسام السابقة حسب الحاجة.
- عند مغادرة هذا الموظف أو الضيف لمؤسستك، تحتاج إلى التأكد من إزالة وصولهم.

يعد هذا الأمر مهما بشكل خاص إذا كانت مؤسستك تخضع لعمليات تدقيق أمنية لتحديد ما إذا كانت حسابات المستخدمين لديها وصول كبير جدا، ما قد يؤدي إلى فرض غرامة إذا كانت تنتهك اللوائح الصناعية أو الإقليمية.

لمزيد من المعلومات، راجع [نظرة عامة على مراجعات صلاحية الوصول](/azure/active-directory/governance/access-reviews-overview).

راجع هذه المقالات لتكوين أنواع مختلفة من مراجعات صلاحية الوصول:

- [المجموعات والتطبيقات](/azure/active-directory/governance/create-access-review)
- [أدوار Azure AD](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [أدوار موارد Azure](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>إعداد إدارة استحقاق Azure AD

إدارة استحقاق Wiht Azure AD، يمكنك إدارة دورة حياة الهوية والوصول على نطاق واسع من خلال أتمتة مهام سير عمل طلب الوصول وتعيينات الوصول والمراجعات وانتهاء الصلاحية.

يحتاج موظفوك إلى الوصول إلى مجموعات وتطبيقات ومواقع مختلفة لأداء عملهم. يمكن أن تكون إدارة هذا الوصول صعبة بسبب تغير المتطلبات، أو إضافة تطبيقات جديدة، أو يحتاج المستخدمون إلى حقوق وصول إضافية. عندما تتعاون مع مؤسسات أخرى، قد لا تعرف من يحتاج في المؤسسة الأخرى إلى الوصول إلى موارد مؤسستك، ولن يعرف المستخدمون الخارجيون التطبيقات أو المجموعات أو المواقع التي تستخدمها مؤسستك.

يمكن أن تساعدك إدارة استحقاق Azure AD على إدارة الوصول إلى المجموعات والتطبيقات ومواقع SharePoint للمستخدمين الداخليين والداخليين بكفاءة أكبر.
 
لمزيد من المعلومات، راجع [نظرة عامة على إدارة استحقاق Azure AD](/azure/active-directory/governance/entitlement-management-overview).