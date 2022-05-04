---
title: النشر المستند إلى التطبيق Microsoft Defender لنقطة النهاية على iOS
ms.reviewer: ''
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على iOS باستخدام تطبيق
keywords: microsoft, defender, Microsoft Defender لنقطة النهاية, ios, app, installation, deploy, uninstallation, intune
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
ms.openlocfilehash: ed4b69aae3a29478a2b8bfb98d8ab605e5af28a8
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188647"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-ios"></a>نشر Microsoft Defender لنقطة النهاية على iOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يصف هذا الموضوع نشر Defender لنقطة النهاية على iOS على Intune Company Portal الأجهزة المسجلة. لمزيد من المعلومات حول تسجيل جهاز Intune، راجع [تسجيل أجهزة iOS/iPadOS في Intune](/mem/intune/enrollment/ios-enroll).

## <a name="before-you-begin"></a>قبل البدء

- تأكد من أن لديك حق الوصول إلى [مركز إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

- تأكد من إجراء تسجيل iOS للمستخدمين. يحتاج المستخدمون إلى تعيين ترخيص Defender لنقطة النهاية لاستخدام Defender لنقطة النهاية على iOS. راجع [تعيين التراخيص للمستخدمين](/azure/active-directory/users-groups-roles/licensing-groups-assign) للحصول على إرشادات حول كيفية تعيين التراخيص.

> [!NOTE]
> يتوفر Microsoft Defender لنقطة النهاية على iOS في [App Store Apple](https://aka.ms/mdatpiosappstore).

## <a name="deployment-steps"></a>خطوات النشر

نشر Defender لنقطة النهاية على iOS عبر Intune Company Portal.

### <a name="add-ios-store-app"></a>إضافة تطبيق متجر iOS

1. في [مركز إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى تطبيق متجر **AppsiOS** -> **/iPadOSAddiOS** ->  ->  وانقر فوق **"تحديد**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-1.png" alt-text="علامة التبويب &quot;إضافة تطبيقات&quot; في مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/ios-deploy-1.png":::

1. في صفحة **"إضافة تطبيق**"، انقر فوق **"البحث في App Store**" واكتب **Microsoft Defender لنقطة النهاية** في شريط البحث. في قسم نتائج البحث، انقر فوق *Microsoft Defender لنقطة النهاية* وانقر فوق **"تحديد**".

1. حدد **iOS 11.0** كأدنى نظام تشغيل. راجع بقية المعلومات حول التطبيق وانقر فوق **"التالي**".

1. في المقطع **"الواجبات** "، انتقل إلى المقطع **"مطلوب** " وحدد **"إضافة مجموعة**". يمكنك بعد ذلك اختيار مجموعة (مجموعات) المستخدم التي ترغب في استهداف Defender لنقطة النهاية على تطبيق iOS. انقر فوق **"تحديد"** ثم " **التالي**".

    > [!NOTE]
    > يجب أن تتكون مجموعة المستخدمين المحددة من المستخدمين المسجلين في Intune.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-2.png" alt-text="علامة التبويب &quot;إضافة مجموعة&quot; في مركز إدارة إدارة نقاط النهاية من Microsoft" lightbox="images/ios-deploy-2.png":::

1. في المقطع *"مراجعة + إنشاء* "، تحقق من صحة كافة المعلومات التي تم إدخالها ثم حدد **"إنشاء**". في لحظات قليلة، يجب إنشاء تطبيق Defender لنقطة النهاية بنجاح، ويجب أن يظهر إعلام في الزاوية العلوية اليسرى من الصفحة.

1. في صفحة معلومات التطبيق المعروضة، في قسم **"Monitor** "، حدد **حالة تثبيت الجهاز** للتحقق من اكتمال تثبيت الجهاز بنجاح.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-3.png" alt-text="صفحة حالة تثبيت الجهاز" lightbox="images/ios-deploy-3.png":::

## <a name="complete-deployment-for-supervised-devices"></a>النشر الكامل للأجهزة الخاضعة للإشراف

يتمتع Microsoft Defender لنقطة النهاية على تطبيق iOS بقدرة متخصصة على أجهزة iOS/iPadOS الخاضعة للإشراف، نظرا إلى زيادة قدرات الإدارة التي يوفرها النظام الأساسي على هذه الأنواع من الأجهزة. كما يمكن أن توفر حماية الويب **دون إعداد VPN محلي على الجهاز**. وهذا يعطي المستخدمين النهائيين تجربة سلسة مع استمرار حمايتهم من التصيد الاحتيالي والهجمات الأخرى المستندة إلى الويب.

### <a name="configure-supervised-mode-via-intune"></a>تكوين الوضع الخاضع للإشراف عبر Intune

بعد ذلك، قم بتكوين الوضع الخاضع للإشراف لتطبيق Defender لنقطة النهاية من خلال نهج App Configuration.

   > [!NOTE]
   > نهج تكوين التطبيق هذا للأجهزة الخاضعة للإشراف ينطبق فقط على الأجهزة المدارة ويجب أن يستهدف جميع أجهزة iOS المدارة كأفضل ممارسة.

1. سجل الدخول إلى [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) وانتقل إلى **نهج** \> تكوين **تطبيقات التطبيقات** \> **Add**. حدد **الأجهزة المدارة**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center4.](images/ios-deploy-4.png)

1. في صفحة *إنشاء نهج تكوين التطبيق* ، قم بتوفير المعلومات التالية:
    - اسم النهج
    - النظام الأساسي: حدد iOS/iPadOS
    - التطبيق المستهدف: حدد **Microsoft Defender لنقطة النهاية** من القائمة

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center5.](images/ios-deploy-5.png)

1. في الشاشة التالية، حدد **"استخدام مصمم التكوين** " كتنسيق. حدد الخاصية التالية:
    - مفتاح التكوين: تم إصداره
    - نوع القيمة: سلسلة
    - قيمة التكوين: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft Admin Center6.](images/ios-deploy-6.png)

1. حدد **"التالي** " لفتح صفحة **علامات النطاق** . علامات النطاق اختيارية. حدد **"التالي** " للمتابعة.

1. في صفحة **"الواجبات** "، حدد المجموعات التي ستتلقى ملف التعريف هذا. بالنسبة لهذا السيناريو، من الأفضل استهداف **جميع الأجهزة**. لمزيد من المعلومات حول تعيين ملفات التعريف، راجع [تعيين ملفات تعريف المستخدمين والجهاز](/mem/intune/configuration/device-profile-assign).

   عند النشر إلى مجموعات المستخدمين، يجب على المستخدم تسجيل الدخول إلى جهاز قبل تطبيق النهج.

   انقر فوق **التالي**.

1. في الصفحة **"مراجعة + إنشاء** "، عند الانتهاء، اختر **"إنشاء**". يتم عرض ملف التعريف الجديد في قائمة ملفات تعريف التكوين.

1. بعد ذلك، يجب نشر ملف تعريف مخصص على أجهزة iOS الخاضعة للإشراف. هذا من أجل قدرات مكافحة التصيد الاحتيالي المحسنة. اتبع الخطوات أدناه:

    - تنزيل ملف تعريف التكوين من [https://aka.ms/mdeiosprofilesupervised](https://aka.ms/mdeiosprofilesupervised)
    - الانتقال إلى ملفات تعريف  -> **DevicesiOS** -> **/iPadOSConfigurationCreate** ->  **Profile**

    > [!div class="mx-imgBorder"]
    > ![صورة لمركز إدارة إدارة نقاط النهاية من Microsoft 7.](images/ios-deploy-7.png)
    
    - توفير اسم لملف التعريف. عند مطالبتك باستيراد ملف تعريف تكوين، حدد الملف الذي تم تنزيله من الخطوة السابقة.
    - في قسم **"الواجب"** ، حدد مجموعة الأجهزة التي تريد تطبيق ملف التعريف هذا عليها. وكأفضل ممارسة، يجب تطبيق ذلك على جميع أجهزة iOS المدارة. حدد **التالي**.
    - في الصفحة **"مراجعة + إنشاء** "، عند الانتهاء، اختر **"إنشاء**". يتم عرض ملف التعريف الجديد في قائمة ملفات تعريف التكوين.


## <a name="auto-onboarding-of-vpn-profile-simplified-onboarding"></a>الإلحاق التلقائي لملف تعريف VPN (الإلحاق المبسط)

بالنسبة للأجهزة غير الخاضعة للإشراف، يتم استخدام VPN من أجل توفير ميزة حماية الويب. هذه ليست شبكة ظاهرية خاصة عادية وهي شبكة ظاهرية خاصة محلية/ذاتية الحلقة لا تأخذ نسبة استخدام الشبكة خارج الجهاز.

>[!NOTE]
>بالنسبة للأجهزة الخاضعة للإشراف، لا يلزم وجود VPN لإمكانية حماية الويب ويتطلب من المسؤولين إعداد ملف تعريف تكوين على الأجهزة الخاضعة للإشراف. لتكوين الأجهزة الخاضعة للإشراف، اتبع الخطوات الواردة في قسم [النشر الكامل للأجهزة الخاضعة للإشراف](#complete-deployment-for-supervised-devices) .

يمكن للمسؤولين تكوين الإعداد التلقائي لملف تعريف VPN. سيؤدي هذا إلى إعداد ملف تعريف Defender for Endpoint VPN تلقائيا دون الحاجة إلى أن يقوم المستخدم بذلك أثناء الإلحاق. 

تبسط هذه الخطوة عملية الإلحاق عن طريق إعداد ملف تعريف VPN. للحصول على تجربة إعداد بدون لمس أو صمت، راجع القسم التالي: [إعداد بدون لمسة](#zero-touch-onboarding-of-microsoft-defender-for-endpoint).

1. في [مركز إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى **ملف** **تعريف DevicesConfiguration** ->  **ProfilesCreate** -> .
1. اختر **النظام الأساسي** ك **iOS/iPadOS** **ونوع ملف التعريف** ك **VPN**. انقر فوق **"إنشاء**".
1. اكتب اسما لملف التعريف وانقر فوق **"التالي**".
1. حدد **VPN مخصص** لنوع الاتصال وفي قسم **الشبكة الظاهرية الخاصة الأساسية** ، أدخل ما يلي:
    - اسم الاتصال = Microsoft Defender لنقطة النهاية
    - عنوان خادم VPN = 127.0.0.1
    - أسلوب المصادقة = "اسم المستخدم وكلمة المرور"
    - تقسيم النفق = تعطيل
    - معرف VPN = com.microsoft.scmx
    - في أزواج قيم المفاتيح، أدخل لوحة التشغيل **التلقائي** للمفتاح وقم بتعيين القيمة إلى **True**.
    - نوع VPN التلقائي = VPN عند الطلب
    - انقر فوق **"إضافة** لقواعد **عند الطلب**" وحدد **"أريد القيام بما يلي = تأسيس VPN****"، أريد أن أقتصر على = كافة المجالات**.

    :::image type="content" source="images/ios-deploy-8.png" alt-text="علامة التبويب إعدادات تكوين ملف تعريف VPN" lightbox="images/ios-deploy-8.png":::

1. انقر فوق "التالي" وقم بتعيين ملف التعريف للمستخدمين المستهدفين.
1. في المقطع *"مراجعة + إنشاء* "، تحقق من صحة كافة المعلومات التي تم إدخالها ثم حدد **"إنشاء**".

## <a name="zero-touch-onboarding-of-microsoft-defender-for-endpoint"></a>إعداد بدون لمسة Microsoft Defender لنقطة النهاية



> [!NOTE]
> لا يمكن تكوين اللمس الصفري على أجهزة iOS المسجلة دون ترابط المستخدم (أجهزة أقل من المستخدم أو الأجهزة المشتركة).

يمكن للمسؤولين تكوين Microsoft Defender لنقطة النهاية للنشر والتنشيط بصمت. في هذا التدفق، يقوم المسؤول بإنشاء ملف تعريف نشر ويتم إعلام المستخدم ببساطة بالتثبيت. يتم تثبيت Defender لنقطة النهاية تلقائيا دون الحاجة إلى فتح المستخدم للتطبيق. اتبع الخطوات أدناه لإعداد نشر بدون لمس أو صمت ل Defender لنقطة النهاية على أجهزة iOS المسجلة:

1. في [مركز إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى **ملف** **تعريف DevicesConfiguration** >  **ProfilesCreate** > .
1. اختر **النظام الأساسي** ك **iOS/iPadOS** **ونوع ملف التعريف** ك **VPN**. حدد **"إنشاء**".
1. اكتب اسما لملف التعريف وحدد **"التالي**".
1. حدد **VPN مخصص** لنوع الاتصال وفي قسم **الشبكة الظاهرية الخاصة الأساسية** ، أدخل ما يلي:
    - اسم الاتصال = Microsoft Defender لنقطة النهاية
    - عنوان خادم VPN = 127.0.0.1
    - أسلوب المصادقة = "اسم المستخدم وكلمة المرور"
    - تقسيم النفق = تعطيل
    - معرف VPN = com.microsoft.scmx
    - في أزواج قيم المفاتيح، أدخل المفتاح **SilentOnboard** وقم بتعيين القيمة إلى **True**.
    - نوع VPN التلقائي = VPN عند الطلب
    - حدد **"إضافة** لقواعد **عند الطلب** " وحدد **أريد القيام بما يلي = إنشاء VPN**، **أريد أن أقتصر على = كافة المجالات**.

    :::image type="content" source="images/ios-deploy-9.png" alt-text="صفحة تكوين ملف تعريف VPN" lightbox="images/ios-deploy-9.png":::

1. حدد **"التالي** " وقم بتعيين ملف التعريف للمستخدمين المستهدفين.
1. في المقطع *"مراجعة + إنشاء* "، تحقق من صحة كافة المعلومات التي تم إدخالها ثم حدد **"إنشاء**".

بمجرد الانتهاء من التكوين أعلاه ومزامنته مع الجهاز، يتم تنفيذ الإجراءات التالية على جهاز (أجهزة) iOS المستهدفة:
    - سيتم نشر Microsoft Defender لنقطة النهاية وإلحاقها بصمت وسيشاهد الجهاز في مدخل Defender لنقطة النهاية.
    - سيتم إرسال إعلام بإشعار الإشعار إلى جهاز المستخدم.
    - سيتم تنشيط حماية الويب والميزات الأخرى.

   > [!NOTE]
   > بالنسبة للأجهزة الخاضعة للإشراف، على الرغم من أن ملف تعريف VPN غير مطلوب، فلا يزال بإمكان المسؤولين إعداد الإعداد بدون لمس عن طريق تكوين ملف تعريف Defender لنقطة النهاية VPN من خلال Intune. سيتم نشر ملف تعريف VPN على الجهاز ولكن سيكون موجودا فقط على الجهاز كملف تعريف تمريري ويمكن حذفه بعد الإلحاق الأولي.

## <a name="complete-onboarding-and-check-status"></a>إكمال الإلحاق والتحقق من الحالة

1. بمجرد تثبيت Defender لنقطة النهاية على iOS على الجهاز، سترى أيقونة التطبيق.

    :::image type="content" source="images/41627a709700c324849bf7e13510c516.png" alt-text="تم إنشاء وصف الهاتف الذكي تلقائيا" lightbox="images/41627a709700c324849bf7e13510c516.png":::

2. اضغط على أيقونة تطبيق Defender لنقطة النهاية (MSDefender) واتبع الإرشادات التي تظهر على الشاشة لإكمال خطوات الإلحاق. تتضمن التفاصيل قبول المستخدم النهائي لأذونات iOS المطلوبة من قبل Defender لنقطة النهاية على iOS.

3. عند نجاح عملية الإلحاق، سيبدأ الجهاز في الظهور على قائمة الأجهزة في مدخل Microsoft 365 Defender.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/device-inventory-screen.png" alt-text="صفحة مخزون الجهاز" lightbox="images/device-inventory-screen.png":::

## <a name="configure-microsoft-defender-for-endpoint-for-supervised-mode"></a>تكوين Microsoft Defender لنقطة النهاية من أجل الوضع الخاضع للإشراف

يتمتع Microsoft Defender لنقطة النهاية على تطبيق iOS بقدرة متخصصة على أجهزة iOS/iPadOS الخاضعة للإشراف، نظرا إلى زيادة قدرات الإدارة التي يوفرها النظام الأساسي على هذه الأنواع من الأجهزة. للاستفادة من هذه الإمكانات، يحتاج تطبيق Defender لنقطة النهاية إلى معرفة ما إذا كان الجهاز في الوضع الخاضع للإشراف.

### <a name="configure-supervised-mode-via-intune"></a>تكوين الوضع الخاضع للإشراف عبر Intune

يسمح لك Intune بتكوين تطبيق Defender ل iOS من خلال نهج App Configuration.

   > [!NOTE]
   > نهج تكوين التطبيق هذا للأجهزة الخاضعة للإشراف ينطبق فقط على الأجهزة المدارة ويجب أن يستهدف جميع أجهزة iOS المدارة كأفضل ممارسة.

1. سجل الدخول إلى [مركز إدارة إدارة نقاط النهاية من Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431) وانتقل إلى **نهج** \> تكوين **تطبيقات التطبيقات** \> **Add**. انقر على **الأجهزة المدارة**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-4.png" alt-text="خيار الأجهزة المدارة" lightbox="images/ios-deploy-4.png":::

1. في صفحة *إنشاء نهج تكوين التطبيق* ، قم بتوفير المعلومات التالية:
    - اسم النهج
    - النظام الأساسي: حدد iOS/iPadOS
    - التطبيق المستهدف: حدد **Microsoft Defender لنقطة النهاية** من القائمة

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-5.png" alt-text="الحقول الأساسية لنهج التكوين للتطبيق" lightbox="images/ios-deploy-5.png":::

1. في الشاشة التالية، حدد **"استخدام مصمم التكوين** " كتنسيق. حدد الخاصية التالية:
    - مفتاح التكوين: تم إصداره
    - نوع القيمة: سلسلة
    - قيمة التكوين: {{issupervised}}

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-deploy-6.png" alt-text="الصفحة التي تريد اختيار تنسيق إعدادات تكوين النهج منها" lightbox="images/ios-deploy-6.png":::

1. انقر فوق **"التالي** " لفتح صفحة **علامات النطاق** . علامات النطاق اختيارية. انقر فوق **التالي** للمتابعة.

1. في صفحة **"الواجبات** "، حدد المجموعات التي ستتلقى ملف التعريف هذا. بالنسبة لهذا السيناريو، من الأفضل استهداف **جميع الأجهزة**. لمزيد من المعلومات حول تعيين ملفات التعريف، راجع [تعيين ملفات تعريف المستخدمين والجهاز](/mem/intune/configuration/device-profile-assign).

   عند النشر إلى مجموعات المستخدمين، يجب على المستخدم تسجيل الدخول إلى جهاز قبل تطبيق النهج.

   انقر فوق **التالي**.

1. في الصفحة **"مراجعة + إنشاء** "، عند الانتهاء، اختر **"إنشاء**". يتم عرض ملف التعريف الجديد في قائمة ملفات تعريف التكوين.

## <a name="next-steps"></a>الخطوات التالية

- [تكوين نهج حماية التطبيق لتضمين إشارات مخاطر Defender لنقطة النهاية (MAM)](ios-install-unmanaged.md)
- [تكوين Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)
