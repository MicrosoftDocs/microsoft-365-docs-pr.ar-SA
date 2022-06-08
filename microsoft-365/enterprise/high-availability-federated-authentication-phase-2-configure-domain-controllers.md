---
title: مرحلة المصادقة الموحدة 2 عالية التوفر لتكوين وحدات التحكم بالمجال
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'ملخص: تكوين وحدات التحكم بالمجال وخادم مزامنة الدليل للمصادقة الموحدة عالية التوفر ل Microsoft 365 في Microsoft Azure.'
ms.openlocfilehash: 765ccb0aaf2611947f505b53b5689009dadd5148
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940679"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a>مرحلة المصادقة الموحدة ذات التوفر العالي 2: تكوين وحدات التحكم بالمجال

في هذه المرحلة من نشر قابلية وصول عالية للمصادقة الموحدة ل Microsoft 365 في خدمات البنية الأساسية ل Azure، يمكنك تكوين وحدتي تحكم بالمجال وخادم مزامنة الدليل في شبكة Azure الظاهرية. يمكن بعد ذلك مصادقة طلبات ويب العميل للمصادقة في شبكة Azure الظاهرية، بدلا من إرسال حركة مرور المصادقة عبر اتصال VPN من موقع إلى موقع إلى الشبكة المحلية.
  
> [!NOTE]
> لا يمكن ل Active Directory Federation Services (AD FS) استخدام Azure Active Directory (Azure AD) كبديل لوحدات تحكم مجال خدمات مجال Active Directory (AD DS). 
  
يجب إكمال هذه المرحلة قبل الانتقال إلى [المرحلة 3: تكوين خوادم AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). راجع [نشر المصادقة الموحدة عالية التوفر ل Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) لجميع المراحل.
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a>إنشاء الأجهزة الظاهرية لوحدة التحكم بالمجال في Azure

أولا، تحتاج إلى تعبئة عمود **اسم الجهاز الظاهري** للجدول M وتعديل أحجام الأجهزة الظاهرية حسب الحاجة في العمود **"الحد الأدنى للحجم** ".
  
|**البند**|**اسم الجهاز الظاهري**|**صورة المعرض**|**نوع التخزين**|**الحد الأدنى للحجم**|
|:-----|:-----|:-----|:-----|:-----|
|1.  <br/> |![خط.](../media/Common-Images/TableLine.png) (وحدة التحكم بالمجال الأولى، مثال DC1)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|2.  <br/> |![خط.](../media/Common-Images/TableLine.png) (وحدة التحكم بالمجال الثانية، مثال DC2)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|3.  <br/> |![خط.](../media/Common-Images/TableLine.png) (خادم مزامنة الدليل، مثال DS1)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|4.  <br/> |![خط.](../media/Common-Images/TableLine.png) (أول خادم AD FS، مثال ADFS1)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|5.  <br/> |![خط.](../media/Common-Images/TableLine.png) (خادم AD FS الثاني، مثال ADFS2)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|6.  <br/> |![خط.](../media/Common-Images/TableLine.png) (أول خادم وكيل تطبيق ويب، مثال WEB1)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
|7.  <br/> |![خط.](../media/Common-Images/TableLine.png) (خادم وكيل تطبيق الويب الثاني، مثال WEB2)  <br/> |مركز بيانات Windows Server 2016  <br/> |Standard_LRS  <br/> |Standard_D2  <br/> |
   
 **الجدول M - الأجهزة الظاهرية للمصادقة الموحدة عالية التوفر ل Microsoft 365 في Azure**
  
للحصول على القائمة الكاملة لأحجام الأجهزة الظاهرية، راجع ["الأحجام" للأجهزة الظاهرية](/azure/virtual-machines/sizes).
  
تنشئ كتلة أوامر Azure PowerShell التالية الأجهزة الظاهرية لوحدتي التحكم بالمجال. حدد قيم المتغيرات، مع إزالة الأحرف \< and > . لاحظ أن كتلة أوامر Azure PowerShell هذه تستخدم قيما من الجداول التالية:
  
- الجدول M، لأجهزتك الظاهرية
    
- الجدول R، لمجموعات الموارد الخاصة بك
    
- الجدول V، لإعدادات الشبكة الظاهرية
    
- الجدول S، للشبكات الفرعية الخاصة بك
    
- الجدول I، لعناوين IP الثابتة
    
- الجدول A، لمجموعات التوفر الخاصة بك
    
تذكر أنك حددت الجداول R وV وS وI و A في [المرحلة 1: تكوين Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية أحدث إصدار من Azure PowerShell. راجع [بدء استخدام Azure PowerShell](/powershell/azure/get-started-azureps). 
  
عند توفير جميع القيم الصحيحة، قم بتشغيل الكتلة الناتجة في موجه Azure PowerShell أو في بيئة البرنامج النصي المتكامل ل PowerShell (ISE) على الكمبيوتر المحلي.
  
> [!TIP]
> لإنشاء كتل أوامر PowerShell جاهزة للتشغيل استنادا إلى الإعدادات المخصصة، استخدم [مصنف تكوين Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx) هذا. 

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
> نظرا لأن هذه الأجهزة الظاهرية مخصصة لتطبيق إنترانت، فلا يتم تعيين عنوان IP عام لها أو تسمية اسم مجال DNS وعرضها على الإنترنت. ومع ذلك، هذا يعني أيضا أنه لا يمكنك الاتصال بها من مدخل Azure. لا يتوفر خيار **الاتصال** عند عرض خصائص الجهاز الظاهري. استخدم ملحق اتصال سطح المكتب البعيد أو أداة سطح المكتب البعيد الأخرى للاتصال بالجهاز الظاهري باستخدام عنوان IP الخاص به أو اسم DNS إنترانت.
  
## <a name="configure-the-first-domain-controller"></a>تكوين وحدة التحكم بالمجال الأولى

استخدم عميل سطح المكتب البعيد الذي تختاره وقم بإنشاء اتصال سطح مكتب بعيد بالجهاز الظاهري الأول لوحدة التحكم بالمجال. استخدم اسم الكمبيوتر أو DNS الخاص به على إنترانت وبيانات اعتماد حساب المسؤول المحلي.
  
بعد ذلك، أضف قرص البيانات الإضافي إلى وحدة التحكم بالمجال الأولى مع هذا الأمر من موجه أوامر Windows PowerShell **على الجهاز الظاهري لوحدة التحكم بالمجال الأول**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، اختبر اتصال وحدة التحكم بالمجال الأول بالمواقع على شبكة مؤسستك باستخدام أمر **ping** إلى أسماء ping وعناوين IP للموارد على شبكة مؤسستك.
  
يضمن هذا الإجراء أن تحليل اسم DNS يعمل بشكل صحيح (أن الجهاز الظاهري تم تكوينه بشكل صحيح مع خوادم DNS المحلية) وأنه يمكن إرسال الحزم من وإلى الشبكة الظاهرية الداخلية. إذا فشل هذا الاختبار الأساسي، فاتصل بقسم تكنولوجيا المعلومات لاستكشاف أخطاء تحليل اسم DNS ومشكلات تسليم حزم البيانات وإصلاحها.
  
بعد ذلك، من موجه الأوامر Windows PowerShell على وحدة التحكم بالمجال الأولى، قم بتشغيل الأوامر التالية:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

ستتم مطالبتك بتوفير بيانات اعتماد حساب مسؤول المجال. ستتم إعادة تشغيل الكمبيوتر.
  
## <a name="configure-the-second-domain-controller"></a>تكوين وحدة التحكم بالمجال الثانية

استخدم عميل سطح المكتب البعيد الذي تختاره وقم بإنشاء اتصال سطح مكتب بعيد بالجهاز الظاهري لوحدة التحكم بالمجال الثانية. استخدم اسم الكمبيوتر أو DNS الخاص به على إنترانت وبيانات اعتماد حساب المسؤول المحلي.
  
بعد ذلك، تحتاج إلى إضافة قرص البيانات الإضافي إلى وحدة التحكم بالمجال الثانية مع هذا الأمر من موجه أوامر Windows PowerShell **على الجهاز الظاهري لوحدة التحكم بالمجال الثانية**:
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، قم بتشغيل الأوامر التالية:
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

ستتم مطالبتك بتوفير بيانات اعتماد حساب مسؤول المجال. ستتم إعادة تشغيل الكمبيوتر.
  
بعد ذلك، تحتاج إلى تحديث خوادم DNS للشبكة الظاهرية بحيث يقوم Azure بتعيين الأجهزة الظاهرية لعناوين IP لوحدتي التحكم بالمجال الجديدتين لاستخدامها كخوادم DNS الخاصة بهم. املأ المتغيرات ثم قم بتشغيل هذه الأوامر من موجه أوامر Windows PowerShell على الكمبيوتر المحلي:
  
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

لاحظ أننا نقوم بإعادة تشغيل وحدتي التحكم بالمجال بحيث لا يتم تكوينهما مع خوادم DNS المحلية كخوادم DNS. نظرا لأنهما خادما DNS بحد ذاتهما، فقد تم تكوينهما تلقائيا مع خوادم DNS المحلية كمرسلي DNS عند ترقيتهم إلى وحدات التحكم بالمجال.
  
بعد ذلك، نحتاج إلى إنشاء موقع النسخ المتماثل ل Active Directory للتأكد من أن الخوادم في شبكة Azure الظاهرية تستخدم وحدات التحكم بالمجال المحلية. الاتصال بأي من وحدة التحكم بالمجال باستخدام حساب مسؤول المجال وتشغيل الأوامر التالية من موجه Windows PowerShell على مستوى المسؤول:
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a>تكوين خادم مزامنة الدليل

استخدم عميل سطح المكتب البعيد الذي تختاره وقم بإنشاء اتصال سطح مكتب بعيد بالجهاز الظاهري لخادم مزامنة الدليل. استخدم اسم الكمبيوتر أو DNS الخاص به على إنترانت وبيانات اعتماد حساب المسؤول المحلي.
  
بعد ذلك، قم بضمه إلى مجال AD DS المناسب باستخدام هذه الأوامر في موجه Windows PowerShell.
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

فيما يلي التكوين الناتج عن إكمال هذه المرحلة بنجاح، مع أسماء أجهزة الكمبيوتر النائبة.
  
**المرحلة 2: وحدات التحكم بالمجال وخادم مزامنة الدليل للبنية الأساسية للمصادقة الموحدة عالية التوفر في Azure**

![المرحلة 2 من البنية الأساسية للمصادقة الموحدة ل Microsoft 365 عالية التوفر في Azure مع وحدات التحكم بالمجال.](../media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a>الخطوة التالية

استخدم [المرحلة 3: تكوين خوادم AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) لمتابعة تكوين حمل العمل هذا.
  
## <a name="see-also"></a>انظر أيضاً

[نشر المصادقة الموحدة عالية التوفر ل Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[هوية موحدة لبيئة التطوير/الاختبار ل Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[مركز الحلول والهندسة من Microsoft 365](../solutions/index.yml)