---
title: النشر اليدوي Microsoft Defender لنقطة النهاية على macOS
description: قم بتثبيت Microsoft Defender لنقطة النهاية على macOS يدويا، من سطر الأوامر.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، التوزيع، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 68f91e4b8f789087aacea14b6b2a8a8b67262fd0
ms.sourcegitcommit: b0b1be67de8f40b199bb9b51eb3568e59377e93a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/18/2022
ms.locfileid: "66159608"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>النشر اليدوي Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

يصف هذا الموضوع كيفية نشر Microsoft Defender لنقطة النهاية على macOS يدويا. يتطلب النشر الناجح إكمال جميع الخطوات التالية:

- [تنزيل حزم التثبيت والإلحاق](#download-installation-and-onboarding-packages)
- [تثبيت التطبيق (macOS 10.15)](#application-installation-macos-1015)
- [تثبيت التطبيق (macOS 11 والإصدارات الأحدث)](#application-installation-macos-11-and-newer-versions)
- [تكوين العميل](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع [Microsoft Defender لنقطة النهاية الرئيسية على صفحة macOS للحصول على](microsoft-defender-endpoint-mac.md) وصف للمتطلبات الأساسية ومتطلبات النظام لإصدار البرنامج الحالي.

## <a name="download-installation-and-onboarding-packages"></a>تنزيل حزم التثبيت والإلحاق

قم بتنزيل حزم التثبيت والإلحاق من مدخل Microsoft 365 Defender:

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">مدخل Microsoft 365 Defender</a>، انتقل إلى **نقاط النهاية الإعدادات > > إدارة الأجهزة > الإلحاق**.
2. في القسم 1 من الصفحة، قم بتعيين نظام التشغيل إلى **macOS** وطريقة النشر إلى **البرنامج النصي المحلي**.
3. في القسم 2 من الصفحة، حدد **تنزيل حزمة التثبيت**. احفظه ك wdav.pkg إلى دليل محلي.
4. في القسم 2 من الصفحة، حدد **"تنزيل حزمة الإلحاق**". احفظه WindowsDefenderATPOnboardingPackage.zip إلى الدليل نفسه.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="خيارات تنزيل حزم التثبيت والإلحاق" lightbox="images/portal-onboarding-macos.png":::

5. من موجه الأوامر، تحقق من أن لديك الملفين.

## <a name="application-installation-macos-1015"></a>تثبيت التطبيق (macOS 10.15)

لإكمال هذه العملية، يجب أن يكون لديك امتيازات المسؤول على الجهاز.

1. انتقل إلى wdav.pkg الذي تم تنزيله في "الباحث" وافتحه.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="تثبيت التطبيق" lightbox="images/mdatp-28-appinstall.png":::

2. حدد **"متابعة**"، وتوافق على شروط الترخيص، وأدخل كلمة المرور عند المطالبة.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="تثبيت التطبيق" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > ستتم مطالبتك بالسماح بتثبيت برنامج تشغيل من Microsoft (إما "تم حظر ملحق النظام" أو "التثبيت قيد الانتظار" أو كليهما. يجب السماح بتثبيت برنامج التشغيل.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="تثبيت التطبيق" lightbox="images/mdatp-30-systemextension.png":::

3. حدد **Open Security Preferences** أو **Open System Preferences > Security & Privacy**. حدد **السماح**:

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="نافذة الأمان والخصوصية" lightbox="images/mdatp-31-securityprivacysettings.png":::

   تتم متابعة التثبيت.

   > [!CAUTION]
   > إذا لم تحدد **"السماح**"، فسيتابع التثبيت بعد 5 دقائق. سيتم تحميل Microsoft Defender لنقطة النهاية، ولكن سيتم تعطيل بعض الميزات، مثل الحماية في الوقت الحقيقي. راجع [استكشاف مشكلات ملحق kernel وإصلاحها](mac-support-kext.md) للحصول على معلومات حول كيفية حل هذه المشكلة.

> [!NOTE]
> قد يطلب macOS إعادة تشغيل الجهاز عند التثبيت الأول Microsoft Defender لنقطة النهاية. لن تتوفر الحماية في الوقت الحقيقي حتى تتم إعادة تشغيل الجهاز.

## <a name="application-installation-macos-11-and-newer-versions"></a>تثبيت التطبيق (macOS 11 والإصدارات الأحدث)

لإكمال هذه العملية، يجب أن يكون لديك امتيازات المسؤول على الجهاز.

1. انتقل إلى wdav.pkg الذي تم تنزيله في "الباحث" وافتحه.

   :::image type="content" source="images/monterey-install-1.png" alt-text="عملية التثبيت للتطبيق" lightbox="images/monterey-install-1.png":::

2. حدد **"متابعة**"، وتوافق على شروط الترخيص، وأدخل كلمة المرور عند المطالبة.

3. في نهاية عملية التثبيت، ستتم ترقيته للموافقة على ملحقات النظام المستخدمة من قبل المنتج. حدد **تفضيلات الأمان المفتوحة**.

   :::image type="content" source="images/monterey-install-2.png" alt-text="الموافقة على ملحق النظام" lightbox="images/monterey-install-2.png":::

4. من نافذة **الخصوصية & الأمان** ، حدد **"السماح**".

   :::image type="content" source="images/monterey-install-3.png" alt-text="تفضيلات أمان ملحق النظام1" lightbox="images/monterey-install-3.png":::

5. كرر الخطوات 3 & 4 لجميع ملحقات النظام الموزعة باستخدام Microsoft Defender لنقطة النهاية على Mac.

6. كجزء من قدرات الكشف عن نقطة النهاية والاستجابة لها، يفحص Microsoft Defender لنقطة النهاية على Mac نسبة استخدام الشبكة للمأخذ ويبلغ عن هذه المعلومات إلى مدخل Microsoft 365 Defender. عند مطالبتك بمنح أذونات Microsoft Defender لنقطة النهاية لتصفية نسبة استخدام الشبكة، حدد **"السماح**".

   :::image type="content" source="images/monterey-install-4.png" alt-text="تفضيلات أمان ملحق النظام2" lightbox="images/monterey-install-4.png":::

7. افتح أمان **تفضيلات** \> النظام **& الخصوصية** وانتقل إلى علامة التبويب **"الخصوصية** ". امنح إذن **الوصول إلى القرص الكامل** إلى **Microsoft Defender** **وMicrosoft Defenders Endpoint Security Extension**.

   :::image type="content" source="images/monterey-install-5.png" alt-text="الوصول الكامل إلى القرص" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>تكوين العميل

1. انسخ wdav.pkg MicrosoftDefenderATPOnboardingMacOs.sh إلى الجهاز حيث تقوم بنشر Microsoft Defender لنقطة النهاية على macOS.

    جهاز العميل غير مقترن org_id. لاحظ أن السمة *org_id* فارغة.

    ```bash
    mdatp health --field org_id
    ```

2. تشغيل البرنامج النصي Bash لتثبيت ملف التكوين:

    ```bash
    Sudo bash -x MicrosoftDefenderATPOnboardingMacOs.sh
    ```

3. تحقق من أن الجهاز الآن مقترن بمؤسستك ويبلغ عن معرف مؤسسة صالح:

    ```bash
    mdatp health --field org_id
    ```

    بعد التثبيت، سترى أيقونة Microsoft Defender في شريط المعلومات macOS في الزاوية العلوية اليسرى.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="أيقونة Microsoft Defender في شريط المعلومات" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>كيفية السماح بالوصول الكامل إلى القرص

> [!CAUTION]
> يحتوي macOS 10.15 (Catalina) على تحسينات أمان وخصوصية جديدة. بدءا من هذا الإصدار، بشكل افتراضي، لا يمكن للتطبيقات الوصول إلى مواقع معينة على القرص (مثل المستندات والتنزيلات وسطح المكتب وما إلى ذلك) دون موافقة صريحة. في حالة عدم وجود هذه الموافقة، لن يتمكن Microsoft Defender لنقطة النهاية من حماية جهازك بشكل كامل.

1. لمنح الموافقة، افتح **أمان تفضيلات** \> النظام & **الوصول إلى القرص الكامل** **لخصوصية الخصوصية** \>  \>. انقر فوق أيقونة التأمين لإجراء تغييرات (أسفل مربع الحوار). حدد Microsoft Defender لنقطة النهاية.

2. قم بتشغيل اختبار الكشف عن AV للتحقق من أن الجهاز تم إلحاقه بشكل صحيح وإعداد التقارير إلى الخدمة. نفذ الخطوات التالية على الجهاز الذي تم إلحاقه حديثا:

    1. تأكد من تمكين الحماية في الوقت الحقيقي (يشار إليها بنتيجة 1 من تشغيل الأمر التالي):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. افتح نافذة Terminal. انسخ الأمر التالي ونفذه:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. يجب أن يكون الملف قد تم عزله بواسطة Defender لنقطة النهاية على Mac. استخدم الأمر التالي لإدراج كافة التهديدات المكتشفة:

        ```bash
        mdatp threat list
        ```

3. قم بتشغيل اختبار الكشف عن الكشف التلقائي والاستجابة على النقط النهائية للتحقق من أن الجهاز تم إلحاقه بشكل صحيح وإعداد التقارير إلى الخدمة. نفذ الخطوات التالية على الجهاز الذي تم إلحاقه حديثا:

   1. في المستعرض مثل Microsoft Edge for Mac أو Safari.

   1. قم بتنزيل DIY.zip MDATP MacOS واستخراجها https://aka.ms/mdatpmacosdiy .

      قد تتم مطالبتك:

      > هل تريد السماح بالتنزيلات على "mdatpclientanalyzer.blob.core.windows.net"؟<br/>
      > يمكنك تغيير مواقع الويب التي يمكنها تنزيل الملفات في تفضيلات مواقع الويب.

4. انقر فوق **"السماح**".

5. افتح **التنزيلات**.

6. يجب أن تشاهد **MDATP MacOS DIY**.

   > [!TIP]
   > إذا نقرت نقرا مزدوجا، فستتلقى الرسالة التالية:
   >
   > > **يتعذر فتح "MDATP MacOS DIY" لأنه لا يمكن أن يكون المطور مدققا.**<br/>
   > > لا يمكن macOS التحقق من أن هذا التطبيق خال من البرامج الضارة.<br/>
   > > **\[الانتقال إلى إلغاء سلة المهملات\]** **\[\]**

7. انقر فوق **إلغاء**.

8. انقر بزر الماوس الأيمن فوق **MDATP MacOS DIY**، ثم انقر فوق **"فتح**".

    يجب أن يعرض النظام الرسالة التالية:

    > **يتعذر على macOS التحقق من مطور MDATP MacOS DIY. هل تريد بالتأكيد فتحه؟**<br/>
    > من خلال فتح هذا التطبيق، سيتم تجاوز أمان النظام الذي يمكن أن يعرض الكمبيوتر والمعلومات الشخصية للبرامج الضارة التي قد تلحق الضرر بجهاز Mac أو تعرض خصوصيتك للخطر.

9. انقر فوق **"فتح**".

    يجب أن يعرض النظام الرسالة التالية:

    > Microsoft Defender لنقطة النهاية - ملف اختبار MACOS الكشف التلقائي والاستجابة على النقط النهائية DIY<br/>
    > سيتوفر التنبيه المقابل في مدخل MDATP.

10. انقر فوق **"فتح**".

    في غضون دقائق قليلة، يجب رفع تنبيه باسم "macOS الكشف التلقائي والاستجابة على النقط النهائية Test Alert".

11. انتقل إلى مدخل Microsoft 365 Defender (https://security.microsoft.com/).

12. انتقل إلى قائمة انتظار التنبيه.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="تنبيه اختبار macOS الكشف التلقائي والاستجابة على النقط النهائية يظهر الخطورة والفئة ومصدر الكشف وقائمة مطوية من الإجراءات" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    انظر إلى تفاصيل التنبيه والمخطط الزمني للجهاز، وقم بتنفيذ خطوات التحقيق العادية.

## <a name="logging-installation-issues"></a>مشاكل تثبيت التسجيل

راجع [مشاكل تثبيت التسجيل](mac-resources.md#logging-installation-issues) للحصول على مزيد من المعلومات حول كيفية العثور على السجل الذي تم إنشاؤه تلقائيا بواسطة المثبت عند حدوث خطأ.

## <a name="uninstallation"></a>الغاء التثبيت

راجع [إلغاء التثبيت](mac-resources.md#uninstalling) للحصول على تفاصيل حول كيفية إزالة Microsoft Defender لنقطة النهاية على macOS من أجهزة العميل.
