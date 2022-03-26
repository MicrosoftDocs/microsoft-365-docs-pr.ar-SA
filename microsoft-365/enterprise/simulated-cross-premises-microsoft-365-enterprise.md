---
title: محاكاة شبكة ظاهرية عبر الموقع في Microsoft 365 اختبار
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: seo-marvel-apr2020
description: 'ملخص: إنشاء شبكة ظاهرية محاكاة عبر الموقع في Microsoft Azure كبيئة اختبار Microsoft 365 اختبارية.'
ms.openlocfilehash: 0d0e22b5c9a12f4757a6dff5892ef72a757d2bda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566584"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>محاكاة شبكة ظاهرية عبر الموقع في Microsoft 365 اختبار

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

تسحبك هذه المقالة من خلال إنشاء بيئة سحابة مختلطة محاكاة باستخدام Microsoft Azure باستخدام شبكتين ظاهريتين من Azure. إليك التكوين الناتج. 
  
![المرحلة 3 من بيئة اختبار الشبكة الظاهرية المحلية المحاكاة، مع الجهاز الظاهري DC2 في XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
هذا الأمر يحاكي بيئة إنتاج سحابة Azure IaaS المختلطة ويتكون من:
  
- شبكة محاكاة ومبسطة في الموقع المحلي مستضافة في شبكة ظاهرية من Azure (شبكة TestLab الظاهرية).
    
- شبكة ظاهرية ظاهرية محاكية مستضافة في Azure (XPrem).
    
- علاقة نظير VNet بين شبكتين ظاهريتين.
    
- وحدة تحكم مجال ثانوية في شبكة XPrem الظاهرية.
    
يوفر ذلك أساسا ونقطة بداية مشتركة يمكنك من خلالها: 
  
- تطوير التطبيقات واختبارها في بيئة سحابة مختلطة من Azure IaaS محاكية.
    
- يمكنك إنشاء تكوينات اختبارية لأجهزة الكمبيوتر، بعضها داخل شبكة TestLab الظاهرية والبعض داخل شبكة XPrem الظاهرية، لمحاكاة أحمال عمل تقنية المعلومات المختلطة المستندة إلى السحابة.
    
هناك ثلاث مراحل رئيسية لإعداد بيئة الاختبار هذه:
  
1. تكوين شبكة TestLab الظاهرية.
    
2. إنشاء الشبكة الظاهرية المحلية.
    
3. تكوين DC2.
    
> [!NOTE]
> يتطلب هذا التكوين اشتراك Azure مدفوع. 

يمكنك استخدام البيئة الناتجة لاختبار ميزات وظائف Microsoft 365 للمؤسسة باستخدام "أدلة اختبار [معمل](m365-enterprise-test-lab-guides.md) الاختبار" إضافية أو بنفسك.[](https://www.microsoft.com/microsoft-365/enterprise)

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> انتقل إلى [Microsoft 365 الخاص بالمؤسسة Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf) للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>المرحلة 1: تكوين شبكة TestLab الظاهرية

استخدم الإرشادات الواردة في المرحلة **1** من التكوين [](simulated-ent-base-configuration-microsoft-365-enterprise.md) الأساسي للمؤسسة الذي تم محاكاته لتكوين أجهزة الكمبيوتر DC1 و APP1 و CLIENT1 في شبكة Azure الظاهرية المسماة TestLab.
  
هذا هو التكوين الحالي. 
  
![تكوين قاعدة المؤسسة المحاكاة في Azure.](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>المرحلة الثانية: إنشاء شبكة XPrem الظاهرية

في هذه المرحلة، يمكنك إنشاء شبكة XPrem الظاهرية الجديدة وتكوينها ثم توصيلها بشبكة TestLab الظاهرية باستخدام نظير VNet.
  
أولا، ابدأ موجه Azure PowerShell على الكمبيوتر المحلي.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell cmdlets](/powershell/azureps-cmdlets-docs/). 
  
سجل الدخول إلى حساب Azure باستخدام هذا الأمر.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام هذا الأمر.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

تعيين اشتراكك في Azure. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك \< and > الأحرف، بالأسماء الصحيحة.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

بعد ذلك، قم بإنشاء شبكة XPrem الظاهرية وحمايتها باستخدام مجموعة أمان الشبكة باستخدام هذه الأوامر.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

بعد ذلك، يمكنك إنشاء علاقة نظير VNet بين TestLab وXPrem VNet باستخدام هذه الأوامر.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

هذا هو التكوين الحالي. 
  
![المرحلة 2 من بيئة اختبار الشبكة الظاهرية المحلية المحاكاة، مع XPrem VNet وعلاقة النظير VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>المرحلة 3: تكوين DC2

في هذه المرحلة، يمكنك إنشاء الجهاز الظاهري DC2 في شبكة XPrem الظاهرية ثم تكوينه ك وحدة تحكم مجال متماثلة.
  
أولا، أنشئ جهازا ظاهريا ل DC2. تشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
```powershell
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

بعد ذلك، قم بالاتصال بالآلة الظاهرية DC2 الجديدة من [مدخل Azure](https://portal.azure.com) باستخدام اسم حساب المسؤول المحلي وكلمة المرور الخاصة به.
  
بعد ذلك، قم بتكوين قاعدة Windows جدار الحماية للسماح ب حركة المرور لاختبار الاتصال الأساسي. من موجه الأوامر على مستوى Windows PowerShell على DC2، تشغيل هذه الأوامر. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

يجب أن ينتج عن أمر ping أربعة ردود ناجحة من عنوان IP 10.0.0.4. هذا اختبار لحركة المرور عبر علاقة نظير VNet. 
  
بعد ذلك، أضف قرص البيانات الإضافية كحجم جديد باستخدام حرف محرك الأقراص F: باستخدام هذا الأمر من موجه الأوامر Windows PowerShell على DC2.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، قم بتكوين DC2 ك وحدة تحكم مجال متماثلة corp.contoso.com المجال. تشغيل هذه الأوامر من موجه الأوامر Windows PowerShell على DC2.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

تجدر الإشارة إلى أنه تتم مطالبتك بتزويد كل من كلمة مرور CORPUser1\\ وكلمة مرور وضع استعادة خدمات الدليل (DSRM) وإعادة تشغيل DC2. 
  
الآن وقد أصبح لشبكة XPrem الظاهرية خادم DNS الخاص بها (DC2)، يجب تكوين شبكة XPrem الظاهرية لاستخدام خادم DNS هذا. تشغيل هذه الأوامر من موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

من مدخل Azure على الكمبيوتر المحلي، اتصل ب DC1 باستخدام بيانات اعتماد CORPUser1\\. لتكوين مجال CORP بحيث تستخدم أجهزة الكمبيوتر والمستخدمون وحدة تحكم المجال المحلية الخاصة بهم للمصادقة، قم بتشغيل هذه الأوامر من موجه أوامر على مستوى Windows PowerShell على DC1.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

هذا هو التكوين الحالي. 
  
![المرحلة 3 من بيئة اختبار الشبكة الظاهرية المحلية المحاكاة، مع الجهاز الظاهري DC2 في XPrem VNet.](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
بيئة سحابة Azure المختلطة التي تم محاكاتها جاهزة الآن للاختبار.
  
أنت الآن جاهز لتجربة ميزات إضافية Microsoft 365 [للمؤسسات](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>الخطوات التالية

استكشف هذه المجموعات الإضافية من "أدلة اختبار المعمل":
  
- [الهوية](m365-enterprise-test-lab-guides.md#identity)
- [إدارة أجهزة المحمول](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [حماية المعلومات](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 دليل اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[Microsoft 365 نظرة عامة حول المؤسسة](microsoft-365-overview.md)

[Microsoft 365 وثائق المؤسسة](/microsoft-365-enterprise/)