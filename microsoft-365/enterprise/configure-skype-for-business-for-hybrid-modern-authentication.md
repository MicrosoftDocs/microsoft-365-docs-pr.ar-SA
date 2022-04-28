---
title: كيفية تكوين Skype for Business المحلي لاستخدام المصادقة الحديثة المختلطة
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: تعرف على كيفية تكوين Skype for Business المحلي لاستخدام المصادقة الحديثة المختلطة (HMA)، مما يوفر لك مصادقة المستخدم وتخويله بشكل أكثر أمانا.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f5e48905416f84ed1a4c48f7e6f1a4b6477f73e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093471"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>كيفية تكوين Skype for Business المحلي لاستخدام المصادقة الحديثة المختلطة

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

المصادقة الحديثة، هي طريقة لإدارة الهوية التي توفر مصادقة المستخدم وتخويله أكثر أمانا، وهي متوفرة لخادم Skype for Business المحلي وخادم Exchange المحلي، وتقسيم المجال Skype for Business المختلطة.

> [!IMPORTANT]
> هل ترغب في معرفة المزيد حول المصادقة الحديثة (MA) ولماذا قد تفضل استخدامها في شركتك أو مؤسستك؟ تحقق من [هذا المستند](hybrid-modern-auth-overview.md) للحصول على نظرة عامة. إذا كنت بحاجة إلى معرفة ما هي Skype for Business التي يتم دعمها مع MA، فهذا موثق هنا!

**قبل أن نبدأ**، استخدم هذه المصطلحات:

- المصادقة الحديثة (MA)

- المصادقة الحديثة المختلطة (HMA)

- Exchange المحلي (EXCH)

- Exchange Online (EXO)

- Skype for Business المحلي (SFB)

- Skype for Business Online (SFBO)

أيضا، إذا تضمن رسم في هذه المقالة كائنا رمادي اللون أو باهتا، فهذا يعني أن العنصر المعروض باللون الرمادي **غير** مضمن في التكوين الخاص ب MA.

## <a name="read-the-summary"></a>قراءة الملخص

يقسم هذا الملخص العملية إلى خطوات قد تفقد في أثناء التنفيذ، وهو مناسب لقائمة اختيار شاملة لتتبع مكان تواجدك في العملية.

1. أولا، تأكد من تلبية جميع المتطلبات الأساسية.

1. نظرا إلى أن العديد من **المتطلبات الأساسية** شائعة لكل من Skype for Business Exchange، [راجع مقالة النظرة العامة لقائمة الاختيار ما قبل req](hybrid-modern-auth-overview.md). قم بذلك  *قبل*  بدء أي من الخطوات الواردة في هذه المقالة.

1. جمع المعلومات الخاصة ب HMA التي ستحتاجها في ملف، أو OneNote.

1. تشغيل المصادقة الحديثة ل EXO (إذا لم تكن قيد التشغيل بالفعل).

1. تشغيل المصادقة الحديثة ل SFBO (إذا لم يكن قيد التشغيل بالفعل).

1. تشغيل المصادقة الحديثة المختلطة Exchange المحلي.

1. تشغيل المصادقة الحديثة المختلطة Skype for Business المحلي.

تقوم هذه الخطوات بتشغيل MA ل SFB وSFBO وEXCH وEXO - أي جميع المنتجات التي يمكنها المشاركة في تكوين HMA ل SFB وSFBO (بما في ذلك التبعيات على EXCH/EXO). وبعبارة أخرى، إذا كان المستخدمون موجودين في/لديهم علب بريد تم إنشاؤها في أي جزء من Hybrid (EXO + SFBO أو EXO + SFB أو EXCH + SFBO أو EXCH + SFB)، فسيبدو منتجك النهائي كما يلي:

![يحتوي Skype مختلط 6 لمخطط HMA للأعمال على MA في جميع المواقع الأربعة الممكنة.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

كما ترون هناك أربعة أماكن مختلفة لتشغيل MA! للحصول على أفضل تجربة مستخدم، نوصي بتشغيل MA في جميع المواقع الأربعة من هذه المواقع. إذا لم تتمكن من تشغيل MA في كل هذه المواقع، فقم بضبط الخطوات بحيث تقوم بتشغيل MA فقط في المواقع الضرورية للبيئة الخاصة بك.

راجع [موضوع قابلية الدعم Skype for Business مع MA](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) للمخططات المعتمدة.

> [!IMPORTANT]
> تحقق مرة أخرى من أنك استوفيت جميع المتطلبات الأساسية قبل البدء. ستجد هذه المعلومات في [نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>جمع جميع المعلومات الخاصة ب HMA التي ستحتاجها

بعد التحقق من أنك تستوفي [المتطلبات الأساسية](hybrid-modern-auth-overview.md) لاستخدام المصادقة الحديثة (راجع الملاحظة أعلاه)، يجب إنشاء ملف للاحتفاظ بالمعلومات التي ستحتاجها لتكوين HMA في الخطوات التالية. الأمثلة المستخدمة في هذه المقالة:

- **مجال SIP/SMTP**

  - السابقين. contoso.com (موحد مع Office 365)

- **معرف المستأجر**

  - المعرف الفريد العمومي (GUID) الذي يمثل مستأجر Office 365 (عند تسجيل الدخول إلى contoso.onmicrosoft.com).

- **عناوين URL لخدمة ويب SFB 2015 CU5**

ستحتاج إلى عناوين URL لخدمة الويب الداخلية والخارجية لجميع تجمعات SfB 2015 المنشورة. للحصول على هذه، قم بتشغيل ما يلي من Skype for Business Management Shell:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- السابقين. الداخليه: https://lyncwebint01.contoso.com

- السابقين. الخارجيه: https://lyncwebext01.contoso.com

إذا كنت تستخدم خادم Standard Edition، فسيكون عنوان URL الداخلي فارغا. في هذه الحالة، استخدم مجموعة fqdn لعنوان URL الداخلي.

## <a name="turn-on-modern-authentication-for-exo"></a>تشغيل المصادقة الحديثة ل EXO

اتبع الإرشادات هنا: [Exchange Online: كيفية تمكين المستأجر الخاص بك للمصادقة الحديثة.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>تشغيل المصادقة الحديثة ل SFBO

اتبع الإرشادات هنا: [Skype for Business Online: تمكين المستأجر للمصادقة الحديثة](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>تشغيل المصادقة الحديثة المختلطة Exchange المحلي

اتبع الإرشادات هنا: [كيفية تكوين Exchange Server المحلي لاستخدام المصادقة الحديثة المختلطة](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>تشغيل المصادقة الحديثة المختلطة Skype for Business المحلي

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>إضافة عناوين URL لخدمة الويب المحلية ك SPNs في Azure Active Directory

ستحتاج الآن إلى تشغيل الأوامر لإضافة عناوين URL (التي تم جمعها سابقا) ككيانات الخدمة في SFBO.

> [!NOTE]
> تحدد أسماء كيانات الخدمة (SPNs) خدمات الويب وتربطها بكيان أمان (مثل اسم حساب أو مجموعة) بحيث يمكن للخدمة العمل نيابة عن مستخدم معتمد. يستخدم العملاء الذين يصادقون على خادم المعلومات المضمنة في SPNs.

1. أولا، اتصل ب Azure Active Directory (Azure AD) باستخدام [هذه الإرشادات](/powershell/azure/active-directory/overview).

2. قم بتشغيل هذا الأمر، محليا، للحصول على قائمة بعناوين URL لخدمة ويب SFB.

   لاحظ أن AppPrincipalId يبدأ ب `00000004`. يتوافق هذا مع Skype for Business Online.

   دون (ولقطة شاشة للمقارنة اللاحقة) إخراج هذا الأمر، والذي سيتضمن عنوان URL SE وWS، ولكنه يتكون في الغالب من SPNs التي تبدأ ب `00000004-0000-0ff1-ce00-000000000000/`.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. إذا كانت عناوين URL SFB الداخلية **أو** الخارجية من أماكن العمل مفقودة (على سبيل المثال، https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) وسنحتاج إلى إضافة تلك السجلات المحددة إلى هذه القائمة.

    تأكد من استبدال  *عناوين URL المثال* أدناه بعناوين URL الفعلية في أوامر "إضافة"!

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. تحقق من إضافة سجلاتك الجديدة عن طريق تشغيل الأمر **Get-MsolServicePrincipal** من الخطوة 2 مرة أخرى، والبحث من خلال الإخراج. قارن القائمة أو لقطة الشاشة من قبل بقائمة SPN الجديدة. يمكنك أيضا لقطة شاشة للقائمة الجديدة لسجلاتك. إذا نجحت، فسترى عنواني URL الجديدين في القائمة. وفقا لمثالنا، ستتضمن قائمة SPNs الآن عناوين URL https://lyncwebint01.contoso.com المحددة و https://lyncwebext01.contoso.com/.

### <a name="create-the-evosts-auth-server-object"></a>إنشاء كائن خادم المصادقة EvoSTS

تشغيل الأمر التالي في Skype for Business Management Shell.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>تمكين المصادقة الحديثة المختلطة

هذه هي الخطوة التي تقوم بالفعل بتشغيل MA. يمكن تشغيل جميع الخطوات السابقة مسبقا دون تغيير تدفق مصادقة العميل. عندما تكون مستعدا لتغيير تدفق المصادقة، قم بتشغيل هذا الأمر في Skype for Business Management Shell.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>التحقق

بمجرد تمكين HMA، سيستخدم تسجيل الدخول التالي للعميل تدفق المصادقة الجديد. لاحظ أن تشغيل HMA فقط لن يؤدي إلى إعادة المصادقة لأي عميل. يقوم العملاء بإعادة المصادقة استنادا إلى مدة بقاء الرموز المميزة للمصادقة و/أو الشهادات التي لديهم.

لاختبار أن HMA يعمل بعد تمكينه، سجل الخروج من اختبار عميل SFB Windows وتأكد من النقر فوق "حذف بيانات الاعتماد الخاصة بي". سجل الدخول مرة أخرى. يجب على العميل الآن استخدام تدفق المصادقة الحديثة وسيتضمن تسجيل الدخول الآن **مطالبة Office 365** لحساب 'العمل أو المؤسسة التعليمية'، يتم مشاهدته مباشرة قبل أن يتصل العميل بالخادم ويسجل دخولك.

يجب عليك أيضا التحقق من "معلومات التكوين" لعملاء Skype for Business ل "OAuth Authority". للقيام بذلك على الكمبيوتر العميل، اضغط باستمرار على المفتاح CTRL في الوقت نفسه الذي تنقر فيه بزر الماوس الأيمن فوق أيقونة Skype for Business في علبة الإعلامات Windows. انقر فوق **"معلومات التكوين** " في القائمة التي تظهر. في النافذة "Skype for Business Configuration Information" التي ستظهر على سطح المكتب، ابحث عن ما يلي:

:::image type="content" alt-text="تعرض معلومات التكوين لعميل Skype for Business باستخدام المصادقة الحديثة عنوان URL ل Lync وEWS OAUTH Authority ل https://login.windows.net/common/oauth2/authorize." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

يجب أيضا الضغط باستمرار على المفتاح CTRL في نفس الوقت الذي تنقر فيه بزر الماوس الأيمن فوق أيقونة عميل Outlook (أيضا في علبة الإعلامات Windows) وانقر فوق "حالة الاتصال". ابحث عن عنوان SMTP للعميل مقابل نوع AuthN من 'Bearer\*'، والذي يمثل الرمز المميز للحامل المستخدم في OAuth.

## <a name="related-articles"></a>المقالات ذات الصلة

[الارتباط مرة أخرى إلى نظرة عامة على المصادقة الحديثة](hybrid-modern-auth-overview.md).

هل تحتاج إلى معرفة كيفية استخدام المصادقة الحديثة لعملاء Skype for Business؟ لدينا خطوات هنا: [نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business Exchange](./hybrid-modern-auth-overview.md) المحلية.
