---
title: استكشاف مشاكل المعلومات وإصلاحها
description: استخدم هذه المقالة كدليل حول استكشاف مشاكل المعلومات وإصلاحها.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: None
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: de415ba7b68df786ead038bb72465c445a86ba5a
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 09/12/2021
ms.locfileid: "63567116"
---
# <a name="troubleshooting-information-barriers"></a>استكشاف مشاكل المعلومات وإصلاحها

[يمكن أن تساعد حواجز](information-barriers.md) المعلومات مؤسستك على البقاء متوافقا مع المتطلبات القانونية واللوائح الصناعية. على سبيل المثال، باستخدام حواجز المعلومات، يمكنك تقييد الاتصال بين مجموعات معينة من المستخدمين لتجنب حدوث تضارب في المصالح أو مشاكل أخرى. (لمعرفة المزيد حول كيفية إعداد حواجز المعلومات، راجع [تعريف سياسات لعوائق المعلومات](information-barriers-policies.md).)

في حالة خوض الأشخاص مشاكل غير متوقعة بعد وضع حواجز المعلومات، هناك بعض الخطوات التي يمكنك اتخاذها لحل هذه المشاكل. استخدم هذه المقالة كدليل.

> [!IMPORTANT]
> لتنفيذ المهام الموضحة في هذه المقالة، يجب أن يتم تعيين دور مناسب لك، مثل أحد الإجراءات التالية:<br/>- Microsoft 365 Enterprise عام<br/>- المسؤول العام<br/>- مسؤول التوافق<br/>- إدارة توافق IB (هذا دور جديد!)<p>لمعرفة المزيد حول المتطلبات الأساسية لعوائق المعلومات، راجع [المتطلبات الأساسية (لنهج حاجز المعلومات)](information-barriers-policies.md#prerequisites).<p>تأكد من [الاتصال بمركز & التوافق PowerShell](/powershell/exchange/connect-to-scc-powershell).

## <a name="issue-users-are-unexpectedly-blocked-from-communicating-with-others-in-microsoft-teams"></a>المشكلة: يتم حظر المستخدمين بشكل غير متوقع من التواصل مع الآخرين في Microsoft Teams 

في هذه الحالة، أبلغ الأشخاص عن مشاكل غير متوقعة تتعلق بالتواصل مع الآخرين في Microsoft Teams. بعض الأمثلة هي:

- يبحث المستخدم عن مستخدم آخر في Microsoft Teams، ولكن يتعذر عليه العثور عليه.
- يمكن للمستخدم العثور على مستخدم آخر في Microsoft Teams، ولكن لا يمكنه تحديده.
- يمكن للمستخدم رؤية مستخدم آخر، ولكن لا يمكنه إرسال رسائل إلى هذا المستخدم الآخر في Microsoft Teams.

### <a name="what-to-do"></a>ما يجب فعله

تحديد ما إذا كان المستخدمون يتأثرون نهج حاجز المعلومات أم لا. استنادا إلى كيفية تكوين السياسات، قد تعمل حواجز المعلومات كما هو متوقع. أو، قد تحتاج إلى تحسين سياسات مؤسستك.

1. استخدم **الأمر Cmdlet Get-InformationBarrierRecipientStatus** مع المعلمة Identity. 

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity` <p> يمكنك استخدام أي قيمة هوية تعرف كل مستلم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز (DN) أو DN المكين أو عنوان البريد الإلكتروني أو GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb` <p> في هذا المثال، نستخدم اسما مستعارا (*ميغالب*) لمعلمة الهوية. سيرجع أمر cmdlet هذا معلومات تشير إلى ما إذا كان المستخدم متأثرا ب نهج حاجز المعلومات. (ابحث عن *ExoPolicyId: \<GUID>.) |

    **إذا لم يتم تضمين المستخدمين في سياسات حاجز المعلومات، فاتصل بالدعم**. وإلا، فتابع إلى الخطوة التالية.

2. تعرف على الشرائح المضمنة في نهج حاجز المعلومات. للقيام بذلك، استخدم `Get-InformationBarrierPolicy` الأمر cmdlet مع معلمة الهوية. 

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Get-InformationBarrierPolicy` <p> استخدم التفاصيل، مثل GUID (ExoPolicyId) النهج الذي تلقيته أثناء الخطوة السابقة، كقيمة هوية. | `Get-InformationBarrierPolicy -Identity b42c3d0f-49e9-4506-a0a5-bf2853b5df6f` <p> في هذا المثال، نحن نتلقى معلومات مفصلة حول نهج حاجز المعلومات الذي به ExoPolicyId *b42c3d0f-49e9-4506-a0a5-bf2853b5df6f*. |

    بعد تشغيل الأمر cmdlet، في النتائج، ابحث عن **القيم AssignedSegment** و **SegmentsAllowed** و **SegmentsBlocked** .

    على سبيل المثال، بعد تشغيل `Get-InformationBarrierPolicy` cmdlet، شاهدنا ما يلي في قائمة النتائج:

    ```powershell
    AssignedSegment : Sales
    SegmentsAllowed : {}
    SegmentsBlocked : {Research}
    ```

    في هذه الحالة، يمكننا رؤية أن نهج حاجز المعلومات يؤثر على الأشخاص في قسمي المبيعات والأبحاث. في هذه الحالة، يتم منع الأشخاص في المبيعات من التواصل مع الأشخاص في الأبحاث.

    إذا بدا هذا صحيحا، فهذا يعني أن حواجز المعلومات تعمل كما هو متوقع. إذا لم يكن الأمر كذلك، فاتابع إلى الخطوة التالية.

3. تأكد من تعريف الشرائح بشكل صحيح. للقيام بذلك، استخدم `Get-OrganizationSegment` الأمر cmdlet، ثم راجع قائمة النتائج.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Get-OrganizationSegment`<p> استخدم الأمر cmdlet هذا مع معلمة الهوية. | `Get-OrganizationSegment -Identity c96e0837-c232-4a8a-841e-ef45787d8fcd` <p> في هذا المثال، نحن نتلقى معلومات حول المقطع الذي به GUID *c96e0837-c232-4a8a-841e-ef45787d8fcd*. |

    راجع تفاصيل المقطع. إذا لزم الأمر [، قم بتحرير مقطع](information-barriers-edit-segments-policies.md#edit-a-segment)، ثم إعادة استخدام `Start-InformationBarrierPoliciesApplication` cmdlet.

    **إذا كنت لا تزال تواجه مشاكل في نهج حاجز المعلومات، فاتصل بالدعم**.

## <a name="issue-communications-are-allowed-between-users-who-should-be-blocked-in-microsoft-teams"></a>المشكلة: يتم السماح بالاتصالات بين المستخدمين الذين يجب حظرهم في Microsoft Teams

في هذه الحالة، على الرغم من أن حواجز المعلومات محددة ونشطة ومطبقة، فإن الأشخاص الذين يجب منعهم من التواصل مع بعضهم البعض يتمكنون بطريقة ما من الدردشة مع بعضهم البعض والاتصال ببعضهم البعض في Microsoft Teams.

### <a name="what-to-do"></a>ما يجب فعله

تحقق من تضمين المستخدمين المعنيين في نهج حاجز المعلومات. 

1. استخدم **الأمر Cmdlet Get-InformationBarrierRecipientStatus** مع معلمات الهوية.

    |**بناء الجملة** _|_ *Example**|
    |:----------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال الماجد أو عنوان البريد الإلكتروني أو GUID. |`Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> في هذا المثال، نشير إلى حسابي مستخدم في Office 365: *ميغان* و *alexw* ل *Alex*. |

    > [!TIP]
    > يمكنك أيضا استخدام الأمر cmdlet هذا لمستخدم واحد: `Get-InformationBarrierRecipientStatus -Identity <value>`

2. راجع النتائج. ترجع **Cmdlet Get-InformationBarrierRecipientStatus** معلومات حول المستخدمين، مثل قيم السمات وأي سياسات حاجز معلومات يتم تطبيقها.

    راجع النتائج، ثم قم باتخاذ الخطوات التالية، كما هو موضح في الجدول التالي:

    |**النتائج**|**ما يجب فعله بعد ذلك**|
    |:----------|:------------------|
    | لا توجد أي شرائح مدرجة للمستخدم (المستخدمين) المحددين | القيام بوا واحد من الخطوات التالية:<br/>- قم بتعيين المستخدمين إلى مقطع موجود من خلال تحرير ملفات تعريف المستخدمين في Azure Active Directory. (راجع [تكوين خصائص حساب المستخدم باستخدام Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md).)<br/>- تعريف مقطع باستخدام سمة [معتمدة لعوائق المعلومات](information-barriers-attributes.md). بعد ذلك [، يمكنك تحديد نهج جديد](information-barriers-policies.md#part-2-define-information-barrier-policies) أو [تحرير نهج موجود](information-barriers-edit-segments-policies.md#edit-a-policy) لتضمين هذا المقطع. |
    | يتم سرد الشرائح ولكن لا يتم تعيين أي سياسات لعوائق المعلومات لهذه الشرائح | القيام بوا واحد من الخطوات التالية:<br/>- [تعريف نهج جديد لعوائق المعلومات](information-barriers-policies.md#part-2-define-information-barrier-policies) لكل مقطع في السؤال <br/>- [تحرير نهج حاجز معلومات موجود](information-barriers-edit-segments-policies.md#edit-a-policy) لتعيينه إلى المقطع الصحيح |
    | يتم سرد الشرائح وكل منها مضمن في نهج حاجز المعلومات | - تشغيل `Get-InformationBarrierPolicy` cmdlet للتحقق من أن سياسات حاجز المعلومات نشطة<br/>- تشغيل `Get-InformationBarrierPoliciesApplicationStatus` cmdlet لتأكيد تطبيق النهج<br/>- تشغيل `Start-InformationBarrierPoliciesApplication` cmdlet لتطبيق كل سياسات حاجز المعلومات النشطة |

## <a name="issue-i-need-to-remove-a-single-user-from-an-information-barrier-policy"></a>المشكلة: أحتاج إلى إزالة مستخدم واحد من نهج حاجز المعلومات

في هذه الحالة، تكون سياسات حاجز المعلومات في وضع التنفيذ، ويحظر على مستخدم واحد أو أكثر بشكل غير متوقع التواصل مع الآخرين في Microsoft Teams. بدلا من إزالة سياسات حاجز المعلومات تماما، يمكنك إزالة مستخدم واحد أو أكثر من سياسات حاجز المعلومات.

### <a name="what-to-do"></a>ما يجب فعله

يتم تعيين سياسات حاجز المعلومات إلى شرائح من المستخدمين. يتم تعريف الشرائح باستخدام سمات [معينة في ملفات تعريف حساب المستخدم](information-barriers-attributes.md). إذا كان عليك إزالة نهج من مستخدم واحد، فنظر في تحرير ملف تعريف هذا المستخدم في Azure Active Directory حتى لا يعود المستخدم مضمنا في مقطع يتأثر بعوائق المعلومات.

1. استخدم **الأمر Cmdlet Get-InformationBarrierRecipientStatus** مع معلمات الهوية. ترجع cmdlet هذه معلومات حول المستخدمين، مثل قيم السمات وأي سياسات حاجز معلومات يتم تطبيقها.

    |**بناء الجملة**|**مثال**|
    |:---------|:----------|
    | `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> يمكنك استخدام أي قيمة تعرف كل مستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال الماجد أو عنوان البريد الإلكتروني أو GUID. | `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> في هذا المثال، نشير إلى حسابي مستخدم في Office 365: *ميغان* و *alexw* ل *Alex*.          |
    | `Get-InformationBarrierRecipientStatus -Identity <value>` <p> يمكنك استخدام أي قيمة تعرف المستخدم بشكل فريد، مثل الاسم أو الاسم المستعار أو الاسم المميز أو اسم المجال الماجد أو عنوان البريد الإلكتروني أو GUID.|`Get-InformationBarrierRecipientStatus -Identity jeanp`<p> في هذا المثال، نشير إلى حساب واحد في Office 365: *Office 365.* |

2. راجع النتائج لمعرفة ما إذا كان قد تم تعيين سياسات حاجز المعلومات، ونهج المقطع (الشرائح) التي ينتمي إليها المستخدم (المستخدمون).

3. لإزالة مستخدم من مقطع يتأثر بعوائق المعلومات، قم بتحديث معلومات ملف تعريف المستخدم [في Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).

4. انتظر حوالي 30 دقيقة حتى يحدث FwdSync. أو قم بتشغيل `Start-InformationBarrierPoliciesApplication` الأمر cmdlet لتطبيق كل سياسات حاجز المعلومات النشطة.

## <a name="issue-the-information-barrier-application-process-is-taking-too-long"></a>المشكلة: تستغرق عملية تطبيق حاجز المعلومات وقتا طويلا جدا

بعد تشغيل **الأمر cmdlet Start-InformationBarrierPoliciesApplication** ، تستغرق العملية وقتا طويلا جدا للانتهاء.

### <a name="what-to-do"></a>ما يجب فعله

ضع في اعتبارك أنه عند تشغيل الأمر cmdlet الخاص بتطبيق النهج، يتم تطبيق نهج حاجز المعلومات (أو إزالتها)، للمستخدم حسب المستخدم، لكل الحسابات في مؤسستك. إذا كان لديك عدد كبير من المستخدمين، سيستغرق الأمر بعض الوقت ل المعالجة. (كمرشاد عام، تستغرق معالجة 5000 حساب مستخدم ساعة تقريبا.)

1. استخدم **الأمر cmdlet Get-InformationBarrierPoliciesApplicationStatus** للتحقق من حالة تطبيق النهج الأخير.

    |**لعرض تطبيق النهج الأخير**|**لعرض حالة كل تطبيقات النهج**|
    |:---------------------------------------------|:---------------------------------------------|
    | `Get-InformationBarrierPoliciesApplicationStatus` | `Get-InformationBarrierPoliciesApplicationStatus -All $true` |

    سيعرض هذا معلومات حول ما إذا كان تطبيق النهج قد اكتمل أو فشل أو كان في وضع التقدم.

2. استنادا إلى نتائج الخطوة السابقة، يمكنك اتباع إحدى الخطوات التالية:
  
    |**الحالة**|**الخطوة التالية**|
    |:---------|:------------|
    | **لم يتم البدء** | إذا مر أكثر من 45 دقيقة منذ تشغيل الأمر **cmdlet Start-InformationBarrierPoliciesApplication** ، فراجع سجل التدقيق لمعرفة ما إذا كانت هناك أي أخطاء في تعريفات النهج، أو سبب آخر لعدم بدء التطبيق. |
    | **فشل** | إذا فشل التطبيق، فراجع سجل التدقيق. راجع أيضا الشرائح والسياسات. هل تم تعيين أي مستخدمين إلى أكثر من مقطع واحد؟ هل تم تعيين أكثر من مقطع واحد على شكل poliicy؟ إذا لزم الأمر، قم بتحرير [الشرائح](information-barriers-edit-segments-policies.md#edit-a-segment) و [/أو تحرير](information-barriers-edit-segments-policies.md#edit-a-policy) النهج، ثم قم بتشغيل **الأمر cmdlet Start-InformationBarrierPoliciesApplication** مرة أخرى. |
    | **التقدم** | إذا كان التطبيق لا يزال قيد التقدم، فاسمح له بالمزيد من الوقت لإكماله. إذا كانت هناك عدة أيام، فاجمع سجلات التدقيق، ثم اتصل بالدعم. |

## <a name="issue-information-barrier-policies-are-not-being-applied-at-all"></a>المشكلة: لا يتم تطبيق سياسات حاجز المعلومات على الإطلاق

في هذه الحالة، لديك شرائح معرفة ونهج حاجز معلومات محددة وقد حاولت تطبيق هذه السياسات. ومع ذلك، عند تشغيل `Get-InformationBarrierPoliciesApplicationStatus` الأمر cmdlet، يمكنك رؤية فشل تطبيق النهج هذا.

### <a name="what-to-do"></a>ما يجب فعله

تأكد من أن مؤسستك لا تملك [Exchange دفتر](/exchange/address-books/address-book-policies/address-book-policies) Exchange في مكانها. ستمنع هذه السياسات تطبيق سياسات حاجز المعلومات.

1. الاتصال إلى [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. تشغيل [الأمر Cmdlet Get-AddressBookPolicy](/powershell/module/exchange/get-addressbookpolicy) ، ومراجعة النتائج.

    |**النتائج**|**الخطوة التالية**|
    |:----------|:------------|
    | Exchange إدراج سياسات دفتر العنوان | [إزالة سياسات دفتر العنوان](/exchange/address-books/address-book-policies/remove-an-address-book-policy) |
    | لا توجد أي سياسات دفتر عنوان |مراجعة سجلات التدقيق لمعرفة سبب فشل تطبيق النهج |

3. [عرض حالة حسابات المستخدمين أو الشرائح أو النهج أو تطبيق النهج](information-barriers-policies.md#view-status-of-user-accounts-segments-policies-or-policy-application).

## <a name="issue-information-barrier-policy-not-applied-to-all-designated-users"></a>المشكلة: لا يتم تطبيق نهج حاجز المعلومات على جميع المستخدمين المعينين

بعد تحديد الشرائح، ونهج حاجز المعلومات المحددة، ومحاولة تطبيق هذه النهج، قد تجد أن النهج ينطبق على بعض المستلمين، وليس على الآخرين.
عند تشغيل `Get-InformationBarrierPoliciesApplicationStatus` الأمر cmdlet، ابحث في الإخراج عن نص مثل هذا.

> الهوية: `<application guid>`
>
> إجمالي المستلمين: 81527
>
> المستلمون الفاشلون: 2
>
> فئة الفشل: بلا
>
> الحالة: مكتمل

### <a name="what-to-do"></a>ما يجب فعله

1. ابحث في سجل التدقيق عن `<application guid>`. يمكنك نسخ رمز PowerShell هذا وتعديله للمتغيرات.

```powershell
$DetailedLogs = Search-UnifiedAuditLog -EndDate <yyyy-mm-ddThh:mm:ss>  -StartDate <yyyy-mm-ddThh:mm:ss> -RecordType InformationBarrierPolicyApplication -ResultSize 1000 |?{$_.AuditData.Contains(<application guid>)} 
```

2. تحقق من الإخراج التفصيلي من سجل التدقيق لقيم الحقول `"UserId"` و `"ErrorDetails"` . سيمنحك هذا سبب الفشل. يمكنك نسخ رمز PowerShell هذا وتعديله للمتغيرات.

```powershell
   $DetailedLogs[1] |fl
```

على سبيل المثال:

> "UserId": User1
>
>"ErrorDetails":"Status: IBPolicyConflict. خطأ: تعارض مقطع IB "المقطع id1" ومشرط IB "المقطع id2" ولا يمكن تعيينه إلى المستلم.

3. عادة، ستكتشف أنه قد تم تضمين مستخدم في أكثر من مقطع واحد. يمكنك إصلاح ذلك عن طريق تحديث `-UserGroupFilter` القيمة في `OrganizationSegments`.

4. إعادة تطبيق سياسات حاجز المعلومات باستخدام هذه الإجراءات [سياسات "حواجز المعلومات](information-barriers-policies.md#part-3-apply-information-barrier-policies)".

## <a name="resources"></a>الموارد

- [تعريف سياسات لعوائق المعلومات في Microsoft Teams](information-barriers-policies.md)
- [عوائق المعلومات](information-barriers.md)