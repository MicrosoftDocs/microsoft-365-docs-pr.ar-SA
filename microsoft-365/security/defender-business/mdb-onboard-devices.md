---
title: إلحاق الأجهزة Microsoft Defender for Business
description: تعرف على كيفية إلحاق الأجهزة ب Defender for Business لحماية أجهزتك من اليوم الأول.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9b4228ba31594e8c6893d4bc45e2fc1994139231
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772205"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>إلحاق الأجهزة Microsoft Defender for Business

باستخدام Defender for Business، لديك العديد من الخيارات للاختيار من بينها لإلحاق أجهزة شركتك. ترشدك هذه المقالة عبر هذه الخيارات وتوفر نظرة عامة حول كيفية عمل الإلحاق.

## <a name="what-to-do"></a>ما يجب فعله

1. حدد علامة تبويب: 
   - **Windows 10 و11**
   - **ماك**
   - **الخوادم** (جديد! Windows Server أو Linux Server)
   - **الأجهزة المحمولة** (لأجهزة iOS/iPadOS أو Android)
2. اعرض خيارات الإلحاق، واتبع الإرشادات الموجودة في علامة التبويب المحددة.
3. تابع إلى خطواتك التالية.

## <a name="windows-10-and-11"></a>[**Windows 10 و11**](#tab/Windows10and11)

## <a name="windows-10-and-11"></a>Windows 10 و11

اختر أحد الخيارات التالية لإلحاق أجهزة عميل Windows ب Defender for Business:

- [البرنامج النصي المحلي](#local-script-for-windows-10-and-11) (لإعداد الأجهزة يدويا في مدخل Microsoft 365 Defender)
- [نهج المجموعة](#group-policy-for-windows-10-and-11) (إذا كنت تستخدم بالفعل نهج المجموعة في مؤسستك)
- [Microsoft Intune](#intune-for-windows-10-and-11) (مضمن في [Microsoft 365 Business Premium](../../business-premium/index.md))

### <a name="local-script-for-windows-10-and-11"></a>البرنامج النصي المحلي Windows 10 و11

يمكنك استخدام برنامج نصي محلي لإلحاق أجهزة عميل Windows. عند تشغيل البرنامج النصي الإلحاق على جهاز، فإنه ينشئ ثقة مع Azure Active Directory، إذا لم تكن هذه الثقة موجودة بالفعل؛ يسجل الجهاز في Microsoft Intune، إذا لم يكن مسجلا بالفعل؛ ثم يقوم بإلحاق الجهاز ب Defender for Business. يعمل أسلوب البرنامج النصي المحلي حتى إذا لم يكن لديك Intune حاليا، وهذه هي الطريقة الموصى بها لعملاء Defender for Business.

> [!TIP]
> نوصي بإلحاق ما يصل إلى 10 أجهزة في وقت تستخدم فيه أسلوب البرنامج النصي المحلي.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **"نقاط نهاية الإعدادات** > "، ثم ضمن **"إدارة الجهاز"**، اختر **"إلحاق".**

3. حدد **Windows 10 و11**، ثم في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

4. حدد **تنزيل حزمة الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

5. على جهاز Windows، قم باستخراج محتويات حزمة التكوين إلى موقع، مثل مجلد سطح المكتب. يجب أن يكون لديك ملف باسم `WindowsDefenderATPLocalOnboardingScript.cmd`. 

6. افتح موجه أوامر كمسؤول.

7. اكتب موقع ملف البرنامج النصي. على سبيل المثال، إذا قمت بنسخ الملف إلى مجلد سطح المكتب، فستكتب `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`، ثم اضغط على مفتاح الإدخال Enter (أو حدد **"موافق**").

8. بعد تشغيل البرنامج النصي، [قم بتشغيل اختبار الكشف](#run-a-detection-test-on-a-windows-10-or-11-device).

### <a name="group-policy-for-windows-10-and-11"></a>نهج المجموعة ل Windows 10 و11

إذا كنت تفضل استخدام نهج المجموعة لإلحاق عملاء Windows، فاتبع الإرشادات الواردة في [أجهزة Windows الملحقة باستخدام نهج المجموعة](../defender-endpoint/configure-endpoints-gp.md). تصف هذه المقالة خطوات الإلحاق Microsoft Defender لنقطة النهاية. خطوات الإلحاق ب Defender for Business متشابهة.

### <a name="intune-for-windows-10-and-11"></a>Intune ل Windows 10 و11

إذا كان اشتراكك يتضمن Intune، يمكنك إلحاق عملاء Windows والأجهزة الأخرى في مركز إدارة Microsoft إدارة نقاط النهاية ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). على سبيل المثال، إذا كان لديك [Microsoft 365 Business Premium](../../business/index.yml)، فلديك بالفعل Intune كجزء من اشتراكك، ويمكنك استخدام Intune لإلحاق الأجهزة.  

هناك العديد من الأساليب المتاحة لتسجيل الأجهزة في Intune. نوصي باستخدام إحدى الطرق التالية:

- [تمكين التسجيل التلقائي في Windows](/mem/intune/enrollment/windows-enroll) للأجهزة المملوكة للشركة أو التي تديرها الشركة
- [اطلب من المستخدمين تسجيل أجهزة Windows 10/11 الخاصة بهم في Intune](/mem/intune/user-help/enroll-windows-10-device)

#### <a name="to-enable-automatic-enrollment-for-windows-10-and-11"></a>لتمكين التسجيل التلقائي Windows 10 و11

عند إعداد التسجيل التلقائي، يضيف المستخدمون حساب العمل الخاص بهم إلى الجهاز. في الخلفية، يسجل الجهاز وينضم إلى Azure Active Directory (Azure AD) ويتم تسجيله في Intune.

1. انتقل إلى مدخل Azure ([https://portal.azure.com/](https://portal.azure.com/)) وسجل الدخول.

2. حدد **Azure Active Directory** > **Mobility (MDM وMAM)** > **Microsoft Intune**.

3. تكوين **نطاق مستخدم MDM** **ونطاق مستخدم MAM**.

   :::image type="content" source="media/mem-mam-scope-azure-ad.png" alt-text="لقطة شاشة لإعداد نطاق مستخدم MDM ونطاق مستخدم MAM في Intune.":::

   - بالنسبة لنطاق مستخدم MDM، نوصي بتحديد **الكل** بحيث يمكن لجميع المستخدمين تسجيل أجهزة Windows الخاصة بهم تلقائيا.
   - في قسم نطاق مستخدم MAM، نوصي بالقيم الافتراضية التالية لعناوين URL:

       - **عنوان URL لشروط استخدام MDM**
       - **عنوان URL لاكتشاف MDM**
       - **عنوان URL لتوافق MDM**

4. حدد **حفظ**.

5. بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة في Defender for Business. [تعرف على المزيد حول مجموعات الأجهزة في Defender for Business](mdb-create-edit-device-groups.md).

> [!TIP]
> لمعرفة المزيد، راجع [تمكين التسجيل التلقائي في Windows](/mem/intune/enrollment/windows-enroll).

#### <a name="to-have-users-enroll-their-own-windows-10-and-11-devices"></a>لجعل المستخدمين يسجلون Windows 10 الخاصة بهم و11 جهازا

1. شاهد الفيديو التالي لمعرفة كيفية عمل التسجيل:<br/><br/>

   > [!VIDEO https://www.youtube.com/embed/TKQxEckBHiE?rel=0]  

2. شارك هذه المقالة مع المستخدمين في مؤسستك: [تسجيل أجهزة Windows 10/11 في Intune](/mem/intune/user-help/enroll-windows-10-device).

3. بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة في Defender for Business. [تعرف على المزيد حول مجموعات الأجهزة في Defender for Business](mdb-create-edit-device-groups.md).

### <a name="run-a-detection-test-on-a-windows-10-or-11-device"></a>تشغيل اختبار الكشف على جهاز Windows 10 أو 11

بعد إلحاق أجهزة Windows ب Defender for Business، يمكنك تشغيل اختبار الكشف على الجهاز للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على جهاز Windows، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه أوامر كمسؤول.

3. في نافذة موجه الأوامر، قم بتشغيل أمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجحت، سيتم وضع علامة على اختبار الكشف كمكتمل، وسيظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم إلحاقه حديثا في حوالي 10 دقائق.

## <a name="view-a-list-of-onboarded-devices"></a>عرض قائمة بالأجهزة التي تم إلحاقها

لعرض قائمة الأجهزة التي تم إلحاقها ب Defender for Business، انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). في جزء التنقل، ضمن **نقاط النهاية**، اختر **مخزون الجهاز**.

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب لهذه الأجهزة ([Windows 10 و11 أو Mac أو الخوادم أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانتقل إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Defender for Business](mdb-configure-security-settings.md)
- راجع [بدء استخدام Defender for Business](mdb-get-started.md).

## <a name="mac"></a>[**ماك**](#tab/mac)

## <a name="mac"></a>ماك

> [!NOTE]
> نوصي باستخدام [برنامج نصي محلي لإلحاق Mac](#local-script-for-mac). على الرغم من أنه يمكنك [إعداد التسجيل ل Mac باستخدام Intune](/mem/intune/enrollment/macos-enroll)، فإن البرنامج النصي المحلي هو أبسط طريقة لإلحاق Mac ب Defender for Business. 

اختر أحد الخيارات التالية لإلحاق Mac:

- [البرنامج النصي المحلي لنظام التشغيل Mac](#local-script-for-mac) (*مستحسن*)
- [Intune for Mac](#intune-for-mac)

### <a name="local-script-for-mac"></a>البرنامج النصي المحلي ل Mac

عند تشغيل البرنامج النصي المحلي على جهاز Mac، فإنه ينشئ ثقة مع Azure Active Directory، إذا لم تكن هذه الثقة موجودة بالفعل؛ يسجل Mac في Microsoft Intune، إذا لم يكن مسجلا بالفعل؛ ثم يقوم بإلحاق Mac ب Defender for Business. يعمل أسلوب البرنامج النصي المحلي حتى إذا لم يكن لديك Intune حاليا. نوصي بإلحاق ما يصل إلى 10 أجهزة في كل مرة باستخدام هذه الطريقة.

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **"نقاط نهاية الإعدادات** > "، ثم ضمن **"إدارة الجهاز"**، اختر **"إلحاق".**

3. حدد **macOS**. في قسم **أسلوب النشر** ، اختر **البرنامج النصي المحلي**. 

4. حدد **"تنزيل حزمة الإلحاق**"، واحفظها في محرك أقراص قابل للإزالة. حدد أيضا **تنزيل حزمة التثبيت**، واحفظها على جهازك القابل للإزالة.

5. على جهاز Mac، احفظ حزمة التثبيت في `wdav.pkg` دليل محلي.

6. احفظ حزمة `WindowsDefenderATPOnboardingPackage.zip` الإلحاق بنفس الدليل الذي استخدمته لحزمة التثبيت.

7. استخدم "الباحث" للانتقال إليك `wdav.pkg` بعد حفظه، ثم افتحه.

8. حدد **"متابعة**"، وتوافق على شروط الترخيص، ثم أدخل كلمة المرور عند المطالبة.

9. ستتم مطالبتك بالسماح بتثبيت برنامج تشغيل من Microsoft (إما "تم حظر ملحق النظام" أو "التثبيت قيد الانتظار" أو كليهما). يجب السماح بتثبيت برنامج التشغيل: حدد **"تفضيلات الأمان المفتوحة**" أو "**أمان تفضيلات** >  النظام المفتوح **" & الخصوصية**، ثم حدد **"السماح**".

10. استخدم أمر Python التالي في Bash لتشغيل حزمة الإلحاق: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.sh`

بعد تسجيل جهاز Mac في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Defender for Business](mdb-create-edit-device-groups.md).

### <a name="intune-for-mac"></a>Intune for Mac

إذا كان اشتراكك يتضمن Microsoft Intune، يمكنك إلحاق Mac في مركز إدارة Microsoft إدارة نقاط النهاية ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). على سبيل المثال، إذا كان لديك [Microsoft 365 Business Premium](../../business/index.yml)، فلديك بالفعل Intune كجزء من اشتراكك.  

تتوفر عدة طرق لتسجيل Mac في Intune. نوصي بأحد الأساليب التالية:

- [اختيار خيار لجهاز Mac المملوك للشركة](#options-for-company-owned-mac)
- [اطلب من المستخدمين تسجيل جهاز Mac الخاص بهم في Intune](#ask-users-to-enroll-their-own-mac-in-intune)

#### <a name="options-for-company-owned-mac"></a>خيارات Mac المملوكة للشركة

اختر أحد الخيارات التالية لتسجيل أجهزة Mac التي تديرها الشركة في Intune:

| الخيار  | الوصف  |
|---------|---------|
| تسجيل جهاز Apple التلقائي |  استخدم هذه الطريقة لأتمتة التسجيل على الأجهزة التي تم شراؤها من خلال Apple Business Manager أو Apple School Manager. ينشر تسجيل الجهاز التلقائي ملف تعريف التسجيل "عبر الهواء"، لذلك لا تحتاج إلى الوصول الفعلي إلى الأجهزة. <br/><br/>راجع [تسجيل Mac تلقائيا باستخدام Apple Business Manager أو Apple School Manager](/mem/intune/enrollment/device-enrollment-program-enroll-macos). |
| مدير تسجيل الأجهزة (DEM)  |  استخدم هذا الأسلوب لعمليات النشر واسعة النطاق وعندما يكون هناك عدة أشخاص في مؤسستك يمكنهم المساعدة في إعداد التسجيل. يمكن لشخص ما له أذونات مدير تسجيل الأجهزة (DEM) تسجيل ما يصل إلى 1000 جهاز باستخدام حساب Azure Active Directory واحد. يستخدم هذا الأسلوب تطبيق Company Portal أو تطبيق Microsoft Intune لتسجيل الأجهزة. لا يمكنك استخدام حساب DEM لتسجيل الأجهزة عبر تسجيل الجهاز التلقائي.<br/><br/> راجع [تسجيل الأجهزة في Intune باستخدام حساب إدارة تسجيل الأجهزة](/mem/intune/enrollment/device-enrollment-manager-enroll).  |
| التسجيل المباشر  | تسجيل مباشر يسجل الأجهزة دون ترابط المستخدم، لذلك هذا الأسلوب هو الأفضل للأجهزة غير المرتبطة بمستخدم واحد. يتطلب منك هذا الأسلوب الوصول الفعلي إلى أجهزة Mac التي تقوم بتسجيلها. <br/><br/>راجع [استخدام التسجيل المباشر ل Mac](/mem/intune/enrollment/device-enrollment-direct-enroll-macos).      |

#### <a name="ask-users-to-enroll-their-own-mac-in-intune"></a>اطلب من المستخدمين تسجيل جهاز Mac الخاص بهم في Intune

إذا كانت شركتك تفضل أن يقوم الأشخاص بتسجيل أجهزتهم الخاصة في Intune، فوجه المستخدمين إلى اتباع الخطوات التالية:

1. انتقل إلى موقع ويب Company Portal ([https://portal.manage.microsoft.com/](https://portal.manage.microsoft.com/)) وسجل الدخول.

2. اتبع الإرشادات الموجودة على موقع ويب Company Portal لإضافة جهازه.

3. قم بتثبيت تطبيق Company Portal في [https://aka.ms/EnrollMyMac](https://aka.ms/EnrollMyMac)، واتبع الإرشادات الموجودة في التطبيق.

### <a name="confirm-that-a-mac-is-onboarded"></a>تأكد من أن جهاز Mac تم إلحاقه

1. للتأكد من أن الجهاز مقترن بشركتك، استخدم أمر Python التالي في Bash:

   `mdatp health --field org_id`.

2. إذا كنت تستخدم macOS 10.15 (Catalina) أو إصدار أحدث، فامنح Defender for Business موافقة لحماية جهازك. انتقل إلى أمان **تفضيلات** >  النظام &**الوصول إلى القرص الكامل** **لخصوصية الخصوصية** >  > . حدد أيقونة التأمين في أسفل مربع الحوار لإجراء تغييرات، ثم حدد **Microsoft Defender for Business** (أو **Defender لنقطة النهاية**، إذا كان هذا ما تراه).

3. للتحقق من أن الجهاز تم إلحاقه، استخدم الأمر التالي في Bash:

   `mdatp health --field real_time_protection_enabled`

بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Defender for Business](mdb-create-edit-device-groups.md).

## <a name="view-a-list-of-onboarded-devices"></a>عرض قائمة بالأجهزة التي تم إلحاقها

لعرض قائمة الأجهزة التي تم إلحاقها ب Defender for Business، انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). في جزء التنقل، ضمن **نقاط النهاية**، اختر **مخزون الجهاز**.

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب لهذه الأجهزة ([Windows 10 و11 أو Mac أو الخوادم أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانتقل إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Defender for Business](mdb-configure-security-settings.md).
- راجع [بدء استخدام Defender for Business](mdb-get-started.md).

## <a name="servers"></a>[**الخوادم**](#tab/Servers)

## <a name="servers"></a>الخوادم

> [!NOTE]
> **القدرة على إلحاق خادم قيد المعاينة حاليا**.

اختر نظام التشغيل للخادم:

- [Windows Server](#windows-server)
- [Linux Server](#linux-server)

## <a name="windows-server"></a>Windows Server

> [!IMPORTANT]
> **القدرة على إلحاق نقاط نهاية Windows Server قيد المعاينة حاليا**. تأكد من تلبية المتطلبات التالية قبل إلحاق نقطة نهاية Windows Server:
> - تم تشغيل إعداد **ميزات المعاينة** . في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، انتقل إلى **ميزات معاينة الميزات** المتقدمة **العامة** > **لنقاط النهاية** **للإعدادات** >  >  > .
> - نطاق فرض Windows Server قيد التشغيل. انتقل إلى **نطاق فرض** **إدارة** >  تكوين **نقاط النهاية** **للإعدادات** >  > . حدد **"استخدام MDE" لفرض إعدادات تكوين الأمان من MEM**، وحدد  **Windows Server**، ثم حدد **"حفظ**".

يمكنك إلحاق مثيل من Windows Server إلى Defender for Business باستخدام برنامج نصي محلي.

### <a name="local-script-for-windows-server"></a>البرنامج النصي المحلي ل Windows Server

1. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

2. في جزء التنقل، اختر **"نقاط نهاية الإعدادات** > "، ثم ضمن **"إدارة الجهاز"**، اختر **"إلحاق".**

3. حدد نظام تشغيل، مثل **Windows Server 1803 و2019 و2022**، ثم في قسم **أسلوب النشر** ، اختر **البرنامج النصي المحلي**. 

   إذا حددت **Windows Server 2012 R2 و2016**، فسيكون لديك حزمتان لتنزيلهما وتشغيلهما: حزمة تثبيت وحزمة إلحاق. تحتوي حزمة التثبيت على ملف MSI يقوم بتثبيت عامل Defender for Business. تحتوي حزمة الإلحاق على البرنامج النصي لإلحاق نقطة نهاية Windows Server ب Defender for Business.

4. حدد **تنزيل حزمة الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

   إذا قمت بتحديد **Windows Server 2012 R2 و2016**، فحدد أيضا **تنزيل حزمة التثبيت** واحفظ الحزمة في محرك أقراص قابل للإزالة

5. على نقطة نهاية Windows Server، قم باستخراج محتويات حزمة التثبيت/الإلحاق إلى موقع مثل مجلد سطح المكتب. يجب أن يكون لديك ملف باسم `WindowsDefenderATPLocalOnboardingScript.cmd`. 

   إذا كنت تقوم بإلحاق Windows Server 2012 R2 أو Windows Server 2016، فقم باستخراج حزمة التثبيت أولا.

6. افتح موجه أوامر كمسؤول.

7. إذا كنت تقوم بإلحاق Windows Server 2012R2 أو Windows Server 2016، فقم بتشغيل الأمر التالي:

   `Msiexec /i md4ws.msi /quiet` 

   إذا كنت تقوم بإلحاق Windows Server 1803 أو 2019 أو 2022، فتخطى هذه الخطوة وانتقل إلى الخطوة 8.

8. اكتب موقع ملف البرنامج النصي. على سبيل المثال، إذا قمت بنسخ الملف إلى مجلد سطح المكتب، فستكتب `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`، ثم اضغط على مفتاح الإدخال Enter (أو حدد **"موافق**").

9. انتقل إلى [تشغيل اختبار الكشف على Windows Server](#run-a-detection-test-on-windows-server).

### <a name="run-a-detection-test-on-windows-server"></a>تشغيل اختبار الكشف على Windows Server

بعد إلحاق نقطة نهاية Windows Server ب Defender for Business، يمكنك تشغيل اختبار الكشف للتأكد من أن كل شيء يعمل بشكل صحيح:

1. على جهاز Windows Server، قم بإنشاء مجلد: `C:\test-MDATP-test`.

2. افتح موجه أوامر كمسؤول.

3. في نافذة موجه الأوامر، قم بتشغيل أمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجحت، سيتم وضع علامة على اختبار الكشف كمكتمل، وسيظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم إلحاقه حديثا في حوالي 10 دقائق.

## <a name="linux-server"></a>Linux Server

> [!IMPORTANT]
> **القدرة على إلحاق نقاط نهاية Linux Server قيد المعاينة حاليا**. تأكد من تلبية المتطلبات التالية قبل إلحاق نقطة نهاية Linux Server:
> - تم تشغيل إعداد **ميزات المعاينة** . في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، انتقل إلى **ميزات معاينة الميزات** المتقدمة **العامة** > **لنقاط النهاية** **للإعدادات** >  >  > .
> - يمكنك تلبية [المتطلبات الأساسية Microsoft Defender لنقطة النهاية على Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).

### <a name="onboard-linux-server-endpoints"></a>إلحاق نقاط نهاية Linux Server

يمكنك استخدام الأساليب التالية لإلحاق مثيل Linux Server إلى Defender for Business:

- **البرنامج النصي المحلي:** راجع [نشر Microsoft Defender لنقطة النهاية على Linux يدويا](../defender-endpoint/linux-install-manually.md).
- **Ansible:** راجع [نشر Microsoft Defender لنقطة النهاية على Linux مع Ansible](../defender-endpoint/linux-install-with-ansible.md).
- **الشيف:** راجع [Deploy Defender لنقطة النهاية على Linux مع Chef](../defender-endpoint/linux-deploy-defender-for-endpoint-with-chef.md).
- **دميه:** راجع [نشر Microsoft Defender لنقطة النهاية على Linux باستخدام Puppet](../defender-endpoint/linux-install-with-puppet.md).

> [!NOTE]
> إلحاق مثيل من Linux Server إلى Defender for Business هو نفس إلحاق [Microsoft Defender لنقطة النهاية على Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md).

## <a name="view-a-list-of-onboarded-devices"></a>عرض قائمة بالأجهزة التي تم إلحاقها

لعرض قائمة الأجهزة التي تم إلحاقها ب Defender for Business، انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). في جزء التنقل، ضمن **نقاط النهاية**، اختر **مخزون الجهاز**.

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب لهذه الأجهزة ([Windows 10 و11 أو Mac أو الخوادم أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانتقل إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Defender for Business](mdb-configure-security-settings.md).
- راجع [بدء استخدام Defender for Business](mdb-get-started.md).

## <a name="mobile-devices"></a>[**الأجهزة المحمولة**](#tab/mobiles)

## <a name="mobile-devices"></a>الأجهزة المحمولة

ستحتاج Microsoft Intune إلى إلحاق الأجهزة المحمولة، مثل أجهزة Android وiOS/iPadOS. إذا كان لديك [Microsoft 365 Business Premium](../../business/index.yml)، فلديك Intune. 

راجع الموارد التالية للحصول على المساعدة في تسجيل هذه الأجهزة في Intune:

- [تسجيل أجهزة Android](/mem/intune/enrollment/android-enroll)
- [تسجيل أجهزة iOS أو iPadOS](/mem/intune/enrollment/ios-enroll)

بعد تسجيل جهاز في Intune، يمكنك إضافته إلى مجموعة أجهزة. [تعرف على المزيد حول مجموعات الأجهزة في Defender for Business](mdb-create-edit-device-groups.md).

## <a name="next-steps"></a>الخطوات التالية

- إذا كان لديك أجهزة أخرى لإلحاقها، فحدد علامة التبويب لهذه الأجهزة ([Windows 10 و11 أو Mac أو الخوادم أو الأجهزة المحمولة](#what-to-do))، واتبع الإرشادات الواردة في علامة التبويب هذه.
- إذا انتهيت من إلحاق الأجهزة، فانتقل إلى [الخطوة 5: تكوين إعدادات الأمان والنهج في Defender for Business](mdb-configure-security-settings.md).
- راجع [بدء استخدام Defender for Business](mdb-get-started.md).
