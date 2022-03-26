---
title: المرحلة 3 من المصادقة المتحدة عالية التوفر تكوين خوادم AD FS
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
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: تعرف على كيفية إنشاء خوادم AD FS وتكوينها للمصادقة المتحدة عالية التوفر Microsoft 365 Microsoft Azure.
ms.openlocfilehash: c26fc68aa382ce93c62b6edbce4040b7e0813474
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570031"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a>المرحلة 3 من المصادقة المتحدة عالية التوفر: تكوين خوادم AD FS

في هذه المرحلة من نشر توفر عال للمصادقة Microsoft 365 المتحدة في خدمات البنية الأساسية في Azure، يمكنك إنشاء موازن تحميل داخلي وخادم AD FS.
  
يجب عليك إكمال هذه المرحلة قبل الانتقال إلى المرحلة [4: تكوين وواجبات تطبيقات الويب](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). راجع [نشر المصادقة](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) المتحدة عالية التوفر Microsoft 365 Azure لجميع المراحل.
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a>إنشاء الأجهزة الظاهرية خادم AD FS في Azure

استخدم الكتلة التالية من أوامر PowerShell لإنشاء الأجهزة الظاهرية للخادمين AD FS. تستخدم مجموعة أوامر PowerShell هذه القيم من الجداول التالية:
  
- الجدول M، للآلات الظاهرية
    
- الجدول R، لمجموعات الموارد
    
- الجدول الخامس، لإعدادات الشبكة الظاهرية
    
- الجدول S، بالنسبة إلى الشبكة الفرعية
    
- الجدول 1، بالنسبة إلى عناوين IP الثابتة
    
- الجدول A،  مجموعات التوفر الخاصة بك
    
تذكر أنك قمت بتعريف الجدول M في المرحلة [2:](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) تكوين وحدات تحكم المجال والجداول R وV وS وI و A في المرحلة [1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
أولا، يمكنك إنشاء موازن تحميل داخلي من Azure للخادمين AD FS. حدد القيم للمتغيرات، مع إزالة \< and > الأحرف. عند توفير كافة القيم الصحيحة، يمكنك تشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في POWERShell ISE.
  
> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم هذا Microsoft Excel [تكوين.](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) 

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

بعد ذلك، قم بإنشاء الأجهزة الظاهرية للخادم AD FS.
  
عند توفير كافة القيم الصحيحة، يمكنك تشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في POWERShell ISE.
  
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
> ونظرا لأن هذه الأجهزة الظاهرية خاصة بتطبيق إنترانت، لا يتم تعيين عنوان IP عام أو تسمية اسم مجال DNS ويتم عرضها على الإنترنت. ومع ذلك، فهذا يعني أيضا أنه لا يمكنك الاتصال بها من مدخل Azure. لا **الاتصال** خيار التحكم عند عرض خصائص الجهاز الظاهري. استخدم ملحق اتصال سطح المكتب البعيد أو أداة أخرى لسطح المكتب البعيد للاتصال بالآلة الظاهرية باستخدام عنوان IP الخاص به أو اسم إنترانت DNS.
  
لكل جهاز ظاهري، استخدم عميل سطح المكتب البعيد الذي تختاره وأنشئ اتصال سطح مكتب عن بعد. استخدم اسم إنترانت DNS أو الكمبيوتر وبيانات اعتماد حساب المسؤول المحلي.
  
لكل جهاز ظاهري، يمكنك ضمها إلى مجال خدمات مجال Active Directory (AD DS) المناسب باستخدام هذه الأوامر في Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

إليك التكوين الناتج عن إكمال هذه المرحلة بنجاح، مع أسماء أجهزة الكمبيوتر النائبة.
  
**المرحلة 3: خوادم AD FS وموازن التحميل الداخلي للبنية الأساسية للمصادقة المتحدة عالية التوفر في Azure**

![المرحلة 3 من التوفر العالي Microsoft 365 المصادقة الخارجية في Azure مع خوادم AD FS.](../media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدام [المرحلة 4: تكوين](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) تكاتف تطبيقات الويب لمواصلة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر المصادقة المتحدة عالية التوفر Microsoft 365 Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[الهوية المتحدة لبيئة Microsoft 365/اختبارك](federated-identity-for-your-microsoft-365-dev-test-environment.md)