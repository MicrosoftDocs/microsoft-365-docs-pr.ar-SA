---
title: نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية للاستخدام مع خوادم Skype for Business Exchange المحلية
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: scotv
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
description: في هذه المقالة، ستتعرف على المصادقة الحديثة المختلطة والمتطلبات الأساسية للاستخدام مع خوادم Skype for Business Exchange المحلية.
ms.openlocfilehash: c161f205aba1222f39811155bef5c6be6da613d0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093383"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>نظرة عامة على المصادقة الحديثة المختلطة والمتطلبات الأساسية لاستخدامها مع خوادم Skype for Business Exchange المحلية

*تنطبق هذه المقالة على كل من Microsoft 365 Enterprise و Office 365 Enterprise.*

_المصادقة الحديثة_ هي طريقة لإدارة الهوية التي توفر مصادقة المستخدم وتخويله بشكل أكثر أمانا. وهي متوفرة Office 365 عمليات النشر المختلط لخادم Skype for Business المحلي وخادم Exchange المحلي، Skype for Business المختلطة منقسمة المجال. ترتبط هذه المقالة بمستندات ذات صلة حول المتطلبات الأساسية وإعداد/تعطيل المصادقة الحديثة وبعض العميل ذي الصلة (على سبيل المثال. معلومات Outlook والعملاء Skype).

- [ما هي المصادقة الحديثة؟](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [ما الذي يتغير عند استخدام المصادقة الحديثة؟](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [التحقق من حالة المصادقة الحديثة للبيئة المحلية](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [هل تفي بالمتطلبات الأساسية للمصادقة الحديثة؟](#do-you-meet-modern-authentication-prerequisites)
- [ما الذي أحتاج إلى معرفته أيضا قبل البدء؟](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>ما هي المصادقة الحديثة؟
<a name="BKMK_WhatisModAuth"> </a>

المصادقة الحديثة هي مصطلح مظلة لمجموعة من أساليب المصادقة والتخويل بين العميل (على سبيل المثال، الكمبيوتر المحمول أو هاتفك) والخادم، بالإضافة إلى بعض إجراءات الأمان التي تعتمد على نهج الوصول التي قد تكون على دراية بها بالفعل. ويتضمن ما يلي:

- **أساليب المصادقة**: المصادقة متعددة العوامل (MFA)؛ مصادقة البطاقة الذكية؛ المصادقة المستندة إلى شهادة العميل
- **أساليب التخويل**: تنفيذ Microsoft للتخويل المفتوح (OAuth)
- **نهج الوصول المشروط**: الوصول المشروط لإدارة تطبيقات المحمول (MAM) وAzure Active Directory (Azure AD)

تمنح إدارة هويات المستخدمين باستخدام المصادقة الحديثة المسؤولين العديد من الأدوات المختلفة لاستخدامها عندما يتعلق الأمر بتأمين الموارد وتوفر أساليب أكثر أمانا لإدارة الهوية لكل من السيناريوهات المحلية (Exchange Skype for Business)، Exchange المختلطة، Skype for Business السيناريوهات المختلطة/المقسمة.

لأن Skype for Business يعمل بشكل وثيق مع Exchange، سيتأثر سلوك تسجيل الدخول Skype for Business مستخدمي العميل بحالة المصادقة الحديثة Exchange. كما أنه ينطبق إذا كان لديك بنية مختلطة Skype for Business _منقسمة المجال_، حيث يكون لديك كل من Skype for Business Online و Skype for Business محليا، مع وجود مستخدمين في الموقعين.

لمزيد من المعلومات حول المصادقة الحديثة في Office 365، راجع [Office 365 دعم تطبيق العميل - المصادقة متعددة العوامل](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> اعتبارا من أغسطس 2017، سيكون لدى جميع المستأجرين Office 365 الجدد الذين يتضمنون Skype for Business عبر الإنترنت Exchange عبر الإنترنت مصادقة حديثة ممكنة بشكل افتراضي. لن يكون للمستأجرين الموجودين مسبقا تغيير في حالة MA الافتراضية الخاصة بهم، ولكن جميع المستأجرين الجدد يدعمون تلقائيا مجموعة موسعة من ميزات الهوية التي تراها مدرجة أعلاه. للتحقق من حالة MA، راجع [التحقق من حالة المصادقة الحديثة لقسم البيئة المحلية](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .

## <a name="what-changes-when-i-use-modern-authentication"></a>ما الذي يتغير عند استخدام المصادقة الحديثة؟
<a name="BKMK_WhatChanges"> </a>

عند استخدام المصادقة الحديثة مع خادم Skype for Business محلي أو خادم Exchange، لا تزال تقوم *بمصادقة* المستخدمين المحليين، ولكن تتغير قصة *تخويل* وصولهم إلى الموارد (مثل الملفات أو رسائل البريد الإلكتروني). هذا هو السبب في أنه على الرغم من أن المصادقة الحديثة تتعلق بالاتصالات بين العميل والخادم، فإن الخطوات التي تم اتخاذها أثناء تكوين MA تؤدي إلى تعيين evoSTS (خدمة الرمز المميز للأمان المستخدمة من قبل Azure AD) كخادم المصادقة لخادم Skype for Business وخادم Exchange محليا.

يسمح التغيير في evoSTS للخوادم المحلية بالاستفادة من OAuth (إصدار الرمز المميز) لتخول عملائك، ويسمح أيضا لخدمتك المحلية باستخدام أساليب الأمان الشائعة في السحابة (مثل المصادقة متعددة العوامل). بالإضافة إلى ذلك، يصدر evoSTS الرموز المميزة التي تسمح للمستخدمين بطلب الوصول إلى الموارد دون توفير كلمة المرور الخاصة بهم كجزء من الطلب. بغض النظر عن مكان استضافة المستخدمين (عبر الإنترنت أو محليا)، وبغض النظر عن الموقع الذي يستضيف المورد المطلوب، سيصبح EvoSTS جوهر تخويل المستخدمين والعملاء بمجرد تكوين المصادقة الحديثة.

على سبيل المثال، إذا احتاج عميل Skype for Business إلى الوصول إلى خادم Exchange للحصول على معلومات التقويم نيابة عن مستخدم، فإنه يستخدم مكتبة مصادقة Microsoft (MSAL) للقيام بذلك. MSAL هي مكتبة تعليمات برمجية مصممة لجعل الموارد الآمنة في الدليل الخاص بك متاحة لتطبيقات العميل باستخدام الرموز المميزة للأمان OAuth. تعمل MSAL مع OAuth للتحقق من المطالبات وتبادل الرموز المميزة (بدلا من كلمات المرور)، لمنح المستخدم حق الوصول إلى مورد. في الماضي، قد تكون السلطة في معاملة مثل هذه -- الخادم الذي يعرف كيفية التحقق من صحة مطالبات المستخدم وإصدار الرموز المميزة المطلوبة -- خدمة رمز الأمان المميز محليا، أو حتى خدمات الأمان المشترك لـ Active Directory. ومع ذلك، فإن المصادقة الحديثة تركز هذه السلطة باستخدام Azure AD.

وهذا يعني أيضا أنه على الرغم من أن الخادم Exchange والبيئات Skype for Business قد تكون محلية بالكامل، فإن الخادم المخول سيكون متصلا بالإنترنت، ويجب أن يكون لدى البيئة المحلية لديك القدرة على إنشاء اتصال باشتراكك Office 365 في السحابة والحفاظ عليه (ومثيل Azure AD الذي يستخدمه اشتراكك كدليل له).

ما الذي لا يتغير؟ سواء كنت تستخدم خادما مختلطا منقسم المجال أو تستخدم خادما Skype for Business Exchange محليا، يجب على جميع المستخدمين أولا المصادقة *المحلية*. في التنفيذ المختلط للمصادقة الحديثة، يشير _كل من Lyncdiscovery_ و _Autodiscovery_ إلى الخادم المحلي.

> [!IMPORTANT]
> إذا كنت بحاجة إلى معرفة طبولوجيا Skype for Business المحددة المدعومة ب MA، فهذا [موثق هنا](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>التحقق من حالة المصادقة الحديثة للبيئة المحلية
<a name="BKMK_CheckStatus"> </a>

نظرا لأن المصادقة الحديثة تغير خادم التخويل المستخدم عند تطبيق الخدمات OAuth/S2S، تحتاج إلى معرفة ما إذا كانت المصادقة الحديثة ممكنة أو معطلة لبيئات Skype for Business Exchange المحلية. يمكنك التحقق من الحالة على خوادم Exchange عن طريق تشغيل أمر PowerShell التالي:

```powershell
Get-OrganizationConfig | ft OAuth*
```

إذا كانت قيمة الخاصية _OAuth2ClientProfileEnabled_ **False**، فسيتم تعطيل المصادقة الحديثة.

لمزيد من المعلومات حول Get-OrganizationConfig cmdlet، راجع [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

يمكنك التحقق من خوادم Skype for Business عن طريق تشغيل أمر PowerShell التالي:

```powershell
Get-CSOAuthConfiguration
```

إذا أرجع الأمر خاصية _OAuthServers_ فارغة، أو إذا كانت قيمة _الخاصية ClientADALAuthOverride_ غير **مسموح بها**، فسيتم تعطيل المصادقة الحديثة.

لمزيد من المعلومات حول Get-CsOAuthConfiguration cmdlet، راجع [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>هل تفي بالمتطلبات الأساسية للمصادقة الحديثة؟

تحقق من هذه العناصر وتحقق منها من القائمة قبل المتابعة:

- **Skype for Business محدد**
  - يجب أن تحتوي كافة الخوادم على تحديث تراكمي (CU5) في مايو 2017 Skype for Business Server 2015 أو إصدار أحدث
    - **استثناء** - يمكن أن يكون الجهاز الفرعي للقابلية للبقاء (SBA) على الإصدار الحالي (استنادا إلى Lync 2013)
  - تتم إضافة مجال SIP كمجال موحد في Office 365
  - يجب أن يكون لكافة واجهات SFB الأمامية اتصالات صادرة إلى الإنترنت، إلى عناوين URL للمصادقة Office 365 (TCP 443) وعناوين CRLs جذر الشهادة المعروفة (TCP 80) المدرجة في الصفوف 56 و125 من القسم "Microsoft 365 Common and Office" [لعناوين URL Office 365 ونطاقات عناوين IP](urls-and-ip-address-ranges.md).

- **Skype for Business المحلي في بيئة Office 365 مختلطة**
  - نشر Skype for Business Server 2019 مع تشغيل كافة الخوادم Skype for Business Server 2019.
  - نشر Skype for Business Server 2015 مع تشغيل جميع الخوادم Skype for Business Server 2015.
  - نشر بحد أقصى إصدارين مختلفين من الخادم كما هو موضح أدناه:
    - Skype خاص بخادم الأعمال 2015
    - Skype خاص بخادم الأعمال 2019
  - يجب تثبيت آخر التحديثات التراكمية على جميع خوادم Skype for Business، راجع [Skype for Business Server التحديثات](/skypeforbusiness/sfb-server-updates) للعثور على كافة التحديثات المتوفرة وإدارتها.
  - لا يوجد Lync Server 2010 أو 2013 في البيئة المختلطة.

>[!NOTE]
>إذا كانت الخوادم الأمامية Skype for Business تستخدم خادما وكيلا للوصول إلى الإنترنت، فيجب إدخال عنوان IP للخادم الوكيل ورقم المنفذ المستخدم في قسم التكوين في ملف web.config لكل واجهة أمامية.

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
> تأكد من الاشتراك في موجز RSS [لعناوين URL Office 365 ونطاقات عناوين IP](urls-and-ip-address-ranges.md) للبقاء على اطلاع بأحدث إدخالات عناوين URL المطلوبة.

- **Exchange Server محدد**
  - أنت تستخدم إما Exchange server 2013 CU19 وما فوق، Exchange server 2016 CU8 وما فوق، أو Exchange Server 2019 CU1 وما فوق.
  - لا يوجد خادم Exchange 2010 في البيئة.
  - لم يتم تكوين إلغاء تحميل SSL. يتم دعم إنهاء SSL وإعادة تشفيره.
  - في حالة استخدام بيئتك لبنية أساسية لخادم وكيل للسماح للخوادم بالاتصال بالإنترنت، تأكد من أن جميع خوادم Exchange تحتوي على الخادم الوكيل المحدد في [الخاصية InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server المحلي في بيئة Office 365 مختلطة**

  - إذا كنت تستخدم Exchange Server 2013، فيجب تثبيت دور خادم علبة البريد وخادم Client Access على الأقل. في حين أنه من الممكن تثبيت أدوار علبة البريد والوصول إلى العميل على خوادم منفصلة، نوصي بشدة بتثبيت كلا الدورين على نفس الخادم لتوفير المزيد من الموثوقية والأداء المحسن.
  - إذا كنت تستخدم خادم Exchange 2016 أو إصدار أحدث، يجب أن يكون دور خادم علبة البريد مثبتا على خادم واحد على الأقل.
  - لا يوجد خادم Exchange 2007 أو 2010 في البيئة المختلطة.
  - يجب تثبيت آخر التحديثات التراكمية على كافة خوادم Exchange، راجع [الترقية Exchange إلى آخر التحديثات التراكمية](/exchange/plan-and-deploy/install-cumulative-updates) للعثور على كافة التحديثات المتوفرة وإدارتها.

- **متطلبات العميل والبروتوكول Exchange**

    يتم تحديد توفر المصادقة الحديثة عن طريق الجمع بين العميل والبروتوكول والتكوين. إذا لم تكن المصادقة الحديثة معتمدة من قبل العميل والبروتوكول و/أو التكوين، فسيستمر العميل في استخدام المصادقة القديمة.
  
    يدعم العملاء والبروتوكولات التالية المصادقة الحديثة مع Exchange المحلية عند تمكين المصادقة الحديثة في البيئة:

  |**العملاء**|**البروتوكول الأساسي**|**ملاحظات**|
  |:-----|:-----|:-----|
  |Outlook 2013 والإي وقت لاحق  <br/> |MAPI عبر HTTP  <br/> |يجب تمكين MAPI عبر HTTP ضمن Exchange من أجل استخدام المصادقة الحديثة مع هؤلاء العملاء (ممكن أو صحيح للتثبيتات الجديدة لحزمة خدمة Exchange 2013 1 وما فوقها)؛ لمزيد من المعلومات، راجع [كيفية عمل المصادقة الحديثة لتطبيقات عميل Office 2013 و Office 2016](modern-auth-for-office-2013-and-2016.md).  <br/> تأكد من تشغيل الحد الأدنى المطلوب من الإصدار Outlook؛ راجع [آخر التحديثات لإصدارات Outlook التي تستخدم Windows Installer (MSI).](/officeupdates/outlook-updates-msi)  <br/> |
  |Outlook 2016 for Mac والإي وقت لاحق  <br/> |Exchange Web Services  <br/> |  <br/> |
  |Outlook لنظامي التشغيل iOS وAndroid  <br/> | تقنية مزامنة Microsoft <br/> |راجع [استخدام المصادقة الحديثة المختلطة مع Outlook لنظامي التشغيل iOS وAndroid](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) لمزيد من المعلومات.  <br/> |
  |عملاء Exchange ActiveSync (على سبيل المثال، بريد iOS11)  <br/> |Exchange ActiveSync  <br/> |بالنسبة Exchange ActiveSync العملاء الذين يدعمون المصادقة الحديثة، يجب إعادة إنشاء ملف التعريف للتبديل من المصادقة الأساسية إلى المصادقة الحديثة.  <br/> |

    لا يدعم العملاء و/أو البروتوكولات غير المدرجة (على سبيل المثال، POP3) المصادقة الحديثة مع Exchange المحلية ويستمرون في استخدام آليات المصادقة القديمة حتى بعد تمكين المصادقة الحديثة في البيئة.

- **المتطلبات الأساسية العامة**
  - تتطلب سيناريوهات غابة الموارد ثقة ثنائية الاتجاه مع غابة الحساب لضمان إجراء عمليات بحث SID المناسبة أثناء طلبات المصادقة الحديثة المختلطة. 
  - إذا كنت تستخدم AD FS، يجب أن يكون لديك Windows 2012 R2 AD FS 3.0 وما فوق للاتحاد.
  - تكوينات الهوية الخاصة بك هي أي من الأنواع التي يدعمها Azure AD الاتصال، مثل مزامنة تجزئة كلمة المرور، والمصادقة التمريرية، و STS الداخلي المدعوم من قبل Office 365.
  - لديك الاتصال تكوين Azure AD وتشغيله للنسخ المتماثل للمستخدم ومزامنته.
  - لقد تحققت من تكوين التكوين المختلط باستخدام Exchange وضع المخطط المختلط الكلاسيكي بين البيئة المحلية والبيئة Office 365. يقول بيان الدعم الرسمي Exchange المختلط إنه يجب أن يكون لديك إما وحدة CU حالية أو وحدة CU حالية - 1.
    > [!NOTE]
    > المصادقة الحديثة المختلطة غير معتمدة مع [Hybrid Agent](/exchange/hybrid-deployment/hybrid-agent).

  - تأكد من أن كل من مستخدم اختبار محلي، بالإضافة إلى مستخدم اختبار مختلط موجود في Office 365، يمكنه تسجيل الدخول إلى عميل سطح المكتب Skype for Business (إذا كنت تريد استخدام المصادقة الحديثة مع Skype) وMicrosoft Outlook (إذا كنت تريد استخدام المصادقة الحديثة مع Exchange).
  - تأكد من عدم تكوين إعداد SignInOptions في Microsoft Office إلى إعداده الأكثر تقييدا. لمزيد من المعلومات، راجع [كيفية السماح Office بالاتصال بالإنترنت](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>ما الذي أحتاج إلى معرفته أيضا قبل البدء؟
<a name="BKMK_Whatelse"> </a>

- تتضمن جميع سيناريوهات الخوادم المحلية إعداد مصادقة حديثة محليا (في الواقع، Skype for Business هناك قائمة بالطوبولوجيا المدعومة) بحيث يكون الخادم المسؤول عن المصادقة والتخويل في سحابة Microsoft (خدمة الرمز المميز للأمان في Azure AD، تسمى 'evoSTS')، وتحديث Azure AD حول عناوين URL أو مساحات الأسماء المستخدمة من قبل التثبيت المحلي لأي من Skype for Business أو Exchange. لذلك، تأخذ الخوادم المحلية تبعية Microsoft Cloud. يمكن اعتبار اتخاذ هذا الإجراء تكوين "المصادقة المختلطة".
- ترتبط هذه المقالة بالآخرين الذين سيساعدونك على اختيار طبولوجيا المصادقة الحديثة المعتمدة (الضرورية فقط Skype for Business)، والمقالات الإرشادية التي تحدد خطوات الإعداد، أو خطوات تعطيل المصادقة الحديثة، Exchange محليا Skype for Business المحلي. أضف هذه الصفحة إلى المفضلة في المستعرض إذا كنت ستحتاج إلى قاعدة رئيسية لاستخدام المصادقة الحديثة في بيئة الخادم.

## <a name="related-topics"></a>المواضيع ذات الصلة
<a name="BKMK_URLListforMA"> </a>

- [كيفية تكوين Exchange Server المحلي لاستخدام المصادقة الحديثة](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype for Business الطبولوجيا المدعومة بالمصادقة الحديثة](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [كيفية تكوين Skype for Business المحلي لاستخدام المصادقة الحديثة](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [إزالة المصادقة الحديثة المختلطة أو تعطيلها من Skype for Business Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
