---
title: كيفية تكوين Exchange Server المحلي لاستخدام المصادقة الحديثة المختلطة
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/27/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: تعرف على كيفية تكوين Exchange Server محلي لاستخدام المصادقة الحديثة المختلطة (HMA)، مما يوفر لك مصادقة المستخدم وتخويله بشكل أكثر أمانا.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2ee190a541fdf3e4e77a251e040f2cb69416088c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095741"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>كيفية تكوين Exchange Server المحلي لاستخدام المصادقة الحديثة المختلطة

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

المصادقة الحديثة المختلطة (HMA) هي طريقة لإدارة الهوية التي توفر مصادقة المستخدم وتخويله أكثر أمانا، وهي متوفرة لعمليات النشر المختلطة Exchange الخادم المحلي.

## <a name="definitions"></a>التعاريف

قبل أن نبدأ، يجب أن تكون على دراية ببعض التعريفات:

- HMA للمصادقة \> الحديثة المختلطة

- Exchange المحلي \> EXCH

- \> EXCHANGE ONLINE EXO

أيضا، *إذا كان رسم في هذه المقالة يحتوي على كائن 'رمادي اللون' أو 'باهت' يعني أن العنصر المعروض باللون الرمادي غير مضمن في التكوين الخاص ب HMA*.

## <a name="enabling-hybrid-modern-authentication"></a>تمكين المصادقة الحديثة المختلطة

يعني تشغيل HMA ما يلي:

1. تأكد من تلبية المتطلبات المسبقة قبل البدء.

1. نظرا إلى أن العديد من **المتطلبات الأساسية** شائعة لكل من Skype for Business Exchange، [فإن نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business المحلية وخوادم Exchange](hybrid-modern-auth-overview.md). قم بذلك قبل بدء أي من الخطوات الواردة في هذه المقالة.
متطلبات حول علب البريد المرتبطة التي سيتم إدراجها.

1. إضافة عناوين URL لخدمة الويب المحلية **كأسماء الخدمة الأساسية (SPNs)** في Azure AD. في حالة هجين EXCH مع **مستأجرين متعددين**، يجب إضافة عناوين URL لخدمة الويب المحلية هذه ك SPNs في Azure AD لجميع المستأجرين المختلطين مع EXCH.

1. ضمان تمكين جميع الدلائل الظاهرية ل HMA

1. التحقق من وجود كائن خادم المصادقة EvoSTS

1. تمكين HMA في EXCH.

> [!NOTE]
> هل يدعم إصدار Office MA؟ اطلع على [كيفية عمل المصادقة الحديثة لتطبيقات عميل Office 2013 و Office 2016](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>تأكد من تلبية جميع المتطلبات الأساسية

نظرا إلى أن العديد من المتطلبات الأساسية شائعة لكل من Skype for Business Exchange، راجع [نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business المحلية وخوادم Exchange](hybrid-modern-auth-overview.md). قم بذلك  *قبل*  بدء أي من الخطوات الواردة في هذه المقالة.

> [!NOTE]
> لا يعمل Outlook Web App Exchange لوحة التحكم مع المصادقة الحديثة المختلطة.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>إضافة عناوين URL لخدمة الويب المحلية ك SPNs في Azure AD

تشغيل الأوامر التي تعين عناوين URL لخدمة الويب المحلية ك SPNs Azure AD. يتم استخدام SPNs من قبل أجهزة العميل والأجهزة أثناء المصادقة والتخويل. يجب تسجيل كافة عناوين URL التي يمكن استخدامها للاتصال من الموقع المحلي إلى Azure Active Directory (Azure AD) في Azure AD (وهذا يشمل مساحات الأسماء الداخلية والخارجية).

أولا، جمع كافة عناوين URL التي تحتاج إلى إضافتها في AAD (دليل Azure النشط). تشغيل هذه الأوامر محليا:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

تأكد من أن عملاء عناوين URL قد يتصلون مدرجين كأسماء أساسية لخدمة HTTPS في AAD (دليل Azure النشط). في حالة وجود EXCH في هجين مع **مستأجرين متعددين**، يجب إضافة SPNs HTTPS هذه في AAD (دليل Azure النشط) جميع المستأجرين المختلطين مع EXCH.

1. أولا، اتصل AAD (دليل Azure النشط) [بهذه الإرشادات](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > تحتاج إلى استخدام خيار _الاتصال-MsolService_ من هذه الصفحة لتتمكن من استخدام الأمر أدناه.

2. بالنسبة لعناوين URL المرتبطة Exchange، اكتب الأمر التالي:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   دون (ولقطة شاشة للمقارنة اللاحقة) إخراج هذا الأمر، والذي يجب أن يتضمن عنوان `https://*autodiscover.yourdomain.com*` URL، `https://*mail.yourdomain.com*` ولكن يتكون في الغالب من SPNs التي تبدأ ب `00000002-0000-0ff1-ce00-000000000000/`. إذا كانت هناك `https://` عناوين URL من الموقع الخاص بك مفقودة، فيجب إضافة هذه السجلات المحددة إلى هذه القائمة.

3. إذا لم تتمكن من رؤية سجلات MAPI/HTTP وEWS وActiveSync وOAB وOAB وAudiscover الداخلية في هذه القائمة، فيجب إضافتها باستخدام الأمر أدناه (عناوين URL المثال هي `mail.corp.contoso.com` و `owa.contoso.com`، ولكن يمكنك **استبدال عناوين URL كمثال بعناوين URL الخاصة بك**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. تحقق من إضافة سجلاتك الجديدة عن طريق تشغيل `Get-MsolServicePrincipal` الأمر من الخطوة 2 مرة أخرى، والبحث من خلال الإخراج. قارن القائمة / لقطة الشاشة من قبل بقائمة SPNs الجديدة. يمكنك أيضا التقاط لقطة شاشة للقائمة الجديدة لسجلاتك. إذا نجحت، فسترى عنواني URL الجديدين في القائمة. وفقا لمثالنا، ستتضمن قائمة SPNs الآن عناوين URL `https://mail.corp.contoso.com` المحددة و `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>التحقق من تكوين الدلائل الظاهرية بشكل صحيح

تحقق الآن من تمكين OAuth بشكل صحيح في Exchange على كافة الدلائل الظاهرية التي قد يستخدمها Outlook عن طريق تشغيل الأوامر التالية:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

تحقق من الإخراج للتأكد من تمكين **OAuth** على كل من هذه VDirs، وسوف يبدو شيئا مثل هذا (والشيء الرئيسي الذي يجب أن ننظر إليه هو "OAuth"):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

إذا كان OAuth مفقودا من أي خادم وأي من الدلائل الظاهرية الأربعة، فستحتاج إلى إضافته باستخدام الأوامر ذات الصلة قبل المتابعة ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory) و [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory) و [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) و [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>تأكيد وجود كائن خادم المصادقة EvoSTS

ارجع إلى Exchange Management Shell المحلية لهذا الأمر الأخير. الآن يمكنك التحقق من أن الموقع الخاص بك يحتوي على إدخال لموفر مصادقة evoSTS:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

يجب أن يظهر الإخراج الخاص بك AuthServer لاسم EvoSts مع GUID وينبغي أن تكون الحالة 'Enabled' True. إذا لم تتمكن من رؤية ذلك، يجب تنزيل أحدث إصدار من معالج التكوين المختلط وتشغيله.

> [!NOTE]
> في حالة هجين EXCH مع **مستأجرين متعددين**، يجب أن يظهر الإخراج الخاص بك مصادقة واحدة من اسم `EvoSts - {GUID}` كل مستأجر في مختلط مع EXCH ويجب أن تكون الحالة **الممكنة** True لجميع كائنات AuthServer هذه.

> [!IMPORTANT]
> إذا كنت تقوم بتشغيل Exchange 2010 في بيئتك، فلن يتم إنشاء موفر مصادقة EvoSTS.

## <a name="enable-hma"></a>تمكين HMA

قم بتشغيل الأمر التالي في Exchange Management Shell، محليا، مع \<GUID\> استبدال سطر الأوامر بالسلسلة في البيئة الخاصة بك:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> في الإصدارات القديمة من معالج التكوين المختلط، تمت تسمية EvoSts AuthServer ببساطة باسم EvoSTS دون إرفاق GUID. لا يوجد أي إجراء تحتاج إلى اتخاذه، ما عليك سوى تعديل سطر الأوامر أعلاه ليعكس ذلك عن طريق إزالة جزء GUID من الأمر:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

إذا كان إصدار EXCH Exchange 2016 (CU18 أو أعلى) أو Exchange 2019 (CU7 أو أعلى) وتم تكوين الإصدار المختلط مع تنزيل HCW بعد سبتمبر 2020، فقم بتشغيل الأمر التالي في Exchange Management Shell، المحلي:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> في حالة وجود EXCH في مجموعة مختلطة مع **مستأجرين متعددين**، هناك العديد من كائنات AuthServer الموجودة في EXCH مع المجالات المقابلة لكل مستأجر.  يجب تعيين علامة **IsDefaultAuthorizationEndpoint** إلى true (باستخدام **IsDefaultAuthorizationEndpoint** cmdlet) لأي من كائنات AuthServer هذه. لا يمكن تعيين هذه العلامة إلى true لكافة كائنات Authserver وسيتم تمكين HMA حتى إذا تم تعيين علامة **IsDefaultAuthorizationEndpoint الخاصة بعنصر** AuthServer إلى true.
> 
> بالنسبة إلى المعلمة **DomainName** ، استخدم قيمة مجال المستأجر، والتي تكون عادة في النموذج `contoso.onmicrosoft.com`.

## <a name="verify"></a>التحقق

بمجرد تمكين HMA، سيستخدم تسجيل الدخول التالي للعميل تدفق المصادقة الجديد. لاحظ أن تشغيل HMA فقط لن يؤدي إلى إعادة المصادقة لأي عميل، وقد يستغرق Exchange بعض الوقت لالتقاط الإعدادات الجديدة.

يجب أيضا الضغط باستمرار على المفتاح CTRL في نفس الوقت الذي تنقر فيه بزر الماوس الأيمن فوق أيقونة عميل Outlook (أيضا في علبة الإعلامات Windows) وانقر فوق "حالة الاتصال". ابحث عن عنوان SMTP للعميل مقابل نوع **Authn** من `Bearer\*`، والذي يمثل الرمز المميز للحامل المستخدم في OAuth.

> [!NOTE]
> هل تحتاج إلى تكوين Skype for Business باستخدام HMA؟ ستحتاج إلى مقالتين: واحدة تسرد [الطبولوجيا المدعومة](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)، والأخرى توضح لك [كيفية إجراء التكوين](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>استخدام المصادقة الحديثة المختلطة مع Outlook لنظامي التشغيل iOS وAndroid

إذا كنت عميلا محليا تستخدم خادم Exchange على TCP 443، فاسمح بنسبة استخدام الشبكة من نطاقات IP التالية:

```console
52.125.128.0/20
52.127.96.0/23
```

يتم أيضا توثيق نطاقات عناوين IP هذه في [نقاط النهاية الإضافية غير المضمنة في عنوان IP Office 365 وخدمة ويب URL](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>المواضيع ذات الصلة

[متطلبات تكوين المصادقة الحديثة للانتقال من Office 365 مخصص/ITAR إلى vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
