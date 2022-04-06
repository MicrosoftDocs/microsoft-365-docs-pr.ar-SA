---
title: نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mde، android، التثبيت، النشر، إزالة التثبيت،
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
ms.openlocfilehash: aab50764a13a671cdeb10902744456dcbc1cb48f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471396"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="جزء تطبيق 'إضافة متجر Android' في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة"  lightbox="images/mda-addandroidstoreapp.png":::

2. في الصفحة **إضافة تطبيق** وفي *القسم معلومات التطبيق* ، أدخل:

   - **الاسم**
   - **الوصف**
   - **Publisher** Microsoft.
   - **URL لمتجر التطبيقات** ك https://play.google.com/store/apps/details?id=com.microsoft.scmx (Defender for Endpoint app Google Play Store URL)

   الحقول الأخرى اختيارية. حدد **التالي**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="تعرض الصفحة &quot;إضافة تطبيق&quot; معلومات عنوان URL وناشر التطبيق في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة" lightbox="images/mda-addappinfo.png":::

3. في المقطع *الواجبات* ، انتقل إلى المقطع **مطلوب** وحدد **إضافة مجموعة.** يمكنك بعد ذلك اختيار مجموعة (مجموعة) المستخدمين التي تريد استهداف Defender ل Endpoint على تطبيق Android. اختر **تحديد** ثم **التالي**.

    > [!NOTE]
    > يجب أن تتكون مجموعة المستخدمين المحددة من المستخدمين المسجلين في Intune.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="الجزء &quot;إضافة مجموعة&quot; في الصفحة &quot;إضافة تطبيق&quot; في مدخل إدارة نقاط النهاية من Microsoft &quot;مركز الإدارة&quot;" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. في المقطع **مراجعة+إنشاء** ، تحقق من صحة كل المعلومات التي تم إدخالها، ثم حدد **إنشاء**.

    في لحظات قليلة، سيتم إنشاء تطبيق Defender for Endpoint بنجاح، وسيظهر إعلام في الزاوية العلوية اليسرى من الصفحة.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="جزء حالة التطبيق في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. في صفحة معلومات التطبيق التي يتم عرضها، في المقطع  جهاز العرض، حدد  حالة تثبيت الجهاز للتحقق من اكتمال تثبيت الجهاز بنجاح.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="صفحة حالة تثبيت الجهاز في مدخل Microsoft Defender 365" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>إكمال حالة الboarding والتحقق

1. بمجرد تثبيت Defender for Endpoint على Android على الجهاز، سترى أيقونة التطبيق.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="أيقونة ATP ل Microsoft Defender المدرجة في جزء البحث" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. اضغط على Microsoft Defender لنقطة النهاية التطبيق واتبع الإرشادات التي تظهر على الشاشة لإكمال لصق التطبيق. تتضمن التفاصيل قبول المستخدم النهائي لأذونات Android المطلوبة من قبل Defender for Endpoint على Android.

3. عند نجاح عملية الضم، سيبدأ الجهاز في الظهور على قائمة الأجهزة في Microsoft 365 Defender المدخل.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="جهاز في مدخل Microsoft Defender لنقطة النهاية"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>النشر على الأجهزة التي تم تسجيلها في Android Enterprise

يدعم Defender for Endpoint على Android الأجهزة التي تم تسجيلها في Android Enterprise.

لمزيد من المعلومات حول خيارات التسجيل المعتمدة بواسطة Intune، راجع [خيارات التسجيل](/mem/intune/enrollment/android-enroll).

**حاليا، يتم دعم الأجهزة المملوكة شخصيا مع ملف تعريف العمل والتسجيلات التي تملكها الشركة بشكل كامل على أجهزة المستخدم المدارة بالكامل للنشر.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>إضافة Microsoft Defender لنقطة النهاية على Android ك تطبيق Google Play مدار

اتبع الخطوات أدناه لإضافة تطبيق Microsoft Defender لنقطة النهاية إلى Google Play المدار.

1. في [إدارة نقاط النهاية من Microsoft إدارة ،](https://go.microsoft.com/fwlink/?linkid=2109431) انتقل إلى **تطبيقات** \> **تطبيقات Android إضافة** \> وحدد **تطبيق Google Play المدار**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="جزء إضافة التطبيقات في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. على صفحة Google Play المدارة التي يتم تحميلها لاحقا، انتقل إلى مربع البحث وأدخل `Microsoft Defender`. يجب أن يعرض بحثك Microsoft Defender لنقطة النهاية التطبيق في Google Play المدار. انقر فوق Microsoft Defender لنقطة النهاية التطبيق من نتيجة بحث التطبيقات.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="صفحة Google Play المدارة في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. في صفحة وصف التطبيق التي ستنشر بعد ذلك، يجب أن تتمكن من رؤية تفاصيل التطبيق على Defender for Endpoint. راجع المعلومات على الصفحة، ثم حدد **موافقة**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="صفحة Google Play المدارة في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::
      

4. سيتم تقديم الأذونات التي يحصل عليها Defender for Endpoint لكي يعمل. راجعها ثم حدد **موافقة**.

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="صفحة الموافقة على الأذونات في مدخل Microsoft Defender 365" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. سيتم تقديم صفحة إعدادات الموافقة. تؤكد الصفحة تفضيلك لمعالجة أذونات التطبيق الجديدة التي قد يطلبها Defender for Endpoint على Android. راجع الخيارات وحدد الخيار المفضل لديك. حدد **تم**.

    بشكل افتراضي، تحدد Google Play المدارة **الاحتفاظ بالموافقة عندما يطلب التطبيق أذونات جديدة**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" صفحة إكمال تكوين إعدادات الموافقة في مدخل Microsoft Defender 365" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. بعد تحديد معالجة الأذونات، حدد **مزامنة** Microsoft Defender لنقطة النهاية إلى قائمة التطبيقات.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="جزء المزامنة في مدخل Microsoft Defender 365" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. ستكتمل المزامنة في غضون دقائق قليلة.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="جزء حالة مزامنة التطبيق في صفحة تطبيقات Android في مدخل Microsoft Defender 365"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. حدد الزر **تحديث** في شاشة تطبيقات Android Microsoft Defender لنقطة النهاية يجب أن يكون مرئيا في قائمة التطبيقات.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="الصفحة التي تعرض التطبيق المتزامن" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. يدعم Defender for Endpoint سياسات تكوين التطبيق للأجهزة المدارة عبر Intune. يمكن الاستفادة من هذه الإمكانية للحصول على أذونات (أذونات) Android القابلة للتطبيق، وبالتالي لا يحتاج المستخدم إلى قبول هذه الأذونات (الأذونات).

    1. في صفحة **التطبيقات** ، انتقل إلى نهج > نهج تكوين التطبيق > **إضافة > مدارة**.

       :::image type="content" source="images/android-mem.png" alt-text="جزء &quot;سياسات تكوين التطبيق&quot; في مدخل إدارة نقاط النهاية من Microsoft مركز الإدارة" lightbox="images/android-mem.png":::

    1. في الصفحة **إنشاء نهج تكوين التطبيق** ، أدخل التفاصيل التالية:

        - الاسم: Microsoft Defender لنقطة النهاية.
        - اختر **Android Enterprise** كنهاية أساسية.
        - اختر **ملف تعريف العمل كنوع** ملف تعريف فقط.
        - انقر **فوق تحديد تطبيق**، **واختر Microsoft Defender ATP**، وحدد **موافق** ثم **التالي**.

        :::image type="content" source="images/android-create-app.png" alt-text=" جزء تفاصيل التطبيق المقترن" lightbox="images/android-create-app.png":::

    1. في الصفحة **الإعدادات**، انتقل إلى المقطع أذونات انقر فوق إضافة لعرض قائمة الأذونات المعتمدة. في المقطع إضافة أذونات، حدد الأذونات التالية:

       - مساحة تخزين خارجية (قراءة)
       - مساحة تخزين خارجية (كتابة)

       ثم حدد **موافق**.

       :::image type="content" source="images/android-create-app-config.png" alt-text="الجزء &quot;إضافة أذونات&quot;" lightbox="images/android-create-app-config.png":::

    1. من المفترض أن ترى الآن الأذونات المدرجة والآن يمكنك أن تقوم بجريرة تلقائية على كليهما عن طريق اختيار "طلب تلقائي" في القائمة المنسدلة حالة الأذونات ثم تحديد **التالي**.

       :::image type="content" source="images/android-auto-grant.png" alt-text="جزء حالة الأذونات" lightbox="images/android-auto-grant.png":::

    1. في صفحة **الواجبات** ، حدد مجموعة المستخدمين التي سيتم تعيين نهج تكليف التطبيق لها. انقر **فوق تحديد المجموعات لتضمين** المجموعة القابلة للتطبيق وتحديدها ثم تحديد **التالي**. عادة ما تكون المجموعة المحددة هنا هي المجموعة نفسها التي يمكنك تعيين Microsoft Defender لنقطة النهاية Android لها.

       :::image type="content" source="images/android-select-group.png" alt-text="جزء المجموعات المحددة" lightbox="images/android-select-group.png":::

    1. في الصفحة **مراجعة + إنشاء** التي تأتي بعد ذلك، راجع كل المعلومات ثم حدد **إنشاء**.

        يتم الآن تعيين نهج تكوين التطبيق ل Defender for Endpoint الذي يقوم بالتخزين التلقائي لإذن التخزين إلى مجموعة المستخدمين المحددة.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="علامة التبويب &quot;مراجعة + إنشاء&quot; في الصفحة &quot;إنشاء نهج تكوين التطبيق&quot;" lightbox="images/android-review-create.png":::

10. حدد **تطبيق ATP ل Microsoft Defender** في القائمة \> **خصائص** \> **تحرير الواجبات**\>.

   :::image type="content" source="images/mda-properties.png" alt-text="الخيار &quot;تحرير&quot; على الصفحة &quot;خصائص&quot;" lightbox="images/mda-properties.png":::

11. تعيين التطبيق ك تطبيق *مطلوب* إلى مجموعة مستخدمين. يتم تثبيته تلقائيا في ملف *تعريف العمل* أثناء المزامنة التالية للجهاز عبر Company Portal التطبيق. يمكن إجراء هذا الواجب من خلال الانتقال إلى  \> مجموعة إضافة المقطع مطلوب، وتحديد مجموعة المستخدمين والنقر فوق **تحديد**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="صفحة تحرير التطبيق" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. في الصفحة **تحرير التطبيق** ، راجع كل المعلومات التي تم إدخالها أعلاه. ثم حدد **مراجعة + حفظ** ثم **حفظ** مرة أخرى لبدء التعيين.

### <a name="auto-setup-of-always-on-vpn"></a>الإعداد التلقائي ل VPN دائما

يدعم Defender for Endpoint سياسات تكوين الجهاز للأجهزة المدارة عبر Intune. يمكن الاستفادة من هذه الإمكانية للإعداد التلقائي ل **VPN** دائما على الأجهزة التي تم تسجيلها في Android Enterprise، لذلك لا يحتاج المستخدم إلى إعداد خدمة VPN أثناء الالتحاق.

1. على **الأجهزة،** حدد **ملفات تعريف التكوين** \> **إنشاء النظام الأساسي لملف التعريف** \>  \> **Android Enterprise**

   حدد **قيود الجهاز** ضمن أحد الخطوات التالية، استنادا إلى نوع تسجيل جهازك:
   - **ملف تعريف العمل المدار والمخصص Corporate-Owned بالكامل**
   - **ملف تعريف العمل الممتلك شخصيا**

   حدد **إنشاء**.

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="عنصر القائمة &quot;ملفات تعريف التكوين&quot; في جزء &quot;النهج&quot;" lightbox="images/1autosetupofvpn.png":::

2. **تكوين الإعدادات** توفير **اسم** ووصف لتعريف ملف تعريف التكوين بشكل  فريد.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="الحقلان &quot;اسم ملف تعريف تكوين الأجهزة&quot; و&quot;الوصف&quot; في جزء &quot;الأساسيات&quot;" lightbox="images/2autosetupofvpn.png":::

3. حدد **الاتصال** وتكوين VPN:

   - تمكين **VPN دائما**

     قم بإعداد عميل VPN في ملف تعريف العمل للاتصال ب VPN وإعادة الاتصال به تلقائيا كلما أمكن ذلك. يمكن تكوين عميل VPN واحد فقط ل VPN دائما على جهاز معين، لذا تأكد من عدم نشر أكثر من نهج VPN واحد دائما على جهاز واحد.

   - تحديد **"مخصص** " في القائمة المنسدلة "عميل VPN"

     VPN المخصص في هذه الحالة هو Defender for Endpoint VPN الذي يتم استخدامه لتوفير ميزة حماية الويب.

     > [!NOTE]
     > Microsoft Defender لنقطة النهاية أن يكون التطبيق مثبتا على جهاز المستخدم، لكي يعمل الإعداد التلقائي لهذه VPN.

   - أدخل **"معر ة** الحزمة" Microsoft Defender لنقطة النهاية التطبيق في متجر Google Play. بالنسبة إلى عنوان URL الخاص لتطبيق Defender <https://play.google.com/store/apps/details?id=com.microsoft.scmx>، يكون "الم ID الحزمة **" هو com.microsoft.scmx**

   - **وضع التأمين** غير مكون (افتراضي)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="جزء الاتصال ضمن علامة التبويب إعدادات التكوين" lightbox="images/3autosetupofvpn.png":::

4. **الواجب**

   في صفحة **الواجبات** ، حدد مجموعة المستخدمين التي سيتم تعيين نهج تكليف التطبيق لها. اختر **تحديد المجموعات** لتضمين المجموعة القابلة للتطبيق وتحديدها، ثم حدد **التالي**. عادة ما تكون المجموعة المحددة هنا هي المجموعة نفسها التي يمكنك تعيين Microsoft Defender لنقطة النهاية Android لها.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="جزء تعيين ملف تعريف تكوين الأجهزة في قيود الجهاز" lightbox="images/4autosetupofvpn.png":::

5. في الصفحة **مراجعة + إنشاء** التي تأتي بعد ذلك، راجع كل المعلومات ثم حدد **إنشاء**.
يتم الآن تعيين ملف تعريف تكوين الجهاز إلى مجموعة المستخدمين المحددة.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="توفير ملف تعريف تكوين الأجهزة ل Review + create" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>التحقق من الحالة وإكمال الboarding

1. تأكد من حالة تثبيت Microsoft Defender لنقطة النهاية Android بالنقر فوق حالة **تثبيت الجهاز**. تحقق من عرض الجهاز هنا.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="جزء حالة تثبيت الجهاز" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. على الجهاز، يمكنك التحقق من حالة التكهين من خلال الذهاب إلى **ملف تعريف العمل**. تأكد من توفر Defender for Endpoint وأنك مسجل في الأجهزة المملوكة شخصيا **باستخدام ملف تعريف العمل**. إذا كنت مسجلا في جهاز مستخدم تملكه الشركة ويدار بشكل كامل، سيكون لديك ملف تعريف واحد على الجهاز حيث يمكنك تأكيد توفر Defender for Endpoint.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="جزء عرض التطبيق" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. عند تثبيت التطبيق، افتح التطبيق واقبل الأذونات، ومن ثم يجب أن تكون عملية التركيب ناجحة.

    :::image type="content" source="images/MDE_new.png" alt-text="عرض تطبيق Microsoft Defender لنقطة النهاية على جهاز محمول" lightbox="images/MDE_new.png":::

4. في هذه المرحلة، يتم تشغيل الجهاز بنجاح في Defender for Endpoint على Android. يمكنك التحقق من ذلك على Microsoft 365 Defender [من](https://security.microsoft.com) خلال الانتقال إلى **صفحة مخزون** الجهاز.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="مدخل Microsoft Defender لنقطة النهاية" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على Microsoft Defender لنقطة النهاية على Android](microsoft-defender-endpoint-android.md)
- [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md)
