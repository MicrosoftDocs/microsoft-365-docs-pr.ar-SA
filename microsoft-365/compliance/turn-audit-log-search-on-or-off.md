---
title: تشغيل التدقيق أو إيقاف تشغيله
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: كيفية تشغيل ميزة البحث في سجل التدقيق أو إيقاف تشغيلها في مدخل توافق Microsoft Purview لتمكين قدرة المسؤولين على البحث في سجل التدقيق أو تعطيلها.
ms.openlocfilehash: 3602a35169670b61a124cda40c9ab50b481571d8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078856"
---
# <a name="turn-auditing-on-or-off"></a>تشغيل التدقيق أو إيقاف تشغيله

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

سيتم تشغيل تسجيل التدقيق بشكل افتراضي للمؤسسات Microsoft 365 والمؤسسات Office 365. ومع ذلك، عند إعداد مؤسسة Microsoft 365 جديدة أو مؤسسة Office 365 جديدة، يجب التحقق من حالة التدقيق لمؤسستك. للحصول على الإرشادات، راجع [قسم التحقق من حالة التدقيق لمؤسستك](#verify-the-auditing-status-for-your-organization) في هذه المقالة. 

عند تشغيل التدقيق في مدخل توافق Microsoft Purview، يتم تسجيل نشاط المستخدم والمسؤول من مؤسستك في سجل التدقيق ويتم الاحتفاظ به لمدة 90 يوما، وما يصل إلى عام واحد وفقا للترخيص المعين للمستخدمين. ومع ذلك، قد يكون لدى مؤسستك أسباب لعدم الرغبة في تسجيل بيانات سجل التدقيق والاحتفاظ بها. في هذه الحالات، قد يقرر المسؤول العام إيقاف تشغيل التدقيق في Microsoft 365.

> [!IMPORTANT]
> إذا أوقفت تشغيل التدقيق في Microsoft 365، فلا يمكنك استخدام واجهة برمجة تطبيقات نشاط الإدارة Office 365 أو Microsoft Sentinel للوصول إلى بيانات التدقيق لمؤسستك. يعني إيقاف تشغيل التدقيق باتباع الخطوات الواردة في هذه المقالة أنه لن يتم إرجاع أي نتائج عند البحث في سجل التدقيق باستخدام مدخل التوافق أو عند تشغيل **search-UnifiedAuditLog** cmdlet في Exchange Online PowerShell. وهذا يعني أيضا أن سجلات التدقيق لن تكون متوفرة من خلال واجهة برمجة تطبيقات نشاط الإدارة Office 365 أو Microsoft Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>قبل تشغيل التدقيق أو إيقاف تشغيله

- يجب تعيين دور سجلات التدقيق في Exchange Online لتشغيل التدقيق أو إيقاف تشغيله في مؤسستك Microsoft 365. بشكل افتراضي، يتم تعيين هذا الدور إلى مجموعات دور إدارة التوافق وإدارة المؤسسة في صفحة **الأذونات** في مركز إدارة Exchange. المسؤولون العموميون في Microsoft 365 هم أعضاء في مجموعة دور إدارة المؤسسة في Exchange Online.

    > [!NOTE]
    > يجب تعيين أذونات للمستخدمين في Exchange Online لتشغيل التدقيق أو إيقاف تشغيله. إذا قمت بتعيين دور سجلات التدقيق للمستخدمين في صفحة **الأذونات** في مدخل التوافق، فلن يتمكنوا من تشغيل التدقيق أو إيقاف تشغيله. وذلك لأن cmdlet الأساسي هو أمر cmdlet Exchange Online PowerShell.

- للحصول على إرشادات مفصلة خطوة بخطوة حول البحث في سجل التدقيق، راجع [البحث في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md). لمزيد من المعلومات حول واجهة برمجة تطبيقات نشاط الإدارة Microsoft 365، راجع [بدء استخدام واجهات برمجة تطبيقات إدارة Microsoft 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="verify-the-auditing-status-for-your-organization"></a>التحقق من حالة التدقيق لمؤسستك

للتحقق من تشغيل التدقيق لمؤسستك، يمكنك تشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

تشير قيمة الخاصية `True`  _UnifiedAuditLogIngestionEnabled_ إلى أن التدقيق قيد التشغيل. تشير قيمة الإشارة `False` إلى أن التدقيق غير قيد التشغيل.

> [!NOTE]
> تأكد من تشغيل الأمر السابق في Exchange Online PowerShell. لا يمكنك استخدام Security & Compliance PowerShell لتشغيل هذا الأمر.

## <a name="turn-on-auditing"></a>تشغيل التدقيق

إذا لم يكن التدقيق قيد التشغيل لمؤسستك، يمكنك تشغيله في مدخل التوافق أو باستخدام Exchange Online PowerShell. قد يستغرق الأمر عدة ساعات بعد تشغيل التدقيق قبل أن تتمكن من إرجاع النتائج عند البحث في سجل التدقيق.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>استخدام مركز التوافق لتشغيل التدقيق

1. انتقل إلى <https://compliance.microsoft.com> وسجل الدخول.

2. في جزء التنقل الأيمن من مدخل التوافق، انقر فوق **"تدقيق**".

   إذا لم يكن التدقيق قيد التشغيل لمؤسستك، يتم عرض شعار يطالبك ببدء تسجيل نشاط المستخدم والمسؤول.

   ![شعار على صفحة التدقيق.](../media/AuditingBanner.png)

3. انقر فوق شعار **بدء تسجيل المستخدم ونشاط المسؤول** .

   قد يستغرق الأمر ما يصل إلى 60 دقيقة حتى يدخل التغيير حيز التنفيذ.

### <a name="use-powershell-to-turn-on-auditing"></a>استخدام PowerShell لتشغيل التدقيق

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. قم بتشغيل أمر PowerShell التالي لتشغيل التدقيق.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    يتم عرض رسالة تفيد بأن التغيير قد يستغرق ما يصل إلى 60 دقيقة حتى يدخل حيز التنفيذ.
  
## <a name="turn-off-auditing"></a>إيقاف تشغيل التدقيق

يجب عليك استخدام Exchange Online PowerShell لإيقاف تشغيل التدقيق.
  
1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. قم بتشغيل أمر PowerShell التالي لإيقاف تشغيل التدقيق.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. بعد فترة، تحقق من إيقاف تشغيل التدقيق (معطل). هناك طريقتان للقيام بذلك:

    - في Exchange Online PowerShell، قم بتشغيل الأمر التالي:

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      تشير قيمة الخاصية  `False`  _UnifiedAuditLogIngestionEnabled_ إلى إيقاف تشغيل التدقيق.

    - انتقل إلى صفحة **التدقيق** في مدخل التوافق.

      إذا لم يكن التدقيق قيد التشغيل لمؤسستك، يتم عرض شعار يطالبك ببدء تسجيل نشاط المستخدم والمسؤول.

## <a name="audit-records-when-auditing-status-is-changed"></a>تدقيق السجلات عند تغيير حالة التدقيق

يتم تدقيق التغييرات التي يتم إجراؤها على حالة التدقيق في مؤسستك. وهذا يعني أنه يتم تسجيل سجلات التدقيق عند تشغيل التدقيق أو إيقاف تشغيله. يمكنك البحث في سجل تدقيق المسؤول Exchange لسجلات التدقيق هذه.

للبحث في سجل تدقيق المسؤول Exchange لسجلات التدقيق التي يتم إنشاؤها عند تشغيل التدقيق أو إيقاف تشغيله، قم بتشغيل الأمر التالي في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Search-AdminAuditLog -Cmdlets Set-AdminAuditLogConfig -Parameters UnifiedAuditLogIngestionEnabled
```

تحتوي سجلات التدقيق لهذه الأحداث على معلومات حول وقت تغيير حالة التدقيق، والمسؤول الذي قام بتغييرها، وعنوان IP الخاص بالكمبيوتر الذي تم استخدامه لإجراء التغيير. تعرض لقطات الشاشة التالية سجلات التدقيق التي تتوافق مع تغيير حالة التدقيق في مؤسستك.

### <a name="audit-record-for-turning-on-auditing"></a>سجل التدقيق لتشغيل التدقيق

![سجل التدقيق لتشغيل التدقيق](../media/AuditStatusAuditingEnabled.png)

تشير قيمة `Confirm` خاصية *CmdletParameters* إلى أنه تم تشغيل تسجيل التدقيق الموحد في مركز التوافق أو عن طريق تشغيل **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true** cmdlet.

### <a name="audit-record-for-turning-off-auditing"></a>سجل التدقيق لإيقاف تشغيل التدقيق

![سجل التدقيق لإيقاف تشغيل التدقيق](../media/AuditStatusAuditingDisabled.png)

`Confirm` قيمة غير مضمنة في الخاصية *CmdletParameters*. يشير هذا إلى أنه تم إيقاف تشغيل تسجيل التدقيق الموحد عن طريق تشغيل الأمر **set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false** .

لمزيد من المعلومات حول البحث في سجل تدقيق المسؤول Exchange، راجع [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog).
