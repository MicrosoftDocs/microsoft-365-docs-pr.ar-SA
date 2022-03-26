---
title: الهوية المتحدة لبيئة اختبار Microsoft 365 الخاصة بك
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'ملخص: تكوين المصادقة الخارجية لبيئة Microsoft 365 الاختبار.'
ms.openlocfilehash: 6553590c06df4caf099c7b4db47d253bd37b39fd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63569382"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>الهوية المتحدة لبيئة اختبار Microsoft 365 الخاصة بك

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

Microsoft 365 دعم الهوية المتحدة. وهذا يعني أنه بدلا من إجراء عملية التحقق من صحة بيانات الاعتماد نفسها، Microsoft 365 المستخدم الذي يقوم بتوصيل خادم مصادقة Microsoft 365 موثوق به. إذا كانت بيانات اعتماد المستخدم صحيحة، يصدر خادم المصادقة المتحدة رمز أمان مميز يرسله العميل Microsoft 365 كدليل على المصادقة. تسمح الهوية المتحدة ب إلغاء تحميل المصادقة Microsoft 365 وسيناريوهات الأمان والمصادقة المتقدمة.
  
تصف هذه المقالة كيفية تكوين المصادقة المتحدة لبيئة Microsoft 365 الاختبار، مما يؤدي إلى ما يلي:

![المصادقة الخارجية لبيئة Microsoft 365 الاختبار.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
يتكون هذا التكوين من:
  
- اشتراك Microsoft 365 E5 الإصدار التجريبي أو الإنتاج.
    
- إنترانت منظمة مبسطة متصلة بالإنترنت، تتكون من خمسة أجهزة ظاهرية على شبكة فرعية لشبكة ظاهرية من Azure (DC1 و APP1 و CLIENT1 و ADFS1 و PROXY1). يتم تشغيل الاتصال Azure AD على APP1 لمزامنة قائمة الحسابات في مجال خدمات مجال Active Directory Microsoft 365. يتلقى PROXY1 طلبات المصادقة الواردة. يتحقق ADFS1 من صحة بيانات الاعتماد باستخدام DC1 وي يصدر رموز الأمان المميزة.
    
يتضمن إعداد بيئة الاختبار هذه خمس مراحل:
- [المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [المرحلة الثانية: إنشاء خادم AD FS](#phase-2-create-the-ad-fs-server)
- [المرحلة 3: إنشاء خادم وكيل ويب](#phase-3-create-the-web-proxy-server)
- [المرحلة 4: إنشاء شهادة موقعة ذاتيا وتكوين ADFS1 وS PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [المرحلة 5: Microsoft 365 الهوية المتحدة](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> لا يمكنك تكوين بيئة الاختبار هذه باستخدام اشتراك الإصدار التجريبي من Azure.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة كلمة المرور لبيئة Microsoft 365 الاختبار

اتبع الإرشادات الواردة [في مزامنة كلمة المرور لمزامنة Microsoft 365](password-hash-sync-m365-ent-test-environment.md). يبدو التكوين الناتج كما يلي:
  
![المؤسسة التي تم محاكاتها مع بيئة اختبار مزامنة كلمة المرور.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراك Microsoft 365 E5 تجريبية أو مدفوعة.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 و APP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل Azure AD الاتصال APP1 لمزامنة مجال خدمات مجال TESTLAB Active Directory (AD DS) مع مستأجر Azure AD لاشتراكاتك Microsoft 365 بشكل دوري.

## <a name="phase-2-create-the-ad-fs-server"></a>المرحلة الثانية: إنشاء خادم AD FS

يوفر خادم AD FS مصادقة Microsoft 365 بين الحسابات والحسابات في corp.contoso.com المستضاف على DC1.
  
لإنشاء جهاز Azure ظاهري ل ADFS1، قم بتعبئة اسم اشتراكك ومجموعة الموارد وموقع Azure لتكوين الأساس، ثم قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
```powershell
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

بعد ذلك، استخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية ADFS1 باستخدام اسم حساب المسؤول المحلي وكلمة المرور في ADFS1، ثم افتح Windows PowerShell الأوامر.
  
للتحقق من دقة الاسم واتصال الشبكة بين ADFS1 و DC1، قم **بتشغيل الأمر dc1.corp.contoso.com** وتحقق من وجود أربعة ردود.
  
بعد ذلك، انضم إلى الجهاز الظاهري ADFS1 إلى مجال CORP باستخدام هذه الأوامر في Windows PowerShell على ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

يبدو التكوين الناتج كما يلي:
  
![أضاف خادم AD FS إلى DirSync Microsoft 365 الاختبار.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>المرحلة 3: إنشاء خادم وكيل ويب

يوفر PROXY1 وكيلا لرسائل المصادقة بين المستخدمين الذين يحاولون المصادقة و ADFS1.
  
لإنشاء جهاز Azure ظاهري ل PROXY1، قم بتعبئة اسم مجموعة الموارد وموقع Azure، ثم قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> يتم تعيين عنوان IP عام ثابت ل PROXY1 لأنك ستنشئ سجل DNS عاما يشير إلى ذلك ويجب ألا يتغير عند إعادة تشغيل الجهاز الظاهري PROXY1.
  
بعد ذلك، أضف قاعدة إلى مجموعة أمان الشبكة لشبكة CorpNet الفرعية للسماح بترقيم البيانات الواردة غير المرغوب فيها من الإنترنت إلى عنوان IP الخاص ل PROXY1 وميناء TCP 443. تشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

بعد ذلك، استخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية PROXY1 باستخدام اسم حساب المسؤول المحلي وكلمة المرور في PROXY1، ثم افتح موجه أوامر Windows PowerShell على PROXY1.
  
للتحقق من دقة الاسم واتصال الشبكة بين PROXY1 و DC1، قم **بتشغيل الأمر dc1.corp.contoso.com** وتحقق من وجود أربعة ردود.
  
بعد ذلك، انضم إلى الجهاز الظاهري PROXY1 إلى مجال CORP باستخدام هذه الأوامر في Windows PowerShell على PROXY1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

اعرض عنوان IP العام ل PROXY1 باستخدام أوامر Azure PowerShell هذه على الكمبيوتر المحلي.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

بعد ذلك، يمكنك العمل مع موفر DNS العام وإنشاء سجل DNS A عام جديد **ل fs.testlab.**\<*your DNS domain name*> التي يتم حلها إلى عنوان IP المعروض بواسطة الأمر **"مضيف الكتابة** ". **fs.testlab.**\<*your DNS domain name*> يشار إليه فيما بعد باسم  *FQDN لخدمة الاتحاد*.
  
بعد ذلك، استخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية DC1 باستخدام بيانات اعتماد CORPUser1\\، ثم قم بتشغيل الأوامر التالية على موجه أوامر Windows PowerShell المسؤول:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
تنشئ هذه الأوامر سجل DNS A داخلي بحيث تتمكن الأجهزة الظاهرية على شبكة Azure الظاهرية من حل FQDN لخدمة الاتحاد الداخلي إلى عنوان IP الخاص ل ADFS1.
  
يبدو التكوين الناتج كما يلي:
  
![أضاف الخادم الوكيل لتطبيق ويب إلى DirSync Microsoft 365 الاختبار.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>المرحلة 4: إنشاء شهادة موقعة ذاتيا وتكوين ADFS1 وS PROXY1

في هذه المرحلة، يمكنك إنشاء شهادة رقمية موقعة ذاتيا لخدمة الاتحاد FQDN وتكوين ADFS1 وS PROXY1 كمزرعة AD FS.
  
أولا، استخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية DC1 باستخدام بيانات اعتماد CORPUser1\\، ثم افتح موجه أوامر Windows PowerShell المسؤول.
  
بعد ذلك، أنشئ حساب خدمة AD FS بهذا الأمر في موجه الأوامر Windows PowerShell على DC1:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
لاحظ أن هذا الأمر يطالبك بتزويدك بكلمة مرور الحساب. اختر كلمة مرور قوية وسجلها في موقع آمن. ستحتاج إليها في هذه المرحلة وفي المرحلة 5.
  
استخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية ADFS1 باستخدام بيانات اعتماد CORPUser1\\. افتح موجه أوامر على مستوى المسؤول Windows PowerShell ADFS1، وملء FQDN لخدمة الاتحاد، ثم قم بتشغيل هذه الأوامر لإنشاء شهادة موقعة ذاتيا:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

بعد ذلك، استخدم هذه الخطوات لحفظ الشهادة الجديدة الموقعة ذاتيا كملف.
  
1. حدد **بدء**، **وأدخلmmc.exe**، ثم اضغط على **Enter**.
    
2. حدد **FileAdd** > **/Remove Snap-in**.
    
3. في **إضافة الوظائف الإضافية** أو إزالتها، انقر نقرا مزدوجا فوق الشهادات في قائمة الوظائف الإضافية المتوفرة، وحدد حساب **الكمبيوتر**، ثم حدد **التالي**.
    
4. في **تحديد الكمبيوتر**، حدد **إنهاء**، ثم حدد **موافق**.
    
5. في جزء الشجرة، افتح **الشهادات (الكمبيوتر المحلي) > الشهادات > الشخصية**.
    
6. حدد الشهادة مع FQDN لخدمة الاتحاد واضغط عليها مع الاستمرار (أو انقر ب الماوس الأيمن **فوقها**)، وحدد كل المهام، ثم حدد تصدير.
    
7. في صفحة **الترحيب** ، حدد **التالي**.
    
8. في الصفحة **تصدير مفتاح خاص** ، حدد **نعم**، ثم حدد **التالي**.
    
9. في الصفحة **تصدير تنسيق الملف** ، حدد **تصدير كل الخصائص الموسعة**، ثم حدد **التالي**.
    
10. في صفحة **الأمان** ، حدد **كلمة المرور** وأدخل كلمة مرور في **كلمة المرور** **وتأكيد كلمة المرور.**
    
11. في الصفحة **ملف لتصدير** ، حدد **استعراض**.
    
12. استعرض إلى **المجلد C:\\Certs** ، وأدخل **SSL** في **اسم** الملف، ثم حدد **حفظ.**
    
13. في الصفحة **ملف لتصدير** ، حدد **التالي**.
    
14. في الصفحة **إكمال معالج تصدير الشهادة** ، حدد **إنهاء**. عند المطالبة، حدد **موافق**.
    
بعد ذلك، قم بتثبيت خدمة AD FS بهذا الأمر في موجه الأوامر Windows PowerShell ADFS1:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

انتظر حتى اكتمال التثبيت.
  
بعد ذلك، قم بتكوين خدمة AD FS باستخدام الخطوات التالية:
  
1. حدد **بدء**، ثم حدد **أيقونة مدير الخادم** .
    
2. في جزء الشجرة من Server Manager، حدد **AD FS**.
    
3. في شريط الأدوات في الأعلى، حدد رمز التحذير البرتقالي اللون، ثم حدد **تكوين خدمة الاتحاد على هذا الخادم**.
    
4. في صفحة **الترحيب** في معالج تكوين خدمات الاتحاد ل Active Directory، حدد **التالي**.
    
5. على الصفحة **الاتصال AD DS**، حدد **التالي**.
    
6. في الصفحة **تحديد خصائص الخدمة** :
    
  - للحصول **على شهادة SSL**، حدد السهم لأسفل، ثم حدد الشهادة التي بها اسم FQDN لخدمة الاتحاد.
    
  - في **اسم عرض خدمة الاتحاد**، أدخل اسم مؤسستك الخيالية.
    
  - حدد **التالي**.
    
7. في الصفحة **تحديد حساب الخدمة** ، حدد **تحديد** **لاسم الحساب**.
    
8. في **تحديد حساب مستخدم أو خدمة**، أدخل **ADFS-Service**، وحدد **التحقق من الأسماء**، ثم حدد **موافق**.
    
9. في **كلمة مرور الحساب**، أدخل كلمة المرور الخاصة ADFS-Service الحساب، ثم حدد **التالي**.
    
10. في الصفحة **تحديد قاعدة بيانات التكوين** ، حدد **التالي**.
    
11. في الصفحة **خيارات المراجعة** ، حدد **التالي**.
    
12. في صفحة **الاختبارات الأساسية** ، حدد **تكوين**.

13. في صفحة **النتائج** ، حدد **إغلاق**.
    
14. حدد **بدء**، وحدد أيقونة الطاقة، وحدد **إعادة تشغيل**، ثم حدد **متابعة**.
    
من مدخل [Azure،](https://portal.azure.com) اتصل ب PROXY1 باستخدام بيانات اعتماد حساب CORPUser1\\.
  
بعد ذلك، استخدم هذه الخطوات لتثبيت الشهادة الموقعة ذاتيا **على كل من PROXY1 و APP1**.
  
1. حدد **بدء**، **وأدخلmmc.exe**، ثم اضغط على **Enter**.
    
2. حدد **ملف > إضافة/إزالة المحاذاة**.
    
3. في **إضافة الوظائف الإضافية** أو إزالتها، انقر نقرا مزدوجا فوق الشهادات في قائمة الوظائف الإضافية المتوفرة، وحدد حساب **الكمبيوتر**، ثم حدد **التالي**.
    
4. في **تحديد الكمبيوتر**، حدد **إنهاء**، ثم حدد **موافق**.
    
5. في جزء الشجرة، افتح **الشهادات (الكمبيوتر المحلي)** > **PersonalCertificates** > .
    
6. حدد شخصي (أو انقر ب الماوس **الأيمن) مع** الاستمرار، وحدد **كل المهام**، ثم حدد **استيراد**.
    
7. في صفحة **الترحيب** ، حدد **التالي**.
    
8. في الصفحة **ملف لاستيراد**، أدخل **\\\\adfs1certssl.pfx\\\\**، ثم حدد **التالي**.
    
9. في صفحة **حماية المفتاح الخاص** ، أدخل كلمة مرور الشهادة في **كلمة المرور**، ثم حدد **التالي.**
    
10. في صفحة **مخزن الشهادة** ، حدد **التالي.**
    
11. في صفحة **إكمال** ، حدد **إنهاء**.
    
12. في صفحة **مخزن الشهادات** ، حدد **التالي**.
    
13. عند المطالبة، حدد **موافق**.
    
14. في جزء الشجرة، حدد **شهادات**.
    
15. حدد الشهادة مع الاستمرار (أو انقر ب الماوس الأيمن فوقها)، ثم حدد **نسخ**.
    
16. في جزء الشجرة، افتح **المصادقة الجذر الموثوق بها** **AuthoritiesCertificates** > .
    
17. حرك مؤشر الماوس أسفل قائمة الشهادات المثبتة، وحدد مع الاستمرار (أو انقر بزر الماوس الأيمن)، ثم حدد **لصق**.
    
افتح موجه أوامر PowerShell على مستوى المسؤول ثم ادير الأمر التالي:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

انتظر حتى اكتمال التثبيت.
  
استخدم هذه الخطوات لتكوين خدمة وكيل تطبيق ويب لاستخدام ADFS1 كخادم الاتحاد الخاص بها:
  
1. حدد **بدء**، ثم حدد **Server Manager**.
    
2. في جزء الشجرة، حدد **الوصول البعيد**.
    
3. في شريط الأدوات في الأعلى، حدد رمز التحذير البرتقالي اللون، ثم حدد **فتح معالج وكيل تطبيق ويب**.
    
4. في صفحة **الترحيب** من معالج تكوين وكيل تطبيق ويب، حدد **التالي**.
    
5. في صفحة **خادم الاتحاد** :
    
  - في المربع **اسم خدمة الاتحاد** ، أدخل FQDN لخدمة الاتحاد.
    
  - في المربع **اسم المستخدم**، أدخل **CORPUser1\\**.
    
  - في المربع **كلمة** المرور، أدخل كلمة المرور لحساب User1.
    
  - حدد **التالي**.
    
6. في صفحة **شهادة وكيل AD FS** ، حدد السهم لأسفل، وحدد الشهادة مع FQDN لخدمة الاتحاد، ثم حدد **التالي**.
    
7. في صفحة **التأكيد** ، حدد **تكوين**.
    
8. في صفحة **النتائج** ، حدد **إغلاق**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>المرحلة 5: Microsoft 365 الهوية المتحدة

استخدم مدخل [Azure](https://portal.azure.com) للاتصال بالآلة الظاهرية APP1 باستخدام بيانات اعتماد حساب CORPUser1\\.
  
استخدم هذه الخطوات لتكوين Azure AD الاتصال اشتراكك Microsoft 365 المصادقة الخارجية:
  
1. من سطح المكتب، انقر نقرا مزدوجا فوق **Azure AD الاتصال**.
    
2. في صفحة **مرحبا بك في Azure AD الاتصال**، حدد **تكوين**.
    
3. في صفحة **المهام الإضافية** ، حدد **تغيير تسجيل الدخول** إلى المستخدم، ثم حدد **التالي**.
    
4. في الصفحة **الاتصال Azure AD**، أدخل اسم حساب المسؤول العام وكلمة المرور، ثم حدد **التالي**.
    
5. في صفحة **تسجيل الدخول إلى** المستخدم، حدد **الاتحاد مع AD FS**، ثم حدد **التالي**.
    
6. في صفحة **مزرعة AD FS** ، حدد استخدام مزرعة **AD FS** موجودة، وأدخل **ADFS1** في المربع **اسم** الخادم، ثم حدد **التالي**.
    
7. عند مطالبتك بإدخال بيانات اعتماد الخادم، أدخل بيانات اعتماد حساب CORPUser1\\، ثم حدد **موافق**.
    
8. في صفحة **بيانات اعتماد مسؤول** المجال، أدخل **CORPUser1\\** في المربع اسم المستخدم، وأدخل كلمة مرور الحساب في المربع كلمة  المرور، ثم حدد **التالي**.
    
9. في **صفحة حساب خدمة AD FS**، أدخل **CORPADFS-Service\\** في المربع اسم المستخدم  للمجال، وأدخل كلمة مرور الحساب في المربع **كلمة مرور** مستخدم المجال، ثم حدد **التالي**.
    
10. في **صفحة مجال Azure AD،** في **المجال**، حدد اسم المجال الذي أنشأته مسبقا وأضيفته إلى اشتراكك في المرحلة 1، ثم حدد **التالي**.
    
11. في الصفحة **جاهز لتكوين** ، حدد **تكوين**.
    
12. في الصفحة **اكتمال التثبيت** ، حدد **التحقق**.
    
    من المفترض أن تشاهد رسائل تشير إلى أنه تم التحقق من تكوين الإنترنت والإنترانت.
    
13. في الصفحة **اكتمال التثبيت** ، حدد **إنهاء**.
    
لإظهار أن المصادقة الخارجية تعمل:
  
1. افتح مثيلا خاصا جديدا للمستعرض على الكمبيوتر المحلي واذهب إلى [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. بالنسبة إلى بيانات اعتماد تسجيل الدخول **، أدخل user1@**\<*the domain created in Phase 1*>.
    
    على سبيل المثال، إذا كان مجال **الاختبار testlab.contoso.com،** يمكنك إدخال "user1@testlab.contoso.com". اضغط على **المفتاح Tab** أو Microsoft 365 إعادة توجيهك تلقائيا.
    
    من المفترض أن ترى الآن **أن اتصالك ليس صفحة** خاصة. أنت ترى ذلك لأنك قمت بتثبيت شهادة موقعة ذاتيا على ADFS1 لا يمكن للكمبيوتر المكتبي التحقق من صحتها. في عملية نشر إنتاج المصادقة الخارجية، يمكنك استخدام شهادة من مرجع ممصادقة موثوق به ولا يمكن للمستخدمين رؤية هذه الصفحة.
    
3. في الصفحة **اتصالك ليس خاصا** ، حدد **متقدم**، ثم حدد **متابعة إلى \<*your federation service FQDN*>**. 
    
4. على الصفحة التي تحتوي على اسم مؤسستك الخيالية، سجل الدخول باستخدام ما يلي:
    
  - **CORP\\ User1** للاسم
    
  - كلمة المرور لحساب User1
    
    من المفترض أن ترى Microsoft Office **الصفحة** الرئيسية.
    
يوضح هذا الإجراء أن اشتراكك التجريبي متكاتف مع مجال AD DS corp.contoso.com استضافة على DC1. فيما يلي أساسيات عملية المصادقة:
  
1. عند استخدام المجال المتحدة الذي أنشأته في المرحلة 1 ضمن اسم حساب تسجيل الدخول، يعيد Microsoft 365 توجيه المستعرض إلى FQDN و PROXY1 لخدمة الاتحاد.
    
2. يرسل PROXY1 إلى الكمبيوتر المحلي صفحة تسجيل الدخول الخيالية للشركة.
    
3. عند إرسال CORPUser1\\ وكلمة المرور إلى PROXY1، فإنه سيرسلها إلى ADFS1.
    
4. يتحقق ADFS1 من صحة CORPUser1\\ وكلمة المرور باستخدام DC1 ويرسل رمز أمان مميزا إلى الكمبيوتر المحلي.
    
5. يرسل الكمبيوتر المحلي رمز الأمان المميز Microsoft 365.
    
6. Microsoft 365 التحقق من أن رمز الأمان المميز تم إنشاؤه بواسطة ADFS1 ويسمح بالوصول.
    
تم الآن تكوين اشتراكك التجريبي باستخدام المصادقة الخارجية. يمكنك استخدام بيئة dev/test هذه لسيناريوهات المصادقة المتقدمة.
  
## <a name="next-step"></a>الخطوة التالية

عندما تكون جاهزا لنشر المصادقة المتحدة الجاهزة للإنتاج والمتوفرة بشكل عال ل Microsoft 365 Azure، راجع نشر المصادقة المتحدة عالية التوفر Microsoft 365 [Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
