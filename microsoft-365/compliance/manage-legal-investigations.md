---
title: إدارة التحقيقات القانونية في Microsoft 365
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 2e5fbe9f-ee4d-4178-8ff8-4356bc1b168e
ms.custom:
- seo-marvel-apr2020
description: استخدم حالات eDiscovery في مدخل التوافق في Microsoft Purview لإدارة التحقيق القانوني لمؤسستك.
ms.openlocfilehash: 9db3a1e9ad831c74c9468121eaa0800875c74e5a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623794"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>إدارة التحقيقات القانونية في Microsoft 365

لدى المؤسسات العديد من الأسباب للاستجابة لحالة قانونية تتعلق ببعض المديرين التنفيذيين أو الموظفين الآخرين في مؤسستك. قد يتضمن ذلك العثور على مزيد من المعلومات الخاصة بالتحقيق والاحتفاظ بها بسرعة في البريد الإلكتروني والمستندات ومحادثات المراسلة الفورية ومواقع المحتويات الأخرى التي يستخدمها الأشخاص في مهام العمل اليومية الخاصة بهم. يمكنك تنفيذ هذه الأنشطة والعديد من الأنشطة المماثلة الأخرى باستخدام أدوات حالة eDiscovery في مركز الأمان والتوافق.
  
**هل تريد معرفة كيفية إدارة Microsoft للتحقيقات في eDiscovery؟** فيما يلي [مستند تقني تقني](https://go.microsoft.com/fwlink/?linkid=852161) يمكنك تنزيله يشرح كيفية استخدام نفس أدوات البحث والتحقيق لإدارة سير عمل eDiscovery الداخلي.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>إدارة التحقيقات القانونية مع حالات eDiscovery

تتيح لك حالات eDiscovery التحكم في الأشخاص الذين يمكنهم إنشاء حالات eDiscovery والوصول إليها وإدارتها في مؤسستك. استخدم الحالات لإضافة أعضاء والتحكم في أنواع الإجراءات التي يمكنهم تنفيذها، ووضع قائمة احتجاز على مواقع المحتوى ذات الصلة بقضية قانونية، واستخدام أداة البحث في المحتوى للبحث في المواقع المحتفظ بها عن المحتوى الذي قد يستجيب لحالتك. ثم يمكنك أيضا تصدير هذه النتائج وتنزيلها لمزيد من التحقيق من قبل المراجعين الخارجيين.
  
- [إدارة سير عمل eDiscovery الخاص بك](./get-started-core-ediscovery.md) عن طريق إنشاء حالات eDiscovery واستخدامها لكل تحقيق قانوني يجب على مؤسستك القيام به.

- [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md) للتحكم في الأشخاص الذين يمكنهم إنشاء حالات eDiscovery وإدارتها في مؤسستك.

- [إعداد حدود التوافق](set-up-compliance-boundaries.md) للتحكم في مواقع محتوى المستخدم التي يمكن لمديري eDiscovery البحث فيها.

- [ابحث عن محتوى](search-for-content.md) في مؤسستك.

### <a name="use-scripts-for-advanced-scenarios"></a>استخدام البرامج النصية للسيناريوهات المتقدمة

مثل القسم السابق الذي أدرج البرامج النصية لسيناريوهات البحث في المحتوى، أنشأنا أيضا بعض البرامج النصية Security & Compliance PowerShell لمساعدتك على إدارة حالات eDiscovery.
  
- [إنشاء تقرير احتجاز eDiscovery](create-a-report-on-holds-in-ediscovery-cases.md) يحتوي على معلومات حول كافة عمليات الاحتجاز المقترنة بحالات eDiscovery في مؤسستك.

- [أضف علب البريد ومواقع OneDrive](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) لقائمة مستخدمين إلى قائمة احتجاز eDiscovery.
  
## <a name="manage-legal-investigations-with-the-ediscovery-premium-solution-in-microsoft-365"></a>إدارة التحقيقات القانونية باستخدام حل eDiscovery (Premium) في Microsoft 365

يعتمد حل Microsoft Purview eDiscovery (Premium) في Microsoft 365 على قدرات eDiscovery والتحليلات الموجودة في Office 365. يوفر هذا الحل الجديد، *المسمى eDiscovery (Premium)* سير عمل شامل للاحتفاظ بالمحتوى الذي يستجيب للتحقيقات الداخلية والخارجية لمؤسستك وجمعه ومراجعته وتحليله وتصديره. كما يتيح للفرق القانونية إدارة سير عمل إعلام الاحتجاز القانوني بأكمله للتواصل مع أمناء الحفظ المعنيين بقضية ما.

يتطلب eDiscovery (Premium) اشتراك E5 لمؤسسة Microsoft 365 أو Office 365. لمزيد من المعلومات حول الترخيص، راجع [إعداد eDiscovery (Premium).](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)

فيما يلي نظرة عامة سريعة على سير العمل المضمن في eDiscovery (Premium). لمزيد من المعلومات، راجع [إدارة سير عمل eDiscovery (Premium](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow)).

- [إنشاء حالة](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) للبدء.

- [يمكنك إدارة أمناء الحفظ](managing-custodians.md) من خلال إضافتهم إلى قضية ووضع محتوى قانوني في علبة بريدهم وحساب OneDrive وMicrosoft Teams الأعضاء فيها.

- [إدارة الاتصالات](managing-custodian-communications.md) مع أمناء الحفظ من خلال أتمتة عملية إعلام الاحتجاز القانوني.

- [فهرسة بيانات الوصي](processing-data-for-case.md) وإصلاح أخطاء الفهرسة حتى تتمكن من جمع البيانات بشكل فعال للتحقيقات الخاصة بك.

- [جمع البيانات](collecting-data-for-ediscovery.md) لحالة [وإضافتها إلى مجموعة مراجعة](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) لمزيد من التحقيق.

- [عرض](view-documents-in-review-set.md) المستندات وبيانات [الاستعلام](review-set-search.md) وعناصر [العلامات](tagging-documents.md) في مجموعة مراجعة.

- [تحليل بيانات الحالة](analyzing-data-in-review-set.md) باستخدام أدوات التحليلات المتقدمة.

- [تصدير بيانات الحالة](exporting-data-ediscover20.md) للمراجعة من قبل مستشار خارجي.

- [إدارة الوظائف طويلة الأمد](managing-jobs-ediscovery20.md) في eDiscovery (Premium).