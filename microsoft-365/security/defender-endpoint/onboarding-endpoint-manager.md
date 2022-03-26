---
title: الboarding باستخدام إدارة نقاط النهاية من Microsoft
description: تعرف على كيفية ال متن الطائرة في Microsoft Defender لنقطة النهاية باستخدام إدارة نقاط النهاية من Microsoft
keywords: التهيئة، التكوين، النشر، النشر، إدارة نقطة النهاية، Microsoft Defender ل Endpoint، إنشاء مجموعة، استجابة الكشف عن نقطة النهاية، حماية الجيل التالي، الحد من سطح الهجوم، إدارة نقطة نهاية Microsoft
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
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 261cb8af0f1fbb4c118aca649945f66015f1d25c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63570357"
---
# <a name="onboarding-using-microsoft-endpoint-manager"></a>الboarding باستخدام إدارة نقاط النهاية من Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

هذه المقالة هي جزء من دليل النشر، وهي تعمل كطريقة تكاتف كمثال.

في موضوع [التخطيط](deployment-strategy.md) ، تم توفير عدة أساليب للأجهزة المجهزة للخدمة. يتناول هذا الموضوع البنية الأصلية للسحابة.

![صورة لهندسة السحابة الأصلية.](images/cloud-native-architecture.png)
 *رسم تخطيطي لهنيات البيئة*

على الرغم من أن Defender for Endpoint يدعم التكهن بنقاط النهاية والأدوات المختلفة، لا تغطي هذه المقالة هذه النقاط والأدوات. للحصول على معلومات حول التكديب العام باستخدام أساليب وأدوات النشر المعتمدة الأخرى، راجع [نظرة عامة على التكديب](onboarding.md).

[إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) هو نظام أساسي للحلول يوحد خدمات متعددة. وتتضمن هذه [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) الأجهزة المستندة إلى البيانات.

يرشد هذا الموضوع المستخدمين في:

- الخطوة 1: تهيئة الأجهزة للخدمة عن طريق إنشاء مجموعة في إدارة نقاط النهاية من Microsoft (MEM) لتعيين تكوينات على
- الخطوة 2: تكوين Defender لإمكانيات نقطة النهاية باستخدام إدارة نقاط النهاية من Microsoft

ستعرض لك إرشادات التكسير هذه الخطوات الأساسية التالية التي تحتاج إلى اتخاذها عند استخدام إدارة نقاط النهاية من Microsoft:

- [تحديد الأجهزة أو المستخدمين الهدفين](#identify-target-devices-or-users)
  - إنشاء مجموعة Azure Active Directory (مستخدم أو جهاز)
- [إنشاء ملف تعريف تكوين](#step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities)
  - في إدارة نقاط النهاية من Microsoft، سنرشدك في إنشاء نهج منفصل لكل قدرة.

## <a name="resources"></a>الموارد

فيما يلي الارتباطات التي ستحتاج إليها لبقية العملية:

- [مدخل MEM](https://aka.ms/memac)
- [Microsoft 365 Defender](https://security.microsoft.com)
- [خطوط أمان Intune الأساسية](/mem/intune/protect/security-baseline-settings-defender-atp#microsoft-defender)

لمزيد من المعلومات حول إدارة نقاط النهاية من Microsoft، راجع هذه الموارد:

- [إدارة نقاط النهاية من Microsoft الصفحة](/mem/)
- [منشور مدونة حول نشر Intune و ConfigMgr](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace/)
- [فيديو مقدمة حول MEM](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace)

## <a name="step-1-onboard-devices-by-creating-a-group-in-mem-to-assign-configurations-on"></a>الخطوة 1: أجهزة التهيئة من خلال إنشاء مجموعة في MEM لتعيين تكوينات على

### <a name="identify-target-devices-or-users"></a>تحديد الأجهزة أو المستخدمين الهدفين

في هذا القسم، سنقوم بإنشاء مجموعة اختبار لتعيين تكويناتك عليها.

> [!NOTE]
> يستخدم Intune مجموعات Azure Active Directory (Azure AD) لإدارة الأجهزة والمستخدمين. ب أنت مسؤول Intune، يمكنك إعداد المجموعات لتتناسب مع احتياجات المؤسسة.
>
> لمزيد من المعلومات، راجع [إضافة مجموعات لتنظيم المستخدمين والأجهزة](/mem/intune/fundamentals/groups-add).

### <a name="create-a-group"></a>إنشاء مجموعة

1. افتح مدخل MEM.

2. افتح **المجموعات > جديدة**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل1.](images/66f724598d9c3319cba27f79dd4617a4.png)

3. أدخل التفاصيل وأنشئ مجموعة جديدة.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل 2.](images/b1e0206d675ad07db218b63cd9b9abc3.png)

4. أضف المستخدم أو الجهاز الاختباري.

5. من جزء **المجموعات > كافة** المجموعات، افتح المجموعة الجديدة.

6. حدد  **الأعضاء > إضافة أعضاء**.

7. ابحث عن المستخدم أو الجهاز الاختباري وحدده.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل3.](images/149cbfdf221cdbde8159d0ab72644cd0.png)

8. أصبحت الآن مجموعة الاختبار لديك عضوا لاختباره.

## <a name="step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities"></a>الخطوة 2: إنشاء سياسات تكوين لتكوين قدرات نقطة النهاية ل Microsoft Defender

في المقطع التالي، ستنشئ عددا من سياسات التكوين.

أولا هو نهج تكوين لتحديد مجموعات المستخدمين أو الأجهزة التي سيتم تهيئةها في Defender لنقطة النهاية:

- [الكشف عن نقطة النهاية والاستجابة لها](#endpoint-detection-and-response)

بعد ذلك، ستستمر في إنشاء عدة أنواع مختلفة من سياسات أمان نقاط النهاية:

- [حماية الجيل التالي](#next-generation-protection)
- [الحد من سطح الهجوم](#attack-surface-reduction---attack-surface-reduction-rules)

### <a name="endpoint-detection-and-response"></a>الكشف عن نقطة النهاية والاستجابة لها

1. افتح مدخل MEM.

2. انتقل إلى **نقطة النهاية > للكشف عن نقطة النهاية والاستجابة لها**. انقر فوق **إنشاء ملف تعريف**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل4.](images/58dcd48811147feb4ddc17212b7fe840.png)

3. ضمن **النظام الأساسي، حدد Windows 10 واللاحقة، ملف التعريف - الكشف عن نقطة النهاية والاستجابة > إنشاء**.

4. أدخل اسما ووصفا، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل5.](images/a5b2d23bdd50b160fef4afd25dda28d4.png)

5. حدد الإعدادات كما تقتضي الحاجة، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل6.](images/cea7e288b5d42a9baf1aef0754ade910.png)

    > [!NOTE]
    > في هذا المثيل، تم ملء هذا البرنامج بشكل تلقائي بتكامل Defender for Endpoint بالفعل مع Intune. لمزيد من المعلومات حول التكامل، راجع [تمكين Microsoft Defender لنقطة النهاية في Intune](/mem/intune/protect/advanced-threat-protection-configure#to-enable-microsoft-defender-atp).
    >
    > الصورة التالية هي مثال لما ستشاهده عندما لا يكون Microsoft Defender for Endpoint متكاملا مع Intune:
    >
    > ![صورة إدارة نقاط النهاية من Microsoft portal7.](images/2466460812371ffae2d19a10c347d6f4.png)

6. أضف علامات النطاق إذا لزم الأمر، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل8.](images/ef844f52ec2c0d737ce793f68b5e8408.png)

7. أضف مجموعة اختبار بالنقر فوق **تحديد المجموعات لتضمينها** واختيارها، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل9.](images/fc3525e20752da026ec9f46ab4fec64f.png)

8. راجع وقبل، ثم حدد  **إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft 10.](images/289172dbd7bd34d55d24810d9d4d8158.png)

9. يمكنك عرض النهج المكتمل.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل11.](images/5a568b6878be8243ea2b9d82d41ed297.png)

### <a name="next-generation-protection"></a>حماية الجيل التالي

1. افتح مدخل MEM.

2. انتقل إلى **برنامج الحماية من الفيروسات > Endpoint > نهج.**

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل 12.](images/6b728d6e0d71108d768e368b416ff8ba.png)

3. حدد **النظام الأساسي - Windows 10 واللاحقة - Windows وملف التعريف - برنامج الحماية من الفيروسات من Microsoft Defender > إنشاء**.

4. أدخل الاسم والوصف، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل13.](images/a7d738dd4509d65407b7d12beaa3e917.png)

5. في **صفحة إعدادات التكوين**: قم بتعيين التكوينات التي تتطلبها برنامج الحماية من الفيروسات من Microsoft Defender (الحماية السحابية والاستثناءات Real-Time الحماية والحماية وا الإصلاح).

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل14.](images/3840b1576d6f79a1d72eb14760ef5e8c.png)

6. أضف علامات النطاق إذا لزم الأمر، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل15.](images/2055e4f9b9141525c0eb681e7ba19381.png)

7. حدد المجموعات لتضمينها، ثم قم بتعيينها إلى مجموعة الاختبار، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل16.](images/48318a51adee06bff3908e8ad4944dc9.png)

8. راجع وإنشاء، ثم حدد  **إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft 17.](images/dfdadab79112d61bd3693d957084b0ec.png)

9. سترى نهج التكوين الذي أنشأته.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل18.](images/38180219e632d6e4ec7bd25a46398da8.png)

### <a name="attack-surface-reduction---attack-surface-reduction-rules"></a>تقليل مساحة الهجوم - قواعد الحد من سطح الهجوم

1. افتح مدخل MEM.

2. انتقل إلى **أمان نقطة النهاية > الحد من مساحة الهجوم**.

3. حدد  **إنشاء نهج**.

4. حدد **النظام الأساسي - Windows 10 واللاحقة - ملف التعريف -** قواعد تقليل مساحة الهجوم > إنشاء.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل19.](images/522d9bb4288dc9c1a957392b51384fdd.png)

5. أدخل اسما ووصفا، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل20.](images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png)

6. في الصفحة **إعدادات التكوين**: قم بتعيين التكوينات التي تتطلبها لقواعد تقليل مساحة الهجوم، ثم حدد  **التالي**.

    > [!NOTE]
    > سنقوم بتكوين كل قواعد تقليل مساحة الهجوم للتدقيق.
    >
    > لمزيد من المعلومات، راجع [قواعد الحد من سطح الهجوم](attack-surface-reduction.md).

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft portal21.](images/dd0c00efe615a64a4a368f54257777d0.png)

7. أضف علامات النطاق كما تقتضي الحاجة، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل22.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. حدد المجموعات لتضمينها وتعيينها إلى مجموعة اختبار، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل23.](images/45cefc8e4e474321b4d47b4626346597.png)

9. راجع التفاصيل، ثم حدد  **إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل24.](images/2c2e87c5fedc87eba17be0cdeffdb17f.png)

10. عرض النهج.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft portal25.](images/7a631d17cc42500dacad4e995823ffef.png)

### <a name="attack-surface-reduction---web-protection"></a>تقليل مساحة الهجوم - حماية الويب

1. افتح مدخل MEM.

2. انتقل إلى **أمان نقطة النهاية > الحد من مساحة الهجوم**.

3. حدد  **إنشاء نهج**.

4. حدد **Windows 10 واللاحقة - حماية > إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل26.](images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png)

5. أدخل اسما ووصفا، ثم حدد  **التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل27.](images/5be573a60cd4fa56a86a6668b62dd808.png)

6. في الصفحة **إعدادات التكوين**: قم بتعيين التكوينات التي تحتاج إليها لحماية ويب، ثم حدد  **التالي**.

    > [!NOTE]
    > نحن نعمل على تكوين حماية ويب للحظر.
    >
    > لمزيد من المعلومات، راجع [حماية الويب](web-protection-overview.md).

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل28.](images/6104aa33a56fab750cf30ecabef9f5b6.png)

7. أضف **علامات النطاق كما هو مطلوب > التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل29.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. حدد **تعيين إلى مجموعة > التالي**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل30.](images/45cefc8e4e474321b4d47b4626346597.png)

9. حدد **مراجعة وإنشاء > إنشاء**.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft portal31.](images/8ee0405f1a96c23d2eb6f737f11c1ae5.png)

10. عرض النهج.

    > [!div class="mx-imgBorder"]
    > ![صورة إدارة نقاط النهاية من Microsoft المدخل32.](images/e74f6f6c150d017a286e6ed3dffb7757.png)

## <a name="validate-configuration-settings"></a>التحقق من صحة إعدادات التكوين

### <a name="confirm-policies-have-been-applied"></a>تأكيد تطبيق سياسات

بعد تعيين نهج التكوين، سيستغرق التطبيق بعض الوقت.

للحصول على معلومات حول التوقيت، راجع [معلومات تكوين Intune](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

لتأكيد تطبيق نهج التكوين على جهاز الاختبار، اتبع العملية التالية لكل نهج تكوين.

1. افتح مدخل MEM وانتقل إلى النهج ذي الصلة كما هو موضح في الخطوات أعلاه. يوضح المثال التالي إعدادات حماية الجيل التالي.

    > [!div class="mx-imgBorder"]
    > [![صورة إدارة نقاط النهاية من Microsoft portal33.](images/43ab6aa74471ee2977e154a4a5ef2d39.png)](images/43ab6aa74471ee2977e154a4a5ef2d39.png#lightbox)

2. حدد **نهج التكوين** لعرض حالة النهج.

    > [!div class="mx-imgBorder"]
    > [![صورة إدارة نقاط النهاية من Microsoft المدخل34.](images/55ecaca0e4a022f0e29d45aeed724e6c.png)](images/55ecaca0e4a022f0e29d45aeed724e6c.png#lightbox)

3. حدد  **حالة الجهاز** لرؤية الحالة.

    > [!div class="mx-imgBorder"]
    > [![صورة إدارة نقاط النهاية من Microsoft المدخل35.](images/18a50df62cc38749000dbfb48e9a4c9b.png)](images/18a50df62cc38749000dbfb48e9a4c9b.png#lightbox)

4. حدد  **حالة المستخدم** لرؤية الحالة.

    > [!div class="mx-imgBorder"]
    > [![صورة إدارة نقاط النهاية من Microsoft المدخل36.](images/4e965749ff71178af8873bc91f9fe525.png)](images/4e965749ff71178af8873bc91f9fe525.png#lightbox)

5. حدد  **الحالة لكل إعداد** لرؤية الحالة.

    > [!TIP]
    > طريقة العرض هذه مفيدة جدا لتحديد أي إعدادات تتضارب مع نهج آخر.

    > [!div class="mx-imgBorder"]
    > [![صورة إدارة نقاط النهاية من Microsoft المدخل37.](images/42acc69d0128ed09804010bdbdf0a43c.png)](images/42acc69d0128ed09804010bdbdf0a43c.png#lightbox)

### <a name="confirm-endpoint-detection-and-response"></a>تأكيد الكشف عن تهديدات نقاط النهاية والرد عليها

1. قبل تطبيق التكوين، لا Endpoint Protection بدء خدمة Defender for Endpoint Protection.

    > [!div class="mx-imgBorder"]
    > [![صورة لوحة الخدمات1.](images/b418a232a12b3d0a65fc98248dbb0e31.png)](images/b418a232a12b3d0a65fc98248dbb0e31.png#lightbox)

2. بعد تطبيق التكوين، يجب بدء خدمة Endpoint Protection ل Defender.

    > [!div class="mx-imgBorder"]
    > [![صورة لوحة الخدمات2.](images/a621b699899f1b41db211170074ea59e.png)](images/a621b699899f1b41db211170074ea59e.png#lightbox)

3. بعد تشغيل الخدمات على الجهاز، يظهر الجهاز في Microsoft 365 Defender المدخل.

    > [!div class="mx-imgBorder"]
    > [![صورة Microsoft 365 Defender المدخل.](images/df0c64001b9219cfbd10f8f81a273190.png)](images/df0c64001b9219cfbd10f8f81a273190.png#lightbox)

### <a name="confirm-next-generation-protection"></a>تأكيد حماية الجيل التالي

1. قبل تطبيق النهج على جهاز اختبار، يجب أن تكون قادرا على إدارة الإعدادات يدويا كما هو موضح أدناه.

    > [!div class="mx-imgBorder"]
    > ![صورة إعداد page1.](images/88efb4c3710493a53f2840c3eac3e3d3.png)

2. بعد تطبيق النهج، يجب ألا تتمكن من إدارة الإعدادات يدويا.

    > [!NOTE]
    > في الصورة التالية، **يتم** عرض تشغيل الحماية التي يتم توفيرها  في السحابة و تشغيل الحماية في الوقت الحقيقي كمدارة.

    > [!div class="mx-imgBorder"]
    > ![صورة إعداد page2.](images/9341428b2d3164ca63d7d4eaa5cff642.png)

### <a name="confirm-attack-surface-reduction---attack-surface-reduction-rules"></a>تأكيد تقليل مساحة الهجوم - قواعد الحد من سطح الهجوم

1. قبل تطبيق النهج على جهاز اختبار، اكتب نافذة PowerShell وا اكتب `Get-MpPreference`.

2. يجب أن يستجيب هذا باستخدام الأسطر التالية بدون محتوى:

    > AttackSurfaceReductionOnlyExclusions:
    >
    > AttackSurfaceReductionRules_Actions:
    >
    > AttackSurfaceReductionRules_Ids:

    ![صورة سطر الأوامر 1.](images/cb0260d4b2636814e37eee427211fe71.png)

3. بعد تطبيق النهج على جهاز اختبار، افتح تطبيق PowerShell Windows وا اكتب `Get-MpPreference`.

4. يجب أن يستجيب هذا باستخدام الأسطر التالية مع المحتوى كما هو موضح أدناه:

    ![صورة سطر الأوامر2.](images/619fb877791b1fc8bc7dfae1a579043d.png)

### <a name="confirm-attack-surface-reduction---web-protection"></a>تأكيد تقليل مساحة الهجوم - حماية الويب

1. على جهاز الاختبار، افتح حساب PowerShell Windows وا اكتب `(Get-MpPreference).EnableNetworkProtection`.

2. يجب أن يستجيب هذا ب 0 كما هو موضح أدناه.

    ![صورة سطر الأوامر3.](images/196a8e194ac99d84221f405d0f684f8c.png)

3. بعد تطبيق النهج، افتح حساب PowerShell Windows وا اكتب `(Get-MpPreference).EnableNetworkProtection`.

4. يجب أن يستجيب هذا باستخدام 1 كما هو موضح أدناه.

    ![صورة سطر الأوامر 4.](images/c06fa3bbc2f70d59dfe1e106cd9a4683.png)
