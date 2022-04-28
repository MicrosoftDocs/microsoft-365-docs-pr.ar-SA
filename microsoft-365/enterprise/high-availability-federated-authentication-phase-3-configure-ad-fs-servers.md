---
title: مرحلة المصادقة الموحدة 3 عالية التوفر لتكوين خوادم AD FS
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: تعرف على كيفية إنشاء وتكوين خوادم AD FS للمصادقة الموحدة عالية التوفر الخاصة بك Microsoft 365 في Microsoft Azure.
ms.openlocfilehash: ed0974c8286a5bbad083152d2e2f9aeb01f659df
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101238"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>مرحلة المصادقة الموحدة 3 ذات قابلية وصول عالية: تكوين خوادم AD FS

في هذه المرحلة من نشر قابلية وصول عالية للمصادقة الموحدة Microsoft 365 في خدمات البنية الأساسية ل Azure، يمكنك إنشاء موازن تحميل داخلي وخادمين AD FS.
  
يجب إكمال هذه المرحلة قبل الانتقال إلى [المرحلة 4: تكوين وكلاء تطبيق الويب](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). راجع [نشر المصادقة الموحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) لجميع المراحل.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>إنشاء الأجهزة الظاهرية لخادم AD FS في Azure

استخدم الكتلة التالية من أوامر PowerShell لإنشاء الأجهزة الظاهرية لخادمين AD FS. تستخدم مجموعة أوامر PowerShell هذه قيما من الجداول التالية:
  
- الجدول M، لأجهزتك الظاهرية
    
- الجدول R، لمجموعات الموارد الخاصة بك
    
- الجدول V، لإعدادات الشبكة الظاهرية
    
- الجدول S، للشبكات الفرعية الخاصة بك
    
- الجدول I، لعناوين IP الثابتة
    
- الجدول A، لمجموعات التوفر الخاصة بك
    
تذكر أنك حددت الجدول M في [المرحلة 2: تكوين وحدات تحكم المجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) والجداول R وV وS وI و A في [المرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية أحدث إصدار من Azure PowerShell. راجع [بدء استخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
أولا، يمكنك إنشاء موازن تحميل داخلي ل Azure لخادمين AD FS. حدد قيم المتغيرات، مع إزالة الأحرف \< and > . عند توفير جميع القيم المناسبة، قم بتشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في PowerShell ISE.
  
> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم [مصنف التكوين Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) هذا. 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

بعد ذلك، قم بإنشاء الأجهزة الظاهرية لخادم AD FS.
  
عند توفير جميع القيم المناسبة، قم بتشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في PowerShell ISE.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> نظرا لأن هذه الأجهزة الظاهرية مخصصة لتطبيق إنترانت، فلا يتم تعيين عنوان IP عام لها أو تسمية اسم مجال DNS وعرضها على الإنترنت. ومع ذلك، هذا يعني أيضا أنه لا يمكنك الاتصال بها من مدخل Azure. لا يتوفر خيار **الاتصال** عند عرض خصائص الجهاز الظاهري. استخدم ملحق اتصال سطح المكتب البعيد أو أداة سطح المكتب البعيد الأخرى للاتصال بالجهاز الظاهري باستخدام عنوان IP الخاص به أو اسم DNS إنترانت.
  
لكل جهاز ظاهري، استخدم عميل سطح المكتب البعيد الذي تختاره وقم بإنشاء اتصال سطح مكتب بعيد. استخدم اسم الكمبيوتر أو DNS الخاص به على إنترانت وبيانات اعتماد حساب المسؤول المحلي.
  
لكل جهاز ظاهري، قم بضمها إلى مجال خدمات مجال Active Directory المناسب (AD DS) باستخدام هذه الأوامر في موجه Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

فيما يلي التكوين الناتج عن إكمال هذه المرحلة بنجاح، مع أسماء أجهزة الكمبيوتر النائبة.
  
**المرحلة 3: خوادم AD FS وموازن التحميل الداخلي للبنية الأساسية للمصادقة الموحدة عالية التوفر في Azure**

![المرحلة 3 من قابلية الوصول العالية Microsoft 365 البنية الأساسية للمصادقة الموحدة في Azure مع خوادم AD FS.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدم [المرحلة 4: تكوين وكلاء تطبيق الويب](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) لمتابعة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر مصادقة موحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[هوية موحدة لبيئة التطوير/الاختبار Microsoft 365 الخاصة بك](federated-identity-for-your-microsoft-365-dev-test-environment.md)