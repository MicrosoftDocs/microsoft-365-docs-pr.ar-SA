---
title: نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune
description: يصف كيفية نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mde، android، التثبيت، التوزيع، إلغاء التثبيت،
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
ms.openlocfilehash: c743b54e27bc9caa60bb6b4e24191d626ece6fcf
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490498"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-android-with-microsoft-intune"></a>نشر Microsoft Defender لنقطة النهاية على Android باستخدام Microsoft Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

تعرف على كيفية نشر Defender لنقطة النهاية على Android على Intune Company Portal الأجهزة المسجلة. لمزيد من المعلومات حول تسجيل جهاز Intune، راجع [تسجيل جهازك](/mem/intune/user-help/enroll-device-android-company-portal).

> [!NOTE]
> **يتوفر Defender لنقطة النهاية على Android الآن على [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.scmx)**
>
> يمكنك الاتصال ب Google Play من Intune لنشر تطبيق Defender لنقطة النهاية عبر أوضاع تسجيل مسؤول الجهاز وAndroid Enterprise.
>
> تتم التحديثات إلى التطبيق تلقائيا عبر Google Play.

## <a name="deploy-on-device-administrator-enrolled-devices"></a>النشر على الأجهزة المسجلة في مسؤول الجهاز

تعرف على كيفية نشر Defender لنقطة النهاية على Android على Intune Company Portal - الأجهزة المسجلة من قبل مسؤول الجهاز.

### <a name="add-as-android-store-app"></a>إضافة كتطبيق متجر Android

1. في [مركز إدارة Microsoft إدارة نقاط النهاية](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى تطبيق متجر **تطبيقات** \> **Android** \> **Add \> Android** واختر **"تحديد**".

   :::image type="content" source="images/mda-addandroidstoreapp.png" alt-text="جزء تطبيق &quot;إضافة متجر Android&quot; في مدخل Microsoft إدارة نقاط النهاية مسؤول Center"  lightbox="images/mda-addandroidstoreapp.png":::

2. في صفحة **"إضافة تطبيق** " وفي قسم *"معلومات التطبيق* "، أدخل:

   - **الاسم**
   - **الوصف**
   - **Publisher** ك Microsoft.
   - **عنوان URL لمتجر التطبيقات** ك https://play.google.com/store/apps/details?id=com.microsoft.scmx (Defender for Endpoint app متجر Google Play URL)

   الحقول الأخرى اختيارية. حدد **التالي**.

   :::image type="content" source="images/mda-addappinfo.png" alt-text="صفحة &quot;إضافة تطبيق&quot; تعرض معلومات ناشر التطبيق وعنوان URL في مدخل Microsoft إدارة نقاط النهاية مسؤول Center" lightbox="images/mda-addappinfo.png":::

3. في المقطع *"الواجبات* "، انتقل إلى المقطع **"مطلوب** " وحدد **"إضافة مجموعة".** يمكنك بعد ذلك اختيار مجموعة (مجموعات) المستخدمين التي ترغب في استهداف Defender لنقطة النهاية على تطبيق Android. اختر **"تحديد"** ثم **"التالي**".

    > [!NOTE]
    > يجب أن تتكون مجموعة المستخدمين المحددة من المستخدمين المسجلين في Intune.
    >
    > :::image type="content" source="images/363bf30f7d69a94db578e8af0ddd044b.png" alt-text="الجزء &quot;إضافة مجموعة&quot; في صفحة &quot;إضافة تطبيق&quot; في مدخل Microsoft إدارة نقاط النهاية مسؤول Center" lightbox="images/363bf30f7d69a94db578e8af0ddd044b.png":::

4. في المقطع **Review+Create** ، تحقق من صحة كافة المعلومات التي تم إدخالها ثم حدد **"إنشاء**".

    في بضع لحظات، سيتم إنشاء تطبيق Defender لنقطة النهاية بنجاح، وسيظهر إعلام في الزاوية العلوية اليسرى من الصفحة.

    :::image type="content" source="images/86cbe56f88bb6e93e9c63303397fc24f.png" alt-text="جزء حالة التطبيق في مدخل مركز إدارة نقاط النهاية مسؤول Microsoft" lightbox="images/86cbe56f88bb6e93e9c63303397fc24f.png":::

5. في صفحة معلومات التطبيق المعروضة، في قسم **"Monitor** "، حدد **حالة تثبيت الجهاز** للتحقق من اكتمال تثبيت الجهاز بنجاح.

    :::image type="content" source="images/513cf5d59eaaef5d2b5bc122715b5844.png" alt-text="صفحة حالة تثبيت الجهاز في مدخل Microsoft Defender 365" lightbox="images/513cf5d59eaaef5d2b5bc122715b5844.png":::

### <a name="complete-onboarding-and-check-status"></a>إكمال الإلحاق والتحقق من الحالة

1. بمجرد تثبيت Defender لنقطة النهاية على Android على الجهاز، سترى أيقونة التطبيق.

   :::image type="content" source="images/7cf9311ad676ec5142002a4d0c2323ca.jpg" alt-text="أيقونة Microsoft Defender ATP المدرجة في جزء البحث" lightbox="images/7cf9311ad676ec5142002a4d0c2323ca.jpg":::

2. اضغط على أيقونة تطبيق Microsoft Defender لنقطة النهاية واتبع الإرشادات التي تظهر على الشاشة لإكمال إلحاق التطبيق. تتضمن التفاصيل قبول المستخدم النهائي لأذونات Android المطلوبة من قبل Defender لنقطة النهاية على Android.

3. عند نجاح عملية الإلحاق، سيبدأ الجهاز في الظهور على قائمة الأجهزة في مدخل Microsoft 365 Defender.

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="جهاز في مدخل Microsoft Defender لنقطة النهاية"  lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="deploy-on-android-enterprise-enrolled-devices"></a>النشر على الأجهزة المسجلة في Android Enterprise

يدعم Defender لنقطة النهاية على Android الأجهزة المسجلة في Android Enterprise.

لمزيد من المعلومات حول خيارات التسجيل التي يدعمها Intune، راجع [خيارات التسجيل](/mem/intune/enrollment/android-enroll).

**حاليا، يتم دعم الأجهزة المملوكة شخصيا مع ملف تعريف العمل وتسجيلات أجهزة المستخدم المدارة بالكامل المملوكة للشركة للتوزيع.**

## <a name="add-microsoft-defender-for-endpoint-on-android-as-a-managed-google-play-app"></a>إضافة Microsoft Defender لنقطة النهاية على Android كتطبيق Google Play مدار

اتبع الخطوات أدناه لإضافة تطبيق Microsoft Defender لنقطة النهاية إلى Google Play المدار.

1. في [مركز إدارة Microsoft إدارة نقاط النهاية](https://go.microsoft.com/fwlink/?linkid=2109431)، انتقل إلى **تطبيقات** \> **Android Apps** \> **Add** وحدد **تطبيق Google Play المدار**.

    :::image type="content" source="images/579ff59f31f599414cedf63051628b2e.png" alt-text="جزء إضافة التطبيق في مدخل مركز إدارة Microsoft إدارة نقاط النهاية" lightbox="images/579ff59f31f599414cedf63051628b2e.png":::

2. في صفحة Google Play المدارة التي يتم تحميلها لاحقا، انتقل إلى مربع البحث وأدخل `Microsoft Defender`. يجب أن يعرض بحثك تطبيق Microsoft Defender لنقطة النهاية في Google Play المدار. انقر فوق تطبيق Microsoft Defender لنقطة النهاية من نتيجة البحث في التطبيقات.

    :::image type="content" source="images/0f79cb37900b57c3e2bb0effad1c19cb.png" alt-text="صفحة Google Play المدارة في مدخل مركز إدارة Microsoft إدارة نقاط النهاية" lightbox="images/0f79cb37900b57c3e2bb0effad1c19cb.png":::

3. في صفحة وصف التطبيق التي تظهر بعد ذلك، يجب أن تكون قادرا على رؤية تفاصيل التطبيق على Defender لنقطة النهاية. راجع المعلومات الموجودة على الصفحة ثم حدد **"موافقة**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/07e6d4119f265037e3b80a20a73b856f.png" alt-text="صفحة Google Play المدارة في مدخل مركز إدارة Microsoft إدارة نقاط النهاية" lightbox="images/07e6d4119f265037e3b80a20a73b856f.png":::

4. سيتم تقديم الأذونات التي يحصل عليها Defender for Endpoint لكي يعمل. راجعها ثم حدد **"موافقة**".

    :::image type="content" source="images/206b3d954f06cc58b3466fb7a0bd9f74.png" alt-text="صفحة الموافقة على الأذونات في مدخل Microsoft Defender 365" lightbox="images/206b3d954f06cc58b3466fb7a0bd9f74.png":::

5. سيتم تقديم صفحة إعدادات الموافقة. تؤكد الصفحة تفضيلك للتعامل مع أذونات التطبيق الجديدة التي قد يطلبها Defender لنقطة النهاية على Android. راجع الخيارات وحدد الخيار المفضل لديك. حدد **«Done»**.

    بشكل افتراضي، يحدد Google Play المدار **الاحتفاظ بالموافقة عندما يطلب التطبيق أذونات جديدة**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ffecfdda1c4df14148f1526c22cc0236.png" alt-text=" صفحة إكمال تكوين إعدادات الموافقة في مدخل Microsoft Defender 365" lightbox="images/ffecfdda1c4df14148f1526c22cc0236.png":::

6. بعد إجراء الأذونات التي تعالج التحديد، حدد **"مزامنة**" للمزامنة Microsoft Defender لنقطة النهاية إلى قائمة التطبيقات.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/34e6b9a0dae125d085c84593140180ed.png" alt-text="جزء المزامنة في مدخل Microsoft Defender 365" lightbox="images/34e6b9a0dae125d085c84593140180ed.png":::

7. ستكتمل المزامنة بعد بضع دقائق.

    :::image type="content" source="images/9fc07ffc150171f169dc6e57fe6f1c74.png" alt-text="جزء حالة مزامنة التطبيق في صفحة تطبيقات Android في مدخل Microsoft Defender 365"  lightbox="images/9fc07ffc150171f169dc6e57fe6f1c74.png":::

8. حدد الزر **"تحديث**" في شاشة تطبيقات Android ويجب أن يكون Microsoft Defender لنقطة النهاية مرئيا في قائمة التطبيقات.

    :::image type="content" source="images/fa4ac18a6333335db3775630b8e6b353.png" alt-text="الصفحة التي تعرض التطبيق الذي تمت مزامنته" lightbox="images/fa4ac18a6333335db3775630b8e6b353.png":::

9. يدعم Defender لنقطة النهاية نهج تكوين التطبيقات للأجهزة المدارة عبر Intune. يمكن الاستفادة من هذه الإمكانية لتحديد تكوينات مختلفة ل Defender.

    1. في صفحة **التطبيقات** ، انتقل إلى **نهج تكوين > نهج التطبيق > إضافة أجهزة مدارة >**.

       :::image type="content" source="images/android-mem.png" alt-text="جزء نهج تكوين التطبيق في مدخل مركز إدارة Microsoft إدارة نقاط النهاية" lightbox="images/android-mem.png":::

    1. في صفحة **إنشاء نهج تكوين التطبيق** ، أدخل التفاصيل التالية:

        - الاسم: Microsoft Defender لنقطة النهاية.
        - اختر **Android Enterprise** كمنصة.
        - اختر **ملف تعريف العمل كنوع** ملف تعريف فقط.
        - انقر فوق **"تحديد تطبيق**"، واختر **Microsoft Defender ATP**، وحدد **"موافق** " ثم **"التالي**".

        :::image type="content" source="images/android-create-app.png" alt-text=" جزء تفاصيل التطبيق المقترن" lightbox="images/android-create-app.png":::

    1. في **الصفحة "إعدادات"** ، انتقل إلى قسم **إعدادات التكوين** واختر **"استخدام مصمم التكوين"** بتنسيق إعدادات التكوين. 

       :::image type="content" alt-text="صورة لنهج إنشاء تطبيق android." source="images/configurationformat.png" lightbox="images/configurationformat.png":::

    1. انقر فوق **"إضافة"** لعرض قائمة التكوينات المعتمدة. حدد التكوين المطلوب وانقر فوق **"موافق**".

       :::image type="content" alt-text="صورة لتحديد نهج التكوين لنظام التشغيل android." source="images/selectconfigurations.png" lightbox="images/selectconfigurations.png":::

    1. يجب أن تشاهد كافة التكوينات المحددة مدرجة. يمكنك تغيير قيمة التكوين كما هو مطلوب ثم تحديد **"التالي**".

       :::image type="content" alt-text="صورة لنهج التكوين المحددة." source="images/listedconfigurations.png" lightbox="images/listedconfigurations.png":::

    1. في صفحة **"الواجبات** "، حدد مجموعة المستخدمين التي سيتم تعيين نهج تكوين التطبيق لها. انقر فوق **"تحديد المجموعات" لتضمين** المجموعة القابلة للتطبيق وتحديدها، ثم حدد **"التالي**". عادة ما تكون المجموعة المحددة هنا هي نفس المجموعة التي ستقوم بتعيين Microsoft Defender لنقطة النهاية تطبيق Android إليها.

       :::image type="content" source="images/android-select-group.png" alt-text="جزء المجموعات المحددة" lightbox="images/android-select-group.png":::

    1. في الصفحة **Review + Create** التي تأتي بعد ذلك، راجع كافة المعلومات ثم حدد **Create**.

        يتم الآن تعيين نهج تكوين التطبيق ل Defender لنقطة النهاية لأتمتة إذن التخزين إلى مجموعة المستخدمين المحددة.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="images/android-review-create.png" alt-text="علامة التبويب &quot;مراجعة + إنشاء&quot; في صفحة &quot;إنشاء نهج تكوين التطبيق&quot;" lightbox="images/android-review-create.png":::

10. حدد تطبيق **Microsoft Defender ATP** في القائمة \> "**تحرير** **تعيينات** \> **الخصائص**\>".

    :::image type="content" source="images/mda-properties.png" alt-text="الخيار &quot;تحرير&quot; على الصفحة &quot;خصائص&quot;" lightbox="images/mda-properties.png":::

11. تعيين التطبيق كتطبيق *مطلوب* إلى مجموعة مستخدمين. يتم تثبيته تلقائيا في *ملف تعريف العمل* أثناء المزامنة التالية للجهاز عبر تطبيق Company Portal. يمكن تنفيذ هذا التعيين بالانتقال إلى **المجموعة "إضافة** مقطع \> *مطلوب*"، وتحديد مجموعة المستخدمين والنقر فوق **"تحديد**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ea06643280075f16265a596fb9a96042.png" alt-text="صفحة تحرير التطبيق" lightbox="images/ea06643280075f16265a596fb9a96042.png":::

12. في صفحة **"تحرير التطبيق** "، راجع كافة المعلومات التي تم إدخالها أعلاه. ثم حدد **Review + Save** ثم **Save** مرة أخرى لبدء التعيين.

### <a name="auto-setup-of-always-on-vpn"></a>الإعداد التلقائي ل VPN دائما

يدعم Defender لنقطة النهاية نهج تكوين الجهاز للأجهزة المدارة عبر Intune. يمكن الاستفادة من هذه الإمكانية **للإعداد التلقائي ل VPN Always-on على** الأجهزة المسجلة في Android Enterprise، لذلك لا يحتاج المستخدم النهائي إلى إعداد خدمة VPN أثناء الإلحاق.

1. على **الأجهزة**، حدد **Configuration Profiles** \> **Create Profile** \> **Platform** \> **Android Enterprise**

   حدد **قيود الجهاز** ضمن أحد الإجراءات التالية، استنادا إلى نوع تسجيل الجهاز:
   - **ملف تعريف العمل المدار بالكامل والمخصص Corporate-Owned**
   - **ملف تعريف العمل المملوك شخصيا**

   حدد **"إنشاء**".

   :::image type="content" source="images/1autosetupofvpn.png" alt-text="عنصر قائمة ملفات تعريف التكوين في جزء &quot;النهج&quot;" lightbox="images/1autosetupofvpn.png":::

2. **إعدادات التكوين** توفير **اسم** **ووصف** لتعريف ملف تعريف التكوين بشكل فريد.

   :::image type="content" source="images/2autosetupofvpn.png" alt-text="الحقلان &quot;اسم ملف تعريف تكوين الأجهزة&quot; و&quot;الوصف&quot; في جزء &quot;الأساسيات&quot;" lightbox="images/2autosetupofvpn.png":::

3. حدد **الاتصال** وكون VPN:

   - تمكين **VPN دائما**

     إعداد عميل VPN في ملف تعريف العمل للاتصال تلقائيا وإعادة الاتصال بشبكة VPN كلما أمكن ذلك. يمكن تكوين عميل VPN واحد فقط ل VPN دائما على جهاز معين، لذا تأكد من عدم نشر أكثر من نهج VPN واحد دائما على جهاز واحد.

   - تحديد **مخصص** في القائمة المنسدلة لعميل VPN

     VPN المخصص في هذه الحالة هو Defender لنقطة النهاية VPN الذي يستخدم لتوفير ميزة حماية الويب.

     > [!NOTE]
     > يجب تثبيت تطبيق Microsoft Defender لنقطة النهاية على جهاز المستخدم، من أجل تشغيل الإعداد التلقائي ل VPN هذا.

   - أدخل **معرف الحزمة** لتطبيق Microsoft Defender لنقطة النهاية في متجر Google Play. بالنسبة إلى عنوان URL <https://play.google.com/store/apps/details?id=com.microsoft.scmx>لتطبيق Defender، معرف الحزمة هو **com.microsoft.scmx**

   - **وضع التأمين** غير مكون (افتراضي)

     :::image type="content" source="images/3autosetupofvpn.png" alt-text="جزء الاتصال ضمن علامة التبويب &quot;إعدادات التكوين&quot;" lightbox="images/3autosetupofvpn.png":::

4. **التعيين**

   في صفحة **"الواجبات** "، حدد مجموعة المستخدمين التي سيتم تعيين نهج تكوين التطبيق إليها. اختر **"تحديد المجموعات** " لتضمين المجموعة القابلة للتطبيق وتحديدها، ثم حدد **"التالي**". عادة ما تكون المجموعة المحددة هنا هي نفس المجموعة التي ستقوم بتعيين Microsoft Defender لنقطة النهاية تطبيق Android إليها.

   :::image type="content" source="images/4autosetupofvpn.png" alt-text="جزء تعيين ملف تعريف تكوين الأجهزة في قيود الجهاز" lightbox="images/4autosetupofvpn.png":::

5. في الصفحة **Review + Create** التي تأتي بعد ذلك، راجع كافة المعلومات ثم حدد **Create**.
تم الآن تعيين ملف تعريف تكوين الجهاز إلى مجموعة المستخدمين المحددة.

   :::image type="content" source="images/5autosetupofvpn.png" alt-text="توفير ملف تعريف تكوين الأجهزة للمراجعة + الإنشاء" lightbox="images/5autosetupofvpn.png":::

## <a name="check-status-and-complete-onboarding"></a>التحقق من الحالة وإكمال الإلحاق

1. تأكد من حالة تثبيت Microsoft Defender لنقطة النهاية على Android بالنقر فوق **حالة تثبيت الجهاز**. تحقق من عرض الجهاز هنا.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/900c0197aa59f9b7abd762ab2b32e80c.png" alt-text="جزء حالة تثبيت الجهاز" lightbox="images/900c0197aa59f9b7abd762ab2b32e80c.png":::

2. على الجهاز، يمكنك التحقق من صحة حالة الإلحاق بالانتقال إلى **ملف تعريف العمل**. تأكد من توفر Defender لنقطة النهاية وأنك مسجل في **الأجهزة المملوكة شخصيا مع ملف تعريف العمل**. إذا كنت مسجلا في **جهاز مستخدم مملوك للشركة مدار بالكامل**، فسيكون لديك ملف تعريف واحد على الجهاز حيث يمكنك تأكيد توفر Defender لنقطة النهاية.

    :::image type="content" source="images/c2e647fc8fa31c4f2349c76f2497bc0e.png" alt-text="جزء عرض التطبيق" lightbox="images/c2e647fc8fa31c4f2349c76f2497bc0e.png":::

3. عند تثبيت التطبيق، افتح التطبيق واقبل الأذونات ومن ثم يجب أن يكون الإعداد ناجحا.

    :::image type="content" source="images/MDE_new.png" alt-text="عرض تطبيق Microsoft Defender لنقطة النهاية على جهاز محمول" lightbox="images/MDE_new.png":::

4. في هذه المرحلة، تم إلحاق الجهاز بنجاح ب Defender لنقطة النهاية على Android. يمكنك التحقق من ذلك على [مدخل Microsoft 365 Defender](https://security.microsoft.com) عن طريق الانتقال إلى صفحة **"مخزون الجهاز**".

    :::image type="content" source="images/9fe378a1dce0f143005c3aa53d8c4f51.png" alt-text="مدخل Microsoft Defender لنقطة النهاية" lightbox="images/9fe378a1dce0f143005c3aa53d8c4f51.png":::

## <a name="set-up-microsoft-defender-in-personal-profile-on-android-enterprise-in-byod-mode"></a>إعداد Microsoft Defender في ملف التعريف الشخصي على Android Enterprise في وضع BYOD

### <a name="set-up-microsoft-defender-in-personal-profile"></a>إعداد Microsoft Defender في ملف التعريف الشخصي

يمكن للمسؤولين الانتقال إلى [مركز إدارة نقاط النهاية من Microsoft](https://endpoint.microsoft.com) لإعداد وتكوين دعم Microsoft Defender في ملفات التعريف الشخصية باتباع الخطوات التالية:

1. انتقل إلى **نهج تكوين التطبيقات> التطبيقات** وانقر فوق **"إضافة**". حدد **الأجهزة المدارة**.

    > [!div class="mx-imgBorder"]
    > ![صورة لإضافة نهج تكوين التطبيق.](images/addpolicy.png)

1. أدخل **الاسم** **والوصف** لتحديد نهج التكوين بشكل فريد. حدد النظام الأساسي ك **'Android Enterprise'**، ونوع ملف التعريف ك **'ملف تعريف العمل المملوك شخصيا فقط'** والتطبيق المستهدف ' **Microsoft Defender'**.

    > [!div class="mx-imgBorder"]
    > ![صورة لنهج تكوين التسمية.](images/selectapp.png)

1. في صفحة الإعدادات، في **"تنسيق إعدادات التكوين"**، حدد **"استخدام مصمم التكوين"** وانقر فوق **"إضافة**". من قائمة التكوينات التي يتم عرضها، حدد **"Microsoft Defender في ملف التعريف الشخصي".**

    > [!div class="mx-imgBorder"]
    > ![صورة لتكوين ملف التعريف الشخصي.](images/addconfiguration.png)

1. سيتم سرد التكوين المحدد. قم بتغيير **قيمة التكوين إلى 1** لتمكين ملفات تعريف دعم Microsoft Defender الشخصية. سيظهر إعلام لإعلام المسؤول بنفس الشيء. انقر فوق **"التالي**".

    > [!div class="mx-imgBorder"]
    > ![صورة لتغيير قيمة التكوين.](images/changeconfigvalue.png)

1. **تعيين** نهج التكوين إلى مجموعة من المستخدمين. **مراجعة النهج وإنشاءه** .

    > [!div class="mx-imgBorder"]
    > ![صورة لمراجعة النهج وإنشاءه.](images/savepolicy.png)

يمكن للمسؤولين أيضا إعداد **عناصر تحكم الخصوصية** من مركز إدارة Microsoft إدارة نقاط النهاية للتحكم في البيانات التي يمكن أن يرسلها عميل Defender للأجهزة المحمولة إلى مدخل الأمان. لمزيد من المعلومات، راجع [تكوين عناصر التحكم في الخصوصية](android-configure.md).

يمكن للمؤسسات الاتصال بمستخدميها لحماية ملف التعريف الشخصي باستخدام Microsoft Defender على أجهزة BYOD المسجلة.

- المتطلبات الأساسية: يجب أن يكون Microsoft Defender مثبتا بالفعل ونشطا في ملف تعريف العمل لتمكين Microsoft Defender في ملفات التعريف الشخصية.

### <a name="to-complete-onboarding-a-device"></a>لإكمال إلحاق جهاز

1. تثبيت تطبيق Microsoft Defender في ملف تعريف شخصي باستخدام حساب متجر Google Play شخصي.
2. تثبيت تطبيق مدخل الشركة على ملف التعريف الشخصي. لا يلزم تسجيل الدخول.
3. عندما يقوم مستخدم بتشغيل التطبيق، سيرى شاشة تسجيل الدخول. **تسجيل الدخول باستخدام حساب الشركة فقط**.
4. في تسجيل الدخول الناجح، سيرى المستخدمون الشاشات التالية:
   1. **شاشة EULA**: يتم تقديمها فقط إذا لم يوافق المستخدم بالفعل في ملف تعريف العمل.
   2. **شاشة الإشعار**: يحتاج المستخدمون إلى تقديم الموافقة على هذه الشاشة للمضي قدما في إلحاق التطبيق. هذا مطلوب فقط أثناء التشغيل الأول للتطبيق.
5. توفير الأذونات المطلوبة لإكمال الإلحاق.

> [!NOTE]
> **المتطلبات الأساسية:**
>
> 1. يجب تمكين مدخل الشركة على ملف التعريف الشخصي.
> 2. يجب أن يكون Microsoft Defender مثبتا ونشطا بالفعل في ملف تعريف العمل.

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على Microsoft Defender لنقطة النهاية على Android](microsoft-defender-endpoint-android.md)
- [تكوين Microsoft Defender لنقطة النهاية على ميزات Android](android-configure.md)
