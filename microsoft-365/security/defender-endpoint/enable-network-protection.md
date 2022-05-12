---
title: تشغيل حماية الشبكة
description: تمكين حماية الشبكة باستخدام نهج المجموعة أو PowerShell أو إدارة الجهاز الجوال Configuration Manager.
keywords: حماية الشبكة، مهاجمات، موقع ويب ضار، ip، مجال، مجالات، تمكين، تشغيل
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
ms.openlocfilehash: e53cda0ac61bdc546e972d663bf0063b02b21ad3
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363247"
---
# <a name="turn-on-network-protection"></a>تشغيل حماية الشبكة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- برنامج الحماية من الفيروسات من Microsoft Defender

**الأنظمة الأساسية**
- بالنسبة لنظام التشغيل

> [!TIP]
> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

تساعد [حماية الشبكة](network-protection.md) على منع الموظفين من استخدام أي تطبيق للوصول إلى المجالات الخطرة التي قد تستضيف رسائل التصيد الاحتيالي والمستغلة والمحتوى الضار الآخر على الإنترنت. يمكنك [تدقيق حماية الشبكة](evaluate-network-protection.md) في بيئة اختبار لعرض التطبيقات التي سيتم حظرها قبل تمكين حماية الشبكة.

[تعرف على المزيد حول خيارات تكوين تصفية الشبكة.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>التحقق مما إذا كانت حماية الشبكة ممكنة

تحقق مما إذا تم تمكين حماية الشبكة على جهاز محلي باستخدام محرر التسجيل.

1. حدد زر **البدء** في شريط المهام واكتب **regedit** لفتح محرر السجل.

2. اختر **HKEY_LOCAL_MACHINE** من القائمة الجانبية.

3. انتقل عبر القوائم المتداخلة إلى **SOFTWARE** \> **Policies** \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Protection**.

إذا كان المفتاح مفقودا، فان انتقل إلى **SOFTWARE** \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Protection**.

4. حدد **EnableNetworkProtection** لمشاهدة الحالة الحالية لحماية الشبكة على الجهاز:

   - 0 أو **إيقاف تشغيل**
   - 1 أو **تشغيل**
   - 2، أو وضع **التدقيق**

    :::image type="content" source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" alt-text="مفتاح تسجيل Network Protection" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>تمكين حماية الشبكة

تمكين حماية الشبكة باستخدام أي من هذه الأساليب:

- [PowerShell](#powershell)
- [إدارة الجهاز الجوال (MDM)](#mobile-device-management-mdm)
- [إدارة نقاط النهاية من Microsoft](#microsoft-endpoint-manager)
- [نهج المجموعة](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. اكتب **powershell** في قائمة البدء، وانقر بزر الماوس الأيمن **فوق Windows PowerShell** وحدد **"تشغيل" كمسؤول**.

2. أدخل cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. اختياري: تمكين الميزة في وضع التدقيق باستخدام cmdlet التالي:

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    استخدمها `Disabled` بدلا من `AuditMode` الميزة أو `Enabled` لإيقاف تشغيلها.

### <a name="mobile-device-management-mdm"></a>إدارة أجهزة المحمول (MDM)

استخدم موفر خدمة تكوين [./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) (CSP) لتمكين حماية الشبكة أو تعطيلها أو تمكين وضع التدقيق.

[تحديث النظام الأساسي لمكافحة البرامج الضارة من Microsoft Defender إلى أحدث إصدار](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) قبل تمكين حماية الشبكة أو تعطيلها أو تمكين وضع التدقيق.


### <a name="microsoft-endpoint-manager"></a>إدارة نقاط النهاية من Microsoft

1. سجل الدخول إلى مركز إدارة إدارة نقاط النهاية من Microsoft (https://endpoint.microsoft.com).

2. انتقل إلى **ملف** تعريف  > **DevicesConfigurationCreate** >  **profile**.

3. في القائمة **المنبثقة "إنشاء ملف تعريف** "، حدد **"النظام الأساسي** " واختر **"نوع ملف التعريف** **كقوالب**".

4. في **اسم القالب**، اختر **حماية نقطة النهاية** من قائمة القوالب، ثم حدد **"إنشاء**".

4. انتقل إلى **Endpoint** **protectionBasics** > ، وقم بتوفير اسم لملف التعريف الخاص بك، ثم حدد **"التالي**".

5. في قسم **إعدادات التكوين**، انتقل إلى **الحماية من مخاطر الهجمات من Microsoft Defender** >  **Network filteringNetwork** >  **protectionEnable** >  أو **Audit**. حدد **التالي**.

6. حدد **علامات النطاق** المناسبة، **والتعيينات**، **وقواعد قابلية التطبيق** كما هو مطلوب من قبل مؤسستك. يمكن للمسؤولين تعيين المزيد من المتطلبات.

7. راجع كافة المعلومات، ثم حدد **"إنشاء**".

### <a name="group-policy"></a>نهج المجموعة

استخدم الإجراء التالي لتمكين حماية الشبكة على أجهزة الكمبيوتر المتصلة بالمجال أو على كمبيوتر مستقل.

1. على كمبيوتر مستقل، انتقل إلى **شاشة البدء** ثم اكتب نهج **المجموعة "تحرير"** وحدده.

    *-Or-*

    على كمبيوتر إدارة نهج المجموعة منضم إلى المجال، افتح [وحدة تحكم إدارة نهج المجموعة](https://technet.microsoft.com/library/cc731212.aspx)، وانقر بزر الماوس الأيمن فوق العنصر نهج المجموعة الذي تريد تكوينه وحدد **"تحرير**".

2. في **محرر إدارة نهج المجموعة**، انتقل إلى **تكوين الكمبيوتر** وحدد **القوالب الإدارية**.

3. قم بتوسيع الشجرة إلى **مكونات** \> Windows **برنامج الحماية من الفيروسات من Microsoft Defender** \> حماية **شبكة** **defender Exploit Guard** \> Windows.

   > [!NOTE]
   > في الإصدارات القديمة من Windows، قد يقول مسار نهج المجموعة "برنامج الحماية من الفيروسات لـ Windows Defender" بدلا من "برنامج الحماية من الفيروسات من Microsoft Defender".

4. انقر نقرا مزدوجا فوق **"منع المستخدمين والتطبيقات" من الوصول إلى إعداد مواقع الويب الخطرة** وعين الخيار "**ممكن".** في قسم الخيارات، يجب تحديد أحد الخيارات التالية:
    - **حظر** - لا يمكن للمستخدمين الوصول إلى عناوين IP والمجالات الضارة.
    - **تعطيل (افتراضي)** - لن تعمل ميزة حماية الشبكة. لن يتم حظر المستخدمين من الوصول إلى المجالات الضارة.
    - **وضع التدقيق** - إذا قام مستخدم بزيارة عنوان IP أو مجال ضار، فسيتم تسجيل حدث في سجل الأحداث Windows. ومع ذلك، لن يتم حظر المستخدم من زيارة العنوان.

   > [!IMPORTANT]
   > لتمكين حماية الشبكة بشكل كامل، يجب تعيين خيار نهج المجموعة إلى **Enabled** وتحديد **"حظر"** أيضا في القائمة المنسدلة "خيارات".

   > [!NOTE]
   > اختياري: اتبع الخطوات الواردة في [التحقق من تمكين حماية الشبكة](#check-if-network-protection-is-enabled) للتحقق من صحة إعدادات نهج المجموعة.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. افتح وحدة التحكم Configuration Manager.

2. انتقل إلى **Assets and Compliance** >  **Endpoint Protection** >  **Windows Defender Exploit Guard**.

3. حدد **Create Exploit Guard Policy** من الشريط لإنشاء نهج جديد.
   - لتحرير نهج موجود، حدد النهج، ثم حدد **"خصائص** " من الشريط أو قائمة النقر بزر الماوس الأيمن. تحرير خيار **تكوين حماية الشبكة** من علامة التبويب **Network Protection** .  

4. في الصفحة **"عام** "، حدد اسما للنهج الجديد وتحقق من تمكين خيار **حماية الشبكة** .

5. في صفحة **حماية الشبكة** ، حدد أحد الإعدادات التالية للخيار **"تكوين حماية الشبكة"** :
   - **حظر**
   - **مراجعه الحسابات**
   - **ذوي الاحتياجات الخاصه**
   
6. أكمل باقي الخطوات واحفظ النهج. 

7. من الشريط، حدد **"نشر** " لنشر النهج إلى مجموعة.


> [!IMPORTANT]
> بمجرد نشر نهج Exploit Guard من Configuration Manager، لن تتم إزالة إعدادات Exploit Guard من العملاء إذا قمت بإزالة النشر. `Delete not supported`يتم تسجيله في سجل ExploitGuardHandler.log لعميل Configuration Manager إذا قمت بإزالة نشر Exploit Guard الخاص بالعميل. <!--CMADO8538577-->
> يمكن تشغيل البرنامج النصي PowerShell التالي ضمن سياق SYSTEM لإزالة هذه الإعدادات:<!--CMADO9907132-->
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

- [حماية الشبكة والتصاق TCP ثلاثي الاتجاهات](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [تقييم حماية الشبكة](evaluate-network-protection.md)

- [استكشاف أخطاء حماية الشبكة وإصلاحها](troubleshoot-np.md)
