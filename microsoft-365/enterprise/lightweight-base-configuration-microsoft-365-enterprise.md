---
title: تكوين أساس خفيف
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
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
- admindeeplinkMAC
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: استخدم دليل Test Lab هذا لإنشاء بيئة اختبار خفيفة لاختبار Microsoft 365 للمؤسسة.
ms.openlocfilehash: 742fc93b64d2e3c1d858931eb7dbc591ebcd8e9d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63566076"
---
# <a name="the-lightweight-base-configuration"></a>تكوين الأساس الخفيف

*يمكن استخدام دليل Test Lab هذا Microsoft 365 لبيئات الاختبار Office 365 Enterprise المؤسسة.*

تصف هذه المقالة كيفية إنشاء بيئة مبسطة باستخدام اشتراك Microsoft 365 E5 كمبيوتر يعمل Windows 10 Enterprise.

![بيئة اختبار Microsoft 3656 Enterprise الخفيفة.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

يتضمن إنشاء بيئة اختبار خفيفة خمس مراحل:
- [المرحلة 1: إنشاء Microsoft 365 E5 اشتراكك](#phase-1-create-your-microsoft-365-e5-subscription)
- [المرحلة 2: تكوين اشتراكك التجريبي Office 365 الإصدار التجريبي](#phase-2-configure-your-office-365-trial-subscription)
- [المرحلة 3: إضافة اشتراك تجريبي Microsoft 365 E5 الإصدار التجريبي](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [المرحلة 4: إنشاء Windows 10 Enterprise كمبيوتر](#phase-4-create-a-windows-10-enterprise-computer)
- [المرحلة 5: الانضمام إلى Windows 10 إلى Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

استخدم البيئة الناتجة لاختبار ميزات وظائف Microsoft 365 [للمؤسسة](https://www.microsoft.com/microsoft-365/enterprise).

![اختبار دليل المعمل لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> للحصول على خريطة مرئية لكل المقالات في Microsoft 365 دليل اختبار المؤسسة، راجع Microsoft 365 دليل اختبار [المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>قد ترغب في طباعة هذه المقالة لتسجيل المعلومات المحددة التي ستحتاج إليها لهذه البيئة على مدار 30 يوما من الاشتراك التجريبي Office 365 الإصدار التجريبي. يمكنك بسهولة تمديد الاشتراك في التعقب لمدة 30 يوما أخرى. لبيئة اختبار دائمة، أنشئ اشتراكا مدفوعا جديدا باستخدام مستأجر Azure AD منفصل وعدد صغير من التراخيص.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>المرحلة 1: إنشاء Microsoft 365 E5 اشتراكك

نبدأ باشتراك تجريبي Microsoft 365 E5 ثم Microsoft 365 E5 الاشتراك فيه.

>[!NOTE]
>نوصي بإنشاء اشتراك تجريبي Office 365 بحيث يكون لبيئة الاختبار مستأجر Azure AD منفصل عن أي اشتراكات مدفوعة لديك حاليا. يعني هذا الفصل أنه يمكنك إضافة المستخدمين والمجموعات وإزالتها في المستأجر الاختباري دون التأثير على اشتراكات الإنتاج.

لبدء اشتراكك Microsoft 365 E5 التجريبي، ستحتاج أولا إلى اسم شركة وهمية إلى حساب Microsoft جديد.
  
1. نوصي باستخدام متغير من اسم الشركة Contoso لاسم شركتك، وهو شركة وهمية تستخدم في محتوى عينة Microsoft، ولكنها غير مطلوبة. سجل اسم شركتك الوهمية هنا: ![السطر.](../media/Common-Images/TableLine.png)
    
2. التسجيل للحصول على حساب Microsoft جديد [https://outlook.com](https://outlook.com) ، انتقل إلى حساب وأنشئه باستخدام حساب بريد إلكتروني وعنوان جديدين. سوف تستخدم هذا الحساب التسجيل للحصول على Office 365.
    
    - سجل الاسم الأول واسم العائلة لحسابك الجديد هنا: ![السطر.](../media/Common-Images/TableLine.png)
    
    - سجل عنوان حساب البريد الإلكتروني الجديد هنا: ![السطر.](../media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>التسجيل للحصول على اشتراك تجريبي Office 365 E5 الإصدار التجريبي

1. في المستعرض، انتقل إلى [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. في الخطوة 1 من صفحة شكرا **لاختيارك Office 365 E5**، أدخل عنوان حساب بريدك الإلكتروني الجديد.
3. في الخطوة 2 من عملية الاشتراك في التعقب، أدخل المعلومات المطلوبة، ثم قم بإجراء التحقق.
4. في الخطوة 3، أدخل اسم المؤسسة ثم اسم حساب سيكون المسؤول العام للاشتراك.
5. للخطوة 4، سجل صفحة تسجيل الدخول هنا (تحديد ونسخ): ![السطر.](../media/Common-Images/TableLine.png)
6. سجل اسم المستخدم هنا: ![السطر.](../media/Common-Images/TableLine.png). onmicrosoft.com  
   سجل كلمة المرور التي أدخلتها في موقع آمن.
   وستشار إلى هذه القيمة باسم **المسؤول العام**.
7. حدد **الانتقال إلى الإعداد**.
8. في Office 365 E5 الإعداد، حدد متابعة استخدام ***مؤسستك.onmicrosoft.com*** للبريد الإلكتروني، ثم حدد إنهاء **وتابع لاحقا**.

يجب أن ترى مركز مسؤولي Microsoft 365.
    
## <a name="phase-2-configure-your-office-365-trial-subscription"></a>المرحلة 2: تكوين اشتراكك التجريبي Office 365 الإصدار التجريبي

في هذه المرحلة، يمكنك تكوين اشتراكك مع مستخدمين إضافيين وتعيين Office 365 E5 جديدة.
  
للاتصال باشتراكك باستخدام وحدة Azure Active Directory PowerShell النمطية ل Graph من الكمبيوتر، استخدم الإرشادات الموجودة في الاتصال Microsoft 365 [PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
    
في مربع **Windows PowerShell** طلب بيانات الاعتماد، أدخل اسم المسؤول العام (على سبيل المثال، *jdoe@contosotoycompany.onmicrosoft.com)* وكلمة المرور.
  
قم بتعبئة اسم مؤسستك (على سبيل المثال *، contosotoycompany*)، رمز البلد من حرفين لموقعك، وكلمة مرور الحساب الشائعة، ثم قم بتشغيل الأوامر التالية من مطالبة PowerShell:

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License

for($i=2;$i -le 4; $i++) {
    $userUPN= "user$($i)@$($orgName).onmicrosoft.com"
    New-AzureADUser -DisplayName "User $($i)" -GivenName User -SurName $i -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user$($i)"
    $userObjectID = (Get-AzureADUser -SearchString $userupn).ObjectID
    Set-AzureADUserLicense -ObjectId $userObjectID -AssignedLicenses $LicensesToAssign
}
```
> [!NOTE]
> استخدام كلمة مرور شائعة هنا هو للتشغيل التلقائي وسهولة التكوين لبيئة اختبار. ومن الواضح أن هذا الأمر لا يشجع كثيرا على اشتراكات الإنتاج. 

### <a name="record-key-information-for-future-reference"></a>تسجيل معلومات المفتاح للمرجع المستقبلي

إذا لم تكن قد سجلت هذه القيم بعد، فسجلها الآن:
  
- اسم المسؤول العام: ![السطر.](../media/Common-Images/TableLine.png).onmicrosoft.com (من الخطوة 6 من المرحلة 1)
    
    سجل أيضا كلمة المرور لهذا الحساب في موقع آمن.
    
- اسم مؤسسة اشتراكك التجريبي: ![السطر.](../media/Common-Images/TableLine.png) (من الخطوة 4 من المرحلة 1)
    
- لتضمين حسابات المستخدم 2 والمستخدم 3 والمستخدم 4 والمستخدم 5، تشغيل الأمر التالي من Windows وحدة Azure Active Directory النمطية Windows PowerShell موجه:
    
  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    سجل أسماء الحسابات هنا:
    
  - اسم حساب المستخدم 2: user2 @![السطر.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - اسم حساب المستخدم 3: user3 @![السطر.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - اسم حساب المستخدم 4: user4 @![السطر.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - اسم حساب المستخدم 5: user5 @![السطر.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
    سجل أيضا كلمة المرور الشائعة لهذه الحسابات في موقع آمن.
   
### <a name="using-an-office-365-test-environment"></a>استخدام Office 365 اختبارية

إذا كنت بحاجة إلى بيئة اختبار Office 365 فقط، لست بحاجة إلى قراءة ما تبقى من هذه المقالة.

للحصول على أدلة اختبار معمل إضافية تنطبق على كل من Office 365 Microsoft 365، راجع Microsoft 365 دليل [اختبار المؤسسة](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>المرحلة 3: إضافة اشتراك تجريبي Microsoft 365 E5 الإصدار التجريبي

في هذه المرحلة، يمكنك التسجيل للحصول على Microsoft 365 E5 التجريبي وإضافته إلى المؤسسة نفسها مثل اشتراكك التجريبي Office 365 E5 الإصدار التجريبي.
  
أولا، قم بإضافة Microsoft 365 E5 الإصدار التجريبي وتعيين Microsoft 365 جديد لحساب المسؤول العام.
  
1. في نافذة خاصة في مستعرض الإنترنت، استخدم بيانات اعتماد حساب المسؤول العام لتسجيل الدخول إلى مركز مسؤولي Microsoft 365 في [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. في صفحة **مركز مسؤولي Microsoft 365**، في التنقل الأيسر، حدد **خدمات BillingPurchase** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank"></a>
    
3. في صفحة **خدمات الشراء****، حدد Microsoft 365 E5**، ثم حدد **الحصول على الإصدار التجريبي المجاني**.

4. على الصفحة **Microsoft 365 E5** التجريبي، قرر تلقي رسالة نصية أو مكالمة هاتفية، وأدخل رقم هاتفك، **ثم حدد إرسال** رسالة نصية إلي أو **الاتصال بي**. تنفيذ عملية التحقق.

5. في الصفحة **تأكيد طلبك** ، حدد **تجربة الآن**.

6. في صفحة **إيصال الطلب** ، حدد **متابعة**.

7. في مركز مسؤولي Microsoft 365، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users.

8. في **المستخدمون النشطون**، حدد حساب المسؤول.

9. حدد **التراخيص والتطبيقات**.

10. قم بتعطيل ترخيص Office 365 Enterprise E5 وتمكين الترخيص Microsoft 365 E5.

11. حدد **حفظ التغييرات**، ثم أغلق جزء معلومات حساب المستخدم.

بعد ذلك، كرر الخطوات من 8 إلى 11 من الإجراء السابق لكل الحسابات الأخرى (المستخدم 2 والمستخدم 3 والمستخدم 4 والمستخدم 5).
  
> [!NOTE]
> طول الاشتراك التجريبي Microsoft 365 E5 30 يوما. لبيئة اختبار دائمة، حول هذا الاشتراك التجريبي إلى اشتراك مدفوع بعدد صغير من التراخيص.
  
لقد أصبحت بيئة الاختبار لديك الآن:
  
- اشتراك Microsoft 365 E5 تجريبي.
- يتم تمكين جميع حسابات المستخدمين المناسبة (إما فقط المسؤول العام أو جميع حسابات المستخدمين الخمسة) لاستخدام Microsoft 365 E5.
    
يبدو التكوين الناتج، الذي يضيف Microsoft 365 E5، كما يلي:
  
![المرحلة 3 من بيئة اختبار Microsoft 3656 Enterprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>المرحلة 4: إنشاء Windows 10 Enterprise كمبيوتر

في هذه المرحلة، يمكنك إنشاء كمبيوتر مستقل يعمل Windows 10 Enterprise كمبيوتر فعلي أو جهاز ظاهري أو جهاز Azure ظاهري.
  
### <a name="physical-computer"></a>الكمبيوتر الفعلي

على كمبيوتر شخصي، قم بتثبيت Windows 10 Enterprise. يمكنك تنزيل الإصدار التجريبي Windows 10 Enterprise [هنا](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine"></a>الجهاز الظاهري

استخدم الظاهر التشعبي الذي تختاره لإنشاء جهاز ظاهري، ثم Windows 10 Enterprise عليه. يمكنك تنزيل الإصدار التجريبي Windows 10 Enterprise [هنا](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).
  
### <a name="virtual-machine-in-azure"></a>جهاز ظاهري في Azure

لإنشاء جهاز Windows 10 ظاهري في Microsoft Azure، يجب أن يكون لديك اشتراك مستند إلى Visual Studio، والذي لديه حق الوصول إلى الصورة Windows 10 Enterprise. لا تملك أنواع أخرى من اشتراكات Azure، مثل الاشتراكات التجريبية والمدفعة، إمكانية الوصول إلى هذه الصورة. للحصول على أحدث المعلومات، راجع [استخدام Windows في Azure لسيناريوهات dev/test](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية الإصدار الأخير من Azure PowerShell. راجع [بدء العمل باستخدام Azure PowerShell cmdlets](/powershell/azureps-cmdlets-docs/). تقوم مجموعات الأوامر هذه Windows 10 Enterprise ظاهري باسم WIN10 وكل البنية الأساسية المطلوبة، بما في ذلك مجموعة موارد، حساب تخزين، وشبكة ظاهرية. إذا كنت ملما بالفعل باستخدام خدمات البنية الأساسية في Azure، فتكيف مع هذه الإرشادات لتتناسب مع البنية الأساسية التي تم نشرها حاليا.
  
أولا، ابدأ موجه Microsoft PowerShell.
  
سجل الدخول إلى حساب Azure باستخدام هذا الأمر.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام هذا الأمر.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

تعيين اشتراكك في Azure. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف \< and > ، بالاسم الصحيح.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

بعد ذلك، أنشئ مجموعة موارد جديدة. لتحديد اسم مجموعة موارد فريدة، استخدم هذا الأمر لتضمين مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

أنشئ مجموعة الموارد الجديدة باستخدام هذه الأوامر. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف \< and > ، بالأسماء الصحيحة.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، أنشئ شبكة ظاهرية جديدة والآلة الظاهرية WIN10 باستخدام هذه الأوامر. عند مطالبتك بذلك، قم بتوفير اسم وكلمة المرور لحساب المسؤول المحلي ل WIN10 وتخزينها في موقع آمن.
  
```powershell
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
$pip=New-AzPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName WIN10 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>المرحلة 5: الانضمام إلى Windows 10 إلى Azure AD

بعد إنشاء الجهاز الفعلي أو الظاهري Windows 10 Enterprise، سجل الدخول باستخدام حساب مسؤول محلي.
  
> [!NOTE]
> بالنسبة إلى جهاز ظاهري في Azure، استخدم  [هذه الإرشادات](/azure/virtual-machines/windows/connect-logon) للاتصال به.
  
بعد ذلك، انضم إلى كمبيوتر WIN10 إلى مستأجر Azure AD الخاص Microsoft 365 E5 اشتراكك.
  
1. على سطح المكتب للكمبيوتر WIN10، حدد بدء > الإعدادات > **الحسابات > الوصول إلى > الاتصال**.
    
2. في **مربع الحوار إعداد حساب** العمل أو المدرسة، حدد **الانضمام إلى هذا الجهاز إلى Azure Active Directory**.
    
3. في **حساب العمل أو المدرسة**، أدخل اسم حساب المسؤول العام لاشتراكك في Microsoft 365 E5، ثم حدد **التالي**.
    
4. في **إدخال كلمة المرور**، أدخل كلمة المرور لحساب المسؤول العام، ثم حدد **تسجيل الدخول**.
    
5. عند مطالبتك بالتأكد من أن هذه هي مؤسستك، حدد **انضمام**، ثم حدد **تم**.
    
6. أغلق نافذة الإعدادات.
    
بعد ذلك، Microsoft 365 Apps for enterprise على كمبيوتر WIN10:
  
1. افتح Microsoft Edge ثم سجل الدخول إلى [مركز مسؤولي Microsoft 365 بيانات اعتماد](https://admin.microsoft.com) حساب المسؤول العام.
    
2. على علامة **Microsoft Office الصفحة الرئيسية**، حدد **تثبيت Office**.
    
3. عند مطالبتك بما يجب فعله، حدد **تشغيل**، ثم حدد **نعم** للتحكم **في حساب المستخدم**.
    
4. انتظر حتى Office إكمال تثبيته. عندما ترى **أنت كل شيء تم تعيينه!**، حدد **إغلاق** مرتين.
    
تبدو بيئتك الناتجة كما يلي:

![المرحلة 5 من بيئة اختبار Microsoft 3656 Enterprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

يشمل ذلك كمبيوتر WIN10 الذي يحتوي على:

- انضم إلى مستأجر Azure AD الخاص Microsoft 365 E5 اشتراكك.
- مسجل ك جهاز Azure AD في Microsoft Intune (EMS).
- Microsoft 365 Apps for enterprise مثبتا.
  
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
