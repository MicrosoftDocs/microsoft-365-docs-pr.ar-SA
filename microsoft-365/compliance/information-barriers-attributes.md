---
title: سمات حواجز المعلومات
description: هذه المقالة هي مرجع ل سمات حساب مستخدم Azure Active Directory التي يمكنك استخدامها لتعريف شرائح حاجز المعلومات.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 33143e85bf17a707ade6dd0d6d0c66886fd85373
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566315"
---
# <a name="information-barriers-attributes"></a>سمات حواجز المعلومات

يمكن استخدام سمات معينة في Azure Active Directory لتقزز المستخدمين. بعد تحديد الشرائح، يمكن استخدام هذه الشرائح ك عوامل تصفية لنهج حاجز المعلومات. على سبيل المثال، يمكنك استخدام **"القسم** " لتعريف شرائح المستخدمين حسب القسم داخل مؤسستك (بافتراض أنه لا يوجد موظف واحد يعمل في قسمين في الوقت نفسه).

تصف هذه المقالة كيفية استخدام السمات مع حواجز المعلومات، كما أنها توفر قائمة السمات التي يمكن استخدامها. لمعرفة المزيد حول حواجز المعلومات، راجع الموارد التالية:

- [عوائق المعلومات](information-barriers.md)
- [تعريف سياسات لعوائق المعلومات في Microsoft Teams](information-barriers-policies.md)
- [تحرير (أو إزالة) سياسات حاجز المعلومات](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-information-barrier-policies"></a>كيفية استخدام السمات في سياسات حاجز المعلومات

يمكن استخدام السمات المدرجة في هذه المقالة لتعريف شرائح المستخدمين أو تحريرها. تعمل الشرائح المعرفة كمعلمات (تسمى *قيم UserGroupFilter* ) في [سياسات حاجز المعلومات](information-barriers-policies.md).

1. حدد السمة التي تريد استخدامها لتعريف الشرائح. (راجع [المقطع مرجع](#reference) في هذه المقالة.)

2. تأكد من أن حسابات المستخدمين بها قيم تم تعبئتها للنسبة (السمات) التي حددتها في الخطوة 1. عرض تفاصيل حساب المستخدم، وإذا لزم الأمر، قم بتحرير حسابات المستخدمين لتضمين قيم السمات. 

    - لتحرير حسابات متعددة (أو استخدام PowerShell لتحرير حساب واحد)، راجع تكوين خصائص حساب المستخدم باستخدام Office 365 [PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - لتحرير حساب واحد، راجع إضافة معلومات ملف تعريف مستخدم أو تحديثها [باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [تعريف الشرائح باستخدام PowerShell](information-barriers-policies.md#define-segments-using-powershell)، بطريقة مماثلة للأمثلة التالية:

    |**مثال**|**Cmdlet**|
    |:----------|:---------|
    | تعريف مقطع يسمى المقطع 1 باستخدام السمة "القسم" | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | تعريف مقطع يسمى SegmentA باستخدام السمة MemberOf (لنفترض أن هذه السمة تحتوي على أسماء مجموعات، مثل "BlueGroup") | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | تعريف مقطع يسمى Day Traderrs باستخدام ExtensionAttribute1 (لنفترض أن هذه السمة تحتوي على عناوين الوظائف، مثل "Day تريدr") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > عند تحديد الشرائح، استخدم السمة نفسها لكل الشرائح. على سبيل المثال، إذا قمت بتعريف بعض الشرائح باستخدام *القسم*، فحدد كل الشرائح التي تستخدم *القسم*. لا تحدد بعض الشرائح التي تستخدم *القسم* والبعض الآخر باستخدام *MemberOf*. تأكد من عدم تداخل الشرائح؛ يجب تعيين كل مستخدم إلى مقطع واحد بالضبط.

## <a name="reference"></a>المرجع

يسرد الجدول التالي السمات التي يمكنك استخدامها مع حواجز المعلومات.

|**اسم خاصية Azure Active Directory<br/>(اسم عرض LDAP)**|**Exchange الخاصية**|
|:---------------------------------------------------------------|:-------------------------|
| Co | Co |
| الشركة | الشركة |
| القسم | القسم |
| ExtensionAttribute1 | CustomAttribute1 |
| ExtensionAttribute2 | CustomAttribute2 |
| ExtensionAttribute3 | CustomAttribute3 |
| ExtensionAttribute4 | CustomAttribute4 |
| ExtensionAttribute5 | CustomAttribute5 |
| ExtensionAttribute6 | CustomAttribute6 |
| ExtensionAttribute7 | CustomAttribute7 |
| ExtensionAttribute8 | CustomAttribute8 |
| ExtensionAttribute9 | CustomAttribute9 |
| ExtensionAttribute10 | CustomAttribute10 |
| ExtensionAttribute11 | CustomAttribute11 |
| ExtensionAttribute12 | CustomAttribute12 |
| ExtensionAttribute13 | CustomAttribute13 |
| ExtensionAttribute14 | CustomAttribute14 |
| ExtensionAttribute15 | CustomAttribute15 |
| MSExchExtensionCustomAttribute1 | ExtensionCustomAttribute1 |
| MSExchExtensionCustomAttribute2 | ExtensionCustomAttribute2 |
| MSExchExtensionCustomAttribute3 | ExtensionCustomAttribute3 |
| MSExchExtensionCustomAttribute4 | ExtensionCustomAttribute4 |
| MSExchExtensionCustomAttribute5 | ExtensionCustomAttribute5 |
| MailNickname | الاسم المستعار |
| PhysicalDeliveryOfficeName | Office |
| الرمز البريدي | الرمز البريدي |
| ProxyAddresses | EmailAddresses |
| StreetAddress | StreetAddress |
| TargetAddress | ExternalEmailAddress |
| UsageLocation | UsageLocation |
| UserPrincipalName | UserPrincipalName |
| البريد | WindowsEmailAddress |
| الوصف | الوصف |
| MemberOf | MemberOfGroup |

## <a name="resources"></a>الموارد

- [تعريف سياسات لعوائق المعلومات في Microsoft Teams](information-barriers-policies.md)
- [استكشاف مشاكل المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [عوائق المعلومات](information-barriers.md)