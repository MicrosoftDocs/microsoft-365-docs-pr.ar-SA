---
title: إعداد قدرات تشفير الرسائل الجديدة
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/30/2019
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
description: تعرف على تشفير الرسائل من Office 365 الجديدة التي تمكن اتصال البريد الإلكتروني المحمي مع أشخاص من داخل مؤسستك وخارجها.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 006bef8a78a50e3cc47bfcfe7910621a3fa9ef85
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63567157"
---
# <a name="set-up-new-message-encryption-capabilities"></a>إعداد قدرات تشفير الرسائل الجديدة

تسمح تشفير الرسائل من Office 365 الجديدة (OME) ل المؤسسات بمشاركة البريد الإلكتروني المحمي مع أي شخص على أي جهاز. يمكن للمستخدمين تبادل الرسائل المحمية مع Microsoft 365 أخرى، بالإضافة إلى غير العملاء الذين يستخدمون Outlook.com وGmail وخدمات البريد الإلكتروني الأخرى.

اتبع الخطوات أدناه للتأكد من توفر قدرات OME الجديدة في مؤسستك.

## <a name="verify-that-azure-rights-management-is-active"></a>التحقق من أن Azure Rights Management نشطة

تستفيد قدرات OME الجديدة من ميزات الحماية في [Azure Rights Management Services (Azure RMS)،](/azure/information-protection/what-is-information-protection) التقنية المستخدمة بواسطة [Azure Information Protection](/azure/information-protection/what-is-azure-rms) لحماية رسائل البريد الإلكتروني والمستندات عبر التشفير والوصول إلى عناصر التحكم.

الشرط الأساسي الوحيد لاستخدام قدرات OME الجديدة هو أنه يجب تنشيط [Azure Rights Management](/azure/information-protection/what-is-azure-rms) في مستأجر مؤسستك. إذا كان كذلك، Microsoft 365 تنشيط قدرات OME الجديدة تلقائيا ولا تحتاج إلى القيام بأي شيء.

يتم أيضا تنشيط Azure RMS تلقائيا لمعظم الخطط المؤهلة، لذلك ليس عليك على الأرجح تنفيذ أي شيء في هذا الشأن أيضا. راجع [تنشيط Azure Rights Management](/azure/information-protection/activate-service) للحصول على مزيد من المعلومات.

> [!IMPORTANT]
> إذا كنت تستخدم خدمة إدارة حقوق Active Directory (AD RMS) مع Exchange Online، يجب الترحيل إلى [Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) قبل أن تتمكن من استخدام إمكانات OME الجديدة. لا يتوافق OME مع AD RMS.

لمزيد من المعلومات، اطلع على:

- [ما هي الاشتراكات التي أحتاج إليها لاستخدام قدرات OME الجديدة؟](ome-faq.yml#what-subscriptions-do-i-need-to-use-the-new-ome-capabilities-) للتحقق مما إذا كانت خطة الاشتراك تتضمن Azure Information Protection (الذي يتضمن وظائف Azure RMS).
- [Azure Information Protection](https://azure.microsoft.com/services/information-protection/) للحصول على معلومات حول شراء اشتراك مؤهل.

### <a name="manually-activating-azure-rights-management"></a>تنشيط Azure Rights Management يدويا

إذا قمت بتعطيل Azure RMS، أو إذا لم يتم تنشيطه تلقائيا لأي سبب من الأسباب، يمكنك تنشيطه يدويا في:

- **مركز مسؤولي Microsoft 365**: [راجع كيفية تنشيط Azure Rights Management من مركز الإدارة](/azure/information-protection/activate-office365) للحصول على الإرشادات.
- **مدخل Azure**: [راجع كيفية تنشيط Azure Rights Management من مدخل Azure](/azure/information-protection/activate-azure) للحصول على الإرشادات.

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>تكوين إدارة مفتاح مستأجر Azure Information Protection

هذه خطوة اختيارية. السماح ل Microsoft بإدارة المفتاح الجذر ل Azure Information Protection هو الإعداد الافتراضي وأفضل الممارسات المستحسنة لمعظم المؤسسات. إذا كان الأمر كذلك، فلا تحتاج إلى القيام بأي شيء.

هناك العديد من الأسباب، على سبيل المثال متطلبات التوافق، التي قد تتطلب منك إنشاء المفتاح الجذر الخاص بك وإدارته (المعروف أيضا باسم إحضار المفتاح الخاص بك (BYOK)). إذا كان الأمر كذلك، نوصيك لإكمال الخطوات المطلوبة قبل إعداد قدرات OME الجديدة. لمزيد من المعلومات، راجع تخطيط مفتاح مستأجر [Azure Information Protection](/information-protection/plan-design/plan-implement-tenant-key) وتطبيقه.

## <a name="verify-new-ome-configuration-in-exchange-online-powershell"></a>التحقق من تكوين OME الجديد في Exchange Online PowerShell

يمكنك التحقق من تكوين Microsoft 365 المستأجر بشكل صحيح لاستخدام قدرات OME الجديدة [في Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell).

1. [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام حساب مع أذونات المسؤول العام في Microsoft 365 المستأجر.

2. تشغيل Get-IRMConfiguration cmdlet.

     يجب أن ترى قيمة $True لمعلمة AzureRMSLicensingEnabled، التي تشير إلى أنه تم تكوين OME في المستأجر. إذا لم يكن الأمر كذلك، Set-IRMConfiguration لتعيين قيمة AzureRMSLicensingEnabled $True لتمكين OME.

3. تشغيل Test-IRMConfiguration cmdlet باستخدام بناء الجملة التالي:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **مثال**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - بالنسبة إلى المرسل والمستلم، استخدم عنوان البريد الإلكتروني لأي مستخدم في Microsoft 365 المستأجر.

     يجب أن تكون النتائج مماثلة ل:

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

   - قد تختلف أسماء القوالب الافتراضية عن تلك المعروضة أعلاه. لمزيد من المعلومات، راجع تكوين [القوالب وإدارتها ل Azure Information Protection](/azure/information-protection/configure-policy-templates) .

4. قم بتشغيل Remove-PSSession cmdlet لقطع اتصال خدمة إدارة الحقوق.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-new-ome-capabilities"></a>الخطوات التالية: تعريف قواعد تدفق البريد لاستخدام قدرات OME الجديدة

إذا كانت هناك قواعد تدفق بريد تم تكوينها مسبقا لتشفير البريد الإلكتروني في مؤسستك، ستحتاج إلى تحديث القواعد الموجودة لاستخدام قدرات OME الجديدة. بالنسبة إلى عمليات النشر الجديدة، ستحتاج إلى إنشاء قواعد تدفق بريد جديدة.

> [!IMPORTANT]
> إذا لم يتم تحديث قواعد تدفق البريد الموجودة، سيستمر المستخدمون في تلقي البريد المشفر الذي يستخدم تنسيق مرفق HTML السابق، بدلا من تجربة OME السلسة الجديدة.

تحدد قواعد تدفق البريد الشروط التي يجب أن يتم تشفير رسائل البريد الإلكتروني بها، بالإضافة إلى الشروط الخاصة بإزالة هذا التشفير. عند تعيين إجراء لقاعدة، يتم تشفير أي رسائل تتطابق مع شروط القاعدة عند إرسالها.

للحصول على خطوات حول إنشاء قواعد تدفق البريد ل OME، راجع تعريف قواعد تدفق البريد لتشفير رسائل البريد الإلكتروني [في](define-mail-flow-rules-to-encrypt-email.md) Office 365.

لتحديث القواعد الموجودة لاستخدام قدرات OME الجديدة:

1. في مركز مسؤولي Microsoft 365، انتقل إلى **مراكز الإدارة Exchange** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>
2. في مركز Exchange، انتقل إلى تدفق البريد > **القواعد**.
3. لكل قاعدة، في **القيام بما يلي**:
    - حدد **تعديل أمان الرسالة**.
    - حدد **تطبيق تشفير الرسائل من Office 365 وحماية الحقوق**.
    - حدد قالب RMS من القائمة.
    - حدد **حفظ**.
    - حدد **موافق**.
