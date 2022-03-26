---
title: كيفية تكوين Skype for Business لاستخدام المصادقة الحديثة المختلطة
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: تعرف على كيفية تكوين Skype for Business المحلي لاستخدام المصادقة الحديثة المختلطة (HMA)، مما يوفر لك مصادقة مستخدم وتخويل أكثر أمانا.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd42aa6befdbb646217a9829dd59c0821fbd29d3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63568804"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>كيفية تكوين Skype for Business لاستخدام المصادقة الحديثة المختلطة

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

المصادقة الحديثة، هي طريقة لإدارة الهويات توفر مصادقة مستخدم أكثر أمانا وتخويلا، وهي متوفرة للخادم Skype for Business في الموقع وخادم Exchange في الموقع، وs split-domain Skype for Business المختلطة.

> [!IMPORTANT]
> هل ترغب في معرفة المزيد حول المصادقة الحديثة (MA) ولماذا تفضل استخدامها في شركتك أو مؤسستك؟ راجع [هذا المستند للحصول](hybrid-modern-auth-overview.md) على نظرة عامة. إذا كنت بحاجة إلى معرفة Skype for Business التي يتم دعمها مع MA، هذا موثق هنا!

**قبل البدء،** استخدم هذه المصطلحات:

- المصادقة الحديثة (MA)

- المصادقة الحديثة المختلطة (HMA)

- Exchange المحلي (EXCH)

- Exchange Online (EXO)

- Skype for Business المحلي (SFB)

- Skype for Business Online (SFBO)

بالإضافة إلى ذلك، إذا تضمن رسم في هذه المقالة كائنا رمادي اللون أو خافتا، فهذا يعني أن العنصر الموضح باللون الرمادي غير مضمن في التكوين الخاص ب MA.

## <a name="read-the-summary"></a>قراءة الملخص

يجزم هذا الملخص العملية إلى خطوات قد تفقد أثناء التنفيذ، كما أنه جيد لقائمة اختيار شاملة لتعقب مكان وجودك في العملية.

1. أولا، تأكد من تلبية كل المتطلبات الأساسية.

1. نظرا لأن **العديد من المتطلبات** الأساسية شائعة لكل من Skype for Business Exchange، راجع مقالة نظرة عامة لقائمة [اختيار ما قبل إعادة التدقيق](hybrid-modern-auth-overview.md). يمكنك القيام  *بذلك*  قبل بدء أي من الخطوات في هذه المقالة.

1. جمع المعلومات الخاصة ب HMA التي ستحتاج إليها في ملف أو OneNote.

1. تشغيل المصادقة الحديثة ل EXO (إذا لم تكن قد تم تشغيلها بالفعل).

1. تشغيل المصادقة الحديثة ل SFBO (إذا لم تكن قد تم تشغيلها بالفعل).

1. تشغيل المصادقة الحديثة المختلطة Exchange في الموقع.

1. تشغيل المصادقة الحديثة المختلطة Skype for Business في الموقع.

هذه الخطوات تشغيل MA ل SFB و SFBO و EXCH و EXO - أي كل المنتجات التي يمكنها المشاركة في تكوين HMA ل SFB و SFBO (بما في ذلك التبعيات على EXCH/EXO). بعبارة أخرى، إذا كان المستخدمون في علبة بريد تم إنشاؤها في/لديهم علب بريد تم إنشاؤها في أي جزء من المختلط (EXO + SFBO أو EXO + SFB أو EXCH + SFBO أو EXCH + SFB)، سيبدو المنتج النهائي كما يلي:

![تم Skype مختلط Skype HMA للأعمال على MA في كل المواقع الأربعة المحتملة.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

كما ترى، هناك أربعة أماكن مختلفة ل تشغيل MA! للحصول على أفضل تجربة مستخدم، نوصيك تشغيل MA في كل المواقع الأربعة. إذا لم تتمكن من تشغيل MA في كل هذه المواقع، فاضبط الخطوات بحيث يمكنك تشغيل MA فقط في المواقع الضرورية لمواقع بيئتك.

راجع [موضوع قابلية الدعم Skype for Business MA](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) للحصول على طبول معتمدة.

> [!IMPORTANT]
> تحقق مرة أخرى من أنك قد أوفيت بكل المتطلبات الأساسية قبل البدء. ستجد هذه المعلومات في نظرة [عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>تجميع كل المعلومات الخاصة ب HMA التي ستحتاج إليها

بعد التحقق مرة أخرى من أنك تلبي المتطلبات الأساسية لاستخدام المصادقة الحديثة (راجع الملاحظة أعلاه)، يجب إنشاء ملف لإحاطة المعلومات التي ستحتاج إليها لتكوين HMA في الخطوات القادمة.[](hybrid-modern-auth-overview.md) الأمثلة المستخدمة في هذه المقالة:

- **مجال SIP/SMTP**

  - على Ex. contoso.com (يتم الاتحاد مع Office 365)

- **"مستأجر"**

  - الم GUID الذي يمثل Office 365 المستأجر (عند تسجيل الدخول إلى contoso.onmicrosoft.com).

- **عناوين URL لخدمة ويب ل SFB 2015 CU5**

ستحتاج إلى عناوين URL لخدمة الويب الداخلية والخارجية لكل تجمعات SfB 2015 التي تم نشرها. للحصول على هذه، تشغيل ما يلي من Skype for Business Management Shell:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- على Ex. داخلي: https://lyncwebint01.contoso.com

- على Ex. خارجي: https://lyncwebext01.contoso.com

إذا كنت تستخدم خادم Standard Edition، سيكون عنوان URL الداخلي فارغا. في هذه الحالة، استخدم fqdn الخاص بالتجمع ل URL الداخلي.

## <a name="turn-on-modern-authentication-for-exo"></a>تشغيل المصادقة الحديثة ل EXO

اتبع الإرشادات الواردة هنا: [Exchange Online: كيفية تمكين المستأجر للمصادقة الحديثة.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>تشغيل المصادقة الحديثة ل SFBO

اتبع الإرشادات الواردة هنا: [Skype for Business عبر الإنترنت: تمكين المستأجر من المصادقة الحديثة](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>تشغيل المصادقة الحديثة المختلطة Exchange في الموقع

اتبع الإرشادات الواردة هنا: كيفية تكوين Exchange Server [لاستخدام المصادقة الحديثة المختلطة](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>تشغيل المصادقة الحديثة المختلطة Skype for Business في الموقع

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>إضافة عناوين URL لخدمة ويب في الموقع ك SPNs في Azure Active Directory

ستحتاج الآن إلى تشغيل الأوامر لإضافة عناوين URL (التي تم تجميعها سابقا) كخدمات رئيسية في SFBO.

> [!NOTE]
> تحدد الأسماء الأساسية للخدمة (SPNs) خدمات الويب وتقرنها بأهمية أمان (مثل اسم حساب أو مجموعة) بحيث يمكن للخدمة التصرف بالنيابة عن مستخدم معتمد. يستخدم العملاء الذين يصادقون على خادم المعلومات المضمنة في SPNs.

1. أولا، اتصل ب Azure Active Directory (Azure AD) [باستخدام هذه الإرشادات](/powershell/azure/active-directory/overview).

2. يمكنك تشغيل هذا الأمر، في الموقع، للحصول على قائمة عناوين URL لخدمة SFB على الويب.

   لاحظ أن AppPrincipalId يبدأ ب `00000004`. يتوافق هذا مع Skype for Business Online.

   دون (لقطة شاشة للمقارنة لاحقا) إخراج هذا الأمر، الذي سيتضمن عنوان URL SE و WS، ولكن في الغالب يتكون من SPNs التي تبدأ ب `00000004-0000-0ff1-ce00-000000000000/`.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. إذا **كانت عناوين URL** SFB الداخلية أو الخارجية من الموقع المحلي مفقودة ( https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) على سبيل المثال، وسنحتاج إلى إضافة تلك السجلات المحددة إلى هذه القائمة.

    تأكد من استبدال عناوين  *URL* كمثال أدناه مع عناوين URL الفعلية في الأمر إضافة!

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. تحقق من إضافة سجلاتك الجديدة عن طريق تشغيل الأمر **Get-MsolServicePrincipal** من الخطوة 2 مرة أخرى، وبحث الإخراج. قارن القائمة أو لقطة الشاشة من قبل بالقائمة الجديدة ل SPNs. يمكنك أيضا لقطة شاشة للقائمة الجديدة لسجلاتك. إذا نجحت، سترى قائمتي URL جديدتين في القائمة. من خلال مثالنا، ستتضمن قائمة SPNS الآن عناوين URL https://lyncwebint01.contoso.com و https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>إنشاء كائن خادم EvoSTS Auth

تشغيل الأمر التالي في Skype for Business Management Shell.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>تمكين المصادقة الحديثة المختلطة

هذه هي الخطوة التي يتم فيها تشغيل MA فعليا. يمكن تشغيل كل الخطوات السابقة مسبقا دون تغيير تدفق مصادقة العميل. عندما تكون جاهزا لتغيير تدفق المصادقة، يمكنك تشغيل هذا الأمر في Skype for Business Management Shell.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>التحقق

بمجرد تمكين HMA، سيستخدم تسجيل الدخول التالي للعميل تدفق الوثب الجديد. تجدر الإشارة إلى أن تشغيل HMA فقط لن يؤدي إلى إعادة نطق أي عميل. يقوم العملاء بالاستناد إلى مدة عمل الرموز المميزة و/أو السهام التي لديهم.

لاختبار أن HMA يعمل بعد تمكينه، سجل الخروج من عميل SFB Windows وتأكد من النقر فوق "حذف بيانات الاعتماد الخاصة بي". سجل الدخول مرة أخرى. يجب على العميل الآن استخدام تدفق "اونوث الحديث" وستتضمن عملية تسجيل الدخول الآن مطالبة **Office 365** لحساب "العمل أو المدرسة"، يتم اشاهدتها مباشرة قبل اتصال العميل للخادم وتسجيل دخولك.

يجب أيضا التحقق من "معلومات التكوين" Skype for Business العملاء عن "مرجع OAuth". للقيام بذلك على الكمبيوتر العميل، اضغط باستمرار على المفتاح CTRL في الوقت نفسه الذي تنقر فيه ب الماوس الأيمن فوق Skype for Business في Windows الإعلامات. انقر **فوق معلومات التكوين** في القائمة التي تظهر. في نافذة "Skype for Business التكوين" التي ستظهر على سطح المكتب، ابحث عن ما يلي:

:::image type="content" alt-text="تعرض معلومات تكوين عميل Skype for Business باستخدام المصادقة الحديثة عنوان URL مرجعي Lync وEWS OAUTH ل https://login.windows.net/common/oauth2/authorize." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

يجب أيضا الضغط باستمرار على المفتاح CTRL في الوقت نفسه الذي تنقر فيه بضغطة زر الماوس الأيمن فوق أيقونة عميل Outlook (أيضا في علبة إعلامات Windows) والنقر فوق "حالة الاتصال". ابحث عن عنوان SMTP للعميل مقابل نوع AuthN 'Bearer\*'، الذي يمثل الرمز المميز الخاص بالحمل المستخدم في OAuth.

## <a name="related-articles"></a>المقالات ذات الصلة

[ارجع إلى نظرة عامة حول المصادقة الحديثة](hybrid-modern-auth-overview.md).

هل تحتاج إلى معرفة كيفية استخدام المصادقة الحديثة لعملاء Skype for Business؟ لدينا خطوات هنا: نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business Exchange[.](./hybrid-modern-auth-overview.md)
