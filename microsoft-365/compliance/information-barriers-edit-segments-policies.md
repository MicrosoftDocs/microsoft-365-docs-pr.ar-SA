---
title: إدارة نهج حواجز المعلومات
description: تعرف على كيفية تحرير النهج أو إزالتها لحواجز المعلومات.
keywords: Microsoft 365 وMicrosoft Purview والامتثال وحواجز المعلومات
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
ms.openlocfilehash: a84b8e712de53b0abae81a05bbe1b2bef3237beb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635294"
---
# <a name="manage-information-barriers-policies"></a>إدارة نهج حواجز المعلومات

بعد [تحديد نهج حواجز المعلومات (IB)،](information-barriers-policies.md) قد تحتاج إلى إجراء تغييرات على هذه النهج أو على مقاطع المستخدمين، كجزء من [استكشاف الأخطاء وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) أو كصيانة منتظمة.

## <a name="what-do-you-want-to-do"></a>ماذا تريد أن تفعل؟

|**العمل**|**الوصف**|
|:---------|:--------------|
| [تحرير سمات حساب المستخدم](#edit-user-account-attributes) | تعبئة السمات في Azure Active Directory التي يمكن استخدامها لتعريف المقاطع. <br> تحرير سمات حساب المستخدم عندما لا يتم تضمين المستخدمين في المقاطع التي يجب أن تكون، أو لتغيير المقاطع التي يوجد فيها المستخدمون، أو لتعريف المقاطع باستخدام سمات مختلفة. |
| [تحرير مقطع](#edit-a-segment) | تحرير المقاطع عندما تريد تغيير كيفية تعريف مقطع. <br> على سبيل المثال، قد تكون قد قمت بتعريف مقاطع في الأصل باستخدام *القسم* وتريد الآن استخدام سمة أخرى، مثل *MemberOf*. |
| [تحرير نهج](#edit-a-policy) | تحرير نهج حواجز المعلومات عندما تريد تغيير كيفية عمل النهج.<br> على سبيل المثال، بدلا من حظر الاتصالات بين مقطعين، قد تقرر أنك تريد السماح بحدوث الاتصالات بين مقاطع معينة فقط. |
| [تعيين نهج إلى الحالة غير النشطة](#set-a-policy-to-inactive-status) |قم بتعيين نهج إلى الحالة غير النشطة عندما تريد إجراء تغييرات على نهج، أو عندما لا تريد أن يكون النهج ساري المفعول. |
| [إزالة نهج](#remove-a-policy) | قم بإزالة نهج حواجز المعلومات عندما لم تعد بحاجة إلى نهج معين. |
| [إزالة مقطع](#remove-a-segment) | قم بإزالة مقطع حواجز المعلومات عندما لم تعد بحاجة إلى مقطع معين. |
| [إزالة نهج ومقطع](#remove-a-policy-and-segment) | إزالة نهج حواجز المعلومات ومقطع في نفس الوقت. |
| [إيقاف تطبيق نهج](#stop-a-policy-application) | اتخذ هذا الإجراء عندما تريد إيقاف عملية تطبيق نهج حواجز المعلومات. <br> إيقاف تطبيق نهج ليس فوريا، ولا يتراجع عن النهج التي تم تطبيقها بالفعل على المستخدمين. |
| [تحديد نهج لحواجز المعلومات](information-barriers-policies.md) | حدد نهج حواجز المعلومات عندما لا يكون لديك مثل هذه النهج بالفعل، ويجب عليك تقييد الاتصالات بين مجموعات معينة من المستخدمين أو تقييدها. |
| [استكشاف أخطاء حواجز المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | راجع هذه المقالة عندما تواجه مشاكل غير متوقعة مع حواجز المعلومات. |

>[!IMPORTANT]
>لتنفيذ المهام الموضحة في هذه المقالة، يجب تعيين دور مناسب لك، مثل أحد الإجراءات التالية:<br>- Microsoft 365 Enterprise المسؤول العام<br>- المسؤول العام<br>- مسؤول التوافق<br>- إدارة الامتثال ل IB (هذا دور جديد!)<br><br>لمعرفة المزيد حول المتطلبات الأساسية لحواجز المعلومات، راجع [المتطلبات الأساسية (لنهج حواجز المعلومات).](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met)<br><br> تأكد من [الاتصال ب Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>تحرير سمات حساب المستخدم

استخدم هذا الإجراء لتحرير السمات المستخدمة لتقسيم المستخدمين. على سبيل المثال، إذا كنت تستخدم سمة "القسم"، ولم يكن لدى حساب مستخدم واحد أو أكثر حاليا أي قيم مدرجة للقسم، فيجب تحرير حسابات المستخدمين هذه لتضمين معلومات القسم. يتم استخدام سمات حساب المستخدم لتعريف المقاطع بحيث يمكن تعيين نهج حواجز المعلومات.

1. لعرض تفاصيل حساب مستخدم معين، مثل قيم السمات والمقاطع المعينة، استخدم **Get-InformationBarrierRecipientStatus** cmdlet مع معلمات الهوية.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال المتعارف عليه أو عنوان البريد الإلكتروني أو GUID. <br> (يمكنك أيضا استخدام أمر cmdlet هذا لمستخدم واحد: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> في هذا المثال، نشير إلى حسابين للمستخدمين في Office 365: *meganb* for *Megan*، و *alexw* for *Alex*. |

2. حدد السمة التي تريد تحريرها لملفات تعريف (ملفات) حساب المستخدم. لمزيد من المعلومات، راجع [سمات نهج حواجز المعلومات](information-barriers-attributes.md).

3. تحرير حساب مستخدم واحد أو أكثر لتضمين قيم للسمة التي حددتها في الخطوة السابقة. لاتخاذ هذا الإجراء، استخدم أحد الإجراءات التالية:

    - لتحرير حساب واحد، راجع [إضافة معلومات ملف تعريف المستخدم أو تحديثها باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - لتحرير حسابات متعددة (أو استخدام PowerShell لتحرير حساب واحد)، راجع [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>تحرير مقطع

استخدم هذا الإجراء لتحرير تعريف مقطع مستخدم. على سبيل المثال، قد تقوم بتغيير اسم مقطع أو عامل التصفية المستخدم لتحديد الأشخاص المضمنين في المقطع.

1. لعرض كافة المقاطع الموجودة، استخدم **الأمر Get-OrganizationSegment** cmdlet.

    بناء الجمله: `Get-OrganizationSegment`

    سترى قائمة بالشرائح والتفاصيل لكل مقطع، مثل نوع المقطع وقيمة UserGroupFilter الخاصة به، ومن قام بإنشائه أو آخر تعديل له، و GUID، وما إلى ذلك.

    > [!TIP]
    > اطبع قائمة المقاطع أو احفظها للرجوع إليها لاحقا. على سبيل المثال، إذا كنت تريد تحرير مقطع، فستحتاج إلى معرفة اسمه أو تعريف قيمته (يتم استخدامه مع معلمة الهوية).

2. لتحرير مقطع، استخدم **Set-OrganizationSegment** cmdlet مع معلمة **الهوية** والتفاصيل ذات الصلة.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> في هذا المثال، قمنا بتحديث اسم القسم إلى *HRDept* للمقطع باستخدام GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. عند الانتهاء من تحرير مقاطع لمؤسستك، يمكنك [إما تعريف](information-barriers-policies.md#step-3-create-ib-policies) نهج حواجز المعلومات أو [تحريرها](#edit-a-policy) .

## <a name="edit-a-policy"></a>تحرير نهج

1. لعرض قائمة بنهج حواجز المعلومات الحالية، استخدم **Get-InformationBarrierPolicy** cmdlet.

    بناء الجمله: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد تغييره. لاحظ GUID الخاص بالنهج واسمه.

2. استخدم **Set-InformationBarrierPolicy** cmdlet مع معلمة **Identity** ، وحدد التغييرات التي تريد إجراؤها.

    مثال: افترض أنه تم تعريف نهج لمنع مقطع *الأبحاث* من الاتصال *بقسمي المبيعات* *والتسويق* . تم تعريف النهج باستخدام أمر cmdlet هذا: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    لنفترض أننا نريد تغييره حتى يتمكن الأشخاص في قسم *"الأبحاث"* من التواصل مع الأشخاص في قسم *الموارد البشرية* فقط. لإجراء هذا التغيير، نستخدم أمر cmdlet هذا: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    في هذا المثال، قمنا بتغيير *SegmentsBlocked* إلى *SegmentsAllowed* وحددنا مقطع *الموارد البشرية* .

3. عند الانتهاء من تحرير نهج، تأكد من تطبيق التغييرات. (راجع [تطبيق نهج حواجز المعلومات](information-barriers-policies.md#step-4-apply-ib-policies).)

## <a name="set-a-policy-to-inactive-status"></a>تعيين نهج إلى الحالة غير النشطة

1. لعرض قائمة بنهج حواجز المعلومات الحالية، استخدم **Get-InformationBarrierPolicy** cmdlet.

    بناء الجمله: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد تغييره (أو إزالته). لاحظ GUID الخاص بالنهج واسمه.

2. لتعيين حالة النهج إلى غير نشط، استخدم **Set-InformationBarrierPolicy** cmdlet مع معلمة *Identity* وتعيين معلمة *الحالة* إلى *"غير نشط*".

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> في هذا المثال، يتم تعيين نهج حواجز المعلومات الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c9377247* إلى حالة غير نشطة. |

3. لتطبيق التغييرات، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet.

    بناء الجمله: `Start-InformationBarrierPoliciesApplication`

    يتم تطبيق التغييرات على المستخدم حسب المستخدم لمؤسستك. إذا كانت مؤسستك كبيرة، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). وكإرشادات عامة، يستغرق معالجة 5000 حساب مستخدم حوالي ساعة.

4. في هذه المرحلة، يتم تعيين نهج واحد أو أكثر من نهج حواجز المعلومات إلى حالة غير نشطة. من هنا، يمكنك القيام بأي من الإجراءات التالية:

    - احتفظ به كما هو (لا يؤثر نهج معين على الحالة غير النشطة على المستخدمين)
    - [تحرير نهج](#edit-a-policy) 
    - [إزالة نهج](#remove-a-policy)

## <a name="remove-a-policy"></a>إزالة نهج

1. لعرض قائمة بنهج حواجز المعلومات الحالية، استخدم **Get-InformationBarrierPolicy** cmdlet.

    بناء الجمله: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد إزالته. لاحظ GUID الخاص بالنهج واسمه. 

2. تأكد من تعيين النهج إلى حالة غير نشطة. لتعيين حالة النهج إلى غير نشط، استخدم الأمر cmdlet Set-InformationBarrierPolicy مع معلمة الهوية وتعيين معلمة الحالة إلى "غير نشط".

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> في هذا المثال، قمنا بتعيين نهج حواجز المعلومات الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c9377247* إلى حالة غير نشطة. |

3. لتطبيق التغييرات على النهج، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet.

    بناء الجمله: `Start-InformationBarrierPoliciesApplication`

    يتم تطبيق التغييرات على المستخدم حسب المستخدم لمؤسستك. إذا كانت مؤسستك كبيرة، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). وكإرشادات عامة، يستغرق معالجة 5000 حساب مستخدم حوالي ساعة.

4. استخدم **cmdlet Remove-InformationBarrierPolicy** مع معلمة Identity.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> في هذا المثال، نقوم بإزالة النهج الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    عند المطالبة، قم بتأكيد التغيير.

## <a name="remove-a-segment"></a>إزالة مقطع

1. لعرض كافة المقاطع الموجودة، استخدم **الأمر Get-OrganizationSegment** cmdlet.

    بناء الجمله: `Get-OrganizationSegment`

    سترى قائمة بالشرائح والتفاصيل لكل مقطع، مثل نوع المقطع وقيمة UserGroupFilter الخاصة به، ومن قام بإنشائه أو آخر تعديل له، و GUID، وما إلى ذلك.

    >[!TIP]
    >اطبع قائمة المقاطع أو احفظها للرجوع إليها لاحقا. على سبيل المثال، إذا كنت تريد تحرير مقطع، فستحتاج إلى معرفة اسمه أو تعريف قيمته (يتم استخدامه مع معلمة الهوية).

2. حدد المقطع المطلوب إزالته وتأكد من إزالة نهج IB المقترن بالمقطع. راجع إجراء [إزالة نهج](#remove-a-policy) للحصول على التفاصيل.

3. تحرير المقطع الذي ستتم إزالته لإزالة علاقة المستخدمين بهذا المقطع. يقوم هذا الإجراء بتحديث تعريف المقطع وإزالة كافة المستخدمين من المقطع. ستستخدم معلمة UserGroupFilter لإلغاء اقتران المستخدمين عن المقطع قبل الإزالة.

    لتحرير مقطع، استخدم **Set-OrganizationSegment** cmdlet مع معلمة *الهوية* والتفاصيل ذات الصلة.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> في هذا المثال، بالنسبة إلى المقطع الذي يحتوي على GUID c96e0837-c232-4a8a-841e-ef45787d8fcd، قمنا بتعريف اسم القسم على أنه *FakeDept* لإزالة المستخدمين من المقطع. يستخدم هذا المثال سمة *القسم* ، ولكن يمكنك استخدام سمات أخرى حسب الاقتضاء. يستخدم المثال *FakeDept* لأن هذا غير موجود ومن المؤكد أنه لا يحتوي على أي مستخدمين. |

4. لتطبيق التغييرات، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet.

    بناء الجمله: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >تزيل السمة *CleanupGroupSegmentLink* اقتباطات المجموعة مع المقطع الذي لا يحتوي على اقتباطات مستخدمين.

    يتم تطبيق التغييرات على المستخدم حسب المستخدم لمؤسستك. إذا كانت مؤسستك كبيرة، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). وكإرشادات عامة، يستغرق معالجة 5000 حساب مستخدم حوالي ساعة.

5. لإزالة مقطع، استخدم **cmdlet Remove-OrganizationSegment** مع معلمة *الهوية* والتفاصيل ذات الصلة.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> في هذا المثال، تمت إزالة المقطع الذي يحتوي على GUID c96e0837-c232-4a8a-841e-ef45787d8fcd. |

## <a name="remove-a-policy-and-segment"></a>إزالة نهج ومقطع

1. لعرض قائمة بنهج حواجز المعلومات الحالية، استخدم **Get-InformationBarrierPolicy** cmdlet.

    بناء الجمله: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد إزالته. لاحظ GUID الخاص بالنهج واسمه.

2. لعرض كافة المقاطع الموجودة، استخدم **الأمر Get-OrganizationSegment** cmdlet.

    بناء الجمله: `Get-OrganizationSegment`

    سترى قائمة بالمقاطع والتفاصيل لكل مقطع، مثل نوع المقطع وقيمة معلمة *UserGroupFilter* الخاصة به، ومن قام بإنشائه أو آخر تعديل له، و GUID، وما إلى ذلك.

    >[!TIP]
    >اطبع قائمة المقاطع أو احفظها للرجوع إليها لاحقا. على سبيل المثال، إذا كنت تريد تحرير مقطع، فستحتاج إلى معرفة اسمه أو تعريف قيمته (يتم استخدامه مع معلمة الهوية).

3. لتعيين حالة النهج المراد إزالته إلى غير نشط، استخدم **Set-InformationBarrierPolicy** cmdlet مع معلمة *Identity* ومعلمة *الحالة* المعينة إلى *"غير نشط*".

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> في هذا المثال، قمنا بتعيين نهج حواجز المعلومات الذي يحتوي على GUID 43c37853-ea10-4b90-a23d-ab8c93772471 إلى حالة غير نشطة. |

4. تحرير المقطع الذي ستتم إزالته لإزالة علاقة المستخدمين بهذا المقطع. يقوم هذا الإجراء بتحديث تعريف المقطع وإزالة كافة المستخدمين من المقطع. ستستخدم معلمة *UserGroupFilter* لإلغاء اقتران المستخدمين عن المقطع قبل الإزالة.

    لتحرير مقطع، استخدم **Set-OrganizationSegment** cmdlet مع معلمة *الهوية* والتفاصيل ذات الصلة.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> في هذا المثال، بالنسبة إلى المقطع الذي يحتوي على GUID c96e0837-c232-4a8a-841e-ef45787d8fcd، قمنا بتحديث اسم القسم إلى *FakeDept لإزالة* المستخدمين من المقطع. يستخدم هذا المثال سمة *القسم* ، ولكن يمكنك استخدام سمات أخرى حسب الاقتضاء. يستخدم المثال *FakeDept* لأن هذا غير موجود ومن المؤكد أنه لا يحتوي على مستخدمين. |

5. لتطبيق التغييرات، استخدم **Start-InformationBarrierPoliciesApplication** cmdlet.

    بناء الجمله: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >تزيل السمة *CleanupGroupSegmentLink* اقتباطات المجموعة مع المقطع الذي لا يحتوي على اقتباطات مستخدمين.

    يتم تطبيق التغييرات على المستخدم حسب المستخدم لمؤسستك. إذا كانت مؤسستك كبيرة، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). وكإرشادات عامة، يستغرق معالجة 5000 حساب مستخدم حوالي ساعة.

6. استخدم **cmdlet Remove-InformationBarrierPolicy** مع معلمة *Identity* .

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> في هذا المثال، تتم إزالة النهج الذي يحتوي على GUID *43c37853-ea10-4b90-a23d-ab8c93772471* . |

    عند المطالبة، قم بتأكيد التغيير.

7. لإزالة مقطع، استخدم **cmdlet Remove-OrganizationSegment** مع معلمة *الهوية* والتفاصيل ذات الصلة.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> في هذا المثال، تمت إزالة المقطع الذي يحتوي على GUID c96e0837-c232-4a8a-841e-ef45787d8fcd. |

## <a name="stop-a-policy-application"></a>إيقاف تطبيق نهج

بعد البدء في تطبيق نهج حواجز المعلومات، إذا كنت تريد إيقاف تطبيق هذه النهج، فاستخدم الإجراء التالي. سيستغرق بدء العملية حوالي 30-35 دقيقة.

1. لعرض حالة تطبيق نهج حواجز المعلومات الأحدث، استخدم **Get-InformationBarrierPoliciesApplicationStatus** cmdlet.

    بناء الجمله: `Get-InformationBarrierPoliciesApplicationStatus`

    لاحظ GUID الخاص بالتطبيق.

2. استخدم **أمر cmdlet Stop-InformationBarrierPoliciesApplication** مع معلمة Identity.

    |**بناء الجمله**|**المثال**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> في هذا المثال، نحن نوقف تطبيق نهج حواجز المعلومات. |

## <a name="resources"></a>الموارد

- [الحصول على نظرة عامة على حواجز المعلومات](information-barriers.md)
- [تحديد نهج لحواجز المعلومات](information-barriers-policies.md)
- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
- [سمات نهج IB](information-barriers-attributes.md)
- [استكشاف أخطاء حواجز المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)
