---
title: تشغيل حماية الشبكة
description: تمكين حماية الشبكة باستخدام إدارة التكوين وإدارة التكوين أو نهج المجموعة أو PowerShell أو الأجهزة المحمولة.
keywords: حماية الشبكة، استغلالات، موقع ويب ضار، ip، مجال، مجالات، تمكين، تشغيل
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.date: ''
ms.openlocfilehash: b21b2f2a69ab9a85f1f5003104969364ae9c6e78
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63571575"
---
# <a name="turn-on-network-protection"></a>تشغيل حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[تساعد حماية](network-protection.md) الشبكة على منع الموظفين من استخدام أي تطبيق للوصول إلى المجالات الخطيرة التي قد تستضيف رسائل التصيد الاحتيالي والمستغلين والمحتويات الضارة الأخرى على الإنترنت. يمكنك تدقيق [حماية الشبكة](evaluate-network-protection.md) في بيئة اختبار لعرض التطبيقات التي سيتم حظرها قبل تمكينها.

[تعرف على المزيد حول خيارات تكوين تصفية الشبكة.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>التحقق مما إذا تم تمكين حماية الشبكة

تحقق مما إذا تم تمكين حماية الشبكة على جهاز محلي باستخدام محرر السجل.

1. حدد زر **البدء** في شريط المهام وا اكتب **regedit** لفتح محرر السجل.

2. اختر **HKEY_LOCAL_MACHINE** من القائمة الجانبية.

3. انتقل عبر القوائم المتداخلة إلى **سياسات البرامج** \>  \> **Microsoft** \> Windows **Defender Windows** \> **Defender Exploit Guard** \> **Network Protection**.

إذا كان المفتاح مفقودا، فانتقل إلى **برامج** \> **Microsoft Windows** \> **Defender Windows** \> **Defender Exploit Guard** \> **Network Protection**.

4. حدد **EnableNetworkProtection** لرؤية الحالة الحالية لحماية الشبكة على الجهاز:

   - 0، أو **إيقاف التشغيل**
   - 1، أو **على**
   - 2، أو **وضع** التدقيق

    :::image type="content" alt-text="مفتاح تسجيل حماية الشبكة." source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::
    
    
## <a name="enable-network-protection"></a>تمكين حماية الشبكة

تمكين حماية الشبكة باستخدام أي من هذه الأساليب:

- [PowerShell](#powershell)
- [إدارة أجهزة المحمول (MDM)](#mobile-device-management-mdm)
- [إدارة نقاط النهاية من Microsoft](#microsoft-endpoint-manager)
- [نهج المجموعة](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. اكتب **powershell** في قائمة البدء، وانقر بضغطة **Windows PowerShell وحدد** **تشغيل كمسؤول**.

2. أدخل cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. اختياري: تمكين الميزة في وضع التدقيق باستخدام أمر cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    استخدم `Disabled` الميزة بدلا `Enabled` من `AuditMode` أو إيقاف تشغيلها.

### <a name="mobile-device-management-mdm"></a>إدارة أجهزة المحمول (MDM)

استخدم [موفر خدمة تكوين ./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) (CSP) لتمكين حماية الشبكة أو تعطيلها أو تمكين وضع التدقيق.

[تحديث النظام الأساسي للحماية من البرامج الضارة من Microsoft Defender إلى الإصدار الأخير](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) قبل تمكين حماية الشبكة أو تعطيلها أو تمكين وضع التدقيق.


### <a name="microsoft-endpoint-manager"></a>إدارة نقاط النهاية من Microsoft

1. سجل دخولك إلى إدارة نقاط النهاية من Microsoft الإدارة (https://endpoint.microsoft.com).

2. انتقل إلى **ملفات تعريف** **DevicesConfiguration** >  إنشاء  > **ملف تعريف**.

3. في الأمر **إنشاء صورة ملف تعريف** من حولك، حدد **النظام الأساسي** واختر نوع **ملف التعريف** **كقالب**.

4. في اسم **القالب،** اختر **حماية نقطة النهاية** من قائمة القوالب، ثم حدد **إنشاء**.

4. انتقل إلى **Endpoint** **protectionBasics** > ، ووفر اسما لملف التعريف الخاص بك، ثم حدد **التالي**.

5. في المقطع **إعدادات التكوين**، **انتقل إلى الحماية من مخاطر الهجمات من Microsoft Defender** >  **تصفيةNetwork** **حمايةNetworkالمراجعة** >  >  أو **التدقيق**. حدد **التالي**.

6. حدد علامات **النطاق والواجبات** وقواعد إمكانية التطبيق المناسبة كما  هو مطلوب من قبل مؤسستك. يمكن للمسؤولين تعيين المزيد من المتطلبات.

7. راجع كل المعلومات، ثم حدد **إنشاء**.

### <a name="group-policy"></a>نهج المجموعة

استخدم الإجراء التالي لتمكين حماية الشبكة على أجهزة الكمبيوتر المنضمة إلى المجال أو على كمبيوتر مستقل.

1. على كمبيوتر مستقل، انتقل إلى **ابدأ** ثم اكتب وحدد **تحرير نهج المجموعة**.

    *-أو-*

    على كمبيوتر إدارة نهج المجموعة المنضم إلى المجال، افتح وحدة [](https://technet.microsoft.com/library/cc731212.aspx)تحكم إدارة نهج المجموعة، وانقر بيمين فوق كائن نهج المجموعة الذي تريد تكوينه وحدد **تحرير**.

2. في محرر **إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة Windows **مكونات برنامج الحماية من الفيروسات من Microsoft Defender** \>  \> **Windows حماية شبكة Defender Exploit Guard**\>.

   > [!NOTE]
   > في الإصدارات القديمة من Windows، قد يقول مسار نهج المجموعة "برنامج الحماية من الفيروسات لـ Windows Defender" بدلا من "برنامج الحماية من الفيروسات من Microsoft Defender".

4. انقر نقرا مزدوجا **فوق الإعداد منع المستخدمين والتطبيقات من الوصول** إلى مواقع الويب الخطيرة، ثم قم بتعيين الخيار **إلى تمكين**. في قسم الخيارات، يجب تحديد أحد الخيارات التالية:
    - **الحظر** - لا يمكن للمستخدمين الوصول إلى عناوين IP والمجالات الضارة.
    - **تعطيل (افتراضي)** - لن تعمل ميزة حماية الشبكة. لن يتم حظر المستخدمين من الوصول إلى المجالات الضارة.
    - **وضع التدقيق** - إذا قام مستخدم بزيارة عنوان IP ضار أو مجال ضار، سيتم تسجيل حدث في Windows الأحداث. ومع ذلك، لن يتم حظر المستخدم من زيارة العنوان.

   > [!IMPORTANT]
   > لتمكين حماية الشبكة بشكل كامل، يجب تعيين الخيار "نهج المجموعة" إلى  "تمكين" وتحديد "حظر" أيضا في القائمة المنسدلة "خيارات".

تأكد من تمكين حماية الشبكة على كمبيوتر محلي باستخدام محرر السجل:

1. حدد **بدء** وا اكتب **regedit** لفتح **محرر السجل**.

2. انتقل إلى **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Windows Defender Exploit Guard\Network Protection\EnableNetworkProtection**

3. حدد **EnableNetworkProtection** وتأكد من القيمة:
   - 0=إيقاف التشغيل
   - 1=On
   - 2=Audit

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. افتح وحدة التحكم Configuration Manager.

2. انتقل إلى الأصول **والتوافق** > **، Endpoint Protection** >  **Windows Defender Exploit Guard**. 

3. حدد **إنشاء نهج حماية استغلال** من الشريط لإنشاء نهج جديد.
   - لتحرير نهج موجود، حدد النهج، ثم حدد **خصائص** من الشريط أو قائمة النقر بيمين. تحرير الخيار **تكوين حماية الشبكة** من **علامة التبويب حماية** الشبكة.  

4. في الصفحة **عام**، حدد اسما النهج الجديد وتحقق من تمكين خيار حماية الشبكة. 

5. في صفحة **حماية الشبكة** ، حدد أحد الإعدادات التالية للحصول على **الخيار تكوين حماية** الشبكة:
   - **حظر**
   - **التدقيق**
   - **معطل**
   
6. أكمل باقي الخطوات، واحفظ النهج. 

7. من الشريط، حدد **نشر** لنشر النهج إلى مجموعة.


> [!IMPORTANT]
> بمجرد نشر نهج "حماية استغلال" من "إدارة التكوين"، لن تتم إزالة إعدادات "حماية استغلال" من العملاء إذا قمت بإزالة النشر. `Delete not supported` يتم تسجيله في سجل ExploitGuardHandler.log الخاص ب عميل Configuration Manager إذا قمت بإزالة نشر "حماية استغلال" العميل. <!--CMADO8538577-->
> يمكن تشغيل البرنامج النصي التالي من PowerShell ضمن سياق النظام لإزالة هذه الإعدادات:<!--CMADO9907132-->
>
> ```powershell
> $defenderObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_Defender02" -Filter "InstanceID='Defender' and ParentID='./Vendor/MSFT/Policy/Config'"
> $defenderObject.AttackSurfaceReductionRules = $null
> $defenderObject.AttackSurfaceReductionOnlyExclusions = $null
> $defenderObject.EnableControlledFolderAccess = $null
> $defenderObject.ControlledFolderAccessAllowedApplications = $null
> $defenderObject.ControlledFolderAccessProtectedFolders = $null
> $defenderObject.EnableNetworkProtection = $null
> $defenderObject.Put()
>
> $exploitGuardObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_ExploitGuard02" -Filter "InstanceID='ExploitGuard' and ParentID='./Vendor/MSFT/Policy/Config'"
> $exploitGuardObject.ExploitProtectionSettings = $null
> $exploitGuardObject.Put()
>```  

## <a name="see-also"></a>راجع أيضًا

- [حماية الشبكة](network-protection.md)

- [حماية الشبكة ومصافحة TCP ثلاثية](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [تقييم حماية الشبكة](evaluate-network-protection.md)

- [استكشاف مشاكل حماية الشبكة وإصلاحها](troubleshoot-np.md)
