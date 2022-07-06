---
title: استخدام التدقيق (متميز) للتحقق من الحسابات المخترقة
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: استخدم إجراء تدقيق علبة البريد MailItemsAccessed لإجراء التحقيقات الجنائية لحسابات المستخدمين المخترقة.
ms.openlocfilehash: a2c6d8030ba90f213f665036157b3efe0c267e80
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629454"
---
# <a name="use-microsoft-purview-audit-premium-to-investigate-compromised-accounts"></a>استخدام Microsoft Purview Audit (Premium) للتحقيق في الحسابات المخترقة

حساب مستخدم مخترق (يسمى أيضا *تولي الحساب*) هو نوع من الهجوم عندما يحصل المهاجم على حق الوصول إلى حساب مستخدم ويعمل كمستخدم. تسبب هذه الأنواع من الهجمات أحيانا ضررا أكثر مما قد يكون المهاجم مقصودا. عند التحقق من حسابات البريد الإلكتروني المخترقة، يجب أن تفترض أن بيانات البريد قد تم اختراقها أكثر مما يمكن الإشارة إليه من خلال تتبع حالة الحضور الفعلي للمهاجم. استنادا إلى نوع البيانات في رسائل البريد الإلكتروني، يجب أن تفترض أن المعلومات الحساسة قد تم اختراقها أو مواجهة غرامات تنظيمية ما لم تتمكن من إثبات عدم كشف المعلومات الحساسة. على سبيل المثال، تواجه المؤسسات المنظمة ل HIPAA غرامات كبيرة إذا كان هناك دليل على كشف معلومات صحة المرضى (PHI). في هذه الحالات، من غير المحتمل أن يكون المهاجمون مهتمين ب PHI، ولكن لا يزال يتعين على المؤسسات الإبلاغ عن انتهاكات البيانات ما لم تتمكن من إثبات خلاف ذلك.

لمساعدتك في التحقق من حسابات البريد الإلكتروني المخترقة، نقوم الآن بتدقيق عمليات الوصول إلى بيانات البريد بواسطة بروتوكولات البريد والعملاء باستخدام إجراء تدقيق علبة البريد *MailItemsAccessed* . سيساعد هذا الإجراء المدقق الجديد المحققين على فهم انتهاكات بيانات البريد الإلكتروني بشكل أفضل ويساعدك على تحديد نطاق الاختراقات لعناصر بريد معينة قد يتم اختراقها. الهدف من استخدام إجراء التدقيق الجديد هذا هو التجريد من الأدلة الجنائية للمساعدة في التأكيد على أنه لم يتم اختراق جزء معين من بيانات البريد. إذا تمكن مهاجم من الوصول إلى جزء معين من البريد، Exchange Online يدقق الحدث على الرغم من عدم وجود إشارة إلى قراءة عنصر البريد.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>إجراء تدقيق علبة البريد MailItemsAccessed

يعد إجراء MailItemsAccessed الجديد جزءا من وظيفة [التدقيق (Premium)](advanced-audit.md) الجديدة. وهو جزء من [تدقيق علبة بريد Exchange](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) ويتم تمكينه بشكل افتراضي للمستخدمين الذين تم تعيين ترخيص Office 365 أو Microsoft 365 E5 لهم أو للمؤسسات التي لها اشتراك التوافق في Microsoft 365 E5 إضافي.

يغطي إجراء تدقيق علبة البريد MailItemsAccessed كافة بروتوكولات البريد: POP وIMAP و MAPI وEWS Exchange ActiveSync وREST. كما يغطي كلا النوعين من الوصول إلى البريد: *المزامنة* *والربط*.

### <a name="auditing-sync-access"></a>تدقيق الوصول إلى المزامنة

يتم تسجيل عمليات المزامنة فقط عند الوصول إلى علبة بريد بواسطة إصدار سطح المكتب من عميل Outlook لنظام التشغيل Windows أو Mac. أثناء عملية المزامنة، يقوم هؤلاء العملاء عادة بتنزيل مجموعة كبيرة من عناصر البريد من السحابة إلى كمبيوتر محلي. حجم التدقيق لعمليات المزامنة كبير. لذلك، بدلا من إنشاء سجل تدقيق لكل عنصر بريد تمت مزامنته، نقوم بإنشاء حدث تدقيق لمجلد البريد الذي يحتوي على عناصر تمت مزامنتها ونفترض أن *كافة* عناصر البريد في المجلد المتزامن قد تم اختراقها. يتم تسجيل نوع الوصول في حقل OperationProperties لسجل التدقيق.

راجع الخطوة 2 في [قسم استخدام سجلات التدقيق MailItemsAccessed للتحقيقات الجنائية](#use-mailitemsaccessed-audit-records-for-forensic-investigations) للحصول على مثال لعرض نوع الوصول إلى المزامنة في سجل تدقيق.

### <a name="auditing-bind-access"></a>تدقيق الوصول إلى الربط

عملية الربط هي وصول فردي إلى رسالة بريد إلكتروني. للوصول إلى الربط، سيتم تسجيل InternetMessageId للرسائل الفردية في سجل التدقيق. يقوم إجراء التدقيق MailItemsAccessed بربط العمليات ثم تجميعها في سجل تدقيق واحد. يتم تجميع كافة عمليات الربط التي تحدث ضمن فاصل زمني مدته دقيقتين في سجل تدقيق واحد في حقل المجلدات ضمن الخاصية AuditData. يتم تعريف كل رسالة تم الوصول إليها بواسطة InternetMessageId الخاص بها. يتم عرض عدد عمليات الربط التي تم تجميعها في السجل في الحقل OperationCount في الخاصية AuditData.

راجع الخطوة 4 في [قسم استخدام سجلات التدقيق MailItemsAccessed للتحقيقات الجنائية](#use-mailitemsaccessed-audit-records-for-forensic-investigations) للحصول على مثال لعرض نوع الوصول إلى الربط في سجل تدقيق.

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>تقييد سجلات التدقيق MailItemsAccessed

إذا تم إنشاء أكثر من 1000 سجل تدقيق MailItemsAccessed في أقل من 24 ساعة، فسيتوقف Exchange Online عن إنشاء سجلات التدقيق لنشاط MailItemsAccessed. عند تقييد علبة بريد، لن يتم تسجيل نشاط MailItemsAccessed لمدة 24 ساعة بعد تقييد علبة البريد. إذا تم تقييد علبة البريد، فمن المحتمل أن يكون قد تم اختراق علبة البريد خلال هذه الفترة. سيتم استئناف تسجيل نشاط MailItemsAccessed بعد فترة 24 ساعة.

إليك بعض الأمور التي يجب أخذها في الاعتبار حول التقييد:

- يتم تقييد أقل من 1٪ من جميع علب البريد في Exchange Online
- عند تقييد علبة بريد، لا يتم تدقيق سجلات التدقيق لنشاط MailItemsAccessed فقط. لا تتأثر إجراءات تدقيق علبة البريد الأخرى.
- يتم تقييد علب البريد لعمليات الربط فقط. لا يتم تقييد سجلات التدقيق لعمليات المزامنة.
- إذا كانت علبة البريد مقيدة، فيمكنك على الأرجح افتراض وجود نشاط MailItemsAccessed لم يتم تسجيله في سجلات التدقيق.

راجع الخطوة 1 في [قسم استخدام سجلات التدقيق MailItemsAccessed للتحقيقات الجنائية](#use-mailitemsaccessed-audit-records-for-forensic-investigations) للحصول على مثال لعرض الخاصية IsThrottled في سجل تدقيق.

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>استخدام سجلات التدقيق MailItemsAccessed للتحقيقات الجنائية

ينشئ تدقيق علبة البريد سجلات تدقيق للوصول إلى رسائل البريد الإلكتروني بحيث يمكنك أن تكون واثقا من عدم اختراق رسائل البريد الإلكتروني. لهذا السبب، في الظروف التي لم نتمكن فيها من التأكد من الوصول إلى بعض البيانات، نفترض أنه تم ذلك عن طريق تسجيل كل نشاط الوصول إلى البريد.

عادة ما يتم استخدام سجلات التدقيق MailItemsAccessed لأغراض الطب الشرعي بعد حل خرق البيانات وإخلاء المهاجم. لبدء التحقيق الخاص بك، يجب تحديد مجموعة علب البريد التي تم اختراقها وتحديد الإطار الزمني عندما كان المهاجم لديه حق الوصول إلى علب البريد في مؤسستك. بعد ذلك، يمكنك استخدام **Search-UnifiedAuditLog** أو **Search-MailboxAuditLog** cmdlets في [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) للبحث في سجلات التدقيق التي تتوافق مع خرق البيانات.

يمكنك تشغيل أحد الأوامر التالية للبحث عن سجلات التدقيق MailItemsAccessed:

**سجل التدقيق الموحد**:

```powershell
Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000
```

**سجل تدقيق علبة البريد**:

```powershell
Search-MailboxAuditLog -Identity <user> -StartDate 01/06/2020 -EndDate 01/20/2020 -Operations MailItemsAccessed -ResultSize 1000 -ShowDetails
```

> [!TIP]
> أحد الاختلافات الأساسية بين هذين الأمرين cmdlets حيث يمكنك استخدام أمر cmdlet **Search-UnifiedAuditLog** للبحث عن سجلات التدقيق للنشاط الذي يقوم به مستخدم واحد أو أكثر. وذلك لأن *UserIds* هي معلمة متعددة القيم. يبحث أمر cmdlet **Search-MailboxAuditLog** في سجل تدقيق علبة البريد عن مستخدم واحد.

فيما يلي خطوات استخدام سجلات التدقيق MailItemsAccessed للتحقيق في هجوم مستخدم تم اختراقه. تظهر كل خطوة بناء جملة الأمر ل Cmdlets **Search-UnifiedAuditLog** أو **Search-MailboxAuditLog** .

1. تحقق مما إذا كان قد تم تقييد علبة البريد. إذا كان الأمر كذلك، فهذا يعني أن بعض سجلات تدقيق علبة البريد لم تكن لتسجل. في حالة أن أي سجلات تدقيق تحتوي على "IsThrottled" هي "True"، يجب أن تفترض أنه لمدة 24 ساعة بعد إنشاء هذا السجل، وأنه لم يتم تدقيق أي وصول إلى علبة البريد وأنه تم اختراق كافة بيانات البريد.

   للبحث عن سجلات MailItemsAccessed حيث تم تقييد علبة البريد، قم بتشغيل الأمر التالي:

   **سجل التدقيق الموحد**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **سجل تدقيق علبة البريد**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. تحقق من أنشطة المزامنة. إذا كان المهاجم يستخدم عميل بريد إلكتروني لتنزيل الرسائل في علبة بريد، يمكنه قطع اتصال الكمبيوتر بالإنترنت والوصول إلى الرسائل محليا دون التفاعل مع الخادم. في هذه الحالة، لن يتمكن تدقيق علبة البريد من تدقيق هذه الأنشطة.

   للبحث عن سجلات MailItemsAccessed حيث تم الوصول إلى عناصر البريد بواسطة عملية مزامنة، قم بتشغيل الأمر التالي:

   **سجل التدقيق الموحد**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **سجل تدقيق علبة البريد**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. تحقق من أنشطة المزامنة لتحديد حدوث أي منها في نفس السياق الذي يستخدمه المهاجم للوصول إلى علبة البريد. يتم تعريف السياق وتمييزه بواسطة عنوان IP الخاص بالكمبيوتر العميل المستخدم للوصول إلى علبة البريد وبروتوكول البريد. لمزيد من المعلومات، راجع [تحديد سياقات الوصول لقسم سجلات التدقيق المختلفة](#identifying-the-access-contexts-of-different-audit-records) .

   استخدم الخصائص المذكورة أدناه للتحقيق. توجد هذه الخصائص في خاصية AuditData أو OperationProperties. إذا حدث أي من عمليات المزامنة في نفس سياق نشاط المهاجم، فافترض أن المهاجم قام بمزامنة كافة عناصر البريد مع العميل الخاص به، مما يعني أنه قد تم اختراق علبة البريد بأكملها على الأرجح.

   <br>

   ****

   |الخاصيه|الوصف|
   |---|---|
   |ClientInfoString|يصف البروتوكول والعميل (يتضمن الإصدار)|
   |ClientIPAddress|عنوان IP لجهاز العميل.|
   |معرف جلسة العمل|يساعد معرف الجلسة على تمييز إجراءات المهاجم مقابل أنشطة المستخدم اليومية على الحساب نفسه (مفيد للحسابات المخترقة)|
   |Userid|UPN للمستخدم الذي يقرأ الرسالة.|
   |

4. تحقق من وجود أنشطة الربط. بعد تنفيذ الخطوتين 2 والخطوة 3، يمكنك أن تكون واثقا من أنه سيتم التقاط جميع الوصولات الأخرى إلى رسائل البريد الإلكتروني من قبل المهاجم في سجلات التدقيق MailItemsAccessed التي تحتوي على خاصية MailAccessType بقيمة "ربط".

   للبحث عن سجلات MailItemsAccessed حيث تم الوصول إلى عناصر البريد بواسطة عملية ربط، قم بتشغيل الأمر التالي.

   **سجل التدقيق الموحد**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **سجل تدقيق علبة البريد**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   يتم تعريف رسائل البريد الإلكتروني التي تم الوصول إليها بواسطة معرف رسالة الإنترنت الخاصة بها. يمكنك أيضا التحقق لمعرفة ما إذا كانت أي سجلات تدقيق لها نفس سياق تلك الخاصة بنشاط المهاجم الآخر. لمزيد من المعلومات، راجع [تحديد سياقات الوصول لقسم سجلات التدقيق المختلفة](#identifying-the-access-contexts-of-different-audit-records) .

   يمكنك استخدام بيانات التدقيق لعمليات الربط بطريقتين مختلفتين:

   - يمكنك الوصول إلى كل رسائل البريد الإلكتروني التي قام المهاجم بالوصول إليها أو تجميعها باستخدام InternetMessageId للعثور عليها ثم التحقق لمعرفة ما إذا كانت أي من هذه الرسائل تحتوي على معلومات حساسة.
   - استخدم InternetMessageId للبحث في سجلات التدقيق المتعلقة بمجموعة من رسائل البريد الإلكتروني التي يحتمل أن تكون حساسة. يعد هذا الأمر مفيدا إذا كنت مهتما ببعض الرسائل فقط.

## <a name="filtering-of-duplicate-audit-records"></a>تصفية سجلات التدقيق المكررة

تتم تصفية سجلات التدقيق المكررة لعمليات الربط نفسها التي تحدث في غضون ساعة من بعضها البعض لإزالة ضوضاء التدقيق. تتم أيضا تصفية عمليات المزامنة في فواصل زمنية مدتها ساعة واحدة. يحدث الاستثناء لعملية إلغاء التكرار هذه إذا كانت أي من الخصائص الموضحة في الجدول التالي مختلفة بالنسبة إلى InternetMessageId نفسه. إذا كانت إحدى هذه الخصائص مختلفة في عملية مكررة، يتم إنشاء سجل تدقيق جديد. يتم وصف هذه العملية بمزيد من التفصيل في القسم التالي.

<br>

****

|الخاصيه|الوصف|
|---|---|
|ClientIPAddress|عنوان IP لكمبيوتر العميل.|
|ClientInfoString|بروتوكول العميل، العميل المستخدم للوصول إلى علبة البريد.|
|ParentFolder|مسار المجلد الكامل لعنصر البريد الذي تم الوصول إليه.|
|Logon_type|نوع تسجيل الدخول للمستخدم الذي نفذ الإجراء. أنواع تسجيل الدخول (وقيمة قائمة التعداد المقابلة لها) هي المالك (0) أو مسؤول (1) أو المفوض (2).|
|MailAccessType|ما إذا كان الوصول عملية ربط أو مزامنة.|
|MailboxUPN|UPN الخاص بعلبة البريد حيث توجد الرسالة التي تتم قراءتها.|
|User|UPN للمستخدم الذي يقرأ الرسالة.|
|معرف جلسة العمل|يساعد معرف جلسة العمل على التمييز بين إجراءات المهاجم وأنشطة المستخدم اليومية في علبة البريد نفسها (في حالة اختراق الحساب) لمزيد من المعلومات حول جلسات العمل، راجع [سياق نشاط المهاجم ضمن جلسات العمل في Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801).|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>تحديد سياقات الوصول لسجلات التدقيق المختلفة

من الشائع أن يتمكن المهاجم من الوصول إلى علبة بريد في الوقت نفسه الذي يصل فيه مالك علبة البريد إليها. للتمييز بين الوصول من قبل المهاجم ومالك علبة البريد، هناك خصائص سجل التدقيق التي تحدد سياق الوصول. كما هو موضح سابقا، عندما تكون قيم هذه الخصائص مختلفة، حتى عند حدوث النشاط ضمن الفاصل الزمني للتجميع، يتم إنشاء سجلات تدقيق منفصلة. في المثال التالي، هناك ثلاثة سجلات تدقيق مختلفة. يتم تمييز كل واحد من خلال خصائص معرف جلسة العمل و ClientIPAddress. كما يتم التعرف على الرسائل التي تم الوصول إليها.

<br>

****

|سجل التدقيق 1|سجل التدقيق 2|سجل التدقيق 3|
|---|---|---|
|ClientIPAddress **1**<br/>SessionId **2**|ClientIPAddress **2**<br/>SessionId **2**|ClientIPAddress **1**<br/>SessionId **3**|
|InternetMessageId **A**<br/>InternetMessageId **D**<br/>InternetMessageId **E**<br/>InternetMessageId **F**<br/>|InternetMessageId **A**<br/>InternetMessageId **C**|InternetMessageId **B**|
|

إذا كانت أي من الخصائص المدرجة في الجدول في [المقطع السابق](#filtering-of-duplicate-audit-records) مختلفة، يتم إنشاء سجل تدقيق منفصل لتعقب السياق الجديد. سيتم فرز عمليات الوصول إلى سجلات تدقيق منفصلة وفقا للسياق الذي حدث فيه النشاط.

على سبيل المثال، في سجلات التدقيق الموضحة في لقطة الشاشة التالية، على الرغم من أننا نصل إلى البريد من EWSEditor وOWA في وقت واحد، يتم تجميع نشاط الوصول في سجلات تدقيق مختلفة اعتمادا على السياق الذي تم فيه الوصول. في هذه الحالة، يتم تعريف السياق بقيم مختلفة للخاصية ClientInfoString.

![سجلات تدقيق مختلفة استنادا إلى السياق.](../media/MailItemsAccessed4.png)

فيما يلي بناء جملة الأمر الموضح في لقطة الشاشة السابقة:

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
