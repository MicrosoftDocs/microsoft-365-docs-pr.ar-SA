---
title: مرحلة المصادقة الموحدة 1 عالية التوفر لتكوين Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 91266aac-4d00-4b5f-b424-86a1a837792c
description: 'ملخص: تكوين البنية الأساسية ل Microsoft Azure لاستضافة مصادقة موحدة عالية التوفر Microsoft 365.'
ms.openlocfilehash: f83aa494fcdead8f29810dea06193934b8ef26b9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098373"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>مرحلة المصادقة الموحدة عالية التوفر 1: تكوين Azure

في هذه المرحلة، يمكنك إنشاء مجموعات الموارد والشبكة الظاهرية (VNet) ومجموعات التوفر في Azure التي ستستضيف الأجهزة الظاهرية في المراحل 2 و3 و4. يجب إكمال هذه المرحلة قبل الانتقال إلى [المرحلة 2: تكوين وحدات التحكم بالمجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). راجع [نشر المصادقة الموحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) لجميع المراحل.
  
يجب توفير Azure مع هذه المكونات الأساسية:
  
- مجموعات الموارد
    
- شبكة Azure الظاهرية (VNet) متعددة الأماكن مع شبكات فرعية لاستضافة أجهزة Azure الظاهرية
    
- مجموعات أمان الشبكة لتنفيذ عزل الشبكة الفرعية
    
- مجموعات التوفر
    
## <a name="configure-azure-components"></a>تكوين مكونات Azure

قبل البدء في تكوين مكونات Azure، قم بتعبئة الجداول التالية. لمساعدتك في إجراءات تكوين Azure، اطبع هذا القسم واكتب المعلومات المطلوبة أو انسخ هذا المقطع إلى مستند وقم بتعبئته. لإعدادات الشبكة الظاهرية، املأ الجدول V.
  
|**البند**|**إعداد التكوين**|**الوصف**|**قيمه**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |اسم الشبكة الظاهرية  <br/> |اسم لتعيينه إلى VNet (على سبيل المثال FedAuthNet).  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |موقع الشبكة الظاهرية  <br/> |مركز بيانات Azure الإقليمي الذي سيحتوي على الشبكة الظاهرية.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |عنوان IP لجهاز VPN  <br/> |عنوان IPv4 العام لواجهة جهاز VPN على الإنترنت.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |مساحة عنوان الشبكة الظاهرية  <br/> |مساحة العنوان للشبكة الظاهرية. اعمل مع قسم تكنولوجيا المعلومات لتحديد مساحة العنوان هذه.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |مفتاح IPsec المشترك  <br/> |سلسلة أبجدية رقمية عشوائية مكونة من 32 حرفا سيتم استخدامها لمصادقة كلا جانبي اتصال VPN من موقع إلى موقع. العمل مع قسم تكنولوجيا المعلومات أو الأمان لتحديد هذه القيمة الرئيسية. بدلا من ذلك، راجع [إنشاء سلسلة عشوائية لمفتاح IPsec مشترك مسبقا](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول V: تكوين الشبكة الظاهرية الداخلية**
  
بعد ذلك، قم بتعبئة الجدول S للشبكات الفرعية لهذا الحل. يجب أن تكون كافة مسافات العناوين بتنسيق التوجيه بين المجالات (CIDR) بلا فئة، والمعروف أيضا بتنسيق بادئة الشبكة. مثال هو 10.24.64.0/20.
  
بالنسبة إلى الشبكات الفرعية الثلاث الأولى، حدد اسما ومساحة عنوان IP واحدة استنادا إلى مساحة عنوان الشبكة الظاهرية. بالنسبة للشبكة الفرعية للبوابة، حدد مساحة العنوان 27 بت (بطول /27 بادئة) للشبكة الفرعية لبوابة Azure مع ما يلي:
  
1. قم بتعيين وحدات البت المتغيرة في مساحة عنوان الشبكة الظاهرية إلى 1، وصولا إلى وحدات البت المستخدمة من قبل الشبكة الفرعية للبوابة، ثم قم بتعيين وحدات البت المتبقية إلى 0.
    
2. تحويل وحدات البت الناتجة إلى عشرية والتعبير عنها كمساحة عنوان مع تعيين طول البادئة إلى حجم الشبكة الفرعية للبوابة.
    
راجع [حاسبة مساحة العنوان للشبكات الفرعية لبوابة Azure](address-space-calculator-for-azure-gateway-subnets.md) لكتلة أوامر PowerShell وتطبيق وحدة تحكم C# أو Python الذي يقوم بإجراء هذه العملية الحسابية نيابة عنك.
  
اعمل مع قسم تكنولوجيا المعلومات لتحديد مساحات العناوين هذه من مساحة عنوان الشبكة الظاهرية.
  
|**البند**|**اسم الشبكة الفرعية**|**مساحة عنوان الشبكة الفرعية**|**الغرض**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة من قبل وحدة تحكم مجال خدمات مجال Active Directory (AD DS) والأجهزة الظاهرية لخادم مزامنة الدليل (VMs).  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة من قبل الأجهزة الظاهرية ل AD FS.  <br/> |
|3.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة من قبل الأجهزة الظاهرية وكيل تطبيق الويب.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة من قبل الأجهزة الظاهرية لبوابة Azure.  <br/> |
   
 **الجدول S: الشبكات الفرعية في الشبكة الظاهرية**
  
بعد ذلك، املأ الجدول I لعناوين IP الثابتة المعينة إلى الأجهزة الظاهرية ومثيلات موازن التحميل.
  
|**البند**|**الغرض**|**عنوان IP على الشبكة الفرعية**|**قيمه**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |عنوان IP ثابت لوحدة التحكم بالمجال الأولى  <br/> |عنوان IP الرابع الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 1 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |عنوان IP ثابت لوحدة التحكم بالمجال الثانية  <br/> |عنوان IP الخامس الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 1 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |عنوان IP ثابت لخادم مزامنة الدليل  <br/> |عنوان IP السادس الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 1 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |عنوان IP ثابت لموازن التحميل الداخلي لخوادم AD FS  <br/> |عنوان IP الرابع الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 2 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |عنوان IP ثابت لخادم AD FS الأول  <br/> |عنوان IP الخامس الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 2 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |عنوان IP ثابت لخادم AD FS الثاني  <br/> |عنوان IP السادس الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 2 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |عنوان IP ثابت لخادم وكيل تطبيق الويب الأول  <br/> |عنوان IP الرابع الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 3 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |عنوان IP ثابت لخادم وكيل تطبيق الويب الثاني  <br/> |عنوان IP الخامس الممكن لمساحة عنوان الشبكة الفرعية المحددة في العنصر 3 من الجدول S.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول I: عناوين IP الثابتة في الشبكة الظاهرية**
  
بالنسبة إلى خادمين من خوادم نظام أسماء المجالات (DNS) في الشبكة المحلية التي تريد استخدامها عند إعداد وحدات التحكم بالمجال في الشبكة الظاهرية في البداية، قم بتعبئة الجدول D. استخدم قسم تكنولوجيا المعلومات لتحديد هذه القائمة.
  
|**البند**|**اسم مألوف لخادم DNS**|**عنوان IP لخادم DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول D: خوادم DNS المحلية**
  
لتوجيه الحزم من الشبكة الداخلية إلى شبكة المؤسسة عبر اتصال VPN من موقع إلى موقع، يجب تكوين الشبكة الظاهرية مع شبكة محلية تحتوي على قائمة بمساحات العناوين (في علامة CIDR) لجميع المواقع التي يمكن الوصول إليها على الشبكة المحلية لمؤسستك. يجب أن تكون قائمة مساحات العناوين التي تحدد شبكتك المحلية فريدة ويجب ألا تتداخل مع مساحة العنوان المستخدمة للشبكات الظاهرية الأخرى أو الشبكات المحلية الأخرى.
  
بالنسبة إلى مجموعة مسافات عناوين الشبكة المحلية، قم بتعبئة الجدول L. لاحظ أن هناك ثلاثة إدخالات فارغة مدرجة ولكنك ستحتاج عادة إلى المزيد. اعمل مع قسم تكنولوجيا المعلومات لتحديد قائمة مساحات العناوين هذه.
  
|**البند**|**مساحة عنوان الشبكة المحلية**|
|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول L: بادئات العنوان للشبكة المحلية**
  
الآن دعونا نبدأ في بناء البنية الأساسية ل Azure لاستضافة المصادقة الموحدة الخاصة بك Microsoft 365.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية أحدث إصدار من Azure PowerShell. راجع [بدء استخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
أولا، ابدأ موجه Azure PowerShell وقم بتسجيل الدخول إلى حسابك.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم [مصنف التكوين Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) هذا. 

احصل على اسم اشتراكك باستخدام الأمر التالي.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

بالنسبة للإصدارات القديمة من Azure PowerShell، استخدم هذا الأمر بدلا من ذلك.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

تعيين اشتراك Azure الخاص بك. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف \< and > ، بالاسم الصحيح.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

بعد ذلك، قم بإنشاء مجموعات الموارد الجديدة. لتحديد مجموعة فريدة من أسماء مجموعات الموارد، استخدم هذا الأمر لإدراج مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

املأ الجدول التالي لمجموعة أسماء مجموعات الموارد الفريدة.
  
|**البند**|**اسم مجموعة الموارد**|**الغرض**|
|:-----|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |وحدات التحكم بالمجال  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |خوادم AD FS  <br/> |
|3.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |خوادم وكيل تطبيق ويب  <br/> |
|4.  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |عناصر البنية الأساسية  <br/> |
   
 **الجدول R: مجموعات الموارد**
  
إنشاء مجموعات الموارد الجديدة باستخدام هذه الأوامر.
  
```powershell
$locName="<an Azure location, such as West US>"
$rgName="<Table R - Item 1 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 2 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 3 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
$rgName="<Table R - Item 4 - Name column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، يمكنك إنشاء شبكة Azure الظاهرية وشبكاتها الفرعية.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
# Get the shortened version of the location
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the subnets
$subnet1Name="<Table S - Item 1 - Subnet name column>"
$subnet1Prefix="<Table S - Item 1 - Subnet address space column>"
$subnet1=New-AzVirtualNetworkSubnetConfig -Name $subnet1Name -AddressPrefix $subnet1Prefix
$subnet2Name="<Table S - Item 2 - Subnet name column>"
$subnet2Prefix="<Table S - Item 2 - Subnet address space column>"
$subnet2=New-AzVirtualNetworkSubnetConfig -Name $subnet2Name -AddressPrefix $subnet2Prefix
$subnet3Name="<Table S - Item 3 - Subnet name column>"
$subnet3Prefix="<Table S - Item 3 - Subnet address space column>"
$subnet3=New-AzVirtualNetworkSubnetConfig -Name $subnet3Name -AddressPrefix $subnet3Prefix
$gwSubnet4Prefix="<Table S - Item 4 - Subnet address space column>"
$gwSubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnet4Prefix

# Create the virtual network
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gwSubnet,$subnet1,$subnet2,$subnet3 -DNSServer $dnsServers

```

بعد ذلك، يمكنك إنشاء مجموعات أمان الشبكة لكل شبكة فرعية تحتوي على أجهزة ظاهرية. لتنفيذ عزل الشبكة الفرعية، يمكنك إضافة قواعد لأنواع معينة من نسبة استخدام الشبكة المسموح بها أو مرفوضة إلى مجموعة أمان الشبكة لشبكة فرعية.
  
```powershell
# Create network security groups
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName

New-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet1Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet1Name -AddressPrefix $subnet1Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet2Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet2Name -AddressPrefix $subnet2Prefix -NetworkSecurityGroup $nsg

New-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName -Location $locShortName
$nsg=Get-AzNetworkSecurityGroup -Name $subnet3Name -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnet3Name -AddressPrefix $subnet3Prefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

بعد ذلك، استخدم هذه الأوامر لإنشاء البوابات لاتصال VPN من موقع إلى موقع.
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$locName="<Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "GatewaySubnet"

# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -Subnet $subnet

# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig

# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix

# Define the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway

```

> [!NOTE]
> لا تعتمد المصادقة الموحدة للمستخدمين الفرديين على أي موارد محلية. ومع ذلك، إذا أصبح اتصال VPN من موقع إلى موقع غير متوفر، فلن تتلقى وحدات التحكم بالمجال في الشبكة الظاهرية تحديثات لحسابات المستخدمين والمجموعات التي تم إجراؤها في خدمات المجال Active Directory محلي. للتأكد من عدم حدوث ذلك، يمكنك تكوين قابلية وصول عالية لاتصال VPN من موقع إلى موقع. لمزيد من المعلومات، راجع [الاتصال عبر الأماكن و VNet-to-VNet عالي التوفر](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
بعد ذلك، سجل عنوان IPv4 العام لبوابة Azure VPN للشبكة الظاهرية من عرض هذا الأمر:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

بعد ذلك، قم بتكوين جهاز VPN المحلي للاتصال ببوابة Azure VPN. لمزيد من المعلومات، راجع [تكوين جهاز VPN الخاص بك](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
لتكوين جهاز VPN المحلي الخاص بك، ستحتاج إلى ما يلي:
  
- عنوان IPv4 العام لبوابة Azure VPN.
    
- مفتاح IPsec المشترك مسبقا لاتصال VPN من موقع إلى موقع (الجدول V - العنصر 5 - عمود القيمة).
    
بعد ذلك، تأكد من إمكانية الوصول إلى مساحة عنوان الشبكة الظاهرية من شبكتك المحلية. يتم ذلك عادة عن طريق إضافة مسار مطابق لمساحة عنوان الشبكة الظاهرية إلى جهاز VPN الخاص بك ثم الإعلان عن هذا المسار إلى بقية البنية الأساسية للتوجيه لشبكة مؤسستك. اعمل مع قسم تكنولوجيا المعلومات لتحديد كيفية القيام بذلك.
  
بعد ذلك، حدد أسماء ثلاث مجموعات توفر. املأ الجدول A. 
  
|**البند**|**الغرض**|**اسم مجموعة التوفر**|
|:-----|:-----|:-----|
|1.  <br/> |وحدات التحكم بالمجال  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |خوادم AD FS  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |خوادم وكيل تطبيق ويب  <br/> |![خط.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول أ: مجموعات التوفر**
  
ستحتاج إلى هذه الأسماء عند إنشاء الأجهزة الظاهرية في المراحل 2 و3 و4.
  
إنشاء مجموعات التوفر الجديدة باستخدام أوامر Azure PowerShell هذه.
  
```powershell
$locName="<the Azure location for your new resource group>"
$rgName="<Table R - Item 1 - Resource group name column>"
$avName="<Table A - Item 1 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 2 - Resource group name column>"
$avName="<Table A - Item 2 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
$rgName="<Table R - Item 3 - Resource group name column>"
$avName="<Table A - Item 3 - Availability set name column>"
New-AzAvailabilitySet -ResourceGroupName $rgName -Name $avName -Location $locName -Sku Aligned  -PlatformUpdateDomainCount 5 -PlatformFaultDomainCount 2
```

هذا هو التكوين الناتج عن إكمال هذه المرحلة بنجاح.
  
**المرحلة 1: البنية الأساسية ل Azure للمصادقة الموحدة عالية التوفر Microsoft 365**

![المرحلة 1 من قابلية الوصول العالية Microsoft 365 المصادقة الموحدة في Azure مع البنية الأساسية ل Azure.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدم [المرحلة 2: تكوين وحدات التحكم بالمجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) لمتابعة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر مصادقة موحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[هوية موحدة لبيئة التطوير/الاختبار Microsoft 365 الخاصة بك](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[مركز الحلول والهندسة من Microsoft 365](../solutions/index.yml)

[فهم نماذج الهوية Microsoft 365](deploy-identity-solution-identity-model.md)