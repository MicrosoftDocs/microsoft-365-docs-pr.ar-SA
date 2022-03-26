---
title: اختيار المجال الذي يجب استخدامه عند إنشاء مجموعات Microsoft 365
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
description: تعرف على كيفية اختيار المجال الذي يجب استخدامه عند Microsoft 365 مجموعات عبر تكوين سياسات عناوين البريد الإلكتروني باستخدام PowerShell.
ms.openlocfilehash: 31b84304643190f343ae9ee74a947ecf6741f135
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/17/2021
ms.locfileid: "63572810"
---
# <a name="choose-the-domain-to-use-when-creating-microsoft-365-groups"></a>اختيار المجال الذي يجب استخدامه عند إنشاء مجموعات Microsoft 365

تستخدم بعض المؤسسات مجالات بريد إلكتروني منفصلة لتقزز أجزاء مختلفة من أعمالهم. يمكنك تحديد المجال الذي يجب استخدامه عند إنشاء المستخدمين Microsoft 365 المجموعات.
  
إذا كانت مؤسستك بحاجة إلى المستخدمين لإنشاء مجموعاتهم في مجالات أخرى غير مجال عملك المقبول الافتراضي، يمكنك السماح بذلك من خلال تكوين سياسات عناوين البريد الإلكتروني (EAPs) باستخدام PowerShell.

قبل أن تتمكن من تشغيل PowerShell cmdlets، قم بتنزيل وحدة نمطية من الممكن أن تسمح لك بالتحدث إلى مؤسستك وتثبيتها. اطلع على [الاتصال Exchange Online PowerShell البعيد](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="example-scenarios"></a>أمثلة على سيناريوهات

لنقل أن مجال شركتك الرئيسي Contoso.com. ولكن المجال المقبول الافتراضي لمنظمتك service.contoso.com. وهذا يعني أنه سيتم إنشاء المجموعات في service.contoso.com (على سبيل المثال، jimsteam@service.contoso.com).
  
لنقل أن لديك أيضا مجالات فرعية تم تكوينها في مؤسستك. تريد إنشاء المجموعات في هذه المجالات أيضا:
  
- students.contoso.com للطلاب
    
- faculty.contoso.com لأعضاء هيئة التدريس
    
يشرح السيناريوهين التاليين كيفية تنفيذ ذلك.

> [!NOTE]
> عندما يكون لديك عدد كبير من EAPs، يتم تقييمها في ترتيب الأولوية. تعني القيمة 1 الأولوية العليا. بمجرد تطابق EAP، لن يتم تقييم أي EAP آخر والعناوين التي يتم ختمها على المجموعة هي حسب EAP المطابق. > إذا لم تتطابق EAPs مع المعايير المحددة، يتم توفير المجموعة في المجال الافتراضي المقبول في المؤسسة. راجع [إدارة المجالات](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) المقبولة في Exchange Online للحصول على تفاصيل حول كيفية إضافة مجال مقبول.
  
### <a name="scenario-1"></a>السيناريو 1

يوضح المثال التالي كيفية توفير كل Microsoft 365 في مؤسستك في groups.contoso.com المجال.
  
```
New-EmailAddressPolicy -Name Groups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@groups.contoso.com" -Priority 1
```

### <a name="scenario-2"></a>السيناريو 2

لنقل أنك تريد التحكم في المجالات الفرعية التي Microsoft 365 المجموعات فيها. أنت تريد:
  
- المجموعات التي أنشأها الطلاب (المستخدمون الذين تم تعيين **القسم** لديهم إلى **الطلاب**) في students.groups.contoso.com المجال. استخدم هذا الأمر:
    
  ```
  New-EmailAddressPolicy -Name StudentsGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Students'} -Priority 1
  ```

- تحتوي المجموعات التي أنشأها أعضاء هيئة التدريس (المستخدمون الذين تم تعيين قسمهم على عنوان البريد الإلكتروني أو الكلية على faculty.contoso.com **)**) في faculty.groups.contoso.com المجال. استخدم هذا الأمر:
    
  ```
  New-EmailAddressPolicy -Name FacultyGroups -IncludeUnifiedGroupRecipients -EnabledEmailAddressTemplates "SMTP:@faculty.groups.contoso.com","smtp:@groups.contoso.com" -ManagedByFilter {Department -eq 'Faculty' -or EmailAddresses -like "*faculty.contoso.com*"} -Priority 2
  ```

- يتم إنشاء المجموعات التي أنشأها أي شخص آخر في groups.contoso.com المجال. استخدم هذا الأمر:
    
  ```
  New-EmailAddressPolicy -Name OtherGroups -IncludeUnifiedGroupRecipients -EnabledPrimarySMTPAddressTemplate "SMTP:@groups.contoso.com" -Priority 3
  ```

## <a name="change-email-address-policies"></a>تغيير سياسات عناوين البريد الإلكتروني

لتغيير قوالب عناوين البريد الإلكتروني أو الأولوية الخاصة ب EAP موجود، استخدم Set-EmailAddressPolicy cmdlet.
  
```
Set-EmailAddressPolicy -Name StudentsGroups -EnabledEmailAddressTemplates "SMTP:@students.groups.contoso.com","smtp:@groups.contoso.com", "smtp:@students.contoso.com" ManagedByFilter {Department -eq 'Students'} -Priority 2

```

لا يؤثر تغيير EAP على المجموعات التي تم توفيرها بالفعل.
  
## <a name="delete-email-address-policies"></a>حذف سياسات عناوين البريد الإلكتروني

لحذف EAP، استخدم Remove-EmailAddressPolicy cmdlet.
  
```
Remove-EmailAddressPolicy -Identity StudentsGroups
```

لا يؤثر تغيير EAP على المجموعات التي تم توفيرها بالفعل.
  
## <a name="hybrid-requirements"></a>المتطلبات المختلطة

إذا تم تكوين مؤسستك في سيناريو مختلط، فتحقق من تكوين مجموعات Microsoft 365 مع مجموعات [Exchange](/exchange/hybrid-deployment/set-up-microsoft-365-groups) المحلية للتأكد من أن مؤسستك تلبي متطلبات إنشاء Microsoft 365 المجموعات. 
  
## <a name="additional-info-about-using-email-address-policies-groups"></a>معلومات إضافية حول استخدام مجموعات سياسات عناوين البريد الإلكتروني:

هناك بعض الأمور الأخرى التي يجب معرفتها:
  
- تعتمد سرعة إنشاء المجموعات على عدد EAPs التي تم تكوينها في مؤسستك.
    
- يمكن للمسؤولين والمستخدمين أيضا تعديل المجالات عند إنشاء مجموعات.
    
- يتم تحديد مجموعة المستخدمين باستخدام الاستعلامات القياسية (خصائص المستخدم) المتوفرة بالفعل. اطلع على [الخصائص القابلة للتصفية لمعلمة -RecipientFilter](/powershell/exchange/recipientfilter-properties) للخصائص المعتمدة القابلة للتصفية. 
    
- إذا لم تقوم بتكوين أي EAPs للمجموعات، يتم تحديد المجال المقبول الافتراضي لإنشاء المجموعة.
    
- إذا قمت بإزالة مجال تم قبوله، يجب تحديث EAPs أولا، وإلا، سيتأثر توفير المجموعة.
    
- يمكن تكوين الحد الأقصى لعدد 100 من سياسات عناوين البريد الإلكتروني في المؤسسة.
    
## <a name="related-content"></a>المحتوى ذي الصلة

[توصيات تخطيط حوكمة التعاون](collaboration-governance-overview.md#collaboration-governance-planning-recommendations) (مقالة)

[إنشاء خطة حوكمة التعاون](collaboration-governance-first.md) (مقالة)

[إنشاء Microsoft 365 في مركز الإدارة](../admin/create-groups/create-groups.md) (مقالة)