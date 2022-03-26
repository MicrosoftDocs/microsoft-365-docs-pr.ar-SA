---
title: نشر Microsoft Defender ل Endpoint على Android باستخدام Microsoft Intune
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mde، android، التثبيت، النشر، إزالة التثبيت،
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 380e2ecb9ee8df7eb066eef600f796685215662f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63573833"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>نشر Microsoft Defender ل Endpoint على Android باستخدام Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تعرف على كيفية نشر Defender for Endpoint على Android Intune Company Portal الأجهزة التي تم تسجيلها. لمزيد من المعلومات حول تسجيل جهاز Intune، راجع [تسجيل جهازك](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **يتوفر الآن Defender for Endpoint على Android على [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> يمكنك الاتصال ب Google Play من Intune لنشر تطبيق Defender for Endpoint عبر أوضاع تسجيل مسؤول الجهاز وAndroid Enterprise.
>
> يتم تحديث التطبيق تلقائيا عبر Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>النشر على الأجهزة التي تم تسجيلها في "مسؤول الجهاز"

**نشر Defender لنقطة النهاية على نظام التشغيل Android Intune Company Portal - الأجهزة التي تم تسجيلها من قبل مسؤول الجهاز**

تعرف على كيفية نشر Defender for Endpoint على نظام التشغيل Android Intune Company Portal - الأجهزة التي تم تسجيلها من قبل مسؤول الجهاز.

### <a name="add-as-android-store-app"></a>إضافة ك تطبيق متجر Android

1. في [إدارة نقاط النهاية من Microsoft،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **تطبيقات** \> **تطبيقات Android إضافة** \> **\>** تطبيق متجر Android **واختر تحديد**.

   :::image type="content" alt-text="صورة إدارة نقاط النهاية من Microsoft مركز الإدارة إضافة تطبيق متجر android." source="images/mda-addandroidstoreapp.png" lightbox="images/mda-addandroidstoreapp.png":::

2. في الصفحة **إضافة تطبيق** وفي *القسم معلومات التطبيق* ، أدخل:

   - **الاسم**
   - **الوصف**
   - **Publisher** Microsoft.
   - **URL لمتجر التطبيقات** ك https://play.google.com/store/apps/details?id=com.microsoft.scmx (Defender for Endpoint app Google Play Store URL)

   الحقول الأخرى اختيارية. حدد **التالي**.

   :::image type="content" alt-text="صورة إدارة نقاط النهاية من Microsoft مركز الإدارة إضافة معلومات التطبيق." source="images/mda-addappinfo.png" lightbox="images/mda-addappinfo.png":::

3. في المقطع *الواجبات* ، انتقل إلى المقطع **مطلوب** وحدد **إضافة مجموعة.** يمكنك بعد ذلك اختيار مجموعة (مجموعة) المستخدمين التي تريد استهداف Defender ل Endpoint على تطبيق Android. اختر **تحديد** ثم **التالي**.

    > [!NOTE]
    > يجب أن تتكون مجموعة المستخدمين المحددة من المستخدمين المسجلين في Intune.
    >
    > :::image type="content" alt-text="صورة لمجموعات المستخدمين إدارة نقاط النهاية من Microsoft مركز الإدارة." source="images/363bf30f7d69a94db578e8af0ddd044b.png" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. في المقطع **مراجعة+إنشاء** ، تحقق من صحة كل المعلومات التي تم إدخالها، ثم حدد **إنشاء**.

    في لحظات قليلة، سيتم إنشاء تطبيق Defender for Endpoint بنجاح، وسيظهر إعلام في الزاوية العلوية اليسرى من الصفحة.

    :::image type="content" alt-text="صورة إعلام إدارة نقاط النهاية من Microsoft مركز الإدارة لتطبيق Defender for Endpoint." source="images/86cbe56f88bb6e93e9c63303397fc24f.png" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. في صفحة معلومات التطبيق التي يتم عرضها، في المقطع  جهاز العرض، حدد  حالة تثبيت الجهاز للتحقق من اكتمال تثبيت الجهاز بنجاح.

    :::image type="content" alt-text="صورة لتثبيت إدارة نقاط النهاية من Microsoft مركز الإدارة." source="images/513cf5d59eaaef5d2b5bc122715b5844.png" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>إكمال حالة الboarding والتحقق

1. بمجرد تثبيت Defender for Endpoint على Android على الجهاز، سترى أيقونة التطبيق.

    ![أيقونة على الجهاز المحمول.](images/7cf9311ad676ec5142002a4d0c2323ca.jpg)

2. اضغط على أيقونة تطبيق Microsoft Defender for Endpoint واتبع الإرشادات التي تظهر على الشاشة لإكمال تشغيل التطبيق. تتضمن التفاصيل قبول المستخدم النهائي لأذونات Android المطلوبة من قبل Defender for Endpoint على Android.

3. عند نجاح عملية الضم، سيبدأ الجهاز في الظهور على قائمة الأجهزة في Microsoft 365 Defender المدخل.

    :::image type="content" alt-text="صورة جهاز في مدخل Defender for Endpoint." source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>النشر على الأجهزة التي تم تسجيلها في Android Enterprise

يدعم Defender for Endpoint على Android الأجهزة التي تم تسجيلها في Android Enterprise.

لمزيد من المعلومات حول خيارات التسجيل المعتمدة بواسطة Intune، راجع [خيارات التسجيل](/mem/intune/enrollment/android-enroll).

**حاليا، يتم دعم الأجهزة المملوكة شخصيا مع ملف تعريف العمل والتسجيلات التي تملكها الشركة بشكل كامل على أجهزة المستخدم المدارة بالكامل للنشر.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>إضافة Microsoft Defender لنقطة النهاية على Android ك تطبيق Google Play مدار

اتبع الخطوات أدناه لإضافة تطبيق Microsoft Defender for Endpoint إلى Google Play المدار.

1. في [إدارة نقاط النهاية من Microsoft إدارة ،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **تطبيقات** \> **تطبيقات Android إضافة** \> وحدد **تطبيق Google Play المدار**.

    :::image type="content" alt-text="صورة لمدير إدارة نقاط النهاية من Microsoft إدارة google play." source="images/579ff59f31f599414cedf63051628b2e.png" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. على صفحة Google Play المدارة التي يتم تحميلها لاحقا، انتقل إلى مربع البحث وأدخل `Microsoft Defender`. يجب أن يعرض بحثك تطبيق Microsoft Defender لنقطة النهاية في Google Play المدار. انقر فوق تطبيق Microsoft Defender لنقطة النهاية من نتيجة البحث في التطبيقات.

    ![صورة إدارة نقاط النهاية من Microsoft البحث في تطبيقات مركز الإدارة.](images/0f79cb37900b57c3e2bb0effad1c19cb.png)

3. في صفحة وصف التطبيق التي ستنشر بعد ذلك، يجب أن تتمكن من رؤية تفاصيل التطبيق على Defender for Endpoint. راجع المعلومات على الصفحة، ثم حدد **موافقة**.

    > [!div class="mx-imgBorder"]
    > ![لقطة شاشة ل Google Play مدار.](images/07e6d4119f265037e3b80a20a73b856f.png)

4. سيتم تقديم الأذونات التي يحصل عليها Defender for Endpoint لكي يعمل. راجعها ثم حدد **موافقة**.

    ![لقطة شاشة لموافقة تطبيق Defender for Endpoint preview.](images/206b3d954f06cc58b3466fb7a0bd9f74.png)

5. سيتم تقديم صفحة إعدادات الموافقة. تؤكد الصفحة تفضيلك لمعالجة أذونات التطبيق الجديدة التي قد يطلبها Defender for Endpoint على Android. راجع الخيارات وحدد الخيار المفضل لديك. حدد **تم**.

    بشكل افتراضي، تحدد Google Play المدارة **الاحتفاظ بالموافقة عندما يطلب التطبيق أذونات جديدة**.

    > [!div class="mx-imgBorder"]
    > ![صورة ل علامة تبويب الإعلامات.](images/ffecfdda1c4df14148f1526c22cc0236.png)

6. بعد تحديد معالجة الأذونات، حدد **مزامنة** لمزامنة Microsoft Defender ل Endpoint إلى قائمة التطبيقات.

    > [!div class="mx-imgBorder"]
    > ![صورة لصفحة المزامنة.](images/34e6b9a0dae125d085c84593140180ed.png)

7. ستكتمل المزامنة في غضون دقائق قليلة.

    :::image type="content" alt-text="صورة لتطبيق Android." source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. حدد الزر **تحديث** في شاشة تطبيقات Android ويجب أن يكون Microsoft Defender لنقطة النهاية مرئيا في قائمة التطبيقات.

    :::image type="content" alt-text="صورة لقائمة تطبيقات Android." source="images/fa4ac18a6333335db3775630b8e6b353.png" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. يدعم Defender for Endpoint سياسات تكوين التطبيق للأجهزة المدارة عبر Intune. يمكن الاستفادة من هذه الإمكانية للحصول على أذونات (أذونات) Android القابلة للتطبيق، وبالتالي لا يحتاج المستخدم إلى قبول هذه الأذونات (الأذونات).

    1. في صفحة **التطبيقات** ، انتقل إلى نهج > نهج تكوين التطبيق > **إضافة > مدارة**.

       :::image type="content" alt-text="صورة ل إدارة نقاط النهاية من Microsoft مدارة في مركز إدارة android." source="images/android-mem.png":::

    1. في الصفحة **إنشاء نهج تكوين التطبيق** ، أدخل التفاصيل التالية:

        - الاسم: Microsoft Defender لنقطة النهاية.
        - اختر **Android Enterprise** كنهاية أساسية.
        - اختر **ملف تعريف العمل كنوع** ملف تعريف فقط.
        - انقر **فوق تحديد تطبيق**، **واختر Microsoft Defender ATP**، وحدد **موافق** ثم **التالي**.

        :::image type="content" alt-text="صورة لإنشاء صفحة نهج تكوين التطبيق." source="images/android-create-app.png" lightbox="images/android-create-app.png":::

    1. في الصفحة **الإعدادات**، انتقل إلى المقطع أذونات انقر فوق إضافة لعرض قائمة الأذونات المعتمدة. في المقطع إضافة أذونات، حدد الأذونات التالية:

       - مساحة تخزين خارجية (قراءة)
       - مساحة تخزين خارجية (كتابة)

       ثم حدد **موافق**.

       :::image type="content" alt-text="صورة لنظام التشغيل android لإنشاء نهج تكوين التطبيق." source="images/android-create-app-config.png" lightbox="images/android-create-app-config.png":::

    1. من المفترض أن ترى الآن الأذونات المدرجة والآن يمكنك أن تقوم بجريرة تلقائية على كليهما عن طريق اختيار "طلب تلقائي" في القائمة المنسدلة حالة الأذونات ثم تحديد **التالي**.

       :::image type="content" alt-text="صورة لمنحة تلقائية لنظام Android لإنشاء نهج تكوين التطبيق." source="images/android-auto-grant.png" lightbox="images/android-auto-grant.png":::

    1. في صفحة **الواجبات** ، حدد مجموعة المستخدمين التي سيتم تعيين نهج تكليف التطبيق لها. انقر **فوق تحديد المجموعات لتضمين** المجموعة القابلة للتطبيق وتحديدها ثم تحديد **التالي**. عادة ما تكون المجموعة المحددة هنا هي المجموعة نفسها التي تقوم بتعيين تطبيق Android ل Microsoft Defender لها.

       :::image type="content" alt-text="صورة نهج تكوين إنشاء التطبيق." source="images/android-select-group.png" lightbox="images/android-select-group.png":::

    1. في الصفحة **مراجعة + إنشاء** التي تأتي بعد ذلك، راجع كل المعلومات ثم حدد **إنشاء**.

        يتم الآن تعيين نهج تكوين التطبيق ل Defender for Endpoint الذي يقوم بالتخزين التلقائي لإذن التخزين إلى مجموعة المستخدمين المحددة.

        > [!div class="mx-imgBorder"]
        > ![صورة لمراجعة android إنشاء نهج خلط التطبيقات.](images/android-review-create.png)

10. حدد **تطبيق ATP ل Microsoft Defender** في القائمة \> **خصائص** \> **تحرير الواجبات**\>.

    :::image type="content" alt-text="صورة لقائمة التطبيقات." source="images/mda-properties.png" lightbox="images/mda-properties.png":::

11. تعيين التطبيق ك تطبيق *مطلوب* إلى مجموعة مستخدمين. يتم تثبيته تلقائيا في ملف *تعريف العمل* أثناء المزامنة التالية للجهاز عبر Company Portal التطبيق. يمكن إجراء هذا الواجب من خلال الانتقال إلى  \> مجموعة إضافة المقطع مطلوب، وتحديد مجموعة المستخدمين والنقر فوق **تحديد**.

    > [!div class="mx-imgBorder"]
    > ![صورة لتحرير صفحة التطبيق.](images/ea06643280075f16265a596fb9a96042.png)

12. في الصفحة **تحرير التطبيق** ، راجع كل المعلومات التي تم إدخالها أعلاه. ثم حدد **مراجعة + حفظ** ثم **حفظ** مرة أخرى لبدء التعيين.

### <a name="auto-setup-of-always-on-vpn"></a>الإعداد التلقائي ل VPN دائما

يدعم Defender for Endpoint سياسات تكوين الجهاز للأجهزة المدارة عبر Intune. يمكن الاستفادة من هذه الإمكانية للإعداد التلقائي ل **VPN** دائما على الأجهزة التي تم تسجيلها في Android Enterprise، لذلك لا يحتاج المستخدم إلى إعداد خدمة VPN أثناء الالتحاق.

1. على **الأجهزة،** حدد **ملفات تعريف التكوين** \> **إنشاء النظام الأساسي لملف التعريف** \>  \> **Android Enterprise**

   حدد **قيود الجهاز** ضمن أحد الخطوات التالية، استنادا إلى نوع تسجيل جهازك:
   - **ملف تعريف العمل المدار والمخصص Corporate-Owned بالكامل**
   - **ملف تعريف العمل الممتلك شخصيا**

   حدد **إنشاء**.

   :::image type="content" alt-text="صورة لملف تعريف تكوين الأجهزة إنشاء." source="images/1autosetupofvpn.png":::

2. **تكوين الإعدادات** توفير **اسم** ووصف لتعريف ملف تعريف التكوين بشكل  فريد.

   :::image type="content" alt-text="صورة لاسم ملف تعريف تكوين الأجهزة ووصفها." source="images/2autosetupofvpn.png":::

3. حدد **الاتصال** وتكوين VPN:

   - تمكين **VPN دائما**

     قم بإعداد عميل VPN في ملف تعريف العمل للاتصال ب VPN وإعادة الاتصال به تلقائيا كلما أمكن ذلك. يمكن تكوين عميل VPN واحد فقط ل VPN دائما على جهاز معين، لذا تأكد من عدم نشر أكثر من نهج VPN واحد دائما على جهاز واحد.

   - تحديد **"مخصص** " في القائمة المنسدلة "عميل VPN"

     VPN المخصص في هذه الحالة هو Defender for Endpoint VPN الذي يتم استخدامه لتوفير ميزة حماية الويب.

     > [!NOTE]
     > يجب تثبيت تطبيق Microsoft Defender for Endpoint على جهاز المستخدم، لكي يعمل الإعداد التلقائي لهذه VPN.

   - أدخل **"معر ة** الحزمة" لتطبيق Microsoft Defender for Endpoint في متجر Google Play. بالنسبة إلى عنوان URL الخاص لتطبيق Defender <https://play.google.com/store/apps/details?id=com.microsoft.scmx>، يكون "الم ID الحزمة **" هو com.microsoft.scmx**

   - **وضع التأمين** غير مكون (افتراضي)

     ![صورة لملف تعريف تكوين الأجهزة تمكن VPN دائما.](images/3autosetupofvpn.png)
      :::image type="content" alt-text="صورة لملف تعريف تكوين الأجهزة تمكن VPN دائما." source="images/3autosetupofvpn.png":::

4. **الواجب**

   في صفحة **الواجبات** ، حدد مجموعة المستخدمين التي سيتم تعيين نهج تكليف التطبيق لها. اختر **تحديد المجموعات** لتضمين المجموعة القابلة للتطبيق وتحديدها، ثم حدد **التالي**. عادة ما تكون المجموعة المحددة هنا هي المجموعة نفسها التي تقوم بتعيين تطبيق Android ل Microsoft Defender لها.

   ![صورة تعيين ملف تعريف تكوين الأجهزة.](images/4autosetupofvpn.png)

5. في الصفحة **مراجعة + إنشاء** التي تأتي بعد ذلك، راجع كل المعلومات ثم حدد **إنشاء**.
يتم الآن تعيين ملف تعريف تكوين الجهاز إلى مجموعة المستخدمين المحددة.

   ![صورة لملف تعريف تكوين الأجهزة مراجعة وإنشاء.](images/5autosetupofvpn.png)

## <a name="check-status-and-complete-onboarding"></a>التحقق من الحالة وإكمال الboarding

1. تأكد من حالة تثبيت Microsoft Defender ل Endpoint على نظام التشغيل Android بالنقر فوق حالة **تثبيت الجهاز**. تحقق من عرض الجهاز هنا.

    > [!div class="mx-imgBorder"]
    > ![صورة حالة تثبيت الجهاز.](images/900c0197aa59f9b7abd762ab2b32e80c.png)

2. على الجهاز، يمكنك التحقق من حالة التكهين من خلال الذهاب إلى **ملف تعريف العمل**. تأكد من توفر Defender for Endpoint وأنك مسجل في الأجهزة المملوكة شخصيا **باستخدام ملف تعريف العمل**. إذا كنت مسجلا في جهاز مستخدم تملكه الشركة ويدار بشكل كامل، سيكون لديك ملف تعريف واحد على الجهاز حيث يمكنك تأكيد توفر Defender for Endpoint.

    ![صورة التطبيق في الجهاز المحمول.](images/c2e647fc8fa31c4f2349c76f2497bc0e.png)

3. عند تثبيت التطبيق، افتح التطبيق واقبل الأذونات، ومن ثم يجب أن تكون عملية التركيب ناجحة.

    ![صورة جهاز محمول مع تطبيق Microsoft Defender for Endpoint](images/MDE_new.png)

4. في هذه المرحلة، يتم تشغيل الجهاز بنجاح في Defender for Endpoint على Android. يمكنك التحقق من ذلك على Microsoft 365 Defender [من](https://security.microsoft.com) خلال الانتقال إلى **صفحة مخزون** الجهاز.

    :::image type="content" alt-text="صورة لمدخل Microsoft Defender لنقطة النهاية." source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة حول Microsoft Defender لنقطة النهاية على نظام التشغيل Android](microsoft-defender-endpoint-android.md)
- [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md)
