---
title: تكوين قاعدة مؤسسة محاكاة Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: استخدم دليل Test Lab هذا لإنشاء بيئة اختبار مؤسسة محاكاة Microsoft 365 للمؤسسة.
ms.openlocfilehash: d335ed074adc6abe8bc1dabf58392d5b9051ccc6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63567102"
---
# <a name="the-simulated-enterprise-base-configuration"></a>تكوين قاعدة المؤسسة الذي تم محاكاته

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

تصف هذه المقالة كيفية إنشاء بيئة مبسطة Microsoft 365 للمؤسسات تتضمن:

- اشتراك Microsoft 365 E5 تجريبي أو مدفوع.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من ثلاثة أجهزة ظاهرية على شبكة Azure الظاهرية (DC1 و APP1 و CLIENT1).
 
![تكوين قاعدة المؤسسة الذي تم محاكاته.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

يتضمن إنشاء بيئة اختبار مبسطة مرحلتين:
- [المرحلة 1: إنشاء إنترانت محاكاة](#phase-1-create-a-simulated-intranet)
- [المرحلة 2: إنشاء اشتراك Microsoft 365 E5 اشتراكك](#phase-2-create-your-microsoft-365-e5-subscription)

يمكنك استخدام البيئة الناتجة لاختبار ميزات وظائف Microsoft 365 للمؤسسة باستخدام "أدلة اختبار [معمل](m365-enterprise-test-lab-guides.md) الاختبار" إضافية أو بنفسك.[](https://www.microsoft.com/microsoft-365/enterprise)

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، انتقل إلى Microsoft 365 [دليل اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-create-a-simulated-intranet"></a>المرحلة 1: إنشاء إنترانت محاكاة

في هذه المرحلة، يمكنك إنشاء إنترانت محاكاة في خدمات البنية الأساسية ل Azure تتضمن وحدة تحكم مجال خدمات مجال Active Directory (AD DS) وخادم تطبيق وحاسب عميل.

سوف تستخدم أجهزة الكمبيوتر هذه في Microsoft 365 إضافية [ل "أدلة](m365-enterprise-test-lab-guides.md) اختبار المعمل" للمؤسسات لتكوين الهوية المختلطة والإمكانات الأخرى وشرحها.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>الطريقة 1: إنشاء إنترانت محاكاة باستخدام قالب Azure Resource Manager

في هذا الأسلوب، يمكنك استخدام قالب Azure Resource Manager لإنشاء إنترانت المحاكاة. تحتوي قوالب Azure Resource Manager على كل الإرشادات لإنشاء البنية الأساسية للشبكات في Azure، و الأجهزة الظاهرية، وتكوينها.

قبل نشر القالب، اقرأ صفحة [القالب README](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) واستعد المعلومات التالية:

- اسم مجال DNS العام لبيئة الاختبار (testlab.\<*your public domain*>). ستدخل هذا الاسم في الحقل **اسم المجال** في **صفحة النشر** المخصص.
- بادرة تسمية DNS ل عناوين URL الخاصة عناوين IP العامة في الأجهزة الظاهرية. ستحتاج إلى إدخال هذه التسمية في الحقل **"بادرة تسمية Dns** " في **صفحة النشر** المخصص.

بعد قراءة الإرشادات، حدد **نشر إلى Azure** على [صفحة القالب README](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) للبدء.

>[!Note]
>تتطلب إنترانت المحاكاة التي تم إنشاؤها بواسطة قالب Azure Resource Manager اشتراك Azure مدفوع.

بعد اكتمال القالب، يبدو التكوين كما يلي:

![إنترانت المحاكاة في خدمات البنية الأساسية ل Azure.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>الطريقة 2: إنشاء إنترانت محاكاة باستخدام Azure PowerShell

في هذا الأسلوب، Windows PowerShell وحدة Azure PowerShell النمطية لإنشاء البنية الأساسية للشبكة، و الأجهزة الظاهرية، وتكوينها.

استخدم هذا الأسلوب إذا كنت تريد الحصول على تجربة إنشاء عناصر البنية الأساسية ل Azure خطوة واحدة في كل مرة باستخدام PowerShell. يمكنك بعد ذلك تخصيص كتل أوامر PowerShell لنشرك الخاص لألآلات الظاهرية الأخرى في Azure.

#### <a name="step-1-create-dc1"></a>الخطوة 1: إنشاء DC1

في هذه الخطوة، يمكنك إنشاء شبكة Azure ظاهرية وإضافة DC1، وهو جهاز ظاهري هو وحدة تحكم مجال لمجال AD DS.

أولا، ابدأ Windows PowerShell موجه الأوامر على الكمبيوتر المحلي.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell cmdlets](/powershell/azureps-cmdlets-docs/). 
  
سجل الدخول إلى حساب Azure باستخدام الأمر التالي.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام الأمر التالي.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

تعيين اشتراكك في Azure. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك أقواس الزاوية ("<" و">")، بالاسم الصحيح.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

بعد ذلك، أنشئ مجموعة موارد جديدة لمختبر اختبار المؤسسة الذي تم محاكاته. لتحديد اسم مجموعة موارد فريدة، استخدم هذا الأمر لتضمين مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

أنشئ مجموعة الموارد الجديدة باستخدام هذه الأوامر. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك أقواس الزاوية، بالأسماء الصحيحة.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، قم بإنشاء شبكة TestLab الظاهرية التي ستستضيف الشبكة الفرعية لشبكة الشركة لبيئة المؤسسة التي تم محاكاتها وحمايتها باستخدام مجموعة أمان الشبكة. قم بتعبئة اسم مجموعة الموارد وتشغيل هذه الأوامر في موجه الأوامر PowerShell على الكمبيوتر المحلي.
  
```powershell
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

بعد ذلك، يمكنك إنشاء الجهاز الظاهري DC1 وتكوينه ك وحدة تحكم مجال **للوح الاختبار.**\<your public domain> مجال AD DS وخادم DNS للآلات الظاهرية لشبكة TestLab الظاهرية. على سبيل المثال، إذا كان اسم مجالك العام **<span>contoso.com</span>**، سيكون الجهاز الظاهري DC1 وحدة تحكم مجال **<span>للمجال testlab.contoso.com</span>**.
  
لإنشاء جهاز Azure ظاهري ل DC1، قم بتعبئة اسم مجموعة الموارد وتشغيل هذه الأوامر في موجه الأوامر PowerShell على الكمبيوتر المحلي.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

سيتم مطالبتك باسم المستخدم وكلمة المرور لحساب المسؤول المحلي على DC1. استخدم كلمة مرور قوية وسجل الاسم وكلمة المرور في موقع آمن.
  
بعد ذلك، اتصل بالآلة الظاهرية DC1:
  
1. في مدخل [Azure](https://portal.azure.com)، حدد **مجموعات** الموارد > <اسم مجموعة الموارد ***الجديدة_*> > _DC1** >  **الاتصال**.
    
2. في الجزء المفتوح، حدد **تنزيل ملف RDP**. افتح ملف DC1.rdp الذي يتم تنزيله، **ثم حدد الاتصال**.
    
3. حدد اسم حساب المسؤول المحلي ل DC1:
    
   - بالنسبة Windows 7:
    
     في مربع **أمن Windows**، حدد **استخدام حساب آخر**. في **اسم المستخدم،** أدخل **اسم حساب مسؤول DC1local\\**< *>*.
    
   - بالنسبة Windows 8 أو Windows 10:
    
     في مربع **أمن Windows**، حدد **المزيد من** الخيارات، ثم حدد **استخدام حساب مختلف**. في **اسم المستخدم،** أدخل **اسم حساب مسؤول DC1local\\**< *>*.
    
4. في **كلمة** المرور، أدخل كلمة مرور حساب المسؤول المحلي، ثم حدد **موافق**.
    
5. عند المطالبة، حدد **نعم**.
    
بعد ذلك، أضف قرص بيانات إضافي كحجم جديد باستخدام حرف محرك الأقراص F: باستخدام هذا الأمر على موجه الأوامر على مستوى Windows PowerShell على DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، قم بتكوين DC1 ك وحدة تحكم مجال وخادم DNS **للمختبر.**\<*your public domain*> المجال. حدد اسم المجال العام، وأزل أقواس الزاوية، ثم قم بتشغيل هذه الأوامر على مستوى المسؤول Windows PowerShell موجه الأوامر على DC1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
ستحتاج إلى تحديد كلمة مرور مسؤول الوضع الآمن. تخزين كلمة المرور هذه في موقع آمن.
  
لاحظ أن هذه الأوامر قد تستغرق بضع دقائق لإكمالها.
  
بعد إعادة تشغيل DC1، أعد الاتصال بالآلة الظاهرية DC1.
  
1. في مدخل [Azure](https://portal.azure.com)، حدد **مجموعات** الموارد > <*اسم* مجموعة الموارد> > **DC1** >  **الاتصال**.
    
2. قم بتشغيل ملف DC1.rdp الذي يتم تنزيله، **ثم حدد الاتصال**.
    
3. في **أمن Windows**، حدد **استخدام حساب آخر**. في **اسم المستخدم،** أدخل **اسم حساب مسؤول TESTLABlocal\\**< *>*.
    
4. في المربع **كلمة** المرور، أدخل كلمة مرور حساب المسؤول المحلي، ثم حدد **موافق**.
    
5. عند المطالبة، حدد **نعم**.
    
بعد ذلك، أنشئ حساب مستخدم في Active Directory سيتم استخدامه عند تسجيل الدخول إلى أجهزة كمبيوتر أعضاء مجال TESTLAB. تشغيل هذا الأمر على موجه أوامر Windows PowerShell المسؤول.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

تجدر الإشارة إلى أن هذا الأمر يطالبك بتزويدك بكلمة مرور حساب User1. سيتم استخدام هذا الحساب لاتصالات سطح المكتب البعيد لكل أجهزة الكمبيوتر الأعضاء في مجال TESTLAB، لذا اختر كلمة مرور قوية. سجل كلمة مرور حساب User1 واخزنها في موقع آمن.
  
بعد ذلك، قم بتكوين حساب User1 الجديد كمجال ومؤسسة ومسؤول مخطط. تشغيل هذا الأمر في موجه الأوامر على مستوى Windows PowerShell المسؤول.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

أغلق جلسة عمل سطح المكتب البعيد باستخدام DC1 ثم أعد الاتصال باستخدام حساب TESTLABUser1\\.
  
بعد ذلك، للسماح بازدحام البيانات لأداة Ping، ادير هذا الأمر على مستوى المسؤول Windows PowerShell موجه الأوامر.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

يبدو التكوين الحالي كما يلي:
  
![الخطوة 1 من تكوين قاعدة المؤسسة الذي تم محاكاته.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>الخطوة 2: تكوين APP1

في هذه الخطوة، يمكنك إنشاء APP1 وتكوينه، وهو خادم تطبيق يوفر في البداية خدمات مشاركة الملفات والويب.

لإنشاء جهاز Azure الظاهري ل APP1، قم بتعبئة اسم مجموعة الموارد وتشغيل هذه الأوامر في موجه الأوامر على الكمبيوتر المحلي.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

بعد ذلك، اتصل بالآلة الظاهرية APP1 باستخدام اسم حساب المسؤول المحلي وكلمة المرور ل APP1، ثم افتح Windows PowerShell موجه الأوامر.
  
للتحقق من دقة الاسم واتصال الشبكة بين APP1 و DC1، قم **بتشغيل ping dc1.testlab.**\<*your public domain name*> وتحقق من وجود أربعة ردود.
  
بعد ذلك، انضم إلى الجهاز الظاهري APP1 إلى مجال TESTLAB باستخدام هذه الأوامر في Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

تجدر الإشارة إلى أنه بعد تشغيل الأمر **"إضافة كمبيوتر** "، يجب توفير بيانات اعتماد حساب مجال TESTLABUser1\\.
  
بعد إعادة تشغيل APP1، اتصل به باستخدام حساب TESTLABUser1\\، ثم افتح موجه أوامر Windows PowerShell المسؤول.
  
بعد ذلك، اجعل APP1 خادم ويب بهذا الأمر على مستوى Windows PowerShell موجه الأوامر على APP1.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

بعد ذلك، أنشئ مجلدا مشتركا وملفا نصيا داخل المجلد على APP1 باستخدام أوامر PowerShell هذه.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

يبدو التكوين الحالي كما يلي:
  
![الخطوة 2 من تكوين قاعدة المؤسسة الذي تم محاكاته.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>الخطوة 3: تكوين CLIENT1

في هذه الخطوة، يمكنك إنشاء CLIENT1 وتكوينه، والذي يعمل ككمبيوتر محمول أو كمبيوتر لوحي أو كمبيوتر سطح مكتب نموذجي على الإنترانت.

> [!NOTE]  
> تقوم مجموعة الأوامر التالية بإنشاء CLIENT1 Windows Datacenter Server 2016، والذي يمكن القيام به لجميع أنواع اشتراكات Azure. إذا كان لديك اشتراك Visual Studio Azure، يمكنك إنشاء CLIENT1 Windows 10 باستخدام مدخل [Azure](https://portal.azure.com).
  
لإنشاء جهاز Azure ظاهري ل CLIENT1، قم بتعبئة اسم مجموعة الموارد وتشغيل هذه الأوامر في موجه الأوامر على الكمبيوتر المحلي.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

بعد ذلك، اتصل بالآلة الظاهرية CLIENT1 باستخدام اسم حساب المسؤول المحلي CLIENT1 وكلمة المرور، ثم افتح موجه أوامر على مستوى Windows PowerShell المسؤول.
  
للتحقق من دقة الاسم واتصال الشبكة بين CLIENT1 و DC1، قم **بتشغيل ping dc1.testlab.**\<*your public domain name*> أمر في Windows PowerShell موجه الأوامر وتحقق من وجود أربعة ردود.
  
بعد ذلك، انضم إلى الجهاز الظاهري CLIENT1 إلى مجال TESTLAB باستخدام هذه الأوامر في Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

تجدر الإشارة إلى أنه يجب توفير بيانات اعتماد حساب مجال TESTLABUser1\\ بعد تشغيل **الأمر "إضافة كمبيوتر** ".
  
بعد إعادة تشغيل CLIENT1، اتصل به باستخدام اسم حساب TESTLABUser1\\ وكلمة المرور، ثم افتح موجه أوامر Windows PowerShell المسؤول.
  
بعد ذلك، تحقق من إمكانية الوصول إلى موارد مشاركة الويب والملفات على APP1 من CLIENT1.
  
1. في Server Manager، في جزء الشجرة، حدد **خادم محلي**.
    
2. في **خصائص ل CLIENT1**، حدد **على** بجانب **تكوين الأمان المحسن ل IE**.
    
3. في **تكوين الأمان المحسن ل Internet Explorer**، حدد **إيقاف التشغيل** للمسؤولين والمستخدمين، ثم حدد **موافق**. 
    
4. من شاشة البدء، حدد **Internet Explorer**، ثم حدد **موافق**.
    
5. في شريط العنوان، أدخل **http <span>://</span>app1.testab.**\<*your public domain name*>**/**، ثم اضغط على **Enter**. من المفترض أن ترى الصفحة خدمات معلومات الإنترنت ويب ل APP1.
    
6. على شريط مهام سطح المكتب، حدد أيقونة مستكشف الملفات.
    
7. في شريط العنوان، أدخل **\\\\app1Files\\**، ثم اضغط على **Enter**. يجب أن ترى نافذة مجلد مع محتويات المجلد المشترك ملفات.
    
8. في نافذة **المجلد المشترك** ملفات، انقر نقرا مزدوجا **فوقExample.txt** الملف. من المفترض أن ترى محتويات Example.txt الملف.
    
9. أغلقexample.txt **- المفكرة** نوافذ **المجلدات** المشتركة ملفات.
    
يبدو التكوين الحالي كما يلي:
  
![الخطوة 3 من تكوين قاعدة المؤسسة الذي تم محاكاته.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>المرحلة 2: إنشاء اشتراك Microsoft 365 E5 اشتراكك

في هذه المرحلة، يمكنك إنشاء اشتراك Microsoft 365 E5 جديد يستخدم مستأجر Azure AD جديد، وهو اشتراك منفصل عن اشتراك الإنتاج. يمكنك القيام بذلك من خلال طريقتين:

- استخدم اشتراكا تجريبيا Microsoft 365 E5.

  إن Microsoft 365 E5 التجريبي هو 30 يوما، يمكن تمديده بسهولة إلى 60 يوما. عند انتهاء صلاحية الاشتراك التجريبي، يجب إما تحويله إلى اشتراك مدفوع أو إنشاء اشتراك تجريبي جديد. يعني إنشاء اشتراكات تجريبية جديدة أنك ستترك التكوين، الذي قد يتضمن سيناريوهات معقدة، في الخلف.  

- استخدم اشتراك إنتاج منفصلا Microsoft 365 E5 مع عدد صغير من التراخيص.

  هذه تكلفة إضافية، ولكنها تضمن أن لديك بيئة اختبار عمل لا تنتهي صلاحيتها؛ في ذلك، يمكنك تجربة الميزات والتكوينات والسيناريوهات. يمكنك استخدام بيئة الاختبار نفسها على المدى الطويل للحصول على إثباتات المبدأ وإثبات النظير والإدارة وتطوير التطبيق واختباره. هذا هو الأسلوب المستحسن.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>التسجيل للحصول على اشتراك تجريبي Office 365 E5 الإصدار التجريبي

من مدخل Azure، اتصل ب CLIENT1 باستخدام حساب CORP\User1.

لإنشاء اشتراك تجريبي Office 365 E5 جديد، قم بتنفيذ الإرشادات في المرحلة [1](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) من دليل اختبار التكوين الأساسي الخفيف.

لتكوين الاشتراك التجريبي Office 365 E5 الجديد، قم بتنفيذ الإرشادات في المرحلة [2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) من دليل اختبار التكوين الأساسي الخفيف.

#### <a name="using-an-office-365-e5-test-environment"></a>استخدام Office 365 E5 اختبارية

إذا كنت بحاجة إلى بيئة اختبار Office 365 فقط، لست بحاجة إلى قراءة ما تبقى من هذه المقالة.

للحصول على أدلة اختبار معمل إضافية تنطبق على كل من Microsoft 365 Office 365، راجع Microsoft 365 دليل [اختبار المؤسسة](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>إضافة اشتراك تجريبي Microsoft 365 E5 الإصدار التجريبي

لإضافة اشتراك تجريبي Microsoft 365 E5 وتكوين حسابات المستخدمين باستخدام التراخيص، قم بتنفيذ الإرشادات الواردة في المرحلة [3](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) من دليل اختبار المعمل للتكوين الأساسي الخفيف.

  
## <a name="results"></a>النتائج

لقد أصبحت بيئة الاختبار لديك الآن:
  
- Microsoft 365 E5 الإصدار التجريبي.
- يتم تمكين جميع حسابات المستخدمين المناسبة لاستخدام Microsoft 365 E5.
- إنترانت محاكاة وتبسيط.
    
يبدو التكوين النهائي كما يلي:
  
![المرحلة 2 من تكوين قاعدة المؤسسة المحاكاة.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
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