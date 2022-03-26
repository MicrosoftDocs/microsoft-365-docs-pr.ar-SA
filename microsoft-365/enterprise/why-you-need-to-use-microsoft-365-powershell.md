---
title: لماذا تحتاج إلى استخدام PowerShell Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'ملخص: فهم سبب ضرورة استخدام PowerShell لإدارة Microsoft 365، في بعض الحالات بفعالية أكبر وفي حالات أخرى بالضرورة.'
ms.openlocfilehash: 11b84fbd10d2a7180637d377c219502e6ffb00aa
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/13/2021
ms.locfileid: "63572821"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>لماذا تحتاج إلى استخدام PowerShell Microsoft 365

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

باستخدام مركز مسؤولي Microsoft 365، يمكنك إدارة Microsoft 365 المستخدمين والتراخيص الخاصة بك. يمكنك أيضا إدارة خدمات Microsoft 365، مثل Exchange Online Teams و SharePoint عبر الإنترنت. إذا كنت بدلا من ذلك تستخدم PowerShell لإدارة هذه الخدمات، يمكنك الاستفادة من بيئة سطر الأوامر ولغات البرمجة النصية للسرعة والأتمتة والقدرات الإضافية.

توضح هذه المقالة كيفية استخدام PowerShell لإدارة Microsoft 365:

- الكشف عن معلومات إضافية لا يمكنك رؤياها في مركز مسؤولي Microsoft 365

- تكوين الميزات والإعدادات الممكنة فقط باستخدام PowerShell

- تنفيذ عمليات مجمعة

- تصفية البيانات

- طباعة البيانات أو حفظها

- الإدارة عبر الخدمات

ضع في اعتبارك أن PowerShell for Microsoft 365 هو مجموعة من الوحدات النمطية ل Windows PowerShell، وهي بيئة سطر أوامر للخدمات والوحدات الأساسية المستندة إلى Windows. تنشئ هذه البيئة لغة ذات أوامر يمكن توسيعها باستخدام وحدات نموذجية إضافية. فهو يوفر طريقة لتنفيذ الأوامر أو البرامج النصية البسيطة أو المعقدة. على سبيل المثال، بعد تثبيت وحدات PowerShell النمطية ل Microsoft 365 والاتصال باشتراك Microsoft 365، يمكنك تشغيل الأمر التالي لقائمة كل علب بريد المستخدمين Microsoft Exchange Online:

```powershell
Get-Mailbox
```

يمكنك أيضا الحصول على قائمة علب البريد باستخدام مركز مسؤولي Microsoft 365 ولكن ليس من السهل حساب عدد العناصر الموجودة في كل القوائم لكل المواقع لكل تطبيقات الويب.

تم تصميم powerShell Microsoft 365 لمساعدتك على إدارة Microsoft 365، وليس لاستبدال مركز مسؤولي Microsoft 365. يجب أن يكون المسؤولون قادرين على استخدام PowerShell Microsoft 365 بسبب وجود بعض إجراءات التكوين التي يمكن القيام بها فقط من خلال PowerShell Microsoft 365 الأوامر. بالنسبة إلى هذه الحالات، يجب أن تعرف كيفية القيام بما يلي:

- قم بتثبيت PowerShell Microsoft 365 النمطية (تم ذلك مرة واحدة فقط لكل كمبيوتر مسؤول).

- الاتصال اشتراكك Microsoft 365 (مرة واحدة لكل جلسة عمل PowerShell).

- جمع المعلومات المطلوبة لتشغيل أوامر PowerShell المطلوبة Microsoft 365 الأوامر.

- تشغيل PowerShell Microsoft 365 الأوامر.

بعد تعلم هذه المهارات الأساسية، لن تحتاج إلى سرد مستخدمي علبة البريد باستخدام الأمر **الحصول على علبة** البريد. ولا تحتاج أيضا إلى فهم كيفية إنشاء أمر جديد مثل الأمر المستعرض مسبقا لتصنف كل العناصر الموجودة في كل القوائم لكل المواقع لكل تطبيقات الويب. يمكن أن تساعدك Microsoft ومجتمع المسؤولين على تنفيذ مثل هذه المهام حسب الحاجة.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>يمكن أن Microsoft 365 PowerShell for مركز مسؤولي Microsoft 365

تعرض مركز مسؤولي Microsoft 365 العديد من المعلومات المفيدة. ولكنه لا يعرض كل المعلومات المحتملة التي Microsoft 365 حول المستخدمين والتراخيص علب البريد والمواقع. فيما يلي مثال للمستخدمين *والمجموعات* في مركز مسؤولي Microsoft 365:

![مثال لعرض المستخدمين والمجموعات في مركز مسؤولي Microsoft 365.](../media/o365-powershell-users-and-groups.png)

توفر طريقة العرض هذه المعلومات التي تحتاج إليها في العديد من الحالات. ومع ذلك، هناك أوقات تحتاج فيها إلى المزيد. على سبيل المثال، Microsoft 365 الترخيص (Microsoft 365 المتوفرة للمستخدم) بشكل جزئي على الموقع الجغرافي للمستخدم. قد لا تكون السياسات والميزات التي يمكنك توسيعها إلى مستخدم يقيم في الولايات المتحدة هي نفسها تلك التي يمكنك توسيعها إلى مستخدم في الهند أو بلجيكا. اتبع هذه الخطوات في مركز مسؤولي Microsoft 365 لتحديد الموقع الجغرافي للمستخدم:

1. انقر نقرا مزدوجا فوق اسم **العرض للمستخدم**.

2. في جزء عرض خصائص المستخدم، حدد **التفاصيل**.

3. في عرض التفاصيل، حدد **تفاصيل إضافية**.

4. قم بالتمرير حتى تعثر على العنوان **البلد أو المنطقة**:

     ![مثال على معلومات المنطقة لمستخدم في مركز مسؤولي Microsoft 365.](../media/o365-powershell-usage-location.png)

5. اكتب اسم العرض الخاص للمستخدم وموقعه على ورقة، أو انسخه واللصق فيه في المفكرة.

يجب تكرار هذا الإجراء لكل مستخدم. إذا كان لديك العديد من المستخدمين، فقد تكون هذه العملية مملة. باستخدام PowerShell Microsoft 365، يمكنك عرض هذه المعلومات لجميع المستخدمين باستخدام الأمر التالي:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>لا يدعم PowerShell Core الوحدة النمطية Microsoft Azure Active Directory النمطية Windows PowerShell النمطية و cmdlets التي تتضمن *Msol* في اسمها. يجب تشغيل cmdlets هذه من Windows PowerShell.
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

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي (**Get-AzureADUser**)، ولكن يعرض فقط الاسم والموقع لكل مستخدم (**حدد DisplayName، UsageLocation**).

نظرا لأن PowerShell for Microsoft 365 يدعم لغة الأوامر، يمكنك معالجة المعلومات التي يحصل عليها الأمر **Get-AzureADUser** بشكل أكبر. على سبيل المثال، قد ترغب في فرز هؤلاء المستخدمين حسب موقعهم، مع تجميع جميع المستخدمين البرازيليين معا، وكل مستخدمي الولايات المتحدة معا، وما إلى ذلك. إليك الأمر:

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

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي، ولكن فقط عرض اسم كل مستخدم وموقعه وفرزهما أولا حسب موقعه ثم اسمه (فرز **UsageLocation، DisplayName**).

يمكنك أيضا استخدام تصفية إضافية. على سبيل المثال، إذا كنت تريد فقط الاطلاع على معلومات حول المستخدمين ال 20 في البرازيل، فاستخدم هذا الأمر:

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

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي الذي يكون موقعه هو البرازيل (**حيث {$\_. UsageLocation -eq "BR"}**) ثم اعرض الاسم والموقع لكل مستخدم.

 **ملاحظة حول المجالات الكبيرة**

إذا كان لديك مجال كبير بعشرات الآلاف من المستخدمين، فقد تؤدي تجربة بعض الأمثلة التي نعرضها في هذه المقالة إلى التكتل. استنادا إلى عوامل مثل القدرة على الحوسبة وعرض النطاق الترددي للشبكة المتوفر، قد تحاول القيام بالكثير في الوقت نفسه. قد ترغب المؤسسات الكبيرة في تقسيم بعض عمليات PowerShell هذه إلى أمرين.

على سبيل المثال، يرجع الأمر التالي كل حسابات المستخدمين ويظهر الاسم والموقع لكل:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

يعمل هذا بشكل رائع للمجالات الأصغر. ولكن في مؤسسة كبيرة، قد ترغب في تقسيم هذه العملية إلى أمرين: أمر لتخزين معلومات حساب المستخدم في متغير وآخر لعرض المعلومات المطلوبة. فيما يلي مثال على ذلك:

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

تفسير هذه المجموعة من أوامر PowerShell هو:
1. احصل على جميع المستخدمين في اشتراك Microsoft 365 الحالي وخزن المعلومات في متغير يسمى $x (**$x = Get-AzureADUser**).
1.  عرض محتويات المتغير *$x، مع* تضمين اسم كل مستخدم وموقعه فقط ($x |**حدد DisplayName، UsageLocation**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 الميزات التي يمكنك تكوينها فقط باستخدام PowerShell Microsoft 365

الهدف مركز مسؤولي Microsoft 365 هو توفير الوصول إلى المهام الإدارية المفيدة الشائعة التي تنطبق على معظم البيئات. بعبارة أخرى، مركز مسؤولي Microsoft 365 تصميم البرنامج بحيث يمكن للمسؤول النموذجي تنفيذ مهام الإدارة الأكثر شيوعا. ولكن هناك بعض المهام التي لا يمكن القيام بها في مركز الإدارة.

على سبيل المثال، يوفر Skype for Business إدارة عبر الإنترنت بعض الخيارات لإنشاء دعوات اجتماعات مخصصة:

![مثال لعرض دعوات الاجتماعات المخصصة في Skype for Business Online Admin.](../media/o365-powershell-meeting-invitation.png)

باستخدام هذه الإعدادات، يمكنك إضافة لمسة من الطابع الشخصي والاحترافية إلى دعوات الاجتماع. ولكن هناك ما هو أكثر لإعدادات تكوين الاجتماع من مجرد إنشاء دعوات مخصصة للاجتماعات. على سبيل المثال، تسمح الاجتماعات بشكل افتراضي بما يلي:

- المستخدمون المجهولون للحصول على الدخول التلقائي إلى كل اجتماع.

- الحضور لتسجيل الاجتماع.

- سيتم تعيين جميع المستخدمين من مؤسستك كمقدمي عرض عند الانضمام إلى الاجتماع.

لا تتوفر هذه الإعدادات من مركز إدارة Skype for Business Online. يمكنك التحكم فيها من PowerShell Microsoft 365. فيما يلي أمر يقوم بتعطيل هذه الإعدادات الثلاثة:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> لتشغيل هذا الأمر، يجب تثبيت وحدة [Skype for Business PowerShell النمطية عبر الإنترنت](https://www.microsoft.com/download/details.aspx?id=39366).

تفسير أمر PowerShell هذا هو:

1. في إعدادات الاجتماعات Skype for Business Online الجديدة (**Set-CsMeetingConfiguration**)، قم بتعطيل السماح للمستخدمين المجهولين باكتساب الدخول التلقائي إلى الاجتماعات (**-AdmitAnonymousUsersByDefault $False**).
2.  تعطيل قدرة الحضور على تسجيل الاجتماعات (**-AllowConferenceRecording $False**).
3. لا تعين جميع المستخدمين من مؤسستك كمقدمي عرض (**-DesignateAsPresenter "None"**).

لاستعادة هذه الإعدادات الافتراضية (تمكين الخيارات)، يمكنك تشغيل هذا الأمر:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

هناك سيناريوهات أخرى مماثلة أيضا، ولهذا السبب يجب أن يعرف المسؤولون كيفية تشغيل PowerShell Microsoft 365 الأوامر.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>PowerShell for Microsoft 365 هو أمر رائع للعمليات المجمعة

تكون الواجهات المرئية مثل مركز مسؤولي Microsoft 365 أكثر قيمة عندما يكون لديك عملية واحدة للقيام بها. على سبيل المثال، إذا كنت بحاجة إلى تعطيل حساب مستخدم واحد، يمكنك استخدام مركز الإدارة لتحديد موقع خانة الاختيار ومسحها بسرعة. قد يكون ذلك أسهل من تنفيذ عملية مماثلة في PowerShell.

ولكن إذا كان عليك تغيير العديد من الأشياء أو بعض الأشياء المحددة ضمن مجموعة كبيرة من الأشياء الأخرى، مركز مسؤولي Microsoft 365 قد لا تكون الأداة الأفضل. على سبيل المثال، لنق أن عليك تغيير البادأ على الآلاف من أرقام الهواتف أو إزالة المستخدم المحدد كن *ماير* من كل مواقع SharePoint عبر الإنترنت. كيف يمكنك القيام بذلك في مركز مسؤولي Microsoft 365؟

في المثال الأخير، لنقول أن لديك عدة مئات من المواقع SharePoint على الإنترنت، ولا تعرف المواقع التي يكون علياء ماير عضوا فيها. يجب أن تبدأ من مركز مسؤولي Microsoft 365 ثم تنفيذ هذا الإجراء لكل موقع:

1. حدد **عنوان URL** للموقع.

2. في المربع **خصائص مجموعة المواقع** ، حدد الارتباط **عنوان موقع** ويب لفتح الموقع.

3. على الموقع، حدد **مشاركة**.

4. في مربع **الحوار** مشاركة، حدد الارتباط الذي يعرض جميع المستخدمين الذين لديهم أذونات للموقع:

     ![مثال لعرض أعضاء موقع SharePoint Online في SharePoint Online Admin center.](../media/o365-powershell-view-permissions.png)

5. في مربع **الحوار** مشترك مع، حدد **متقدم**.

6. قم بالتمرير لأسفل قائمة المستخدمين، واعثر على كينا ماير وحدده (مع افتراض أن لديه أذونات للموقع)، ثم حدد **إزالة أذونات المستخدم**.

قد يستغرق ذلك وقتا *طويلا* لعدة مئات من المواقع.

البديل هو تشغيل الأمر التالي في PowerShell for Microsoft 365 لإزالة كنعان ماير من كل مواقعك:

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> يتطلب هذا الأمر تثبيت الوحدة النمطية SharePoint [Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

تفسير أمر PowerShell هذا هو: الحصول على كل مواقع SharePoint في اشتراك Microsoft 365 الحالي (**Get-SPOSite**) ولكل موقع قم بإزالة علياء ماير من قائمة المستخدمين الذين يمكنهم الوصول إليه (**ForEach {Remove-SPOUser -Site $\_. Url -LoginName "kenmyer\@ litwareinc.com"}**).

نخبر Microsoft 365 بإزالة علياء ماير من كل موقع، بما في ذلك المواقع التي لا يمكن له الوصول إليها. وبالتالي،  سوف تظهر النتائج أخطاء لتلك المواقع التي لا يمكن الوصول إليها. يمكننا استخدام شرط إضافي في هذا الأمر لإزالة علياء ماير فقط من المواقع التي لديه قائمة تسجيل الدخول الخاصة به. ولكن الأخطاء التي يتم إرجاعها لا تسبب أي ضرر للمواقع نفسها. قد يستغرق تشغيل هذا الأمر بضع دقائق مقابل مئات المواقع، بدلا من ساعات العمل خلال مركز مسؤولي Microsoft 365.

فيما يلي مثال آخر لعملية مجمعة. استخدم هذا الأمر لإضافة *بوني كياريني*، SharePoint جديدة، إلى كل المواقع في المؤسسة:

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

تفسير أمر PowerShell هذا هو: احصل على كل مواقع SharePoint في اشتراك Microsoft 365 الحالي، ولكل موقع، اسمح ل بوني كارني بالوصول عن طريق إضافة اسم تسجيل الدخول الخاص بها إلى مجموعة الأعضاء في الموقع (**ForEach {Add-SPOUser -Site $\_. Url -LoginName "bkearney\@ litwareinc.com" -Group "Members"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell for Microsoft 365 رائع في تصفية البيانات

توفر مركز مسؤولي Microsoft 365 العديد من الطرق لتصفية البيانات لتحديد موقع مجموعة فرعية من المعلومات المستهدفة بسهولة. على سبيل المثال، Exchange من السهل التصفية على أي خاصية في علبة بريد المستخدم. على سبيل المثال، فيما يلي قائمة علب البريد لجميع المستخدمين الذين يعيشون في مدينة بلومينجتون:

![مثال على القيام ببحث متقدم في مركز مسؤولي Microsoft 365 عن قائمة علب البريد لكل المستخدمين الذين يعيشون في مدينة بلومينجتون.](../media/o365-powershell-advanced-search.png)

يتيح <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">لك Exchange إدارة المؤسسة</a> أيضا دمج معايير التصفية. على سبيل المثال، يمكنك العثور على علب البريد لكل الأشخاص الذين يعيشون في بلومينجتون والعمل في قسم الشؤون المالية.

ولكن هناك قيود على ما يمكنك القيام به في Exchange الإدارة. على سبيل المثال، لا يمكنك العثور بسهولة على علب بريد الأشخاص الذين يعيشون في *بلومينجتون* أو سان دييغو، أو علب البريد لكل الأشخاص الذين لا يعيشون في بلومينجتون.

يمكنك استخدام أمر PowerShell for Microsoft 365 التالي للحصول على قائمة لعلب البريد لكل الأشخاص الذين يعيشون في بلومينجتون أو سان دييغو:

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

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي الذين لديهم علبة بريد في مدينة سان دييغو أو بلومينجتون (حيث **{$\_. RecipientTypeDetails -eq "UserMailbox" -and ($\_. City -eq "San Diego" -أو $\_. المدينة -eq "Bloomington")}**)، ثم اعرض الاسم والمدينة لكل منهما (**حدد اسم العرض، المدينة**).

وفيما يلي أمر سرد كل علب البريد للأشخاص الذين يعيشون في أي مكان باستثناء بلومينجتون:

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

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي الذين لديهم علبة بريد غير موجودة في مدينة بلومينجتون (حيث **{$\_. RecipientTypeDetails -eq "UserMailbox" -and $\_. المدينة -ne "Bloomington"}**)، ثم اعرض الاسم والمدينة لكل منهما.

### <a name="use-wildcards"></a>استخدام أحرف البدل

يمكنك أيضا استخدام أحرف البدل في عوامل تصفية PowerShell لمطابقة جزء من الاسم. على سبيل المثال، افترض أنك تبحث عن حساب مستخدم. كل ما يمكنك تذكره هو أن اسم العائلة للمستخدم هو *أندرسون* أو ربما *هيندرسون* أو *يورغنسون*.

يمكنك تعقب هذا المستخدم في مركز مسؤولي Microsoft 365 باستخدام أداة البحث، ثم تنفيذ ثلاث عمليات بحث مختلفة:

- واحد ل  *أندرسون*

- واحد  *لهندرسون*

- واحد ل  *يورغنسون*

ونظرا لأن الأسماء الثلاثة كلها تنتهي ب "son"، يمكنك إخبار PowerShell بعرض جميع المستخدمين الذين ينتهي اسمهم ب "son". إليك الأمر:

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

تفسير أمر PowerShell هذا هو: الحصول على جميع المستخدمين في اشتراك Microsoft 365 الحالي، ولكن استخدم عامل تصفية يسرد فقط المستخدمين الذين تنتهي أسماء أسمائهم الأخيرة ب "son" (**-Filter '{LastName -like "\*son"}'**). ترمز \* إلى أي مجموعة من الأحرف، وهي أحرف في اسم العائلة للمستخدم.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>يسهل PowerShell for Microsoft 365 طباعة البيانات أو حفظها

يتيح مركز مسؤولي Microsoft 365 عرض قوائم البيانات. فيما يلي مثال لمركز إدارة Skype for Business Online يعرض قائمة بالمستخدمين الذين تم تمكينهم Skype for Business Online:

![مثال على Skype for Business مركز إدارة الإنترنت يعرض قائمة بالمستخدمين الذين تم تمكينهم Skype for Business Online.](../media/o365-powershell-lync-users.png)

لحفظ هذه المعلومات في ملف، يجب لصقها في مستند أو Microsoft Excel ورقة عمل. قد تتطلب كلتا الحالتين تنسيقا إضافيا. بالإضافة إلى ذلك، مركز مسؤولي Microsoft 365 طريقة لطباعة القائمة المعروضة مباشرة.

لحسن الحظ، يمكنك استخدام PowerShell ليس فقط لعرض القائمة ولكن لحفظها في ملف يمكن استيراده بسهولة إلى Excel. فيما يلي مثال لحفظ بيانات المستخدم Skype for Business Online إلى ملف قيم مفصولة بفصول (CSV)، يمكن استيراده بسهولة بعد ذلك ك جدول في ورقة عمل Excel:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

فيما يلي مثال على النتائج:

![مثال على جدول تم استيراده إلى Excel عمل Skype for Business بيانات المستخدم عبر الإنترنت التي تم حفظها في ملف قيم مفصولة بفصول.](../media/o365-powershell-data-in-excel.png)

تفسير أمر PowerShell هذا هو: الحصول على جميع مستخدمي Skype for Business عبر الإنترنت في اشتراك Microsoft 365 الحالي (**Get-CsOnlineUser**)؛ الحصول على اسم المستخدم و UPN والموقع فقط (حدد اسم العرض، **UserPrincipalName، UsageLocation**)؛ ثم احفظ هذه المعلومات في ملف CSV المسمى C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\) SfBUsers.csv" -NoTypeInformation**).

يمكنك أيضا استخدام الخيارات لحفظ هذه القائمة كملف XML أو صفحة HTML. في الواقع، باستخدام أوامر PowerShell الإضافية، يمكنك حفظه مباشرة كملف Excel، مع أي تنسيق مخصص تريده.

يمكنك أيضا إرسال إخراج أمر PowerShell الذي يعرض قائمة مباشرة إلى الطابعة الافتراضية في Windows. إليك مثال على الأمر:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

إليك كيف سيبدو المستند المطبوع:

![مثال لمستند مطبوع كان ناتج أمر PowerShell تم إرساله مباشرة إلى الطابعة الافتراضية في Windows.](../media/o365-powershell-printed-data.png)

تفسير أمر PowerShell هذا هو: الحصول على جميع مستخدمي Skype for Business عبر الإنترنت في اشتراك Microsoft 365 الحالي؛ والحصول على اسم المستخدم و UPN والموقع فقط، ثم إرسال هذه المعلومات إلى الطابعة الافتراضية Windows (**الطابعة** الخارجية).

المستند المطبوع له التنسيق البسيط نفسه الذي يتم عرضه في نافذة الأمر PowerShell. للحصول على نسخة مطبوعة، ما عليك سوى إضافة | **خارج الطابعة** إلى نهاية الأمر.

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>يتيح لك PowerShell for Microsoft 365 إدارة منتجات الخادم

تم تصميم المكونات التي Microsoft 365 للعمل معا. على سبيل المثال، افترض أنك أضفت مستخدما جديدا Microsoft 365، وحدد معلومات مثل قسم المستخدم ورقم هاتفه. عندئذ ستتوفر هذه المعلومات إذا كنت تقوم بالوصول إلى معلومات المستخدم في أي من خدمات Microsoft 365: Skype for Business عبر الإنترنت أو Exchange أو SharePoint.

ولكن هذا للحصول على المعلومات الشائعة التي تمتد عبر مجموعة المنتجات. المعلومات الخاصة بالمنتج، مثل المعلومات حول علبة بريد المستخدم Exchange، لا تتوفر عادة عبر المجموعة. على سبيل المثال، تتوفر معلومات حول تمكين علبة بريد المستخدم أو عدم تمكينها في مركز إدارة Exchange فقط.

لنفترض أنك تريد عمل تقرير يعرض المعلومات التالية لجميع المستخدمين:

- اسم العرض الخاص للمستخدم

- ما إذا كان المستخدم مرخصا Microsoft 365

- ما إذا تم تمكين علبة Exchange الخاصة بالمستخدم

- ما إذا كان المستخدم قد تم تمكينه Skype for Business Online

لا يمكنك بسهولة إنشاء مثل هذا التقرير في مركز مسؤولي Microsoft 365. بدلا من ذلك، يجب إنشاء مستند منفصل لتخزين المعلومات، مثل Excel عمل. بعد ذلك، احصل على كل أسماء المستخدمين ومعلومات الترخيص من مركز مسؤولي Microsoft 365، واحصل على معلومات علبة البريد من مركز إدارة <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a>، واحصل على معلومات Skype for Business عبر الإنترنت من مركز إدارة Skype for Business عبر الإنترنت، ثم ادمج المعلومات.

البديل هو استخدام برنامج PowerShell النصي لتجميع التقرير من أجلك.

المثال التالي البرنامج النصي أكثر تعقيدا من الأوامر التي رأيتها حتى الآن في هذه المقالة. ولكنه يعرض إمكانية استخدام PowerShell لإنشاء طرق عرض معلومات يصعب الحصول عليها بخلاف ذلك. فيما يلي البرنامج النصي لتجميع القائمة التي تحتاج إليها وعرضها:

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

تفسير برنامج PowerShell النصي هذا هو:

1. احصل على جميع المستخدمين في اشتراك Microsoft 365 الحالي وخزن المعلومات في متغير يسمى *$x* (**$x = Get-AzureADUser**).
1. ابدأ حلقة يتم تشغيلها فوق جميع المستخدمين في $x المتغير **(التشويه ($i في $x)**).
1. تعريف متغير *$y* تخزين معلومات علبة بريد المستخدم فيه (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. أضف خاصية جديدة إلى معلومات المستخدم المسماة *IsMailBoxEnabled*. قم بتعيينها إلى قيمة الخاصية IsMailBoxEnabled لعلبة بريد المستخدم (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -value $y.IsMailboxEnabled**).
1. حدد متغيرا *يسمى $y*، واخزن معلومات Skype for Business Online الخاصة بالمستخدم فيه (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. أضف خاصية جديدة إلى معلومات المستخدم المسماة *EnabledForSfB*. قم بتعيينها إلى قيمة الخاصية Enabled الخاصة بمعلومات Skype for Business عبر الإنترنت للمستخدم (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -value $y.Enabled**).
1. عرض قائمة المستخدمين، مع تضمين اسمهم فقط، وما إذا كانوا مرخصين، والخصائص الجديدة التي تشير إلى ما إذا كانت علبة البريد الخاصة بهم تم تمكينها وما إذا تم تمكينها Skype for Business Online (**$x | حدد DisplayName، IsLicensed، IsMailboxEnabled، EnabledforSfB**).

## <a name="see-also"></a>راجع أيضًا

[بدء باستخدام PowerShell Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[إدارة Microsoft 365 المستخدمين والتراخيص والمجموعات باستخدام PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[استخدم Windows PowerShell لإنشاء تقارير في Microsoft 365](use-windows-powershell-to-create-reports-in-microsoft-365.md)