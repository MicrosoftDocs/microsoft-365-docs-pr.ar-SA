---
title: بدء استخدام إدارة الوصول المتميزة
description: استخدم هذه المقالة لمعرفة المزيد حول تمكين إدارة الوصول المتميز وتكوينها في Microsoft Purview.
keywords: Microsoft 365، وMicrosoft Purview، والامتثال، وإدارة الوصول المتميز
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
ms.openlocfilehash: d53058e89fc1830b6f35eef270d84b99f2cc9f74
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626326"
---
# <a name="get-started-with-privileged-access-management"></a>بدء استخدام إدارة الوصول المتميزة

ترشدك هذه المقالة من خلال تمكين وتكوين إدارة الوصول المتميزة في مؤسستك. يمكنك استخدام <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a> أو Exchange Management PowerShell لإدارة الوصول المتميز واستخدامه.

## <a name="before-you-begin"></a>قبل البدء

قبل البدء في إدارة الوصول المتميز، يجب عليك تأكيد [اشتراكك في Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) وأي وظائف إضافية. للوصول إلى إدارة الوصول المتميز واستخدامها، يجب أن يكون لدى مؤسستك أحد الاشتراكات أو الوظائف الإضافية التالية:

- اشتراك Microsoft 365 E5 (إصدار مدفوع أو تجريبي)
- اشتراك Microsoft 365 E3 (أو اشتراك Office 365 E3 + اشتراك Enterprise Mobility and Security E3) + الوظيفة الإضافية التوافق في Microsoft 365 E5
- أي اشتراك Microsoft 365 أو Office 365 أو Exchange أو SharePoint أو OneDrive for Business + الوظيفة الإضافية Microsoft 365 E5 Insider Risk Management
- اشتراك Microsoft 365 A5 (إصدار مدفوع أو تجريبي)
- اشتراك Microsoft 365 A3 (أو اشتراك Office 365 A3 + اشتراك Enterprise Mobility and Security A3) + الوظيفة الإضافية لتوافق Microsoft A5
- أي اشتراك Microsoft 365 أو Office 365 أو Exchange أو SharePoint أو OneDrive for Education + الوظيفة الإضافية Microsoft 365 A5 Insider Risk Management
- اشتراك Office 365 Enterprise E5 (إصدار مدفوع أو تجريبي)
- Office 365 Enterprise اشتراك E3 + الوظيفة الإضافية خدمات الامتثال المتطورة في Office 365 (لم تعد متوفرة للاشتراكات الجديدة، راجع الملاحظة)

يجب تعيين أحد التراخيص أعلاه للمستخدمين الذين يقومون بإرسال طلبات إدارة الوصول المتميزة والاستجابة لها.

> [!IMPORTANT]
> لم يعد يتم بيع خدمات الامتثال المتطورة في Office 365 كتشتراك مستقل. عند انتهاء صلاحية الاشتراكات الحالية، يجب على العملاء الانتقال إلى أحد الاشتراكات أعلاه، والتي تحتوي على نفس ميزات التوافق أو ميزات التوافق الإضافية.

إذا لم يكن لديك خطة Office 365 Enterprise E5 موجودة وتريد تجربة إدارة الوصول المتميزة، يمكنك [إضافة Microsoft 365](/office365/admin/try-or-buy-microsoft-365) إلى اشتراكك الحالي في Office 365 أو [التسجيل للحصول على إصدار تجريبي](https://www.microsoft.com/microsoft-365/enterprise) من Microsoft 365 Enterprise E5.

## <a name="enable-and-configure-privileged-access-management"></a>تمكين وتكوين إدارة الوصول المتميز

اتبع هذه الخطوات لإعداد واستخدام الوصول المتميز في مؤسستك:

- [الخطوة 1: إنشاء مجموعة موافق](privileged-access-management-configuration.md#step1)

    قبل البدء في استخدام الوصول المتميز، حدد من يحتاج إلى سلطة الموافقة للطلبات الواردة للوصول إلى المهام المرتفعة والمتميزة. يمكن لأي مستخدم يشكل جزءا من مجموعة الموافقين الموافقة على طلبات الوصول. تم تمكين هذه المجموعة عن طريق إنشاء مجموعة أمان ممكنة للبريد في Office 365.

- [الخطوة 2: تمكين الوصول المتميز](privileged-access-management-configuration.md#step2)

    يجب تمكين الوصول المتميز بشكل صريح في Office 365 مع مجموعة الموافق الافتراضية، بما في ذلك مجموعة من حسابات النظام التي تريد استبعادها من التحكم في الوصول إلى إدارة الوصول المتميز.

- [الخطوة 3: إنشاء نهج وصول](privileged-access-management-configuration.md#step3)

    يتيح لك إنشاء نهج الموافقة تحديد متطلبات الموافقة المحددة المحددة في نطاق المهام الفردية. خيارات نوع الموافقة هي **تلقائية** أو **يدوية**.

- [الخطوة 4: إرسال/الموافقة على طلبات الوصول المتميزة](privileged-access-management-configuration.md#step4)

    بمجرد تمكينه، يتطلب الوصول المتميز موافقات لأي مهمة لها نهج موافقة مقترن محدد. بالنسبة للمهام المضمنة في نهج الموافقة، يجب على المستخدمين طلب الموافقة على الوصول ومنحهم أذونات ضرورية لتنفيذ المهمة.

بعد منح الموافقة، يمكن للمستخدم الطالب تنفيذ المهمة المقصودة وسيقوم الوصول المتميز بتخويل المهمة وتنفيذها نيابة عن المستخدم. تظل الموافقة صالحة للمدة المطلوبة (المدة الافتراضية هي 4 ساعات)، حيث يمكن للمطالب تنفيذ المهمة المقصودة عدة مرات. يتم تسجيل جميع عمليات التنفيذ هذه وإتاحتها للتدقيق الأمني والتوافقي.

> [!NOTE]
> إذا كنت تريد استخدام Exchange Management PowerShell لتمكين الوصول المتميز وتكوينه، فاتبع الخطوات الواردة في [الاتصال Exchange Online PowerShell باستخدام المصادقة متعددة العوامل](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) للاتصال Exchange Online PowerShell باستخدام بيانات اعتماد Office 365. لا تحتاج إلى تمكين المصادقة متعددة العوامل لمؤسستك لاستخدام الخطوات لتمكين الوصول المتميز أثناء الاتصال Exchange Online PowerShell. يؤدي الاتصال بالمصادقة متعددة العوامل إلى إنشاء رمز مميز للمصادقة يستخدمه الوصول المتميز لتوقيع طلباتك.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>الخطوة 1: إنشاء مجموعة موافق

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**"**</a> > **إضافة مجموعة للمجموعات**".

3. حدد **مجموعة الأمان الممكنة للبريد** ثم أكمل حقول **"الاسم**" و" **عنوان البريد الإلكتروني للمجموعة**" و" **الوصف** " للمجموعة الجديدة.

4. حفظ المجموعة. قد يستغرق تكوين المجموعة بالكامل وظهورها في مركز مسؤولي Microsoft 365 بضع دقائق.

5. حدد مجموعة الموافق الجديد وحدد **التحرير** لإضافة مستخدمين إلى المجموعة.

6. حفظ المجموعة.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>الخطوة 2: تمكين الوصول المتميز

### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤول Microsoft 365

1. سجل الدخول [إلى مسؤول Microsoft 365 Center](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، انتقل إلى **إعدادات الإعدادات** >  >  &**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. تمكين عنصر تحكم **المطالبة بالموافقة للمهام المتميزة** .

4. تعيين مجموعة الموافق التي أنشأتها في الخطوة 1 كمجموعة **الموافقين الافتراضيين**.

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
> يتم توفير ميزة حسابات النظام لضمان إمكانية عمل بعض الأتمتة داخل مؤسستك دون اعتماد على الوصول المتميز، ومع ذلك يوصى بأن تكون هذه الاستثناءات استثنائية ويجب الموافقة على تلك المسموح بها وتدقيقها بانتظام.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>الخطوة 3: إنشاء نهج وصول

يمكنك إنشاء وتكوين ما يصل إلى 30 نهج وصول متميز لمؤسستك.

### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤول Microsoft 365

1. سجل الدخول [إلى مسؤول Microsoft 365 Center](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز مسؤول، انتقل إلى **"إعدادات الإعدادات** >  > **"**&**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد **تكوين النهج** وحدد **إضافة نهج**.

5. من الحقول المنسدلة، حدد القيم المناسبة لمؤسستك:

    **نوع النهج**: المهمة أو الدور أو مجموعة الأدوار

    **نطاق النهج**: Exchange

    **اسم النهج**: حدد من النهج المتوفرة

    **نوع الموافقة**: يدوي أو تلقائي

    **مجموعة الموافقة**: حدد مجموعة الموافقين التي تم إنشاؤها في الخطوة 1

6. حدد **"إنشاء"** ثم **"إغلاق**". قد يستغرق تكوين النهج وتمكينه بالكامل بضع دقائق.

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لإنشاء نهج الموافقة وتحديده، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

على سبيل المثال:

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>الخطوة 4: إرسال/الموافقة على طلبات الوصول المتميزة

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>طلب تخويل رفع المستوى لتنفيذ المهام المتميزة

طلبات الوصول المتميز صالحة لمدة تصل إلى 24 ساعة بعد إرسال الطلب. إذا لم تتم الموافقة عليها أو رفضها، تنتهي صلاحية الطلبات ولا تتم الموافقة على الوصول.

#### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤول Microsoft 365

1. سجل الدخول إلى [مسؤول Microsoft 365 Center](https://admin.microsoft.com) باستخدام بيانات الاعتماد الخاصة بك.

2. في مركز مسؤول، انتقل إلى **"إعدادات الإعدادات** >  > **"**&**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد **طلب جديد**. من الحقول المنسدلة، حدد القيم المناسبة لمؤسستك:

    **نوع الطلب**: المهمة أو الدور أو مجموعة الأدوار

    **نطاق الطلب**: Exchange

    **طلب:** تحديد من النهج المتوفرة

    **المدة (الساعات):** عدد ساعات الوصول المطلوب. لا يوجد حد لعدد الساعات التي يمكن طلبها.

    **التعليقات**: الحقل النصي للتعليقات المتعلقة بطلب الوصول

5. حدد **"حفظ"** ثم **"إغلاق**". سيتم إرسال طلبك إلى مجموعة الموافق عبر البريد الإلكتروني.

#### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

قم بتشغيل الأمر التالي في Exchange Online PowerShell لإنشاء طلب موافقة وإرساله إلى مجموعة الموافق:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

على سبيل المثال:

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>عرض حالة طلبات رفع الامتيازات

بعد إنشاء طلب الموافقة، يمكن مراجعة حالة طلب رفع الامتيازات في مركز الإدارة أو في Exchange Management PowerShell باستخدام معرف الطلب المقترن.

#### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد الخاصة بك.

2. في مركز الإدارة، انتقل إلى **إعدادات الإعدادات** >  >  &**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد **"عرض** " لتصفية الطلبات المرسلة حسب حالة **Pending** أو **Approved** أو **Denied** أو **Customer Lockbox** .

#### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

قم بتشغيل الأمر التالي في Exchange Online PowerShell لعرض حالة طلب الموافقة لمعرف طلب معين:

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

على سبيل المثال:

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>الموافقة على طلب تخويل رفع الامتيازات

عند إنشاء طلب موافقة، يتلقى أعضاء مجموعة الموافقين ذات الصلة إعلاما بالبريد الإلكتروني ويمكنهم الموافقة على الطلب المقترن بمعرف الطلب. يتم إعلام الطالب بالموافقة على الطلب أو رفضه عبر رسالة البريد الإلكتروني.

#### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد الخاصة بك.

2. في مركز الإدارة، انتقل إلى **إعدادات الإعدادات** >  >  &**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد طلبا مدرجا لعرض التفاصيل واتخاذ إجراء بشأن الطلب.

5. حدد **"موافقة** " للموافقة على الطلب أو حدد **"رفض** " لرفض الطلب. يمكن أن يتم إبطال الوصول إلى الطلبات التي تمت الموافقة عليها مسبقا عن طريق تحديد **"إبطال".**

#### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

للموافقة على طلب تخويل رفع، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

على سبيل المثال:

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

لرفض طلب تخويل رفع الامتيازات، قم بتشغيل الأمر التالي في Exchange Online PowerShell:

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

على سبيل المثال:

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>حذف نهج وصول متميز في Office 365

إذا لم تعد هناك حاجة إليه في مؤسستك، يمكنك حذف نهج وصول متميز.

### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز الإدارة، انتقل إلى **إعدادات الإعدادات** >  >  &**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. حدد **إدارة نهج الوصول والطلبات**.

4. حدد **تكوين النهج**.

5. حدد النهج الذي تريد حذفه، ثم حدد **"إزالة النهج**".

6. حدد **"إغلاق**".

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لحذف نهج وصول متميز، قم بتشغيل الأمر التالي في Exchange Online Powershell:

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>تعطيل الوصول المتميز في Office 365

إذا لزم الأمر، يمكنك تعطيل إدارة الوصول المتميز لمؤسستك. لا يؤدي تعطيل الوصول المتميز إلى حذف أي نهج موافقة مقترنة أو مجموعات موافقين.

### <a name="in-the-microsoft-365-admin-center"></a>في مركز مسؤولي Microsoft 365

1. سجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك.

2. في مركز مسؤول، انتقل إلى **"إعدادات الإعدادات** >  > **"**&**الوصول المتميز للخصوصية**<a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank"></a> > .

3. تمكين **المطالبة بالموافقة على التحكم بالوصول المتميز** .

### <a name="in-exchange-management-powershell"></a>في Exchange Management PowerShell

لتعطيل الوصول المتميز، قم بتشغيل الأمر التالي في Exchange Online Powershell:

```PowerShell
Disable-ElevatedAccessControl
```
