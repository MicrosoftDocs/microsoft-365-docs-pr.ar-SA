---
title: استخدام قفل الاحتفاظ لتقييد التغييرات على نهج الاستبقاء ونهج تسمية الاستبقاء
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
description: استخدم قفل الاحتفاظ مع نهج الاستبقاء ونهج تسمية الاستبقاء لمساعدتك على تلبية المتطلبات التنظيمية والحماية ضد المسؤولين المملوك.
ms.openlocfilehash: ac957475474e1d99dff541ac9a208ae5dc681217
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761716"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>استخدام قفل الاحتفاظ لتقييد التغييرات على نهج الاستبقاء ونهج تسمية الاستبقاء

>*[Microsoft 365 إرشادات الترخيص للامتثال & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!IMPORTANT]
> حاليا، لا تدعم [نطاقات النهج التكيفي](retention.md#adaptive-or-static-policy-scopes-for-retention) تأمين الاحتفاظ.

تأمين الاحتفاظ تأمين نهج الاستبقاء أو نهج تسمية الاستبقاء بحيث لا يمكن لأي شخص ، بما في ذلك مسؤول عام ، إيقاف تشغيل النهج أو حذف النهج أو جعله أقل تقييدا. قد تكون هناك حاجة إلى هذا التكوين للمتطلبات التنظيمية ويمكن أن يساعد في الحماية ضد المسؤولين المارقين.

عند تأمين نهج الاستبقاء:

- لا يمكن لأي شخص تعطيل النهج أو حذفه
- يمكن إضافة المواقع ولكن لا يمكن إزالتها
- يمكنك تمديد فترة الاستبقاء ولكن لا يمكنك تقليلها

عند تأمين نهج تسمية الاستبقاء:

- لا يمكن لأي شخص تعطيل النهج أو حذفه
- يمكن إضافة المواقع ولكن لا يمكن إزالتها
- يمكن إضافة التسميات ولكن لا يمكن إزالتها

باختصار، يمكن زيادة النهج المؤمن أو توسيعه، ولكن لا يمكن تقليله أو إيقاف تشغيله.

> [!IMPORTANT]
> قبل تأمين نهج الاستبقاء أو نهج تسمية الاستبقاء، من المهم أن تفهم التأثير وتأكد ما إذا كان مطلوبا لمؤسستك. على سبيل المثال، قد تكون هناك حاجة إليها لتلبية المتطلبات التنظيمية. لن يتمكن المسؤولون من تعطيل هذه النهج أو حذفها بعد تطبيق تأمين الاحتفاظ.

تكوين "تأمين الاحتفاظ" بعد إنشاء [نهج استبقاء](create-retention-policies.md)، أو نهج تسمية استبقاء [تنشره](create-apply-retention-labels.md) أو [تطبقه تلقائيا](apply-retention-labels-automatically.md).

> [!NOTE]
> لا يمنع تأمين نهج التسمية المسؤول من تقليل فترة الاستبقاء في تسمية مضمنة في النهج المؤمن. يمكن تلبية هذا المطلب، مع قيود أخرى، عند تكوين تسمية لوضع علامة على العناصر [كسجل تنظيمي](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>كيفية تأمين نهج الاستبقاء أو نهج تسمية الاستبقاء

يجب عليك استخدام PowerShell إذا كنت بحاجة إلى استخدام قفل الحفظ. نظرا لأنه لا يمكن للمسؤولين تعطيل نهج للاستبقاء أو حذفه بعد تطبيق هذا التأمين، فإن تمكين هذه الميزة غير متوفر في واجهة المستخدم للحماية من التكوين العرضي.

تدعم جميع نهج الاستبقاء ومع أي تكوين تأمين الاحتفاظ.

1. [الاتصال إلى Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. ابحث عن اسم النهج الذي تريد تأمينه عن طريق تشغيل [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). على سبيل المثال:
    
   ![قائمة نهج الاستبقاء في PowerShell.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. لوضع قفل الاحتفاظ على النهج الخاص بك، قم بتشغيل [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) cmdlet باسم النهج، وتعيين المعلمة *RestrictiveRetention* إلى true:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" -RestrictiveRetention $true
    ```
    
    على سبيل المثال:
    
    ![معلمة التقييد في PowerShell.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     عند المطالبة، اقرأ واقر بالقيود التي تأتي مع هذا التكوين عن طريق إدخال **Y**:
    
   ![المطالبة بتأكيد رغبتك في تأمين نهج استبقاء في PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

يتم الآن وضع قفل الاحتفاظ على النهج. للتأكيد، قم بتشغيل `Get-RetentionCompliancePolicy` مرة أخرى، ولكن حدد اسم النهج وعرض معلمات النهج:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

يجب أن ترى **أن RestrictiveRetention** معين إلى **True**. على سبيل المثال:

![نهج مؤمن مع جميع المعلمات المعروضة في PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>راجع أيضًا

[موارد لمساعدتك على تلبية المتطلبات التنظيمية لإدارة المعلومات وإدارة السجلات](retention-regulatory-requirements.md)