---
title: تكوين أساسي خفيف الوزن
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/17/2022
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
description: استخدم دليل مختبر الاختبار هذا لإنشاء بيئة اختبار خفيفة لاختبار Microsoft 365 للمؤسسة.
ms.openlocfilehash: fcfa3f67ec790244fc44f3539af8da1df7a09432
ms.sourcegitcommit: f645e0e9db74b25663cd9ddec7e3824d6ffc57f7
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/17/2022
ms.locfileid: "65444191"
---
# <a name="the-lightweight-base-configuration"></a>التكوين الأساسي الخفيف

*يمكن استخدام دليل مختبر الاختبار هذا لكل من Microsoft 365 لبيئات اختبار المؤسسة Office 365 Enterprise.*

تصف هذه المقالة كيفية إنشاء بيئة مبسطة باشتراك Microsoft 365 E5 وكمبيوتر يعمل Windows 10 Enterprise.

![بيئة اختبار Microsoft 3656 Enterprise خفيفة الوزن.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

يتضمن إنشاء بيئة اختبار خفيفة الوزن خمس مراحل:

- [المرحلة 1: إنشاء اشتراكك في Microsoft 365 E5](#phase-1-create-your-microsoft-365-e5-subscription)
- [المرحلة 2: تكوين اشتراكك التجريبي Office 365](#phase-2-configure-your-office-365-trial-subscription)
- [المرحلة 3: إضافة اشتراك تجريبي Microsoft 365 E5](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [المرحلة 4: إنشاء كمبيوتر Windows 10 Enterprise](#phase-4-create-a-windows-10-enterprise-computer)
- [المرحلة 5: الانضمام إلى الكمبيوتر Windows 10 Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

استخدم البيئة الناتجة لاختبار ميزات [ووظائف Microsoft 365 للمؤسسة](https://www.microsoft.com/microsoft-365/enterprise).

![اختبار دلائل المختبر لسحابة Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> للحصول على خريطة مرئية لجميع المقالات في Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة، راجع [Microsoft 365 لمكدس دليل مختبر اختبار المؤسسة](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>قد تحتاج إلى طباعة هذه المقالة لتسجيل المعلومات المحددة التي ستحتاجها لهذه البيئة على مدار 30 يوما من الاشتراك التجريبي Office 365. يمكنك بسهولة تمديد اشتراك المسار لمدة 30 يوما أخرى. للحصول على بيئة اختبار دائمة، قم بإنشاء اشتراك مدفوع جديد مع مستأجر Azure AD منفصل وعدد صغير من التراخيص.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>المرحلة 1: إنشاء اشتراكك في Microsoft 365 E5

نبدأ باشتراك تجريبي Microsoft 365 E5 ثم نضيف اشتراك Microsoft 365 E5 إليه.

>[!NOTE]
>نوصي بإنشاء اشتراك تجريبي Office 365 بحيث تحتوي بيئة الاختبار الخاصة بك على مستأجر Azure AD منفصل عن أي اشتراكات مدفوعة لديك حاليا. يعني هذا الفصل أنه يمكنك إضافة المستخدمين والمجموعات وإزالتها في مستأجر الاختبار دون التأثير على اشتراكات الإنتاج الخاصة بك.

لبدء اشتراكك التجريبي Microsoft 365 E5، تحتاج أولا إلى اسم شركة وهمي وحساب Microsoft جديد.
  
1. نوصي باستخدام متغير من اسم الشركة Contoso لاسم شركتك، وهي شركة وهمية تستخدم في نموذج محتوى Microsoft، ولكنها غير مطلوبة. سجل اسم شركتك الوهمية هنا: ![خط.](../media/Common-Images/TableLine.png)

2. للتسجيل للحصول على حساب Microsoft جديد، انتقل إلى [https://outlook.com](https://outlook.com) حساب باستخدام حساب بريد إلكتروني وعنوان جديدين وأنشئه. ستستخدم هذا الحساب للتسجيل للحصول على Office 365.

    - سجل الاسم الأول واسم العائلة لحسابك الجديد هنا: ![خط.](../media/Common-Images/TableLine.png)

    - سجل عنوان حساب البريد الإلكتروني الجديد هنا: ![خط.](../media/Common-Images/TableLine.png)@outlook.com

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>التسجيل للحصول على اشتراك تجريبي Office 365 E5

1. في المستعرض، انتقل إلى [https://aka.ms/e5trial](https://aka.ms/e5trial).

2. في الخطوة 1 من "**شكرا" لاختيارك صفحة Office 365 E5**، أدخل عنوان حساب بريدك الإلكتروني الجديد.
3. في الخطوة 2 من عملية اشتراك المسار، أدخل المعلومات المطلوبة، ثم قم بإجراء التحقق.
4. في الخطوة 3، أدخل اسم مؤسسة ثم اسم حساب سيكون المسؤول العام للاشتراك.
5. بالنسبة للخطوة 4، سجل صفحة تسجيل الدخول هنا (حدد وانسخ): ![خط.](../media/Common-Images/TableLine.png)
6. سجل معرف المستخدم هنا: ![Line.](../media/Common-Images/TableLine.png). onmicrosoft.com  
   سجل كلمة المرور التي أدخلتها في موقع آمن.
   ستتم الإشارة إلى هذه القيمة باسم **المسؤول العمومي**.
7. حدد **"الانتقال إلى الإعداد**".
8. في إعداد Office 365 E5، حدد **"متابعة" باستخدام *مؤسستك.onmicrosoft.com* للبريد الإلكتروني وتسجيل الدخول**، ثم حدد **"إنهاء" ثم تابع لاحقا**.

يجب أن تشاهد مركز مسؤولي Microsoft 365.

## <a name="phase-2-configure-your-office-365-trial-subscription"></a>المرحلة 2: تكوين اشتراكك التجريبي Office 365

في هذه المرحلة، يمكنك تكوين اشتراكك مع مستخدمين إضافيين وتعيينهم Office 365 E5 التراخيص.
  
للاتصال باشتراكك باستخدام Azure Active Directory PowerShell لوحدة Graph من الكمبيوتر، استخدم الإرشادات الموجودة في [الاتصال Microsoft 365 باستخدام PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

في مربع الحوار **"طلب بيانات الاعتماد" Windows PowerShell**، أدخل اسم المسؤول العام (على سبيل المثال، *jdoe@contosotoycompany.onmicrosoft.com*) وكلمة المرور.
  
املأ اسم مؤسستك (على سبيل المثال، *contosotoycompany*)، ورمز البلد المكون من حرفين لموقعك، وكلمة مرور الحساب الشائعة، ثم قم بتشغيل الأوامر التالية من مطالبة PowerShell:

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
> استخدام كلمة مرور مشتركة هنا هو للأتمتة وسهولة التكوين لبيئة اختبار. ومن الواضح أن هذا لا يشجع كثيرا على اشتراكات الإنتاج.

### <a name="record-key-information-for-future-reference"></a>تسجيل المعلومات الأساسية للرجوع إليها في المستقبل

إذا لم تكن قد سجلت هذه القيم بالفعل، فسجلها الآن:
  
- اسم مسؤول عمومي: ![خط.](../media/Common-Images/TableLine.png).onmicrosoft.com (من الخطوة 6 من المرحلة 1)

    سجل أيضا كلمة المرور لهذا الحساب في موقع آمن.

- اسم مؤسسة الاشتراك التجريبي: ![خط.](../media/Common-Images/TableLine.png) (من الخطوة 4 من المرحلة 1)

- لإدراج حسابات المستخدم 2 والمستخدم 3 والمستخدم 4 والمستخدم 5، قم بتشغيل الأمر التالي من وحدة Azure Active Directory Windows لمطالبة Windows PowerShell:

  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    سجل أسماء الحسابات هنا:

  - اسم حساب المستخدم 2: user2 @![خط.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - اسم حساب المستخدم 3: user3 @![خط.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - اسم حساب المستخدم 4: user4 @![خط.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - اسم حساب المستخدم 5: user5 @![خط.](../media/Common-Images/TableLine.png).onmicrosoft.com

    سجل أيضا كلمة المرور الشائعة لهذه الحسابات في موقع آمن.

### <a name="using-an-office-365-test-environment"></a>استخدام بيئة اختبار Office 365

إذا كنت بحاجة إلى بيئة اختبار Office 365 فقط، فلن تحتاج إلى قراءة باقي هذه المقالة.

للحصول على دلائل مختبر الاختبار الإضافية التي تنطبق على كل من Office 365 Microsoft 365، راجع [Microsoft 365 لدلائل مختبر اختبار المؤسسة](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>المرحلة 3: إضافة اشتراك تجريبي Microsoft 365 E5

في هذه المرحلة، يمكنك التسجيل للحصول على الاشتراك التجريبي Microsoft 365 E5 وإضافته إلى نفس المؤسسة مثل اشتراكك التجريبي Office 365 E5.
  
أولا، أضف اشتراك الإصدار التجريبي Microsoft 365 E5 وقم بتعيين ترخيص Microsoft 365 الجديد إلى حساب المسؤول العام.
  
1. في نافذة خاصة لمستعرض إنترنت، استخدم بيانات اعتماد حساب المسؤول العام لتسجيل الدخول إلى مركز مسؤولي Microsoft 365 في [https://admin.microsoft.com](https://admin.microsoft.com).

2. في صفحة **مركز مسؤولي Microsoft 365**، في جزء التنقل الأيمن، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**خدمات BillingPurchase**</a> > .

3. في صفحة **خدمات الشراء**، حدد **Microsoft 365 E5**، ثم حدد **"Get free trial**".

4. في **الصفحة التجريبية Microsoft 365 E5**، قرر تلقي رسالة نصية أو مكالمة هاتفية، وأدخل رقم هاتفك، ثم حدد **"نصي"** أو **"اتصل بي**". إجراء التحقق.

5. في صفحة **"تأكيد الطلب"** ، حدد **"جرب الآن**".

6. في صفحة **إيصال الطلب** ، حدد **"متابعة**".

7. في مركز مسؤولي Microsoft 365، حدد <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive**</a> >  users.

8. في **المستخدمين النشطين**، حدد حساب المسؤول.

9. حدد **التراخيص والتطبيقات**.

10. قم بتعطيل ترخيص Office 365 Enterprise E5 وتمكين ترخيص Microsoft 365 E5.

11. حدد **"حفظ التغييرات**"، ثم أغلق جزء معلومات حساب المستخدم.

بعد ذلك، كرر الخطوات من 8 إلى 11 من الإجراء السابق لكافة حساباتك الأخرى (المستخدم 2 والمستخدم 3 والمستخدم 4 والمستخدم 5).
  
> [!NOTE]
> طول الاشتراك التجريبي Microsoft 365 E5 هو 30 يوما. للحصول على بيئة اختبار دائمة، قم بتحويل هذا الاشتراك التجريبي إلى اشتراك مدفوع مع عدد صغير من التراخيص.
  
تحتوي بيئة الاختبار الخاصة بك الآن على:
  
- اشتراك تجريبي Microsoft 365 E5.
- يتم تمكين جميع حسابات المستخدمين المناسبة (إما المسؤول العام فقط أو جميع حسابات المستخدمين الخمسة) لاستخدام Microsoft 365 E5.

يبدو التكوين الناتج، الذي يضيف Microsoft 365 E5، كما يلي:
  
![المرحلة 3 من بيئة اختبار Microsoft 3656 Enterprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>المرحلة 4: إنشاء كمبيوتر Windows 10 Enterprise

في هذه المرحلة، يمكنك إنشاء كمبيوتر مستقل يعمل Windows 10 Enterprise إما ككمبيوتر فعلي أو جهاز ظاهري أو جهاز ظاهري من Azure.
  
### <a name="physical-computer"></a>جهاز كمبيوتر فعلي

على كمبيوتر شخصي، قم بتثبيت Windows 10 Enterprise. يمكنك تنزيل الإصدار التجريبي Windows 10 Enterprise [هنا](https://www.microsoft.com/software-download/windows10).
  
### <a name="virtual-machine"></a>الجهاز الظاهري

استخدم برنامج hypervisor الذي تختاره لإنشاء جهاز ظاهري، ثم قم بتثبيت Windows 10 Enterprise عليه. يمكنك تنزيل الإصدار التجريبي Windows 10 Enterprise [هنا](https://www.microsoft.com/software-download/windows10).
  
### <a name="virtual-machine-in-azure"></a>الجهاز الظاهري في Azure

لإنشاء جهاز ظاهري Windows 10 في Microsoft Azure، ***يجب أن يكون لديك اشتراك يستند إلى Visual Studio***، والذي لديه حق الوصول إلى الصورة Windows 10 Enterprise. لا تتوفر للأنواع الأخرى من اشتراكات Azure، مثل الاشتراكات التجريبية والاشتراكات المدفوعة، إمكانية الوصول إلى هذه الصورة. للحصول على أحدث المعلومات، راجع [استخدام عميل Windows في Azure لسيناريوهات التطوير/الاختبار](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> تستخدم مجموعات الأوامر التالية أحدث إصدار من Azure PowerShell. راجع [بدء استخدام أوامر Azure PowerShell cmdlets](/powershell/azureps-cmdlets-docs/). تنشئ مجموعات الأوامر هذه جهازا ظاهريا Windows 10 Enterprise يسمى WIN10 وكافة بنيته الأساسية المطلوبة، بما في ذلك مجموعة موارد وحساب تخزين وشبكة ظاهرية. إذا كنت على دراية بالفعل بخدمات البنية الأساسية ل Azure، فتكيف هذه الإرشادات لتلائم البنية الأساسية المنشورة حاليا.
  
أولا، ابدأ مطالبة Microsoft PowerShell.
  
سجل الدخول إلى حساب Azure باستخدام هذا الأمر.
  
```powershell
Connect-AzAccount
```

احصل على اسم اشتراكك باستخدام هذا الأمر.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

تعيين اشتراك Azure الخاص بك. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف \< and > ، بالاسم الصحيح.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

بعد ذلك، أنشئ مجموعة موارد جديدة. لتحديد اسم مجموعة موارد فريد، استخدم هذا الأمر لإدراج مجموعات الموارد الموجودة.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

إنشاء مجموعة الموارد الجديدة باستخدام هذه الأوامر. استبدل كل شيء ضمن علامات الاقتباس، بما في ذلك الأحرف \< and > ، بالأسماء الصحيحة.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

بعد ذلك، قم بإنشاء شبكة ظاهرية جديدة وجهاز WIN10 الظاهري باستخدام هذه الأوامر. عند المطالبة، قم بتوفير اسم وكلمة مرور حساب المسؤول المحلي ل WIN10 وتخزينها في موقع آمن.
  
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

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>المرحلة 5: الانضمام إلى الكمبيوتر Windows 10 Azure AD

بعد إنشاء الجهاز الفعلي أو الظاهري الذي يحتوي على Windows 10 Enterprise، سجل الدخول باستخدام حساب مسؤول محلي.
  
> [!NOTE]
> بالنسبة إلى جهاز ظاهري في Azure، استخدم  [هذه الإرشادات](/azure/virtual-machines/windows/connect-logon) للاتصال به.
  
بعد ذلك، انضم إلى الكمبيوتر WIN10 إلى المستأجر Azure AD لاشتراكك في Microsoft 365 E5.
  
1. على سطح المكتب على كمبيوتر WIN10، حدد **"بدء > الإعدادات > الحسابات" > الوصول إلى > الاتصال العمل أو المؤسسة التعليمية**.

2. في مربع الحوار **"إعداد حساب العمل أو المؤسسة التعليمية** "، حدد **"الانضمام إلى هذا الجهاز إلى Azure Active Directory**".

3. في **حساب العمل أو المؤسسة التعليمية**، أدخل اسم حساب المسؤول العام لاشتراكك في Microsoft 365 E5، ثم حدد **"التالي**".

4. في **إدخال كلمة المرور**، أدخل كلمة المرور لحساب المسؤول العام، ثم حدد **تسجيل الدخول**.

5. عند مطالبتك بالتأكد من أن هذه هي مؤسستك، حدد **"انضمام**"، ثم حدد **"تم**".

6. أغلق نافذة الإعدادات.

بعد ذلك، قم بتثبيت Microsoft 365 Apps for enterprise على الكمبيوتر WIN10:
  
1. افتح مستعرض Microsoft Edge وسجل الدخول إلى [مركز مسؤولي Microsoft 365](https://admin.microsoft.com) باستخدام بيانات اعتماد حساب المسؤول العام.

2. في علامة التبويب **"Microsoft Office الشريط الرئيسي**"، حدد **"تثبيت Office**".

3. عند مطالبتك بما يجب فعله، حدد **"تشغيل**"، ثم حدد **"نعم** **لعنصر تحكم حساب المستخدم**".

4. انتظر حتى يكمل Office تثبيته. عندما ترى **أنك جاهز تماما!**، حدد **"إغلاق"** مرتين.

تبدو بيئتك الناتجة كما يلي:

![المرحلة 5 من بيئة اختبار Microsoft 3656 Enterprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

يتضمن هذا الكمبيوتر WIN10 الذي يحتوي على:

- انضم إلى المستأجر Azure AD لاشتراكك في Microsoft 365 E5.
- مسجل كجهاز Azure AD في Microsoft Intune (EMS).
- Microsoft 365 Apps for enterprise مثبت.
  
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
