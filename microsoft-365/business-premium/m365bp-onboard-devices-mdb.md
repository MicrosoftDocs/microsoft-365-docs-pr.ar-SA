---
title: إلحاق أجهزة مؤسستك Microsoft Defender for Business
description: إلحاق أجهزة مؤسستك Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.date: 07/19/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 0578aa2e672a0d485057ac983ed85d10828c952d
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893944"
---
# <a name="onboard-enrolled-devices-to-microsoft-defender-for-business"></a>إلحاق الأجهزة المسجلة Microsoft Defender for Business

تتضمن Microsoft 365 Business Premium [Microsoft Defender for Business](../security/defender-business/mdb-overview.md)، وهو حل أمان نقطة النهاية للشركات الصغيرة والمتوسطة الحجم. يوفر Defender for Business حماية الجيل التالي (الحماية من الفيروسات والحماية من البرامج الضارة والحماية المقدمة من السحابة) وحماية جدار الحماية وتصفية محتوى الويب والمزيد لأجهزة شركتك. يتم تطبيق الحماية عند إلحاق الأجهزة وتطبيق نهج الأمان على تلك الأجهزة.

لإلحاق الأجهزة ب Defender for Business، يمكنك الاختيار من بين عدة خيارات:

- [الإلحاق التلقائي لأجهزة Windows المسجلة بالفعل في Microsoft Intune](#use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune)
- [برنامج نصي محلي لإلحاق أجهزة Windows وMac ب Defender for Business](#use-a-local-script-to-onboard-windows-and-mac-devices-to-defender-for-business) (للأجهزة غير المسجلة بالفعل في Intune)
- [Intune لتسجيل الأجهزة الجديدة، بما في ذلك الأجهزة المحمولة](#use-intune-to-enroll-devices) (Windows وMac وiOS وAndroid) ثم تطبيق نهج Defender for Business على تلك الأجهزة

تتضمن هذه المقالة أيضا:

- [ماذا عن الخوادم؟](#what-about-servers) (جديد!)
- [كيفية تشغيل اختبار الكشف على جهاز Windows](#run-a-detection-test-on-a-windows-device)
- [كيفية إلحاق الأجهزة تدريجيا](#onboard-devices-gradually)
- [كيفية إيقاف تشغيل جهاز](#offboard-a-device) إذا تم استبدال جهاز أو إذا غادر شخص ما المؤسسة

> [!IMPORTANT]
> إذا حدث خطأ ما وفشلت عملية الإلحاق، فراجع [Microsoft Defender for Business استكشاف الأخطاء وإصلاحها](../security/defender-business/mdb-troubleshooting.yml).

## <a name="use-automatic-onboarding-for-windows-devices-that-are-already-enrolled-in-intune"></a>استخدام الإلحاق التلقائي لأجهزة Windows المسجلة بالفعل في Intune

يمكنك إلحاق أجهزة عميل Windows ب Defender for Business تلقائيا إذا كانت هذه الأجهزة مسجلة بالفعل في Intune. يكتشف Defender for Business أجهزة عميل Windows المسجلة بالفعل في Intune، ويطالبك باختيار ما إذا كنت تريد إلحاق هذه الأجهزة تلقائيا. ثم يتم تطبيق نهج الأمان والإعدادات في Defender for Business على تلك الأجهزة. نستدعي هذه العملية *الإلحاق التلقائي*. 

يساعد الإلحاق التلقائي على حماية أجهزتك على الفور تقريبا. لاحظ أن خيار الإلحاق التلقائي ينطبق على أجهزة عميل Windows فقط، إذا تم استيفاء الشروط التالية:

- كانت مؤسستك تستخدم بالفعل Intune أو Mobile إدارة الجهاز (MDM) في Intune قبل أن تحصل على Defender for Business (Microsoft 365 Business Premium العملاء لديهم بالفعل Microsoft Intune و MDM).
- لديك بالفعل أجهزة عميل Windows مسجلة في Intune.

> [!TIP]
> إذا تمت مطالبتك باستخدام الإلحاق التلقائي، نوصي بتحديد خيار "جميع الأجهزة المسجلة". وبهذه الطريقة، عندما يتم تسجيل أجهزة Windows في Intune لاحقا، سيتم إلحاقها ب Defender for Business تلقائيا.

لمعرفة المزيد حول الإلحاق التلقائي، راجع [استخدام المعالج لإعداد Microsoft Defender for Business](../security/defender-business/mdb-use-wizard.md).

## <a name="use-a-local-script-to-onboard-windows-and-mac-devices-to-defender-for-business"></a>استخدام برنامج نصي محلي لإلحاق أجهزة Windows وMac ب Defender for Business

يمكنك استخدام برنامج نصي محلي لإلحاق أجهزة Windows وMac. عند تشغيل البرنامج النصي للإلحاق على جهاز، فإنه ينشئ ثقة مع Azure Active Directory (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز في Intune (إذا لم يكن مسجلا بالفعل)، ثم يقوم بإلحاق الجهاز ب Defender for Business. يمكنك إلحاق ما يصل إلى 10 أجهزة في كل مرة باستخدام البرنامج النصي المحلي.

راجع [الأجهزة الملحقة Microsoft Defender for Business](../security/defender-business/mdb-onboard-devices.md) للحصول على إرشادات مفصلة.

## <a name="use-intune-to-enroll-devices"></a>استخدام Intune لتسجيل الأجهزة

لتسجيل جهاز، يمكنك تسجيله بنفسك، أو السماح للمستخدمين بتسجيل الدخول إلى تطبيق مدخل الشركة، وتسجيل أجهزتهم، ثم تثبيت أي تطبيقات مطلوبة. 

إذا كنت تستخدم بالفعل Intune أو Mobile إدارة الجهاز قبل حصولك على Defender for Business، يمكنك الاستمرار في استخدام Intune لإلحاق أجهزة مؤسستك. باستخدام Intune، يمكنك إلحاق أجهزة الكمبيوتر وأجهزة الكمبيوتر اللوحية والهواتف، بما في ذلك أجهزة iOS وAndroid.

راجع [تسجيل الجهاز في Microsoft Intune](/mem/intune/enrollment/device-enrollment). 

## <a name="what-about-servers"></a>ماذا عن الخوادم؟

بشكل افتراضي، لا يتم دعم الخوادم في Microsoft 365 Business Premium والإصدار المستقل من Defender for Business. ومع ذلك، **فإن القدرة على إلحاق خادم، مثل نقطة نهاية تعمل بنظام Windows Server أو Linux Server، أصبحت الآن في وضع المعاينة**! 

راجع [كيفية الحصول على خوادم Microsoft Defender for Business (معاينة).](../security/defender-business/get-defender-business-servers.md)

## <a name="run-a-detection-test-on-a-windows-device"></a>تشغيل اختبار الكشف على جهاز Windows

بعد إلحاق أجهزة Windows ب Defender for Business، يمكنك تشغيل اختبار الكشف على جهاز Windows للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على جهاز Windows، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه الأوامر كمسؤول.

3. في نافذة موجه الأوامر، قم بتشغيل أمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، يتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجح، يتم وضع علامة على اختبار الكشف كمكتمل، ويظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم إلحاقه حديثا في حوالي عشر دقائق.

## <a name="onboard-devices-gradually"></a>إلحاق الأجهزة تدريجيا

إذا كنت تفضل إلحاق الأجهزة على مراحل، والتي نطلق *عليها اسم الإعداد التدريجي للجهاز*، فاتبع الخطوات التالية: 

1. تحديد مجموعة من الأجهزة لإلحاقها.

2. انتقل إلى مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، وسجل الدخول.

3. في جزء التنقل، اختر **"نقاط نهاية الإعدادات** > "، ثم ضمن **"إدارة الجهاز"**، اختر **"إلحاق".**

4. حدد نظام تشغيل (مثل **Windows 10 و11)،** ثم اختر أسلوب إلحاق (مثل **البرنامج النصي المحلي**). اتبع الإرشادات المقدمة للأسلوب الذي حددته.

5. كرر هذه العملية لكل مجموعة من الأجهزة التي تريد إلحاقها. 

> [!TIP]
> لا يتعين عليك استخدام حزمة الإلحاق نفسها في كل مرة تقوم فيها بإلحاق الأجهزة. على سبيل المثال، يمكنك استخدام برنامج نصي محلي لإلحاق بعض الأجهزة، وفي وقت لاحق، يمكنك اختيار طريقة أخرى لإلحاق المزيد من الأجهزة.

## <a name="offboard-a-device"></a>إيقاف تشغيل جهاز

إذا كنت تريد إيقاف تشغيل جهاز، فاستخدم أحد الإجراءات التالية:

1. في جزء التنقل، اختر **"إعدادات"**، ثم اختر **"نقاط النهاية**".

2. ضمن **إدارة الأجهزة**، اختر **"إيقاف الإلحاق**".

3. حدد نظام تشغيل، مثل **Windows 10 و11**، ثم ضمن **"Offboard a device**"، في قسم **أسلوب النشر**، اختر **البرنامج النصي المحلي**. 

4. في شاشة التأكيد، راجع المعلومات، ثم اختر **"تنزيل"** للمتابعة.

5. حدد **تنزيل حزمة إيقاف الإلحاق**. نوصي بحفظ حزمة الإلحاق إلى محرك أقراص قابل للإزالة.

6. قم بتشغيل البرنامج النصي على كل جهاز تريد إيقاف تشغيله. هل تحتاج إلى مساعدة في هذه المهمة؟ راجع الموارد التالية:   

   - أجهزة Windows: [إيقاف تشغيل أجهزة Windows باستخدام برنامج نصي محلي](../security/defender-endpoint/configure-endpoints-script.md#offboard-devices-using-a-local-script) 
   - Mac: [إلغاء التثبيت على Mac](../security/defender-endpoint/mac-resources.md#uninstalling)

> [!IMPORTANT]
> يؤدي إلغاء إلحاق جهاز إلى توقف الأجهزة عن إرسال البيانات إلى Defender for Business. ومع ذلك، يتم الاحتفاظ بالبيانات التي تم تلقيها قبل الإلحاق لمدة تصل إلى ستة (6) أشهر.

## <a name="next-objective"></a>الهدف التالي

[إعداد الحماية لأجهزتك التي تعمل بنظام التشغيل Windows](m365bp-protection-settings-for-windows-10-devices.md).
