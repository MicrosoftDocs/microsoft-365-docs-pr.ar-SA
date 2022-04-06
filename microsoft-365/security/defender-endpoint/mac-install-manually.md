---
title: النشر اليدوي Microsoft Defender لنقطة النهاية macOS
description: ثبت Microsoft Defender لنقطة النهاية على macOS يدويا، من سطر الأوامر.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamf، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: 7793a367b591490f3b70055bc5b437eec798cb28
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475972"
---
# <a name="manual-deployment-for-microsoft-defender-for-endpoint-on-macos"></a>النشر اليدوي Microsoft Defender لنقطة النهاية macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink).

يصف هذا الموضوع كيفية نشر Microsoft Defender لنقطة النهاية على macOS يدويا. يتطلب النشر الناجح إكمال كل الخطوات التالية:

- [تنزيل حزم التثبيت والتركيب](#download-installation-and-onboarding-packages)
- [تثبيت التطبيق (macOS 10.15)](#application-installation-macos-1015)
- [تثبيت التطبيق (macOS 11 والإصدارات الأحدث)](#application-installation-macos-11-and-newer-versions)
- [تكوين العميل](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>المتطلبات الأساسية ومتطلبات النظام

قبل البدء، راجع الصفحة الرئيسية Microsoft Defender لنقطة النهاية [macOS](microsoft-defender-endpoint-mac.md) للحصول على وصف للمتطلبات الأساسية ومتطلبات النظام الخاصة بالإصدار الحالي للبرنامج.

## <a name="download-installation-and-onboarding-packages"></a>تنزيل حزم التثبيت والتركيب

قم بتنزيل حزم التثبيت والتركيب من Microsoft 365 Defender:

1. في <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender،</a> انتقل إلى الإعدادات > نقاط النهاية > إدارة الأجهزة > **التكوين**.
2. في القسم 1 من الصفحة، قم بتعيين نظام التشغيل إلى **macOS** وطريقة النشر إلى **برنامج نصي محلي**.
3. في القسم 2 من الصفحة، حدد **تنزيل حزمة التثبيت**. احفظه ك wdav.pkg في دليل محلي.
4. في القسم 2 من الصفحة، حدد **تنزيل حزمة الboarding**. احفظه WindowsDefenderATPOnboardingPackage.zip إلى الدليل نفسه.

   :::image type="content" source="images/portal-onboarding-macos.png" alt-text="خيارات تنزيل حزم التثبيت والتركيب" lightbox="images/portal-onboarding-macos.png":::

5. من موجه الأوامر، تحقق من أن لديك الملفين.

## <a name="application-installation-macos-1015"></a>تثبيت التطبيق (macOS 10.15)

لإكمال هذه العملية، يجب أن يكون لديك امتيازات المسؤول على الجهاز.

1. انتقل إلى wdav.pkg الذي تم تنزيله في "البحث" وافتحه.

   :::image type="content" source="images/mdatp-28-appinstall.png" alt-text="تثبيت التطبيق" lightbox="images/mdatp-28-appinstall.png":::

2. حدد **متابعة**، ووافق على شروط الترخيص، وأدخل كلمة المرور عند مطالبتك بذلك.

   :::image type="content" source="images/mdatp-29-appinstalllogin.png" alt-text="تثبيت التطبيق" lightbox="images/mdatp-29-appinstalllogin.png":::

   > [!IMPORTANT]
   > وستتم مطالبتك بالسماح بتثبيت برنامج تشغيل من Microsoft (إما "تم حظر ملحق النظام" أو "التثبيت مع الانتظار" أو كليهما. يجب السماح بتثبيت برنامج التشغيل.

     :::image type="content" source="images/mdatp-30-systemextension.png" alt-text="تثبيت التطبيق" lightbox="images/mdatp-30-systemextension.png":::

3. حدد **فتح تفضيلات الأمان** أو **فتح تفضيلات النظام > تفضيلات & الخصوصية**. حدد **السماح**:

   :::image type="content" source="images/mdatp-31-securityprivacysettings.png" alt-text="نافذة الأمان والخصوصية" lightbox="images/mdatp-31-securityprivacysettings.png":::

   يتم متابعة التثبيت.

   > [!CAUTION]
   > إذا لم **تحدد السماح،** سيتابع التثبيت بعد 5 دقائق. Microsoft Defender لنقطة النهاية، ولكن سيتم تعطيل بعض الميزات، مثل الحماية في الوقت الحقيقي. راجع [استكشاف مشاكل ملحقات kernel](mac-support-kext.md) وإصلاحها للحصول على معلومات حول كيفية حل هذه المشكلة.

> [!NOTE]
> قد يطلب macOS إعادة تشغيل الجهاز عند التثبيت الأول Microsoft Defender لنقطة النهاية. لن تتوفر الحماية في الوقت الحقيقي حتى يتم إعادة تشغيل الجهاز.

## <a name="application-installation-macos-11-and-newer-versions"></a>تثبيت التطبيق (macOS 11 والإصدارات الأحدث)

لإكمال هذه العملية، يجب أن يكون لديك امتيازات المسؤول على الجهاز.

1. انتقل إلى wdav.pkg الذي تم تنزيله في "البحث" وافتحه.

   :::image type="content" source="images/monterey-install-1.png" alt-text="عملية تثبيت التطبيق" lightbox="images/monterey-install-1.png":::

2. حدد **متابعة**، ووافق على شروط الترخيص، وأدخل كلمة المرور عند مطالبتك بذلك.

3. في نهاية عملية التثبيت، سيتم ترقية للموافقة على ملحقات النظام التي يستخدمها المنتج. حدد **فتح تفضيلات الأمان**.

   :::image type="content" source="images/monterey-install-2.png" alt-text="الموافقة على ملحق النظام" lightbox="images/monterey-install-2.png":::

4. من نافذة **الأمان & الخصوصية** ، حدد **السماح**.

   :::image type="content" source="images/monterey-install-3.png" alt-text="تفضيلات أمان ملحق النظام1" lightbox="images/monterey-install-3.png":::

5. كرر الخطوات 3 & 4 لكل ملحقات النظام الموزعة مع Microsoft Defender لنقطة النهاية Mac.

6. كجزء من قدرات الكشف عن نقاط النهاية والاستجابة، يفحص Microsoft Defender لنقطة النهاية Mac حركة مرور مآخذ التوصيل ويعيد الإبلاغ عن هذه المعلومات Microsoft 365 Defender المدخل. عند مطالبتك بمنح Microsoft Defender لنقطة النهاية لتصفية حركة مرور الشبكة، حدد **السماح**.

   :::image type="content" source="images/monterey-install-4.png" alt-text="تفضيلات أمان ملحق النظام2" lightbox="images/monterey-install-4.png":::

7. افتح **أمان تفضيلات** \> **النظام & الخصوصية** وانتقل إلى علامة التبويب الخصوصية. امنح إذن الوصول الكامل  إلى **Microsoft Defender** وملحق **أمان نقطة نهاية Microsoft Defender.**

   :::image type="content" source="images/monterey-install-5.png" alt-text="الوصول إلى القرص الكامل" lightbox="images/monterey-install-5.png":::

## <a name="client-configuration"></a>تكوين العميل

1. انسخ wdav.pkg MicrosoftDefenderATPOnboardingMacOs.py إلى الجهاز حيث يمكنك نشر Microsoft Defender لنقطة النهاية macOS.

    جهاز العميل غير مقترن ب org_id. لاحظ *أن org_id فارغة* .

    ```bash
    mdatp health --field org_id
    ```

2. قم بتشغيل البرنامج النصي Python لتثبيت ملف التكوين:

    ```bash
    /usr/bin/python MicrosoftDefenderATPOnboardingMacOs.py
    ```

3. تحقق من أن الجهاز الآن مقترن بمنظمتك ويلتقارير عن هوية مؤسسة صالحة:

    ```bash
    mdatp health --field org_id
    ```

    بعد التثبيت، سترى أيقونة Microsoft Defender في شريط حالة macOS في الزاوية العلوية اليسرى.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mdatp-icon-bar.png" alt-text="أيقونة Microsoft Defender في شريط الحالة" lightbox="images/mdatp-icon-bar.png":::

## <a name="how-to-allow-full-disk-access"></a>كيفية السماح بالوصول إلى القرص الكامل

> [!CAUTION]
> يحتوي macOS 10.15 (Catalina) على تحسينات جديدة على الأمان والخصوصية. بدءا من هذا الإصدار، بشكل افتراضي، لن تتمكن التطبيقات من الوصول إلى مواقع معينة على القرص (مثل المستندات أو التنزيلات أو سطح المكتب وغير ذلك) بدون موافقة صريحة. في حالة عدم وجود هذه الموافقة، Microsoft Defender لنقطة النهاية غير قادر على حماية جهازك بشكل كامل.

1. لمنح الموافقة، افتح **أمان تفضيلات** \> **النظام** & **الوصول إلى الخصوصية** \> \> **في القرص الكامل**. انقر فوق أيقونة التأمين بإجراء تغييرات (أسفل مربع الحوار). حدد Microsoft Defender لنقطة النهاية.

2. يمكنك تشغيل اختبار الكشف عن AV للتحقق من أن الجهاز مدرج بشكل صحيح ويبل ى الخدمة. تنفيذ الخطوات التالية على الجهاز المعين حديثا:

    1. تأكد من تمكين الحماية في الوقت الحقيقي (تشير النتيجة إلى 1 من تشغيل الأمر التالي):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```

    1. فتح نافذة المحطة الطرفية. نسخ الأمر التالي وتنفيذه:

        ```bash
        curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    1. يجب أن يكون الملف معزولا بواسطة Defender for Endpoint على Mac. استخدم الأمر التالي لتضمين جميع التهديدات التي تم الكشف عنها:

        ```bash
        mdatp threat list
        ```

3. يمكنك تشغيل الكشف التلقائي والاستجابة على النقط النهائية الكشف للتحقق من أن الجهاز مدرج بشكل صحيح ويبل ى الخدمة. تنفيذ الخطوات التالية على الجهاز المعين حديثا:

   1. في المستعرض الخاص بك مثل Microsoft Edge for Mac أو Safari.

   1. قم بتنزيل MDATP MacOS DIY.zip منه واستخراجه https://aka.ms/mdatpmacosdiy .

      قد يتم مطالبتك:

      > هل تريد السماح بتنزيلها على "mdatpclientanalyzer.blob.core.windows.net"؟<br/>
      > يمكنك تغيير مواقع الويب التي يمكنها تنزيل الملفات في تفضيلات مواقع الويب.

4. انقر **فوق السماح**.

5. افتح **التنزيلات**.

6. من المفترض أن ترى **MDATP MacOS DIY**.

   > [!TIP]
   > إذا نقرت نقرا مزدوجا، ستصلك الرسالة التالية:
   >
   > > **لا يمكن فتح "MDATP MacOS DIY" لأنه يتعذر على المطور التحقق.**<br/>
   > > يتعذر على macOS التحقق من أن هذا التطبيق خالي من البرامج الضارة.<br/>
   > > **\[الانتقال إلى إلغاء سلة المهملات\]** **\[\]**

7. انقر فوق **إلغاء**.

8. انقر بضغطة **زر الماوس الأيمن فوق MDATP MacOS DIY**، ثم انقر فوق **فتح**.

    يجب أن يعرض النظام الرسالة التالية:

    > **يتعذر على macOS التحقق من مطور MDATP MacOS DIY. هل تريد بالتأكيد فتحه؟**<br/>
    > عند فتح هذا التطبيق، سيتم تجاوز أمان النظام الذي يمكن أن يعرض الكمبيوتر والمعلومات الشخصية للبرامج الضارة التي قد تؤذي جهاز Mac أو تعرض خصوصيتك للخطر.

9. انقر **فوق فتح**.

    يجب أن يعرض النظام الرسالة التالية:

    > Microsoft Defender لنقطة النهاية - macOS الكشف التلقائي والاستجابة على النقط النهائية DIY<br/>
    > سيتوفر التنبيه المقابل في مدخل MDATP.

10. انقر **فوق فتح**.

    في غضون دقائق قليلة، يجب رفع تنبيه باسم "macOS الكشف التلقائي والاستجابة على النقط النهائية الاختبار".

11. انتقل إلى Microsoft 365 Defender المدخل (https://security.microsoft.com/).

12. انتقل إلى قائمة انتظار التنبيهات.

    :::image type="content" source="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png" alt-text="تنبيه اختباري الكشف التلقائي والاستجابة على النقط النهائية macOS يعرض الخطورة والفئة ومصدر الكشف وقائمة م طي الإجراءات" lightbox="images/b8db76c2-c368-49ad-970f-dcb87534d9be.png":::

    أطلع على تفاصيل التنبيه والميول الزمنية للجهاز، وانجز خطوات التحقيق العادية.

## <a name="logging-installation-issues"></a>مشاكل تثبيت التسجيل

راجع [تسجيل مشاكل التثبيت](mac-resources.md#logging-installation-issues) للحصول على مزيد من المعلومات حول كيفية البحث عن السجل الذي تم إنشاؤه تلقائيا الذي أنشأه المثبت عند حدوث خطأ.

## <a name="uninstallation"></a>إلغاء التثبيت

راجع [إلغاء تثبيت للحصول](mac-resources.md#uninstalling) على تفاصيل حول كيفية إزالة Microsoft Defender لنقطة النهاية على macOS من الأجهزة العميلة.
