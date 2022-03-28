---
title: الأجهزة المجهزة على Microsoft Defender for Business
description: التعرف على خيارات االتعليم على الأجهزة في Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 590810e7e8a5486816310da35968d6d9b3659330
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575950"
---
# <a name="onboard-devices-to-microsoft-defender-for-business"></a>الأجهزة المجهزة على Microsoft Defender for Business

> [!IMPORTANT]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء[](../../business-premium/index.md)، بدءا من 1 مارس 2022. يتم عرض Defender for Business لاشتراك مستقل في المعاينة، وسينتهى طرحه تدريجيا للعملاء وشركاء المعلومات الذين سجلوا هنا [](https://aka.ms/mdb-preview) لطلبه. تتضمن [المعاينة مجموعة أولية من السيناريوهات](mdb-tutorials.md#try-these-preview-scenarios)، وسنضيف القدرات بشكل منتظم.
> 
> تتعلق بعض المعلومات الواردة في هذه المقالة بالمنتجات/الخدمات التي تم إصدارها مسبقا التي قد يتم تعديلها بشكل كبير قبل إصدارها تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، للمعلومات المتوفرة هنا. 

باستخدام Microsoft Defender for Business، لديك العديد من الخيارات للاختيار من بينها ل علي أجهزة شركتك. تجول هذه المقالة بين الخيارات وتتضمن نظرة عامة حول كيفية عمل الضم.

>
> **هل لديك دقيقة؟**
> الرجاء إجراء <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">استطلاع قصير حول Microsoft Defender for Business</a>. إننا نحب أن نستمع إلى هذه التكاتف!
>

## <a name="get-the-device-onboarding-guide"></a>الحصول على دليل تشغيل الجهاز

استخدم الدليل والمعلومات التالية لاختيار الخيار الأفضل للشركة.

[:::image type="content" source="media/mdb-device-onboarding.png" alt-text="لقطة شاشة لرسم تخطيطي ل &quot;إضافة جهاز&quot;":::](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) <br/>
[PDF](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.pdf) |  [Visio](https://download.microsoft.com/download/4/d/2/4d2d8a86-2130-45b4-ba42-2997c854383a/MDB-DeviceOnboardingFlow-March2022.vsdx)

## <a name="what-to-do"></a>ما يجب فعله

1. [راجع خياراتك الخاصة بأجهزة التكهين](#device-onboarding-methods)، وحدد طريقة. 

   - [استخدام الالتحاق التلقائي للأجهزة Windows المسجلين بالفعل في إدارة نقاط النهاية من Microsoft](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager)
   - [استخدام برنامج نصي محلي ل Windows أو أجهزة macOS](#local-script-in-defender-for-business)
   - [استخدام إدارة نقاط النهاية من Microsoft على أجهزة Windows أو macOS أو الأجهزة المحمولة](#microsoft-endpoint-manager)
   - [تعرف على كيفية إعداد الجهاز باستخدام تكوين أمان Microsoft Defender for Business](#microsoft-defender-for-business-security-configuration)

2. [تشغيل اختبار الكشف على](#run-a-detection-test) الأجهزة المجهزة Windows حديثا.

3. [راجع الخطوات التالية](#next-steps). 

تتضمن هذه المقالة أيضا معلومات حول [إيقاف تشغيل جهاز](#offboarding-a-device).

## <a name="device-onboarding-methods"></a>أساليب تشغيل الأجهزة

يوفر لك Defender for Business العديد من الطرق المختلفة لتكبس الأجهزة، سواء كنت تستخدم أجهزة إدارة نقاط النهاية من Microsoft بالفعل، أو إذا كنت تريد تجربة مبسطة للتو. تتضمن الأساليب الأكثر استخداما لضم الأجهزة إلى Defender for Business ما يلي:

- **الالتحاق التلقائي** Windows الأجهزة التي تم تسجيلها بالفعل في إدارة نقاط النهاية من Microsoft. تعمل ميزة التكهين التلقائي على إعداد اتصال بين Defender for Business إدارة نقاط النهاية من Microsoft، ثم Windows الأجهزة إلى Defender for Business. لاستخدام هذا الخيار، يجب أن تكون أجهزتك مسجله بالفعل في إدارة نقاط النهاية. للتعرف على المزيد، راجع [التكهين التلقائي](#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager).

- **البرنامج النصي** المحلي ل Windows وأجهزة macOS إلى Defender for Business يدويا. يمكنك تشغيل ما يصل إلى 10 أجهزة في كل مرة باستخدام البرنامج النصي المحلي. لمعرفة المزيد، راجع [البرنامج النصي المحلي في Defender for Business](#local-script-in-defender-for-business).

- **Microsoft Intune** أو **إدارة نقاط النهاية من Microsoft** على Windows وأجهزة macOS والأجهزة المحمولة. يمكنك تسجيل الأجهزة في إدارة نقاط النهاية، ثم إلحاق أجهزتك ب Defender for Business. [Microsoft 365 Business Premium](../../business-premium/index.md) العملاء بالفعل Microsoft Intune، وكل من [](/mem/intune/fundamentals/what-is-intune)Microsoft Intune الأجهزة المحمولة وإدارة الأجهزة المحمولة أصبحت الآن جزءا من إدارة نقاط النهاية[](/mem/intune/enrollment/device-enrollment). لاستخدام هذا الأسلوب[، راجع إدارة نقاط النهاية من Microsoft](#microsoft-endpoint-manager).

- **تكوين أمان Microsoft Defender for Business** للأجهزة المجهزة مباشرة في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). لاستخدام هذا الخيار، يمكنك تكوين إعدادات معينة لتسهيل الاتصال بين Defender for Business إدارة نقاط النهاية. بعد ذلك، يمكنك تشغيل الأجهزة في Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) باستخدام حزمة تقوم بتحديدها وتنزيلها وتشغيلها على كل جهاز. يتم إنشاء الثقة بين الأجهزة، كما يتم دفع Azure Active Directory (Azure AD) ونهج أمان Defender for Business إلى الأجهزة. لمعرفة المزيد، راجع [تكوين أمان Microsoft Defender for Business](#microsoft-defender-for-business-security-configuration). 

> [!IMPORTANT]
> إذا حدث خطأ ما وفشلت عملية التكعيب، فشاهد استكشاف الأخطاء وإصلاحها في [Microsoft Defender for Business](mdb-troubleshooting.yml).

## <a name="automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager"></a>الالتحاق التلقائي للأجهزة Windows المسجلين في إدارة نقاط النهاية من Microsoft

ينطبق خيار التكهين التلقائي على Windows الأجهزة فقط. تتوفر ميزة التهيئة التلقائية إذا تم تحقيق الشروط التالية:

- كانت شركتك تستخدم بالفعل إدارة نقاط النهاية من Microsoft أو Microsoft Intune أو إدارة أجهزة المحمول (MDM) في Microsoft Intune قبل أن حصلت على Defender for Business

- لديك بالفعل أجهزة Windows مسجلين في إدارة نقاط النهاية

إذا Windows تم تسجيل أجهزة أخرى بالفعل في إدارة نقاط النهاية، سيكشف Defender for Business عن هذه الأجهزة أثناء عملية إعداد Defender for Business وتكوينه. سيتم سؤالك عما إذا كنت تريد استخدام التركب التلقائي لجميع أجهزة الكمبيوتر Windows أو بعضها. يمكنك الإضافة إلى جميع Windows مرة واحدة، أو تحديد أجهزة معينة للبدء بها، ثم إضافة المزيد من الأجهزة في وقت لاحق.

> [!TIP]
> نوصي بتحديد الخيار "جميع الأجهزة التي تم تسجيلها". بهذه الطريقة، Windows تسجيل الأجهزة في إدارة نقاط النهاية لاحقا، سيتم إلحاقها في Defender for Business تلقائيا. بالإضافة إلى ذلك، إذا كنت تدير سياسات الأمان وإعداداته في إدارة نقاط النهاية، نوصي بالتبديل إلى مدخل Microsoft 365 Defender لإدارة أجهزتك ونهجك وإعداداتك. لمعرفة المزيد، راجع [اختيار مكان إدارة سياسات](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices) الأمان والأجهزة.

لمعرفة المزيد حول الإعداد التلقائي، راجع الخطوة 2 في استخدام [المعالج لإعداد Microsoft Defender for Business](mdb-use-wizard.md).

## <a name="local-script-in-defender-for-business"></a>البرنامج النصي المحلي في Defender for Business

يمكنك استخدام برنامج نصي محلي ل Windows وأجهزة Mac. عند تشغيل البرنامج النصي ل إلحاق على جهاز، فإنه ينشئ ثقة مع Azure Active Directory (إذا لم تكن هذه الثقة موجودة بالفعل)، ويسجل الجهاز في إدارة نقاط النهاية من Microsoft (إذا لم يكن مسجلا بالفعل)، ثم يتم إلحاق الجهاز ب Defender for Business. هذا الأسلوب مفيد ل عند وضع الأجهزة في Defender for Business. يمكنك إعداد ما يصل إلى 10 أجهزة في كل مرة.

1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول.

2. في جزء التنقل **، اختر الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الأجهزة**، اختر **إلحاق**.

3. حدد نظام تشغيل، مثل **Windows 10 و11** أو **macOS**، ثم في المقطع أسلوب النشر، اختر **برنامج نصي محلي**. 

4. حدد **تنزيل حزمة التكهيل**. نوصيك ب حفظ حزمة التكفير إلى محرك أقراص قابل للإزالة. (إذا قمت بتحديد **macOS،** فحدد أيضا **تنزيل حزمة** التثبيت واحفظها على جهازك القابل للإزالة.)

5. اتبع الإرشادات في الجدول التالي:

   | نظام التشغيل | الإجراء |
   |---|---|
   | بالنسبة لنظام التشغيل | 1. على جهاز Windows، استخرج محتويات حزمة التكوين إلى موقع، مثل مجلد سطح المكتب. يجب أن يكون لديك ملف باسم `WindowsDefenderATPLocalOnboardingScript.cmd`. <br/><br/>2. افتح موجه الأوامر كمسؤول.<br/><br/>3. اكتب موقع ملف البرنامج النصي. على سبيل المثال، إذا نسخت الملف إلى مجلد سطح المكتب، يمكنك كتابة: `%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd`، ثم اضغط على المفتاح Enter (أو حدد **موافق**).<br/><br/>4. بعد تشغيل البرنامج النصي، انتقل إلى [تشغيل اختبار الكشف](#run-a-detection-test). |
   | macOS | 1. على كمبيوتر Mac، احفظ حزمة التثبيت في `wdav.pkg` دليل محلي. <br/><br/>2. احفظ حزمة التركيب بنفس `WindowsDefenderATPOnboardingPackage.zip` الدليل الذي استخدمته لحزمة التثبيت. <br/><br/>3. استخدم "البحث" للانتقال `wdav.pkg` إلى الذي حفظته، ثم افتحه.<br/><br/>4. حدد **متابعة**، ووافق على شروط الترخيص، ثم أدخل كلمة المرور عند مطالبتك بذلك.<br/><br/>5. وستتم مطالبتك بالسماح بتثبيت برنامج تشغيل من Microsoft (إما "تم حظر ملحق النظام" أو "التثبيت مع الانتظار"، أو كليهما. يجب السماح بتثبيت برنامج التشغيل. للسماح التثبيت، حدد فتح تفضيلات **الأمان** أو **فتح** >  تفضيلات **النظامأمان & الخصوصية**، ثم حدد **السماح**.<br/><br/>6. استخدم الأمر Python التالي في Bash لتشغيل حزمة التكرير: `/usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py`. <br/><br/>7. لتأكيد تقترن الجهاز بالشركة، استخدم الأمر Python التالي في Bash: `mdatp health --field org_id`.<br/><br/>8. إذا كنت تستخدم macOS 10.15 (Catalina) أو أي وقت لاحق، فامنح Defender for Business موافقة لحماية جهازك. انتقل إلى **تفضيلات** >  **النظامالخصوص &** **PrivacyPrivacyFull** >  >  **Disk Access**.  حدد أيقونة التأمين التي تريد إدخال تغييرات (أسفل مربع الحوار)، ثم حدد Microsoft Defender for Business (أو Defender for Endpoint، إذا كان هذا ما تراه). <br/><br/>9. للتحقق من أن الجهاز تم الإستخدام، استخدم الأمر التالي في Bash: `mdatp health --field real_time_protection_enabled`.    |

## <a name="microsoft-endpoint-manager"></a>إدارة نقاط النهاية من Microsoft

إذا كنت تستخدم إدارة نقاط النهاية (الذي يتضمن Microsoft Intune وإدارة أجهزة المحمول)، قبل الحصول على Defender for Business، يمكنك الاستمرار في استخدام إدارة نقاط النهاية لضم أجهزة شركتك. باستخدام إدارة نقاط النهاية، يمكنك تشغيل أجهزة الكمبيوتر وأجهزة الكمبيوتر اللوحية والهواتف، بما في ذلك أجهزة iOS وAndroid.

راجع [تسجيل الجهاز في Microsoft Intune](/mem/intune/enrollment/device-enrollment).

## <a name="microsoft-defender-for-business-security-configuration"></a>تكوين أمان Microsoft Defender for Business

> [!NOTE]
> إذا كنت تستخدم بالفعل إدارة نقاط النهاية لإدارة أجهزتك ونهج الأمان، فتخطى هذه الطريقة، ثم راجع [إدارة نقاط النهاية من Microsoft بدلا من](#microsoft-endpoint-manager) ذلك.

تم بناء تكوين أمان Microsoft Defender for Business على إمكانية تعرف باسم [إدارة الأمان ل Microsoft Defender ل Endpoint (معاينة)](/mem/intune/protect/mde-security-integration). يمكنك من إلحاق الأجهزة ب Defender for Business في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) دون الحاجة إلى تسجيل هذه الأجهزة بشكل كامل في إدارة نقاط النهاية من Microsoft مسبقا. 

تمكنك هذه الطريقة من االأجهزة المجهزة وإدارة برامج الحماية من الفيروسات ونهج جدار الحماية في Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). إليك كيفية عمل كل ذلك:

1. قم بتنزيل حزمة التكئب من مدخل Microsoft 365 Defender، ثم قم بتشغيل الحزمة على أجهزتك لتحميل هذه الأجهزة إلى Defender for Business.

2. يعمل تشغيل الحزمة على إنشاء الثقة بين كل جهاز (إذا لم تكن الثقة موجودة بالفعل) و Azure Active Directory (Azure AD). 

3. تتواصل الأجهزة مع إدارة نقاط النهاية باستخدام هوية Azure AD، كما يتم دفع سياسات الأمان في Defender for Business إلى الأجهزة.

4. يمكنك عرض أجهزتك ونهجك في كل من مدخل Microsoft 365 Defender ومركز إدارة إدارة نقاط النهاية ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)).

لاستخدام هذا الخيار، يجب تكوين إعدادات معينة مسبقا. لمعرفة المزيد، بما في ذلك المتطلبات الأساسية وأنظمت التشغيل المعتمدة، راجع [إدارة Microsoft Defender لنقطة النهاية على الأجهزة](/mem/intune/protect/mde-security-integration) التي تستخدم إدارة نقاط النهاية من Microsoft.

## <a name="run-a-detection-test"></a>تشغيل اختبار الكشف

بعد أن قمت Windows الأجهزة إلى Defender for Business، يمكنك تشغيل اختبار الكشف على جهاز Windows للتأكد من أن كل شيء يعمل بشكل صحيح.

1. على Windows، أنشئ مجلدا: `C:\test-MDATP-test`.

2. افتح موجه الأوامر كمسؤول.

3. في نافذة موجه الأوامر، تشغيل الأمر PowerShell التالي:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```

بعد تشغيل الأمر، سيتم إغلاق نافذة موجه الأوامر تلقائيا. إذا نجح، سيتم وضع علامة على اختبار الكشف كمكتمل، وسيظهر تنبيه جديد في مدخل Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) للجهاز الذي تم تحديثه حديثا في غضون 10 دقائق.

## <a name="gradual-device-onboarding"></a>تشغيل الجهاز تدريجيا

يمكنك اجهزه شركتك علي مراحل. *نطلق على هذا الجهاز التدريجي الاستدعاء*. 

1. تحديد مجموعة من الأجهزة لل متنها.

2. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))، ثم سجل الدخول.

3. في جزء التنقل **، اختر الإعدادات** >  **Endpoints**، ثم ضمن **إدارة الأجهزة**، اختر **إلحاق**.

4. حدد نظام تشغيل (مثل **Windows 10 و11)**، ثم اختر أسلوبا لل متن الطائرة (مثل **البرنامج النصي المحلي**). اتبع الإرشادات المتوفرة لطريقة تحديدك.

5. كرر هذه العملية لكل مجموعة من الأجهزة التي تريد اعادتها. 

> [!TIP]
> لست بحاجة إلى استخدام نفس حزمة الإستخدام في كل مرة تقوم فيها بأجهزة الإستخدام. على سبيل المثال، يمكنك استخدام برنامج نصي محلي للوح بعض الأجهزة، وفي وقت لاحق، يمكنك اختيار طريقة أخرى للوح المزيد من الأجهزة.

## <a name="offboarding-a-device"></a>إيقاف تشغيل جهاز

إذا كنت تريد إيقاف تشغيل جهاز، فاستخدم أحد الإجراءات التالية:

| نظام التشغيل | الإجراء |
|---|---|
| بالنسبة لنظام التشغيل | 1. انتقل إلى Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) ثم سجل الدخول.<br/><br/>2. في جزء التنقل، **اختر الإعدادات،** ثم اختر **نقاط النهاية**.<br/><br/>3. ضمن **إدارة الأجهزة**، اختر **إيقاف التشغيل**.<br/><br/>4. حدد نظام تشغيل **، مثل Windows 10 و11**، ثم ضمن **إيقاف** تشغيل جهاز، في المقطع أسلوب النشر، اختر **برنامج نصي محلي**. <br/><br/>5. في شاشة التأكيد، راجع المعلومات، ثم اختر **تنزيل** للمتابعة.<br/><br/>6. حدد **تنزيل حزمة إيقاف التشغيل**. نوصيك ب حفظ حزمة إيقاف التشغيل إلى محرك أقراص قابل للإزالة.<br/><br/>7. تشغيل البرنامج النصي على كل جهاز تريد إيقاف تشغيله.| 
| macOS | 1. انتقل إلى **FinderApplications** > . <br/><br/>2. انقر بيمين فوق Microsoft Defender for Business، ثم اختر **نقل إلى سلة المهملات**. <br/><br/>--- أو --- <br/><br/> استخدم الأمر التالي: `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.|

> [!IMPORTANT]
> يؤدي إيقاف تشغيل الجهاز إلى إيقاف الأجهزة عن إرسال البيانات إلى Defender for Business. ومع ذلك، يتم الاحتفاظ بالبيانات التي تم تلقيها قبل الخروج لمدة تصل إلى ستة (6) أشهر.

## <a name="next-steps"></a>الخطوات التالية

تابع إلى:

- [الخطوة 5: تكوين إعدادات الأمان ونهجه في Microsoft Defender for Business](mdb-configure-security-settings.md)

- [بدء استخدام Microsoft Defender for Business](mdb-get-started.md) 
