---
title: تحديد ما إذا كان النشر المركزي ل الوظائف الإضافية يعمل مع مؤسستك
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b4527d49-4073-4b43-8274-31b7a3166f92
description: حدد ما إذا كان المستأجر والمستخدمون لديك يلبيون المتطلبات، بحيث يمكنك استخدام "النشر المركزي" لنشر Office إضافية.
ms.openlocfilehash: 856e48db79627e0e736c05fe0062680017e24418
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/29/2022
ms.locfileid: "64506956"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>تحديد ما إذا كان النشر المركزي ل الوظائف الإضافية يعمل مع مؤسستك

النشر المركزي هو الطريقة الموصى بها والغنية بالميزات لمعظم العملاء لنشر Office الإضافية للمستخدمين والمجموعات داخل مؤسستك. إذا كنت أحد المسؤولين، فاستخدم هذه الإرشادات لتحديد ما إذا كانت مؤسستك والمستخدمون يلبيون المتطلبات حتى تتمكن من استخدام "النشر المركزي".

يوفر النشر المركزي الفوائد التالية:

- يمكن للمسؤول نشر وظائف إضافية وتعيينها مباشرة إلى مستخدم أو عدة مستخدمين عبر مجموعة أو للجميع في المؤسسة (راجع القسم متطلبات المسؤول للحصول على المعلومات).
- عند بدء تشغيل Office ذي الصلة، يتم تنزيل الوظائف الإضافية تلقائيا. إذا كانت الوظائف الإضافية تدعم أوامر الوظائف الإضافية، تظهر هذه الوظائف الإضافية تلقائيا في الشريط ضمن Office التطبيق.
- لم تعد الوظائف الإضافية تظهر للمستخدمين إذا قام المسؤول ب إيقاف تشغيلها أو حذفها، أو إذا تمت إزالة المستخدم من Azure Active Directory أو من مجموعة تم تعيينها لها.

يدعم النشر المركزي ثلاثة الأنظمة الأساسية لسطح المكتب Windows وتطبيقات Mac Office الإنترنت. يدعم "النشر المركزي" أيضا أجهزة iOS وAndroid (Outlook الإضافية للجوال فقط).

قد يستغرق الأمر ما يصل إلى 24 ساعة حتى تظهر الوظائف الإضافية للعميل لجميع المستخدمين.

## <a name="before-you-begin"></a>قبل البدء

يتطلب النشر المركزي ل الوظائف الإضافية أن المستخدمين يستخدمون تراخيص Microsoft 365 Business (Business Basic أو Business Standard أو Business Premium) أو تراخيص Office 365 Enterprise (E1/E3/E5/F3) أو تراخيص Microsoft 365 Enterprise (E3/E5/F3) (وقد تم الدخول إلى Office باستخدام الم ID التنظيمية الخاصة بهم أو تراخيص Office 365 Education (A1/A3/A5) أو تراخيص Microsoft 365 Education (A3/A5)، كما أن لديها علب بريد Exchange Online ونشطة Exchange Online بريد. يجب أن يكون دليل اشتراكك إما في Azure Active Directory أو أن يكون منتديا به.
يمكنك عرض متطلبات معينة Office Exchange أدناه، أو استخدام مدقق توافق النشر [المركزي](#centralized-deployment-compatibility-checker).

النشر المركزي لا يدعم ما يلي:

- الوظائف الإضافية التي تستهدف Office MSI (باستثناء Outlook 2016)
- خدمة دليل في الموقع
- نشر الوظائف الإضافية إلى Exchange علبة بريد على الموقع
- نشر الوظائف الإضافية SharePoint
- Teams التطبيق
- نشر مكون نموذج عنصر (COM) أو Visual Studio أدوات Office الإضافية (VSTO).
- عمليات نشر Microsoft 365 التي لا تتضمن Exchange Online مثل SKUs: Microsoft 365 Apps for Business Microsoft 365 Apps for Enterprise.

### <a name="office-requirements"></a>Office المتطلبات

- بالنسبة ل Word Excel الوظائف PowerPoint الوظائف الإضافية، يجب أن يستخدم المستخدمون إحدى الوظائف التالية:
  - على جهاز Windows أو الإصدار 1704 أو الإصدارات الأحدث من تراخيص Microsoft 365 Business (Business Basic أو Business Standard أو Business Premium) أو تراخيص Office 365 Enterprise (E1/E3/E5/F3) أو تراخيص Microsoft 365 Enterprise (E3/E5/F3).
  - على جهاز Mac، الإصدار 15.34 أو إصدار أحدث.

- بالنسبة Outlook، يجب أن يستخدم المستخدمون أحد الخطوات التالية:
  - الإصدار 1701 أو الإصدارات الأحدث من تراخيص Microsoft 365 Business (Business Basic أو Business Standard أو Business Premium) أو تراخيص Office 365 Enterprise (E1/E3/E5/F3) أو تراخيص Microsoft 365 Enterprise (E3/E5/F3).
  - الإصدار 1808 أو الإصدارات الأحدث Office Professional Plus 2019 أو Office Standard 2019.
  - الإصدار 16.0.4494.1000 أو الإصدارات الأحدث من Office Professional Plus 2016 (MSI) أو Office Standard 2016 (MSI)\*
  - الإصدار 15.0.4937.1000 أو إصدار أحدث من Office Professional Plus 2013 (MSI) أو Office Standard 2013 (MSI)\*
  - الإصدار 16.0.9318.1000 أو إصدار Office 2016 for Mac
- الإصدار 2.75.0 أو إصدار Outlook المحمول ل iOS
- الإصدار 2.2.145 أو الإصدارات الأحدث من Outlook المحمول لنظام التشغيل Android

    *تظهر إصدارات MSI Outlook الوظائف الإضافية المثبتة من قبل المسؤول في الشريط Outlook المناسب، وليس المقطع "الوظائف الإضافية".

### <a name="exchange-online-requirements"></a>Exchange Online المتطلبات

تخزن Exchange Microsoft بيانات الوظائف الإضافية داخل مستأجر مؤسستك. يجب أن يكون المسؤول الذي ينشر الوظائف الإضافية والمستخدمون الذين يتلقون هذه الوظائف الإضافية على إصدار من Exchange Online يدعم مصادقة OAuth.

راجع مسؤول المؤسسة Exchange لمعرفة التكوين المستخدم. يمكن التحقق من اتصال OAuth لكل مستخدم باستخدام [الأمر Cmdlet Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell.

### <a name="admin-requirements"></a>متطلبات المسؤول

لكي تتمكن من نشر الوظائف الإضافية عبر "النشر المركزي"، يجب أن تكون إما مسؤول عام أو مسؤول Exchange في المؤسسة.

> [!NOTE]
> يمكن Exchange نشر إضافية إذا تم إضافة دور مسؤول التطبيق أو إذا تم تعيين  الخاصية **تسجيلات** التطبيقات إلى true في مركز إدارة Azure Active Directory كما هو موضح في الصورة التالية:
>
> ![صورة](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>مدقق توافق النشر المركزي

باستخدام مدقق توافق النشر المركزي، يمكنك التحقق مما إذا كان المستخدمون على المستأجر قد تم إعدادهم لاستخدام "النشر المركزي" ل Word Excel PowerPoint. مدقق التوافق غير مطلوب Outlook الدعم. قم [بتنزيل مدقق التوافق](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>تشغيل مدقق التوافق

1. ابدأ نافذة PowerShell.exe مرتفعة.

2. قم بتنفيذ الأمر التالي:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. تشغيل **الأمر Invoke-CompatibilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```

   يطالبك هذا الأمر ب _TenantDomain_ (على سبيل المثال _،_ TailspinToysIncorporated.onmicrosoft.com) وبيانات اعتماد _TenantAdmin_ (استخدم بيانات اعتماد المسؤول العام)، ثم يطلب الموافقة.

   > [!NOTE]
   > استنادا إلى عدد المستخدمين في المستأجر، يمكن أن يكتمل المدقق بالدقائق أو الساعات.

عند انتهاء تشغيل الأداة، تنتج ملف إخراج بتنسيق مفصول بفصول (.csv). يتم حفظ الملف في **دليل العمل الحالي** بشكل افتراضي. يحتوي ملف الإخراج على المعلومات التالية:

- اسم المستخدم
- "تعريف المستخدم" (عنوان البريد الإلكتروني للمستخدم)
- النشر المركزي جاهز - إذا كانت العناصر المتبقية صحيحة
- Office خطة - خطة Office تم ترخيصها ل
- Office تنشيط - إذا تم تنشيط Office
- علبة البريد المعتمدة - إذا كانت على علبة بريد تم تمكين OAuth لها

> [!NOTE]
> لا يتم دعم المصادقة متعددة العوامل عند استخدام الوحدة النمطية نشر مركزي في PowerShell. تعمل الوحدة النمطية فقط مع المصادقة الأساسية.

## <a name="user-and-group-assignments"></a>تعيينات المستخدمين والمجموعة

تدعم ميزة النشر المركزي حاليا معظم المجموعات التي يدعمها Azure Active Directory، بما في ذلك المجموعات Microsoft 365 وقوائم التوزيع ومجموعات الأمان.

> [!NOTE]
> مجموعات الأمان غير المعتمدة للبريد غير معتمدة حاليا.

يدعم النشر المركزي التعيينات لمستخدمين فرديين ومجموعات وكل شخص في المستأجر. يدعم النشر المركزي المستخدمين في مجموعات المستوى الأعلى أو المجموعات التي لا تملك مجموعات أصل، ولكن لا يدعم المستخدمين في المجموعات المتداخلة أو المجموعات التي لديها مجموعات أصل.

أطلع على المثال التالي حيث تم تعيين علياء وشيلة والمجموعة قسم المبيعات إلى أحد الوظائف الإضافية. نظرا لأن قسم مبيعات West Coast هو مجموعة متداخلة، لا يتم تعيين برت وفريد إلى أحد الوظائف الإضافية.

![MicrosoftTeams-image](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>معرفة ما إذا كانت المجموعة تحتوي على مجموعات متداخلة

أسهل طريقة للكشف عما إذا كانت المجموعة تحتوي على مجموعات متداخلة هي عرض بطاقة جهة اتصال المجموعة ضمن Outlook. إذا أدخلت اسم المجموعة ضمن الحقل **إلى** في رسالة بريد إلكتروني ثم حددت اسم المجموعة عند حلها، فإنه سيعرض لك ما إذا كانت تحتوي على مستخدمين أو مجموعات متداخلة. في المثال أدناه، لا تعرض  علامة تبويب الأعضاء Outlook جهة الاتصال لمجموعة الاختبار أي مستخدمين ومجموعتين فرعتين فقط.

![علامة تبويب الأعضاء Outlook جهة الاتصال.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

يمكنك القيام باستعلام عكسي عن طريق حل المجموعة لمعرفة ما إذا كانت عضوا في أي مجموعة. في المثال أدناه، يمكنك أن ترى ضمن علامة التبويب  عضوية في Outlook جهة الاتصال الفرعية أن المجموعة الفرعية 1 هي عضو في مجموعة الاختبار.

![علامة تبويب العضوية في Outlook جهة الاتصال.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

بدلا من ذلك، يمكنك استخدام Azure Active Directory Graph API لتشغيل الاستعلامات للعثور على قائمة المجموعات ضمن مجموعة. لمزيد من المعلومات، راجع [العمليات على المجموعات| Graph API](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>الاتصال ب Microsoft للحصول على الدعم

إذا واجهت أنت أو المستخدمون مشاكل في تحميل الوظائف الإضافية أثناء استخدام تطبيقات Office على الويب (Word و Excel وما إلى ذلك)، والتي تم نشرها مركزيا، فقد تحتاج إلى الاتصال بدعم [Microsoft (تعرف](../../business-video/get-help-support.md) على كيفية القيام بذلك. توفير المعلومات التالية حول بيئة Microsoft 365 في تذكرة الدعم.

|النظام الأساسي|معلومات تصحيح الأخطاء|
|---|---|
|Office|سجلات Charles/Fiddler <br/> معرف المستأجر ([تعرف على كيفية)](/onedrive/find-your-office-365-tenant-id) <br/> CorrelationID. اطلع على مصدر إحدى صفحات Office وابحث عن قيمة "الم ID الارتباط" وأرسلها إلى الدعم:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|العملاء الثراء (Windows، Mac)|سجلات Charles/Fiddler <br/> أرقام إنشاء تطبيق العميل (يفضل أن تكون لقطة شاشة من **ملف/حساب**)|

## <a name="related-content"></a>المحتوى ذي الصلة

[نشر الوظائف الإضافية في مركز الإدارة](../manage/manage-deployment-of-add-ins.md) (مقالة)\
[إدارة الوظائف الإضافية في مركز الإدارة](manage-addins-in-the-admin-center.md) (مقالة)\
[الأسئلة الشائعة حول النشر المركزي](../manage/centralized-deployment-faq.yml) (مقالة)\
[ترقية Microsoft 365 الخاص بك لمستخدمي الأعمال إلى أحدث عميل](../setup/upgrade-users-to-latest-office-client.md) Office (مقالة)
