---
title: نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع الخوادم Skype for Business Exchange
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 12/03/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: في هذه المقالة، ستتعرف على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع الخوادم Skype for Business Exchange.
ms.openlocfilehash: efce3b5a04f2e9500330cab87d7ba8e62ca49db0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63569336"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business Exchange

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise Office 365 Enterprise.*

_المصادقة_ الحديثة هي طريقة لإدارة الهويات توفر مصادقة مستخدم وتخويل أكثر أمانا. وهي متوفرة Office 365 المختلطة ل Skype for Business الخادم Exchange وخادم ويب Exchange، وs split-domain Skype for Business المختلطة. ترتبط هذه المقالة بالم مستندات ذات صلة حول المتطلبات الأساسية وإعداد/تعطيل المصادقة الحديثة وبعض العميل ذي الصلة (على المثال. Outlook Skype العملاء).

- [ما هي المصادقة الحديثة؟](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [ما هي التغييرات التي يتم إدخالها عند استخدام المصادقة الحديثة؟](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [التحقق من حالة المصادقة الحديثة لبيئة العمل المحلية](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [هل تلبي متطلبات المصادقة الحديثة؟](#do-you-meet-modern-authentication-prerequisites)
- [ما الذي أحتاج إلى معرفته أيضا قبل البدء؟](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>ما هي المصادقة الحديثة؟
<a name="BKMK_WhatisModAuth"> </a>

المصادقة الحديثة هي مصطلح عام لمزيج من أساليب المصادقة والتخويل بين عميل (على سبيل المثال، الكمبيوتر المحمول أو هاتفك) وخادم، بالإضافة إلى بعض إجراءات الأمان التي تعتمد على سياسات الوصول التي قد تكون ملما بها بالفعل. وهي تتضمن:

- **أساليب المصادقة**: المصادقة متعددة العوامل (MFA)؛ مصادقة البطاقة الذكية؛ المصادقة المستندة إلى شهادة العميل
- **أساليب التفويض**: تنفيذ Microsoft للتخويل المفتوح (OAuth)
- **سياسات الوصول الشرطي**: الوصول الشرطي إلى إدارة تطبيقات الأجهزة المحمولة (MAM) و Azure Active Directory (Azure AD)

توفر إدارة هويات المستخدمين باستخدام المصادقة الحديثة للمسؤولين العديد من الأدوات المختلفة لاستخدامها عندما يتعلق الأمر بتأمين الموارد، كما توفر أساليب أكثر أمانا لإدارة الهويات لكل من السيناريوهات المحلية (Exchange و Skype for Business) و Exchange المختلطة و Skype for Business المختلطة/split-domain.

ونظرا لأن Skype for Business يعمل بشكل وثيق مع Exchange، فإن سلوك تسجيل الدخول Skype for Business سيتأثر المستخدمون العميلون حالة المصادقة الحديثة Exchange. ينطبق أيضا إذا كان لديك Skype for Business مختلط للمجال المنقسم، حيث يكون لديك كل من Skype for Business Online و Skype for Business المحلية، مع المستخدمين الذين يتم وضعهم في الموقعين.

لمزيد من المعلومات حول المصادقة الحديثة في Office 365، راجع Office 365 [دعم تطبيق العميل - المصادقة متعددة العوامل](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> بحلول أغسطس 2017، سيتم تمكين Office 365 المستأجرين الجدد الذين Skype for Business عبر الإنترنت Exchange عبر الإنترنت بالمصادقة الحديثة بشكل افتراضي. لن يقوم المستأجرون الموجودون مسبقا بتغيير في حالة MA الافتراضية الخاصة بهم، ولكن جميع المستأجرين الجدد يدعمون تلقائيا المجموعة الموسعة من ميزات الهوية التي تراها مدرجة أعلاه. للتحقق من حالة MA، راجع المقطع التحقق من حالة المصادقة الحديثة في البيئة [المحلية](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .

## <a name="what-changes-when-i-use-modern-authentication"></a>ما هي التغييرات التي يتم إدخالها عند استخدام المصادقة الحديثة؟
<a name="BKMK_WhatChanges"> </a>

عند استخدام المصادقة الحديثة مع خادم Skype for Business أو Exchange المحلي، لا يزال المستخدمون المحليون يصادقون، ولكن  تتغير قصة الإذن بالوصول إلى الموارد (مثل الملفات أو رسائل البريد  الإلكتروني). هذا هو السبب في أنه على الرغم من أن المصادقة الحديثة حول اتصال العميل وخادم الخدمة، إلا أن الخطوات التي تم اتخاذها أثناء تكوين MA تؤدي إلى تعيين evoSTS (خدمة رموز الأمان المميزة المستخدمة بواسطة Azure AD) على أنها خادم مصادقة ل Skype for Business وخادم Exchange المحلي.

يتيح التغيير إلى evoSTS للخوادم المحلي الاستفادة من OAuth (إصدار الرمز المميز) لمصادقة عملائك، كما يتيح أيضا استخدام أساليب الأمان الشائعة في السحابة (مثل المصادقة متعددة العوامل). بالإضافة إلى ذلك، يصدر evoSTS الرموز المميزة التي تسمح للمستخدمين بطلب الوصول إلى الموارد دون توفير كلمة المرور الخاصة بهم كجزء من الطلب. بغض النظر عن مكان تهيئة المستخدمين لديك (من الإنترنت أو المحلي)، و بغض النظر عن الموقع الذي يستضيف المورد المطلوب، سيصبح EvoSTS أساس تفويض المستخدمين والعملاء بمجرد تكوين المصادقة الحديثة.

على سبيل المثال، إذا كان عميل Skype for Business يحتاج إلى الوصول إلى Exchange الخادم للحصول على معلومات التقويم نيابة عن مستخدم، فإنه يستخدم مكتبة مصادقة Microsoft (MSAL) للقيام بذلك. إن MSAL هي مكتبة رموز تم تصميمها لجعل الموارد الآمنة في الدليل متوفرة للتطبيقات العميلة باستخدام رموز OAuth المميزة بالأمان. تعمل MSAL مع OAuth للتحقق من صحة المطالبات وتبادل الرموز المميزة (بدلا من كلمات المرور)، لمنح المستخدم حق الوصول إلى مورد. في الماضي، كانت السلطة في معاملة مثل هذه-- الخادم الذي يعرف كيفية التحقق من صحة مطالبات المستخدمين وكيفية إصدار الرموز المميزة المطلوبة-- قد تكون خدمة رموز الأمان المميزة المحلية، أو حتى خدمات الأمان العامة ل Active Directory. ومع ذلك، فإن المصادقة الحديثة تمركز هذه السلطة باستخدام Azure AD.

وهذا يعني أيضا أنه على الرغم من أن بيئتي Exchange و Skype for Business قد تكون كلها في الموقع المحلي، إلا أن الخادم المعتمد سيكون متصلا بالإنترنت، ويجب أن تكون البيئة المحلية لديك قادرة على إنشاء اتصال باشتراك Office 365 في السحابة والمحافظة عليه (ومثيل Azure AD الذي يستخدمه اشتراكك دليله).

ما الذي لا يتغير؟ سواء كنت في مجال مختلط منقسم أو تستخدم Skype for Business وخادم Exchange، يجب أن يقوم جميع المستخدمين أولا بالمصادقة *على الخادم في الموقع.* في تنفيذ مختلط للمصادقة الحديثة، يشير _كل من Lyncdiscovery_ و _Autodiscovery_ إلى الخادم الخاص بك في الموقع.

> [!IMPORTANT]
> إذا كنت بحاجة إلى معرفة Skype for Business المعينة المعتمدة مع MA، يتم توثيق ذلك [هنا](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>التحقق من حالة المصادقة الحديثة لبيئة العمل المحلية
<a name="BKMK_CheckStatus"> </a>

نظرا لأن المصادقة الحديثة تغير خادم التخويل المستخدم عند تطبيق الخدمات على OAuth/S2S، يجب معرفة ما إذا كانت المصادقة الحديثة تم تمكينها أو تعطيلها لبيئات Skype for Business وبيئات Exchange المحلية. يمكنك التحقق من الحالة على خوادم Exchange عن طريق تشغيل الأمر PowerShell التالي:

```powershell
Get-OrganizationConfig | ft OAuth*
```

إذا كانت قيمة الخاصية _OAuth2ClientProfileEnabled_ **False**، يتم تعطيل المصادقة الحديثة.

لمزيد من المعلومات حول Get-OrganizationConfig cmdlet، راجع [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

يمكنك التحقق من Skype for Business من خلال تشغيل الأمر PowerShell التالي:

```powershell
Get-CSOAuthConfiguration
```

إذا كان الأمر يرجع خاصية _OAuthServers_ فارغة، أو إذا كانت قيمة الخاصية _ClientADALAuthOverride_ غير مسموح بها، يتم تعطيل المصادقة الحديثة.

لمزيد من المعلومات حول Get-CsOAuthConfiguration cmdlet، راجع [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>هل تلبي متطلبات المصادقة الحديثة؟

تحقق من هذه العناصر وتحقق من قائمتك قبل المتابعة:

- **Skype for Business محدد**
  - يجب أن يكون لدى كل الخوادم تحديث تراكمي ل مايو 2017 (CU5) Skype for Business Server 2015 أو إصدار لاحق
    - **استثناء** - يمكن أن يكون الجهاز الفرعي (SBA) ل قابلية التشغيل على الإصدار الحالي (استنادا إلى Lync 2013)
  - يضاف مجال SIP كمجال مسترد في Office 365
  - يجب أن يكون لدى كل الأطراف الأمامية ل SFB اتصالات الصادرة بالإنترنت، إلى عناوين URL للمصادقة في Office 365 (TCP 443) وCRLS الجذر للشهادات المعروفة (TCP 80) المدرجة في الصفوف 56 و125 من قسم "Microsoft 365 Common و Office" من [عناوين URL في Office 365 ونطاقات عناوين IP](urls-and-ip-address-ranges.md).

- **Skype for Business المحلية في بيئة Office 365 مختلطة**
  - نشر Skype for Business Server 2019 مع تشغيل كل الخوادم Skype for Business Server 2019.
  - نشر Skype for Business Server 2015 مع تشغيل كل الخوادم Skype for Business Server 2015.
  - نشر مع إصداري خادم مختلفين كحد أقصى كما هو مذكور أدناه:
    - Skype خاص بخادم الأعمال 2015
    - Skype خاص بخادم الأعمال 2019
  - يجب أن Skype for Business كافة الخوادم على التحديثات التراكمية الأخيرة مثبتة، [راجع](/skypeforbusiness/sfb-server-updates) Skype for Business Server الجديدة للعثور على كل التحديثات المتوفرة وإدارتها.
  - لا يوجد Lync Server 2010 أو 2013 في البيئة المختلطة.

>[!NOTE]
>إذا كانت Skype for Business الأمامية تستخدم خادما وكيلا للوصول إلى الإنترنت، فيجب إدخال عنوان IP للخادم الوكيل رقم المنفذ المستخدم في مقطع التكوين لملف web.config لكل واجهة أمامية.

- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> تأكد من الاشتراك في موجز RSS Office 365 [عناوين URL وIP](urls-and-ip-address-ranges.md) لتظل على مستجدات القوائم الأخيرة من عناوين URL المطلوبة.

- **Exchange Server محدد**
  - أنت تستخدم Exchange 2013 CU19 أو Exchange server 2016 CU8 أو لأعلى أو Exchange Server CU1 والي أعلى.
  - لا يوجد Exchange 2010 في البيئة.
  - لم يتم تكوين إيقاف تشغيل SSL. يتم دعم إنهاء SSL و إعادة تشفيره.
  - في حال كانت بيئتك تستخدم بنية أساسية للخادم الوكيل للسماح للخوادم بالاتصال بالإنترنت، تأكد من أن كل خوادم Exchange لديها الخادم الوكيل المحدد في الخاصية [InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server المحلية في بيئة Office 365 مختلطة**

  - إذا كنت تستخدم Exchange Server 2013، فيجب أن يكون دور خادم واحد على الأقل مثبتا على علبة البريد وخادم Client Access. في حين أنه من الممكن تثبيت أدوار "علبة البريد" و"وصول العميل" على خوادم منفصلة، إلا أننا نوصي بشدة بتثبيت كلا الدورين على الخادم نفسه لتوفير المزيد من الوثوقية والأداء المحسن.
  - إذا كنت تستخدم Exchange 2016 أو إصدار أحدث، فيجب أن يكون دور خادم علبة البريد مثبتا على خادم واحد على الأقل.
  - لا يوجد أي Exchange 2007 أو 2010 في البيئة المختلطة.
  - يجب Exchange تثبيت التحديثات التراكمية الأخيرة لكل الخوادم، راجع ترقية Exchange إلى التحديثات [](/exchange/plan-and-deploy/install-cumulative-updates) التراكمية الأخيرة للعثور على كل التحديثات المتوفرة وإدارتها.

- **Exchange العميل والبروتوكول**

    يتم تحديد توفر المصادقة الحديثة من خلال تركيبة العميل والبروتوكول والتكوين. إذا لم تكن المصادقة الحديثة معتمدة من قبل العميل والبروتوكول و/أو التكوين، فإن العميل سيستمر في استخدام المصادقة القديمة.
  
    يدعم العملاء والبروتوكولات التالية المصادقة الحديثة مع Exchange عند تمكين المصادقة الحديثة في البيئة:

  |**العملاء**|**البروتوكول الأساسي**|**ملاحظات**|
  |:-----|:-----|:-----|
  |Outlook 2013 واللاحقة  <br/> |MAPI عبر HTTP  <br/> |يجب تمكين MAPI عبر HTTP ضمن Exchange لاستخدام المصادقة الحديثة مع هؤلاء العملاء (تمكين أو True لتثبيتات جديدة لحزمة خدمة Exchange 2013 1 والأعلى)؛ لمزيد من المعلومات، راجع كيفية عمل المصادقة الحديثة لتطبيقات عميل [Office 2013 و Office 2016](modern-auth-for-office-2013-and-2016.md).  <br/> تأكد من تشغيل الحد الأدنى المطلوب من إصدار Outlook؛ راجع التحديثات الأخيرة لإصدارات Outlook التي تستخدم Windows [Installer (MSI)](/officeupdates/outlook-updates-msi) .  <br/> |
  |Outlook 2016 for Mac واللاحقة  <br/> |Exchange Web Services  <br/> |  <br/> |
  |Outlook لنظامي التشغيل iOS وAndroid  <br/> | تقنية مزامنة Microsoft <br/> |راجع [استخدام المصادقة الحديثة المختلطة مع Outlook لنظامي التشغيل iOS وAndroid](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) للحصول على مزيد من المعلومات.  <br/> |
  |Exchange ActiveSync العملاء (على سبيل المثال، بريد iOS11)  <br/> |Exchange ActiveSync  <br/> |بالنسبة Exchange ActiveSync العملاء الذين يدعمون المصادقة الحديثة، يجب إعادة إنشاء ملف التعريف للتبديل من المصادقة الأساسية إلى المصادقة الحديثة.  <br/> |

    لا يدعم العملاء و/أو البروتوكولات غير المدرجة (على سبيل المثال، POP3) المصادقة الحديثة باستخدام Exchange المحلي ويتابعون استخدام آليات المصادقة القديمة حتى بعد تمكين المصادقة الحديثة في البيئة.

- **المتطلبات الأساسية العامة**
  - تتطلب سيناريوهات غابة الموارد ثقة ثنائية مع غابة الحساب لضمان إجراء عمليات البحث في SID المناسبة أثناء طلبات المصادقة الحديثة المختلطة. 
  - إذا كنت تستخدم AD FS، يجب أن Windows 2012 R2 AD FS 3.0 والأعلى للاتحاد.
  - إن تكوينات هويتك هي أي من الأنواع المعتمدة بواسطة Azure AD الاتصال، مثل مزامنة كلمة المرور والمصادقة المرورية وS STS المدعمة بواسطة Office 365.
  - لديك Azure AD الاتصال يعمل لتكرار المستخدم ومزامنته.
  - لقد قمت بالتحقق من تكوين التكوين المختلط باستخدام Exchange "طبولوجيا مختلطة كلاسيكية" بين بيئتك المحلية Office 365 المحلية. بيان الدعم الرسمي Exchange المختلط يقول أنه يجب أن يكون لديك وحدة CU حالية أو وحدة CU حالية - 1.
    > [!NOTE]
    > المصادقة الحديثة المختلطة غير معتمدة مع ["الوكيل المختلط](/exchange/hybrid-deployment/hybrid-agent)".

  - تأكد من أن كل من مستخدم الاختبار المحلي، بالإضافة إلى مستخدم اختبار مختلط تم استخدامه في Office 365، يمكنه تسجيل الدخول إلى عميل سطح مكتب Skype for Business (إذا كنت تريد استخدام المصادقة الحديثة مع Skype) و Microsoft Outlook (إذا كنت تريد استخدام المصادقة الحديثة مع Exchange).
  - تأكد من عدم تكوين الإعداد SignInOptions في Microsoft Office الإعداد الأكثر تقييدا. لمزيد من المعلومات، [راجع كيفية السماح Office الاتصال بالإنترنت](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>ما الذي أحتاج إلى معرفته أيضا قبل البدء؟
<a name="BKMK_Whatelse"> </a>

- تتضمن كل السيناريوهات للخوادم المحليه إعداد مصادقة حديثة في الموقع المحلي (في الواقع، ل Skype for Business توجد قائمة بالطبول المعتمدة) بحيث يكون الخادم المسؤول عن المصادقة والتخويل في Microsoft Cloud (خدمة الرمز المميز لأمن Azure AD، التي تسمى 'evoSTS')، وتحديث Azure AD حول عناوين URL أو مساحات الاسم المستخدمة بواسطة التثبيت المحلي لأي من Skype for Business أو Exchange. وبالتالي، فإن الخوادم في الموقع تتخذ تبعية Microsoft Cloud. يمكن اعتبار اتخاذ هذا الإجراء تكوين 'وث مختلط'.
- تربط هذه المقالة الآخرين التي ستساعدك على اختيار طبول المصادقة الحديثة المعتمدة (الضرورية فقط ل Skype for Business)، والمقالات المساعدة التي توضح خطوات الإعداد، أو خطوات تعطيل المصادقة الحديثة، ل Exchange المحلي و Skype for Business المحلي. فضل هذه الصفحة في المستعرض إذا كنت ستحتاج إلى قاعدة منزلية لاستخدام المصادقة الحديثة في بيئة الخادم.

## <a name="related-topics"></a>مواضيع ذات صلة
<a name="BKMK_URLListforMA"> </a>

- [كيفية تكوين Exchange Server لاستخدام المصادقة الحديثة](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype for Business الطبول المدعمة مع المصادقة الحديثة](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [كيفية تكوين Skype for Business للاستخدام "المصادقة الحديثة"](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
