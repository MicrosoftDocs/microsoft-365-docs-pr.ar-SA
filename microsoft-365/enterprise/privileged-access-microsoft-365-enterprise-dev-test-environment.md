---
title: إدارة الوصول المتميز Microsoft 365 لبيئة اختبار المؤسسة
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: استخدم دليل مختبر الاختبار هذا لتمكين إدارة الوصول المتميز Microsoft 365 لبيئة اختبار المؤسسة.
ms.openlocfilehash: 8520e4cf224164c62c10858e67359c0fa1a9fc85
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66008430"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>إدارة الوصول المتميز Microsoft 365 لبيئة اختبار المؤسسة

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

تصف هذه المقالة كيفية تكوين إدارة الوصول المتميز لزيادة الأمان في Microsoft 365 لبيئة اختبار المؤسسة.

يتضمن تكوين إدارة الوصول المتميز ثلاث مراحل:

- [المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [المرحلة 2: تكوين إدارة الوصول المتميز](#phase-2-configure-privileged-access-management)
- [المرحلة 3: التحقق من أن الموافقة مطلوبة للمهام المتميزة والمرتفعة](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>المرحلة 1: إنشاء Microsoft 365 لبيئة اختبار المؤسسة

إذا كنت ترغب في تكوين إدارة الوصول المتميز بطريقة خفيفة الوزن مع الحد الأدنى من المتطلبات، فاتبع الإرشادات في [التكوين الأساسي الخفيف](lightweight-base-configuration-microsoft-365-enterprise.md).
  
إذا كنت ترغب في تكوين إدارة الوصول المتميز في مؤسسة محاكاة، فاتبع الإرشادات [الواردة في مصادقة المرور](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> لا يتطلب اختبار إدارة الوصول المتميز بيئة اختبار المؤسسة المحاكاة، والتي تتضمن محاكاة إنترانت متصلة بالإنترنت ومزامنة الدليل لغاب خدمات مجال Active Directory. يتم توفيره هنا كخيار بحيث يمكنك اختبار إدارة الوصول المتميزة وتجربتها في بيئة تمثل مؤسسة نموذجية.

## <a name="phase-2-configure-privileged-access-management"></a>المرحلة 2: تكوين إدارة الوصول المتميز

في هذه المرحلة، قم بتكوين مجموعة موافقين وتمكين إدارة الوصول المتميزة Microsoft 365 لبيئة اختبار المؤسسة. للحصول على تفاصيل إضافية ونظرة عامة على إدارة الوصول المتميز، راجع [إدارة الوصول المتميز](../compliance/privileged-access-management-overview.md).

لإعداد الوصول المتميز واستخدامه في مؤسستك، نفذ الخطوات التالية.

### <a name="step-1-create-an-approvers-group"></a>[الخطوة 1: إنشاء مجموعة موافق](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

قبل البدء في استخدام الوصول المتميز، حدد من سيكون لديه سلطة الموافقة على الطلبات الواردة للوصول إلى المهام المرتفعة والمتميزة. يمكن لجميع المستخدمين الذين هم جزء من مجموعة الموافقين الموافقة على طلبات الوصول. لاستخدام الوصول المتميز، يجب إنشاء مجموعة أمان ممكنة للبريد في Microsoft 365. في بيئة الاختبار الخاصة بك، قم بتسمية مجموعة الأمان الجديدة "الموافقون على الوصول المتميز" وأضف "المستخدم 3" الذي تم إنشاؤه مسبقا في خطوات دليل مختبر الاختبار السابقة.

### <a name="step-2-enable-privileged-access"></a>[الخطوة 2: تمكين الوصول المتميز](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

يجب تشغيل الوصول المتميز بشكل صريح في Microsoft 365 مع مجموعة الموافق الافتراضية، ويجب أن يتضمن مجموعة من حسابات النظام التي تريد استبعادها من التحكم في الوصول إلى إدارة الوصول المتميز. تأكد من تمكين الوصول المتميز في مؤسستك قبل بدء المرحلة 3 من هذا الدليل.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>المرحلة 3: التحقق من أن الموافقة مطلوبة للمهام المتميزة والمرتفعة

في هذه المرحلة، تحقق من أن نهج الوصول المتميز يعمل وأن المستخدمين يحتاجون إلى الموافقة لتنفيذ المهام المتميزة والمحددة.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>اختبار القدرة على تنفيذ مهمة غير معرفة في نهج وصول متميز

أولا، حاول إنشاء قاعدة دفتر يومية جديدة في Exchange Online PowerShell. لم يتم تعريف مهمة [New-JournalRule](/powershell/module/exchange/new-journalrule) حاليا في نهج وصول متميز لمؤسستك.

1. على الكمبيوتر المحلي، [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام بيانات الاعتماد مع دور Exchange Role Management لبيئة الاختبار الخاصة بك.
2. إنشاء قاعدة دفتر يومية جديدة لمؤسستك عن طريق تشغيل الأمر التالي:

   ```PowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. تحقق من إنشاء قاعدة دفتر اليومية الجديدة بنجاح:

   ```PowerShell
   Get-JournalRule -Identity "JournalRule1"
   ```

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>إنشاء نهج وصول متميز جديد للمهمة New-JournalRule

> [!NOTE]
> إذا لم تكن قد أكملت بالفعل الخطوتي 1 و2 من المرحلة 2 من هذا الدليل، فتأكد من اتباع الخطوات لإنشاء مجموعة موافق باسم "الموافقون على الوصول المتميز" لتمكين الوصول المتميز في بيئة الاختبار الخاصة بك.

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد باستخدام دور Exchange Role Management لبيئة الاختبار الخاصة بك.
2. في مركز الإدارة، انتقل إلى **الإعدادات** >  الوصول المتميز للأمان **& الخصوصية** > .
3. حدد **إدارة نهج الوصول والطلبات**.
4. حدد **تكوين النهج**، ثم حدد **"إضافة نهج**".
5. من الحقول المنسدلة، حدد القيم التالية أو أدخلها:

    **نوع النهج**: **نطاق نهج** المهمة: **اسم Exchange Policy**: **نوع الموافقة على** قاعدة دفتر اليومية الجديد: **مجموعة الموافقة** اليدوية: الموافقون على الوصول المتميز  

6. حدد **"إنشاء**"، ثم حدد **"إغلاق**". قد يستغرق تكوين النهج وتمكينه بالكامل بضع دقائق. تأكد من السماح بوقت تمكين النهج بالكامل قبل اختبار متطلبات الموافقة في الخطوة التالية.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>اختبار متطلبات الموافقة للمهمة New-JournalRule المحددة في نهج الوصول المتميز

1. على الكمبيوتر المحلي، [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام بيانات الاعتماد مع دور Exchange Role Management لبيئة الاختبار الخاصة بك.

2. في Exchange Online PowerShell، قم بإنشاء قاعدة دفتر يومية جديدة لمؤسستك:

   ```PowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. عرض الخطأ "أذونات غير كافية" في Exchange Online PowerShell:

   ```PowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>طلب الوصول لإنشاء قاعدة دفتر يومية جديدة باستخدام المهمة New-JournalRule

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد باستخدام دور Exchange Role Management لبيئة الاختبار الخاصة بك.

2. في مركز الإدارة، انتقل إلى **الإعدادات** >  الوصول المتميز للأمان **& الخصوصية** > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد **طلب جديد**. من الحقول المنسدلة، حدد القيم المناسبة لمؤسستك:

    **نوع الطلب**: **نطاق طلب** المهمة: Exchange **مدة** قاعدة دفتر اليومية الجديدة **(الساعات):****تعليقان**: طلب إذن لإنشاء قاعدة دفتر يومية جديدة  

5. حدد **"حفظ"**، ثم حدد **"إغلاق**". سيتم إرسال طلبك إلى مجموعة الموافق عبر البريد الإلكتروني.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>الموافقة على طلب الوصول المتميز لإنشاء قاعدة دفتر يومية جديدة

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد للمستخدم 3 في بيئة الاختبار (عضو في مجموعة أمان "الموافقون على الوصول المتميز" في بيئة الاختبار).

2. في مركز الإدارة، انتقل إلى **الإعدادات** >  الوصول المتميز للأمان **& الخصوصية** > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد الطلب المعلق، ثم حدد **"موافق** " لمنح حق الوصول إلى حساب المستخدم لإنشاء قاعدة دفتر يومية جديدة. سيتلقى الحساب (المستخدم الطالب) تأكيدا بالبريد الإلكتروني بأنه تم منح الموافقة.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>اختبار إنشاء قاعدة دفتر يومية جديدة مع الموافقة على الوصول المتميز للمهمة New-JournalRule

1. على الكمبيوتر المحلي، [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) باستخدام بيانات الاعتماد مع دور Exchange Role Management لبيئة الاختبار الخاصة بك.

2. في Exchange Online PowerShell، قم بإنشاء قاعدة دفتر يومية جديدة لمؤسستك:

   ```PowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. تحقق من إنشاء قاعدة دفتر اليومية الجديدة بنجاح:

   ```PowerShell
   Get-JournalRule -Identity "JournalRule2"
   ```

## <a name="next-step"></a>الخطوة التالية

استكشف ميزات [وإمكانات إضافية لحماية المعلومات](m365-enterprise-test-lab-guides.md#information-protection) في بيئة الاختبار الخاصة بك.

## <a name="see-also"></a>راجع أيضًا

- [Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)
- [نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)
- [موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)
