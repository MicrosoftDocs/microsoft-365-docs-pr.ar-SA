---
title: كيفية تكوين Exchange Server لاستخدام المصادقة الحديثة المختلطة
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: تعرف على كيفية تكوين Exchange Server المحلي لاستخدام المصادقة الحديثة المختلطة (HMA)، مما يوفر لك مصادقة مستخدم وتخويل أكثر أمانا.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0889008595717308695c1ad9c5d2a9f1766d1ea
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63568737"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>كيفية تكوين Exchange Server لاستخدام المصادقة الحديثة المختلطة

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

إن المصادقة الحديثة المختلطة (HMA) هي طريقة لإدارة الهويات توفر مصادقة وتخويلا أكثر أمانا للمستخدم، وهي متوفرة Exchange التوزيع المختلط المحلي للخادم.

## <a name="definitions"></a>التعريفات

قبل البدء، يجب أن تكون على دراية ببعض التعريفات:

- HMA "المصادقة الحديثة المختلطة \> "

- Exchange في الموقع \> EXCH

- \> Exchange Online EXO

بالإضافة إلى ذلك، إذا تضمن رسم في هذه المقالة كائنا 'رمادي اللون' أو 'باهت' مما يعني أن العنصر الموضح باللون الرمادي غير مضمن في التكوين الخاص *ب HMA*.

## <a name="enabling-hybrid-modern-authentication"></a>تمكين المصادقة الحديثة المختلطة

يعني تشغيل HMA ما يلي:

1. التأكد من أنك تلبي prereqs قبل البدء.

1. نظرا لأن **العديد** من المتطلبات الأساسية شائعة لكل من Skype for Business Exchange والمصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business Exchange [.](hybrid-modern-auth-overview.md) يمكنك القيام بذلك قبل بدء أي من الخطوات في هذه المقالة.
متطلبات حول علب البريد المرتبطة لإدراجها.

1. إضافة عناوين URL لخدمة ويب المحلي ك أسماء رئيسية للخدمة **(SPNs)** في Azure AD. في حالة وجود EXCH مختلط مع مستأجرين متعددين، يجب إضافة عناوين URL لخدمة الويب هذه ك SPNs في Azure AD لكل المستأجرين المختلطين مع EXCH.

1. التأكد من تمكين كل الدلائل الظاهرية ل HMA

1. التحقق من كائن خادم Auth في EvoSTS

1. تمكين HMA في EXCH.

> [!NOTE]
> هل يدعم إصدارك من Office MA؟ راجع [كيفية عمل المصادقة الحديثة Office 2013 Office عميل 2016](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>تأكد من تلبية كل المتطلبات الأساسية

نظرا لأن العديد من المتطلبات الأساسية شائعة لكل من Skype for Business و Exchange، راجع نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business Exchange [أو](hybrid-modern-auth-overview.md) خوادم. يمكنك القيام  *بذلك*  قبل بدء أي من الخطوات في هذه المقالة.

> [!NOTE]
> Outlook Web App Exchange التحكم باستخدام المصادقة الحديثة المختلطة.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>إضافة عناوين URL لخدمة ويب في الموقع ك SPNs في Azure AD

قم بتشغيل الأوامر التي تعمل على تعيين عناوين URL لخدمة ويب في الموقع ك Azure AD SPNs. يتم استخدام SPNs بواسطة أجهزة العميل والأجهزة أثناء المصادقة والتخويل. يجب تسجيل كل عناوين URL التي يمكن استخدامها للاتصال من موقع Azure Active Directory المحلي (Azure AD) في Azure AD (يشمل ذلك مساحات الاسم الداخلية والخارجية).

أولا، قم بجمع كل عناوين URL التي تحتاج إلى إضافتها في AAD (دليل Azure النشط). تشغيل هذه الأوامر في الموقع:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

تأكد من أن عملاء عناوين URL قد يتصلوا مدرجين كلأسماء الأساسية لخدمة HTTPS في AAD (دليل Azure النشط). في حالة وجود EXCH مختلط مع مستأجرين متعددين، يجب إضافة HTTPS SPNs هذه في AAD (دليل Azure النشط) من جميع المستأجرين المختلطين مع EXCH.

1. أولا، اتصل AAD (دليل Azure النشط) [باستخدام هذه الإرشادات](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > يجب استخدام خيار الاتصال _MsolService_ من هذه الصفحة لكي تتمكن من استخدام الأمر أدناه.

2. بالنسبة إلى Exchange URL ذات الصلة، اكتب الأمر التالي:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   دون (ولشاشة الشاشة للمقارنة لاحقا) `https://*autodiscover.yourdomain.com*` `https://*mail.yourdomain.com*` إخراج هذا الأمر، الذي يجب أن يتضمن عنوان URL وURL، ولكن في الغالب يتكون من SPNs التي تبدأ ب `00000002-0000-0ff1-ce00-000000000000/`. إذا كانت هناك `https://` عناوين URL مفقودة من موقعك في الموقع، يجب إضافة تلك السجلات المحددة إلى هذه القائمة.

3. إذا لم تظهر سجلات MAPI/HTTP وEWS و ActiveSync و OAB و Autodiscover الداخلية والخارجية في هذه القائمة، فيجب إضافتها باستخدام الأمر أدناه (`mail.corp.contoso.com``owa.contoso.com`مثال عناوين URL هي و ، ولكن يمكنك استبدال عناوين URL كمثال بعناوي URL الخاصة **بك**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. تحقق من إضافة السجلات الجديدة عن طريق تشغيل `Get-MsolServicePrincipal` الأمر من الخطوة 2 مرة أخرى، وبحث الإخراج. قارن القائمة / لقطة الشاشة من قبل بالقائمة الجديدة ل SPNs. قد تأخذ أيضا لقطة شاشة للقائمة الجديدة لسجلاتك. إذا نجحت، سترى قائمتي URL جديدتين في القائمة. من خلال مثالنا، ستتضمن قائمة SPNS الآن عناوين URL `https://mail.corp.contoso.com` و `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>التحقق من تكوين الدلائل الظاهرية بشكل صحيح

تحقق الآن من تمكين OAuth بشكل صحيح في Exchange على كل الدلائل Outlook الظاهرية التي قد تستخدمها عن طريق تشغيل الأوامر التالية:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

تحقق من الإخراج للتأكد من تمكين **OAuth** على كل واحد من هذه VDirs، سيبدو مثل هذا (والشيء الرئيسي الذي يجب النظر له هو 'OAuth'):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

إذا كانت OAuth مفقودة من أي خادم وأي من الدلائل الظاهرية الأربعة، يجب إضافتها باستخدام الأوامر ذات الصلة قبل المتابعة ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory) و [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory) و [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) و [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>تأكيد وجود كائن خادم EvoSTS Auth

العودة إلى الموقع Exchange Management Shell لهذا الأمر الأخير. يمكنك الآن التحقق من أن لديك إدخالا لموفر مصادقة evoSTS:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

يجب أن يظهر الإخراج الخاص بك AuthServer من Name EvoSts مع GUID ويجب أن تكون الحالة 'Enabled' True. إذا لم تشاهد ذلك، يجب تنزيل أحدث إصدار من معالج التكوين المختلط وتشغيله.

> [!NOTE]
> في حالة وجود EXCH مختلط مع مستأجرين متعددين، يجب أن يظهر الإخراج AuthServer `EvoSts - {GUID}` واحد من الاسم لكل مستأجر مختلط مع EXCH ويجب  أن تكون الحالة تمكين True لكل كائنات AuthServer هذه.

> [!IMPORTANT]
> إذا كنت تقوم بتشغيل Exchange 2010 في بيئتك، فلن يتم إنشاء موفر مصادقة EvoSTS.

## <a name="enable-hma"></a>تمكين HMA

تشغيل الأمر التالي في Exchange Management Shell\<GUID\>، المحلية، مع استبدال السلسلة في بيئتك في سطر الأوامر:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> في الإصدارات القديمة من معالج التكوين المختلط، كان EvoSts AuthServer يسمى ببساطة EvoSTS دون إرفاق GUID. لا يوجد أي إجراء تحتاج إلى اتخاذه، ما عليك سوى تعديل سطر الأوامر أعلاه لتعكس ذلك عن طريق إزالة جزء GUID من الأمر:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

إذا كان إصدار EXCH هو Exchange 2016 (CU18 أو إصدار أحدث) أو Exchange 2019 (CU7 أو إصدار أحدث) تم تكوينه مع HCW تم تنزيله بعد سبتمبر 2020، فشغل الأمر التالي في Exchange Management Shell، المحلي:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> في حالة وجود EXCH مختلط مع مستأجرين متعددين، هناك عدة كائنات AuthServer موجودة في EXCH مع مجالات مقابلة لكل مستأجر.  يجب تعيين علامة **IsDefaultAuthorizationEndpoint** إلى true (باستخدام **أمر cmdlet IsDefaultAuthorizationEndpoint** ) لأي من كائنات AuthServer هذه. لا يمكن تعيين هذه العلامة إلى true لكل كائنات Authserver وقد يتم تمكين HMA حتى لو تم تعيين علامة **IsDefaultAuthorizationEndpoint** الخاصة ب كائن AuthServer هذه إلى true.
> 
> بالنسبة إلى **المعلمة DomainName** ، استخدم قيمة مجال المستأجر، التي تكون عادة في النموذج `contoso.onmicrosoft.com`.

## <a name="verify"></a>التحقق

بمجرد تمكين HMA، سيستخدم تسجيل الدخول التالي للعميل تدفق الوثب الجديد. تجدر الإشارة إلى أن تشغيل HMA فقط لن يؤدي إلى إعادة نطق أي عميل، وقد يستغرق الأمر بعض الوقت Exchange الإعدادات الجديدة.

يجب أيضا الضغط باستمرار على المفتاح CTRL في الوقت نفسه الذي تنقر فيه بضغطة زر الماوس الأيمن فوق أيقونة عميل Outlook (أيضا في علبة إعلامات Windows) والنقر فوق "حالة الاتصال". ابحث عن عنوان SMTP للعميل مقابل نوع **Authn** `Bearer\*`من ، الذي يمثل الرمز المميز الخاص بالحمل المستخدم في OAuth.

> [!NOTE]
> هل تحتاج إلى تكوين Skype for Business HMA؟ ستحتاج إلى مقالتين: مقالة تسرد طبول مدعمة، ومقالة توضح لك كيفية [القيام بهذا التكوين](configure-skype-for-business-for-hybrid-modern-authentication.md).[](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>استخدام المصادقة الحديثة المختلطة مع Outlook لنظامي التشغيل iOS وAndroid

إذا كنت عميلا في الموقع تستخدم خادم Exchange TCP 443، فاسمح بزحام الشبكة من نطاقات IP التالية:

```console
52.125.128.0/20
52.127.96.0/23
```

تم توثيق نطاقات عناوين IP هذه أيضا في نقاط النهاية الإضافية غير المضمنة في [Office 365 IP وخدمة URL على الويب](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>المواضيع ذات الصلة

[متطلبات تكوين المصادقة الحديثة للانتقال من Office 365/ITAR إلى vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
