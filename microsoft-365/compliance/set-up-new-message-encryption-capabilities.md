---
title: إعداد تشفير الرسائل من Microsoft Purview
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/16/2022
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 7ff0c040-b25c-4378-9904-b1b50210d00e
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: تعرف على Microsoft Purview Message Encryption الذي يتيح اتصالا محميا بالبريد الإلكتروني مع أشخاص داخل مؤسستك وخارجها.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 48a5ca3bad7c0fb0d7120cb4e35bc5f24902a46e
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043329"
---
# <a name="set-up-message-encryption"></a>إعداد تشفير الرسائل

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يسمح Microsoft Purview Message Encryption للمؤسسات بمشاركة البريد الإلكتروني المحمي مع أي شخص على أي جهاز. يمكن للمستخدمين تبادل الرسائل المحمية مع مؤسسات Microsoft 365 أخرى، بالإضافة إلى جهات خارجية باستخدام Outlook.com وGmail وخدمات البريد الإلكتروني الأخرى.

اتبع الخطوات أدناه للتأكد من توفر تشفير رسائل "Microsoft Purview" في مؤسستك.

## <a name="verify-that-azure-rights-management-is-active"></a>التحقق من أن Azure Rights Management نشط

يستفيد تشفير الرسائل من Microsoft Purview من ميزات الحماية في [Azure Rights Management Services (Azure RMS)،](/azure/information-protection/what-is-information-protection) التقنية المستخدمة من قبل [Azure حماية البيانات](/azure/information-protection/what-is-azure-rms) لحماية رسائل البريد الإلكتروني والمستندات عبر عناصر التحكم في التشفير والوصول.

الشرط الأساسي الوحيد لاستخدام تشفير رسائل Microsoft Purview هو أنه يجب تنشيط [Azure Rights Management](/azure/information-protection/what-is-azure-rms) في مستأجر مؤسستك. إذا كان الأمر كذلك، Microsoft 365 تنشيط تشفير الرسالة تلقائيا ولا تحتاج إلى القيام بأي شيء.

يتم أيضا تنشيط Azure RMS تلقائيا لمعظم الخطط المؤهلة، لذلك ربما لا تضطر إلى القيام بأي شيء في هذا الصدد أيضا. راجع [تنشيط Rights Management Azure](/azure/information-protection/activate-service) لمزيد من المعلومات.

> [!IMPORTANT]
> إذا كنت تستخدم خدمة Rights Management Active Directory (AD RMS) مع Exchange Online، فستحتاج إلى [الترحيل إلى Azure حماية البيانات](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) قبل أن تتمكن من استخدام تشفير الرسالة. تشفير رسائل Microsoft Purview غير متوافق مع AD RMS.

لمزيد من المعلومات، اطلع على:

- [الأسئلة المتداولة حول تشفير الرسائل](ome-faq.yml) للتحقق مما إذا كانت خطة الاشتراك تتضمن Azure حماية البيانات (والتي تتضمن وظيفة Azure RMS).
- [حماية البيانات Azure](https://azure.microsoft.com/services/information-protection/) للحصول على معلومات حول شراء اشتراك مؤهل.

### <a name="manually-activating-azure-rights-management"></a>تنشيط Azure Rights Management يدويا

إذا قمت بتعطيل Azure RMS، أو إذا لم يتم تنشيطه تلقائيا لأي سبب من الأسباب، يمكنك تنشيطه يدويا في:

- **مركز مسؤولي Microsoft 365**: راجع [كيفية تنشيط azure Rights Management من مركز الإدارة](/azure/information-protection/activate-office365) للحصول على الإرشادات.
- **مدخل Azure**: راجع [كيفية تنشيط azure Rights Management من مدخل Azure](/azure/information-protection/activate-azure) للحصول على الإرشادات.

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>تكوين إدارة مفتاح مستأجر Azure حماية البيانات

هذه خطوة اختيارية. السماح ل Microsoft بإدارة المفتاح الجذر ل Azure حماية البيانات هو الإعداد الافتراضي وأفضل الممارسات الموصى بها لمعظم المؤسسات. إذا كانت هذه هي الحالة، فلن تحتاج إلى القيام بأي شيء.

هناك العديد من الأسباب، على سبيل المثال متطلبات التوافق، التي قد تتطلب منك إنشاء المفتاح الجذر الخاص بك وإدارته (المعروف أيضا باسم إحضار المفتاح الخاص بك (BYOK)). إذا كان الأمر كذلك، نوصي بإكمال الخطوات المطلوبة قبل إعداد تشفير الرسائل من Microsoft Purview. راجع [تخطيط وتنفيذ مفتاح مستأجر Azure حماية البيانات](/information-protection/plan-design/plan-implement-tenant-key) للحصول على المزيد.

## <a name="verify-microsoft-purview-message-encryption-configuration-in-exchange-online-powershell"></a>التحقق من تكوين تشفير الرسائل ل Microsoft Purview في Exchange Online PowerShell

يمكنك التحقق من تكوين مستأجر Microsoft 365 بشكل صحيح لاستخدام تشفير رسائل Microsoft Purview في [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell).

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام حساب بأذونات المسؤول العام في مستأجر Microsoft 365.

2. تشغيل Get-IRMConfiguration cmdlet.

     يجب أن تشاهد قيمة $True للمعلمة AzureRMSLicensingEnabled، والتي تشير إلى تكوين تشفير رسالة "Microsoft Purview" في المستأجر الخاص بك. إذا لم يكن كذلك، فاستخدم Set-IRMConfiguration لتعيين قيمة AzureRMSLicensingEnabled إلى $True لتمكين تشفير رسائل Microsoft Purview.

3. تشغيل Test-IRMConfiguration cmdlet باستخدام بناء الجملة التالي:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **مثال**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - بالنسبة للمرسل والمستلم، استخدم عنوان البريد الإلكتروني لأي مستخدم في مستأجر Microsoft 365.

     يجب أن تكون نتائجك مشابهة ل:

     ```console
     Results : Acquiring RMS Templates ...
                - PASS: RMS Templates acquired.  Templates available: Contoso  - Confidential View Only, Contoso  - Confidential, Do Not
            Forward.
            Verifying encryption ...
                - PASS: Encryption verified successfully.
            Verifying decryption ...
                - PASS: Decryption verified successfully.
            Verifying IRM is enabled ...
                - PASS: IRM verified successfully.

            OVERALL RESULT: PASS
     ```

   - سيحل اسم مؤسستك محل *Contoso*.

   - قد تختلف أسماء القوالب الافتراضية عن تلك المعروضة أعلاه. راجع [تكوين وإدارة القوالب ل Azure حماية البيانات](/azure/information-protection/configure-policy-templates) للحصول على المزيد.

4. إذا فشل الاختبار مع رسالة خطأ **فشلت في الحصول على قوالب RMS**، فنفذ الأوامر التالية وقم بتشغيل Test-IRMConfiguration cmdlet للتحقق من اجتيازه.

   ```powershell
   $RMSConfig = Get-AadrmConfiguration
   $LicenseUri = $RMSConfig.LicensingIntranetDistributionPointUrl
   Set-IRMConfiguration -LicensingLocation $LicenseUri
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```
5. قم بتشغيل Remove-PSSession cmdlet لقطع الاتصال بخدمة Rights Management.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-microsoft-purview-message-encryption"></a>الخطوات التالية: تحديد قواعد تدفق البريد لاستخدام تشفير رسائل Microsoft Purview

إذا كانت هناك قواعد تدفق بريد تم تكوينها مسبقا لتشفير البريد الإلكتروني في مؤسستك، فستحتاج إلى تحديث القواعد الموجودة لاستخدام تشفير رسائل Microsoft Purview. بالنسبة إلى عمليات النشر الجديدة، تحتاج إلى إنشاء قواعد تدفق بريد جديدة.

> [!IMPORTANT]
> إذا لم تقم بتحديث قواعد تدفق البريد الموجودة، فسيستمر المستخدمون في تلقي البريد المشفر الذي يستخدم تنسيق مرفق HTML السابق، بدلا من التجربة السلسة الجديدة.

تحدد قواعد تدفق البريد الشروط التي يجب تشفير رسائل البريد الإلكتروني فيها، بالإضافة إلى شروط إزالة هذا التشفير. عند تعيين إجراء لقاعدة، يتم تشفير أي رسائل تطابق شروط القاعدة عند إرسالها.

للحصول على خطوات حول إنشاء تشفير رسائل قواعد تدفق البريد، راجع [تعريف قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني في Office 365](define-mail-flow-rules-to-encrypt-email.md).

لتحديث القواعد الموجودة لاستخدام تشفير رسائل Microsoft Purview:

1. في مركز مسؤولي Microsoft 365، انتقل إلى **مراكز** >  الإدارة <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.
2. في مركز إدارة Exchange، انتقل إلى **"قواعد تدفق البريد" >**.
3. لكل قاعدة، قم **بما يلي**:
    - حدد **تعديل أمان الرسالة**.
    - حدد **تطبيق تشفير الرسائل Office 365 وحماية الحقوق**.
    - حدد قالب RMS من القائمة.
    - حدد **حفظ**.
    - حدد **موافق**.
