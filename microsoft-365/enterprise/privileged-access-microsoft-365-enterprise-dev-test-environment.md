---
title: إدارة الوصول المتميزة Microsoft 365 بيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: استخدم دليل Test Lab هذا لتمكين إدارة الوصول المتميزة Microsoft 365 بيئة اختبار المؤسسة.
ms.openlocfilehash: 424b7c09a89b20d134654293a1e9c9abd69d6ff2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63567086"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>إدارة الوصول المتميزة Microsoft 365 بيئة اختبار المؤسسة

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

تصف هذه المقالة كيفية تكوين إدارة الوصول المتميزة لزيادة الأمان Microsoft 365 بيئة اختبار المؤسسة.

يتضمن تكوين إدارة الوصول المتميز ثلاث مراحل:

- [المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة الثانية: تكوين إدارة الوصول المتميزة](#phase-2-configure-privileged-access-management)
- [المرحلة 3: التحقق من أن الموافقة مطلوبة للمهام المتميزة والمرتفعة](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 بيئة اختبار المؤسسة

إذا كنت تريد تكوين إدارة الوصول المتميزة بطريقة خفيفة بالحد الأدنى من المتطلبات، فاتبع الإرشادات الموجودة في [تكوين الأساس الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت تريد تكوين إدارة وصول متميزة في مؤسسة محاكاة، فاتبع الإرشادات الواردة في [المصادقة المرورية](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>لا يتطلب اختبار إدارة الوصول المتميز بيئة اختبار المؤسسة المحاكاة، التي تتضمن إنترانت محاكاة متصلة بالإنترنت ومزامنة الدليل الغابات خدمات مجال Active Directory. يتم توفيرها هنا كخيار بحيث يمكنك اختبار إدارة الوصول المتميزة واختبارها في بيئة تمثل مؤسسة نموذجية.

## <a name="phase-2-configure-privileged-access-management"></a>المرحلة الثانية: تكوين إدارة الوصول المتميزة

في هذه المرحلة، قم بتكوين مجموعة الموافقين وتمكين إدارة الوصول المتميزة Microsoft 365 بيئة اختبار المؤسسة. للحصول على مزيد من التفاصيل و نظرة عامة حول إدارة الوصول المتميزة، راجع [إدارة الوصول المتميز](../compliance/privileged-access-management-overview.md).

لإعداد الوصول المميز واستخدامه في مؤسستك، قم بتنفيذ الخطوات التالية.

#### <a name="step-1-create-an-approvers-group"></a>[الخطوة 1: إنشاء مجموعة الموافق](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

قبل البدء في استخدام الوصول المتميز، حدد من سيكون لديه مرجع الموافقة للطلبات الواردة للوصول إلى المهام المتميزة والمرتفعة. يمكن لجميع المستخدمين الذين هم جزء من مجموعة الموافقين الموافقة على طلبات الوصول. لاستخدام الوصول المميز، يجب إنشاء مجموعة أمان تمكين البريد في Microsoft 365. في بيئة الاختبار، قم بتكران اسم مجموعة الأمان الجديدة "الموافقون المميزون على الوصول" وأضف "المستخدم 3" الذي تم إنشاؤه مسبقا في خطوات دليل اختبار سابقة.

#### <a name="step-2-enable-privileged-access"></a>[الخطوة 2: تمكين الوصول المميز](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

يجب تشغيل الوصول المميز بشكل صريح في Microsoft 365 مع مجموعة الموافقين الافتراضية، ويجب أن يتضمن مجموعة من حسابات النظام التي تريد استبعادها من عنصر تحكم الوصول المتميز لإدارة الوصول. تأكد من تمكين الوصول المميز في مؤسستك قبل بدء المرحلة 3 من هذا الدليل.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>المرحلة 3: التحقق من أن الموافقة مطلوبة للمهام المتميزة والمرتفعة

في هذه المرحلة، تحقق من أن نهج الوصول المميز يعمل وأن المستخدمين بحاجة إلى الموافقة لتنفيذ مهام محددة عالية ومتميزة.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>اختبار القدرة على تنفيذ مهمة غير معرفة في نهج وصول مميز

أولا، اتصل Exchange Management PowerShell باستخدام بيانات اعتماد مستخدم تم تكوينها باستخدام دور Exchange إدارة الدور في بيئة الاختبار الخاصة بك ومحاولة إنشاء قاعدة دفتر يومية جديدة. لا [يتم تعريف المهمة New-JournalRule](/powershell/module/exchange/new-journalrule) حاليا في نهج وصول مميز لمنظمتك.

1. على الكمبيوتر المحلي، افتح وحدة PowerShell Exchange Online Remote PowerShell في **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** باستخدام بيانات الاعتماد مع دور Exchange إدارة الدور لبيئة الاختبار.
2. في Exchange إدارة PowerShell، أنشئ قاعدة دفتر يومية جديدة لمنظمتك:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. عرض أن قاعدة دفتر اليومية الجديدة قد تم إنشاؤها بنجاح في Exchange Management PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>إنشاء نهج وصول مميز جديد New-JournalRule المهمة

>[!NOTE]
>إذا لم تكن قد أكملت خطوتي 1 و2 من المرحلة 2 من هذا الدليل، فتأكد من اتباع الخطوات لإنشاء مجموعة الموافقين المسماة "الموافقون على الوصول المتميز" لتمكين الوصول المتميز في بيئة الاختبار.

1. سجل [الدخول إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد Exchange دور إدارة الدور لبيئة الاختبار.
2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **الأمان & الوصول إلى** **PrivacyPrivileged** > .
3. حدد **إدارة سياسات الوصول وطلباته**.
4. حدد **تكوين النهج**، ثم حدد **إضافة نهج**.
5. من الحقول المنسدل، حدد القيم التالية أو أدخلها:

    **نوع النهج****: نطاق نهج** المهمة: Exchange **اسم** "السياسة": نوع الموافقة على قاعدة دفتر اليومية **الجديد: مجموعة** الموافقة **اليدوية:** الموافقون المميزون على الوصول  

6. حدد **إنشاء**، ثم حدد **إغلاق**. قد يستغرق تكوين النهج وتمكينه بشكل كامل بضع دقائق. تأكد من السماح بتمكين النهج بشكل كامل قبل اختبار متطلبات الموافقة في الخطوة التالية.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>اختبار متطلبات الموافقة للمهمة New-JournalRule المحددة في نهج وصول مميز

1. على الكمبيوتر المحلي، افتح وحدة PowerShell Exchange Online Remote PowerShell في **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** باستخدام بيانات الاعتماد مع دور Exchange إدارة الدور لبيئة الاختبار.

2. في Exchange إدارة PowerShell، أنشئ قاعدة دفتر يومية جديدة لمنظمتك:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. عرض الخطأ "أذونات غير كافية" في Exchange Management PowerShell:

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>طلب الوصول لإنشاء قاعدة دفتر يومية جديدة باستخدام New-JournalRule

1. سجل [الدخول إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد Exchange دور إدارة الدور لبيئة الاختبار.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **الأمان & الوصول إلى** **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد **طلب جديد**. من الحقول المنسدل، حدد القيم المناسبة لمنظمتك:

    **نوع الطلب****: نطاق طلب** المهمة: Exchange مطلب **: مدة** قاعدة دفتر اليومية الجديدة **(الساعات)**: تعليقان **: طلب** إذن لإنشاء قاعدة دفتر يومية جديدة  

5. حدد **حفظ**، ثم حدد **إغلاق**. سيتم إرسال طلبك إلى مجموعة الموافق عبر البريد الإلكتروني.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>الموافقة على طلب الوصول المتميز لإنشاء قاعدة دفتر يومية جديدة

1. سجل دخولك [إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات اعتماد المستخدم 3 في بيئة الاختبار (عضو في مجموعة الأمان "الموافقون على الوصول المميزون" في بيئة الاختبار).

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **الأمان & الوصول إلى** **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد الطلب المعلق، ثم حدد **موافقة** لمنح حق الوصول إلى حساب المستخدم لإنشاء قاعدة دفتر يومية جديدة. سيتلقى الحساب (المستخدم الذي يطلب الطلب) تأكيدا عبر البريد الإلكتروني بأنه تم منح الموافقة.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>اختبار إنشاء قاعدة دفتر يومية جديدة ذات وصول مميز تمت الموافقة عليه New-JournalRule المهمة

1. على الكمبيوتر المحلي، افتح وحدة PowerShell Exchange Online Remote PowerShell في **Microsoft Corporation** >  **Microsoft Exchange Online Remote PowerShell Module** باستخدام بيانات الاعتماد مع دور Exchange إدارة الدور لبيئة الاختبار.

2. في Exchange إدارة PowerShell، أنشئ قاعدة دفتر يومية جديدة لمنظمتك:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. عرض أن قاعدة دفتر اليومية الجديدة قد تم إنشاؤها بنجاح في Exchange Management PowerShell.

## <a name="next-step"></a>الخطوة التالية

استكشف [ميزات حماية](m365-enterprise-test-lab-guides.md#information-protection) المعلومات الإضافية وإمكانياتها في بيئة الاختبار.

## <a name="see-also"></a>راجع أيضًا

- [Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)
- [Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)
- [Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)
