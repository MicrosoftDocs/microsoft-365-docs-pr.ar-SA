---
title: مراقبة أحداث خصوصية البيانات في مؤسستك والاستجابة لها
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: استخدم سياسات التدقيق والتنبيه وطلبات موضوع البيانات لمراقبة أحداث البيانات الشخصية والاستجابة لها.
ms.openlocfilehash: 74efff60bb8e0ad6f170b57c86e384d3b689eee1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63571140"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>مراقبة أحداث خصوصية البيانات في مؤسستك والاستجابة لها

Microsoft 365 هذه الميزات لمساعدتك على مراقبة أحداث خصوصية البيانات في مؤسستك وتحريتها والاستجابة لها عند تشغيل الإمكانات ذات الصلة. قد يكون من المهم أيضا وجود عمليات وإجراءات ووثائق أخرى لكل منها لإظهار التوافق مع الجهات التنظيمية.

وتتضمن هذه الخيارات: 

- التدقيق ونهج التنبيه
- طلبات موضوع البيانات (بما في ذلك البحث في المحتوى و eDiscovery)
- أدوات التحقق وإعداد التقارير الإضافية

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>لوائح خصوصية البيانات التي تؤثر على استخدام أدوات المراقبة والاستجابة

فيما يلي قائمة نموذجية لأنظمة خصوصية البيانات التي قد ترتبط بضوابط إدارة المعلومات:

- المادة 46 من LGPD
- المادة 48 من LGPD
- مقالة GDPR (5)(1)(f)
- مقالة GDPR (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

لمزيد من المعلومات، راجع [تقييم مخاطر خصوصية البيانات وتحديد المعلومات الحساسة](information-protection-deploy-assess.md).

عادة ما تدعو أنظمة خصوصية البيانات إلى ما يلي للمراقبة والاستجابة:

- التدقيق والتنبيه وإعداد التقارير حول الأنشطة المتعلقة بمساحة تخزين البيانات الشخصية ومشاركتها ومراجعتها
- القدرة على الاستجابة لطلب موضوع البيانات (DSR) وفي بعض الحالات، تنفيذ إجراءات التحقيق وغيرها من التدابير الإدارية للامتثال لمثل هذه الطلبات.

قد ترغب مؤسستك أيضا في تنفيذ أنشطة المراقبة والاستجابة لأغراض أخرى، مثل احتياجات التوافق الأخرى أو لأسباب تتعلق بأعمال. يجب أن يتم إنشاء نظام المراقبة والاستجابة لخصوصية البيانات كجزء من التخطيط الشامل للاستجابة والمراقبة والتنفيذ والإدارة.

لمساعدتك على بدء استخدام نظام مراقبة واستجابات في Microsoft 365 لأنظمة خصوصية البيانات، تسرد هذه المقالة قدرات مفيدة في Microsoft 365 للإجابة على أسئلة مثل: 

- ما هو نوع المراقبة اليومية وتقنيات التحقق وإعداد التقارير المتوفرة لأنواع البيانات ومصادرها المختلفة؟
- ما هي الآليات المطلوبة لمعالجة طلبات موضوع البيانات (DSRs) وأي إجراءات تصحيحية، مثل إخفاء الهوية والحذف والحذف.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>سياسات التدقيق والتنبيه في مركز الأمان والتوافق

راجع هذه المقالات لإعداد التدقيق والتدقيق المتقدم ونهج التنبيه:

- [التدقيق الموحد](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [تدقيق علبة البريد](../compliance/enable-mailbox-auditing.md)
- [التدقيق المتقدم](../compliance/advanced-audit.md)
- [سياسات التنبيه](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>طلبات موضوع البيانات ل القانون العام لحماية البيانات (GDPR) و CCPA

راجع [طلبات موضوع البيانات ل القانون العام](/compliance/regulatory/gdpr-dsr-Office365) لحماية البيانات (GDPR) و CCPA للحصول على معلومات حول الاستجابة ل DSR في Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>إدارة المستخدمين المحذوفة في Microsoft Stream

بالنسبة إلى Microsoft Stream، عند حذف مستخدم من Azure Active Directory (Azure AD)، إذا كان اسمه مقترن بفيديو Stream تم نشره قبل هذه النقطة، يبقى عنوان بريده الإلكتروني مقترن بالفيديو. راجع [إدارة المستخدمين المحذوفة من Microsoft Stream](/stream/managing-deleted-users) لإزالتها.

## <a name="insider-risk-management-as-an-investigative-tool"></a>إدارة مخاطر Insider كأداة تحقق

[إدارة مخاطر Insider في Microsoft 365](../compliance/insider-risk-management.md) هي ميزة في مركز إدارة التوافق من Microsoft لمساعدتك على تقليل المخاطر الداخلية من خلال تمكينك من الكشف عن الأنشطة الخطر في مؤسستك وتحريها واتخاذ إجراء بشأنها.