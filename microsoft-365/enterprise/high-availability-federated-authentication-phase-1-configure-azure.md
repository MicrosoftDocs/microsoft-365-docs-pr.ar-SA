---
title: المرحلة 1 من المصادقة المتحدة عالية التوفر تكوين Azure
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'ملخص: قم بتكوين البنية الأساسية ل Microsoft Azure لاستضافة المصادقة الخارجية عالية التوفر Microsoft 365.'
ms.openlocfilehash: 35666baf98b45419f41a0078729ac5a5a6fab995
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/04/2022
ms.locfileid: "63569377"
---
# <a name="high-availability-federated-authentication-phase-1-configure-azure"></a>المرحلة 1 من المصادقة المتحدة عالية التوفر: تكوين Azure

في هذه المرحلة، يمكنك إنشاء مجموعات الموارد والشبكات الظاهرية (VNet) ومجموعات التوفر في Azure التي ستستضيف الأجهزة الظاهرية في المراحل 2 و3 و4. يجب إكمال هذه المرحلة قبل الانتقال إلى المرحلة [2: تكوين وحدات التحكم بالمجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). راجع [نشر المصادقة](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) المتحدة عالية التوفر Microsoft 365 Azure لجميع المراحل.
  
يجب أن يتم توفير Azure مع هذه المكونات الأساسية:
  
- مجموعات الموارد
    
- شبكة Azure الظاهرية (VNet) مع شبكات فرعية لاستضافة أجهزة Azure الظاهرية
    
- مجموعات أمان الشبكة لأداء عزل الشبكة الفرعية
    
- مجموعات التوفر
    
## <a name="configure-azure-components"></a>تكوين مكونات Azure

قبل البدء في تكوين مكونات Azure، قم بتعبئة الجداول التالية. لمساعدتك في إجراءات تكوين Azure، اطبع هذا المقطع واكتب المعلومات المطلوبة أو انسخ هذا المقطع إلى مستند واملأه. لإعدادات VNet، قم بتعبئة الجدول V.
  
|**عنصر**|**إعداد التكوين**|**الوصف**|**القيمة**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |اسم VNet  <br/> |اسم لتعيينه إلى VNet (على سبيل المثال FedAuthNet).  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |موقع VNet  <br/> |مركز بيانات Azure الإقليمي الذي سيحتوي على الشبكة الظاهرية.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |عنوان IP لجهاز VPN  <br/> |عنوان IPv4 العام لواجهة جهاز VPN على الإنترنت.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |مساحة عنوان VNet  <br/> |مساحة العنوان للشبكة الظاهرية. اعمل مع قسم تكنولوجيا المعلومات لتحديد مساحة العنوان هذه.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |مفتاح IPsec المشترك  <br/> |سلسلة رقمية عشوائية من 32 حرفا سيتم استخدامها لمصادقة كلا جانبي اتصال VPN من موقع إلى موقع. اعمل مع قسم المعلومات أو قسم الأمان لتحديد قيمة المفتاح هذه. بدلا من ذلك، راجع [إنشاء سلسلة عشوائية لمفتاح IPsec تم اختياره مسبقا](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول الخامس: تكوين الشبكة الظاهرية المحلية**
  
بعد ذلك، قم بتعبئة الجدول S للنتوءات الفرعية لهذا الحل. يجب أن تكون كل مسافات العنوان بتنسيق التوجيه بين الفئات (CIDR)، المعروف أيضا بتنسيقبادات الشبكة. مثال على ذلك هو 10.24.64.0/20.
  
بالنسبة إلى الشبكات الفرعية الثلاثة الأولى، حدد اسما ومساحة عنوان IP واحدة استنادا إلى مساحة عنوان الشبكة الظاهرية. بالنسبة إلى شبكة البوابة الفرعية، حدد مساحة العنوان 27 بت (بطول البادرة 27/) الخاص 27 شبكة بوابة Azure الفرعية مع ما يلي:
  
1. قم بتعيين بت المتغيرات في مساحة العنوان في VNet إلى 1، حتى البتات التي تستخدمها شبكة البوابة الفرعية، ثم قم بتعيين البتات المتبقية إلى 0.
    
2. تحويل البت الناتج إلى رقم عشري والتعبير عنه كمساحة عنوان مع تعيين طول البادوية إلى حجم الشبكة الفرعية للبوابة.
    
راجع [حاسبة مساحة العنوان لبوابة Azure](address-space-calculator-for-azure-gateway-subnets.md) الفرعية لحظر أوامر PowerShell وتطبيق وحدة تحكم C# أو Python الذي ينفذ هذه العملية الحسابية لك.
  
اعمل مع قسم تكنولوجيا المعلومات لتحديد مسافات العنوان هذه من مساحة عنوان الشبكة الظاهرية.
  
|**عنصر**|**اسم الشبكة الفرعية**|**مساحة عنوان الشبكة الفرعية**|**الغرض**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية التي تستخدمها وحدة التحكم في مجال خدمات مجال Active Directory (AD DS) وأجهزة خادم مزامنة الدليل الظاهرية (VMs).  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة بواسطة AD FS VMs.  <br/> |
|3.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية التي يستخدمها وكيل تطبيق الويب VMs.  <br/> |
|4.  <br/> |GatewaySubnet  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |الشبكة الفرعية المستخدمة بواسطة VMs بوابة Azure.  <br/> |
   
 **الجدول S: الشبكات الفرعية في الشبكة الظاهرية**
  
بعد ذلك، قم بتعبئة الجدول الأول عن عناوين IP الثابتة المعينة إلى الأجهزة الظاهرية ومثيلات موازن التحميل.
  
|**عنصر**|**الغرض**|**عنوان IP على الشبكة الفرعية**|**القيمة**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |عنوان IP ثابت ل وحدة التحكم بالمجال الأولى  <br/> |عنوان IP المحتمل الرابع لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 1 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |عنوان IP ثابت ل وحدة التحكم بالمجال الثاني  <br/> |عنوان IP المحتمل الخامس لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 1 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |عنوان IP ثابت لخادم مزامنة الدليل  <br/> |عنوان IP المحتمل السادس لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 1 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |عنوان IP ثابت لموازن التحميل الداخلي للخوادم AD FS  <br/> |عنوان IP المحتمل الرابع لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 2 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|5.  <br/> |عنوان IP ثابت لأول خادم AD FS  <br/> |عنوان IP المحتمل الخامس لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 2 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|6.  <br/> |عنوان IP ثابت للخادم AD FS الثاني  <br/> |عنوان IP المحتمل السادس لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 2 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|7.  <br/> |عنوان IP ثابت لأول خادم وكيل لتطبيق ويب  <br/> |عنوان IP المحتمل الرابع لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 3 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|8.  <br/> |عنوان IP ثابت للخادم الوكيل الثاني لتطبيق ويب  <br/> |عنوان IP المحتمل الخامس لمساحة عنوان الشبكة الفرعية المعرفة في العنصر 3 من الجدول S.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول 1: عناوين IP الثابتة في الشبكة الظاهرية**
  
بالنسبة إلى خادمي نظام أسماء المجالات (DNS) في الشبكة المحلية التي تريد استخدامها عند إعداد وحدات تحكم المجال في الشبكة الظاهرية في البداية، قم بتعبئة الجدول D. استخدم قسم المعلومات لتحديد هذه القائمة.
  
|**عنصر**|**اسم خادم DNS**|**عنوان IP للخادم DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول D: خوادم DNS في الموقع**
  
توجيه الحزم من الشبكة المحلية إلى شبكة مؤسستك عبر اتصال VPN من موقع إلى موقع، يجب تكوين الشبكة الظاهرية مع شبكة محلية تحتوي على قائمة بمساحات العنوان (في CIDR notation) لكل المواقع التي يمكن الوصول إليها على الشبكة المحلية لمنظمتك. يجب أن تكون قائمة مساحات العنوان التي تعرف شبكتك المحلية فريدة ويجب ألا تتداخل مع مساحة العنوان المستخدمة للشبكات الظاهرية الأخرى أو الشبكات المحلية الأخرى.
  
بالنسبة إلى مجموعة مساحات عنوان الشبكة المحلية، قم بتعبئة الجدول L. تجدر الإشارة إلى أن ثلاثة إدخالات فارغة مدرجة ولكنك ستحتاج عادة إلى المزيد. اعمل مع قسم المعلومات لتحديد قائمة مساحات العنوان هذه.
  
|**عنصر**|**مساحة عنوان الشبكة المحلية**|
|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول L:بادئات العنوان للشبكة المحلية**
  
فلنبدأ الآن في إنشاء البنية الأساسية ل Azure لاستضافة المصادقة الخارجية Microsoft 365.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
أولا، ابدأ مطالبة Azure PowerShell ثم قم بتسجيل الدخول إلى حسابك.
  
```powershell
Connect-AzAccount
```

> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم هذا Microsoft Excel [تكوين.](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) 

احصل على اسم اشتراكك باستخدام الأمر التالي.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

بالنسبة للإصدارات القديمة من Azure PowerShell، استخدم هذا الأمر بدلا من ذلك.
  
```powershell
Get-AzSubscription | Sort Name | Select SubscriptionName
```

تعيين اشتراكك في Azure. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك \< and > الأحرف، بالاسم الصحيح.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

بعد ذلك، قم بإنشاء مجموعات الموارد الجديدة. لتحديد مجموعة فريدة من أسماء مجموعات الموارد، استخدم هذا الأمر لقائمة مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

قم بتعبئة الجدول التالي لمجموعة أسماء مجموعة الموارد الفريدة.
  
|**عنصر**|**اسم مجموعة الموارد**|**الغرض**|
|:-----|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |وحدات التحكم بالمجال  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |خوادم AD FS  <br/> |
|3.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |خوادم وكيل تطبيق ويب  <br/> |
|4.  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |عناصر البنية الأساسية  <br/> |
   
 **الجدول R: مجموعات الموارد**
  
أنشئ مجموعات الموارد الجديدة باستخدام هذه الأوامر.
  
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

بعد ذلك، يمكنك إنشاء مجموعات أمان الشبكة لكل شبكة فرعية تحتوي على أجهزة ظاهرية. لتنفيذ عزل الشبكة الفرعية، يمكنك إضافة قواعد لأنواع معينة من حركة المرور المسموح بها أو التي تم رفضها إلى مجموعة أمان الشبكة لشبكة فرعية.
  
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
> لا تعتمد المصادقة الخارجية للمستخدمين الفرديين على أي موارد المحلية. ومع ذلك، إذا لم يكن اتصال VPN هذا من موقع إلى موقع متوفرا، فإن وحدات التحكم بالمجال في VNet لن تتلقى تحديثات حسابات المستخدمين والمجموعات التي تم إدخالها في خدمات مجال Active Directory المحلية. للتأكد من عدم حدوث ذلك، يمكنك تكوين توفر عال لاتصال VPN من موقع إلى موقع. لمزيد من المعلومات، راجع الاتصالية عبر الموقع و [VNet-to-VNet المتوفرة بشكل كبير](/azure/vpn-gateway/vpn-gateway-highlyavailable)
  
بعد ذلك، سجل عنوان IPv4 العام لبوابة Azure VPN للشبكة الظاهرية من عرض هذا الأمر:
  
```powershell
Get-AzPublicIpAddress -Name $publicGatewayVipName -ResourceGroupName $rgName
```

بعد ذلك، قم بتكوين جهاز VPN الخاص بك في الموقع للاتصال ببوابة Azure VPN. لمزيد من المعلومات، راجع [تكوين جهاز VPN](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
لتكوين جهاز VPN الخاص بك، ستحتاج إلى ما يلي:
  
- عنوان IPv4 العام لبوابة Azure VPN.
    
- مفتاح IPsec المشترك مسبقا لاتصال VPN من موقع إلى موقع (الجدول V - العنصر 5 - عمود القيمة).
    
بعد ذلك، تأكد من أن مساحة العنوان للشبكة الظاهرية يمكن الوصول إليها من الشبكة المحلية. يتم ذلك عادة عن طريق إضافة مسار مناظر لمساحة عنوان الشبكة الظاهرية إلى جهاز VPN الخاص بك، ثم الإعلان عن المسار إلى بقية البنية الأساسية التوجيه لشبكة المؤسسة. اعمل مع قسم المعلومات لتحديد كيفية القيام بذلك.
  
بعد ذلك، حدد أسماء مجموعات التوفر الثلاث. املأ الجدول A. 
  
|**عنصر**|**الغرض**|**اسم مجموعة التوفر**|
|:-----|:-----|:-----|
|1.  <br/> |وحدات التحكم بالمجال  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |خوادم AD FS  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |خوادم وكيل تطبيق ويب  <br/> |![السطر.](../media/Common-Images/TableLine.png)  <br/> |
   
 **الجدول أ: مجموعات التوفر**
  
ستحتاج إلى هذه الأسماء عند إنشاء الأجهزة الظاهرية في المراحل 2 و3 و4.
  
قم بإنشاء مجموعات التوفر الجديدة باستخدام أوامر Azure PowerShell هذه.
  
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

هذا هو التكوين الناتج عن الإكمال الناجح لهذه المرحلة.
  
**المرحلة 1: البنية الأساسية ل Azure للمصادقة الخارجية عالية التوفر Microsoft 365**

![المرحلة الأولى من التوفر العالي Microsoft 365 المتحدة في Azure مع البنية الأساسية ل Azure.](../media/4e7ba678-07df-40ce-b372-021bf7fc91fa.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدام [المرحلة الثانية: تكوين وحدات التحكم بالمجالات](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) للمتابعة مع تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر المصادقة المتحدة عالية التوفر Microsoft 365 Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[الهوية المتحدة لبيئة Microsoft 365/اختبارك](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 حل وهندسة](../solutions/index.yml)

[فهم Microsoft 365 الهوية](deploy-identity-solution-identity-model.md)