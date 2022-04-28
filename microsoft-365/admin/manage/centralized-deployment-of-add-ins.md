---
title: تحديد ما إذا كان النشر المركزي للوظائف الإضافية يعمل لمؤسستك
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
description: حدد ما إذا كان المستأجر والمستخدمون يستوفون المتطلبات، بحيث يمكنك استخدام "النشر المركزي" لنشر Office الوظائف الإضافية.
ms.openlocfilehash: 4d135e76034880e1419e296f2c201536be98b4bc
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093757"
---
# <a name="determine-if-centralized-deployment-of-add-ins-works-for-your-organization"></a>تحديد ما إذا كان النشر المركزي للوظائف الإضافية يعمل لمؤسستك

النشر المركزي هو الطريقة الموصى بها والأكثر غنى بالميزات لمعظم العملاء لنشر الوظائف الإضافية Office للمستخدمين والمجموعات داخل مؤسستك. إذا كنت مسؤولا، فاستخدم هذه الإرشادات لتحديد ما إذا كانت مؤسستك والمستخدمون يستوفون المتطلبات حتى تتمكن من استخدام "النشر المركزي".

يوفر النشر المركزي المزايا التالية:

- يمكن للمسؤول نشر وظيفة إضافية وتعيينها مباشرة لمستخدم أو لعدة مستخدمين عبر مجموعة أو لجميع الأشخاص في المؤسسة (راجع قسم متطلبات المسؤول للحصول على معلومات).
- عند بدء تشغيل تطبيق Office ذي الصلة، يتم تنزيل الوظيفة الإضافية تلقائيا. إذا كانت الوظيفة الإضافية تدعم أوامر الوظيفة الإضافية، تظهر الوظيفة الإضافية تلقائيا في الشريط داخل تطبيق Office.
- لم تعد الوظائف الإضافية تظهر للمستخدمين إذا قام المسؤول بإيقاف تشغيل الوظيفة الإضافية أو حذفها، أو إذا تمت إزالة المستخدم من Azure Active Directory أو من مجموعة تم تعيين الوظيفة الإضافية إليها.

يدعم النشر المركزي ثلاثة أنظمة أساسية لسطح المكتب Windows وMac وتطبيقات Office عبر الإنترنت. يدعم النشر المركزي أيضا iOS وAndroid (Outlook الوظائف الإضافية للأجهزة المحمولة فقط).

قد يستغرق ظهور الوظيفة الإضافية للعميل لجميع المستخدمين ما يصل إلى 24 ساعة.

## <a name="before-you-begin"></a>قبل البدء

يتطلب النشر المركزي للوظائف الإضافية أن يستخدم المستخدمون تراخيص Microsoft 365 Business (Business Basic أو Business Standard أو Business Premium) أو تراخيص Office 365 Enterprise (E1/E3/E5/F3) أو تراخيص Microsoft 365 Enterprise (E3/E5/F3) (ويتم تسجيل الدخول إليها Office باستخدام معرف المؤسسة أو تراخيص Office 365 Education (A1/A3/A5) أو تراخيص Microsoft 365 Education (A3/A5)، ولديك علب بريد Exchange Online Exchange Online ونشطة. يجب أن يكون دليل الاشتراك الخاص بك إما في Azure Active Directory أو موحدا له.
يمكنك عرض متطلبات محددة Office Exchange أدناه، أو استخدام [مدقق توافق النشر المركزي](#centralized-deployment-compatibility-checker).

لا يدعم النشر المركزي ما يلي:

- الوظائف الإضافية التي تستهدف إصدار MSI Office (باستثناء Outlook 2016)
- خدمة دليل محلي
- نشر الوظيفة الإضافية إلى علبة بريد Exchange On-Prem
- نشر الوظيفة الإضافية إلى SharePoint
- تطبيقات Teams
- نشر نموذج عنصر المكون (COM) أو أدوات Visual Studio للوظائف الإضافية Office (VSTO).
- عمليات نشر Microsoft 365 التي لا تتضمن Exchange Online مثل وحدات SKU: Microsoft 365 Apps للأعمال Microsoft 365 Apps للمؤسسة.

### <a name="office-requirements"></a>متطلبات Office

- بالنسبة إلى الوظائف الإضافية Word و Excel و PowerPoint، يجب أن يستخدم المستخدمون أحد الإجراءات التالية:
  - على جهاز Windows أو الإصدار 1704 أو إصدار أحدث من تراخيص Microsoft 365 Business (Business Basic أو Business Standard أو Business Premium) أو تراخيص Office 365 Enterprise (E1/E3/E5/F3) أو تراخيص Microsoft 365 Enterprise (E3/E5/F3).
  - على جهاز Mac، الإصدار 15.34 أو الإصدارات الأحدث.

- بالنسبة Outlook، يجب أن يستخدم المستخدمون أحد الإجراءات التالية:
  - الإصدار 1701 أو أحدث من تراخيص Microsoft 365 Business (Business Basic أو Business Standard أو Business Premium) أو تراخيص Office 365 Enterprise (E1/E3/E5/F3) أو تراخيص Microsoft 365 Enterprise (E3/E5/F3).
  - الإصدار 1808 أو إصدار أحدث من Office Professional Plus 2019 أو Office Standard 2019.
  - الإصدار 16.0.4494.1000 أو أحدث من Office Professional Plus 2016 (MSI) أو Office Standard 2016 (MSI)\*
  - الإصدار 15.0.4937.1000 أو إصدار أحدث من Office Professional Plus 2013 (MSI) أو Office Standard 2013 (MSI)\*
  - الإصدار 16.0.9318.1000 أو إصدار أحدث من Office 2016 for Mac
- الإصدار 2.75.0 أو إصدار أحدث من Outlook للأجهزة المحمولة لنظام التشغيل iOS
- الإصدار 2.2.145 أو إصدار أحدث من Outlook للأجهزة المحمولة لنظام التشغيل Android

    *تعرض إصدارات MSI من Outlook الوظائف الإضافية المثبتة من قبل المسؤول في شريط Outlook المناسب، وليس قسم "الوظائف الإضافية الخاصة بي".

### <a name="exchange-online-requirements"></a>متطلبات Exchange Online

تقوم Microsoft Exchange بتخزين بيانات الوظائف الإضافية داخل مستأجر مؤسستك. يجب أن يكون المسؤول الذي يقوم بنشر الوظائف الإضافية والمستخدمين الذين يتلقون هذه الوظائف الإضافية على إصدار من Exchange Online يدعم مصادقة OAuth.

راجع مسؤول Exchange مؤسستك لمعرفة التكوين المستخدم. يمكن التحقق من اتصال OAuth لكل مستخدم باستخدام [Test-OAuthConnectivity](/powershell/module/exchange/test-oauthconnectivity) PowerShell cmdlet.

### <a name="admin-requirements"></a>متطلبات المسؤول

لنشر وظيفة إضافية عبر النشر المركزي، يجب أن تكون مسؤولا عموميا أو مسؤولا Exchange في المؤسسة.

> [!NOTE]
> يمكن لمسؤول Exchange نشر وظيفة إضافية إذا تمت إضافة دور **مسؤول التطبيق** أو إذا تم تعيين خاصية **App Registrations** إلى true في مركز إدارة Azure Active Directory كما هو موضح في الصورة التالية:
>
> ![الصوره](https://user-images.githubusercontent.com/89943918/144516704-8874a10d-b540-41f3-ae9d-c07a8d7e143f.png)

### <a name="centralized-deployment-compatibility-checker"></a>مدقق توافق نشر مركزي

باستخدام "مدقق توافق النشر المركزي"، يمكنك التحقق مما إذا كان قد تم إعداد المستخدمين في المستأجر لاستخدام "النشر المركزي" ل Word Excel PowerPoint. مدقق التوافق غير مطلوب لدعم Outlook. تنزيل [مدقق التوافق](https://aka.ms/officeaddindeploymentorgcompatibilitychecker).

#### <a name="run-the-compatibility-checker"></a>تشغيل مدقق التوافق

1. بدء نافذة PowerShell.exe غير مقيدة.

2. قم بتنفيذ الأمر التالي:

   ```powershell
   Import-Module O365CompatibilityChecker
   ```

3. تشغيل الأمر **Invoke-CompatibilityCheck** :

   ```powershell
   Invoke-CompatibilityCheck
   ```

   يطالبك هذا الأمر ب _TenantDomain_ (على سبيل المثال، _TailspinToysIncorporated.onmicrosoft.com_) وبيانات اعتماد _TenantAdmin_ (استخدم بيانات اعتماد المسؤول العمومي)، ثم يطلب الموافقة.

   > [!NOTE]
   > استنادا إلى عدد المستخدمين في المستأجر الخاص بك، يمكن أن يكتمل المدقق في دقائق أو ساعات.

عند انتهاء تشغيل الأداة، تنتج ملف إخراج بتنسيق مفصول بفواصل (.csv). يتم حفظ الملف **إلى دليل العمل الحالي** بشكل افتراضي. يحتوي ملف الإخراج على المعلومات التالية:

- اسم المستخدم
- معرف المستخدم (عنوان البريد الإلكتروني للمستخدم)
- النشر المركزي جاهز - إذا كانت العناصر المتبقية صحيحة
- خطة Office - خطة Office المرخص لهم
- تم تنشيط Office - إذا تم تنشيطها Office
- علبة البريد المعتمدة - إذا كانت موجودة في علبة بريد ممكنة بواسطة OAuth

> [!NOTE]
> المصادقة متعددة العوامل غير معتمدة عند استخدام الوحدة النمطية PowerShell للتوزيع المركزي. تعمل الوحدة النمطية فقط مع المصادقة الأساسية.

## <a name="user-and-group-assignments"></a>تعيينات المستخدم والمجموعة

تدعم ميزة النشر المركزي حاليا غالبية المجموعات التي يدعمها Azure Active Directory، بما في ذلك مجموعات Microsoft 365 وقوائم التوزيع ومجموعات الأمان.

> [!NOTE]
> مجموعات الأمان غير الممكنة للبريد غير معتمدة حاليا.

يدعم النشر المركزي التعيينات للمستخدمين الفرديين والمجموعات وكل شخص في المستأجر. يدعم النشر المركزي المستخدمين في مجموعات المستوى الأعلى أو المجموعات التي لا تحتوي على مجموعات أصل، ولكن ليس المستخدمين في المجموعات أو المجموعات المتداخلة التي تحتوي على مجموعات أصل.

ألق نظرة على المثال التالي حيث يتم تعيين Sandra و Sheila ومجموعة قسم المبيعات إلى وظيفة إضافية. لأن قسم مبيعات الساحل الغربي هو مجموعة متداخلة، لا يتم تعيين Bert وFred إلى وظيفة إضافية.

![صورة MicrosoftTeams](../../media/683094bb-1160-4cce-810d-26ef7264c592.png)

### <a name="find-out-if-a-group-contains-nested-groups"></a>معرفة ما إذا كانت المجموعة تحتوي على مجموعات متداخلة

أسهل طريقة للكشف عما إذا كانت المجموعة تحتوي على مجموعات متداخلة هي عرض بطاقة جهة اتصال المجموعة ضمن Outlook. إذا أدخلت اسم المجموعة ضمن الحقل **"إلى"** في رسالة بريد إلكتروني ثم حددت اسم المجموعة عند حلها، فسيظهر لك ما إذا كان يحتوي على مستخدمين أو مجموعات متداخلة. في المثال أدناه، لا تعرض علامة التبويب **"الأعضاء**" في بطاقة جهة الاتصال Outlook لمجموعة الاختبار أي مستخدمين ومجموعتين فرعيتين فقط.

![علامة تبويب الأعضاء Outlook بطاقة جهة الاتصال.](../../media/d9db88c4-d752-426c-a480-b11a5b3adcd6.png)

يمكنك القيام بالاستعلام المعاكس عن طريق حل المجموعة لمعرفة ما إذا كانت عضوا في أي مجموعة. في المثال أدناه، يمكنك أن ترى ضمن علامة التبويب **"عضوية**" في بطاقة جهة الاتصال Outlook أن المجموعة الفرعية 1 هي عضو في مجموعة الاختبار.

![علامة تبويب العضوية لبطاقة جهة الاتصال Outlook.](../../media/a9f9b6ab-9c19-4822-9e3d-414ca068c42f.png)

بدلا من ذلك، يمكنك استخدام واجهة برمجة تطبيقات Azure Active Directory Graph لتشغيل الاستعلامات للعثور على قائمة المجموعات داخل مجموعة. لمزيد من المعلومات، راجع [العمليات على المجموعات| مرجع واجهة برمجة تطبيقات Graph](/previous-versions/azure/ad/graph/api/groups-operations).

### <a name="contacting-microsoft-for-support"></a>الاتصال ب Microsoft للحصول على الدعم

إذا واجهتك أنت أو المستخدمون مشاكل في تحميل الوظيفة الإضافية أثناء استخدام تطبيقات Office للويب (Word، Excel، وما إلى ذلك)، والتي تم نشرها مركزيا، فقد تحتاج إلى الاتصال بدعم Microsoft ([تعرف على كيفية إجراء ذلك](../../business-video/get-help-support.md). قم بتوفير المعلومات التالية حول بيئة Microsoft 365 في تذكرة الدعم.

|منصه|معلومات تتبع الأخطاء|
|---|---|
|Office|سجلات كارلس/Fiddler <br/> معرف المستأجر ([تعرف على كيفية)](/onedrive/find-your-office-365-tenant-id) <br/> معرف الارتباط. اعرض مصدر إحدى صفحات المكتب وابحث عن قيمة معرف الارتباط وأرسلها إلى الدعم:  <br/>`<input name=" **wdCorrelationId**" type="hidden" value=" **{BC17079E-505F-3000-C177-26A8E27EB623}**">` <br/> `<input name="user_id" type="hidden" value="1003bffd96933623"></form>`|
|العملاء الثريون (Windows، Mac)|سجلات كارلس/Fiddler <br/> إنشاء أرقام لتطبيق العميل (يفضل أن تكون لقطة شاشة من **File/Account**)|

## <a name="related-content"></a>المحتويات ذات الصلة

[نشر الوظائف الإضافية في مركز الإدارة](../manage/manage-deployment-of-add-ins.md) (مقالة)\
[إدارة الوظائف الإضافية في مركز الإدارة](manage-addins-in-the-admin-center.md) (مقالة)\
[الأسئلة المتداولة حول النشر المركزي](../manage/centralized-deployment-faq.yml) (مقالة)\
[ترقية Microsoft 365 لمستخدمي الأعمال إلى أحدث عميل Office](../setup/upgrade-users-to-latest-office-client.md) (مقالة)
