---
title: هوية موحدة لبيئة اختبار Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'ملخص: تكوين المصادقة الموحدة لبيئة اختبار Microsoft 365.'
ms.openlocfilehash: 0214c7778176641c6446106cf92ed173b81b71de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101018"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>هوية موحدة لبيئة اختبار Microsoft 365

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

يدعم Microsoft 365 الهوية المتحدة. وهذا يعني أنه بدلا من إجراء التحقق من صحة بيانات الاعتماد نفسها، Microsoft 365 يشير المستخدم المتصل إلى خادم مصادقة موحد Microsoft 365 يثق به. إذا كانت بيانات اعتماد المستخدم صحيحة، يصدر خادم المصادقة المتحدة رمز أمان مميزا يرسله العميل بعد ذلك إلى Microsoft 365 كدليل على المصادقة. تسمح الهوية الموحدة بإلغاء تحميل المصادقة وتوسيع نطاقها لاشتراك Microsoft 365 وسيناريوهات المصادقة والأمان المتقدمة.
  
تصف هذه المقالة كيفية تكوين المصادقة الموحدة لبيئة اختبار Microsoft 365، مما يؤدي إلى ما يلي:

![المصادقة الموحدة لبيئة اختبار Microsoft 365.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
يتكون هذا التكوين من:
  
- اشتراك تجريبي أو إنتاج Microsoft 365 E5.
    
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من خمسة أجهزة ظاهرية على شبكة فرعية لشبكة Azure الظاهرية (DC1 وAPP1 و CLIENT1 و ADFS1 و PROXY1). يتم تشغيل الاتصال Azure AD على APP1 لمزامنة قائمة الحسابات في مجال خدمات مجال Active Directory إلى Microsoft 365. يتلقى PROXY1 طلبات المصادقة الواردة. يتحقق ADFS1 من صحة بيانات الاعتماد باستخدام DC1 ويصدر الرموز المميزة للأمان.
    
يتضمن إعداد بيئة الاختبار هذه خمس مراحل:
- [المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [المرحلة 2: إنشاء خادم AD FS](#phase-2-create-the-ad-fs-server)
- [المرحلة 3: إنشاء خادم وكيل الويب](#phase-3-create-the-web-proxy-server)
- [المرحلة 4: إنشاء شهادة موقعة ذاتيا وتكوين ADFS1 و PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [المرحلة 5: تكوين Microsoft 365 للهوية الموحدة](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> لا يمكنك تكوين بيئة الاختبار هذه مع اشتراك Azure Trial.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>المرحلة 1: تكوين مزامنة تجزئة كلمة المرور لبيئة اختبار Microsoft 365

اتبع الإرشادات في [مزامنة تجزئة كلمة المرور Microsoft 365](password-hash-sync-m365-ent-test-environment.md). يبدو التكوين الناتج كما يلي:
  
![المؤسسة المحاكاة مع بيئة اختبار مزامنة تجزئة كلمة المرور.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
يتكون هذا التكوين من:
  
- اشتراكات تجريبية أو مدفوعة Microsoft 365 E5.
- إنترانت مؤسسة مبسطة متصلة بالإنترنت، تتكون من أجهزة DC1 وAPP1 و CLIENT1 الظاهرية على شبكة فرعية لشبكة Azure الظاهرية. يتم تشغيل الاتصال Azure AD على APP1 لمزامنة مجال خدمات مجال ACTIVE DIRECTORY TESTLAB (AD DS) مع مستأجر Azure AD لاشتراكات Microsoft 365 بشكل دوري.

## <a name="phase-2-create-the-ad-fs-server"></a>المرحلة 2: إنشاء خادم AD FS

يوفر خادم AD FS مصادقة موحدة بين Microsoft 365 والحسابات في مجال corp.contoso.com المستضاف على DC1.
  
لإنشاء جهاز ظاهري Azure ل ADFS1، املأ اسم اشتراكك ومجموعة الموارد وموقع Azure لتكوينك الأساسي، ثم قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
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

بعد ذلك، استخدم [مدخل Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري ADFS1 باستخدام اسم حساب مسؤول ADFS1 المحلي وكلمة المرور، ثم افتح موجه أوامر Windows PowerShell.
  
للتحقق من تحليل الاسم واتصال الشبكة بين ADFS1 و DC1، قم بتشغيل الأمر **dc1.corp.contoso.com ping** وتحقق من وجود أربعة ردود.
  
بعد ذلك، قم بضم الجهاز الظاهري ADFS1 إلى مجال CORP باستخدام هذه الأوامر في موجه Windows PowerShell على ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

يبدو التكوين الناتج كما يلي:
  
![تمت إضافة خادم AD FS إلى DirSync لبيئة اختبار Microsoft 365.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>المرحلة 3: إنشاء خادم وكيل الويب

يوفر PROXY1 وكيلا لرسائل المصادقة بين المستخدمين الذين يحاولون المصادقة و ADFS1.
  
لإنشاء جهاز ظاهري من Azure ل PROXY1، قم بتعبئة اسم مجموعة الموارد وموقع Azure، ثم قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
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
> يتم تعيين عنوان IP عام ثابت ل PROXY1 لأنك ستقوم بإنشاء سجل DNS عام يشير إليه ويجب ألا يتغير عند إعادة تشغيل الجهاز الظاهري PROXY1.
  
بعد ذلك، أضف قاعدة إلى مجموعة أمان الشبكة للشبكة الفرعية CorpNet للسماح بنسبة استخدام الشبكة الواردة غير المطلوبة من الإنترنت إلى عنوان IP الخاص PROXY1 ومنفذ TCP 443. قم بتشغيل هذه الأوامر في موجه أوامر Azure PowerShell على الكمبيوتر المحلي.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

بعد ذلك، استخدم [مدخل Microsoft Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري PROXY1 باستخدام اسم حساب المسؤول المحلي PROXY1 وكلمة المرور، ثم افتح موجه أوامر Windows PowerShell على PROXY1.
  
للتحقق من تحليل الاسم والاتصال بالشبكة بين PROXY1 و DC1، قم بتشغيل الأمر **dc1.corp.contoso.com ping** وتحقق من وجود أربعة ردود.
  
بعد ذلك، قم بضم الجهاز الظاهري PROXY1 إلى مجال CORP باستخدام هذه الأوامر في موجه Windows PowerShell على PROXY1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

عرض عنوان IP العام ل PROXY1 مع أوامر Azure PowerShell هذه على الكمبيوتر المحلي.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

بعد ذلك، العمل مع موفر DNS العام وإنشاء سجل DNS A عام جديد ل **fs.testlab.**\<*your DNS domain name*> الذي يتم حله إلى عنوان IP المعروض بواسطة الأمر **"Write-Host** ". **fs.testlab.**\<*your DNS domain name*> يشار إليها فيما بعد باسم  *FQDN لخدمة الاتحاد*.
  
بعد ذلك، استخدم [مدخل Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري DC1 باستخدام بيانات اعتماد CORPUser1\\، ثم قم بتشغيل الأوامر التالية في موجه الأوامر Windows PowerShell على مستوى المسؤول:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
تقوم هذه الأوامر بإنشاء سجل DNS A داخلي بحيث يمكن للأجهزة الظاهرية على شبكة Azure الظاهرية حل FQDN لخدمة الاتحاد الداخلي إلى عنوان IP الخاص ل ADFS1.
  
يبدو التكوين الناتج كما يلي:
  
![تمت إضافة خادم وكيل تطبيق الويب إلى DirSync لبيئة اختبار Microsoft 365.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>المرحلة 4: إنشاء شهادة موقعة ذاتيا وتكوين ADFS1 و PROXY1

في هذه المرحلة، يمكنك إنشاء شهادة رقمية موقعة ذاتيا لخدمة الاتحاد FQDN وتكوين ADFS1 و PROXY1 كمزرعة AD FS.
  
أولا، استخدم [مدخل Microsoft Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري DC1 باستخدام بيانات اعتماد CORPUser1\\، ثم افتح موجه أوامر Windows PowerShell على مستوى المسؤول.
  
بعد ذلك، قم بإنشاء حساب خدمة AD FS مع هذا الأمر في موجه الأوامر Windows PowerShell على DC1:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
لاحظ أن هذا الأمر يطالبك بتوفير كلمة مرور الحساب. اختر كلمة مرور قوية وسجلها في موقع آمن. ستحتاج إليها لهذه المرحلة وبالنسبة للمرحلة 5.
  
استخدم [مدخل Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري ADFS1 باستخدام بيانات اعتماد CORPUser1\\. افتح موجه أوامر Windows PowerShell على مستوى المسؤول على ADFS1، وقم بتعبئة FQDN لخدمة الاتحاد، ثم قم بتشغيل هذه الأوامر لإنشاء شهادة موقعة ذاتيا:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

بعد ذلك، استخدم هذه الخطوات لحفظ الشهادة الموقعة ذاتيا الجديدة كملف.
  
1. حدد **"ابدأ**"، وأدخل **mmc.exe**، ثم اضغط على **مفتاح الإدخال Enter**.
    
2. حدد **FileAdd** > **/Remove Snap-in**.
    
3. في **إضافة الوظائف الإضافية أو إزالتها**، انقر نقرا مزدوجا فوق **"الشهادات"** في قائمة الوظائف الإضافية المتوفرة، وحدد **حساب الكمبيوتر**، ثم حدد **"التالي**".
    
4. **في "تحديد الكمبيوتر**"، حدد **"إنهاء**"، ثم حدد **"موافق**".
    
5. في جزء الشجرة، افتح **الشهادات (الكمبيوتر المحلي) > شهادات > الشخصية**.
    
6. حدد واحتفظ (أو انقر بزر الماوس الأيمن) بالشهادة باستخدام FQDN لخدمة الاتحاد، وحدد **كافة المهام**، ثم حدد **"تصدير**".
    
7. في صفحة **الترحيب** ، حدد **"التالي**".
    
8. في الصفحة **"تصدير مفتاح خاص** "، حدد **"نعم**"، ثم حدد **"التالي**".
    
9. في الصفحة **"تصدير تنسيق الملف** "، حدد **"تصدير كافة الخصائص الموسعة**"، ثم حدد **"التالي**".
    
10. في صفحة **الأمان** ، حدد **كلمة المرور** وأدخل كلمة مرور في **كلمة المرور** **وتأكد من كلمة المرور.**
    
11. في الصفحة **"ملف للتصدير** "، حدد **"استعراض**".
    
12. استعرض وصولا إلى مجلد **C:\\Certs** ، وأدخل **SSL** **في اسم الملف**، ثم حدد **"حفظ".**
    
13. في الصفحة **"ملف للتصدير** "، حدد **"التالي**".
    
14. في صفحة **"إكمال معالج تصدير الشهادة** "، حدد **"إنهاء**". عند المطالبة، حدد **"موافق**".
    
بعد ذلك، قم بتثبيت خدمة AD FS مع هذا الأمر في موجه الأوامر Windows PowerShell على ADFS1:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

انتظر حتى يكتمل التثبيت.
  
بعد ذلك، قم بتكوين خدمة AD FS باستخدام الخطوات التالية:
  
1. حدد **البدء**، ثم حدد أيقونة **Server Manager** .
    
2. في جزء شجرة Server Manager، حدد **AD FS**.
    
3. في شريط الأدوات في الأعلى، حدد رمز التحذير البرتقالي، ثم حدد **تكوين خدمة الاتحاد على هذا الخادم**.
    
4. في صفحة **الترحيب** في معالج تكوين خدمات الأمان المشترك لـ Active Directory، حدد **"التالي**".
    
5. في صفحة **الاتصال إلى AD DS**، حدد **"التالي**".
    
6. في الصفحة **"تحديد خصائص الخدمة** ":
    
  - بالنسبة **لشهادة SSL**، حدد السهم لأسفل، ثم حدد الشهادة التي تحمل اسم FQDN لخدمة الاتحاد.
    
  - في **اسم عرض خدمة الاتحاد**، أدخل اسم مؤسستك الخيالية.
    
  - حدد **التالي**.
    
7. في صفحة **"تحديد حساب الخدمة** "، حدد **"تحديد** **لاسم الحساب**".
    
8. في **تحديد حساب المستخدم أو الخدمة**، أدخل **ADFS-Service**، وحدد **"التحقق من الأسماء**"، ثم حدد **"موافق**".
    
9. في **كلمة مرور الحساب**، أدخل كلمة المرور لحساب ADFS-Service، ثم حدد **"التالي**".
    
10. في صفحة **"تحديد قاعدة بيانات التكوين** "، حدد **"التالي**".
    
11. في الصفحة **"خيارات المراجعة** "، حدد **"التالي**".
    
12. في صفحة **"التحقق من المتطلبات الأساسية** "، حدد **"Configure**".

13. في صفحة **النتائج** ، حدد **"إغلاق**".
    
14. حدد **"ابدأ**"، وحدد أيقونة الطاقة، وحدد **"إعادة التشغيل**"، ثم حدد **"متابعة**".
    
من [مدخل Microsoft Azure](https://portal.azure.com)، اتصل ب PROXY1 باستخدام بيانات اعتماد حساب CORPUser1\\.
  
بعد ذلك، استخدم هذه الخطوات لتثبيت الشهادة الموقعة ذاتيا على **كل من PROXY1 وAPP1**.
  
1. حدد **"ابدأ**"، وأدخل **mmc.exe**، ثم اضغط على **مفتاح الإدخال Enter**.
    
2. حدد **ملف > إضافة/إزالة انطباق**.
    
3. في **إضافة الوظائف الإضافية أو إزالتها**، انقر نقرا مزدوجا فوق **"الشهادات"** في قائمة الوظائف الإضافية المتوفرة، وحدد **حساب الكمبيوتر**، ثم حدد **"التالي**".
    
4. **في "تحديد الكمبيوتر**"، حدد **"إنهاء**"، ثم حدد **"موافق**".
    
5. في جزء الشجرة، افتح **Certificates (Local Computer)** > **PersonalCertificates** > .
    
6. حدد " **Personal**" (أو انقر بزر الماوس الأيمن) مع الاستمرار، وحدد **"كافة المهام**"، ثم حدد **"استيراد**".
    
7. في صفحة **الترحيب** ، حدد **"التالي**".
    
8. في الصفحة **"ملف لاستيراد**"، أدخل **\\\\adfs1certssl.pfx\\\\**، ثم حدد **"التالي**".
    
9. في صفحة **حماية المفتاح الخاص** ، أدخل كلمة مرور الشهادة في **كلمة المرور**، ثم حدد **"التالي".**
    
10. في صفحة **مخزن الشهادات** ، حدد **"التالي".**
    
11. في الصفحة **"إكمال"** ، حدد **"إنهاء**".
    
12. في صفحة **مخزن الشهادات** ، حدد **"التالي**".
    
13. عند المطالبة، حدد **"موافق**".
    
14. في جزء الشجرة، حدد **"Certificates**".
    
15. حدد الشهادة واحتفظ بها (أو انقر بزر الماوس الأيمن فوقها)، ثم حدد **"نسخ**".
    
16. في جزء الشجرة، افتح **Trusted Root Certification** AuthoritiesCertificates > .
    
17. حرك مؤشر الماوس أسفل قائمة الشهادات المثبتة، وحدد باستمرار (أو انقر بزر الماوس الأيمن)، ثم حدد **"لصق".**
    
افتح موجه أوامر PowerShell على مستوى المسؤول وقم بتشغيل الأمر التالي:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

انتظر حتى يكتمل التثبيت.
  
استخدم هذه الخطوات لتكوين خدمة وكيل تطبيق الويب لاستخدام ADFS1 كخادم اتحادي خاص به:
  
1. حدد **البدء**، ثم حدد **Server Manager**.
    
2. في جزء الشجرة، حدد **Remote Access**.
    
3. في شريط الأدوات في الأعلى، حدد رمز التحذير البرتقالي، ثم حدد **"فتح معالج وكيل تطبيق ويب**".
    
4. في صفحة **الترحيب** الخاصة بمعالج تكوين وكيل تطبيق ويب، حدد **"التالي**".
    
5. في صفحة **خادم الاتحاد** :
    
  - في مربع **اسم خدمة الاتحاد** ، أدخل FQDN لخدمة الاتحاد.
    
  - في مربع **اسم المستخدم**، أدخل **CORPUser1\\**.
    
  - في المربع **"كلمة المرور** "، أدخل كلمة المرور لحساب User1.
    
  - حدد **التالي**.
    
6. في صفحة **شهادة وكيل AD FS** ، حدد السهم لأسفل، وحدد الشهادة باستخدام FQDN لخدمة الاتحاد، ثم حدد **"التالي**".
    
7. في صفحة **التأكيد** ، حدد **Configure**.
    
8. في صفحة **النتائج** ، حدد **"إغلاق**".
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>المرحلة 5: تكوين Microsoft 365 للهوية الموحدة

استخدم [مدخل Microsoft Azure](https://portal.azure.com) للاتصال بالجهاز الظاهري APP1 باستخدام بيانات اعتماد حساب CORPUser1\\.
  
استخدم هذه الخطوات لتكوين الاتصال Azure AD واشتراكك Microsoft 365 للمصادقة الموحدة:
  
1. من سطح المكتب، انقر نقرا مزدوجا فوق **الاتصال Azure AD**.
    
2. في صفحة **"Welcome to Azure AD الاتصال**"، حدد **"Configure**".
    
3. في صفحة **"المهام الإضافية** "، حدد **"تغيير تسجيل دخول المستخدم**"، ثم حدد **"التالي**".
    
4. في **الاتصال إلى صفحة Azure AD**، أدخل اسم حساب المسؤول العام وكلمة المرور، ثم حدد **"التالي**".
    
5. في صفحة **تسجيل دخول المستخدم** ، حدد **"Federation with AD FS**"، ثم حدد **"التالي**".
    
6. في صفحة **مزرعة AD FS** ، حدد **"استخدام مزرعة AD FS" موجودة**، وأدخل **ADFS1** في المربع **"اسم الخادم** "، ثم حدد **"التالي**".
    
7. عند مطالبتك ببيانات اعتماد الخادم، أدخل بيانات اعتماد حساب CORPUser1\\، ثم حدد **"موافق**".
    
8. في صفحة بيانات اعتماد **مسؤول المجال**، أدخل **CORPUser1\\** في مربع **اسم المستخدم**، وأدخل كلمة مرور الحساب في المربع **"كلمة المرور**"، ثم حدد **"التالي**".
    
9. في صفحة **حساب خدمة AD FS**، أدخل **CORPADFS-Service\\** في مربع **اسم المستخدم للمجال**، وأدخل كلمة مرور الحساب في المربع **"كلمة مرور مستخدم المجال**"، ثم حدد **"التالي**".
    
10. في صفحة **مجال Azure AD** ، في **المجال**، حدد اسم المجال الذي أنشأته مسبقا وأضفته إلى اشتراكك في المرحلة 1، ثم حدد **"التالي**".
    
11. في الصفحة **"جاهز للتكوين"** ، حدد **"Configure**".
    
12. في الصفحة **"اكتمال التثبيت**"، حدد **"التحقق".**
    
    يجب أن تشاهد رسائل تشير إلى أنه تم التحقق من كل من تكوين الإنترانت والإنترنت.
    
13. في الصفحة **"اكتمال التثبيت** "، حدد **"إنهاء**".
    
لإثبات أن المصادقة الموحدة تعمل:
  
1. افتح مثيلا خاصا جديدا للمستعرض على الكمبيوتر المحلي وانتقل إلى [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. للحصول على بيانات اعتماد تسجيل الدخول، أدخل **user1@**\<*the domain created in Phase 1*>.
    
    على سبيل المثال، إذا كان مجال الاختبار **الخاص بك testlab.contoso.com**، يمكنك إدخال "user1@testlab.contoso.com". اضغط على المفتاح **Tab** أو اسمح Microsoft 365 بإعادة توجيهك تلقائيا.
    
    يجب أن ترى الآن **أن اتصالك ليس صفحة خاصة** . ترى ذلك لأنك قمت بتثبيت شهادة موقعة ذاتيا على ADFS1 لا يمكن لكمبيوتر سطح المكتب التحقق من صحتها. في نشر إنتاج المصادقة الموحدة، يمكنك استخدام شهادة من مرجع مصدق موثوق به ولن يرى المستخدمون هذه الصفحة.
    
3. في صفحة **الاتصال الخاصة بك ليست صفحة خاصة** ، حدد **"خيارات متقدمة**"، ثم حدد **"متابعة" إلى \<*your federation service FQDN*>**. 
    
4. في الصفحة التي تحمل اسم مؤسستك الخيالية، سجل الدخول باستخدام ما يلي:
    
  - **كورب\\ User1** للاسم
    
  - كلمة المرور لحساب User1
    
    يجب أن تشاهد الصفحة **الرئيسية Microsoft Office**.
    
يوضح هذا الإجراء أن اشتراكك التجريبي موحد مع مجال AD DS corp.contoso.com المستضاف على DC1. فيما يلي أساسيات عملية المصادقة:
  
1. عند استخدام المجال الموحد الذي أنشأته في المرحلة 1 ضمن اسم حساب تسجيل الدخول، Microsoft 365 إعادة توجيه المستعرض إلى FQDN و PROXY1 لخدمة الاتحاد.
    
2. يرسل PROXY1 إلى الكمبيوتر المحلي صفحة تسجيل الدخول الخيالية للشركة.
    
3. عند إرسال CORPUser1\\ وكلمة المرور إلى PROXY1، فإنه يعيد توجيهها إلى ADFS1.
    
4. يتحقق ADFS1 من صحة CORPUser1\\ وكلمة المرور باستخدام DC1 ويرسل رمز أمان مميزا إلى الكمبيوتر المحلي.
    
5. يرسل الكمبيوتر المحلي رمز الأمان المميز إلى Microsoft 365.
    
6. يتحقق Microsoft 365 من إنشاء الرمز المميز للأمان بواسطة ADFS1 ويسمح بالوصول.
    
تم الآن تكوين اشتراكك التجريبي باستخدام المصادقة الموحدة. يمكنك استخدام بيئة التطوير/الاختبار هذه لسيناريوهات المصادقة المتقدمة.
  
## <a name="next-step"></a>الخطوة التالية

عندما تكون مستعدا لنشر المصادقة الموحدة الجاهزة للإنتاج وعالية التوفر Microsoft 365 في Azure، راجع [نشر المصادقة الموحدة عالية التوفر Microsoft 365 في Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
