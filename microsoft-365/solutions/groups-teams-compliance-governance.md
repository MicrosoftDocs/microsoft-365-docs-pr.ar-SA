---
title: خيارات التوافق لمجموعات Microsoft 365 والتعاون Teams SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: تعرف على خيارات التوافق للمجموعات Microsoft 365 والتعاون Teams والتعاون SharePoint.
ms.openlocfilehash: afbbc6e507d613e028f65dbc157ec2222414af8c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939115"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>خيارات التوافق لمجموعات Microsoft 365 والتعاون Teams SharePoint

يوفر Microsoft 365 مجموعة كاملة من الأدوات للحفاظ على التوافق مع تعاون المستخدمين. راجع هذه الخيارات وفكر في كيفية تعيينها لاحتياجات عملك، وحساسية بياناتك، ونطاق الأشخاص الذين يحتاج المستخدمون إلى التعاون معهم.

يوفر الجدول التالي مرجعا سريعا لعناصر التحكم في التوافق المتوفرة في Microsoft 365. يتم توفير مزيد من المعلومات في الأقسام التالية.

|الفئة|الوصف|المرجع|
|:-------|:----------|:--------|
|استبقاء المعلومات|||
||الاحتفاظ بالبريد الخاص بالمجموعات ومحتوى SharePoint|[تعرف على نهج الاستبقاء SharePoint OneDrive](../compliance/retention-policies-sharepoint.md)|
||الاحتفاظ بالدردشة والرسائل|[تعرف على نهج الاستبقاء Microsoft Teams](../compliance/retention-policies-teams.md)|
|تصنيف المعلومات|||
||تصنيف المجموعات والفرق|[استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)|
||تصنيف المحتوى الحساس تلقائيا|[تطبيق تسمية حساسية على المحتوى تلقائياً](../compliance/apply-sensitivity-label-automatically.md)|
||تشفير المحتوى الحساس|[تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](../compliance/encryption-sensitivity-labels.md)|
|حماية المعلومات|||
||منع فقدان المعلومات الحساسة|[تعرف على منع فقدان بيانات Microsoft Purview](../compliance/dlp-learn-about-dlp.md)|
||حماية المعلومات الحساسة في الدردشة.|[منع فقدان بيانات Microsoft Purview Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||تعريف المعلومات الحساسة لمؤسستك|[أنواع المعلومات الحساسة المخصصة](../compliance/sensitive-information-type-learn-about.md)|
|تجزئة المستخدم|||
||تقييد الاتصال بين مقاطع المستخدم|[عوائق المعلومات](../compliance/information-barriers.md)|
|موقع البيانات|||
||تخزين البيانات في مواقع جغرافية محددة|[Microsoft 365 متعدد المواقع الجغرافية](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>استبقاء المعلومات

تتوفر نهج الاستبقاء للاحتفاظ بالعناصر المستخدمة للتعاون في المجموعات والفرق أو حذفها، بما في ذلك الملفات والرسائل والبريد. يمكن تعيين النهج للاحتفاظ بها وحذفها أو الاحتفاظ بها فقط أو حذفها فقط. تتم حماية المعلومات التي يغطيها نهج الاستبقاء في حالة انتهاء صلاحية المجموعة أو الفريق أو حذفها.

إن تكوين نهج استبقاء مجموعات Microsoft 365 يغطي علبة بريد المجموعة وموقع SharePoint والملفات المقترنة به.

- [تعرف على نهج الاستبقاء SharePoint OneDrive](../compliance/retention-policies-sharepoint.md)

نهج الاستبقاء Teams الاحتفاظ برسائل الدردشة والقنوات. بينما يتم تخزين رسائل الدردشة والقنوات في علب بريد Exchange، فإنها لا تتأثر بنهج الاستبقاء Exchange. يجب تعيين نهج الاستبقاء لتطبيقها على Teams الدردشات ورسائل القناة Teams. 

يتم الاحتفاظ بدردشات المستخدم إلى أجل غير مسمى حتى إذا تم حذف حساب مستخدم. إذا كنت لا تريد الاحتفاظ بهذه البيانات إلى أجل غير مسمى، ففكر في استخدام نهج استبقاء لحذف دردشات المستخدم بعد وقت محدد أو تضمين هذا الحذف في عملية حذف المستخدم.

- [تعرف على نهج الاستبقاء Microsoft Teams](../compliance/retention-policies-teams.md)

- [نهج الاستبقاء في Microsoft Teams](/microsoftteams/retention-policies)

يمكن تعيين نهج استبقاء واحد لتطبيقه على Teams الدردشة ورسائل القناة Teams. 

موارد إضافية:

- [التعرف على نهج الاستبقاء](../compliance/retention.md)

- [علامات الاستبقاء ونهج الاستبقاء](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) في Exchange

## <a name="information-classification"></a>تصنيف المعلومات

يمكنك استخدام تسميات الحساسية للتحكم في وصول الضيف وخصوصية المجموعة والفريق والوصول من خلال الأجهزة غير المدارة للمجموعات والفرق. من خلال تطبيق التسمية، يتم تكوين هذه الإعدادات تلقائيا كما هو محدد بواسطة إعدادات التسمية.

- [استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md)

يمكنك تكوين Microsoft 365 لتطبيق تسميات الحساسية تلقائيا على الملفات ورسائل البريد الإلكتروني استنادا إلى المعايير التي تحددها، بما في ذلك الكشف عن أنواع المعلومات الحساسة أو مطابقة الأنماط مع المصنفات القابلة للتدريب.

- [تطبيق تسمية حساسية على المحتوى تلقائياً](../compliance/apply-sensitivity-label-automatically.md)

يمكنك استخدام تسميات الحساسية لتشفير الملفات، ما يسمح فقط للأولئك الذين لديهم أذونات بفك تشفيرها وقراءتها.

- [تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](../compliance/encryption-sensitivity-labels.md)

- [تكوين فريق مع عزل أمان](./secure-teams-security-isolation.md)

موارد إضافية:

- [التعرّف على تسميات الحساسية](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>حماية المعلومات

يمكن أن تمنع نهج DLP المشاركة العرضية للمعلومات الحساسة عبر SharePoint Exchange Teams. يمكنك إنشاء نهج تحدد الإجراءات التي يجب اتخاذها (مثل حظر الوصول) استنادا إلى مجموعة من القواعد.

- [التعرّف على تفادي فقدان البيانات](../compliance/dlp-learn-about-dlp.md)

يمكن أن يساعد DLP في Teams في حماية المعلومات الحساسة في Teams رسائل الدردشة والقنوات عن طريق حذف الرسائل التي تحتوي على معلومات حساسة.

- [منع فقدان البيانات Microsoft Teams](../compliance/dlp-microsoft-teams.md)

إذا كانت لديك معلومات حساسة فريدة لمؤسستك، مثل أسماء التعليمات البرمجية للمشروع، يمكنك إنشاء أنواع المعلومات الحساسة الخاصة بك وتطبيقها على نهج DLP لحماية المحتوى في المجموعات والفرق SharePoint.

- [أنواع المعلومات الحساسة المخصصة](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>تجزئة المستخدم

باستخدام حواجز المعلومات، يمكنك تقسيم بياناتك والمستخدمين لتقييد الاتصال غير المرغوب فيه والتعاون بين المجموعات وتجنب تعارضات الاهتمام في مؤسستك. تتيح لك حواجز المعلومات إنشاء نهج للسماح بتعاون الملفات أو الدردشة أو الاتصال أو دعوات الاجتماع أو منعها بين مجموعات من الأشخاص في مؤسستك.

- [عوائق المعلومات](../compliance/information-barriers.md)

- [حواجز المعلومات في Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [استخدام حواجز المعلومات مع SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>موقع البيانات

باستخدام Microsoft 365 Multi-Geo، يمكنك توفير وتخزين البيانات الثابتة في المواقع الجغرافية التي اخترتها لتلبية متطلبات موقع البيانات. في بيئة متعددة المناطق الجغرافية، يتكون مستأجر Microsoft 365 الخاص بك من موقع مركزي (حيث تم توفير اشتراكك في Microsoft 365 في الأصل) وموقع واحد أو أكثر من مواقع الأقمار الصناعية حيث يمكنك تخزين البيانات.

- [Microsoft 365 متعدد المواقع الجغرافية](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [التخطيط Microsoft 365 متعدد المناطق الجغرافية](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[الأمان والامتثال Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[حماية المعلومات](../compliance/information-protection.md)
