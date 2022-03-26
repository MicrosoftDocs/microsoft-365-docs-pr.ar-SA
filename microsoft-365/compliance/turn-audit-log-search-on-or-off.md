---
title: تشغيل التدقيق أو إيقاف تشغيله
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
ms.custom: seo-marvel-apr2020
description: كيفية تشغيل ميزة البحث في سجل التدقيق أو إيقاف تشغيلها في مركز التوافق في Microsoft 365 لتمكين قدرة المسؤولين على البحث في سجل التدقيق أو تعطيلها.
ms.openlocfilehash: e36fe410ed75522b0d531f2f9f7901b78f4974eb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63566573"
---
# <a name="turn-auditing-on-or-off"></a>تشغيل التدقيق أو إيقاف تشغيله

سيتم تشغيل تسجيل التدقيق بشكل افتراضي Microsoft 365 Office 365 المؤسسات. ومع ذلك، عند إعداد Microsoft 365 أو Office 365 جديدة، يجب التحقق من حالة التدقيق لمنظمتك. للحصول على الإرشادات، راجع [المقطع التحقق من حالة التدقيق لمنظمتك](#verify-the-auditing-status-for-your-organization) في هذه المقالة. 

عند تشغيل التدقيق في مركز التوافق في Microsoft 365، يتم تسجيل نشاط المسؤول والمستخدم من مؤسستك في سجل التدقيق والاحتفاظ به لمدة 90 يوما، وما يصل إلى عام واحد استنادا إلى الترخيص المعين للمستخدمين. ومع ذلك، قد يكون لدى مؤسستك أسباب عدم تسجيل بيانات سجل التدقيق والاحتفاظ بها. في هذه الحالات، قد يقرر المسؤول العام إيقاف تشغيل التدقيق في Microsoft 365.

> [!IMPORTANT]
> إذا قمت إيقاف تشغيل التدقيق في Microsoft 365، لا يمكنك استخدام Office 365 API لنشاط الإدارة أو Microsoft Sentinel للوصول إلى بيانات التدقيق لم المؤسسة. يعني إيقاف تشغيل التدقيق باتباع الخطوات في هذه المقالة أنه لن يتم إرجاع أي نتائج عند البحث في سجل التدقيق باستخدام مركز التوافق في Microsoft 365 أو عند تشغيل **الأمر cmdlet Search-UnifiedAuditLog** في Exchange Online PowerShell. وهذا يعني أيضا أن سجلات التدقيق لن تكون متوفرة من خلال Office 365 API لنشاط الإدارة أو Microsoft Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>قبل تشغيل التدقيق أو إيقاف تشغيله

- يجب أن يتم تعيين دور "سجلات التدقيق" Exchange Online تشغيل التدقيق أو إيقاف تشغيله في مؤسستك Microsoft 365. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور إدارة التوافق وإدارة المؤسسة على صفحة الأذونات في  Exchange مركز الإدارة. المسؤولون العامون Microsoft 365 أعضاء في مجموعة دور إدارة المؤسسة في Exchange Online.

    > [!NOTE]
    > يجب تعيين أذونات للمستخدمين في Exchange Online تشغيل التدقيق أو إيقاف تشغيله. إذا قمت بتعيين دور سجلات التدقيق للمستخدمين على صفحة الأذونات  في مركز التوافق في Microsoft 365، فلن يتمكنوا من تشغيل التدقيق أو إيقاف تشغيله. وذلك لأن أمر cmdlet الأساسي هو Exchange Online PowerShell cmdlet.

- للحصول على إرشادات مفصلة خطوة بخطوة حول البحث في سجل التدقيق، راجع [البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md). لمزيد من المعلومات حول Microsoft 365 API لنشاط الإدارة، راجع بدء [استخدام Microsoft 365 واجهات برمجة التطبيقات للإدارة](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="verify-the-auditing-status-for-your-organization"></a>التحقق من حالة التدقيق لمنظمتك

للتحقق من تشغيل التدقيق لمنظمتك، يمكنك تشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

تشير القيمة الخاصة `True` ب  _الخاصية UnifiedAuditLogIngestionEnabled_ إلى أنه تم تشغيل التدقيق. تشير قيمة `False` تشير إلى أنه لم يتم تشغيل التدقيق.

> [!NOTE]
> تأكد من تشغيل الأمر السابق في Exchange Online PowerShell. لا يمكنك استخدام الأمان & Compliance PowerShell لتشغيل هذا الأمر.

## <a name="turn-on-auditing"></a>تشغيل التدقيق

إذا لم يتم تشغيل التدقيق لمنظمتك، يمكنك تشغيلها في مركز التوافق في Microsoft 365 أو باستخدام Exchange Online PowerShell. قد يستغرق تشغيل التدقيق عدة ساعات قبل أن تتمكن من إرجاع النتائج عند البحث في سجل التدقيق.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>استخدام مركز التوافق ل تشغيل التدقيق

1. انتقل إلى <https://compliance.microsoft.com> ثم سجل الدخول.

2. في جزء التنقل الأيسر من مركز التوافق في Microsoft 365، انقر فوق **تدقيق**.

   إذا لم يتم تشغيل التدقيق لمنظمتك، يتم عرض شعار يطالبك ببدء تسجيل نشاط المستخدم والمسؤول.

   ![شعار على صفحة التدقيق.](../media/AuditingBanner.png)

3. انقر فوق **شعار بدء تسجيل نشاط المستخدم والمسؤول** .

   قد يستغرق الأمر ما يصل إلى 60 دقيقة حتى يتم تأثير التغيير.

### <a name="use-powershell-to-turn-on-auditing"></a>استخدام PowerShell تشغيل التدقيق

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. قم بتشغيل الأمر PowerShell التالي لتشغيل التدقيق.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    يتم عرض رسالة تقول إن التغيير قد يستغرق ما يصل إلى 60 دقيقة حتى يتم التنفيذ.
  
## <a name="turn-off-auditing"></a>إيقاف تشغيل التدقيق

يجب عليك استخدام Exchange Online PowerShell إيقاف تشغيل التدقيق.
  
1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. قم بتشغيل الأمر PowerShell التالي لتشغيل التدقيق.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. بعد مرور بعض الوقت، تحقق من إيقاف تشغيل التدقيق (معطل). هناك طريقتان للقيام بذلك:

    - في Exchange Online PowerShell، تشغيل الأمر التالي:

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      تشير قيمة _الخاصية UnifiedAuditLogIngestionEnabled_ إلى أنه تم إيقاف تشغيل التدقيق.`False`

    - انتقل إلى **صفحة التدقيق** في مركز التوافق في Microsoft 365.

      إذا لم يتم تشغيل التدقيق لمنظمتك، يتم عرض شعار يطالبك ببدء تسجيل نشاط المستخدم والمسؤول.

## <a name="audit-records-when-auditing-status-is-changed"></a>سجلات التدقيق عند تغيير حالة التدقيق

يتم تدقيق التغييرات التي يتم إدخالها على حالة التدقيق في مؤسستك. وهذا يعني أنه يتم تسجيل سجلات التدقيق عند تشغيل التدقيق أو إيقاف تشغيله. يمكنك البحث في Exchange تدقيق المسؤول عن سجلات التدقيق هذه.

للبحث في Exchange تدقيق المسؤول لسجلات التدقيق التي يتم إنشاؤها عند تشغيل التدقيق أو إيقاف تشغيله، قم بتشغيل الأمر التالي [في Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Search-AdminAuditLog -Cmdlets Set-AdminAuditLogConfig -Parameters UnifiedAuditLogIngestionEnabled
```

تحتوي سجلات التدقيق لهذه الأحداث على معلومات حول وقت تغيير حالة التدقيق، والمسؤول الذي قام بتغييرها، وعنوان IP للكمبيوتر الذي تم استخدامه لتغييره. تعرض لقطات الشاشة التالية سجلات التدقيق التي تتوافق مع تغيير حالة التدقيق في مؤسستك.

### <a name="audit-record-for-turning-on-auditing"></a>سجل التدقيق عند تشغيل التدقيق

![سجل التدقيق عند تشغيل التدقيق](../media/AuditStatusAuditingEnabled.png)

`Confirm` تشير القيمة في خاصية *CmdletParameters* إلى أنه تم تشغيل تسجيل التدقيق الموحد في مركز التوافق أو عن طريق تشغيل **الأمر Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true** cmdlet.

### <a name="audit-record-for-turning-off-auditing"></a>سجل التدقيق إيقاف تشغيل التدقيق

![سجل التدقيق إيقاف تشغيل التدقيق](../media/AuditStatusAuditingDisabled.png)

لا يتم تضمين `Confirm` قيمة في خاصية *CmdletParameters* . يشير ذلك إلى أنه تم إيقاف تشغيل تسجيل التدقيق الموحد عن طريق تشغيل الأمر **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled** $false.

لمزيد من المعلومات حول البحث في Exchange تدقيق المسؤول، راجع [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog).
