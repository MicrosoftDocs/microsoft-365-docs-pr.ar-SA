---
title: سمات حواجز المعلومات
description: هذه المقالة هي مرجع لسمات حساب مستخدم Azure Active Directory التي يمكنك استخدامها لتعريف مقاطع حواجز المعلومات.
keywords: حواجز Microsoft 365، Microsoft Purview، التوافق، المعلومات
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
ms.openlocfilehash: e09331fb819d2b00764cd6dacd1687ade8ee116c
ms.sourcegitcommit: 99494a5530ad64802f341573ad42796134190296
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/13/2022
ms.locfileid: "65396256"
---
# <a name="information-barriers-attributes"></a>سمات حواجز المعلومات

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يمكن استخدام بعض السمات في Azure Active Directory لتقسيم المستخدمين في حواجز المعلومات (IB). بمجرد تعريف المقاطع، يمكن استخدام هذه المقاطع كعوامل تصفية لنهج IB. على سبيل المثال، قد تستخدم **"القسم"** لتعريف شرائح المستخدمين حسب القسم داخل مؤسستك (بافتراض عدم عمل موظف واحد لقسمين في الوقت نفسه).

تصف هذه المقالة كيفية استخدام السمات مع حواجز المعلومات، وتوفر قائمة بالسمات التي يمكن استخدامها. لمعرفة المزيد حول حواجز المعلومات، راجع الموارد التالية:

- [عوائق المعلومات](information-barriers.md)
- [تحديد نهج لحواجز المعلومات في Microsoft Teams](information-barriers-policies.md)
- [تحرير (أو إزالة) نهج IB](information-barriers-edit-segments-policies.md)

## <a name="how-to-use-attributes-in-ib-policies"></a>كيفية استخدام السمات في نهج IB

يمكن استخدام السمات المذكورة في هذه المقالة لتعريف مقاطع من المستخدمين أو تحريرها. تعمل المقاطع المحددة كمعلمات (تسمى قيم *UserGroupFilter* ) في [نهج IB](information-barriers-policies.md).

1. حدد السمة التي تريد استخدامها لتعريف المقاطع. (راجع المقطع ["مرجع](#reference) " في هذه المقالة.)

2. تأكد من أن حسابات المستخدمين تحتوي على قيم معبأة للسمة (السمات) التي حددتها في الخطوة 1. عرض تفاصيل حساب المستخدم، وإذا لزم الأمر، فحرر حسابات المستخدمين لتضمين قيم السمات. 

    - لتحرير حسابات متعددة (أو استخدام PowerShell لتحرير حساب واحد)، راجع [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

    - لتحرير حساب واحد، راجع [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

3. [تعريف المقاطع باستخدام PowerShell](information-barriers-policies.md#define-segments-using-powershell)، على غرار الأمثلة التالية:

    |**المثال**|**Cmdlet**|
    |:----------|:---------|
    | تعريف مقطع يسمى Segment1 باستخدام سمة القسم | `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "Department -eq 'Department1'"` |
    | تعريف مقطع يسمى SegmentA باستخدام السمة MemberOf (افترض أن هذه السمة تحتوي على أسماء مجموعات، مثل "BlueGroup") | `New-OrganizationSegment -Name "SegmentA" -UserGroupFilter "MemberOf -eq 'BlueGroup'"` |
    | تعريف مقطع يسمى DayNamrs باستخدام ExtensionAttribute1 (افترض أن هذه السمة تحتوي على عناوين وظيفية، مثل "Day_r") | `New-OrganizationSegment -Name "DayTraders" -UserGroupFilter "ExtensionAttribute1 -eq 'DayTrader'"` |

    > [!TIP]
    > عند تعريف المقاطع، استخدم السمة نفسها لكافة المقاطع. على سبيل المثال، إذا قمت بتعريف بعض المقاطع باستخدام *القسم*، فحدد جميع المقاطع باستخدام *القسم*. لا تحدد بعض الشرائح باستخدام *القسم* والبعض الآخر باستخدام *MemberOf*. تأكد من عدم تداخل المقاطع؛ يجب تعيين كل مستخدم إلى مقطع واحد بالضبط.

## <a name="reference"></a>المرجع

يسرد الجدول التالي السمات التي يمكنك استخدامها مع حواجز المعلومات.

|**اسم<br/> خاصية Azure Active Directory (اسم عرض LDAP)**|**اسم خاصية Exchange**|
|:---------------------------------------------------------------|:-------------------------|
| شريك في العمل | شريك في العمل |
| الشركه | الشركه |
| اداره | اداره |
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
| Proxyaddresses | عناوين البريد الإلكتروني |
| عنوان الشارع | عنوان الشارع |
| Targetaddress | ExternalEmailAddress |
| تحديد الاستخدام | تحديد الاستخدام |
| UserPrincipalName | UserPrincipalName |
| البريد | WindowsEmailAddress |
| الوصف | الوصف |
| عضو من | MemberOfGroup |

## <a name="resources"></a>الموارد

- [تحديد نهج لحواجز المعلومات في Microsoft Teams](information-barriers-policies.md)
- [استكشاف أخطاء حواجز المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
- [عوائق المعلومات](information-barriers.md)
