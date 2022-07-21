---
title: تحديد أوامر PowerShell cmdlets المتوفرة للاستبقاء
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: normal
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: حدد أوامر PowerShell cmdlets للاحتفاظ ب Microsoft 365 التي تدعم التكوين على نطاق واسع أو التشغيل التلقائي أو قد تكون مطلوبة لسيناريوهات التكوين المتقدمة.
ms.openlocfilehash: bdbda5de65421fa73f45a278e2346777835062d9
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66941981"
---
# <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>PowerShell cmdlets لنهج الاستبقاء وتسميات الاستبقاء

>*[إرشادات ترخيص Microsoft 365 للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

استخدم الأقسام التالية لتحديد أوامر PowerShell cmdlets الرئيسية المتوفرة لنهج الاستبقاء وتسميات الاستبقاء التي قد تحتاجها للتكوين على نطاق واسع أو البرامج النصية التلقائية أو سيناريوهات التكوين المتقدمة. للحصول على القائمة الكاملة من أوامر cmdlets، راجع [قائمة الاحتفاظ بالنهج والتوافق](/powershell/module/exchange#policy-and-compliance-retention) من وثائق PowerShell.

قبل استخدام أوامر cmdlets هذه، يجب عليك أولا [الاتصال ب Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

في الأوصاف التالية، يمكن أن يشير نهج الاستبقاء إلى نهج استبقاء (بدون تسميات) أو نهج تسمية استبقاء. تحدد كل سياسة ما إذا كانت ثابتة أو موائمة مفتوحة ومواقع النهج الذي سيتم تطبيقه. ثم يتطلب النهج قاعدة واحدة لإكمال التكوين.

على سبيل المثال:
- يحتاج نهج الاستبقاء إلى قاعدة تحدد إعدادات الاستبقاء، مثل الاحتفاظ لمدة خمس سنوات ثم الحذف.

عند استخدام تسميات الاستبقاء، تحتوي هذه على إعدادات الاستبقاء وتحتاج نهجها إلى قواعد مختلفة:
- يحتاج نهج تسمية الاستبقاء الذي تنشره إلى قاعدة تحدد التسميات التي يجب عرضها في التطبيقات.
- يحتاج نهج تسمية الاستبقاء للتطبيق التلقائي إلى قاعدة تحدد التسمية لتطبيقها وشروط تطبيق التسمية.

## <a name="retention-cmdlets-for-most-locations"></a>أوامر cmdlets للاستبقاء لمعظم المواقع

استخدم أوامر cmdlets في الجدول التالي عندما تكون المواقع بريد **Exchange الإلكتروني** **أو مواقع SharePoint** **أو حسابات OneDrive** **أو مجموعات Microsoft 365** **أو Skype for Business أو** **مجلدات Exchange العامة** أو **رسائل دردشة Teams** أو **رسائل قناة Teams**.

لا تستخدم أوامر cmdlets هذه عندما تكون المواقع لرسائل القناة الخاصة في Teams أو رسائل مستخدم Yammer أو رسائل مجتمع Yammer. تحتوي هذه المواقع على أوامر cmdlets بديلة يتم تحديدها في [القسم التالي](#retention-cmdlets-specific-to-teams-private-channels-and-yammer).

|Cmdlet|الوصف|المواقع القابلة للتطبيق|
|:-----|:-----|:-----|:-----|
|[Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) <br /><br /> [Get-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) |عملية لمرة واحدة لإنشاء تخزين، أو عرض هذا التخزين لتسميات الاستبقاء |بريد Exchange الإلكتروني <br /><br />مواقع SharePoint <br /><br /> حسابات OneDrive <br /><br /> مجموعات Microsoft 365|
|[Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)<br /><br> [New-ComplianceTag](/powershell/module/exchange/new-compliancetag) <br /><br> [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag) <br /><br> [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag) |عرض تسميات الاستبقاء أو إنشائها أو حذفها أو تكوينها |بريد Exchange الإلكتروني <br /><br /> مواقع SharePoint <br /><br /> حسابات OneDrive<br /><br /> مجموعات Microsoft 365|
|[Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig) <br /><br /> [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/remove-retentioncompliancepolicy)  |عرض تكوين إعلام مراجعة الترتيب وإعدادات التذكير أو تكوينه |بريد Exchange الإلكتروني <br /><br /> مواقع SharePoint <br /><br /> حسابات OneDrive <br /><br /> مجموعات Microsoft 365|
|[Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) <br /><br /> [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy) <br /><br /> [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) |عرض النهج للاستبقاء أو إنشائها أو حذفها أو تكوينها |بريد Exchange الإلكتروني <br /><br /> مواقع SharePoint <br /><br /> حسابات OneDrive<br /><br /> مجموعات Microsoft 365 <br /><br /> Skype for Business <br /><br /> مجلدات Exchange العامة <br /><br /> رسائل دردشة Teams <br /><br /> رسائل قناة Teams |
|[Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) <br /><br /> [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)  | عرض إعدادات النهج الخاصة بتسميات الاستبقاء أو الاستبقاء أو إنشائها وتكوينها وحذفها |بريد Exchange الإلكتروني <br /><br /> مواقع SharePoint <br /><br /> حسابات OneDrive <br /><br /> مجموعات Microsoft 365 <br /><br /> Skype for Business <br /><br /> مجلدات Exchange العامة <br /><br /> رسائل دردشة Teams <br /><br /> رسائل قناة Teams |

## <a name="retention-cmdlets-specific-to-teams-private-channels-and-yammer"></a>أوامر cmdlets للاستبقاء الخاصة بقنوات Teams الخاصة و Yammer

استخدم أوامر cmdlet التالية عندما تكون المواقع **لرسائل قناة Teams الخاصة** أو **رسائل مستخدم Yammer** أو **رسائل مجتمع Yammer**.

عندما تكون المواقع مخصصة لرسائل دردشة Teams أو رسائل قناة Teams أو بريد Exchange الإلكتروني أو مواقع SharePoint أو حسابات OneDrive أو مجموعات Microsoft 365 أو Skype for Business أو Exchange، استخدم أوامر cmdlets المدرجة في [القسم السابق](#retention-cmdlets-for-most-locations).

|Cmdlet|الوصف|المواقع القابلة للتطبيق|
|:-----|:-----|:-----|:-----|
|[Get-AppRetentionCompliancePolicy](/powershell/module/exchange/get-appretentioncompliancepolicy) <br /><br> [New-AppRetentionCompliancePolicy](/powershell/module/exchange/new-appretentioncompliancepolicy) <br /><br> [Remove-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) <br /><br> [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) | عرض نهج الاستبقاء أو إنشائها أو حذفها أو تكوينها |رسائل القناة الخاصة في Teams <br /><br /> رسائل مستخدم Yammer <br /><br /> رسائل مجتمع Yammer|
|[Get-AppRetentionComplianceRule](/powershell/module/exchange/get-appretentioncompliancerule) <br /><br /> [New-AppRetentionComplianceRule](/powershell/module/exchange/new-appretentioncompliancerule) <br /><br /> [Remove-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) <br /><br /> [Set-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) | عرض إعدادات الاستبقاء أو إنشائها أو حذفها أو تكوينها لنهج الاستبقاء |رسائل القناة الخاصة في Teams <br /><br /> رسائل مستخدم Yammer <br /><br /> رسائل مجتمع Yammer|

## <a name="configuration-guidance"></a>إرشادات التكوين

استخدم صفحات التعليمات المقترنة بكل cmdlet للحصول على معلومات وأمثلة مفصلة.

للحصول على تعليمات إرشادية لإنشاء تسميات الاستبقاء ثم نشرها، راجع [إنشاء تسميات الاستبقاء ونشرها باستخدام PowerShell](bulk-create-publish-labels-using-powershell.md).