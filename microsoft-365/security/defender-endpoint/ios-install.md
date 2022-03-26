---
title: النشر المستند إلى التطبيق ل Microsoft Defender لنقطة النهاية على نظام التشغيل iOS
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على نظام التشغيل iOS باستخدام تطبيق
keywords: microsoft، defender، Microsoft Defender ل Endpoint، ios، التطبيق، التثبيت، النشر، إزالة التثبيت، intune
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 003c7cee09499fdec46f7d588e792878e0d3be66
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63569846"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>نشر Microsoft Defender لنقطة النهاية على نظام التشغيل iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يصف هذا الموضوع نشر Defender for Endpoint على iOS Intune Company Portal الأجهزة التي تم تسجيلها. لمزيد من المعلومات حول تسجيل جهاز Intune، راجع [تسجيل أجهزة iOS/iPadOS في Intune](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>قبل البدء

- تأكد من إمكانية الوصول إلى [مركز إدارة إدارة نقطة نهاية Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

- تأكد من أن تسجيل iOS يتم للمستخدمين. يحتاج المستخدمون إلى تعيين ترخيص Defender for Endpoint لكي يستخدم Defender for Endpoint على نظام iOS. راجع تعيين [التراخيص للمستخدمين](/azure/active-directory/users-groups-roles/licensing-groups-assign) للحصول على إرشادات حول كيفية تعيين التراخيص.

> [!NOTE]
> يتوفر Microsoft Defender ل Endpoint على نظام التشغيل iOS في [Apple App Store](https://aka.ms/mdatpiosappstore).

## <a name="deployment-steps"></a>خطوات النشر

نشر Defender لنقطة النهاية على نظام iOS عبر Intune Company Portal.

### <a name="add-ios-store-app"></a>إضافة تطبيق متجر iOS

1. في [مركز إدارة Microsoft Endpoint،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **تطبيق متجر AppsiOS** -> **/iPadOSAddiOS** ->  ->  وانقر فوق **تحديد**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center1.](images/ios-deploy-1.png)

1. في الصفحة **إضافة تطبيق** ، انقر فوق **البحث في متجر التطبيقات** وا اكتب **Microsoft Defender لنقطة** النهاية في شريط البحث. في المقطع نتائج البحث، انقر فوق *Microsoft Defender لنقطة النهاية* وانقر فوق **تحديد**.

1. حدد **iOS 11.0** كحد أدنى لنظام التشغيل. راجع المعلومات المتبقية حول التطبيق وانقر فوق **التالي**.

1. في المقطع **الواجبات** ، انتقل إلى المقطع **مطلوب** وحدد **إضافة مجموعة**. يمكنك بعد ذلك اختيار مجموعة (مجموعة) المستخدمين التي تريد استهداف Defender ل Endpoint على تطبيق iOS. انقر **فوق تحديد** ثم **فوق التالي**.

    > [!NOTE]
    > يجب أن تتكون مجموعة المستخدمين المحددة من المستخدمين المسجلين في Intune.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center2.](images/ios-deploy-2.png)

1. في المقطع *مراجعة + إنشاء* ، تحقق من صحة كل المعلومات التي تم إدخالها ثم حدد **إنشاء**. في لحظات قليلة، يجب إنشاء تطبيق Defender for Endpoint بنجاح، ويجب أن يظهر إعلام في الزاوية العلوية اليسرى من الصفحة.

1. في صفحة معلومات التطبيق التي يتم عرضها، في المقطع  جهاز العرض، حدد  حالة تثبيت الجهاز للتحقق من اكتمال تثبيت الجهاز بنجاح.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center3.](images/ios-deploy-3.png)

## <a name="complete-deployment-for-supervised-devices"></a>النشر الكامل للأجهزة المجهزة

يحتوي تطبيق Microsoft Defender ل Endpoint على iOS على قدرة متخصصة على أجهزة iOS/iPadOS التي تم توفيرها، نظرا لإمكانيات الإدارة المتزايدة التي يوفرها النظام الأساسي على هذه الأنواع من الأجهزة. كما يمكن أن يوفر حماية **ويب بدون إعداد VPN محلي على الجهاز**. يمنح ذلك المستخدمين تجربة سلسة مع الحماية من التصيد الاحتيالي وهجمة أخرى مستندة إلى الويب.

### <a name="configure-supervised-mode-via-intune"></a>تكوين "الوضع غير المهيئ" عبر Intune

بعد ذلك، قم بتكوين الوضع الذي تم تهيئته لتطبيق Defender for Endpoint من خلال نهج تكوين التطبيق.

   > [!NOTE]
   > ينطبق نهج تكوين التطبيق هذا للأجهزة المدارة فقط على الأجهزة المدارة ويجب أن يتم استهدافه لجميع أجهزة iOS المدارة كأفضل ممارسة.

1. سجل الدخول إلى إدارة نقاط النهاية من Microsoft [إدارة التطبيقات](https://go.microsoft.com/fwlink/?linkid=2109431) واذهب إلى **إضافة** \> سياسات **تكوين** \> تطبيقات **التطبيقات**. حدد **الأجهزة المدارة**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center4.](images/ios-deploy-4.png)

1. في الصفحة *إنشاء نهج تكوين التطبيق* ، قم بتوفير المعلومات التالية:
    - اسم النهج
    - النظام الأساسي: حدد iOS/iPadOS
    - التطبيق المستهدف: حدد **Microsoft Defender لنقطة النهاية** من القائمة

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center5.](images/ios-deploy-5.png)

1. في الشاشة التالية، حدد **استخدام مصمم التكوين** كالتنسق. حدد الخاصية التالية:
    - مفتاح التكوين: تم إصداره
    - نوع القيمة: سلسلة
    - قيمة التكوين: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center6.](images/ios-deploy-6.png)

1. حدد **التالي** لفتح صفحة **علامات النطاق** . علامات النطاق اختيارية. حدد **التالي** للمتابعة.

1. في صفحة **الواجبات** ، حدد المجموعات التي ستتلقى ملف التعريف هذا. بالنسبة إلى هذا السيناريو، من أفضل الممارسات استهداف **جميع الأجهزة**. لمزيد من المعلومات حول تعيين ملفات التعريف، راجع [تعيين ملفات تعريف المستخدمين والجهاز](/mem/intune/configuration/device-profile-assign).

   عند النشر إلى مجموعات المستخدمين، يجب على المستخدم تسجيل الدخول إلى جهاز قبل تطبيق النهج.

   انقر فوق **التالي**.

1. في الصفحة **مراجعة + إنشاء** ، عندما تنتهي، اختر **إنشاء**. يتم عرض ملف التعريف الجديد في قائمة ملفات تعريف التكوين.

1. بعد ذلك، يجب نشر ملف تعريف مخصص على أجهزة iOS التي تم نشرها. هذا الأمر لإمكانيات مكافحة التصيد الاحتيالي المحسنة. اتبع الخطوات أدناه:

    - تنزيل ملف تعريف المؤتمرات من [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - الانتقال إلى **ملفات تعريف DevicesiOS** -> **/iPadOSConfiguration** ->  **إنشاء** ->  **ملف تعريف**

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center7.](images/ios-deploy-7.png)
    
    - توفير اسم لملف التعريف. عند مطالبتك باستيراد ملف تعريف تكوين، حدد الملف الذي تم تنزيله من الخطوة السابقة.
    - في مقطع **الواجب** ، حدد مجموعة الأجهزة التي تريد تطبيق ملف التعريف هذا عليها. من أفضل الممارسات، يجب تطبيق ذلك على جميع أجهزة iOS المدارة. حدد **التالي**.
    - في الصفحة **مراجعة + إنشاء** ، عندما تنتهي، اختر **إنشاء**. يتم عرض ملف التعريف الجديد في قائمة ملفات تعريف التكوين.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>الأتمتة في ملف تعريف VPN (الأتمتة المبسطة)

بالنسبة للأجهزة غير الموفرة، يتم استخدام VPN لتوفير ميزة حماية الويب. هذه ليست VPN عادية وهي VPN محلية/ذاتية التكرار لا تأخذ حركة المرور خارج الجهاز.

>[!NOTE]
>بالنسبة للأجهزة التي تخضع للإشراف، لا تحتاج VPN إلى إمكانية حماية ويب وتتطلب من المسؤولين إعداد ملف تعريف تكوين على الأجهزة التي تم حمايتها. لتكوين الأجهزة التي تم تهيئتها، اتبع الخطوات في القسم [نشر كامل للأجهزة التي تم تهيئتها](#complete-deployment-for-supervised-devices) .

يمكن للمسؤولين تكوين الإعداد التلقائي لملف تعريف VPN. يؤدي ذلك إلى إعداد ملف تعريف VPN ل Defender for Endpoint تلقائيا دون أن يحتاج المستخدم إلى القيام بذلك أثناء التكوين. 

تبسط هذه الخطوة عملية الضبط من خلال إعداد ملف تعريف VPN. للحصول على تجربة التكهف أو اللمس الصامت، راجع القسم التالي: اللوحة التي تعمل [بلمسة صفرية](#zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview).

1. في [مركز إدارة إدارة نقطة نهاية Microsoft،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **DevicesConfiguration** ->  Profiles  -> **إنشاء ملف تعريف**.
1. اختر **النظام الأساسي** **ك iOS/iPadOS** ونوع **ملف التعريف** ك **VPN**. انقر **فوق إنشاء**.
1. اكتب اسما لملف التعريف وانقر فوق **التالي**.
1. حدد **VPN مخصص** لنوع الاتصال وفي القسم **Base VPN** ، أدخل ما يلي:
    - اسم الاتصال = Microsoft Defender لنقطة النهاية
    - عنوان خادم VPN = 127.0.0.1
    - أسلوب Auth = "اسم المستخدم وكلمة المرور"
    - تقسيم التهكية = تعطيل
    - معرف VPN = com.microsoft.scmx
    - في أزواج قيم المفاتيح، أدخل المفتاح **AutoOnboard** ثم قم بتعيين القيمة إلى **True**.
    - نوع VPN التلقائي = VPN عند الطلب
    - انقر **فوق** **إضافة لقواعد** عند الطلب وحدد أريد القيام بما يلي **= إنشاء VPN**، أريد تقييد **= كافة المجالات**.

    ![لقطة شاشة لإعدادات تكوين ملف تعريف VPN](images/ios-deploy-8.png)

1. انقر فوق التالي، ثم قم بتعيين ملف التعريف للمستخدمين المستهدفين.
1. في المقطع *مراجعة + إنشاء* ، تحقق من صحة كل المعلومات التي تم إدخالها ثم حدد **إنشاء**.

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint-preview"></a>التشغيل بدون لمس ل Microsoft Defender لنقطة النهاية (معاينة)

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

> [!NOTE]
> لا يمكن تكوين اللمس الصفري على أجهزة iOS التي يتم تسجيلها بدون تقارب المستخدم (أجهزة أقل من المستخدم أو أجهزة مشتركة).

يمكن للمسؤولين تكوين Microsoft Defender ل Endpoint لنشره وتنشيطه بصمت. في هذا التدفق، ينشئ المسؤول ملف تعريف نشر، ويخطر المستخدم ببساطة بالثبيت. يتم تثبيت Defender ل Endpoint تلقائيا دون الحاجة إلى أن يقوم المستخدم بفتح التطبيق. اتبع الخطوات أدناه لإعداد النشر الصامت أو بدون لمس ل Defender for Endpoint على أجهزة iOS التي تم تسجيلها:

1. في [مركز إدارة إدارة نقطة نهاية Microsoft،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **DevicesConfiguration** >  Profiles  > **إنشاء ملف تعريف**.
1. اختر **النظام الأساسي** **ك iOS/iPadOS** ونوع **ملف التعريف** ك **VPN**. حدد **إنشاء**.
1. اكتب اسما لملف التعريف وحدد **التالي**.
1. حدد **VPN مخصص** لنوع الاتصال وفي القسم **Base VPN** ، أدخل ما يلي:
    - اسم الاتصال = Microsoft Defender لنقطة النهاية
    - عنوان خادم VPN = 127.0.0.1
    - أسلوب Auth = "اسم المستخدم وكلمة المرور"
    - تقسيم التهكية = تعطيل
    - معرف VPN = com.microsoft.scmx
    - في أزواج قيم المفاتيح، أدخل **المفتاح SilentOnboard** ثم قم بتعيين القيمة إلى **True**.
    - نوع VPN التلقائي = VPN عند الطلب
    - حدد **إضافة** لقواعد **عند** الطلب وحدد أريد القيام بما يلي **= إنشاء VPN**، أريد تقييد **= كافة المجالات**.

    ![لقطة شاشة لتكوين ملف تعريف VPN.](images/ios-deploy-9.png)

1. حدد **التالي** ، ثم قم بتعيين ملف التعريف للمستخدمين المستهدفين.
1. في المقطع *مراجعة + إنشاء* ، تحقق من صحة كل المعلومات التي تم إدخالها ثم حدد **إنشاء**.

بمجرد إنجاز التكوين أعلاه ومزامنته مع الجهاز، يتم اتخاذ الإجراءات التالية على جهاز (أجهزة) iOS المستهدفة:
    - سيتم نشر Microsoft Defender ل Endpoint وإلوحاء بصمت وسيرى الجهاز في مدخل Defender for Endpoint.
    - سيتم إرسال إعلام مؤقت إلى جهاز المستخدم.
    - سيتم تنشيط Web Protection وميزات أخرى.

   > [!NOTE]
   > بالنسبة للأجهزة التي تم تهيئتها، على الرغم من أن ملف تعريف VPN غير مطلوب، لا يزال يمكن للمسؤولين إعداد الإعداد بدون لمس من خلال تكوين ملف تعريف VPN ل Defender for Endpoint من خلال Intune. سيتم نشر ملف تعريف VPN على الجهاز ولكن سيكون موجودا فقط على الجهاز كملف تعريف تمريري ويمكن حذفه بعد الالوح الأولي.

## <a name="complete-onboarding-and-check-status"></a>إكمال حالة الboarding والتحقق

1. بمجرد تثبيت Defender for Endpoint على نظام التشغيل iOS على الجهاز، سترى أيقونة التطبيق.

    ![لقطة شاشة ل "وصف هاتف ذكي" يتم إنشاؤه تلقائيا.](images/41627a709700c324849bf7e13510c516.png)

2. اضغط على أيقونة تطبيق Defender for Endpoint (MSDefender) واتبع الإرشادات التي تظهر على الشاشة لإكمال خطوات اللصق. تتضمن التفاصيل قبول المستخدم النهائي لأذونات iOS المطلوبة بواسطة Defender for Endpoint على iOS.

3. عند نجاح عملية الضم، سيبدأ الجهاز في الظهور على قائمة الأجهزة في Microsoft 365 Defender المدخل.

    > [!div class="mx-imgBorder"]
    > ![لقطة شاشة لوصف هاتف خليوي يتم إنشاؤه تلقائيا.](images/device-inventory-screen.png)


## <a name="next-steps"></a>الخطوات التالية

- [تكوين نهج حماية التطبيق لتضمين إشارات خطر Defender for Endpoint (MAM)](ios-install-unmanaged.md)
- [تكوين Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
