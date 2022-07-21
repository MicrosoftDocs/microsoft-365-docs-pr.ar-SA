---
title: إدارة الوصول إلى Microsoft Whiteboard لبيئات GCC High
ms.author: v-jdeweese
author: johnddeweese
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: تعرف على كيفية تمكين بيانات Whiteboard وتعطيلها وإدارتها.
ms.openlocfilehash: 2f79f53ce68dd9179b2b652f46a4245b9ed6ffdb
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66942417"
---
# <a name="manage-access-to-microsoft-whiteboard-for-gcc-high-environments"></a>إدارة الوصول إلى Microsoft Whiteboard لبيئات GCC High

>[!NOTE]
> تنطبق هذه الإرشادات على بيئات سحابة مجتمع الولايات المتحدة (GCC) العالية.

يتم تمكين Microsoft Whiteboard على OneDrive for Business بشكل افتراضي لمستأجري Microsoft 365 القابلين للتطبيق. يمكن تمكينه أو تعطيله على مستوى المستأجر. يجب عليك أيضا التأكد من تمكين **خدمات Microsoft Whiteboard** في **تطبيقات Enterprise** **لمركز** >  إدارة Azure Active Directory.

عناوين URL التالية مطلوبة:

- 'https://*.office365.us/'
- 'https://login.microsoftonline.us/'
- 'https://graph.microsoft.us/'
- 'https://graph.microsoftazure.us/'
- 'https://admin.onedrive.us'
- 'https://shell.cdn.office.net/'
- 'https://config.ecs.gov.teams.microsoft.us'
- 'https://tb.events.data.microsoft.com/'

يمكنك التحكم في الوصول إلى Whiteboard بالطرق التالية:

- تمكين Whiteboard للمستأجر بأكمله أو تعطيله باستخدام [الوحدة النمطية SharePoint Online PowerShell](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell).

- إظهار لوح المعلومات أو إخفاؤه لمستخدمين محددين في الاجتماعات باستخدام نهج اجتماع Teams. سيظل مرئيا عبر الويب والعملاء الأصليين وتطبيق علامة تبويب Teams.

- طلب نهج الوصول المشروط للوصول إلى Whiteboard باستخدام مركز إدارة Azure Active Directory.

>[!NOTE]
> لا يظهر لوح المعلومات على OneDrive for Business في مركز مسؤولي Microsoft 365. يخفي نهج اجتماع Teams نقاط إدخال لوح المعلومات فقط، ولا يمنع المستخدمين من استخدام Whiteboard. تمنع حالات الوصول المشروط الوصول إلى Whiteboard، ولكنها لا تخفي نقاط الإدخال.

## <a name="enable-or-disable-whiteboard"></a>تمكين لوح المعلومات أو تعطيله

لتمكين Whiteboard للمستأجر أو تعطيله، قم بالخطوات التالية: 

1. استخدم [الوحدة النمطية SharePoint Online PowerShell](/microsoft-365/enterprise/manage-sharepoint-online-with-microsoft-365-powershell) لتمكين جميع تجارب Fluid أو تعطيلها عبر مستأجر Microsoft 365.

2. الاتصال ب [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

3. تمكين Fluid باستخدام cmdlet التالي <code>Set-SPOTenant</code> :

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>

يجب أن يستغرق التغيير حوالي 60 دقيقة لتطبيقه عبر إيجارك. إذا لم تتمكن من رؤية هذا الخيار، فستحتاج إلى تحديث الوحدة النمطية.

>[!NOTE]
> بشكل افتراضي، يتم تمكين Whiteboard. إذا تم تعطيله في تطبيقات مؤسسة Azure Active Directory، فلن يعمل Whiteboard على OneDrive for Business.

## <a name="show-or-hide-whiteboard"></a>إظهار لوح المعلومات أو إخفاؤه

لإظهار لوح المعلومات أو إخفاؤه في الاجتماعات، راجع [إعدادات نهج الاجتماع](/microsoftteams/meeting-policies-content-sharing).

## <a name="see-also"></a>راجع أيضًا

[إدارة البيانات ل Whiteboard - GCC High](manage-data-gcc-high.md)

[إدارة المشاركة ل Whiteboard - GCC High](manage-sharing-gcc-high.md)

[إدارة العملاء ل Whiteboard - GCC High](manage-clients-gcc-high.md)




