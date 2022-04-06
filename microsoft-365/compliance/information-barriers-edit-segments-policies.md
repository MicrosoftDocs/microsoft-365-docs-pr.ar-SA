---
title: إدارة سياسات حواجز المعلومات
description: تعرف على كيفية تحرير أو إزالة السياسات والشرائح لعوائق المعلومات.
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
ms.openlocfilehash: fc8cc7e4fcbfb9fe9c2ee0f1c531511d9c2fa0b6
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634350"
---
# <a name="manage-information-barriers-policies"></a>إدارة سياسات حواجز المعلومات

بعد تحديد [سياسات](information-barriers-policies.md) عوائق المعلومات، قد تحتاج إلى إجراء تغييرات على السياسات أو شرائح المستخدمين كجزء من استكشاف الأخطاء وإصلاحها أو الصيانة العادية.[](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)

## <a name="what-do-you-want-to-do"></a>ماذا تريد أن تفعل؟

|**الإجراء**|**الوصف**|
|:---------|:--------------|
| [تحرير سمات حساب المستخدم](#edit-user-account-attributes) | قم بتعبئة السمات في Azure Active Directory التي يمكن استخدامها لتعريف الشرائح. <br> يمكنك تحرير سمات حساب المستخدم عندما لا يتم تضمين المستخدمين في الشرائح التي يجب أن يكونوا عليها، أو لتغيير الشرائح التي يوجد فيها المستخدمون، أو لتعريف الشرائح التي تستخدم سمات مختلفة. |
| [تحرير مقطع](#edit-a-segment) | قم بتحرير الشرائح عندما تريد تغيير كيفية تعريف مقطع. <br> على سبيل المثال، قد يكون لديك شرائح معرفة في الأصل تستخدم *القسم* وتريد الآن استخدام سمة أخرى، مثل *MemberOf*. |
| [تحرير نهج](#edit-a-policy) | قم بتحرير نهج عوائق المعلومات عندما تريد تغيير طريقة عمل النهج.<br> على سبيل المثال، بدلا من حظر الاتصالات بين مقطعين، قد تقرر أنك تريد السماح بحدث الاتصالات بين شرائح معينة فقط. |
| [تعيين نهج إلى حالة غير نشطة](#set-a-policy-to-inactive-status) |قم بتعيين نهج إلى حالة غير نشطة عندما تريد إجراء تغييرات على نهج، أو عندما لا تريد أن يكون النهج في وضع التنفيذ. |
| [إزالة نهج](#remove-a-policy) | قم بإزالة نهج حواجز المعلومات عندما لا تحتاج إلى نهج معين في مكانه. |
| [إزالة مقطع](#remove-a-segment) | قم بإزالة مقطع حواجز المعلومات عندما لا تحتاج إلى مقطع معين. |
| [إزالة نهج وشرائح](#remove-a-policy-and-segment) | قم بإزالة نهج حاجز المعلومات ومشرق في الوقت نفسه. |
| [إيقاف تطبيق نهج](#stop-a-policy-application) | اتخاذ هذا الإجراء عندما تريد إيقاف عملية تطبيق سياسات حواجز المعلومات. <br> إن إيقاف تطبيق نهج ليس فوريا، ولا يؤدي إلى التراجع عن النهج المطبقة بالفعل على المستخدمين. |
| [تعريف سياسات لعوائق المعلومات](information-barriers-policies.md) | حدد نهج حواجز المعلومات عندما لا تكون لديك مثل هذه النهج في مكانها، ويجب تقييد الاتصالات أو تقييدها بين مجموعات معينة من المستخدمين. |
| [استكشاف مشاكل المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting) | راجع هذه المقالة عندما تخوض مشاكل غير متوقعة تتعلق بعوائق المعلومات. |

>[!IMPORTANT]
>لتنفيذ المهام الموضحة في هذه المقالة، يجب أن يتم تعيين دور مناسب لك، مثل أحد الإجراءات التالية:<br>- Microsoft 365 Enterprise عام<br>- المسؤول العام<br>- مسؤول التوافق<br>- إدارة توافق IB (هذا دور جديد!)<br><br>لمعرفة المزيد حول المتطلبات الأساسية لعوائق المعلومات، راجع المتطلبات الأساسية [(لنهج عوائق المعلومات)](information-barriers-policies.md#step-1-make-sure-prerequisites-are-met).<br><br> تأكد من [الاتصال بمركز التوافق & PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="edit-user-account-attributes"></a>تحرير سمات حساب المستخدم

استخدم هذا الإجراء لتحرير السمات المستخدمة لتقزز المستخدمين. على سبيل المثال، إذا كنت تستخدم سمة "القسم"، وكان حساب مستخدم واحد أو أكثر لا يتضمن حاليا أي قيم مدرجة في القسم، فيجب تحرير حسابات المستخدمين هذه لتضمين معلومات القسم. يتم استخدام سمات حساب المستخدم لتعريف الشرائح بحيث يمكن تعيين سياسات عوائق المعلومات.

1. لعرض تفاصيل حساب مستخدم معين، مثل قيم السمات والمشريط (الأجزاء المعينة)، استخدم **الأمر Cmdlet Get-InformationBarrierRecipientStatus** مع معلمات الهوية.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <br> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال الماجد أو عنوان البريد الإلكتروني أو GUID. <br> (يمكنك أيضا استخدام الأمر cmdlet هذا لمستخدم واحد: `Get-InformationBarrierRecipientStatus -Identity <value>`) |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <br> في هذا المثال، نشير إلى حسابي مستخدم في Office 365: *ميغان* و *alexw* ل *Alex*. |

2. حدد السمة التي تريد تحريرها لملف تعريف (ملفات) حساب المستخدم. لمزيد من المعلومات، راجع [السمات لنهج عوائق المعلومات](information-barriers-attributes.md).

3. قم بتحرير حساب مستخدم واحد أو أكثر لتضمين قيم السمة التي حددتها في الخطوة السابقة. لاتخاذ هذا الإجراء، استخدم أحد الإجراءات التالية:

    - لتحرير حساب واحد، راجع إضافة معلومات ملف تعريف مستخدم أو تحديثها [باستخدام Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

    - لتحرير حسابات متعددة (أو استخدام PowerShell لتحرير حساب واحد)، راجع تكوين خصائص حساب المستخدم باستخدام Office 365 [PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).

## <a name="edit-a-segment"></a>تحرير مقطع

استخدم هذا الإجراء لتحرير تعريف مقطع مستخدم. على سبيل المثال، يمكنك تغيير اسم المقطع أو عامل التصفية المستخدم لتحديد الأشخاص المضمنين في المقطع.

1. لعرض كل الشرائح الموجودة، استخدم **الأمر Cmdlet Get-OrganizationSegment** .

    بناء الجملة: `Get-OrganizationSegment`

    سترى قائمة بالشرائح والتفاصيل الخاصة بكل مقطع، مثل نوع المقطع وقيمته UserGroupFilter ومن قام بإنشاءه أو تعديله الأخير و GUID وما إلى ذلك.

    > [!TIP]
    > يمكنك طباعة قائمة الشرائح أو حفظها كمرجع في وقت لاحق. على سبيل المثال، إذا كنت تريد تحرير مقطع، ستحتاج إلى معرفة اسمه أو قيمة التعريف الخاصة به (يتم استخدام هذا مع معلمة الهوية).

2. لتحرير مقطع، استخدم **الأمر cmdlet Set-OrganizationSegment** مع **معلمة الهوية** والتفاصيل ذات الصلة.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` |`Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'HRDept'"` <br> في هذا المثال، قمنا بتحديث اسم القسم إلى *HRDept* للمشرق باستخدام GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

3. عند الانتهاء من تحرير مقاطع لمنظمتك، يمكنك تحديد سياسات عوائق المعلومات أو تحريرها.[](#edit-a-policy) [](information-barriers-policies.md#step-3-define-information-barrier-policies)

## <a name="edit-a-policy"></a>تحرير نهج

1. لعرض قائمة ونهج عوائق المعلومات الحالية، استخدم **الأمر cmdlet Get-InformationBarrierPolicy** .

    بناء الجملة: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد تغييره. لاحظ GUID واسم النهج.

2. استخدم **الأمر cmdlet Set-InformationBarrierPolicy** مع معلمة **الهوية** ، وحدد التغييرات التي تريد إدخالها.

    مثال: لنفترض أنه تم تعريف نهج لمنع مقطع *الأبحاث* من التواصل مع قسمي المبيعات  *والتسويق*. تم تعريف النهج باستخدام الأمر cmdlet هذا: `New-InformationBarrierPolicy -Name "Research-SalesMarketing" -AssignedSegment "Research" -SegmentsBlocked "Sales","Marketing"`

    لنفترض أننا نريد تغييره بحيث يمكن للأشخاص في مقطع  الأبحاث التواصل مع الأشخاص في قسم *الموارد* البشرية فقط. لتغيير هذا التغيير، نستخدم الأمر cmdlet هذا: `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -SegmentsAllowed "HR"`

    في هذا المثال، قمنا بتغيير *"الأجزاءBlocked"* إلى *"شرائح"،* وحددنا مقطع *الموارد* البشرية.

3. عند الانتهاء من تحرير نهج، تأكد من تطبيق التغييرات. (راجع [تطبيق سياسات حواجز المعلومات](information-barriers-policies.md#step-4-apply-information-barrier-policies).)

## <a name="set-a-policy-to-inactive-status"></a>تعيين نهج إلى حالة غير نشطة

1. لعرض قائمة ونهج عوائق المعلومات الحالية، استخدم **الأمر cmdlet Get-InformationBarrierPolicy** .

    بناء الجملة: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد تغييره (أو إزالته). لاحظ GUID واسم النهج.

2. لتعيين حالة النهج إلى غير نشطة، استخدم الأمر **cmdlet Set-InformationBarrierPolicy** مع معلمة الهوية ومعاينة الحالة إلى *غير نشط*. 

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> في هذا المثال، يتم تعيين نهج حواجز المعلومات الذي لديه GUID *43c37853-ea10-4b90-a23d-ab8c9377247* إلى حالة غير نشطة. |

3. لتطبيق التغييرات، استخدم **الأمر cmdlet Start-InformationBarrierPoliciesApplication** .

    بناء الجملة: `Start-InformationBarrierPoliciesApplication`

    يتم تطبيق التغييرات على مؤسستك من قبل المستخدم. إذا كانت مؤسستك كبيرة الحجم، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). كمرشاد عام، تستغرق معالجة 5000 حساب مستخدم ساعة تقريبا.

4. في هذه المرحلة، يتم تعيين واحد أو أكثر من سياسات عوائق المعلومات إلى حالة غير نشطة. من هنا، يمكنك القيام بأي من الإجراءات التالية:

    - الاحتفاظ به كما هو (نهج تم تعيينه إلى حالة غير نشطة لا يكون له أي تأثير على المستخدمين)
    - [تحرير نهج](#edit-a-policy) 
    - [إزالة نهج](#remove-a-policy)

## <a name="remove-a-policy"></a>إزالة نهج

1. لعرض قائمة ونهج عوائق المعلومات الحالية، استخدم **الأمر cmdlet Get-InformationBarrierPolicy** .

    بناء الجملة: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد إزالته. لاحظ GUID واسم النهج. 

2. تأكد من تعيين النهج إلى حالة غير نشطة. لتعيين حالة النهج إلى غير نشطة، استخدم الأمر cmdlet Set-InformationBarrierPolicy مع معلمة الهوية ومعاينة الحالة إلى غير نشط.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive`  | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c9377247 -State Inactive` <br> في هذا المثال، نقوم بتعيين نهج حواجز المعلومات الذي لديه GUID *43c37853-ea10-4b90-a23d-ab8c9377247* إلى حالة غير نشطة. |

3. لتطبيق تغييراتك على النهج، استخدم **الأمر cmdlet Start-InformationBarrierPoliciesApplication** .

    بناء الجملة: `Start-InformationBarrierPoliciesApplication`

    يتم تطبيق التغييرات على مؤسستك من قبل المستخدم. إذا كانت مؤسستك كبيرة الحجم، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). كمرشاد عام، تستغرق معالجة 5000 حساب مستخدم ساعة تقريبا.

4. استخدم **الأمر cmdlet Remove-InformationBarrierPolicy** مع معلمة الهوية.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> في هذا المثال، نقوم بإزالة النهج الذي به GUID *43c37853-ea10-4b90-a23d-ab8c93772471*. |

    عند مطالبتك بذلك، تأكد من التغيير.

## <a name="remove-a-segment"></a>إزالة مقطع

1. لعرض كل الشرائح الموجودة، استخدم **الأمر Cmdlet Get-OrganizationSegment** .

    بناء الجملة: `Get-OrganizationSegment`

    سترى قائمة بالشرائح والتفاصيل الخاصة بكل مقطع، مثل نوع المقطع وقيمته UserGroupFilter ومن قام بإنشاءه أو تعديله الأخير و GUID وما إلى ذلك.

    >[!TIP]
    >يمكنك طباعة قائمة الشرائح أو حفظها كمرجع في وقت لاحق. على سبيل المثال، إذا كنت تريد تحرير مقطع، ستحتاج إلى معرفة اسمه أو قيمة التعريف الخاصة به (يتم استخدام هذا مع معلمة الهوية).

2. حدد المقطع الذي تريد إزالته وتأكد من إزالة نهج IB المقترن بالمشرق. راجع الإجراء [إزالة نهج](#remove-a-policy) للحصول على التفاصيل.

3. قم بتحرير المقطع الذي سيتم إزالته لإزالة علاقة المستخدمين بهذا المقطع. يقوم هذا الإجراء بتحديث تعريف المقطع وإزالة جميع المستخدمين من المقطع. سوف تستخدم المعلمة UserGroupFilter لإزالة المستخدمين من المقطع قبل الإزالة.

    لتحرير مقطع، استخدم **الأمر cmdlet Set-OrganizationSegment** مع *معلمة الهوية* والتفاصيل ذات الصلة.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> في هذا المثال، بالنسبة إلى المقطع الذي به GUID c96e0837-c232-4a8a-841e-ef45787d8fcd، قمنا بتعريف اسم القسم على أنه *"زائفDept* " لإزالة المستخدمين من المقطع. يستخدم هذا المثال *السمة "القسم* "، ولكن يمكنك استخدام سمات أخرى حسب الاقتضاء. يستخدم المثال *FakeDept* لأن هذا غير موجود ومن المؤكد أنه لا يحتوي على أي مستخدمين. |

4. لتطبيق التغييرات، استخدم **الأمر cmdlet Start-InformationBarrierPoliciesApplication** .

    بناء الجملة: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*تزيل السمة CleanupGroupSegmentLink* اقترانات المجموعات مع المقطع بدون اقترانات المستخدمين.

    يتم تطبيق التغييرات على مؤسستك من قبل المستخدم. إذا كانت مؤسستك كبيرة الحجم، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). كمرشاد عام، تستغرق معالجة 5000 حساب مستخدم ساعة تقريبا.

5. لإزالة مقطع، استخدم **الأمر cmdlet Remove-OrganizationSegment** مع *معلمة الهوية* والتفاصيل ذات الصلة.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> في هذا المثال، تمت إزالة المقطع الذي به GUID c96e0837-c232-4a8a-841e-ef45787d8fcd. |

## <a name="remove-a-policy-and-segment"></a>إزالة نهج ومشرق

1. لعرض قائمة ونهج عوائق المعلومات الحالية، استخدم **الأمر cmdlet Get-InformationBarrierPolicy** .

    بناء الجملة: `Get-InformationBarrierPolicy`

    في قائمة النتائج، حدد النهج الذي تريد إزالته. لاحظ GUID واسم النهج.

2. لعرض كل الشرائح الموجودة، استخدم **الأمر Cmdlet Get-OrganizationSegment** .

    بناء الجملة: `Get-OrganizationSegment`

    سترى قائمة بالشرائح والتفاصيل الخاصة بكل مقطع، مثل نوع المقطع وقيمة معلمة *UserGroupFilter* الخاصة به، ومن قام بإنشاءه أو تعديله آخر مرة، و GUID، وما إلى ذلك.

    >[!TIP]
    >يمكنك طباعة قائمة الشرائح أو حفظها كمرجع في وقت لاحق. على سبيل المثال، إذا كنت تريد تحرير مقطع، ستحتاج إلى معرفة اسمه أو قيمة التعريف الخاصة به (يتم استخدام هذا مع معلمة الهوية).

3. لتعيين حالة النهج الذي تريد إزالته إلى غير نشط، استخدم الأمر **Cmdlet Set-InformationBarrierPolicy** مع معلمة الهوية ومعاينة  الحالة إلى *غير نشط*.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Inactive` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Inactive` <br> في هذا المثال، نقوم بتعيين نهج عوائق المعلومات الذي لديه GUID 43c37853-ea10-4b90-a23d-ab8c93772471 إلى حالة غير نشطة. |

4. قم بتحرير المقطع الذي سيتم إزالته لإزالة علاقة المستخدمين بهذا المقطع. يقوم هذا الإجراء بتحديث تعريف المقطع وإزالة جميع المستخدمين من المقطع. سوف تستخدم المعلمة *UserGroupFilter* لإزالة المستخدمين من المقطع قبل الإزالة.

    لتحرير مقطع، استخدم **الأمر cmdlet Set-OrganizationSegment** مع *معلمة الهوية* والتفاصيل ذات الصلة.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Set-OrganizationSegment -Identity GUID -UserGroupFilter "attribute -eq 'attributevalue'"` | `Set-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd -UserGroupFilter "Department -eq 'FakeDept'"` <br> في هذا المثال، بالنسبة إلى المقطع الذي به GUID c96e0837-c232-4a8a-841e-ef45787d8fcd، قمنا بتحديث اسم القسم إلى *FakeDept* لإزالة المستخدمين من المقطع. يستخدم هذا المثال *السمة "القسم* "، ولكن يمكنك استخدام سمات أخرى حسب الاقتضاء. يستخدم المثال *FakeDept* لأن هذا غير موجود ومن المؤكد أنه لا يحتوي على مستخدمين. |

5. لتطبيق التغييرات، استخدم **الأمر cmdlet Start-InformationBarrierPoliciesApplication** .

    بناء الجملة: `Start-InformationBarrierPoliciesApplication -CleanupGroupSegmentLink`

    >[!NOTE]
    >*تزيل السمة CleanupGroupSegmentLink* اقترانات المجموعات مع المقطع بدون اقترانات المستخدمين.

    يتم تطبيق التغييرات على مؤسستك من قبل المستخدم. إذا كانت مؤسستك كبيرة الحجم، فقد يستغرق إكمال هذه العملية 24 ساعة (أو أكثر). كمرشاد عام، تستغرق معالجة 5000 حساب مستخدم ساعة تقريبا.

6. استخدم **الأمر cmdlet Remove-InformationBarrierPolicy** مع *معلمة الهوية* .

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Remove-InformationBarrierPolicy -Identity GUID` | `Remove-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471` <br> في هذا المثال، تتم إزالة النهج الذي به GUID *43c37853-ea10-4b90-a23d-ab8c93772471* . |

    عند مطالبتك بذلك، تأكد من التغيير.

7. لإزالة مقطع، استخدم **الأمر cmdlet Remove-OrganizationSegment** مع *معلمة الهوية* والتفاصيل ذات الصلة.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Remove-OrganizationSegment -Identity GUID` | `Remove-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <br> في هذا المثال، تمت إزالة المقطع مع GUID c96e0837-c232-4a8a-841e-ef45787d8fcd. |

## <a name="stop-a-policy-application"></a>إيقاف تطبيق نهج

بعد بدء تطبيق سياسات حواجز المعلومات، إذا كنت تريد منع تطبيق هذه السياسات، فاستخدم الإجراء التالي. سيستغرق بدء العملية من 30 إلى 35 دقيقة تقريبا.

1. لعرض حالة تطبيق نهج حاجز المعلومات الأخير، استخدم **الأمر cmdlet Get-InformationBarrierPoliciesApplicationStatus** .

    بناء الجملة: `Get-InformationBarrierPoliciesApplicationStatus`

    لاحظ GUID الخاص للتطبيق.

2. استخدم **الأمر cmdlet Stop-InformationBarrierPoliciesApplication** مع معلمة Identity.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Stop-InformationBarrierPoliciesApplication -Identity GUID` | `Stop-InformationBarrierPoliciesApplication -Identity 46237888-12ca-42e3-a541-3fcb7b5231d1` <p> في هذا المثال، نقوم بإيقاف تطبيق سياسات عوائق المعلومات. |

## <a name="resources"></a>الموارد

- [الحصول على نظرة عامة حول حواجز المعلومات](information-barriers.md)
- [تعريف سياسات لعوائق المعلومات](information-barriers-policies.md)
- [تعرف على المزيد حول حواجز المعلومات في Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [تعرف على المزيد حول حواجز المعلومات في SharePoint Online](/sharepoint/information-barriers)
- [تعرف على المزيد حول حواجز المعلومات في OneDrive](/onedrive/information-barriers)
- [سمات سياسات حواجز المعلومات](information-barriers-attributes.md)
- [استكشاف مشاكل المعلومات وإصلاحها](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting)