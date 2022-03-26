---
title: تحكم الوصول في Microsoft 365 Teams و SharePoint
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
description: تعرف على كيفية إدارة الوصول في Microsoft 365 والمجموعات Teams SharePoint.
ms.openlocfilehash: e01326093476f341c6c4c75448efbdf8c745779f
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/17/2021
ms.locfileid: "63569953"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>تحكم الوصول في Microsoft 365 Teams و SharePoint

هناك العديد من عناصر التحكم التي تمكنك من التحكم في كيفية وصول الأشخاص إلى الموارد في المجموعات والفرق SharePoint. راجع هذه الخيارات وكيفية تعيينها لاحتياجات عملك وحساسية بياناتك ونطاق الأشخاص الذين يحتاج المستخدمون إلى التعاون معهم.

يوفر الجدول التالي مرجعا سريعا لمراقبة الوصول المتوفرة في Microsoft 365. يتم توفير مزيد من المعلومات في الأقسام التالية.

|الفئة|الوصف|المرجع|
|:-------|:----------|:--------|
|العضوية|||
||اكتشاف الفرق الخاصة|[إدارة اكتشاف الفرق الخاصة في Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)|
||عضوية المجموعة الديناميكية استنادا إلى القواعد|[إنشاء مجموعة ديناميكية أو تحديثها في Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)|
||التحكم في الأشخاص الذين يمكنهم مشاركة الملفات والمجلدات والمواقع.|[إعداد طلبات الوصول وإدارتها](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|الوصول الشرطي|||
||المصادقة متعددة العوامل|[مصادقة Azure AD متعددة العوامل](/azure/active-directory/authentication/concept-mfa-howitworks)|
||التحكم في الوصول إلى الجهاز استنادا إلى حساسية المجموعة أو الفريق أو الموقع.|[استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md)|
||تقييد الوصول إلى الموقع للأجهزة غير التي يتم تدراجها.|[التحكم SharePoint الوصول من الأجهزة غير المراقبة](/sharepoint/control-access-from-unmanaged-devices)|
||التحكم في الوصول إلى الموقع استنادا إلى الموقع|[التحكم في الوصول SharePoint OneDrive البيانات استنادا إلى موقع الشبكة](/sharepoint/control-access-based-on-network-location)|
|وصول الضيف|||
||السماح بالمشاركة SharePoint أو حظرها من مجالات محددة.|[تقييد مشاركة SharePoint OneDrive حسب المجال](/sharepoint/restricted-domains-sharing)|
||السماح بعضوية الفريق أو المجموعة أو حظرها من مجالات محددة.|[السماح بدعوات لمستخدمي B2B أو حظرها من مؤسسات معينة](/azure/active-directory/b2b/allow-deny-list)|
||منع المشاركة المجهولة.|[إيقاف تشغيل ارتباطات أي شخص](./share-limit-accidental-exposure.md#turn-off-anyone-links)|
||التحكم في أذونات ارتباطات الوصول المجهولة.|[تعيين أذونات الارتباط لاارتباطات أي شخص](./best-practices-anonymous-sharing.md#set-link-permissions)|
||التحكم في انتهاء صلاحية ارتباطات المشاركة المجهولة.|[تعيين تاريخ انتهاء صلاحية لالروابط "أي شخص"](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)|
||التحكم في نوع ارتباط المشاركة الذي يظهر للمستخدمين بشكل افتراضي.|[تغيير نوع الارتباط الافتراضي لموقع](/sharepoint/change-default-sharing-link)|
||حصر المشاركة الخارجية ب أشخاص معينين.|[حصر المشاركة الخارجية لمجموعات أمان محددة](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||التحكم في وصول الضيف إلى مجموعة أو فريق أو موقع استنادا إلى حساسية المعلومات.|[استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md)|
||إيقاف تشغيل خيارات المشاركة.|[تقييد المشاركة في Microsoft 365](./microsoft-365-limit-sharing.md)|
|إدارة المستخدمين|||
||مراجعة عضوية الفريق والمجموعة بشكل منتظم.|[ما هي مراجعات الوصول إلى Azure AD؟](/azure/active-directory/governance/access-reviews-overview)|
||أتمتة إدارة الوصول إلى المجموعات والفرق.|[ما هي إدارة استحقاق Azure AD؟](/azure/active-directory/governance/entitlement-management-overview)|
||السماح للأشخاص بإنشاء قنوات خاصة أو حظرهم في Teams.|[إدارة دورة حياة القنوات الخاصة في Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)|

## <a name="membership"></a>العضوية

ويتحكم المالكون في عضوية الفرق والمجموعات. يمكن للأعضاء دعوة الآخرين، ولكن يتم إرسال الدعوات إلى المالكين للموافقة عليها. على الرغم من أن الفرق والمجموعات العامة يمكن اكتشافها من قبل أي شخص في المؤسسة، يمكنك التحكم في ما إذا كانت الفرق والمجموعات الخاصة قابلة لاكتشافها:

- [إدارة اكتشاف الفرق الخاصة في Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)

يمكنك إدارة عضوية مجموعة أو فريق ديناميكيا استنادا إلى بعض المعايير، مثل القسم. في هذه الحالة، يتعذر على الأعضاء والملاك دعوة أشخاص إلى الفريق. تستخدم المجموعات الديناميكية بيانات التعريف التي تحددها في Azure Active Directory للتحكم في من هو عضو في المجموعة. تأكد من أن بيانات التعريف التي تستخدمها مكتملة ويمكن أن تؤدي بيانات التعريف غير الصحيحة إلى ترك المستخدمين خارج المجموعات أو إضافة مستخدمين غير صحيحين.

- [إنشاء مجموعة ديناميكية أو تحديثها في Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

SharePoint المواقع إمكانية إضافة المالكين والأعضاء والزائرين بعيدا عن عضوية المجموعة أو الفريق. استنادا إلى متطلباتك، قد ترغب في تقييد الأشخاص الذين يمكنهم دعوة الأشخاص إلى الموقع. بالإضافة إلى ذلك، استنادا إلى حساسية المعلومات في موقع معين، قد ترغب في تقييد الأشخاص الذين يمكنهم مشاركة الملفات والمجلدات. يتم تكوين هذه القيود بواسطة الفريق أو المجموعة أو مالك الموقع:

- [إعداد طلبات الوصول وإدارتها](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>الوصول الشرطي

باستخدام Microsoft 365، يمكنك طلب مصادقة متعددة العوامل لكل من الأشخاص داخل مؤسستك وخارجها. هناك العديد من الخيارات الخاصة بالظروف عند مطالبة الأشخاص بعامل ثان للمصادقة. نوصي بشدة بنشر المصادقة متعددة العوامل لمنظمتك:

- [مصادقة Azure AD متعددة العوامل](/azure/active-directory/authentication/concept-mfa-howitworks)

إذا كانت لديك معلومات حساسة في بعض مجموعاتك وفرقك، يمكنك فرض سياسات إدارة الأجهزة استنادا إلى تسمية حساسية مجموعة أو فريق. يمكنك حظر الوصول بالكامل من الأجهزة غير المجهزة، أو السماح بالوصول المحدود إلى الويب فقط:

- [استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md)

في SharePoint، يمكنك تقييد الوصول إلى المواقع من مواقع شبكة محددة.

- [التحكم في الوصول SharePoint OneDrive البيانات استنادا إلى موقع الشبكة](/sharepoint/control-access-based-on-network-location)


موارد إضافية:

- [التخطيط لنشر الوصول الشرطي](/azure/active-directory/conditional-access/plan-conditional-access)

- [Microsoft Intune عامة](/mem/intune/fundamentals/what-is-intune)

- [التحكم SharePoint الوصول من الأجهزة غير المراقبة](/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>وصول الضيف

يمكنك تقييد الضيوف استنادا إلى مجال عنوان بريدهم الإلكتروني. SharePoint إعدادات تقييد مجال على مستوى المؤسسة ومجال خاص بالموقع. المجموعات Teams استخدام القوائم المسموح بها للمجال أو القوائم المحظورة في Azure AD. تأكد من تكوين الإعدادين لتجنب المشاركة غير المرغوب فيها وضمان تجربة مستخدم متناسقة:

- [تقييد مشاركة SharePoint OneDrive حسب المجال](/sharepoint/restricted-domains-sharing)

- [السماح بدعوات لمستخدمي B2B أو حظرها من مؤسسات معينة](/azure/active-directory/b2b/allow-deny-list)

Microsoft 365 مشاركة مجهولة للملفات والمجلدات باستخدام *ارتباطات* مشاركة أي شخص. *يمكن* إعادة توجيه ارتباطات أي شخص ويمكن لأي شخص له الارتباط الوصول إلى العنصر المشترك. استنادا إلى حساسية البيانات، يجب مراعاة كيفية استخدام ارتباطات أي شخص  - بما في ذلك إيقاف تشغيلها بالكامل أو تقييد أذونات الارتباط للقراءة فقط أو تعيين وقت انتهاء صلاحية لها:

- [إيقاف تشغيل ارتباطات أي شخص](./share-limit-accidental-exposure.md#turn-off-anyone-links)

- [تعيين أذونات الارتباط لاارتباطات أي شخص](./best-practices-anonymous-sharing.md#set-link-permissions)

- [تعيين تاريخ انتهاء صلاحية لالروابط "أي شخص"](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)

عند مشاركة الملفات أو المجلدات، يكون لدى المستخدمين عدة أنواع ارتباطات للاختيار من بينها. لتقليل مخاطر المشاركة غير المناسبة عن طريق الخطأ، يمكنك تغيير نوع الارتباط الافتراضي الذي يتم تقديمه للمستخدمين عند المشاركة. على سبيل المثال، قد يؤدي تغيير الإعداد الافتراضي من *ارتباطات أي* شخص - التي  تسمح بالوصول المجهول - إلى الأشخاص في ارتباطات مؤسستك إلى تقليل خطر المشاركة الخارجية غير المرغوب فيها للمعلومات الحساسة:

- [تغيير نوع الارتباط الافتراضي لموقع](/sharepoint/change-default-sharing-link)

إذا كانت مؤسستك لديها بيانات حساسة تحتاج إلى مشاركتها مع الضيوف، ولكنك قلق بشأن المشاركة غير المناسبة، يمكنك حصر المشاركة الخارجية للملفات والمجلدات بأعضاء مجموعات الأمان المحددة. بهذه الطريقة، يمكنك تقييد المشاركة خارجيا لمجموعة معينة من الأشخاص، أو طلب تدريب المستخدمين حول المشاركة الخارجية المناسبة قبل إضافتهم إلى مجموعة الأمان:

- [حصر المشاركة الخارجية لمجموعات أمان محددة](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

المجموعات Teams إعدادات على مستوى المؤسسة تسمح بالوصول إلى الضيف أو ترفضه. على الرغم من أنه يمكنك تقييد وصول الضيوف إلى فرق أو مجموعات معينة باستخدام [Microsoft PowerShell](per-group-guest-access.md)، نوصي بإجراء ذلك باستخدام تسمية الحساسية. باستخدام تسميات الحساسية، يمكنك تلقائيا السماح بالوصول إلى الضيف أو رفضه استنادا إلى التسمية المطبقة:

- [استخدام تسميات الحساسية لحماية المحتوى في Microsoft Teams ومجموعات Microsoft 365 ومواقع SharePoint ويب](../compliance/sensitivity-labels-teams-groups-sites.md)

في بيئة حيث تقوم بدعوة الضيوف بشكل متكرر إلى المجموعات والفرق، يمكنك إعداد مراجعات وصول الضيوف المجدولة بانتظام. يمكن مطالبة المالكين بمراجعة الضيوف في مجموعاتهم وفرقهم والموافقة على الوصول أو رفضه.

- [إعداد مراجعات وصول الضيوف](/microsoft-365/solutions/create-secure-guest-sharing-environment#set-up-guest-access-reviews)

Microsoft 365 العديد من الطرق المختلفة لمشاركة المعلومات. إذا كانت لديك معلومات حساسة وتريد تقييد طريقة مشاركتها، فراجع الخيارات المتعلقة بتقييد المشاركة:

- [تقييد المشاركة في Microsoft 365](./microsoft-365-limit-sharing.md)

موارد إضافية:

- [إعداد التعاون الآمن باستخدام Microsoft 365](./setup-secure-collaboration-with-teams.md)

- [أفضل الممارسات لمشاركة الملفات والمجلدات مع المستخدمين الذين لم يتم تأييدهم](./best-practices-anonymous-sharing.md)

- [الحد من التعرض العرضي للملفات عند المشاركة مع أشخاص من خارج مؤسستك](./share-limit-accidental-exposure.md)

- [إنشاء بيئة مشاركة ضيوف آمنة](./create-secure-guest-sharing-environment.md)

- [تمكين التعاون الخارجي بين الشركات وإدارة مَن يمكنه دعوة الضيوف](/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>إدارة المستخدمين

مع تطور المجموعات والفرق في مؤسستك، من الجيد مراجعة عضوية الفريق والمجموعات بشكل منتظم. قد يكون هذا مفيدا بشكل خاص للفرق والمجموعات ذات العضوية المتغيرة أو تلك التي تحتوي على معلومات حساسة أو تلك التي تتضمن ضيوفا. فكر في إعداد مراجعات الوصول لهذه الفرق والمجموعات:

- [ما هي مراجعات الوصول إلى Azure AD؟](/azure/active-directory/governance/access-reviews-overview)

تملك العديد من المؤسسات شراكة عمل مع مؤسسات أخرى أو موردين رئيسيين يتعاونون معهم بشكل معمق. قد يكون من الصعب إدارة المستخدمين والوصول إلى الموارد في هذه السيناريوهات. فكر في أتمتة بعض مهام إدارة المستخدمين وحتى نقل بعضها إلى المؤسسة الشريكة:

- [ما هي إدارة استحقاق Azure AD؟](/azure/active-directory/governance/entitlement-management-overview)

تسمح القنوات الخاصة Teams بالمحادثات المحددة النطاق ومشاركة الملفات بين مجموعة فرعية من أعضاء الفريق. استنادا إلى احتياجات عملك المحددة، قد ترغب في السماح بهذه الإمكانية أو حظرها.

- [القنوات الخاصة في Microsoft Teams](/MicrosoftTeams/private-channels)

- [إدارة دورة حياة القنوات الخاصة في Microsoft Teams](/MicrosoftTeams/private-channels-life-cycle-management)

موارد إضافية:

- [إدارة هوية Azure Active Directory](/azure/active-directory/governance)

## <a name="related-topics"></a>المواضيع ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md)

[الأمان والتوافق في Microsoft Teams](/microsoftteams/security-compliance-overview)

[إدارة إعدادات المشاركة في SharePoint](/sharepoint/turn-external-sharing-on-or-off)

[إنشاء شبكة خارجية وإدارتها في Yammer](/yammer/work-with-external-users/create-and-manage-an-external-network)

[تكوين Teams من ثلاثة مستويات من الحماية](./configure-teams-three-tiers-protection.md)