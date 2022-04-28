---
title: محاكاة تكوين قاعدة المؤسسة Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: استخدم دليل مختبر الاختبار هذا لإنشاء بيئة اختبار مؤسسة محاكاة Microsoft 365 للمؤسسة.
ms.openlocfilehash: 9c52bf657e91ceca9ef6e43f20a523a57a7b5042
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078702"
---
# <a name="the-simulated-enterprise-base-configuration"></a>التكوين الأساسي لمحاكاة المؤسسة

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

تصف هذه المقالة كيفية إنشاء بيئة مبسطة Microsoft 365 للمؤسسة تتضمن:

- اشتراك تجريبي أو مدفوع Microsoft 365 E5.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من ثلاثة أجهزة ظاهرية على شبكة Azure الظاهرية (DC1 وAPP1 و CLIENT1).
 
![تكوين قاعدة المؤسسة المحاكاة.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

يتضمن إنشاء بيئة اختبار مبسطة مرحلتين:
- [المرحلة 1: إنشاء إنترانت محاكاة](#phase-1-create-a-simulated-intranet)
- [المرحلة 2: إنشاء اشتراكك في Microsoft 365 E5](#phase-2-create-your-microsoft-365-e5-subscription)

يمكنك استخدام البيئة الناتجة لاختبار ميزات [ووظائف Microsoft 365 للمؤسسة](https://www.microsoft.com/microsoft-365/enterprise) باستخدام [دلائل مختبر الاختبار الإضافية](m365-enterprise-test-lab-guides.md) أو بنفسك.

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، انتقل إلى [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-create-a-simulated-intranet"></a>المرحلة 1: إنشاء إنترانت محاكاة

في هذه المرحلة، أنشئ إنترانت محاكاة في خدمات البنية الأساسية ل Azure التي تتضمن وحدة تحكم مجال خدمات مجال Active Directory (AD DS)، وخادم تطبيق، وكمبيوتر عميل.

ستستخدم أجهزة الكمبيوتر هذه في [Microsoft 365 إضافية لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md) لتكوين الهوية المختلطة والقدرات الأخرى وإظهارها.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>الأسلوب 1: إنشاء إنترانت محاكاة باستخدام قالب azure Resource Manager

في هذا الأسلوب، يمكنك استخدام قالب azure Resource Manager لإنشاء الإنترانت المحاكاة. تحتوي قوالب azure Resource Manager على جميع الإرشادات لإنشاء البنية الأساسية الشبكات Azure والأجهزة الظاهرية وتكوينها.

قبل نشر القالب، اقرأ [صفحة README للقالب](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) واجهز المعلومات التالية:

- اسم مجال DNS العام لبيئة الاختبار الخاصة بك (testlab.\<*your public domain*>). ستدخل هذا الاسم في الحقل **"اسم المجال"** في صفحة **النشر المخصصة** .
- بادئة تسمية DNS لعناوين URL لعناوين IP العامة للأجهزة الظاهرية. ستحتاج إلى إدخال هذه التسمية في حقل بادئة **تسمية Dns** في صفحة **النشر المخصصة** .

بعد قراءة الإرشادات، حدد **Deploy to Azure** على [صفحة README للقالب](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) للبدء.

>[!Note]
>يتطلب الإنترانت المحاكي الذي تم إنشاؤه بواسطة قالب azure Resource Manager اشتراك Azure مدفوعا.

بعد اكتمال القالب، يبدو التكوين كما يلي:

![الإنترانت المحاكي في خدمات البنية الأساسية ل Azure.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>الأسلوب 2: إنشاء إنترانت المحاكاة باستخدام Azure PowerShell

في هذه الطريقة، يمكنك استخدام Windows PowerShell والوحدة النمطية Azure PowerShell لإنشاء البنية الأساسية للشبكات والأجهزة الظاهرية وتكوينها.

استخدم هذا الأسلوب إذا كنت تريد الحصول على خبرة في إنشاء عناصر البنية الأساسية ل Azure خطوة واحدة في كل مرة باستخدام PowerShell. يمكنك بعد ذلك تخصيص كتل أوامر PowerShell للنشر الخاص بك من الأجهزة الظاهرية الأخرى في Azure.

#### <a name="step-1-create-dc1"></a>الخطوة 1: إنشاء DC1

في هذه الخطوة، يمكنك إنشاء شبكة ظاهرية Azure وإضافة DC1، وهو جهاز ظاهري هو وحدة تحكم بالمجال لمجال AD DS.

أولا، ابدأ موجه أوامر Windows PowerShell على الكمبيوتر المحلي.
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية أحدث إصدار من Azure PowerShell. راجع [بدء استخدام أوامر Azure PowerShell cmdlets](/powershell/azureps-cmdlets-docs/). 
  
سجل الدخول إلى حساب Azure الخاص بك باستخدام الأمر التالي.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام الأمر التالي.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

تعيين اشتراك Azure الخاص بك. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأقواس الزاوية ("<" و">")، بالاسم الصحيح.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

بعد ذلك، قم بإنشاء مجموعة موارد جديدة لمختبر اختبار المؤسسة المحاكي. لتحديد اسم مجموعة موارد فريد، استخدم هذا الأمر لإدراج مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

إنشاء مجموعة الموارد الجديدة باستخدام هذه الأوامر. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأقواس الزاوية، بالأسماء الصحيحة.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، قم بإنشاء شبكة TestLab الظاهرية التي ستستضيف الشبكة الفرعية لشبكة الشركة لبيئة المؤسسة المحاكاة وحمايتها مع مجموعة أمان الشبكة. املأ اسم مجموعة الموارد وقم بتشغيل هذه الأوامر في موجه الأوامر PowerShell على الكمبيوتر المحلي.
  
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

بعد ذلك، يمكنك إنشاء الجهاز الظاهري DC1 وتكوينه كوحدة تحكم بالمجال **لملف الاختبار.**\<your public domain> مجال AD DS وخادم DNS للأجهزة الظاهرية لشبكة TestLab الظاهرية. على سبيل المثال، إذا كان اسم مجالك العام **<span>contoso.com</span>**، فسيكون الجهاز الظاهري DC1 وحدة تحكم بالمجال لمجال **<span>testlab.contoso.com</span>**.
  
لإنشاء جهاز ظاهري Azure ل DC1، املأ اسم مجموعة الموارد الخاصة بك وقم بتشغيل هذه الأوامر في موجه أوامر PowerShell على الكمبيوتر المحلي.
  
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

ستتم مطالبتك باسم مستخدم وكلمة مرور لحساب المسؤول المحلي على DC1. استخدم كلمة مرور قوية وسجل الاسم وكلمة المرور في موقع آمن.
  
بعد ذلك، اتصل بالجهاز الظاهري DC1:
  
1. في [مدخل Azure](https://portal.azure.com)، حدد **مجموعات الموارد** > <**_اسم مجموعة الموارد الجديدة_*_> > _* DC1** >  **الاتصال**.
    
2. في الجزء المفتوح، حدد **تنزيل ملف RDP**. افتح ملف DC1.rdp الذي تم تنزيله، ثم حدد **الاتصال**.
    
3. حدد اسم حساب المسؤول المحلي DC1:
    
   - ل Windows 7:
    
     في مربع الحوار **أمن Windows**، حدد **"استخدام حساب آخر**". في **اسم المستخدم**، أدخل *اسم حساب مسؤول DC1local* **\\**<>.
    
   - بالنسبة Windows 8 أو Windows 10:
    
     في مربع الحوار **أمن Windows**، حدد **"المزيد من الخيارات**"، ثم حدد **"استخدام حساب مختلف**". في **اسم المستخدم**، أدخل *اسم حساب مسؤول DC1local* **\\**<>.
    
4. في **كلمة المرور**، أدخل كلمة مرور حساب المسؤول المحلي، ثم حدد **"موافق**".
    
5. عند المطالبة، حدد **"نعم**".
    
بعد ذلك، أضف قرص بيانات إضافي كوحدة تخزين جديدة مع حرف محرك الأقراص F: مع هذا الأمر في موجه أوامر Windows PowerShell على مستوى المسؤول على DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

بعد ذلك، قم بتكوين DC1 كوحدة تحكم بالمجال وخادم DNS ل **testlab.**\<*your public domain*> المجال. حدد اسم مجالك العام، وقم بإزالة الأقواس الزاوية، ثم قم بتشغيل هذه الأوامر على مستوى المسؤول Windows PowerShell موجه الأوامر على DC1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
ستحتاج إلى تحديد كلمة مرور مسؤول الوضع الآمن. تخزين كلمة المرور هذه في موقع آمن.
  
لاحظ أن هذه الأوامر قد تستغرق بضع دقائق لإكمالها.
  
بعد إعادة تشغيل DC1، أعد الاتصال بالجهاز الظاهري DC1.
  
1. في [مدخل Microsoft Azure](https://portal.azure.com)، حدد **مجموعات الموارد** > <*اسم مجموعة الموارد*> > **DC1** >  **الاتصال**.
    
2. قم بتشغيل ملف DC1.rdp الذي تم تنزيله، ثم حدد **الاتصال**.
    
3. في **أمن Windows**، حدد **"استخدام حساب آخر**". في **اسم المستخدم**، أدخل *اسم حساب مسؤول TESTLABlocal* **\\**<>.
    
4. في المربع **"كلمة المرور** "، أدخل كلمة مرور حساب المسؤول المحلي، ثم حدد **"موافق**".
    
5. عند المطالبة، حدد **"نعم**".
    
بعد ذلك، أنشئ حساب مستخدم في Active Directory سيتم استخدامه عند تسجيل الدخول إلى أجهزة كمبيوتر أعضاء مجال TESTLAB. تشغيل هذا الأمر على مستوى المسؤول Windows PowerShell موجه الأوامر.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

لاحظ أن هذا الأمر يطالبك بتوفير كلمة مرور حساب User1. سيتم استخدام هذا الحساب لاتصالات سطح المكتب البعيد لكافة أجهزة الكمبيوتر الأعضاء في مجال TESTLAB، لذا اختر كلمة مرور قوية. تسجيل كلمة مرور حساب User1 وتخزينها في موقع آمن.
  
بعد ذلك، قم بتكوين حساب User1 الجديد كمجال، والمؤسسة، ومسؤول المخطط. قم بتشغيل هذا الأمر على مستوى المسؤول Windows PowerShell موجه الأوامر.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

أغلق جلسة عمل سطح المكتب البعيد باستخدام DC1 ثم أعد الاتصال باستخدام حساب TESTLABUser1\\.
  
بعد ذلك، للسماح بنسبة استخدام الشبكة لأداة Ping، قم بتشغيل هذا الأمر على مستوى المسؤول Windows PowerShell موجه الأوامر.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

يبدو التكوين الحالي كما يلي:
  
![الخطوة 1 من تكوين قاعدة المؤسسة المحاكاة.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>الخطوة 2: تكوين APP1

في هذه الخطوة، يمكنك إنشاء وتكوين APP1، وهو خادم تطبيق يوفر في البداية خدمات مشاركة الملفات والويب.

لإنشاء جهاز ظاهري من Azure ل APP1، قم بتعبئة اسم مجموعة الموارد الخاصة بك وتشغيل هذه الأوامر في موجه الأوامر على الكمبيوتر المحلي.
  
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

بعد ذلك، اتصل بالجهاز الظاهري APP1 باستخدام اسم حساب مسؤول APP1 المحلي وكلمة المرور، ثم افتح موجه أوامر Windows PowerShell.
  
للتحقق من تحليل الاسم واتصال الشبكة بين APP1 و DC1، قم بتشغيل **ping dc1.testlab.**\<*your public domain name*> الأمر والتحقق من وجود أربعة ردود.
  
بعد ذلك، قم بضم الجهاز الظاهري APP1 إلى مجال TESTLAB باستخدام هذه الأوامر في موجه Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

لاحظ أنه بعد تشغيل الأمر **"جهاز الكمبيوتر الإضافي** "، يجب توفير بيانات اعتماد حساب المجال TESTLABUser1\\.
  
بعد إعادة تشغيل APP1، اتصل به باستخدام حساب TESTLABUser1\\، ثم افتح موجه أوامر Windows PowerShell على مستوى المسؤول.
  
بعد ذلك، اجعل APP1 خادم ويب مع هذا الأمر في موجه أوامر Windows PowerShell على مستوى المسؤول على APP1.
  
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
  
![الخطوة 2 من التكوين الأساسي لمحاكاة المؤسسة.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>الخطوة 3: تكوين CLIENT1

في هذه الخطوة، يمكنك إنشاء وتكوين CLIENT1، الذي يعمل ككمبيوتر محمول أو كمبيوتر لوحي أو كمبيوتر سطح مكتب نموذجي على إنترانت.

> [!NOTE]  
> تنشئ مجموعة الأوامر التالية CLIENT1 قيد التشغيل Windows Server 2016 Datacenter، والذي يمكن القيام به لجميع أنواع اشتراكات Azure. إذا كان لديك اشتراك Azure يستند إلى Visual Studio، يمكنك إنشاء CLIENT1 قيد التشغيل Windows 10 باستخدام [مدخل Azure](https://portal.azure.com).
  
لإنشاء جهاز ظاهري من Azure ل CLIENT1، قم بتعبئة اسم مجموعة الموارد الخاصة بك وتشغيل هذه الأوامر في موجه الأوامر على الكمبيوتر المحلي.
  
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

بعد ذلك، اتصل بالجهاز الظاهري CLIENT1 باستخدام اسم حساب المسؤول المحلي CLIENT1 وكلمة المرور، ثم افتح موجه أوامر Windows PowerShell على مستوى المسؤول.
  
للتحقق من تحليل الاسم واتصال الشبكة بين CLIENT1 و DC1، قم بتشغيل **ping dc1.testlab.**\<*your public domain name*> الأمر في موجه أوامر Windows PowerShell وتحقق من وجود أربعة ردود.
  
بعد ذلك، قم بضم الجهاز الظاهري CLIENT1 إلى مجال TESTLAB باستخدام هذه الأوامر في موجه Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

تجدر الإشارة إلى أنه يجب توفير بيانات اعتماد حساب مجال TESTLABUser1\\ بعد تشغيل الأمر **Add-Computer** .
  
بعد إعادة تشغيل CLIENT1، اتصل به باستخدام اسم حساب TESTLABUser1\\ وكلمة المرور، ثم افتح موجه أوامر Windows PowerShell على مستوى المسؤول.
  
بعد ذلك، تحقق من أنه يمكنك الوصول إلى موارد مشاركة الويب والملفات على APP1 من CLIENT1.
  
1. في Server Manager، في جزء الشجرة، حدد **"الخادم المحلي**".
    
2. في **خصائص CLIENT1**، حدد **"On** " بجوار **تكوين أمان IE المحسن**.
    
3. في **Internet Explorer Enhanced Security Configuration**، حدد **"إيقاف التشغيل** **للمسؤولين** **والمستخدمين**"، ثم حدد **"موافق**".
    
4. من شاشة البدء، حدد **Internet Explorer**، ثم حدد **"موافق**".
    
5. في شريط العناوين، أدخل **http <span>://</span>app1.testab.**\<*your public domain name*>**/** ثم اضغط على مفتاح الإدخال **Enter**. يجب أن تشاهد صفحة ويب خدمات معلومات الإنترنت الافتراضية ل APP1.
    
6. على شريط مهام سطح المكتب، حدد أيقونة مستكشف الملفات.
    
7. في شريط العناوين، أدخل **\\\\app1Files\\**، ثم اضغط على **مفتاح الإدخال Enter**. يجب أن تشاهد نافذة مجلد مع محتويات المجلد المشترك "ملفات".
    
8. في نافذة المجلد المشترك " **ملفات** "، انقر نقرا مزدوجا فوق ملف **Example.txt** . يجب أن تشاهد محتويات ملف Example.txt.
    
9. أغلق **example.txt - المفكرة** ونوافذ **المجلد المشترك** للملفات.
    
يبدو التكوين الحالي كما يلي:
  
![الخطوة 3 من تكوين قاعدة المؤسسة المحاكاة.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>المرحلة 2: إنشاء اشتراكك في Microsoft 365 E5

في هذه المرحلة، يمكنك إنشاء اشتراك Microsoft 365 E5 جديد يستخدم مستأجر Azure AD جديد، وهو اشتراك منفصل عن اشتراك الإنتاج الخاص بك. يمكنك القيام بذلك بطريقتين:

- استخدام اشتراك تجريبي من Microsoft 365 E5.

  الاشتراك التجريبي Microsoft 365 E5 هو 30 يوما، والتي يمكن تمديدها بسهولة إلى 60 يوما. عند انتهاء صلاحية الاشتراك التجريبي، يجب عليك إما تحويله إلى اشتراك مدفوع أو إنشاء اشتراك تجريبي جديد. يعني إنشاء اشتراكات تجريبية جديدة أنك ستترك التكوين الخاص بك، والذي قد يتضمن سيناريوهات معقدة، في الخلف.  

- استخدم اشتراك إنتاج منفصلا من Microsoft 365 E5 مع عدد صغير من التراخيص.

  هذه تكلفة إضافية، ولكنها تضمن أن لديك بيئة اختبار عمل لا تنتهي صلاحيتها؛ في ذلك، يمكنك تجربة الميزات والتكوينات والسيناريوهات. يمكنك استخدام نفس بيئة الاختبار على المدى الطويل لإثبات المبدأ، والظاهرية للأقران والإدارة، وتطوير التطبيقات واختبارها. هذا هو الأسلوب الموصى به.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>التسجيل للحصول على اشتراك تجريبي Office 365 E5

من مدخل Microsoft Azure، اتصل ب CLIENT1 باستخدام حساب CORP\User1.

لإنشاء اشتراك تجريبي Office 365 E5 جديد، نفذ الإرشادات في [المرحلة 1](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-microsoft-365-e5-subscription) من دليل اختبار اختبار التكوين الأساسي الخفيف.

لتكوين اشتراكك التجريبي Office 365 E5 الجديد، قم بتنفيذ الإرشادات في [المرحلة 2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) من دليل اختبار مختبر التكوين الأساسي الخفيف.

#### <a name="using-an-office-365-e5-test-environment"></a>استخدام بيئة اختبار Office 365 E5

إذا كنت بحاجة إلى بيئة اختبار Office 365 فقط، فلن تحتاج إلى قراءة باقي هذه المقالة.

للحصول على دلائل مختبر اختبار إضافية تنطبق على كل من Microsoft 365 Office 365، راجع [Microsoft 365 لدلائل مختبر الاختبار للمؤسسات](m365-enterprise-test-lab-guides.md).

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>إضافة اشتراك تجريبي Microsoft 365 E5

لإضافة اشتراك تجريبي Microsoft 365 E5 وتكوين حسابات المستخدمين لديك مع التراخيص، قم بتنفيذ الإرشادات في [المرحلة 3](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) من دليل اختبار مختبر التكوين الأساسي الخفيف.

  
## <a name="results"></a>نتائج

تحتوي بيئة الاختبار الخاصة بك الآن على:
  
- اشتراك تجريبي Microsoft 365 E5.
- يتم تمكين جميع حسابات المستخدمين المناسبة لاستخدام Microsoft 365 E5.
- إنترانت محاكاة ومبسطة.
    
يبدو التكوين النهائي كما يلي:
  
![المرحلة 2 من تكوين قاعدة المؤسسة المحاكاة.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
أنت الآن جاهز لتجربة ميزات إضافية [من Microsoft 365 للمؤسسة](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>الخطوات التالية

استكشف هذه المجموعات الإضافية من دلائل مختبر الاختبار:
  
- [الهوية](m365-enterprise-test-lab-guides.md#identity)
- [إدارة الأجهزة المحمولة](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [حماية المعلومات](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>راجع أيضًا

[Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md)

[نظرة عامة حول Microsoft 365 للمؤسسات](microsoft-365-overview.md)

[موارد ووثائق Microsoft 365 للمؤسسات](/microsoft-365-enterprise/)