---
title: الاتصال شبكة المحلية إلى شبكة Microsoft Azure الظاهرية
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 'ملخص: تعرف على كيفية تكوين شبكة Azure ظاهرية Office الخادم باستخدام اتصال VPN من موقع إلى موقع.'
ms.openlocfilehash: 5ba05dd432a6f6fe323e9d9cfd2542dcb1cc7efb
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570037"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>الاتصال شبكة المحلية إلى شبكة Microsoft Azure الظاهرية

يتم توصيل شبكة Azure الظاهرية المحلية بالشبكة المحلية، وتوسيع الشبكة لتضمين الشبكات الفرعية و الأجهزة الظاهرية المستضافة في خدمات البنية الأساسية في Azure. يسمح هذا الاتصال لأجهزة الكمبيوتر الموجودة على الشبكة المحلية بالوصول مباشرة إلى الأجهزة الظاهرية في Azure والعكس بالعكس. 

على سبيل المثال، يحتاج خادم مزامنة الدليل الذي يعمل على جهاز Azure الظاهري إلى الاستعلام عن وحدات التحكم بالمجالات المحلية للحصول على تغييرات على الحسابات ومزامنة هذه التغييرات مع اشتراكك في Microsoft 365 الإلكتروني. توضح لك هذه المقالة كيفية إعداد شبكة Azure ظاهرية من موقع إلى موقع باستخدام اتصال شبكة ظاهرية خاصة (VPN) جاهزة لاستضافة أجهزة Azure الظاهرية.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>تكوين شبكة Azure ظاهرية عبر الموقع

لا يجب عزل الأجهزة الظاهرية في Azure عن بيئتك المحلية. لتوصيل أجهزة Azure الظاهرية بالموارد المحلية للشبكة، يجب تكوين شبكة Azure الظاهرية المحلية. يعرض الرسم التخطيطي التالي المكونات المطلوبة لنشر شبكة Azure ظاهرية مع جهاز ظاهري في Azure.
  
![الشبكة المحلية المتصلة ب Microsoft Azure بواسطة اتصال VPN من موقع إلى موقع.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
في الرسم التخطيطي، هناك شبكتان متصلتان بواسطة اتصال VPN من موقع إلى موقع: الشبكة المحلية وشبكة Azure الظاهرية. اتصال VPN من موقع إلى موقع هو:

- بين نطاقي نهاية قابلتين للمعالجة وتقعان على الإنترنت العام.
- تم إنهاؤه بواسطة جهاز VPN على الشبكة المحلية وبوابة Azure VPN على شبكة Azure الظاهرية.

تستضيف شبكة Azure الظاهرية الأجهزة الظاهرية. يتم إعادة توجيه حركة مرور الشبكة التي تنشأ من أجهزة ظاهرية على شبكة Azure الظاهرية إلى بوابة VPN، التي تقوم بعد ذلك ب إعادة توجيه حركة المرور عبر اتصال VPN من موقع إلى موقع بجهاز VPN على الشبكة المحلية. ثم تهيئ البنية الأساسية التوجيه للشبكة المحلية حركة المرور إلى وجهتها.

>[!Note]
>يمكنك أيضا استخدام [ExpressRoute](https://azure.microsoft.com/services/expressroute/)، وهو اتصال مباشر بين مؤسستك وشبكة Microsoft. لا تنقل حركة المرور عبر ExpressRoute عبر الإنترنت العام. لا تصف هذه المقالة استخدام ExpressRoute.
>
  
لإعداد اتصال VPN بين شبكة Azure الظاهرية وشبكة الاتصال المحلية، اتبع الخطوات التالية: 
  
1. **في الموقع:** قم بتعريف مسار شبكة المحلية وإنشاءه لمساحة العنوان لشبكة Azure الظاهرية التي تشير إلى جهاز VPN الخاص بك.
    
2. **Microsoft Azure:** إنشاء شبكة ظاهرية من Azure باستخدام اتصال VPN من موقع إلى موقع. 
    
3. **في الموقع:** قم بتكوين الجهاز المحلي أو جهاز VPN الخاص بالبرمجيات لإنهاء اتصال VPN، الذي يستخدم أمان بروتوكول الإنترنت (IPsec).
    
بعد إنشاء اتصال VPN من موقع إلى موقع، يمكنك إضافة أجهزة Azure الظاهرية إلى الشبكات الفرعية للشبكة الظاهرية.
  
## <a name="plan-your-azure-virtual-network"></a>تخطيط شبكة Azure الظاهرية
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>المتطلبات الأساسية
<a name="Prerequisites"></a>

- اشتراك Azure. للحصول على معلومات حول اشتراكات Azure، انتقل إلى [صفحة كيفية شراء Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- مساحة عنوان IPv4 خاصة متوفرة لتعيينها إلى الشبكة الظاهرية وشبكاتها الفرعية، مع توفير مساحة كافية من أجل النمو لاحتواء عدد الأجهزة الظاهرية المطلوبة الآن وفي المستقبل.
    
- جهاز VPN متوفر في شبكتك المحلية لإنهاء اتصال VPN من موقع إلى موقع يدعم متطلبات IPsec. لمزيد من المعلومات، راجع [حول أجهزة VPN لاتصالات](/azure/vpn-gateway/vpn-gateway-about-vpn-devices) الشبكة الظاهرية من موقع إلى موقع.
    
- التغييرات التي يتم إدخالها على البنية الأساسية التوجيه بحيث يتم إعادة توجيه حركة المرور إلى مساحة العنوان لشبكة Azure الظاهرية إلى جهاز VPN الذي يستضيف اتصال VPN من موقع إلى موقع.
    
- وكيل ويب يمنح أجهزة الكمبيوتر المتصلة بالشبكة المحلية والوصول إلى شبكة Azure الظاهرية إلى الإنترنت.
    
### <a name="solution-architecture-design-assumptions"></a>افتراضات تصميم هندسة الحلول

تمثل القائمة التالية اختيارات التصميم التي تم اتخاذها لهياية الحل هذه. 
  
- يستخدم هذا الحل شبكة ظاهرية واحدة من Azure مع اتصال VPN من موقع إلى موقع. تستضيف شبكة Azure الظاهرية شبكة فرعية واحدة يمكنها أن تحتوي على أجهزة ظاهرية متعددة. 
    
- يمكنك استخدام خدمة التوجيه والوصول عن بعد (RRAS) في Windows Server 2016 أو Windows Server 2012 لإنشاء اتصال VPN من موقع إلى موقع IPsec بين الشبكة المحلية وشبكة Azure الظاهرية. يمكنك أيضا استخدام خيارات أخرى، مثل أجهزة VPN ل Cisco أو Juniper Networks.
    
- قد لا تزال الشبكة المحلية تملك خدمات الشبكة مثل خدمات مجال Active Directory (AD DS) ونظام أسماء المجالات (DNS) وخادمات الوكيل. استنادا إلى متطلباتك، قد يكون من المفيد وضع بعض موارد الشبكة هذه في شبكة Azure الظاهرية.
    
بالنسبة إلى شبكة Azure الظاهرية الموجودة التي بها شبكة فرعية واحدة أو أكثر، حدد ما إذا كانت هناك مساحة عنوان متبقية لشبكة فرعية إضافية لاستضافة الأجهزة الظاهرية المطلوبة، استنادا إلى متطلباتك. إذا لم يكن لديك مساحة عنوان متبقية لشبكة فرعية إضافية، فنشئ شبكة ظاهرية إضافية لديها اتصال VPN خاص بها من موقع إلى موقع.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>تخطيط تغييرات البنية الأساسية التوجيه لشبكة Azure الظاهرية

يجب تكوين بنية التوجيه الأساسية المحلية الخاصة بك من أجل إعادة توجيه حركة المرور الموجهة إلى مساحة العنوان لشبكة Azure الظاهرية إلى جهاز VPN المحلية الذي يستضيف اتصال VPN من موقع إلى موقع.
  
تعتمد الطريقة الدقيقة لتحديث البنية الأساسية التوجيه على كيفية إدارة معلومات التوجيه، والتي يمكن أن تكون:
  
- تحديثات جدول التوجيه استنادا إلى التكوين اليدوي.
    
- تحديثات جدول التوجيه استنادا إلى بروتوكولات التوجيه، مثل بروتوكول معلومات التوجيه (RIP) أو فتح المسار الأقصر أولا (OSPF).
    
استشر متخصص التوجيه للتأكد من إعادة توجيه حركة المرور الموجهة لشبكة Azure الظاهرية إلى جهاز VPN المحلية.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>التخطيط لقواعد جدار الحماية الخاصة ب حركة المرور من جهاز VPN الداخلي وإلحامه

إذا كان جهاز VPN الخاص بك على شبكة محيطة بها جدار حماية بين الشبكة المحيطة والإنترنت، فقد تحتاج إلى تكوين جدار الحماية للقواعد التالية للسماح باتصال VPN من موقع إلى موقع.
  
- المرور إلى جهاز VPN (الوارد من الإنترنت):
    
  - عنوان IP الوجهة لجهاز VPN وبروتوكول IP 50
    
  - عنوان IP الوجهة لجهاز VPN وميناء وجهة UDP 500
    
  - عنوان IP الوجهة لجهاز VPN وميناء وجهة UDP 4500
    
- حركة المرور من جهاز VPN (الصادر إلى الإنترنت):
    
  - عنوان IP المصدر لجهاز VPN وبروتوكول IP 50
    
  - عنوان IP المصدر لجهاز VPN ومصدر UDP المنفذ 500
    
  - عنوان IP المصدر لجهاز VPN ومصدر UDP المنفذ 4500
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>التخطيط لمساحة عنوان IP الخاصة لشبكة Azure الظاهرية

يجب أن تكون مساحة عنوان IP الخاصة لشبكة Azure الظاهرية قادرة على استيعاب العناوين التي يستخدمها Azure لاستضافة الشبكة الظاهرية وبها شبكة فرعية واحدة على الأقل بها عناوين كافية لألعاب Azure الظاهرية.
  
لتحديد عدد العناوين المطلوبة الشبكة الفرعية، قم بعد عدد الأجهزة الظاهرية التي تحتاج إليها الآن، واقدر النمو في المستقبل، ثم استخدم الجدول التالي لتحديد حجم الشبكة الفرعية.
  
|**عدد الأجهزة الظاهرية المطلوبة**|**عدد بت المضيف المطلوب**|**حجم الشبكة الفرعية**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>تخطيط ورقة العمل لتكوين شبكة Azure الظاهرية
<a name="worksheet"> </a>

قبل إنشاء شبكة Azure ظاهرية لاستضافة الأجهزة الظاهرية، يجب تحديد الإعدادات المطلوبة في الجداول التالية.
  
لإعدادات الشبكة الظاهرية، قم بتعبئة الجدول V.
  
 **الجدول الخامس: تكوين الشبكة الظاهرية المحلية**
  
|**عنصر**|**عنصر التكوين**|**الوصف**|**القيمة**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |اسم الشبكة الظاهري  <br/> |اسم لتعيينه إلى شبكة Azure الظاهرية (على سبيل المثال DirSyncNet).  <br/> |![السطر.](../media/Common-Images/TableLine.png) |
|2.  <br/> |موقع الشبكة الظاهري  <br/> |مركز بيانات Azure الذي سيحتوي على الشبكة الظاهرية (مثل West US).  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |عنوان IP لجهاز VPN  <br/> |عنوان IPv4 العام لواجهة جهاز VPN على الإنترنت. اعمل مع قسم المعلومات لتحديد هذا العنوان.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |مساحة عنوان الشبكة الظاهرية  <br/> |مساحة العنوان (المعرفة فيبادرة عنوان خاص واحد) للشبكة الظاهرية. اعمل مع قسم تكنولوجيا المعلومات لتحديد مساحة العنوان هذه. يجب أن تكون مساحة العنوان بتنسيق التوجيه بين الفئات (CIDR)، المعروف أيضا بتنسيقبادات الشبكة. مثال على ذلك هو 10.24.64.0/20.  <br/> |![السطر.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |مفتاح IPsec المشترك  <br/> |سلسلة رقمية عشوائية من 32 حرفا سيتم استخدامها لمصادقة كلا جانبي اتصال VPN من موقع إلى موقع. اعمل مع قسم المعلومات أو قسم الأمان لتحديد قيمة المفتاح هذه ثم تخزينها في موقع آمن. بدلا من ذلك، راجع [إنشاء سلسلة عشوائية لمفتاح IPsec تم اختياره مسبقا](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![السطر.](../media/Common-Images/TableLine.png) <br/> |
   
قم بتعبئة الجدول S للنتات الفرعية لهذا الحل.
  
- بالنسبة إلى الشبكة الفرعية الأولى، حدد مساحة عنوان 28 بت (بطول بادئة /28) لبوابة Azure الفرعية. راجع [حساب مساحة عنوان الشبكة الفرعية لبوابة شبكات Azure](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) الظاهرية للحصول على معلومات حول كيفية تحديد مساحة العنوان هذه.
    
- بالنسبة للشبكة الفرعية الثانية، حدد اسما ودودا ومساحة عنوان IP واحدة استنادا إلى مساحة عنوان الشبكة الظاهرية والغرض الوصفي.
    
اعمل مع قسم تكنولوجيا المعلومات لتحديد مسافات العنوان هذه من مساحة عنوان الشبكة الظاهرية. يجب أن تكون كلتا اثنتين من مسافات العنوان بتنسيق CIDR.
  
 **الجدول S: الشبكات الفرعية في الشبكة الظاهرية**
  
|**عنصر**|**اسم الشبكة الفرعية**|**مساحة عنوان الشبكة الفرعية**|**الغرض**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة بواسطة بوابة Azure.  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
بالنسبة إلى خوادم DNS المحلية التي تريد أن تستخدمها الأجهزة الظاهرية في الشبكة الظاهرية، قم بتعبئة الجدول D. امنح كل خادم DNS اسما ودودا وعنوان IP واحدا. لا يحتاج هذا الاسم الصديق إلى مطابقة اسم المضيف أو اسم الكمبيوتر الخاص بخادم DNS. تجدر الإشارة إلى إدراج إدخالين فارغين، ولكن يمكنك إضافة المزيد. اعمل مع قسم المعلومات لتحديد هذه القائمة.
  
 **الجدول D: خوادم DNS في الموقع**
  
|**عنصر**|**اسم خادم DNS**|**عنوان IP للخادم DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
ل توجيه الحزم من شبكة Azure الظاهرية إلى شبكة مؤسستك عبر اتصال VPN من موقع إلى موقع، يجب تكوين الشبكة الظاهرية مع شبكة محلية. تتضمن هذه الشبكة المحلية قائمة مسافات العنوان (بتنسيق CIDR) لكل المواقع على الشبكة المحلية لمنظمتك التي يجب أن تصل إليها الأجهزة الظاهرية في الشبكة الظاهرية. يمكن أن يكون هذا كل المواقع على الشبكة المحلية أو مجموعة فرعية. يجب أن تكون قائمة مساحات العنوان التي تعرف شبكتك المحلية فريدة ويجب ألا تتداخل مع مسافات العنوان المستخدمة لهذه الشبكة الظاهرية أو الشبكات الظاهرية الأخرى المحلية.
  
بالنسبة إلى مجموعة مساحات عنوان الشبكة المحلية، قم بتعبئة الجدول L. تجدر الإشارة إلى أن ثلاثة إدخالات فارغة مدرجة ولكنك ستحتاج عادة إلى المزيد. اعمل مع قسم المعلومات لتحديد هذه القائمة.
  
 **الجدول L:بادئات العنوان للشبكة المحلية**
  
|**عنصر**|**مساحة عنوان الشبكة المحلية**|
|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![سطر](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>خارطة طريق النشر
<a name="DeploymentRoadmap"> </a>

تتألف عملية إنشاء الشبكة الظاهرية المحلية وإضافة أجهزة ظاهرية في Azure من ثلاث مراحل:
  
- المرحلة 1: إعداد الشبكة المحلية.
    
- المرحلة الثانية: إنشاء الشبكة الظاهرية المحلية في Azure.
    
- المرحلة 3 (اختياري): إضافة أجهزة ظاهرية.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>المرحلة 1: إعداد الشبكة المحلية
<a name="Phase1"></a>

يجب تكوين الشبكة المحلية باستخدام مسار يشير إلى حركة المرور الموجهة إلى مساحة العنوان للشبكة الظاهرية ويصلها في النهاية إلى الموجه على حافة الشبكة المحلية. استشر مسؤول الشبكة لتحديد كيفية إضافة المسار إلى البنية الأساسية التوجيه للشبكة المحلية.
  
إليك التكوين الناتج.
  
![يجب أن يكون للشبكة المحلية مسار لمساحة عنوان الشبكة الظاهرية التي تشير إلى جهاز VPN.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>المرحلة الثانية: إنشاء الشبكة الظاهرية المحلية في Azure
<a name="Phase2"></a>

أولا، افتح مطالبة Azure PowerShell. إذا لم تكن قد قمت بتثبيت Azure PowerShell، فشاهد [بدء العمل باستخدام Azure PowerShell](/powershell/azure/get-started-azureps).

 
بعد ذلك، قم بتسجيل الدخول إلى حساب Azure باستخدام هذا الأمر.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام الأمر التالي.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

قم بتعيين اشتراكك في Azure باستخدام هذه الأوامر. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك < >، باسم الاشتراك الصحيح.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

بعد ذلك، أنشئ مجموعة موارد جديدة للشبكة الظاهرية. لتحديد اسم مجموعة موارد فريدة، استخدم هذا الأمر لتضمين مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

أنشئ مجموعة الموارد الجديدة باستخدام هذه الأوامر.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، ستنشئ شبكة Azure الظاهرية.
  
```powershell
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

إليك التكوين الناتج.
  
![لم يتم توصيل الشبكة الظاهرية بالشبكة المحلية بعد.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
بعد ذلك، استخدم هذه الأوامر لإنشاء البوابات لاتصال VPN من موقع إلى موقع.
  
```powershell
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

إليك التكوين الناتج.
  
![بات للشبكة الظاهرية الآن بوابة.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
بعد ذلك، قم بتكوين جهاز VPN الخاص بك في الموقع للاتصال ببوابة Azure VPN. لمزيد من المعلومات، راجع [حول أجهزة VPN لاتصالات شبكة Azure الظاهرية من موقع إلى موقع](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
لتكوين جهاز VPN الخاص بك، ستحتاج إلى ما يلي:
  
- عنوان IPv4 العام لبوابة Azure VPN للشبكة الظاهرية. استخدم **الأمر Get-AzPublicIpAddress -name $vnetGatewayIpConfigName -ResourceGroupName $rgName** لعرض هذا العنوان.
    
- مفتاح IPsec المشترك مسبقا لاتصال VPN من موقع إلى موقع (الجدول V- العنصر 5 - عمود القيمة).
    
إليك التكوين الناتج.
  
![أصبحت الشبكة الظاهرية الآن متصلة بالشبكة المحلية.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>المرحلة 3 (اختياري): إضافة أجهزة ظاهرية

إنشاء الأجهزة الظاهرية التي تحتاج إليها في Azure. لمزيد من المعلومات، راجع إنشاء [Windows ظاهري باستخدام مدخل Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
استخدم الإعدادات التالية:
  
- على علامة **التبويب أساسيات** ، حدد الاشتراك والمجموعة الموارد نفسها التي حددتها الشبكة الظاهرية. ستحتاج إلى هذه في وقت لاحق تسجيل الدخول إلى الجهاز الظاهري. في المقطع **تفاصيل المثيل** ، اختر حجم الجهاز الظاهري المناسب. سجل اسم مستخدم حساب المسؤول وكلمة المرور في موقع آمن. 
    
- على علامة **التبويب** الشبكة، حدد اسم الشبكة الظاهرية الشبكة الفرعية لاستضافة الأجهزة الظاهرية (وليس GatewaySubnet). اترك كل الإعدادات الأخرى في قيمها الافتراضية.
    
تأكد من أن جهازك الظاهري يستخدم DNS بشكل صحيح من خلال التحقق من DNS الداخلي للتأكد من إضافة سجلات العنوان (أ) للجهاز الظاهري الجديد. للوصول إلى الإنترنت، يجب تكوين أجهزة Azure الظاهرية لاستخدام الخادم الوكيل للشبكة المحلية. اتصل بمسؤول الشبكة للحصول على خطوات تكوين إضافية لتنفيذها على الخادم.
  
إليك التكوين الناتج.
  
![تستضيف الشبكة الظاهرية الآن الأجهزة الظاهرية التي يمكن الوصول إليها من الشبكة المحلية.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>الخطوة التالية
  
[نشر Microsoft 365 الدليل في Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)