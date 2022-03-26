---
title: المرحلة 2 من المصادقة المتحدة عالية التوفر تكوين وحدات التحكم بالمجال
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'ملخص: تكوين وحدات التحكم بالمجال وخادم مزامنة الدليل للمصادقة المتحدة عالية التوفر Microsoft 365 Microsoft Azure.'
ms.openlocfilehash: 82199d6782e9c2497214d501da9e27ac0956edcd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63572858"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>المرحلة 2 من المصادقة المتحدة عالية التوفر: تكوين وحدات تحكم المجال

في هذه المرحلة من نشر توفر عال لمصادقة Microsoft 365 المتحدة في خدمات البنية الأساسية ل Azure، يمكنك تكوين جهازي تحكم مجال وخادم مزامنة الدليل في شبكة Azure الظاهرية. يمكن بعد ذلك المصادقة على طلبات العميل على الويب للمصادقة في شبكة Azure الظاهرية، بدلا من إرسال حركة مرور المصادقة عبر اتصال VPN من موقع إلى موقع بالشبكة المحلية.
  
> [!NOTE]
> يتعذر على خدمات Active Directory Federation Services (AD FS) استخدام Azure Active Directory (Azure AD) كبديل لتحكمات مجال خدمات مجال Active Directory (AD DS). 
  
يجب إكمال هذه المرحلة قبل الانتقال إلى المرحلة [3: تكوين خوادم AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). راجع [نشر المصادقة](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) المتحدة عالية التوفر Microsoft 365 Azure لجميع المراحل.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>إنشاء أجهزة ظاهرية وحدة التحكم بالمجال في Azure

أولا، تحتاج إلى تعبئة العمود اسم الجهاز  الافتراضي في الجدول M وتعديل أحجام الأجهزة الظاهرية كما هو مطلوب في العمود **الحد الأدنى للحجم**.
  
|**عنصر**|**اسم الجهاز الظاهري**|**صورة المعرض**|**نوع التخزين**|**الحد الأدنى للحجم**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (وحدة تحكم المجال الأولى، مثال DC1)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (وحدة تحكم المجال الثانية، مثال DC2)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (خادم مزامنة الدليل، مثال DS1)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (أول خادم AD FS، مثال ADFS1)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (خادم AD FS الثاني، مثال ADFS2)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (أول خادم وكيل لتطبيق ويب، مثال WEB1)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![السطر.](../media/Common-Images/TableLine.png) (الخادم الوكيل الثاني لتطبيق ويب، مثال WEB2)  <br/> |Windows Datacenter ل Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **الجدول M - الأجهزة الظاهرية للمصادقة المتحدة عالية التوفر Microsoft 365 Azure**
  
للحصول على القائمة الكاملة لأحجام الأجهزة الظاهرية، راجع [أحجام الأجهزة الظاهرية](/azure/virtual-machines/virtual-machines-windows-sizes).
  
تنشئ كتلة أوامر Azure PowerShell التالية الأجهزة الظاهرية لتحكم المجالين. حدد القيم للمتغيرات، مع إزالة \< and > الأحرف. تجدر الإشارة إلى أن كتلة أوامر Azure PowerShell هذه تستخدم قيما من الجداول التالية:
  
- الجدول M، للآلات الظاهرية
    
- الجدول R، لمجموعات الموارد
    
- الجدول الخامس، لإعدادات الشبكة الظاهرية
    
- الجدول S، بالنسبة إلى الشبكة الفرعية
    
- الجدول 1، بالنسبة إلى عناوين IP الثابتة
    
- الجدول A،  مجموعات التوفر الخاصة بك
    
تذكر أنك قمت بتعريف الجداول R وV و S و I و A في المرحلة [1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
عند توفير كافة القيم الصحيحة، يمكنك تشغيل الكتلة الناتجة في موجه Azure PowerShell أو في بيئة البرامج النصية المتكاملة (ISE) في PowerShell على الكمبيوتر المحلي.
  
> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم هذا Microsoft Excel [تكوين.](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> ونظرا لأن هذه الأجهزة الظاهرية خاصة بتطبيق إنترانت، لا يتم تعيين عنوان IP عام أو تسمية اسم مجال DNS ويتم عرضها على الإنترنت. ومع ذلك، فهذا يعني أيضا أنه لا يمكنك الاتصال بها من مدخل Azure. لا **الاتصال** خيار التحكم عند عرض خصائص الجهاز الظاهري. استخدم ملحق اتصال سطح المكتب البعيد أو أداة أخرى لسطح المكتب البعيد للاتصال بالآلة الظاهرية باستخدام عنوان IP الخاص به أو اسم إنترانت DNS.
  
## <a name="configure-the-first-domain-controller"></a>تكوين وحدة تحكم المجال الأولى

استخدم عميل سطح المكتب البعيد الذي تختاره وأنشئ اتصال سطح المكتب البعيد بجهاز ظاهري أول وحدة تحكم مجال. استخدم اسم إنترانت DNS أو الكمبيوتر وبيانات اعتماد حساب المسؤول المحلي.
  
بعد ذلك، أضف قرص البيانات الإضافي إلى وحدة التحكم بالمجال الأولى باستخدام هذا الأمر من موجه أوامر Windows PowerShell على الجهاز الظاهري الأول وحدة تحكم **المجال**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، اختبر اتصال وحدة التحكم بالمجال الأولى بالمواقع على شبكة المؤسسة باستخدام أمر الاتصال لأسماء الاتصال  وعناوين IP للموارد على شبكة المؤسسة.
  
يضمن هذا الإجراء أن دقة اسم DNS تعمل بشكل صحيح (تكوين الجهاز الظاهري بشكل صحيح مع خوادم DNS المحلية) وأن الحزم يمكن إرسالها إلى الشبكة الظاهرية المحلية وإليها. إذا فشل هذا الاختبار الأساسي، فاتصل بقسم المعلومات لديك لا استكشاف مشاكل تسليم الحزم واسم DNS وإصلاحها.
  
بعد ذلك، Windows PowerShell موجه الأوامر على وحدة التحكم بالمجال الأولى، تشغيل الأوامر التالية:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

وستطلب منك توفير بيانات اعتماد حساب مسؤول المجال. سيتم إعادة تشغيل الكمبيوتر.
  
## <a name="configure-the-second-domain-controller"></a>تكوين وحدة تحكم المجال الثانية

استخدم عميل سطح المكتب البعيد الذي تختاره وأنشئ اتصال سطح المكتب البعيد بجهاز ظاهري ثان لتحكم المجال. استخدم اسم إنترانت DNS أو الكمبيوتر وبيانات اعتماد حساب المسؤول المحلي.
  
بعد ذلك، ستحتاج إلى إضافة قرص البيانات الإضافية إلى وحدة التحكم بالمجال الثاني باستخدام هذا الأمر من موجه أوامر Windows PowerShell على الجهاز الظاهري **الثاني** وحدة تحكم المجال:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، تشغيل الأوامر التالية:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

وستطلب منك توفير بيانات اعتماد حساب مسؤول المجال. سيتم إعادة تشغيل الكمبيوتر.
  
بعد ذلك، ستحتاج إلى تحديث خوادم DNS للشبكة الظاهرية بحيث يعين Azure عناوين IP الخاصة بجهازي التحكم بالمجال الجديدين لاستخدامها كخادمات DNS. قم بتعبئة المتغيرات ثم قم بتشغيل هذه الأوامر من موجه أوامر Windows PowerShell على الكمبيوتر المحلي:
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

تجدر الإشارة إلى أننا نقوم بإعادة تشغيل جهازي تحكم المجال بحيث لا يتم تكوينها مع خوادم DNS في الموقع كخادمات DNS. ونظرا لأنهما خادما DNS نفسيهما، فقد تم تكوينهما تلقائيا باستخدام خوادم DNS في الموقع كمرسلات DNS عند ترقيةهما إلى وحدات تحكم المجال.
  
بعد ذلك، نحتاج إلى إنشاء موقع النسخ المتماثل ل Active Directory للتأكد من أن الخوادم في شبكة Azure الظاهرية تستخدم وحدات التحكم بالمجالات المحلية. الاتصال إلى وحدة تحكم المجال باستخدام حساب مسؤول المجال وتشغيل الأوامر التالية من موجه على مستوى Windows PowerShell:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>تكوين خادم مزامنة الدليل

استخدم عميل سطح المكتب البعيد الذي تختاره وأنشئ اتصال سطح المكتب البعيد بالآلة الظاهرية لمزامنة الدليل. استخدم اسم إنترانت DNS أو الكمبيوتر وبيانات اعتماد حساب المسؤول المحلي.
  
بعد ذلك، يمكنك ضمه إلى مجال AD DS المناسب باستخدام هذه الأوامر في Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

إليك التكوين الناتج عن إكمال هذه المرحلة بنجاح، مع أسماء أجهزة الكمبيوتر النائبة.
  
**المرحلة 2: وحدات التحكم بالمجال وخادم مزامنة الدليل للبنية الأساسية للمصادقة المتحدة عالية التوفر في Azure**

![المرحلة 2 من التوفر العالي Microsoft 365 المصادقة الخارجية في Azure مع وحدات التحكم بالمجال.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدام [المرحلة 3: تكوين خوادم AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) لمواصلة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر المصادقة المتحدة عالية التوفر Microsoft 365 Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[الهوية المتحدة لبيئة Microsoft 365/اختبارك](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Microsoft 365 حل وهندسة](../solutions/index.yml)