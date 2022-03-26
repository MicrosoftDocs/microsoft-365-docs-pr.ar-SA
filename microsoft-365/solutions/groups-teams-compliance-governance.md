---
title: خيارات التوافق Microsoft 365 مجموعات Teams والتعاون SharePoint المشترك
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
description: تعرف على خيارات التوافق Microsoft 365 المجموعات Teams والتعاون SharePoint المشترك.
ms.openlocfilehash: ab840ea5652a13087ecc8d505391bac152ca1052
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/17/2021
ms.locfileid: "63568735"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>خيارات التوافق Microsoft 365 مجموعات Teams والتعاون SharePoint المشترك

Microsoft 365 مجموعة كاملة من الأدوات للحفاظ على التوافق مع تعاون المستخدمين. راجع هذه الخيارات وكيفية تعيينها لاحتياجات عملك وحساسية بياناتك ونطاق الأشخاص الذين يحتاج المستخدمون إلى التعاون معهم.

يوفر الجدول التالي مرجعا سريعا لمراقبة التوافق المتوفرة في Microsoft 365. يتم توفير مزيد من المعلومات في الأقسام التالية.

|الفئة|الوصف|المرجع|
|:-------|:----------|:--------|
|استبقاء المعلومات|||
||الاحتفاظ بالبريد SharePoint المجموعات|[تعرف على المزيد حول سياسات الاستبقاء SharePoint OneDrive](../compliance/retention-policies-sharepoint.md)|
||الاحتفاظ بالدردشة والرسائل|[تعرف على المزيد حول سياسات الاستبقاء Microsoft Teams](../compliance/retention-policies-teams.md)|
|تصنيف المعلومات|||
||تصنيف المجموعات والفرق|[استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md)|
||تصنيف المحتوى الحساس تلقائيا|[تطبيق تسمية حساسية على المحتوى تلقائيا](../compliance/apply-sensitivity-label-automatically.md)|
||تشفير المحتوى الحساس|[تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](../compliance/encryption-sensitivity-labels.md)|
|حماية المعلومات|||
||منع فقدان المعلومات الحساسة|[التعرف على منع فقدان البيانات](../compliance/dlp-learn-about-dlp.md)|
||حماية المعلومات الحساسة في الدردشة.|[منع فقدان البيانات Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||تعريف المعلومات الحساسة لمنظمتك|[أنواع المعلومات الحساسة المخصصة](../compliance/sensitive-information-type-learn-about.md)|
|تقسيم المستخدم|||
||تقييد الاتصال بين شرائح المستخدمين|[عوائق المعلومات](../compliance/information-barriers.md)|
|الإقامة في البيانات|||
||تخزين البيانات في مواقع جغرافية محددة|[Microsoft 365 الجغرافيا المتعددة](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>استبقاء المعلومات

تتوفر سياسات الاستبقاء للاحتفاظ بالعناصر المستخدمة للتعاون في المجموعات والفرق أو حذفها، بما في ذلك الملفات والرسائل والبريد. يمكن تعيين السياسات للاحتفاظ بها وحذفها، أو للاحتفاظ بها فقط، أو حذفها فقط. تكون المعلومات التي يغطيها نهج الاستبقاء محمية في حالة انتهاء صلاحية المجموعة أو الفريق أو حذفها.

يشمل تكوين نهج استبقاء Microsoft 365 المجموعات علبة بريد المجموعة والملفات SharePoint موقع المجموعة وملفاتها.

- [تعرف على المزيد حول سياسات الاستبقاء SharePoint OneDrive](../compliance/retention-policies-sharepoint.md)

لنهج الاستبقاء Teams رسائل الدردشة والقناة. بينما يتم تخزين رسائل الدردشة والقناة في علب Exchange البريد، فإنها لا تتأثر Exchange الاستبقاء. يجب تعيين سياسات الاستبقاء لتطبيقها على Teams الدردشات Teams القنوات. 

يتم الاحتفاظ دردشات المستخدمين إلى أجل غير مسمى حتى لو تم حذف حساب مستخدم. إذا كنت لا تريد الاحتفاظ بهذه البيانات إلى أجل غير مسمى، فحدد استخدام نهج استبقاء لحذف دردشات المستخدمين بعد وقت محدد أو تضمين هذا الحذف في عملية حذف المستخدم.

- [تعرف على المزيد حول سياسات الاستبقاء Microsoft Teams](../compliance/retention-policies-teams.md)

- [سياسات الاستبقاء في Microsoft Teams](/microsoftteams/retention-policies)

يمكن تعيين نهج استبقاء واحد لتطبيقه على Teams الرسائل Teams القناة. 

موارد إضافية:

- [التعرف على سياسات الاستبقاء](../compliance/retention.md)

- [علامات الاستبقاء ونهج الاستبقاء](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) في Exchange

## <a name="information-classification"></a>تصنيف المعلومات

يمكنك استخدام تسميات الحساسية لتتحكم في وصول الضيف وخصوصية المجموعة والفريق والوصول بواسطة الأجهزة غير الإدارة للمجموعات والفرق. من خلال تطبيق التسمية، يتم تكوين هذه الإعدادات تلقائيا كما هو محدد بواسطة إعدادات التسمية.

- [استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md)

يمكنك تكوين Microsoft 365 لتطبيق تسميات الحساسية تلقائيا على الملفات ورسائل البريد الإلكتروني استنادا إلى المعايير التي تحددها، بما في ذلك الكشف عن أنواع المعلومات الحساسة أو النمط المطابق مع المصنفات القابلة للتدريب.

- [تطبيق تسمية حساسية على المحتوى تلقائيا](../compliance/apply-sensitivity-label-automatically.md)

يمكنك استخدام تسميات الحساسية لتشفير الملفات، مما يسمح فقط لأولئك الذين لهم أذونات بفك تشفيرها وقراءتها.

- [تقييد الوصول إلى المحتوى باستخدام تسميات الحساسية لتطبيق التشفير](../compliance/encryption-sensitivity-labels.md)

- [تكوين فريق مع عزل الأمان](./secure-teams-security-isolation.md)

موارد إضافية:

- [التعرّف على تسميات الحساسية](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>حماية المعلومات

يمكن أن تمنع سياسات DLP المشاركة العرضية للمعلومات الحساسة عبر SharePoint Exchange Teams. يمكنك إنشاء سياسات تحدد الإجراءات التي يجب اتخاذها (مثل حظر الوصول) استنادا إلى مجموعة من القواعد.

- [التعرف على منع فقدان البيانات](../compliance/dlp-learn-about-dlp.md)

يمكن أن تساعد Teams DLP في حماية المعلومات الحساسة في رسائل Teams عبر حذف الرسائل التي تحتوي على معلومات حساسة.

- [منع فقدان البيانات Microsoft Teams](../compliance/dlp-microsoft-teams.md)

إذا كانت لديك معلومات حساسة فريدة لمنظمتك، مثل أسماء رمز المشروع، يمكنك إنشاء أنواع المعلومات الحساسة الخاصة بك وتطبيقها على سياسات DLP لحماية المحتوى في المجموعات والفرق SharePoint.

- [أنواع المعلومات الحساسة المخصصة](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>تقسيم المستخدم

باستخدام حواجز المعلومات، يمكنك تقسيم البيانات والمستخدمين لتقييد التواصل والتعاون غير المرغوب فيهما بين المجموعات وتجنب تعارضات الاهتمامات في مؤسستك. تتيح لك حواجز المعلومات إنشاء سياسات للسماح أو منع التعاون في الملفات أو الدردشة أو الاتصال أو دعوات الاجتماعات بين مجموعات من الأشخاص في مؤسستك.

- [عوائق المعلومات](../compliance/information-barriers.md)

- [حواجز المعلومات في Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [استخدام حواجز المعلومات مع SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>الإقامة في البيانات

باستخدام Microsoft 365 الجغرافيا المتعددة، يمكنك توفير البيانات وتخزينها في المواقع الجغرافية التي اخترتها لتلبية متطلبات الإقامة الخاصة بالبيانات. في بيئة Multi-Geo، يتكون Microsoft 365 المستأجر الخاص بك من موقع مركزي (حيث تم توفير اشتراك Microsoft 365 في الأصل) وموقع أقمار صناعية واحد أو أكثر حيث يمكنك تخزين البيانات.

- [Microsoft 365 الجغرافيا المتعددة](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [التخطيط Microsoft 365 Multi-Geo](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[الأمان والتوافق Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[حماية المعلومات](../compliance/information-protection.md)
