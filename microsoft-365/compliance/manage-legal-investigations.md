---
title: إدارة التحريات القانونية في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: استخدم حالات eDiscovery في مركز التوافق في Microsoft 365 لإدارة التحقيق القانوني في مؤسستك.
ms.openlocfilehash: fc4e89645ef1912c33ab89ec190c87dc9c8a8965
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566319"
---
# <a name="manage-legal-investigations-in-microsoft-365"></a>إدارة التحريات القانونية في Microsoft 365

لدى المؤسسات أسباب كثيرة للاستجابة إلى حالة قانونية تتعلق بموظفين تنفيذيين معينين أو موظفين آخرين في مؤسستك. قد يتضمن ذلك البحث بسرعة والاحتفاظ بمعلومات إضافية خاصة بالتحقيق في البريد الإلكتروني والمستندات ومحادثات المراسلة الفورية ومواقع المحتوى الأخرى التي يستخدمها الأشخاص في مهام العمل اليومية. يمكنك تنفيذ هذه الأنشطة والعديد من الأنشطة المشابهة الأخرى باستخدام أدوات حالة eDiscovery في مركز الأمان والتوافق.
  
**هل تريد معرفة كيفية إدارة Microsoft لتحريات eDiscovery؟** إليك [ورقة تقنية بيضاء](https://go.microsoft.com/fwlink/?linkid=852161) يمكنك تنزيلها تشرح كيفية استخدام أدوات البحث والتحري نفسها لإدارة سير عمل eDiscovery الداخلي.

## <a name="manage-legal-investigations-with-ediscovery-cases"></a>إدارة التحقيق القانوني مع حالات eDiscovery

تسمح لك حالات eDiscovery بالتحكم في الأشخاص الذين يمكنهم إنشاء حالات eDiscovery والوصول إليها وإدارتها في مؤسستك. استخدم الحالات لإضافة الأعضاء والتحكم في أنواع الإجراءات التي يمكنهم تنفيذها، وضع وضع الانتظار على مواقع المحتويات ذات الصلة بقضيتك القانونية، واستخدام أداة البحث في المحتوى للبحث في المواقع المحتفظ بها عن المحتوى الذي قد يكون مستجيبا لقضيتك. بعد ذلك، يمكنك أيضا تصدير هذه النتائج وتنزيلها لمزيد من التحقيق من قبل المراجعين الخارجيين.
  
- [يمكنك إدارة سير عمل eDiscovery بإنشاء](./get-started-core-ediscovery.md) حالات eDiscovery واستخدامها لكل تحقيق قانوني يجب على مؤسستك القيام به.

- [قم بتعيين أذونات eDiscovery](assign-ediscovery-permissions.md) للتحكم في الأشخاص الذين يمكنهم إنشاء حالات eDiscovery وإدارتها في مؤسستك.

- [قم بإعداد حدود التوافق](set-up-compliance-boundaries.md) للتحكم في مواقع محتوى المستخدم التي يمكن لمديري eDiscovery البحث فيها.

- [ابحث عن المحتوى](search-for-content.md) في مؤسستك.

### <a name="use-scripts-for-advanced-scenarios"></a>استخدام البرامج النصية للسيناريوهات المتقدمة

مثل القسم السابق الذي أدرج البرامج النصية لسيناريوهات البحث في المحتوى، قمنا أيضا بإنشاء بعض برامج الأمان & مركز التوافق PowerShell لمساعدتك على إدارة حالات eDiscovery.
  
- [أنشئ تقرير الاستمرار في eDiscovery](create-a-report-on-holds-in-ediscovery-cases.md) يحتوي على معلومات حول كل حالات الاحتفاظ المقترنة ب eDiscovery في مؤسستك.

- [أضف علب البريد OneDrive مواقع](use-a-script-to-add-users-to-a-hold-in-ediscovery.md) لقائمة المستخدمين إلى قائمة eDiscovery.
  
## <a name="manage-legal-investigations-with-the-advanced-ediscovery-solution-in-microsoft-365"></a>إدارة التحريات القانونية باستخدام Advanced eDiscovery في Microsoft 365

يعتمد Advanced eDiscovery في Microsoft 365 على قدرات eDiscovery والتحليلات الموجودة في Office 365. يوفر هذا الحل الجديد *، Advanced eDiscovery*، سير عمل شامل للمحافظة على المحتوى الذي يستجيب إلى التحريات الداخلية والخارجية في مؤسستك وجمعه ومراجعته وتحليله وتصديره. كما يتيح أيضا للفرق القانونية إدارة سير عمل إعلام الاحتجاز القانوني بالكامل للتواصل مع اطباء الوصاية المشاركين في قضية ما.

Advanced eDiscovery اشتراك E5 Microsoft 365 أو Office 365 المؤسسة. لمزيد من المعلومات حول الترخيص، راجع [إعداد](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses) Advanced eDiscovery.

فيما يلي نظرة عامة سريعة حول سير العمل المضمن في Advanced eDiscovery. لمزيد من المعلومات، راجع [إدارة سير Advanced eDiscovery العمل](create-and-manage-advanced-ediscoveryv2-case.md#manage-the-workflow).

- [أنشئ حالة للبدء](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) .

- [يمكنك إدارة](managing-custodians.md) التغذية عن طريق إضافتهم إلى حالة ووضع قيد الاحتجاز القانوني على المحتوى في علبة البريد الخاصة بهم، OneDrive حسابهم، Microsoft Teams أعضاء فيها.

- [يمكنك إدارة](managing-custodian-communications.md) الاتصالات مع اطباء التكاتف من خلال أتمتة عملية إعلام الاحتجاز القانوني.

- [فهرسة البيانات الفهرسة](processing-data-for-case.md) وإصلاح أخطاء الفهرسة حتى تتمكن من تجميع البيانات بشكل فعال من أجل إجراء التحريات.

- [تجميع بيانات](collecting-data-for-ediscovery.md) حالة [وإضافتها إلى مجموعة مراجعة لمزيد](collecting-data-for-ediscovery.md#add-search-results-to-a-review-set) من التحقيق.

- [عرض](view-documents-in-review-set.md) [المستندات وبيانات](review-set-search.md) الاستعلامات [والعناصر](tagging-documents.md) ذات العلامات في مجموعة مراجعة.

- [تحليل بيانات الحالة](analyzing-data-in-review-set.md) باستخدام أدوات التحليلات المتقدمة.

- [تصدير بيانات حالة الدعوى](exporting-data-ediscover20.md) لمراجعتها من قبل مستشار خارجي.

- [إدارة المهام الطويلة في](managing-jobs-ediscovery20.md) Advanced eDiscovery.