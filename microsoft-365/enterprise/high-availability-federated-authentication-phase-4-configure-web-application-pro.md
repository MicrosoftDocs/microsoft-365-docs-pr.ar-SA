---
title: التوفر العالي للمصادقة الخارجية المرحلة 4 تكوين مصادقة محترفي تطبيقات الويب
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'ملخص: قم بتكوين خوادم وكيل تطبيق ويب للمصادقة الخارجية عالية التوفر Microsoft 365 Microsoft Azure.'
ms.openlocfilehash: ea50a48fe4bebd997ecf6b472a60e57772bf2b0f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63570008"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>المرحلة 4 من المصادقة المتحدة ذات التوفر العالي: تكوين محترفي تطبيقات الويب

في هذه المرحلة من نشر توفر عال للمصادقة Microsoft 365 المتحدة في خدمات البنية الأساسية في Azure، يمكنك إنشاء موازن تحميل داخلي وخادم AD FS.
  
يجب إكمال هذه المرحلة قبل الانتقال إلى المرحلة [5:](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) تكوين المصادقة الخارجية Microsoft 365. راجع [نشر المصادقة](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) المتحدة عالية التوفر Microsoft 365 Azure لجميع المراحل.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>إنشاء موازن التحميل المواجه للإنترنت في Azure

يجب إنشاء موازن تحميل يواجه الإنترنت بحيث يوزع Azure حركة مرور مصادقة العميل الواردة من الإنترنت بالتساوي بين الخادمين الوكيلين لتطبيق ويب.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
عند توفير قيم مجموعة الموارد والموقع، يمكنك تشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في POWERShell ISE.
  
> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم هذا Microsoft Excel [تكوين.](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) 

```powershell
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

لعرض عنوان IP العام المعين إلى موازن التحميل المواجه للإنترنت، قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>تحديد FQDN لخدمة الاتحاد وإنشاء سجلات DNS

يجب تحديد اسم DNS لتحديد اسم خدمة الاتحاد على الإنترنت. سيتم الاتصال Azure AD Microsoft 365 باستخدام هذا الاسم في المرحلة 5، والذي سيصبح جزءا من عنوان URL الذي يرسله Microsoft 365 إلى توصيل العملاء للحصول على رمز أمان مميز. مثال على ذلك fs.contoso.com (fs تعني خدمة الاتحاد).
  
بمجرد أن يكون لديك FDQN لخدمة الاتحاد، قم بإنشاء مجال DNS عام سجل ل FDQN لخدمة الاتحاد يتم حله إلى عنوان IP العام لموازن التحميل المواجه للإنترنت في Azure.
  
|**الاسم**|**النوع**|**TTL**|**القيمة**|
|:-----|:-----|:-----|:-----|
|FDQN لخدمة الاتحاد  <br/> |A  <br/> |3600  <br/> |عنوان IP العام لموازن التحميل المواجه للإنترنت في Azure (المعروض بواسطة الأمر **"مضيف الكتابة** " في المقطع السابق) <br/> |
   
فيما يلي مثال على ذلك:
  
|**الاسم**|**النوع**|**TTL**|**القيمة**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
بعد ذلك، أضف سجل عنوان DNS إلى مساحة اسم DNS الخاصة في مؤسستك التي تحل FQDN لخدمة الاتحاد إلى عنوان IP الخاص المعين إلى موازن التحميل الداخلي للخوادم AD FS (الجدول I، العنصر 4، عمود القيمة).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>إنشاء الأجهزة الظاهرية للخادم الوكيل لتطبيق ويب في Azure

استخدم الكتلة التالية من أوامر Azure PowerShell لإنشاء الأجهزة الظاهرية للخادمين الوكيلين لتطبيق ويب. 
  
لاحظ أن مجموعات أوامر Azure PowerShell التالية تستخدم قيما من الجداول التالية:
  
- الجدول M، للآلات الظاهرية
    
- الجدول R، لمجموعات الموارد
    
- الجدول الخامس، لإعدادات الشبكة الظاهرية
    
- الجدول S، بالنسبة إلى الشبكة الفرعية
    
- الجدول 1، بالنسبة إلى عناوين IP الثابتة
    
- الجدول A،  مجموعات التوفر الخاصة بك
    
تذكر أنك قمت بتعريف الجدول M في المرحلة [2:](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) تكوين وحدات تحكم المجال والجداول R وV وS وI و A في المرحلة [1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
عند توفير كافة القيم الصحيحة، يمكنك تشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في POWERShell ISE.
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> ونظرا لأن هذه الأجهزة الظاهرية خاصة بتطبيق إنترانت، لا يتم تعيين عنوان IP عام أو تسمية اسم مجال DNS ويتم عرضها على الإنترنت. ومع ذلك، فهذا يعني أيضا أنه لا يمكنك الاتصال بها من مدخل Azure. لا **الاتصال** خيار التحكم عند عرض خصائص الجهاز الظاهري. استخدم ملحق اتصال سطح المكتب البعيد أو أداة أخرى لسطح المكتب البعيد للاتصال بالآلة الظاهرية باستخدام عنوان IP الخاص به أو اسم إنترانت DNS وبيانات اعتماد حساب المسؤول المحلي.
  
إليك التكوين الناتج عن إكمال هذه المرحلة بنجاح، مع أسماء أجهزة الكمبيوتر النائبة.
  
**المرحلة 4: موازن التحميل المواجه للإنترنت وخادم وكيل تطبيق ويب للبنية الأساسية للمصادقة المتحدة عالية التوفر في Azure**

![المرحلة 4 من التوفر العالي Microsoft 365 المصادقة الخارجية في Azure مع خوادم وكيل تطبيق الويب.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدام [المرحلة 5: تكوين مصادقة Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) لمواصلة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر المصادقة المتحدة عالية التوفر Microsoft 365 Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[الهوية المتحدة لبيئة Microsoft 365/اختبارك](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 حل وهندسة](../solutions/index.yml)