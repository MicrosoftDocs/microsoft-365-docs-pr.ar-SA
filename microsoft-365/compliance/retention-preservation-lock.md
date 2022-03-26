---
title: استخدام "تأمين الاحتفاظ" لتقييد التغييرات لنهج الاستبقاء ونهج تسميات الاستبقاء
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
description: استخدم "تأمين الاحتفاظ" مع سياسات الاستبقاء ونهج تسميات الاستبقاء لمساعدتك على تلبية المتطلبات التنظيمية وللحماية من المسؤولين المخادعين.
ms.openlocfilehash: 64c2bb8f2718ce0da9d638b5b8b6bd4f89d33668
ms.sourcegitcommit: f6fff04431d632db02e7bdbf12f691091a30efad
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/18/2021
ms.locfileid: "63572972"
---
# <a name="use-preservation-lock-to-restrict-changes-to-retention-policies-and-retention-label-policies"></a>استخدام "تأمين الاحتفاظ" لتقييد التغييرات لنهج الاستبقاء ونهج تسميات الاستبقاء

>*[Microsoft 365 إرشادات الترخيص لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!IMPORTANT]
> حاليا، [لا](retention.md#adaptive-or-static-policy-scopes-for-retention) تدعم نطاقات النهج التكييفية تأمين الاحتفاظ.

تأمين الاحتفاظ تأمين تأمين نهج الاستبقاء أو نهج تسمية الاستبقاء بحيث لا يمكن لأحد، بما في ذلك المسؤول العام، إيقاف تشغيل النهج أو حذفه أو جعله أقل تقييدا. قد يكون هذا التكوين مطلوبا للمتطلبات التنظيمية ويمكن أن يساعد في الحماية من المسؤولين المسؤولين عن العمل.

عند تأمين نهج استبقاء:

- لا يمكن لأحد تعطيل النهج أو حذفه
- يمكن إضافة المواقع ولكن لا يمكن إزالتها
- يمكنك تمديد فترة الاستبقاء وليس إنقاصها

عند تأمين نهج تسمية استبقاء:

- لا يمكن لأحد تعطيل النهج أو حذفه
- يمكن إضافة المواقع ولكن لا يمكن إزالتها
- يمكن إضافة التسميات ولكن لا يمكن إزالتها

باختصار، يمكن زيادة نهج مؤمن أو توسيعه، ولكن لا يمكن تقليله أو إيقاف تشغيله.

> [!IMPORTANT]
> قبل تأمين نهج الاستبقاء أو نهج تسمية الاستبقاء، من المهم فهم التأثير وتأكيد ما إذا كان مطلوبا لم المؤسسة. على سبيل المثال، قد تكون هناك حاجة لتلبية المتطلبات التنظيمية. لن يتمكن المسؤولون من تعطيل هذه السياسات أو حذفها بعد تطبيق تأمين الاحتفاظ.

تكوين تأمين الاحتفاظ بعد إنشاء نهج استبقاء أو نهج [](create-retention-policies.md)تسمية استبقاء تقوم [بنشره](create-apply-retention-labels.md) أو [تطبيقه بشكل تلقائي](apply-retention-labels-automatically.md).

> [!NOTE]
> لا يمنع تأمين نهج تسمية المسؤول من تقليل فترة الاستبقاء في تسمية مضمنة في النهج المضمن. يمكن أن يتم تطبيق هذا المتطلب، مع قيود أخرى، عند تكوين تسمية لتسمية العناصر [كسجل تنظيمي](records-management.md#records).

## <a name="how-to-lock-a-retention-policy-or-retention-label-policy"></a>كيفية تأمين نهج استبقاء أو نهج تسمية استبقاء

يجب استخدام PowerShell إذا كنت بحاجة إلى استخدام "تأمين الاحتفاظ". نظرا لعدم تمكن المسؤولين من تعطيل نهج الاستبقاء أو حذفه بعد تطبيق هذا التأمين، فإن تمكين هذه الميزة غير متوفر في واجهة المستخدم للحماية من التكوين العرضي.

تدعم كل سياسات الاستبقاء وأي تكوين الاحتفاظ ب Lock.

1. [الاتصال إلى مركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. ابحث عن اسم النهج الذي تريد تأمينه عن طريق تشغيل [Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy). على سبيل المثال:
    
   ![قائمة سياسات الاستبقاء في PowerShell.](../media/retention-policy-preservation-lock-get-retentioncompliancepolicy.PNG)

3. لتعيين تأمين الاحتفاظ على نهجك، قم بتشغيل الأمر [Cmdlet Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) مع اسم النهج، ومعاينة *المعلمة RestrictiveRetention* إلى true:
    
    ```powershell
    Set-RetentionCompliancePolicy -Identity "<Name of Policy>" –RestrictiveRetention $true
    ```
    
    على سبيل المثال:
    
    ![المعلمة RestrictiveRetention في PowerShell.](../media/retention-policy-preservation-lock-restrictiveretention.PNG)
    
     عند مطالبتك بذلك، اقرأ القيود التي تأتي مع هذا التكوين وأقر بها بإدخال **Y**:
    
   ![المطالبة لتأكيد أنك تريد تأمين نهج استبقاء في PowerShell.](../media/retention-policy-preservation-lock-confirmation-prompt.PNG)

يتم الآن وضع تأمين الاحتفاظ على النهج. لتأكيد ذلك، قم بتشغيله `Get-RetentionCompliancePolicy` مرة أخرى، ولكن حدد اسم النهج واعرض معلمات النهج:

```powershell
Get-RetentionCompliancePolicy -Identity "<Name of Policy>" |Fl
```

يجب أن ترى **تم تعيين RestrictiveRetention** إلى **True**. على سبيل المثال:

![نهج مؤمن مع كل المعلمات المعروضة في PowerShell.](../media/retention-policy-preservation-lock-locked-policy.PNG)

## <a name="see-also"></a>راجع أيضًا

[الموارد لمساعدتك على تلبية المتطلبات التنظيمية لإدارة المعلومات وإدارة السجلات](retention-regulatory-requirements.md)