---
title: لماذا تحتاج إلى استخدام PowerShell Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: admindeeplinkEXCHANGE
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'ملخص: فهم لماذا يجب عليك استخدام PowerShell لإدارة Microsoft 365، في بعض الحالات بشكل أكثر كفاءة وفي حالات أخرى حسب الضرورة.'
ms.openlocfilehash: 114b97ff27ae1b79e58589eb746a261f83dc422f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097921"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>لماذا تحتاج إلى استخدام PowerShell Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

باستخدام مركز مسؤولي Microsoft 365، يمكنك إدارة حسابات المستخدمين والتراخيص Microsoft 365. يمكنك أيضا إدارة خدمات Microsoft 365، مثل Exchange Online Teams SharePoint Online. إذا كنت بدلا من ذلك تستخدم PowerShell لإدارة هذه الخدمات، يمكنك والاستفادة من سطر الأوامر وبيئة لغة البرمجة النصية للسرعة والأتمتة والقدرات الإضافية.

توضح هذه المقالة كيفية استخدام PowerShell لإدارة Microsoft 365 إلى:

- الكشف عن معلومات إضافية لا يمكنك رؤيتها في مركز مسؤولي Microsoft 365

- تكوين الميزات والإعدادات الممكنة فقط باستخدام PowerShell

- إجراء عمليات مجمعة

- تصفية البيانات

- طباعة البيانات أو حفظها

- الإدارة عبر الخدمات

ضع في اعتبارك أن PowerShell Microsoft 365 هو مجموعة من الوحدات النمطية Windows PowerShell، وهي بيئة سطر أوامر للخدمات والأنظمة الأساسية المستندة إلى Windows. تنشئ هذه البيئة لغة command-shell التي يمكن توسيعها بوحدات نمطية إضافية. يوفر طريقة لتنفيذ أوامر أو برامج نصية بسيطة أو معقدة. على سبيل المثال، بعد تثبيت PowerShell للوحدات النمطية Microsoft 365 والاتصال باشتراكك في Microsoft 365، يمكنك تشغيل الأمر التالي لإدراج جميع علب بريد المستخدمين Microsoft Exchange Online:

```powershell
Get-Mailbox
```

يمكنك أيضا الحصول على قائمة بعلب البريد باستخدام مركز مسؤولي Microsoft 365 ولكن عد العناصر في جميع القوائم لكافة المواقع لكافة تطبيقات الويب ليس سهلا.

تم تصميم PowerShell ل Microsoft 365 لمساعدتك في إدارة Microsoft 365، وليس لاستبدال مركز مسؤولي Microsoft 365. يجب أن يكون المسؤولون قادرين على استخدام PowerShell Microsoft 365 لأن هناك بعض إجراءات التكوين التي يمكن القيام بها فقط من خلال PowerShell لأوامر Microsoft 365. بالنسبة إلى هذه الحالات، تحتاج إلى معرفة كيفية:

- تثبيت PowerShell للوحدات النمطية Microsoft 365 (يتم ذلك مرة واحدة فقط لكل كمبيوتر مسؤول).

- الاتصال إلى اشتراكك في Microsoft 365 (مرة واحدة لكل جلسة عمل PowerShell).

- جمع المعلومات اللازمة لتشغيل PowerShell المطلوبة لأوامر Microsoft 365.

- تشغيل PowerShell لأوامر Microsoft 365.

بعد تعلم هذه المهارات الأساسية، لن تحتاج إلى سرد مستخدمي علبة البريد باستخدام الأمر **Get-Mailbox** . لا يتعين عليك أيضا فهم كيفية إنشاء أمر جديد مثل الأمر المذكور سابقا لحساب كافة العناصر في جميع القوائم لكافة المواقع لكافة تطبيقات الويب الخاصة بك. يمكن أن تساعدك Microsoft ومجتمع المسؤولين في تنفيذ مثل هذه المهام حسب الحاجة.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>يمكن ل PowerShell ل Microsoft 365 الكشف عن المعلومات التي لا يمكنك رؤيتها مع مركز مسؤولي Microsoft 365

يعرض مركز مسؤولي Microsoft 365 العديد من المعلومات المفيدة. ولكنه لا يعرض كل المعلومات المحتملة التي Microsoft 365 تخزنها حول المستخدمين والتراخيص وعلب البريد والمواقع. فيما يلي مثال *للمستخدمين والمجموعات* في مركز مسؤولي Microsoft 365:

![مثال على عرض المستخدمين والمجموعات في مركز مسؤولي Microsoft 365.](../media/o365-powershell-users-and-groups.png)

توفر طريقة العرض هذه المعلومات التي تحتاجها في كثير من الحالات. ومع ذلك، هناك أوقات تحتاج فيها إلى المزيد. على سبيل المثال، يعتمد ترخيص Microsoft 365 (وميزات Microsoft 365 المتوفرة للمستخدم) جزئيا على الموقع الجغرافي للمستخدم. قد لا تكون النهج والميزات التي يمكنك توسيعها إلى مستخدم يقيم في الولايات المتحدة هي نفسها تلك التي يمكنك توسيعها إلى مستخدم في الهند أو بلجيكا. اتبع هذه الخطوات في مركز مسؤولي Microsoft 365 لتحديد الموقع الجغرافي للمستخدم:

1. انقر نقرا مزدوجا فوق **اسم العرض** الخاص بالمستخدم.

2. في جزء عرض خصائص المستخدم، حدد **التفاصيل**.

3. في عرض التفاصيل، حدد **تفاصيل إضافية**.

4. قم بالتمرير حتى تعثر على عنوان **البلد أو المنطقة**:

     ![مثال على معلومات المنطقة لمستخدم في مركز مسؤولي Microsoft 365.](../media/o365-powershell-usage-location.png)

5. اكتب اسم العرض الخاص بالمستخدم وموقعه على ورقة، أو انسخه والصقه في المفكرة.

يجب تكرار هذا الإجراء لكل مستخدم. إذا كان لديك العديد من المستخدمين، يمكن أن تكون هذه العملية مملة. باستخدام PowerShell ل Microsoft 365، يمكنك عرض هذه المعلومات لجميع المستخدمين باستخدام الأمر التالي:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory لوحدة Windows PowerShell و cmdlets التي تحتوي على *Msol* باسمها. يجب عليك تشغيل أوامر cmdlets هذه من Windows PowerShell.
>

فيما يلي مثال على النتائج:

```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي (**Get-AzureADUser**)، ولكن فقط عرض اسم وموقع كل مستخدم (**حدد DisplayName، UsageLocation**).

نظرا لأن PowerShell ل Microsoft 365 يدعم لغة shell الأوامر، يمكنك معالجة المعلومات التي تم الحصول عليها من قبل الأمر **Get-AzureADUser**. على سبيل المثال، ربما ترغب في فرز هؤلاء المستخدمين حسب موقعهم، وتجميع جميع المستخدمين البرازيليين معا، وجميع مستخدمي الولايات المتحدة معا، وما إلى ذلك. إليك الأمر:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

فيما يلي مثال على النتائج:

```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي، ولكن فقط عرض الاسم والموقع لكل مستخدم وفرزهما أولا حسب موقعهم ثم اسمهم (**UsageLocation للفرز، DisplayName**).

يمكنك أيضا استخدام تصفية إضافية. على سبيل المثال، إذا كنت تريد فقط رؤية معلومات حول المستخدمين الاستناد إلى البرازيل، فاستخدم هذا الأمر:

```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation
```

فيما يلي مثال على النتائج:

```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي الذي يكون موقعه البرازيل (**حيث {$\_. UsageLocation -eq "BR"}**) ثم عرض الاسم والموقع لكل مستخدم.

 **ملاحظة حول المجالات الكبيرة**

إذا كان لديك مجال كبير مع عشرات الآلاف من المستخدمين، فقد يؤدي تجربة بعض الأمثلة التي نعرضها في هذه المقالة إلى التقييد. استنادا إلى عوامل مثل قوة الحوسبة وعرض النطاق الترددي للشبكة المتاحة، قد تحاول القيام بالكثير في وقت واحد. قد ترغب المؤسسات الكبيرة في تقسيم بعض عمليات PowerShell هذه إلى أمرين.

على سبيل المثال، يقوم الأمر التالي بإرجاع كافة حسابات المستخدمين ويعرض الاسم والموقع لكل منها:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

هذا يعمل بشكل رائع للمجالات الأصغر. ولكن في مؤسسة كبيرة، قد تحتاج إلى تقسيم هذه العملية إلى أمرين: أمر لتخزين معلومات حساب المستخدم في متغير والآخر لعرض المعلومات المطلوبة. فيما يلي مثال على ذلك:

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

تفسير هذه المجموعة من أوامر PowerShell هو:
1. الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي وتخزين المعلومات في متغير يسمى $x (**$x = Get-AzureADUser**).
1.  عرض محتويات *$x* المتغير، ولكن فقط تضمين اسم وموقع كل مستخدم (**$x | حدد DisplayName، UsageLocation**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>يحتوي Microsoft 365 على ميزات يمكنك تكوينها فقط باستخدام PowerShell Microsoft 365

تهدف مركز مسؤولي Microsoft 365 إلى توفير الوصول إلى المهام الإدارية الشائعة والمفيدة التي تنطبق على معظم البيئات. بمعنى آخر، تم تصميم مركز مسؤولي Microsoft 365 بحيث يمكن للمسؤول النموذجي تنفيذ مهام الإدارة الأكثر شيوعا. ولكن هناك بعض المهام التي لا يمكن القيام بها في مركز الإدارة.

على سبيل المثال، يوفر مركز إدارة Skype for Business Online بعض الخيارات لإنشاء دعوات مخصصة للاجتماعات:

![مثال على عرض دعوات مخصصة للاجتماعات في مركز إدارة Skype for Business عبر الإنترنت.](../media/o365-powershell-meeting-invitation.png)

باستخدام هذه الإعدادات، يمكنك إضافة لمسة من التخصيص والاحترافية إلى دعوات الاجتماع. ولكن هناك ما هو أكثر لإعدادات تكوين الاجتماع من مجرد إنشاء دعوات اجتماع مخصصة. على سبيل المثال، بشكل افتراضي، تسمح الاجتماعات بما يلي:

- للمستخدمين المجهولين الدخول التلقائي إلى كل اجتماع.

- الحضور لتسجيل الاجتماع.

- سيتم تعيين جميع المستخدمين من مؤسستك كمقدمي عرض عند الانضمام إلى الاجتماع.

لا تتوفر هذه الإعدادات من مركز إدارة Skype for Business Online. يمكنك التحكم بها من PowerShell Microsoft 365. فيما يلي أمر يعطل هذه الإعدادات الثلاثة:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> لتشغيل هذا الأمر، يجب تثبيت [Skype for Business Online PowerShell Module](https://www.microsoft.com/download/details.aspx?id=39366).

تفسير أمر PowerShell هذا هو:

1. في إعدادات اجتماعات Skype for Business Online الجديدة (**Set-CsMeetingConfiguration**)، قم بتعطيل السماح للمستخدمين المجهولين بدخول الاجتماعات تلقائيا (**-AdmitAnonymousUsersByDefault $False**).
2.  تعطيل قدرة الحضور على تسجيل الاجتماعات (**-AllowConferenceRecording $False**).
3. لا تعين جميع المستخدمين من مؤسستك كمقدمي عرض (**-DesignateAsPresenter "None"**).

لاستعادة هذه الإعدادات الافتراضية (تمكين الخيارات)، قم بتشغيل هذا الأمر:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

هناك سيناريوهات أخرى مشابهة أيضا، ولهذا السبب يجب على المسؤولين معرفة كيفية تشغيل PowerShell لأوامر Microsoft 365.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>يعد PowerShell ل Microsoft 365 رائعا للعمليات المجمعة

تكون الواجهات المرئية مثل مركز مسؤولي Microsoft 365 أكثر قيمة عندما يكون لديك عملية واحدة للقيام بها. على سبيل المثال، إذا كنت بحاجة إلى تعطيل حساب مستخدم واحد، يمكنك استخدام مركز الإدارة لتحديد موقع خانة اختيار ومسحها بسرعة. قد يكون هذا أسهل من تنفيذ عملية مماثلة في PowerShell.

ولكن إذا كان عليك تغيير العديد من الأشياء أو بعض الأشياء المحددة ضمن مجموعة كبيرة من الأشياء الأخرى، فقد لا تكون مركز مسؤولي Microsoft 365 أفضل أداة. على سبيل المثال، لنفترض أنه يجب عليك تغيير البادئة على آلاف أرقام الهواتف أو إزالة المستخدم المحدد *"كنين ماير"* من جميع مواقع SharePoint Online. كيف يمكنك القيام بذلك في مركز مسؤولي Microsoft 365؟

على سبيل المثال الأخير، لنفترض أن لديك عدة مئات SharePoint مواقع عبر الإنترنت، وأنت لا تعرف المواقع التي ينتمي إليها كين ماير. سيتعين عليك البدء من مركز مسؤولي Microsoft 365 ثم تنفيذ هذا الإجراء لكل موقع:

1. حدد **عنوان URL** للموقع.

2. في مربع **خصائص مجموعة المواقع المشتركة** ، حدد الارتباط **"عنوان موقع ويب** " لفتح الموقع.

3. على الموقع، حدد **"مشاركة**".

4. في مربع الحوار **"مشاركة** "، حدد الارتباط الذي يعرض كافة المستخدمين الذين لديهم أذونات للموقع:

     ![مثال لعرض أعضاء موقع SharePoint Online في مركز إدارة SharePoint Online.](../media/o365-powershell-view-permissions.png)

5. في مربع الحوار **"مشترك مع** "، حدد **"خيارات متقدمة**".

6. قم بالتمرير لأسفل قائمة المستخدمين، وابحث عن "كنين ماير" وحدده (بافتراض أن لديه أذونات للموقع)، ثم حدد **"إزالة أذونات المستخدم**".

سيستغرق هذا وقتا *طويلا* لعدة مئات من المواقع.

البديل هو تشغيل الأمر التالي في PowerShell Microsoft 365 لإزالة "كين ماير" من جميع مواقعك:

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> يتطلب هذا الأمر تثبيت [الوحدة النمطية SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

تفسير أمر PowerShell هذا هو: الحصول على جميع مواقع SharePoint في اشتراك Microsoft 365 الحالي (**Get-SPOSite**) ولكل موقع قم بإزالة "كين ماير" من قائمة المستخدمين الذين يمكنهم الوصول إليه (**ForEach {Remove-SPOUser -Site $\_. Url -LoginName "kenmyer\@ litwareinc.com"}**).

نخبر Microsoft 365 بإزالة "كين ماير" من كل موقع، بما في ذلك تلك التي لا يملك حق الوصول إليها. لذلك ستعرض النتائج أخطاء لتلك المواقع التي ليس لديه حق الوصول إليها. يمكننا استخدام شرط إضافي على هذا الأمر لإزالة "كين ماير" فقط من المواقع التي لديه في قائمة تسجيل الدخول الخاصة بهم. ولكن الأخطاء التي يتم إرجاعها لا تسبب أي ضرر للمواقع نفسها. قد يستغرق تشغيل هذا الأمر بضع دقائق مقابل مئات المواقع، بدلا من ساعات العمل خلال مركز مسؤولي Microsoft 365.

فيما يلي مثال آخر لعملية مجمعة. استخدم هذا الأمر لإضافة *مهى كرني*، مسؤول SharePoint جديد، إلى جميع المواقع في المؤسسة:

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

تفسير أمر PowerShell هذا هو: الحصول على جميع مواقع SharePoint في اشتراك Microsoft 365 الحالي ولكل موقع السماح بالوصول إلى مهى كرني عن طريق إضافة اسم تسجيل الدخول الخاص بها إلى مجموعة الأعضاء في الموقع (**ForEach {Add-SPOUser -Site $\_. Url -LoginName "bkearney\@ litwareinc.com" -Group "Members"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>يعد PowerShell ل Microsoft 365 رائعا في تصفية البيانات

يوفر مركز مسؤولي Microsoft 365 عدة طرق لتصفية بياناتك لتحديد موقع مجموعة فرعية مستهدفة من المعلومات بسهولة. على سبيل المثال، يسهل Exchange التصفية على أي خاصية من خصائص علبة بريد المستخدم. على سبيل المثال، إليك قائمة بعلب البريد لجميع المستخدمين الذين يعيشون في مدينة بلومينغتون:

![مثال على إجراء بحث متقدم في مركز مسؤولي Microsoft 365 لقائمة علب البريد لجميع المستخدمين الذين يعيشون في مدينة بلومينغتون.](../media/o365-powershell-advanced-search.png)

يتيح لك <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a> أيضا دمج معايير التصفية. على سبيل المثال، يمكنك العثور على علب البريد لجميع الأشخاص الذين يعيشون في Bloomington ويعملون في قسم الشؤون المالية.

ولكن هناك قيود على ما يمكنك القيام به في مركز إدارة Exchange. على سبيل المثال، لم تتمكن من العثور بسهولة على علب بريد الأشخاص الذين يعيشون في بلومينجتون *أو* سان دييغو، أو علب البريد لجميع الأشخاص الذين لا يعيشون في Bloomington.

يمكنك استخدام أمر PowerShell التالي Microsoft 365 للحصول على قائمة بعلب البريد لجميع الأشخاص الذين يعيشون في Bloomington أو سان دييغو:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

فيما يلي مثال على النتائج:

```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي الذين لديهم علبة بريد في مدينة سان دييغو أو Bloomington (**حيث {$\_. RecipientTypeDetails -eq "UserMailbox" -and ($\_. City -eq "San Tahoma" -or $\_. City -eq "Bloomington")}**)، ثم عرض الاسم والمدينة لكل منهما (**حدد DisplayName, City**).

وإليك الأمر الخاص بإدراج جميع علب البريد للأشخاص الذين يعيشون في أي مكان باستثناء Bloomington:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

فيما يلي مثال على النتائج:

```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي الذين لديهم علبة بريد غير موجودة في مدينة Bloomington (**حيث {$\_. RecipientTypeDetails -eq "UserMailbox" -و$\_. المدينة -ne "Bloomington"}**)، ثم عرض الاسم والمدينة لكل منهما.

### <a name="use-wildcards"></a>استخدام أحرف البدل

يمكنك أيضا استخدام أحرف البدل في عوامل تصفية PowerShell لمطابقة جزء من الاسم. على سبيل المثال، افترض أنك تبحث عن حساب مستخدم. كل ما يمكنك تذكره هو أن اسم عائلة المستخدم كان *أندرسون* أو ربما *هيندرسون* أو *يورجينسون*.

يمكنك تعقب هذا المستخدم في مركز مسؤولي Microsoft 365 باستخدام أداة البحث وإجراء ثلاث عمليات بحث مختلفة:

- واحد من أجل  *أندرسون*

- واحد ل  *Henderson*

- واحد ل  *Jorgenson*

نظرا لأن الأسماء الثلاثة كلها تنتهي ب "son"، يمكنك إخبار PowerShell بعرض جميع المستخدمين الذين ينتهي اسمهم ب "son". إليك الأمر:

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي، ولكن استخدم عامل تصفية يسرد فقط المستخدمين الذين تنتهي أسمائهم الأخيرة ب "son" (**-Filter '{LastName - like "\*son"}'**). يرمز \* إلى أي مجموعة من الأحرف، وهي أحرف في اسم عائلة المستخدم.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>يسهل PowerShell ل Microsoft 365 طباعة البيانات أو حفظها

يتيح لك مركز مسؤولي Microsoft 365 عرض قوائم البيانات. فيما يلي مثال لمركز إدارة Skype for Business Online الذي يعرض قائمة بالمستخدمين الذين تم تمكينهم Skype for Business Online:

![مثال لمركز إدارة Skype for Business Online يعرض قائمة بالمستخدمين الذين تم تمكينهم Skype for Business Online.](../media/o365-powershell-lync-users.png)

لحفظ هذه المعلومات في ملف، يجب لصقها في مستند أو Microsoft Excel ورقة عمل. قد تتطلب أي من الحالتين تنسيقا إضافيا. بالإضافة إلى ذلك، لا يوفر مركز مسؤولي Microsoft 365 طريقة لطباعة القائمة المعروضة مباشرة.

لحسن الحظ، يمكنك استخدام PowerShell ليس فقط لعرض القائمة ولكن لحفظها في ملف يمكن استيراده بسهولة إلى Excel. فيما يلي مثال على أمر لحفظ بيانات المستخدم Skype for Business Online إلى ملف قيم مفصولة بفواصل (CSV)، والذي يمكن استيراده بعد ذلك بسهولة كجدول في ورقة عمل Excel:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

فيما يلي مثال على النتائج:

![مثال لجدول تم استيراده إلى ورقة عمل Excel لبيانات المستخدم Skype for Business Online التي تم حفظها في ملف قيم مفصول بفواصل.](../media/o365-powershell-data-in-excel.png)

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين عبر الإنترنت Skype for Business في اشتراك Microsoft 365 الحالي (**Get-CsOnlineUser**)؛ والحصول على اسم المستخدم و UPN والموقع فقط (**حدد DisplayName و UserPrincipalName و UsageLocation**)، ثم احفظ هذه المعلومات في ملف CSV يسمى C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\" SfBUsers.csv" -NoTypeInformation**).

يمكنك أيضا استخدام الخيارات لحفظ هذه القائمة كملف XML أو صفحة HTML. في الواقع، مع أوامر PowerShell إضافية، يمكنك حفظه مباشرة كملف Excel، مع أي تنسيق مخصص تريده.

يمكنك أيضا إرسال إخراج أمر PowerShell الذي يعرض قائمة مباشرة إلى الطابعة الافتراضية في Windows. فيما يلي مثال على الأمر:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

إليك الشكل الذي سيبدو عليه المستند المطبوع:

![مثال لمستند مطبوع كان ناتج أمر PowerShell تم إرساله مباشرة إلى الطابعة الافتراضية في Windows.](../media/o365-powershell-printed-data.png)

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين Skype for Business Online في اشتراك Microsoft 365 الحالي؛ والحصول على اسم المستخدم و UPN والموقع فقط؛ ثم إرسال هذه المعلومات إلى الطابعة الافتراضية Windows (**خارج الطابعة**).

يحتوي المستند المطبوع على التنسيق البسيط نفسه الذي يحتوي عليه العرض في نافذة أوامر PowerShell. للحصول على نسخة مطبوعة، ما عليك **سوى إضافة | خارج الطابعة** إلى نهاية الأمر.

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>يتيح لك PowerShell ل Microsoft 365 الإدارة عبر منتجات الخادم

تم تصميم المكونات التي تشكل Microsoft 365 للعمل معا. على سبيل المثال، افترض أنك أضفت مستخدما جديدا إلى Microsoft 365، وقمت بتحديد معلومات مثل قسم المستخدم ورقم الهاتف. ستتوفر هذه المعلومات بعد ذلك إذا قمت بالوصول إلى معلومات المستخدم في أي من خدمات Microsoft 365: Skype for Business Online أو Exchange أو SharePoint.

ولكن هذا للمعلومات الشائعة التي تمتد عبر مجموعة المنتجات. لا تتوفر عادة معلومات خاصة بالناتج، مثل معلومات حول علبة بريد Exchange الخاصة بالمستخدم، عبر المجموعة. على سبيل المثال، تتوفر معلومات حول ما إذا كانت علبة بريد المستخدم ممكنة أم لا في مركز إدارة Exchange فقط.

لنفترض أنك تريد إنشاء تقرير يعرض المعلومات التالية لجميع المستخدمين:

- اسم العرض الخاص بالمستخدم

- ما إذا كان المستخدم مرخصا Microsoft 365

- ما إذا كان قد تم تمكين علبة بريد Exchange الخاصة بالمستخدم

- ما إذا كان المستخدم ممكنا ل Skype for Business Online

لا يمكنك بسهولة إنتاج مثل هذا التقرير في مركز مسؤولي Microsoft 365. بدلا من ذلك، سيتعين عليك إنشاء مستند منفصل لتخزين المعلومات، مثل ورقة عمل Excel. بعد ذلك، احصل على جميع أسماء المستخدمين ومعلومات الترخيص من مركز مسؤولي Microsoft 365، واحصل على معلومات علبة البريد من <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">مركز إدارة Exchange</a>، واحصل على معلومات Skype for Business Online من مركز إدارة Skype for Business Online، ثم ادمج ذلك المعلومات.

البديل هو استخدام برنامج نصي PowerShell لتجميع التقرير نيابة عنك.

البرنامج النصي المثال التالي أكثر تعقيدا من الأوامر التي رأيتها حتى الآن في هذه المقالة. ولكن، فإنه يظهر إمكانية استخدام PowerShell لإنشاء طرق عرض المعلومات التي يصعب الحصول عليها بخلاف ذلك. إليك البرنامج النصي لتجميع القائمة التي تحتاجها وعرضها:

```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

فيما يلي مثال على النتائج:

```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

تفسير هذا البرنامج النصي PowerShell هو:

1. الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي وتخزين المعلومات في متغير يسمى *$x* (**$x = Get-AzureADUser**).
1. بدء حلقة يتم تشغيلها عبر جميع المستخدمين في $x المتغير (**foreach ($i في $x)**).
1. تعريف متغير يسمى *$y* وتخزين معلومات علبة بريد المستخدم فيه (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. أضف خاصية جديدة إلى معلومات المستخدم المسماة *IsMailBoxEnabled*. قم بتعيينه إلى قيمة الخاصية IsMailBoxEnabled لعل بريد المستخدم (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
1. حدد متغيرا يسمى *$y*، وقم بتخزين معلومات المستخدم Skype for Business Online فيه (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. أضف خاصية جديدة إلى معلومات المستخدم المسماة *EnabledForSfB*. قم بتعيينه إلى قيمة الخاصية الممكنة لمعلومات Skype for Business Online الخاصة بالمستخدم (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -value $y.Enabled**).
1. اعرض قائمة المستخدمين، ولكن قم بتضمين اسمهم فقط، وما إذا كانوا مرخصين، والخصائص الجديدة التي تشير إلى تمكين علبة البريد الخاصة بهم وما إذا كانت ممكنة Skype for Business Online (**$x | حدد DisplayName، IsLicensed، IsMailboxEnabled، EnabledforSfB**).

## <a name="see-also"></a>راجع أيضًا

[بدء استخدام PowerShell ل Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[إدارة حسابات المستخدمين والتراخيص والمجموعات Microsoft 365 باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[استخدام Windows PowerShell لإنشاء تقارير في Microsoft 365](use-windows-powershell-to-create-reports-in-microsoft-365.md)