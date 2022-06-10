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
ms.openlocfilehash: 5954fc193f6071dbf94277ff57f599e3bb98f7d2
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013255"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>مراقبة أحداث خصوصية البيانات في مؤسستك والاستجابة لها

تتوفر ميزات Microsoft 365 لمساعدتك على مراقبة أحداث خصوصية البيانات في مؤسستك والتحقيق فيها والاستجابة لها أثناء تشغيل القدرات ذات الصلة. وقد يكون وجود عمليات وإجراءات ووثائق أخرى لكل منها مهما أيضا لإظهار الامتثال للهيئات التنظيمية.

وتشمل هذه الخطوات ما يلي: 

- نهج التدقيق والتنبيه
- طلبات موضوع البيانات (بما في ذلك البحث في المحتوى وeDiscovery)
- أدوات التحقيق الإضافية وإعداد التقارير

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>لوائح خصوصية البيانات التي تؤثر على استخدام أدوات المراقبة والاستجابة

فيما يلي عينة من قائمة أنظمة خصوصية البيانات التي قد تتعلق بضوابط إدارة المعلومات:

- مقالة LGPD 46
- مقالة LGPD 48
- مقالة القانون العام لحماية البيانات (5)(1)(f)
- مقالة القانون العام لحماية البيانات (15)(1)(ه)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

لمزيد من المعلومات، راجع [تقييم مخاطر خصوصية البيانات وتحديد المعلومات الحساسة](information-protection-deploy-assess.md).

تستدعي لوائح خصوصية البيانات بشكل عام ما يلي للمراقبة والاستجابة:

- التدقيق والتنبيه والإبلاغ عن الأنشطة المتعلقة بتخزين البيانات الشخصية ومشاركتها ومعالجتها
- القدرة على الاستجابة لطلب موضوع البيانات (DSR) وفي بعض الحالات، تنفيذ إجراءات التحقيق وغيرها من الإجراءات الإدارية للامتثال لمثل هذه الطلبات.

قد ترغب مؤسستك أيضا في تنفيذ أنشطة المراقبة والاستجابة لأغراض أخرى، مثل احتياجات الامتثال الأخرى أو لأسباب تجارية. يجب إنشاء نظام المراقبة والاستجابة لخصوصية البيانات كجزء من المراقبة الشاملة وتخطيط الاستجابة والتنفيذ والإدارة.

لمساعدتك على البدء في نظام المراقبة والاستجابة في Microsoft 365 للوائح خصوصية البيانات، تسرد هذه المقالة إمكانات مفيدة في Microsoft 365 للإجابة عن أسئلة مثل: 

- ما نوع تقنيات المراقبة والتحقيق وإعداد التقارير اليومية المتوفرة لأنواع البيانات والمصادر المختلفة؟
- ما هي الآليات اللازمة للتعامل مع طلبات موضوع البيانات (DSRs) وأي إجراءات إصلاحية، مثل إخفاء الهوية وإعادة التوجيه والحذف.

## <a name="auditing-and-alert-policies-in-the-microsoft-purview-compliance-portal"></a>نهج التدقيق والتنبيه في مدخل توافق Microsoft Purview

راجع هذه المقالات لإعداد التدقيق والتدقيق المتقدم ونهج التنبيه:

- [تدقيق موحد](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [تدقيق علبة البريد](../compliance/enable-mailbox-auditing.md)
- [التدقيق (متميز)](../compliance/advanced-audit.md)
- [نُهج التنبيهات](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>طلبات موضوع البيانات من أجل القانون العام لحماية البيانات (GDPR) وCCPA

راجع [طلبات موضوع البيانات الخاصة ب GDPR وCCPA](/compliance/regulatory/gdpr-dsr-Office365) للحصول على معلومات حول الاستجابة لطلب موضوع البيانات في Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>إدارة المستخدمين المحذوفين في Microsoft Stream

بالنسبة إلى Microsoft Stream، عند حذف مستخدم من Azure Active Directory (Azure AD)، إذا كان اسمه مقترنا بفيديو Stream تم نشره قبل تلك النقطة، يظل عنوان بريده الإلكتروني مقترنا بالفيديو. راجع [إدارة المستخدمين المحذوفين من Microsoft Stream](/stream/managing-deleted-users) لإزالتها.

## <a name="insider-risk-management-as-an-investigative-tool"></a>إدارة المخاطر الداخلية كأداة تحقق

[إدارة المخاطر الداخلية](../compliance/insider-risk-management.md) هي ميزة من بوابة توافق Microsoft Purview لمساعدتك على تقليل المخاطر الداخلية من خلال تمكينك من الكشف عن الأنشطة المحفوفة بالمخاطر في مؤسستك والتحقيق فيها واتخاذ إجراءات بشأنها.
