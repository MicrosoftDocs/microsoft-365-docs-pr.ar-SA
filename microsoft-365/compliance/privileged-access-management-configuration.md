---
title: بدء استخدام إدارة الوصول المتميزة
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: ''
description: استخدم هذه المقالة لمعرفة المزيد حول تمكين إدارة الوصول المتميزة وتكوينها في Office 365.
ms.openlocfilehash: fd7216b09b17f7f900a9aee98059918a1796fe19
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/01/2022
ms.locfileid: "63565933"
---
# <a name="get-started-with-privileged-access-management"></a>بدء استخدام إدارة الوصول المتميزة

يرشدك هذا الموضوع من خلال تمكين إدارة الوصول المتميزة وتكوينها في مؤسستك. يمكنك استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">إما مركز مسؤولي Microsoft 365 أو</a> Exchange Management PowerShell لإدارة الوصول المميز واستخدامه.

## <a name="before-you-begin"></a>قبل البدء

قبل بدء استخدام إدارة الوصول المتميزة، يجب عليك تأكيد اشتراكك في [Microsoft 365 وأي من](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) الوظائف الإضافية. للوصول إلى إدارة الوصول المتميزة واستخدامها، يجب أن يكون لدى مؤسستك أحد الاشتراكات أو الوظائف الإضافية التالية:

- Microsoft 365 E5 الاشتراك (إصدار مدفوع أو تجريبي)
- Microsoft 365 E3 اشتراك (أو Office 365 E3 اشتراك + Enterprise Mobility و Security E3) + التوافق في Microsoft 365 E5 الإضافية
- أي Microsoft 365 أو Office 365 أو Exchange أو SharePoint أو OneDrive for Business اشتراك + Microsoft 365 E5 إدارة مخاطر Insider
- Microsoft 365 A5 الاشتراك (إصدار مدفوع أو تجريبي)
- Microsoft 365 A3 اشتراك (أو Office 365 A3 اشتراك + Enterprise Mobility and Security A3) + الوظائف الإضافية توافق Microsoft A5
- أي Microsoft 365 اشتراك Office 365 أو Exchange أو SharePoint أو OneDrive للتعليم + Microsoft 365 A5 الإضافية إدارة مخاطر Insider
- Office 365 Enterprise E5 (إصدار مدفوع أو تجريبي)
- Office 365 Enterprise اشتراك E3 + خدمات الامتثال المتطورة في Office 365 الإضافية (لم تعد متوفرة للاشتراكات الجديدة، راجع ملاحظة)

يجب تعيين أحد التراخيص أعلاه للمستخدمين الذين يجيبون عن طلبات إدارة الوصول المتميزة ويستجيبون لها.

> [!IMPORTANT]
> خدمات الامتثال المتطورة في Office 365 يتم بيعه لاشتراك مستقل. عند انتهاء صلاحية الاشتراكات الحالية، يجب على العملاء الانتقال إلى أحد الاشتراكات أعلاه، التي تحتوي على نفس ميزات التوافق أو ميزات التوافق الإضافية.

إذا لم يكن لديك خطة Office 365 Enterprise E5 وتريد تجربة إدارة الوصول المتميزة، يمكنك إضافة [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) إلى اشتراك Office 365 الحالي أو التسجيل للحصول على الإصدار التجريبي من Microsoft 365 Enterprise E5.[](https://www.microsoft.com/microsoft-365/enterprise)

## <a name="enable-and-configure-privileged-access-management"></a>تمكين إدارة الوصول المتميزة وتكوينها

اتبع هذه الخطوات لإعداد الوصول المميز واستخدامه في مؤسستك:

- [الخطوة 1: إنشاء مجموعة الموافق](privileged-access-management-configuration.md#step1)

    قبل البدء باستخدام حق الوصول إلى الامتيازات، حدد من يحتاج إلى مرجع الموافقة للطلبات الواردة للوصول إلى المهام المتميزة والمرتفعة. يمكن لأي مستخدم يكون جزءا من مجموعة الموافقين الموافقة على طلبات الوصول. يتم تمكين هذه المجموعة عن طريق إنشاء مجموعة أمان تمكينها للبريد في Office 365.

- [الخطوة 2: تمكين الوصول المميز](privileged-access-management-configuration.md#step2)

    يجب تمكين الوصول المميز بشكل صريح في Office 365 مجموعة الموافق الافتراضية، بما في ذلك مجموعة من حسابات النظام التي تريد استبعادها من عنصر تحكم الوصول المتميز لإدارة الوصول.

- [الخطوة 3: إنشاء نهج وصول](privileged-access-management-configuration.md#step3)

    يسمح لك إنشاء نهج الموافقة بتحديد متطلبات الموافقة المحددة التي يتم تحديد نطاقها في المهام الفردية. خيارات نوع الموافقة هي **تلقائي** أو **يدوي**.

- [الخطوة 4: إرسال/الموافقة على طلبات الوصول المتميزة](privileged-access-management-configuration.md#step4)

    بمجرد تمكين الوصول المميز، يتطلب الحصول على موافقات لأي مهمة تم تعريف نهج الموافقة المقترن بها. بالنسبة للمهام المضمنة في نهج الموافقة، يجب أن يطلب المستخدمون الحصول على الموافقة على الوصول ومنحهم الإذن اللازم لتنفيذ المهمة.

بعد منح الموافقة، يمكن للمستخدم الذي يطلب تنفيذ المهمة المقصودة وسيفوض الوصول المميز المهمة وينفذها نيابة عن المستخدم. تظل الموافقة صالحة للمدة المطلوبة (المدة الافتراضية هي 4 ساعات)، حيث يمكن للمطلب تنفيذ المهمة المقصودة عدة مرات. يتم تسجيل كل عمليات التنفيذ هذه وجعلها متوفرة لتدقيق الأمان والتوافق.

> [!NOTE]
> إذا كنت تريد استخدام Exchange Management PowerShell لتمكين الوصول المتميز وتكوينه، فاتبع الخطوات في [الاتصال إلى Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) باستخدام المصادقة متعددة العوامل للاتصال ب Exchange Online PowerShell باستخدام بيانات اعتماد Office 365. لست بحاجة إلى تمكين المصادقة متعددة العوامل لمنظمتك لاستخدام الخطوات لتمكين الوصول المتميز أثناء الاتصال Exchange Online PowerShell. ينشئ الاتصال بالمصادقة متعددة العوامل رمزا مميزا لمصادقة المصادقة يتم استخدامه بواسطة الوصول المميز لتوقيع طلباتك.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>الخطوة 1: إنشاء مجموعة الموافق

1. سجل [دخولك إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**GroupsAdd**</a> >  **a group**.

3. حدد **مجموعة الأمان التي تم تمكين البريد لها** ، ثم **أكمل حقول الاسم** وعنوان **البريد الإلكتروني للمجموعة** **والوصف** للمجموعة الجديدة.

4. احفظ المجموعة. قد يستغرق تكوين المجموعة بالكامل وإظهارها في مركز مسؤولي Microsoft 365.

5. حدد مجموعة الموافق الجديد وحدد **تحرير** لإضافة مستخدمين إلى المجموعة.

6. احفظ المجموعة.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>الخطوة 2: تمكين الوصول المميز

### <a name="in-the-microsoft-365-admin-center"></a>في مسؤول Microsoft 365

1. سجل [دخولك إلى مسؤول Microsoft 365 باستخدام](https://admin.microsoft.com) بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. تمكين **عنصر التحكم يتطلب موافقات للمهام المتميزة** .

4. تعيين مجموعة الموافق التي أنشأتها في الخطوة 1 كمجموعة الموافقين **الافتراضيين**.

5. **حفظ** **وإغلاق**.

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لتمكين الوصول المتميز وتعيين مجموعة الموافق، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

على سبيل المثال:

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> يتم توفير ميزة حسابات النظام لضمان إمكانية عمل عمليات تلقائية معينة داخل مؤسستك دون الاعتماد على الوصول المتميز، ومع ذلك من المستحسن أن تكون هذه الاستثناءات استثناءات ويجب الموافقة عليها وتدقيقها بشكل منتظم.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>الخطوة 3: إنشاء نهج وصول

يمكنك إنشاء ما يصل إلى 30 من سياسات الوصول المتميزة وتكوينها لمنظمتك.

### <a name="in-the-microsoft-365-admin-center"></a>في مسؤول Microsoft 365

1. سجل [دخولك إلى مسؤول Microsoft 365 باستخدام](https://admin.microsoft.com) بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد **تكوين النهج** وحدد **إضافة نهج**.

5. من الحقول المنسدل، حدد القيم المناسبة لمنظمتك:

    **نوع النهج**: المهمة أو الدور أو مجموعة الدور

    **نطاق النهج**: Exchange

    **اسم النهج**: تحديد من النهج المتوفرة

    **نوع الموافقة**: يدوي أو تلقائي

    **مجموعة الموافقة**: تحديد مجموعة الموافقين التي تم إنشاؤها في الخطوة 1

6. حدد **إنشاء** ثم **إغلاق**. قد يستغرق تكوين النهج وتمكينه بشكل كامل بضع دقائق.

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لإنشاء نهج موافقة وتحديده، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

على سبيل المثال:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>الخطوة 4: إرسال/الموافقة على طلبات الوصول المتميزة

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>طلب تخويل رفع لتنفيذ مهام متميزة

تكون طلبات الوصول المتميز صالحة لمدة تصل إلى 24 ساعة بعد إرسال الطلب. إذا لم يتم الموافقة على الطلبات أو رفضها، تنتهي صلاحية الطلبات ولا يتم الموافقة على الوصول.

#### <a name="in-the-microsoft-365-admin-center"></a>في مسؤول Microsoft 365

1. سجل دخولك إلى مسؤول Microsoft 365 [باستخدام](https://admin.microsoft.com) بيانات الاعتماد الخاصة بك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد **طلب جديد**. من الحقول المنسدل، حدد القيم المناسبة لمنظمتك:

    **نوع الطلب**: المهمة أو الدور أو مجموعة الدور

    **نطاق الطلب**: Exchange

    **طلب:** تحديد من بين السياسات المتوفرة

    **المدة (الساعات)**: عدد الساعات المطلوبة للوصول. لا يوجد حد لعدد الساعات التي يمكن طلبها.

    **التعليقات**: حقل نصي للتعليقات ذات الصلة بطلب الوصول

5. حدد **حفظ** ثم **إغلاق**. سيتم إرسال طلبك إلى مجموعة الموافق عبر البريد الإلكتروني.

#### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

قم بتشغيل الأمر التالي في Exchange Online PowerShell لإنشاء طلب موافقة وإرساله إلى مجموعة الموافق:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

على سبيل المثال:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>عرض حالة طلبات الارتفاع

بعد إنشاء طلب موافقة، يمكن مراجعة حالة طلب رفع في مركز الإدارة أو في Exchange Management PowerShell باستخدام المقترن بم ID الطلب.

#### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل دخولك إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) بيانات الاعتماد الخاصة بك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد **عرض** لتصفية الطلبات التي تم إرسالها حسب **الحالة معلقة** أو **معتمدة أو رفض** أو **مربع تأمين** العميل. 

#### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

تشغيل الأمر التالي في Exchange Online PowerShell لعرض حالة طلب الموافقة لمعين طلب معين:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

على سبيل المثال:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>الموافقة على طلب تخويل رفع

عند إنشاء طلب موافقة، يتلقى أعضاء مجموعة الموافقين ذات الصلة إعلاما بالبريد الإلكتروني ويمكنهم الموافقة على الطلب المقترن بم ID الطلب. يتم إعلام الواطلب بطلب الموافقة أو الرفض عبر رسالة البريد الإلكتروني.

#### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل دخولك إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) بيانات الاعتماد الخاصة بك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد طلبا مدرجا لعرض التفاصيل واتخاذ إجراء بشأن الطلب.

5. حدد **موافقة** للموافقة على الطلب أو حدد **رفض** لرفض الطلب. يمكن أن يتم إبطال الوصول إلى الطلبات التي تمت الموافقة عليها مسبقا عن طريق تحديد **إبطال**.

#### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

للموافقة على طلب تخويل رفع، تشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

على سبيل المثال:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

لرفض طلب تخويل رفع، تشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

على سبيل المثال:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>حذف نهج وصول مميز في Office 365

إذا لم تعد هناك حاجة إليها في مؤسستك، يمكنك حذف نهج وصول مميز.

### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل [دخولك إلى مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. حدد **إدارة سياسات الوصول وطلباته**.

4. حدد **تكوين السياسات**.

5. حدد النهج الذي تريد حذفه، ثم حدد **إزالة النهج**.

6. حدد **إغلاق**.

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لحذف نهج وصول مميز، قم بتشغيل الأمر التالي في Exchange Online Powershell:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>تعطيل الوصول المميز في Office 365

إذا لزم الأمر، يمكنك تعطيل إدارة الوصول المتميز لمنظمتك. لا يحذف تعطيل الوصول المميز أي سياسات موافقة أو مجموعات موافقين مقترنة.

### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل دخولك إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، **انتقل إلى الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**أمان &**</a> **PrivacyPrivileged** > .

3. تمكين عنصر **التحكم يتطلب موافقات للوصول المتميز** .

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لتعطيل الوصول المميز، قم بتشغيل الأمر التالي في Exchange Online Powershell:

```PowerShell
Disable-ElevatedAccessControl
```
