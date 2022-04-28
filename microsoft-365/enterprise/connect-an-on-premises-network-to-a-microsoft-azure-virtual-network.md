---
title: الاتصال شبكة محلية إلى شبكة Microsoft Azure الظاهرية
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: تعرف على كيفية تكوين شبكة Azure الظاهرية عبر أماكن العمل لأحمال عمل خادم Office مع اتصال VPN من موقع إلى موقع.'
ms.openlocfilehash: 8f9d8336bb50821374ada700613d2ae6142baf6d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094847"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>الاتصال شبكة محلية إلى شبكة Microsoft Azure الظاهرية

يتم توصيل شبكة Azure الظاهرية عبر أماكن العمل بشبكتك المحلية، مما يؤدي إلى توسيع شبكتك لتشمل الشبكات الفرعية والأجهزة الظاهرية المستضافة في خدمات البنية الأساسية ل Azure. يتيح هذا الاتصال لأجهزة الكمبيوتر الموجودة على شبكتك المحلية الوصول مباشرة إلى الأجهزة الظاهرية في Azure والعكس بالعكس. 

على سبيل المثال، يحتاج خادم مزامنة الدليل الذي يعمل على جهاز Azure الظاهري إلى الاستعلام عن وحدات التحكم بالمجال المحلية الخاصة بك لإجراء تغييرات على الحسابات ومزامنة هذه التغييرات مع اشتراكك في Microsoft 365. توضح لك هذه المقالة كيفية إعداد شبكة Azure ظاهرية عبر أماكن العمل باستخدام اتصال شبكة ظاهرية خاصة (VPN) من موقع إلى موقع جاهز لاستضافة أجهزة Azure الظاهرية.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>تكوين شبكة Azure الظاهرية متعددة الأماكن

لا يلزم عزل أجهزتك الظاهرية في Azure عن بيئتك المحلية. لتوصيل أجهزة Azure الظاهرية بموارد الشبكة المحلية، يجب تكوين شبكة Azure ظاهرية مشتركة. يوضح الرسم التخطيطي التالي المكونات المطلوبة لتوزيع شبكة Azure ظاهرية داخلية مع جهاز ظاهري في Azure.
  
![الشبكة المحلية المتصلة ب Microsoft Azure من خلال اتصال VPN من موقع إلى موقع.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
في الرسم التخطيطي، هناك شبكتان متصلتان باتصال VPN من موقع إلى موقع: الشبكة المحلية وشبكة Azure الظاهرية. اتصال VPN من موقع إلى موقع هو:

- بين نقطتي النهاية القابلتين للمعالجة والموجودتين على الإنترنت العام.
- تم إنهاؤه بواسطة جهاز VPN على الشبكة المحلية وبوابة Azure VPN على شبكة Azure الظاهرية.

تستضيف شبكة Azure الظاهرية الأجهزة الظاهرية. تتم إعادة توجيه نسبة استخدام الشبكة التي تنشأ من الأجهزة الظاهرية على شبكة Azure الظاهرية إلى بوابة VPN، والتي تقوم بعد ذلك بإعادة توجيه نسبة استخدام الشبكة عبر اتصال VPN من موقع إلى موقع إلى جهاز VPN على الشبكة المحلية. ثم تقوم البنية الأساسية للتوجيه للشبكة المحلية بإعادة توجيه نسبة استخدام الشبكة إلى وجهتها.

>[!Note]
>يمكنك أيضا استخدام [ExpressRoute](https://azure.microsoft.com/services/expressroute/)، وهو اتصال مباشر بين مؤسستك وشبكة Microsoft. لا تنتقل نسبة استخدام الشبكة عبر ExpressRoute عبر الإنترنت العام. لا تصف هذه المقالة استخدام ExpressRoute.
>
  
لإعداد اتصال VPN بين شبكة Azure الظاهرية والشبكة المحلية، اتبع الخطوات التالية: 
  
1. **المحلي:** تحديد مسار شبكة اتصال محلي وإنشاءه لمساحة عنوان شبكة Azure الظاهرية التي تشير إلى جهاز VPN المحلي الخاص بك.
    
2. **Microsoft Azure:** إنشاء شبكة Azure ظاهرية مع اتصال VPN من موقع إلى موقع. 
    
3. **في أماكن العمل:** قم بتكوين جهاز VPN للأجهزة أو البرامج المحلية لإنهاء اتصال VPN، الذي يستخدم أمان بروتوكول الإنترنت (IPsec).
    
بعد إنشاء اتصال VPN من موقع إلى موقع، يمكنك إضافة أجهزة Azure الظاهرية إلى الشبكات الفرعية للشبكة الظاهرية.
  
## <a name="plan-your-azure-virtual-network"></a>تخطيط شبكة Azure الظاهرية
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>المتطلبات الأساسية
<a name="Prerequisites"></a>

- اشتراك Azure. للحصول على معلومات حول اشتراكات Azure، انتقل إلى [صفحة كيفية شراء Azure](https://azure.microsoft.com/pricing/purchase-options/).
    
- مساحة عنوان IPv4 الخاصة المتوفرة لتعيينها إلى الشبكة الظاهرية وشبكاتها الفرعية، مع مساحة كافية للنمو لاستيعاب عدد الأجهزة الظاهرية المطلوبة الآن وفي المستقبل.
    
- جهاز VPN متوفر في شبكتك المحلية لإنهاء اتصال VPN من موقع إلى موقع الذي يدعم متطلبات IPsec. لمزيد من المعلومات، راجع [حول أجهزة VPN لاتصالات الشبكة الظاهرية من موقع إلى موقع](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- يتغير إلى البنية الأساسية للتوجيه بحيث تتم إعادة توجيه نسبة استخدام الشبكة الموجهة إلى مساحة عنوان شبكة Azure الظاهرية إلى جهاز VPN الذي يستضيف اتصال VPN من موقع إلى موقع.
    
- وكيل ويب يمنح أجهزة الكمبيوتر المتصلة بالشبكة المحلية وشبكة Azure الظاهرية إمكانية الوصول إلى الإنترنت.
    
### <a name="solution-architecture-design-assumptions"></a>افتراضات تصميم بنية الحل

تمثل القائمة التالية خيارات التصميم التي تم إجراؤها لبنية الحل هذه. 
  
- يستخدم هذا الحل شبكة Azure ظاهرية واحدة مع اتصال VPN من موقع إلى موقع. تستضيف شبكة Azure الظاهرية شبكة فرعية واحدة يمكن أن تحتوي على أجهزة ظاهرية متعددة. 
    
- يمكنك استخدام خدمة التوجيه والوصول عن بعد (RRAS) في Windows Server 2016 أو Windows Server 2012 لإنشاء اتصال VPN من موقع إلى موقع ل IPsec بين الشبكة المحلية وشبكة Azure الظاهرية. يمكنك أيضا استخدام خيارات أخرى، مثل أجهزة Cisco أو Juniper Networks VPN.
    
- قد لا تزال الشبكة المحلية تحتوي على خدمات شبكة مثل خدمات مجال Active Directory (AD DS) ونظام أسماء المجالات (DNS) والخوادم الوكيلة. اعتمادا على متطلباتك، قد يكون من المفيد وضع بعض موارد الشبكة هذه في شبكة Azure الظاهرية.
    
بالنسبة إلى شبكة Azure الظاهرية الموجودة مع شبكة فرعية واحدة أو أكثر، حدد ما إذا كانت هناك مساحة عنوان متبقية لشبكة فرعية إضافية لاستضافة الأجهزة الظاهرية المطلوبة، استنادا إلى متطلباتك. إذا لم يكن لديك مساحة عنوان متبقية لشبكة فرعية إضافية، ف قم بإنشاء شبكة ظاهرية إضافية لها اتصال VPN من موقع إلى موقع خاص بها.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>تخطيط تغييرات البنية الأساسية للتوجيه لشبكة Azure الظاهرية

يجب تكوين البنية الأساسية للتوجيه المحلي لإعادة توجيه نسبة استخدام الشبكة الموجهة لمساحة عنوان شبكة Azure الظاهرية إلى جهاز VPN المحلي الذي يستضيف اتصال VPN من موقع إلى موقع.
  
تعتمد الطريقة الدقيقة لتحديث البنية الأساسية للتوجيه على كيفية إدارة معلومات التوجيه، والتي يمكن أن تكون:
  
- يتم تحديث جدول التوجيه استنادا إلى التكوين اليدوي.
    
- يتم تحديث جدول التوجيه استنادا إلى بروتوكولات التوجيه، مثل بروتوكول معلومات التوجيه (TP) أو فتح أقصر مسار أولا (OSPF).
    
استشر متخصص التوجيه للتأكد من إعادة توجيه نسبة استخدام الشبكة الموجهة لشبكة Azure الظاهرية إلى جهاز VPN المحلي.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>التخطيط لقواعد جدار الحماية لنسبة استخدام الشبكة من وإلى جهاز VPN المحلي

إذا كان جهاز VPN الخاص بك على شبكة محيطة تحتوي على جدار حماية بين الشبكة المحيطة والإنترنت، فقد تحتاج إلى تكوين جدار الحماية للقواعد التالية للسماح باتصال VPN من موقع إلى موقع.
  
- نسبة استخدام الشبكة إلى جهاز VPN (الوارد من الإنترنت):
    
  - عنوان IP الوجهة لجهاز VPN وبروتوكول IP 50
    
  - عنوان IP الوجهة لجهاز VPN ومنفذ وجهة UDP 500
    
  - عنوان IP الوجهة لجهاز VPN ومنفذ وجهة UDP 4500
    
- نسبة استخدام الشبكة من جهاز VPN (الصادرة إلى الإنترنت):
    
  - عنوان IP المصدر لجهاز VPN وبروتوكول IP 50
    
  - عنوان IP المصدر لجهاز VPN ومنفذ مصدر UDP 500
    
  - عنوان IP المصدر لجهاز VPN ومنفذ مصدر UDP 4500
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>التخطيط لمساحة عنوان IP الخاص لشبكة Azure الظاهرية

يجب أن تكون مساحة عنوان IP الخاص لشبكة Azure الظاهرية قادرة على استيعاب العناوين المستخدمة من قبل Azure لاستضافة الشبكة الظاهرية ومع شبكة فرعية واحدة على الأقل تحتوي على عناوين كافية لأجهزة Azure الظاهرية.
  
لتحديد عدد العناوين المطلوبة للشبكة الفرعية، قم بحساب عدد الأجهزة الظاهرية التي تحتاجها الآن، وتقدير النمو المستقبلي، ثم استخدم الجدول التالي لتحديد حجم الشبكة الفرعية.
  
|**عدد الأجهزة الظاهرية المطلوبة**|**عدد بتات المضيف المطلوبة**|**حجم الشبكة الفرعية**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7  <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>تخطيط ورقة العمل لتكوين شبكة Azure الظاهرية
<a name="worksheet"> </a>

قبل إنشاء شبكة Azure ظاهرية لاستضافة الأجهزة الظاهرية، يجب تحديد الإعدادات المطلوبة في الجداول التالية.
  
لإعدادات الشبكة الظاهرية، املأ الجدول V.
  
 **الجدول V: تكوين الشبكة الظاهرية الداخلية**
  
|**البند**|**عنصر التكوين**|**الوصف**|**قيمه**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |اسم الشبكة الظاهرية  <br/> |اسم لتعيينه إلى شبكة Azure الظاهرية (مثال DirSyncNet).  <br/> |![خط.](../media/Common-Images/TableLine.png) |
|2.  <br/> |موقع الشبكة الظاهرية  <br/> |مركز بيانات Azure الذي سيحتوي على الشبكة الظاهرية (مثل غرب الولايات المتحدة).  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |عنوان IP لجهاز VPN  <br/> |عنوان IPv4 العام لواجهة جهاز VPN على الإنترنت. تعاون مع قسم تكنولوجيا المعلومات لتحديد هذا العنوان.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |مساحة عنوان الشبكة الظاهرية  <br/> |مساحة العنوان (المعرفة في بادئة عنوان خاص واحد) للشبكة الظاهرية. اعمل مع قسم تكنولوجيا المعلومات لتحديد مساحة العنوان هذه. يجب أن تكون مساحة العنوان بتنسيق التوجيه بين المجالات (CIDR) بلا فئة، والمعروف أيضا بتنسيق بادئة الشبكة. مثال هو 10.24.64.0/20.  <br/> |![خط.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |مفتاح IPsec المشترك  <br/> |سلسلة أبجدية رقمية عشوائية مكونة من 32 حرفا سيتم استخدامها لمصادقة كلا جانبي اتصال VPN من موقع إلى موقع. اعمل مع قسم تكنولوجيا المعلومات أو قسم الأمان لتحديد هذه القيمة الرئيسية ثم تخزينها في موقع آمن. بدلا من ذلك، راجع [إنشاء سلسلة عشوائية لمفتاح IPsec مشترك مسبقا](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![خط.](../media/Common-Images/TableLine.png) <br/> |
   
املأ الجدول S للشبكات الفرعية لهذا الحل.
  
- بالنسبة للشبكة الفرعية الأولى، حدد مساحة عنوان 28 بت (بطول /28 بادئة) للشبكة الفرعية لبوابة Azure. راجع [حساب مساحة عنوان الشبكة الفرعية للبوابة لشبكات Azure الظاهرية](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) للحصول على معلومات حول كيفية تحديد مساحة العنوان هذه.
    
- بالنسبة للشبكة الفرعية الثانية، حدد اسما مألوفا ومساحة عنوان IP واحدة استنادا إلى مساحة عنوان الشبكة الظاهرية والغرض الوصفي.
    
اعمل مع قسم تكنولوجيا المعلومات لتحديد مساحات العناوين هذه من مساحة عنوان الشبكة الظاهرية. يجب أن تكون كلتا المساحتين في تنسيق CIDR.
  
 **الجدول S: الشبكات الفرعية في الشبكة الظاهرية**
  
|**البند**|**اسم الشبكة الفرعية**|**مساحة عنوان الشبكة الفرعية**|**الغرض**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة من قبل بوابة Azure.  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
بالنسبة إلى خوادم DNS المحلية التي تريد أن تستخدمها الأجهزة الظاهرية في الشبكة الظاهرية، قم بتعبئة الجدول D. امنح كل خادم DNS اسما مألوفا وعنوان IP واحدا. لا يحتاج هذا الاسم المألوف إلى مطابقة اسم المضيف أو اسم الكمبيوتر لخادم DNS. لاحظ أنه تم سرد إدخالين فارغين، ولكن يمكنك إضافة المزيد. تعاون مع قسم تكنولوجيا المعلومات لتحديد هذه القائمة.
  
 **الجدول D: خوادم DNS المحلية**
  
|**البند**|**اسم مألوف لخادم DNS**|**عنوان IP لخادم DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
لتوجيه الحزم من شبكة Azure الظاهرية إلى شبكة مؤسستك عبر اتصال VPN من موقع إلى موقع، يجب تكوين الشبكة الظاهرية مع شبكة محلية. تحتوي هذه الشبكة المحلية على قائمة بمساحات العناوين (بتنسيق CIDR) لكافة المواقع على الشبكة المحلية لمؤسستك التي يجب أن تصل إليها الأجهزة الظاهرية في الشبكة الظاهرية. يمكن أن يكون هذا كل المواقع على الشبكة المحلية أو مجموعة فرعية. يجب أن تكون قائمة مساحات العناوين التي تحدد شبكتك المحلية فريدة ويجب ألا تتداخل مع مساحات العناوين المستخدمة لهذه الشبكة الظاهرية أو الشبكات الظاهرية الأخرى الداخلية.
  
بالنسبة إلى مجموعة مسافات عناوين الشبكة المحلية، قم بتعبئة الجدول L. لاحظ أن هناك ثلاثة إدخالات فارغة مدرجة ولكنك ستحتاج عادة إلى المزيد. تعاون مع قسم تكنولوجيا المعلومات لتحديد هذه القائمة.
  
 **الجدول L: بادئات العنوان للشبكة المحلية**
  
|**البند**|**مساحة عنوان الشبكة المحلية**|
|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![خط](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>مخطط التوزيع
<a name="DeploymentRoadmap"> </a>

يتكون إنشاء الشبكة الظاهرية الداخلية وإضافة الأجهزة الظاهرية في Azure من ثلاث مراحل:
  
- المرحلة 1: إعداد الشبكة المحلية.
    
- المرحلة 2: إنشاء شبكة ظاهرية داخلية في Azure.
    
- المرحلة 3 (اختيارية): إضافة أجهزة ظاهرية.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>المرحلة 1: إعداد الشبكة المحلية
<a name="Phase1"></a>

يجب تكوين الشبكة المحلية الخاصة بك مع مسار يشير إلى ويرسل في نهاية المطاف نسبة استخدام الشبكة الموجهة لمساحة عنوان الشبكة الظاهرية إلى جهاز التوجيه على حافة الشبكة المحلية. استشر مسؤول الشبكة لتحديد كيفية إضافة المسار إلى البنية الأساسية للتوجيه للشبكة المحلية.
  
إليك التكوين الناتج.
  
![يجب أن يكون للشبكة المحلية مسار لمساحة عنوان الشبكة الظاهرية التي تشير نحو جهاز VPN.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>المرحلة 2: إنشاء شبكة ظاهرية داخلية في Azure
<a name="Phase2"></a>

أولا، افتح موجه Azure PowerShell. إذا لم تقم بتثبيت Azure PowerShell، فراجع [بدء استخدام Azure PowerShell](/powershell/azure/get-started-azureps).

 
بعد ذلك، قم بتسجيل الدخول إلى حساب Azure الخاص بك باستخدام هذا الأمر.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام الأمر التالي.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

قم بتعيين اشتراك Azure باستخدام هذه الأوامر. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف < والأحرف >، باسم الاشتراك الصحيح.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

بعد ذلك، قم بإنشاء مجموعة موارد جديدة للشبكة الظاهرية الخاصة بك. لتحديد اسم مجموعة موارد فريد، استخدم هذا الأمر لإدراج مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

إنشاء مجموعة الموارد الجديدة باستخدام هذه الأوامر.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، يمكنك إنشاء شبكة Azure الظاهرية.
  
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
  
![لم يتم بعد توصيل الشبكة الظاهرية بالشبكة المحلية.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
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
  
![تحتوي الشبكة الظاهرية الآن على بوابة.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
بعد ذلك، قم بتكوين جهاز VPN المحلي للاتصال ببوابة Azure VPN. لمزيد من المعلومات، راجع [حول أجهزة VPN لاتصالات Azure Virtual Network من موقع إلى موقع](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
لتكوين جهاز VPN الخاص بك، ستحتاج إلى ما يلي:
  
- عنوان IPv4 العام لبوابة Azure VPN لشبكتك الظاهرية. استخدم الأمر **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** لعرض هذا العنوان.
    
- مفتاح IPsec المشترك مسبقا لاتصال VPN من موقع إلى موقع (الجدول V - العنصر 5 - عمود القيمة).
    
إليك التكوين الناتج.
  
![الشبكة الظاهرية متصلة الآن بالشبكة المحلية.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>المرحلة 3 (اختياري): إضافة أجهزة ظاهرية

إنشاء الأجهزة الظاهرية التي تحتاجها في Azure. لمزيد من المعلومات، راجع [إنشاء جهاز ظاهري Windows باستخدام مدخل Azure](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
استخدم الإعدادات التالية:
  
- في علامة التبويب **"Basics** "، حدد نفس الاشتراك ومجموعة الموارد مثل شبكتك الظاهرية. ستحتاج إليها لاحقا لتسجيل الدخول إلى الجهاز الظاهري. في قسم **تفاصيل المثيل** ، اختر حجم الجهاز الظاهري المناسب. تسجيل اسم مستخدم حساب المسؤول وكلمة المرور في موقع آمن. 
    
- في علامة التبويب **"Networking** "، حدد اسم الشبكة الظاهرية والشبكة الفرعية لاستضافة الأجهزة الظاهرية (وليس GatewaySubnet). اترك كافة الإعدادات الأخرى عند قيمها الافتراضية.
    
تحقق من أن جهازك الظاهري يستخدم DNS بشكل صحيح عن طريق التحقق من DNS الداخلي للتأكد من إضافة سجلات العنوان (A) للجهاز الظاهري الجديد. للوصول إلى الإنترنت، يجب تكوين أجهزة Azure الظاهرية لاستخدام الخادم الوكيل للشبكة المحلية. اتصل بمسؤول الشبكة للحصول على خطوات تكوين إضافية لتنفيذها على الخادم.
  
إليك التكوين الناتج.
  
![تستضيف الشبكة الظاهرية الآن الأجهزة الظاهرية التي يمكن الوصول إليها من الشبكة المحلية.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>الخطوة التالية
  
[نشر مزامنة دليل Microsoft 365 في Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)