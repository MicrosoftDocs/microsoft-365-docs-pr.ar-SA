---
title: طلبات مربع تأمين العميل
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom: admindeeplinkMAC
description: تعرف على طلبات مربع تأمين العميل التي تسمح لك بالتحكم في كيفية وصول مهندس دعم Microsoft إلى بياناتك عندما تخوض مشكلة ما.
ms.openlocfilehash: 532b1b78c40725fa3558768a6b65beda9b8e05b2
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/15/2022
ms.locfileid: "63566512"
---
# <a name="customer-lockbox-in-office-365"></a>مربع تأمين العميل في Office 365

توفر هذه المقالة إرشادات النشر والتكوين ل Customer Lockbox. يدعم Customer Lockbox الطلبات للوصول إلى البيانات في Exchange Online SharePoint عبر الإنترنت OneDrive for Business. للتوصية بدعم خدمات أخرى، أرسل طلبا في ["مدخل الملاحظات](https://feedbackportal.microsoft.com)".

لمعرفة خيارات ترخيص المستخدمين للاستفادة من عروض Microsoft 365، راجع Microsoft 365 إرشادات الترخيص [لتوافق & الأمان](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

يضمن Customer Lockbox أنه لا يمكن ل Microsoft الوصول إلى المحتوى الخاص بك للقيام بعمليات الخدمة دون الحصول على موافقتك الصريحة. يوفر لك Customer Lockbox عملية سير عمل الموافقة التي تستخدمها Microsoft لضمان السماح فقط للطلبات المعتمدة بالوصول إلى المحتوى الخاص بك. لمعرفة المزيد حول عملية سير عمل Microsoft، راجع [إدارة الوصول المتميز في](privileged-access-management-solution-overview.md) Microsoft 365.

في بعض الأحيان، يساعد مهندسو Microsoft في استكشاف الأخطاء وإصلاحها التي تنشأ عن الخدمة. عادة، يصحح المهندسون المشاكل باستخدام أدوات البحث عن بعد وتصحيح الأخطاء الموسعة التي تستخدمها Microsoft في مكان خدماتها. ومع ذلك، تتطلب بعض الحالات مهندس Microsoft للوصول إلى المحتوى لتحديد السبب الجذر وإصلاح المشكلة. يتطلب Customer Lockbox من المهندس طلب الوصول منك كخطوة نهائية في سير عمل الموافقة. يوفر لك ذلك خيار الموافقة على الطلب أو رفضه لمنظمتك، وتوفير إمكانية التحكم بالوصول المباشر إلى المحتوى.

### <a name="customer-lockbox-overview-video"></a>فيديو نظرة عامة حول مربع تأمين العميل

> [!VIDEO https://www.microsoft.com/videoplayer/embed/8fecf10b-1f03-4849-8b67-76d3d2a43f26?autoplay=false]

## <a name="customer-lockbox-workflow"></a>سير عمل مربع تأمين العميل

توضح هذه الخطوات سير العمل النموذجي عندما يبدأ أحد مهندسي Microsoft طلب مربع تأمين العميل:

1. يواجه شخص ما في المؤسسة مشكلة في علبة Microsoft 365 البريد الخاصة به.

2. بعد أن يقوم المستخدم باصلاح المشكلة وإصلاحها، ولكن لا يمكنه إصلاحها، يفتح طلب دعم باستخدام دعم Microsoft.

3. يراجع مهندس دعم Microsoft طلب الخدمة ويحدد الحاجة إلى الوصول إلى مستأجر المؤسسة لإصلاح المشكلة في Exchange Online.

4. يقوم مهندس دعم Microsoft بتسجيل الدخول إلى أداة طلب مربع تأمين العميل، كما يقوم بطلب الوصول إلى البيانات الذي يتضمن اسم المستأجر الخاص المؤسسة، رقم طلب الخدمة، والوقت المقدر الذي يحتاج إليه المهندس للوصول إلى البيانات.

5. بعد موافقة مدير دعم Microsoft على الطلب، يرسل Customer Lockbox إلى الموافق المعين في المؤسسة إعلاما بالبريد الإلكتروني حول طلب الوصول المعلق من Microsoft.

    ![مثال على إعلام بريد إلكتروني في مربع تأمين العميل.](../media/CustomerLockbox1.png)

   يمكن لأي شخص تم تعيين دور مسؤول الوصول إلى [مربع](/office365/admin/add-users/about-admin-roles) تأمين العميل في مركز مسؤولي Microsoft 365 الموافقة على طلبات مربع تأمين العميل.

6. وي سجل الموافق الدخول إلى مركز مسؤولي Microsoft 365 ويوافق على الطلب. تقوم هذه الخطوة بتشغيل إنشاء سجل تدقيق متوفر من خلال البحث في سجل التدقيق. لمزيد من المعلومات، راجع [تدقيق طلبات مربع تأمين العميل](#auditing-customer-lockbox-requests).

   إذا رفض العميل الطلب أو لم يوافق على الطلب في غضون 12 ساعة، تنتهي صلاحية الطلب ولا يتم منح أي حق وصول لمهندس Microsoft.

   > [!IMPORTANT]
   > لا تتضمن Microsoft أي ارتباطات في إعلامات البريد الإلكتروني في Customer Lockbox التي تتطلب منك تسجيل الدخول إلى Office 365.

7. بعد موافقة الموافق من المؤسسة على الطلب، يتلقى مهندس Microsoft رسالة الموافقة، ويسجل دخوله إلى المستأجر في Exchange Online، ويصلح مشكلة العميل. لدى مهندسي Microsoft المدة المطلوبة لإصلاح المشكلة التي يتم بعدها إبطال الوصول تلقائيا.

> [!NOTE]
> يتم تسجيل جميع الإجراءات التي ينفذها أحد مهندسي Microsoft في سجل التدقيق. يمكنك البحث عن سجلات التدقيق هذه ومراجعتها.

## <a name="turn-customer-lockbox-requests-on-or-off"></a>تشغيل طلبات مربع تأمين العميل أو إيقاف تشغيلها

يمكنك تشغيل عناصر تحكم مربع تأمين العميل في مركز مسؤولي Microsoft 365. عند تشغيل Customer Lockbox، يجب على Microsoft الحصول على موافقة مؤسستك قبل الوصول إلى أي من محتويات المستأجر.

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي تم تعيين دور مسؤول عام له أو معتمد الوصول إلى **مربع** [https://admin.microsoft.com](https://admin.microsoft.com) تأمين العميل، انتقل إلى ثم سجل دخولك.

2. اختر **الإعدادات** >  **أو الإعدادات** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**الأمان & الخصوصية**</a>.

3. حدد **الأمان & الخصوصية**، ثم حدد **مربع تأمين العميل** في العمود الأيمن. تحقق من **خانة الاختيار طلب الموافقة** على كل طلبات الوصول إلى البيانات واحفظ التغييرات التي تم إدخالها على هذه الميزة.

    ![طلب الموافقة على Customer Lockbox](../media/CustomerLockbox4-new.png)

## <a name="approve-or-deny-a-customer-lockbox-request"></a>الموافقة على طلب مربع تأمين العميل أو رفضه

1. باستخدام حساب العمل أو المؤسسة الدراسية الذي تم تعيين دور مسؤول عام له أو معتمد الوصول إلى **مربع** [https://admin.microsoft.com](https://admin.microsoft.com) تأمين العميل، انتقل إلى ثم سجل دخولك.

2. اختر **دعم > طلبات مربع تأمين العميل**.

    ![انقر فوق دعم، ثم فوق طلبات مربع تأمين العميل.](../media/CustomerLockbox5.png)

    يتم عرض قائمة بطلبات مربع تأمين العميل.

    ![قائمة طلبات مربع تأمين العميل.](../media/CustomerLockbox6.png)

3. حدد طلب مربع تأمين العميل، ثم اختر **موافقة** أو **رفض**.

    ![الموافقة على طلبات مربع تأمين العميل.](../media/CustomerLockbox7.png)

    تظهر رسالة تأكيد حول الموافقة على طلب مربع تأمين العميل.

    ![رفض طلبات مربع تأمين العميل.](../media/CustomerLockbox8.png)

> [!NOTE]
> استخدم Set-AccessToCustomerDataRequest cmdlet للموافقة على طلبات مربع تأمين Microsoft 365 العميل أو رفضها أو إلغائها التي تتحكم في إمكانية وصول مهندسي دعم Microsoft إلى بياناتك. لمزيد من المعلومات، راجع [Set-AccessToCustomerDataRequest](/powershell/module/exchange/set-accesstocustomerdatarequest).

## <a name="auditing-customer-lockbox-requests"></a>تدقيق طلبات مربع تأمين العميل

يتم تسجيل سجلات التدقيق التي تتوافق مع طلبات مربع تأمين العميل في Microsoft 365 التدقيق. يمكنك الوصول إلى هذه السجلات باستخدام أداة البحث [في سجل التدقيق](search-the-audit-log-in-security-and-compliance.md) في مركز التوافق في Microsoft 365. يتم أيضا تسجيل الإجراءات المتعلقة بقبول طلب مربع تأمين العميل والإجراءات التي ينفذها مهندسو Microsoft (عند الموافقة على طلبات الوصول) أو رفضها في سجل التدقيق. يمكنك البحث عن سجلات التدقيق هذه ومراجعتها.

### <a name="search-the-audit-log-for-activity-related-to-customer-lockbox-requests"></a>البحث في سجل التدقيق عن النشاط المتعلق بطلبات مربع تأمين العميل

قبل أن تتمكن من استخدام سجل التدقيق لتعقب طلبات مربع تأمين العميل، هناك بعض الخطوات التي يجب اتخاذها لإعداد تسجيل التدقيق، بما في ذلك تعيين أذونات للبحث في سجل التدقيق. لمزيد من المعلومات، راجع [إعداد التدقيق الأساسي في Microsoft 365](set-up-basic-audit.md). بعد إكمال الإعداد، استخدم هذه الخطوات لإنشاء استعلام بحث في سجل التدقيق لإرجاع سجلات التدقيق ذات الصلة ب Customer Lockbox:

1. انتقل إلى <https://compliance.microsoft.com>.
  
2. سجل الدخول باستخدام حساب تم تعيين الأذونات المناسبة له للبحث في سجل التدقيق.

3. في الجزء الأيسر من مركز التوافق، اختر **تدقيق**.

    يتم **عرض** علامة التبويب بحث على **صفحة** التدقيق.

    ![صفحة البحث في سجل التدقيق.](../media/auditlogsearch1.png)
  
4. تكوين معايير البحث التالية:

   1. **تاريخ البدء** **وتاريخ الانتهاء**. حدد تاريخا ونطاقا من الوقت لعرض الأحداث التي وقعت خلال تلك الفترة.  

   2. **الأنشطة**. اترك هذا الحقل فارغا بحيث يرجع البحث سجلات التدقيق لكل الأنشطة. وهذا ضروري لإرجاع أي سجلات تدقيق ذات صلة بطلبات مربع تأمين العميل والنشاط المناظر الذي يقوم به مهندسو Microsoft.

   3. **المستخدمون**. اترك هذا الحقل فارغاً.

   4. **ملف أو مجلد أو موقع**. اترك هذا الحقل فارغاً.

5. انقر **فوق** بحث لتشغيل البحث باستخدام معايير البحث.

    يتم عرض نتائج البحث بعد لحظات قليلة. وستضاف المزيد من نتائج البحث إلى الصفحة حتى اكتمال عملية البحث.

6. انقر فوق الرأس في عمود **النشاط** لفرز النتائج أبجديا استنادا إلى القيم في **عمود** النشاط.

7. قم بالتمرير لأسفل وابحث عن سجلات التدقيق التي لها نشاط **Set-AccessToCustomerDataRequest**. ترتبط السجلات التي بها هذا النشاط بموافق في مؤسستك على الموافقة على طلب مربع تأمين العميل أو رفضه.

8. بدلا من ذلك، انقر فوق الرأس في **عمود المستخدم** لفرز النتائج أبجديا باستخدام القيم في **عمود** المستخدم. ابحث عن قيمة **Microsoft Operator**، التي تشير إلى الأنشطة التي يقوم بها أحد مهندسي Microsoft استجابة لطلب مربع تأمين العميل المعتمد. يعرض **عمود** النشاط الإجراء الذي ينفذه المهندس.

      ![التصفية على "Microsoft Operator" لعرض سجلات التدقيق](../media/CustomerLockbox10.png)

9. في قائمة النتائج، انقر فوق سجل تدقيق لعرضه.

### <a name="export-the-audit-log-search-results"></a>تصدير نتائج البحث في سجل التدقيق

يمكنك أيضا تصدير نتائج البحث في سجل التدقيق إلى ملف CSV ثم فتح الملف في Excel لاستخدام إمكانات التصفية والفرز لتسهيل عملية البحث عن سجلات التدقيق ذات الصلة بطلب الوصول إلى مربع تأمين العميل وعرضها.

لتصدير سجلات التدقيق، استخدم الخطوات السابقة للبحث في سجل التدقيق. عند اكتمال البحث، حدد تصدير > **تنزيل** كل النتائج في أعلى صفحة نتائج البحث. عند اكتمال عملية التصدير، يمكنك تنزيل ملف CSV إلى الكمبيوتر المحلي. للحصول على إرشادات أكثر تفصيلا، راجع تصدير سجلات سجل التدقيق وتكوينها [وعرضها](export-view-audit-log-records.md).

بعد تنزيل الملف، يمكنك فتحه في Excel ثم التصفية في العمود عمليات لعرض سجلات التدقيق لأنشطة **Set-AccessToCustomerDataRequest**. يمكنك أيضا التصفية على العمود **UserIds** (باستخدام القيمة **Microsoft Operator**) لعرض سجلات التدقيق الخاصة بالأنشطة التي ينفذها مهندسو Microsoft.

> [!NOTE]
> عند عرض سجلات التدقيق في ملف CSV، يتم احتواء معلومات إضافية في **العمود بيانات** التدقيق. يتم احتواء المعلومات الموجودة في هذا العمود في كائن JSON، الذي يحتوي على خصائص متعددة تم تكوينها كزوج خاصية *:قيمة* مفصولة بفااصات. يمكنك استخدام ميزة تحويل JSON في محرر Power Query في Excel لتقسيم كل خاصية في كائن JSON في عمود **بيانات** التدقيق إلى أعمدة متعددة بحيث يكون لكل خاصية عمودها الخاص. يسهل هذا الأمر تفسير هذه المعلومات. للحصول على إرشادات مفصلة، راجع [تنسيق سجل التدقيق الذي تم تصديره باستخدام محرر Power Query](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="use-powershell-to-search-and-export-audit-records"></a>استخدام PowerShell للبحث عن سجلات التدقيق وتصديرها

البديل لاستخدام أداة البحث في التدقيق في مركز التوافق في Microsoft 365 هو تشغيل أمر cmdlet [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) في Exchange Online PowerShell. إحدى فوائد استخدام PowerShell هي أنه يمكنك البحث بشكل خاص عن أنشطة **Set-AccessToCustomerDataRequest** أو الأنشطة التي ينفذها مهندسو Microsoft والم ذات الصلة بطلب مربع تأمين العميل.

بعد الاتصال [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)، قم بتشغيل أحد الأوامر التالية. استبدل العنصر النائب نطاق تاريخ معين.

#### <a name="search-for-set-accesstocustomerdatarequest-activities"></a>البحث عن Set-AccessToCustomerDataRequest أخرى

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -Operations Set-AccessToCustomerDataRequest
```

#### <a name="search-for-activities-performed-by-microsoft-engineers"></a>البحث عن الأنشطة التي يقوم بها مهندسو Microsoft

```powershell
Search-UnifiedAuditLog -StartDate xx/xx/xxxx -EndDate xx/xx/xxxx -UserIds "Microsoft Operator"
```

لمزيد من المعلومات والأمثلة، راجع [استخدام PowerShell للبحث عن سجلات سجل التدقيق وتصديرها](export-view-audit-log-records.md#use-powershell-to-search-and-export-audit-log-records).

لقد وفرنا أيضا برنامج PowerShell النصي الذي يمكنك استخدامه للبحث في سجل التدقيق وتصدير النتائج إلى ملف CSV. لمزيد من المعلومات، راجع [استخدام برنامج PowerShell النصي للبحث في سجل التدقيق](audit-log-search-script.md).

### <a name="audit-record-for-a-customer-lockbox-request"></a>سجل التدقيق لطلب مربع تأمين العميل

عندما يوافق شخص في مؤسستك على طلب مربع تأمين العميل أو يرفضه، يتم تسجيل سجل التدقيق في سجل التدقيق يحتوي على المعلومات التالية.

| خاصية سجل التدقيق| الوصف|
|:---------- |:----------|
| التاريخ       | التاريخ والوقت الذي تمت فيه الموافقة على طلب مربع تأمين العميل أو رفضه.
| عنوان IP | عنوان IP للجهاز الذي استخدمه الموافق للموافقة على طلب أو رفضه. |
| User       | حساب الخدمة BOXServiceAccount@\[customerforest.prod.outlook.com\].            |
| Activity   | Set-AccessToCustomerDataRequest; هذا هو نشاط التدقيق الذي يتم تسجيله عند الموافقة على طلب مربع تأمين العميل أو رفضه.                                |
| عنصر       | Guid الخاص بطلب مربع تأمين العميل                             |

تعرض لقطة الشاشة التالية مثالا لسجل تدقيق يتوافق مع طلب مربع تأمين العميل المعتمد. إذا تم رفض طلب مربع تأمين العميل، فقيمة معلمة **الموافقة ستكون** **رفض**.

![سجل التدقيق لطلب مربع تأمين العميل المعتمد.](../media/CustomerLockbox9.png)

### <a name="audit-record-for-an-action-performed-by-a-microsoft-engineer"></a>سجل التدقيق لإجراء ينفذه أحد مهندسي Microsoft

يتم تسجيل الإجراءات التي ينفذها أحد مهندسي Microsoft بعد الموافقة على طلب مربع تأمين العميل (وقد يؤدي ذلك إلى الوصول إلى محتوى العميل) في سجل التدقيق. تحتوي هذه السجلات على المعلومات التالية.

| خاصية سجل التدقيق| الوصف|
|:---------- |:----------|
| التاريخ       | وقت التاريخ الذي تم فيه تنفيذ الإجراء. سيكون الوقت الذي تم فيه تنفيذ هذا الإجراء في غضون 4 ساعات من وقت الموافقة على طلب مربع تأمين العميل.              |
| عنوان IP | عنوان IP لمهندس جهاز Microsoft المستخدم. |
| User       | Microsoft عامل التشغيل؛ تشير هذه القيمة إلى أن السجل مرتبط بطلب مربع تأمين العميل.                                  |
| Activity   | اسم النشاط الذي ينفذه مهندس Microsoft.|
| عنصر       | \<empty\>                                             |

## <a name="frequently-asked-questions"></a>الأسئلة المتكررة

#### <a name="which-microsoft-365-services-does-customer-lockbox-apply-to"></a>ما Microsoft 365 الخدمات التي تنطبق عليها Customer Lockbox؟

مربع تأمين العميل مدعوم حاليا في Exchange Online SharePoint عبر الإنترنت OneDrive for Business.

#### <a name="is-customer-lockbox-available-to-all-customers"></a>هل يتوفر مربع تأمين العميل لجميع العملاء؟

يتم تضمين Customer Lockbox مع اشتراكات Microsoft 365 أو Office 365 E5 ويمكن إضافتها إلى خطط أخرى باستخدام اشتراك في حماية المعلومات والتوافق أو اشتراك في الوظائف الإضافية للتوافق المتقدم. لمزيد من المعلومات، [راجع الخطط والأسعار](https://products.office.com/business/office-365-enterprise-e5-business-software) .

#### <a name="what-is-customer-content"></a>ما هو محتوى العميل؟

محتوى العميل هو البيانات التي أنشأها مستخدمو Microsoft 365 والتطبيقات. تتضمن أمثلة محتوى العميل ما يلي:

- مرفقات البريد الإلكتروني أو البريد الإلكتروني

- SharePoint محتويات الموقع

- معلومات في جزء SharePoint ملف

- Skype for Business ملف العرض التقديمي

- الرسائل الفورية (IM) أو المحادثات الصوتية

- بيانات التخزين النقطي أو بيانات التخزين الهيكلية التي تم إنشاؤها بواسطة العميل (على سبيل المثال، SQL الحاويات)

- معلومات الأمان التي يملكها العميل (على سبيل المثال، الشهادات ومفاتيح التشفير وكلمات المرور)

- الاستدلالات، وكل الاستدلاليات اللاحقة، إذا بقي محتوى العميل

لمزيد من المعلومات حول محتوى العميل في Office 365، راجع Office 365 [مركز الثقة](https://products.office.com/business/office-365-trust-center-privacy/).

#### <a name="who-is-notified-when-there-is-a-request-to-access-my-content"></a>روبوت Who إعلامك عند وجود طلب للوصول إلى المحتوى الخاص بك؟

يتم إعلام المسؤولين العامين وأي شخص تم تعيينه لدور مسؤول الوصول إلى مربع تأمين العميل. هؤلاء هم أيضا نفس المستخدمين الذين يمكنهم الموافقة على طلبات مربع تأمين العميل.

#### <a name="who-can-approve-or-reject-these-requests-in-my-organization"></a>روبوت Who قبول هذه الطلبات أو رفضها في المؤسسة؟

يمكن للمسؤولين العامين وأي شخص تم تعيين دور مسؤول الوصول إلى مربع تأمين العميل له الموافقة على طلبات مربع تأمين العميل. يتحكم العملاء في تعيينات الدور هذه في مؤسساتهم.

#### <a name="how-do-i-opt-in-to-customer-lockbox"></a>كيف يمكنني الاشتراك في Customer Lockbox؟

يمكن للمسؤول العام تمكين مربع تأمين العميل وتكوينه في Microsoft 365 أو <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">مركز مسؤولي Microsoft 365</a>.

#### <a name="if-i-approve-a-customer-lockbox-request-what-can-the-engineer-do-and-how-will-i-know-what-the-microsoft-engineer-did"></a>إذا وافقت على طلب مربع تأمين العميل، فما الذي يمكن للمهندس فعله وكيف يمكنني معرفة ما قام به مهندس Microsoft؟

بعد الموافقة على طلب مربع تأمين العميل، منح مهندس Microsoft هذه الامتيازات الضرورية للوصول إلى محتوى العميل باستخدام cmdlets المعتمدة مسبقا. يتم تسجيل الإجراءات التي قام بها مهندسو Microsoft استجابة لطلبات مربع تأمين العميل ويمكن الوصول إليها في سجل التدقيق في مركز التوافق & الأمان.

#### <a name="how-do-i-know-that-microsoft-follows-the-approval-process"></a>كيف يمكنني معرفة أن Microsoft تتبع عملية الموافقة؟

يمكنك الإشارة التعارضية إلى إعلامات الموافقة على البريد الإلكتروني المرسلة إلى المسؤولين والموافقين في مؤسستك باستخدام محفوظات طلبات مربع [تأمين العميل في مركز مسؤولي Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

يتم تضمين Customer Lockbox في تقرير تدقيق [SOC 1 SSAE 16 الأخير](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports). لمزيد من التفاصيل، يمكنك العثور على أحدث التقارير في [Microsoft Service Trust Portal](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuide?command=Download&downloadType=Document&downloadId=91592749-e86a-43ac-801e-121382614681&docTab=4ce99610-c9c0-11e7-8c2c-f908a777fa4d_SOC%20%2F%20SSAE%2016%20Reports).

#### <a name="can-microsoft-modify-the-list-of-approvers-for-my-tenant-if-not-how-is-it-prevented"></a>هل يمكن لشركة Microsoft تعديل قائمة الموافقين للمستأجر الخاص بى؟ إذا لم يكن الأمر كذلك، فكيف يتم منعه؟

يمكن للمسؤول العام فقط في مؤسستك تحديد من يمكنه الموافقة على طلبات مربع تأمين العميل. وهذا يعني أن أعضاء مجموعة المسؤول العام فقط في Azure Active Directory يمكنهم تحديد الأشخاص الذين يمكنهم الموافقة على الطلب. يتم إدارة عضوية مجموعة المسؤول العام في Azure Active Directory من قبل مؤسستك فقط.

#### <a name="what-if-i-need-more-information-about-a-content-access-request-to-approve-it"></a>ماذا لو احتجت إلى مزيد من المعلومات حول طلب الوصول إلى المحتوى للموافقة عليه؟

يحتوي كل طلب مربع تأمين عميل على Microsoft 365 طلب خدمة. يمكنك الاتصال بدعم Microsoft والإشارة إلى رقم الخدمة هذا للحصول على مزيد من المعلومات حول الطلب.

#### <a name="when-a-customer-lockbox-request-is-approved-how-long-are-the-permissions-valid"></a>عند الموافقة على طلب مربع تأمين العميل، ما المدة التي تكون فيها الأذونات صالحة؟

حاليا، الحد الأقصى لأذونات الوصول الممنوحة لمهندس Microsoft هو 4 ساعات. يمكن لمهندس Microsoft أيضا طلب فترة زمنية أقصر.

#### <a name="how-can-i-get-a-history-of-all-customer-lockbox-requests"></a>كيف يمكنني الحصول على محفوظات لكل طلبات مربع تأمين العملاء؟

يتم عرض كل طلبات مربع تأمين [العميل في مركز مسؤولي Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339).

#### <a name="how-do-i-correlate-the-content-access-requests-with-the-related-audit-logs"></a>كيف يمكنني ربط طلبات الوصول إلى المحتوى بسجلات التدقيق ذات الصلة؟

يحتوي موجز نشاط مركز التوافق على أنشطة سجل مربع تأمين العميل. يمكن للعملاء إنشاء إشارة تتقاطع مع أنشطة سجل Customer Lockbox من موجز النشاط مقابل طلب البريد الإلكتروني الذي يتلقونه.

#### <a name="what-happens-when-a-customer-doesnt-respond-to-a-customer-lockbox-request"></a>ماذا يحدث عندما لا يستجيب أحد العملاء لطلب مربع تأمين العميل؟

تكون مدة طلبات مربع تأمين العميل 12 ساعة بشكل افتراضي. إذا لم ترد على طلب في غضون 12 ساعة، تنتهي صلاحية الطلب.

#### <a name="what-does-microsoft-do-when-a-customer-rejects-a-customer-lockbox-request"></a>ماذا تفعل Microsoft عندما يرفض أحد العملاء طلب مربع تأمين العميل؟

إذا رفض أحد العملاء طلب مربع تأمين العميل، فلا يحدث أي وصول إلى محتوى العميل. إذا استمر مستخدم في مؤسستك في تجربة مشكلة في الخدمة تتطلب من Microsoft الوصول إلى محتوى العميل لحل المشكلة، فقد تستمر مشكلة الخدمة وستعلم Microsoft المستخدم بذلك.

#### <a name="how-do-i-set-up-alerts-whenever-a-request-has-been-approved"></a>كيف يمكنني إعداد التنبيهات كلما تمت الموافقة على طلب؟

لا يوجد خيار مضمن لتنبيه المسؤولين. ومع ذلك، يمكن للمسؤولين إعداد التنبيهات باستخدام [Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security#to-create-policies).

#### <a name="does-customer-lockbox-protect-against-data-requests-from-law-enforcement-agencies-or-other-third-parties"></a>هل يحمي مربع تأمين العميل من طلبات البيانات الواردة من أجهزة تنفيذ القانون أو جهات خارجية أخرى؟

لا. تأخذ Microsoft طلبات  الأطراف الخارجية لبيانات العملاء على محمل الجد. كموفر خدمة سحابية، تدعو Microsoft دائما إلى خصوصية بيانات العملاء. في حال الحصول على مذكرة إحضار، تحاول Microsoft دائما إعادة توجيه الطرف الثالث إلى العميل للحصول على المعلومات. (اقرأ مدونة براد سميث: [حماية بيانات العملاء من تطفل الحكومة](https://blogs.microsoft.com/blog/2013/12/04/protecting-customer-data-from-government-snooping/)). وننشر معلومات [مفصلة بشكل دوري](https://www.microsoft.com/corporate-responsibility/lerr) حول طلبات تطبيق القانون التي تتلقاها Microsoft.

لمزيد من المعلومات، راجع [مركز Microsoft Trust Center](https://www.microsoft.com/trustcenter/default.aspx) فيما يتعلق بطلبات البيانات من جهة خارجية وقسم "الكشف عن بيانات العملاء[](https://www.microsoft.com/Licensing/product-licensing/products.aspx)" في شروط الخدمات عبر الإنترنت.

#### <a name="how-does-microsoft-ensure-that-a-member-of-its-staff-doesnt-have-standing-access-to-customer-content-in-office-365-applications"></a>كيف تضمن Microsoft عدم وصول أحد أعضاء فريق العمل الدائم إلى محتوى العميل في تطبيقات Office 365 التطبيقات؟

تنفذ Microsoft إجراءات وقائية واسعة النطاق من خلال أنظمة التحكم بالوصول، ومكواد التحكم في الوصول لتحديد محاولات التحايل على أنظمة التحكم بالوصول هذه ومعالجة هذه المحاولات. Microsoft 365 مع مبادئ أقل امتياز والوصول في الوقت المناسب. وبالتالي، لا يوجد لدى أي من موظفي Microsoft الإذن بالوصول إلى محتوى العميل بشكل مستمر. إذا تم منح الإذن، فإنه يكون لمدة محدودة. 

Microsoft 365 نظام التحكم بالوصول يسمى *Lockbox* لمعالجة طلبات الأذونات التي تمنح القدرة على تنفيذ الوظائف التشغيلية و الإدارية داخل الخدمة. يجب على عامل التشغيل طلب الوصول إلى محتوى العميل باستخدام Lockbox، مما يتطلب من شخص آخر اتخاذ إجراء بشأن الطلب (على سبيل المثال، الموافقة عليه) قبل منح حق الوصول. لا يمكن أن يكون الشخص الثاني هو الواجب ويجب تعيينه للموافقة على الوصول إلى محتوى العميل. لا يحصل عامل التشغيل على حق الوصول المؤقت إلى محتوى العميل إلا إذا تمت الموافقة على الطلب. بعد انتهاء فترة الارتفاع، يبطل Lockbox الوصول.

راجع شروط الخدمات عبر [الإنترنت](https://www.microsoft.com/licensing/product-licensing/products) للحصول على مزيد من التفاصيل حول ممارسات الأمان العامة من Microsoft.

#### <a name="under-what-circumstances-do-microsoft-engineers-need-access-to-my-content"></a>ما هي الظروف التي يحتاج فيها مهندسو Microsoft إلى الوصول إلى المحتوى الخاص بك؟

السيناريو الأكثر شيوعا حيث يحتاج مهندسو Microsoft إلى الوصول إلى محتوى العميل هو عندما يقوم العميل بطلب دعم يتطلب الوصول إلى استكشاف الأخطاء وإصلاحها. المبدأ الأساسي Microsoft 365 هو أن الخدمة تعمل بدون وصول Microsoft إلى محتوى العميل. يتم تنفيذ جميع عمليات الخدمات التي تقوم بها Microsoft بشكل كامل، كما يتم التحكم في المشاركة البشرية بشكل كبير وتجريدها بعيدا عن محتوى العميل. الهدف من Microsoft 365 هو الوصول إلى محتوى العميل لدعم الخدمة غير مطلوب حتى يوافق العميل على طلب معين للوصول إلى Microsoft.

#### <a name="i-already-thought-my-data-was-secure-with-the-microsoft-cloud-so-why-do-i-need-customer-lockbox"></a>لقد اعتقدت بالفعل أن بياناتي آمنة مع سحابة Microsoft، فلماذا أحتاج إلى Customer Lockbox؟

يوفر Customer Lockbox طبقة تحكم إضافية من خلال توفير إمكانية منح العملاء تفويض وصول صريح لعمليات الخدمة. من خلال إظهار وجود إجراءات لتخويل صريح بالوصول إلى البيانات، يساعد Customer Lockbox أيضا العملاء على الوفاء ببعض التزامات التوافق مثل HIPAA و FEDRAMP.
