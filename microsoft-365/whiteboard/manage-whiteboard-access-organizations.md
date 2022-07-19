---
title: إدارة الوصول إلى Microsoft Whiteboard لمؤسستك
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: تعرف على كيفية إعداد Microsoft Whiteboard لمؤسستك في مركز مسؤولي Microsoft 365.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 1de0cd66a817a3db50b98bf6895be20184c974fc
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/30/2022
ms.locfileid: "66857473"
---
# <a name="manage-access-to-microsoft-whiteboard-for-your-organization"></a>إدارة الوصول إلى Microsoft Whiteboard لمؤسستك

>[!NOTE]
> تنطبق هذه المقالة على المؤسسات أو المؤسسات التعليمية التي تستخدم Whiteboard. بالنسبة إلى البيئات العالية لحكومة الولايات المتحدة، راجع [إدارة الوصول إلى Microsoft Whiteboard لبيئات GCC High](manage-whiteboard-access-gcc-high.md).

Microsoft Whiteboard عبارة عن لوحة تعاون مرئية حيث يتجمع الأشخاص والمحتوى والأفكار معا. اليوم، يعمل Whiteboard على Azure لعملاء المؤسسة والتعليم. لوح المعلومات قيد الانتقال ليتم تشغيله أعلى OneDrive for Business. سيجلب هذا الانتقال العديد من الإمكانات الجديدة ويسمح لك بإنشاء ألواح المعلومات ومشاركتها واكتشافها وإدارتها بسهولة كأي مستند من مستندات Office.

يتم تمكين Whiteboard تلقائيا لمستأجري Microsoft 365 القابلين للتطبيق. 

يتوافق Whiteboard مع المعايير العالمية بما في ذلك SOC 1 و SOC 2 و ISO 27001 و HIPAA وبنود الاتحاد الأوروبي النموذجية. 

إعدادات المسؤول التالية مطلوبة ل Whiteboard:

- يجب تمكين لوح المعلومات بشكل عام في مركز مسؤولي Microsoft 365.

- <code>Set-SPOTenant -IsWBFluidEnabled</code> يجب تمكين cmdlet باستخدام [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

>[!NOTE]
> يتم الآن طرح تخزين OneDrive for Business. عند الانتقال إلى مركز مسؤولي Microsoft 365، يتم تعطيل خيار الاشتراك في تخزين OneDrive for Business أو رفضه إذا تم بالفعل نقل المستأجر إلى OneDrive for Business.

يمكنك التحكم في الوصول إلى Whiteboard بالطرق التالية:

- تمكين Whiteboard للمستأجر بأكمله أو تعطيله باستخدام مركز مسؤولي Microsoft 365.

- إظهار لوح المعلومات أو إخفاؤه لمستخدمين محددين في الاجتماعات باستخدام نهج اجتماع Teams. سيظل مرئيا عبر الويب والعملاء الأصليين وتطبيق علامة تبويب Teams.

- طلب نهج الوصول المشروط للوصول إلى Whiteboard باستخدام مركز إدارة Azure Active Directory.

>[!NOTE]
> تعمل نهج اجتماعات Teams على إخفاء نقاط إدخال لوح المعلومات فقط؛ لا يمنع المستخدمون من استخدام Whiteboard. تمنع نهج الوصول المشروط أي وصول إلى Whiteboard، ولكنها لا تخفي نقاط الإدخال.

## <a name="enable-or-disable-whiteboard"></a>تمكين لوح المعلومات أو تعطيله

لتمكين Whiteboard للمستأجر أو تعطيله، قم بالخطوات التالية:

1. انتقل إلى مركز مسؤولي Microsoft 365.

2. في الصفحة الرئيسية لمركز الإدارة، في مربع البحث في الجزء العلوي الأيمن، اكتب *لوح المعلومات*.

3. في نتائج البحث، حدد **إعدادات لوح المعلومات**.

4. في لوحة Whiteboard، قم بتبديل **تشغيل Whiteboard أو إيقاف تشغيله لمؤسستك بأكملها** إلى **"تشغيل**".

5. حدد **حفظ**.

6. الاتصال ب [SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

7. تمكين Fluid باستخدام cmdlet التالي <code>Set-SPOTenant</code> :

   <pre><code class="lang-powershell">Set-SPOTenant -IsWBFluidEnabled $true</code></pre>
 
## <a name="show-or-hide-whiteboard"></a>إظهار لوح المعلومات أو إخفاؤه

لإظهار لوح المعلومات أو إخفاؤه في الاجتماعات، راجع [إعدادات نهج الاجتماع](/microsoftteams/meeting-policies-content-sharing). 

## <a name="prevent-access-to-whiteboard"></a>منع الوصول إلى Whiteboard

لمنع الوصول إلى Whiteboard لمستخدمين محددين، راجع [إنشاء نهج الوصول المشروط](/azure/active-directory/conditional-access/concept-conditional-access-policies).

## <a name="see-also"></a>راجع أيضًا

[إدارة البيانات ل Whiteboard](manage-data-organizations.md)

[إدارة المشاركة ل Whiteboard](manage-sharing-organizations.md)

[توزيع لوح المعلومات على Windows](deploy-on-windows-organizations.md)
