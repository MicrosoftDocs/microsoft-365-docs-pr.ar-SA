---
title: اختر المجال الذي تريد استخدامه عند إنشاء مجموعات Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 7cf5655d-e523-4bc3-a93b-3ccebf44a01a
recommendations: false
description: تعرف على كيفية اختيار المجال الذي تريد استخدامه عند إنشاء مجموعات Microsoft 365 عن طريق تكوين نهج عناوين البريد الإلكتروني باستخدام PowerShell.
ms.openlocfilehash: c6eb1bbccf8745c88941f40d6fefeed29aec5620
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012527"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>اختر المجال الذي تريد استخدامه عند إنشاء مجموعات Microsoft 365

تستخدم بعض المؤسسات مجالات بريد إلكتروني منفصلة لتقسيم أجزاء مختلفة من أعمالها. يمكنك تحديد المجال الذي يجب استخدامه عند قيام المستخدمين بإنشاء مجموعات Microsoft 365.
  
إذا كانت مؤسستك بحاجة إلى أن يقوم المستخدمون بإنشاء مجموعاتهم في مجالات أخرى غير المجال المقبول الافتراضي لأعمالك، يمكنك السماح بذلك عن طريق تكوين نهج عناوين البريد الإلكتروني (EAPs) باستخدام PowerShell.

قبل أن تتمكن من تشغيل PowerShell cmdlets، قم بتنزيل وتثبيت وحدة نمطية تسمح لك بالتحدث إلى مؤسستك. تحقق [من الاتصال Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>أمثلة على السيناريوهات

لنفترض أن مجال عملك الرئيسي Contoso.com. ولكن المجال المقبول الافتراضي لمؤسستك service.contoso.com. وهذا يعني أنه سيتم إنشاء المجموعات في service.contoso.com (على سبيل المثال، jimsteam@service.contoso.com).
  
لنفترض أن لديك أيضا مجالات فرعية تم تكوينها في مؤسستك. تريد إنشاء المجموعات في هذه المجالات أيضا:
  
- students.contoso.com للطلاب
    
- faculty.contoso.com لأعضاء هيئة التدريس
    
يوضح السيناريوهان التاليان كيفية إنجاز هذا.

> [!NOTE]
> عندما يكون لديك EAPs، يتم تقييمها بترتيب الأولوية. القيمة 1 تعني الأولوية القصوى. بمجرد تطابق EAP، لا يتم تقييم أي EAP آخر وتكون العناوين التي يتم طابعها على المجموعة وفقا ل EAP المطابق. > إذا لم تتطابق EAPs مع المعايير المحددة، يتم توفير المجموعة في المجال المقبول الافتراضي للمؤسسة. اطلع على [إدارة المجالات المقبولة في Exchange Online](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) للحصول على تفاصيل حول كيفية إضافة مجال مقبول.
  
### <a name="scenario-1"></a>السيناريو 1

يوضح لك المثال التالي كيفية توفير كافة مجموعات Microsoft 365 في مؤسستك في مجال groups.contoso.com.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>السيناريو 2

لنفترض أنك تريد التحكم في المجالات الفرعية Microsoft 365 المجموعات التي تم إنشاؤها فيها. أنت تريد:
  
- المجموعات التي أنشأها الطلاب (المستخدمون الذين تم تعيين **القسم** **لهم)** في مجال students.groups.contoso.com. استخدم هذا الأمر:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- المجموعات التي أنشأها أعضاء هيئة التدريس (المستخدمون الذين تم تعيين **القسم** لهم إلى **هيئة التدريس أو عنوان البريد الإلكتروني يحتوي على faculty.contoso.com)**) في مجال faculty.groups.contoso.com. استخدم هذا الأمر:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- يتم إنشاء المجموعات التي أنشأها أي شخص آخر في المجال groups.contoso.com. استخدم هذا الأمر:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>تغيير نهج عنوان البريد الإلكتروني

لتغيير قوالب الأولوية أو عنوان البريد الإلكتروني ل EAP موجود، استخدم Set-EmailAddressPolicy cmdlet.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

لا يؤثر تغيير EAP على المجموعات التي تم توفيرها بالفعل.
  
## <a name="delete-email-address-policies"></a>حذف نهج عنوان البريد الإلكتروني

لحذف EAP، استخدم Remove-EmailAddressPolicy cmdlet.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

لا يؤثر تغيير EAP على المجموعات التي تم توفيرها بالفعل.
  
## <a name="hybrid-requirements"></a>المتطلبات المختلطة

إذا تم تكوين مؤسستك في سيناريو مختلط، فتحقق من [تكوين مجموعات Microsoft 365 مع Exchange مختلطة محلية](/exchange/hybrid-deployment/set-up-microsoft-365-groups) للتأكد من أن مؤسستك تلبي متطلبات إنشاء مجموعات Microsoft 365. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>معلومات إضافية حول استخدام مجموعات نهج عناوين البريد الإلكتروني:

هناك بعض الأشياء الإضافية التي يجب معرفتها:
  
- تعتمد مدى سرعة إنشاء المجموعات على عدد EAPs التي تم تكوينها في مؤسستك.
    
- يمكن للمسؤولين والمستخدمين أيضا تعديل المجالات عند إنشاء المجموعات.
    
- يتم تحديد مجموعة المستخدمين باستخدام الاستعلامات القياسية (خصائص المستخدم) المتوفرة بالفعل. تحقق من [الخصائص القابلة للتصفية للمعلمة -RecipientFilter](/powershell/exchange/recipientfilter-properties) للخصائص المعتمدة القابلة للتصفية. 
    
- إذا لم تقم بتكوين أي EAPs للمجموعات، فسيتم تحديد المجال المقبول الافتراضي لإنشاء المجموعة.
    
- إذا قمت بإزالة مجال مقبول، يجب عليك تحديث EAPs أولا، وإلا، فسيتأثر توفير المجموعة.
    
- يمكن تكوين حد أقصى يبلغ 100 نهج لعناوين البريد الإلكتروني لمؤسسة ما.
    
## <a name="related-content"></a>المحتويات ذات الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (مقالة)

[إنشاء خطة حوكمة التعاون (](collaboration-governance-first.md) مقالة)

[إنشاء مجموعة Microsoft 365 في مركز الإدارة](../admin/create-groups/create-groups.md) (مقالة)