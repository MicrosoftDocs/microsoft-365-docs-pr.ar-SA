---
title: مرحلة المصادقة الموحدة ذات قابلية الوصول العالية 4 لتكوين وكلاء تطبيق الويب
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'ملخص: تكوين خوادم وكيل تطبيق الويب للمصادقة الموحدة عالية التوفر الخاصة بك Microsoft 365 في Microsoft Azure.'
ms.openlocfilehash: 2200d4f7c0aafbaff11dd5d9b5b5b414fae06b5f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091270"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>مرحلة المصادقة الموحدة 4 عالية التوفر: تكوين وكلاء تطبيق الويب

في هذه المرحلة من نشر قابلية وصول عالية للمصادقة الموحدة Microsoft 365 في خدمات البنية الأساسية ل Azure، يمكنك إنشاء موازن تحميل داخلي وخادمين AD FS.
  
يجب إكمال هذه المرحلة قبل الانتقال إلى [المرحلة 5: تكوين المصادقة الموحدة Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). راجع [نشر المصادقة الموحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) لجميع المراحل.
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>إنشاء موازنة التحميل التي تواجه الإنترنت في Azure

يجب إنشاء موازن تحميل يواجه الإنترنت بحيث يوزع Azure حركة مرور مصادقة العميل الواردة من الإنترنت بالتساوي بين خادمي وكيل تطبيق الويب.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية أحدث إصدار من Azure PowerShell. راجع [بدء استخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
عند توفير قيم الموقع ومجموعة الموارد، قم بتشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في PowerShell ISE.
  
> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم [مصنف التكوين Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) هذا. 

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

لعرض عنوان IP العام المعين إلى موازن التحميل الذي يواجه الإنترنت، قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي:
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>تحديد FQDN لخدمة الاتحاد وإنشاء سجلات DNS

تحتاج إلى تحديد اسم DNS لتحديد اسم خدمة الاتحاد على الإنترنت. سيقوم azure AD الاتصال بتكوين Microsoft 365 بهذا الاسم في المرحلة 5، والتي ستصبح جزءا من عنوان URL الذي Microsoft 365 إرساله إلى العملاء المتصلين للحصول على رمز أمان مميز. مثال على ذلك هو fs.contoso.com (fs يرمز إلى خدمة الاتحاد).
  
بمجرد أن يكون لديك FDQN لخدمة الاتحاد الخاصة بك، قم بإنشاء سجل مجال DNS عام A ل FDQN لخدمة الاتحاد الذي يحل إلى عنوان IP العام لموازن التحميل الذي يواجه Azure عبر الإنترنت.
  
|**الاسم**|**نوع**|**TTL**|**قيمه**|
|:-----|:-----|:-----|:-----|
|FDQN لخدمة الاتحاد  <br/> |A  <br/> |3600  <br/> |عنوان IP العام لموازن التحميل الذي يواجه Azure عبر الإنترنت (يتم عرضه بواسطة الأمر **Write-Host** في القسم السابق) <br/> |
   
فيما يلي مثال على ذلك:
  
|**الاسم**|**نوع**|**TTL**|**قيمه**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
بعد ذلك، أضف سجل عنوان DNS إلى مساحة اسم DNS الخاصة بالمؤسسة التي تقوم بحل FQDN لخدمة الاتحاد إلى عنوان IP الخاص المعين إلى موازن التحميل الداخلي لخوادم AD FS (الجدول I، العنصر 4، عمود القيمة).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>إنشاء الأجهزة الظاهرية لخادم وكيل تطبيق الويب في Azure

استخدم الكتلة التالية من أوامر Azure PowerShell لإنشاء الأجهزة الظاهرية لخادمين وكيل تطبيق الويب. 
  
لاحظ أن مجموعات أوامر Azure PowerShell التالية تستخدم قيما من الجداول التالية:
  
- الجدول M، لأجهزتك الظاهرية
    
- الجدول R، لمجموعات الموارد الخاصة بك
    
- الجدول V، لإعدادات الشبكة الظاهرية
    
- الجدول S، للشبكات الفرعية الخاصة بك
    
- الجدول I، لعناوين IP الثابتة
    
- الجدول A، لمجموعات التوفر الخاصة بك
    
تذكر أنك حددت الجدول M في [المرحلة 2: تكوين وحدات تحكم المجال](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) والجداول R وV وS وI و A في [المرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
عند توفير جميع القيم المناسبة، قم بتشغيل الكتلة الناتجة في موجه أوامر Azure PowerShell أو في PowerShell ISE.
  
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
> نظرا لأن هذه الأجهزة الظاهرية مخصصة لتطبيق إنترانت، فلا يتم تعيين عنوان IP عام لها أو تسمية اسم مجال DNS وعرضها على الإنترنت. ومع ذلك، هذا يعني أيضا أنه لا يمكنك الاتصال بها من مدخل Azure. لا يتوفر خيار **الاتصال** عند عرض خصائص الجهاز الظاهري. استخدم ملحق اتصال سطح المكتب البعيد أو أداة سطح المكتب البعيد الأخرى للاتصال بالجهاز الظاهري باستخدام عنوان IP الخاص به أو اسم DNS إنترانت وبيانات اعتماد حساب المسؤول المحلي.
  
فيما يلي التكوين الناتج عن إكمال هذه المرحلة بنجاح، مع أسماء أجهزة الكمبيوتر النائبة.
  
**المرحلة 4: موازن التحميل المواجه للإنترنت وخوادم وكيل تطبيق الويب للبنية الأساسية للمصادقة الموحدة عالية التوفر في Azure**

![المرحلة 4 من قابلية الوصول العالية Microsoft 365 البنية الأساسية للمصادقة الموحدة في Azure مع خوادم وكيل تطبيق الويب.](../media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدم [المرحلة 5: تكوين المصادقة الموحدة Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) لمتابعة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر مصادقة موحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[هوية موحدة لبيئة التطوير/الاختبار Microsoft 365 الخاصة بك](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[مركز الحلول والهندسة من Microsoft 365](../solutions/index.yml)