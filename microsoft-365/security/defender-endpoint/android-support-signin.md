---
title: استكشاف المشكلات على Microsoft Defender لنقطة النهاية على Android وإصلاحها
description: استكشاف مشكلات Microsoft Defender لنقطة النهاية على Android وإصلاحها
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mde، android، السحابة، الاتصال، الاتصال
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
ms.openlocfilehash: 0a6f53b0723d7f3e9b4761aa83238e618d947e55
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783414"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>استكشاف المشكلات وإصلاحها على Microsoft Defender لنقطة النهاية على Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

عند إلحاق جهاز، قد ترى مشاكل في تسجيل الدخول بعد تثبيت التطبيق.

أثناء الإلحاق، قد تواجه مشاكل في تسجيل الدخول بعد تثبيت التطبيق على جهازك.

توفر هذه المقالة حلولا للمساعدة في معالجة مشاكل تسجيل الدخول.

## <a name="sign-in-failed---unexpected-error"></a>فشل تسجيل الدخول - خطأ غير متوقع

**فشل تسجيل الدخول:** *خطأ غير متوقع، حاول لاحقا*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="فشل خطأ في تسجيل الدخول، حدث خطأ غير متوقع في صفحة تسجيل الدخول إلى مدخل Microsoft Defender 365." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**رساله:**

خطأ غير متوقع، حاول لاحقا

**يسبب:**

لديك إصدار قديم من تطبيق "Microsoft Authenticator" مثبت على جهازك.

**حل:**

قم بتثبيت الإصدار الأخير [Microsoft Authenticator من متجر](https://play.google.com/store/apps/details?id=com.azure.authenticator) Google Play وحاول مرة أخرى.

## <a name="sign-in-failed---invalid-license"></a>فشل تسجيل الدخول - ترخيص غير صالح

**فشل تسجيل الدخول:** *ترخيص غير صحيح، الرجاء الاتصال بالمسؤول*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="تفاصيل جهة الاتصال للتوجيه في صفحة تسجيل الدخول لمدخل Microsoft Defender 365" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**رسالة:** *ترخيص غير صالح، الرجاء الاتصال بالمسؤول*

**يسبب:**

ليس لديك ترخيص Microsoft 365 معين، أو لا تملك مؤسستك ترخيصا لاشتراك Microsoft 365 Enterprise.

**حل:**

اتصل بالمسؤول للحصول على المساعدة.

## <a name="report-unsafe-site"></a>الإبلاغ عن موقع غير آمن

تنتحل مواقع التصيد الاحتيالي مواقع الويب الموثوق بها لغرض الحصول على معلوماتك الشخصية أو المالية. تفضل بزيارة صفحة ["تقديم ملاحظات حول حماية الشبكة](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) " إذا كنت تريد الإبلاغ عن موقع ويب قد يكون موقع تصيد احتيالي.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>لا يتم حظر صفحات التصيد الاحتيالي على بعض أجهزة الشركات المصنعة للمعدات الأصلية

**ينطبق على:** الشركات المصنعة للأجهزة الأصلية المحددة فقط

- **Xiaomi**

لا يتم حظر التصيد الاحتيالي وتهديدات الويب الضارة التي يكتشفها Defender لنقطة النهاية ل Android على بعض أجهزة Xiaomi. لا تعمل الوظائف التالية على هذه الأجهزة.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="رسالة إعلام غير آمنة للموقع" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**يسبب:**

تتضمن أجهزة Xiaomi نموذجا جديدا للأذونات. يمنع هذا Defender لنقطة النهاية لنظام التشغيل Android من عرض النوافذ المنبثقة أثناء تشغيله في الخلفية.

إذن أجهزة Xiaomi: "عرض النوافذ المنبثقة أثناء التشغيل في الخلفية."

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="جزء الإعدادات المنبثقة في مدخل Microsoft Defender 365" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**حل:**

تمكين الإذن المطلوب على أجهزة Xiaomi.

- عرض النوافذ المنبثقة أثناء التشغيل في الخلفية.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>تعذر السماح بإذن "الحماية الدائمة" أثناء الإلحاق على بعض أجهزة الشركة المصنعة للمعدات الأصلية

**ينطبق على:** أجهزة معينة من الشركات المصنعة للمعدات الأصلية فقط.

- **Xiaomi مع Android 11**

يطلب Defender App إذن تحسين البطارية/الحماية الدائمة على الأجهزة كجزء من إلحاق التطبيق، ويرجع تحديد **السماح** خطأ تعذر تعيين الإذن. يؤثر فقط على الإذن الأخير المسمى "الحماية الدائمة". 

**يسبب:**

غير Xiaomi أذونات تحسين البطارية في Android 11. لا يسمح ل Defender لنقطة النهاية بتكوين هذا الإعداد لتجاهل تحسينات البطارية.

**حل:**

نحن نعمل مع الشركة المصنعة للمعدات الأصلية للعثور على حل لتمكين هذا الإذن من شاشة إلحاق التطبيق. سنقوم بتحديث الوثائق عند حل هذه المشكلة.
يمكن للمستخدمين اتباع هذه الخطوات لتمكين نفس الأذونات من إعدادات الجهاز: 

1. انتقل إلى **الإعدادات** على جهازك.

2. ابحث عن **تحسين طاقة البطارية وحدده**.

   :::image type="content" source="images/search-battery-optimisation.png" alt-text="الصفحة التي يمكنك البحث فيها وتحديد &quot;تحسين طاقة البطارية&quot;" lightbox="images/search-battery-optimisation.png":::

3. في **الوصول إلى تطبيق خاص**، حدد **تحسين طاقة البطارية**.

   :::image type="content" source="images/special-app-access.png" alt-text="جزء الوصول إلى التطبيق الخاص الذي يمكنك من خلاله تحديد &quot;تحسين طاقة البطارية&quot;" lightbox="images/special-app-access.png":::

4. قم بتغيير القائمة المنسدلة لإظهار **كافة التطبيقات**.

   :::image type="content" source="images/show-all-apps-2.png" alt-text="القائمة المنسدلة التي يمكنك من خلالها تغيير القيمة إلى جميع التطبيقات ضمن جزء تحسين البطارية" lightbox="images/show-all-apps-2.png":::

   :::image type="content" source="images/show-all-apps-1.png" alt-text="القائمة المنسدلة التي تعرض خيار &quot;جميع التطبيقات&quot; ضمن جزء &quot;تحسين البطارية&quot;" lightbox="images/show-all-apps-1.png":::

5. حدد موقع "Microsoft Defender لنقطة النهاية" وحدد **"عدم التحسين**".

   :::image type="content" source="images/select-dont-optimise.png" alt-text="الصفحة التي تمكن موقع الخيار Microsoft Defender لنقطة النهاية وتحديد &quot;عدم التحسين&quot;" lightbox="images/select-dont-optimise.png":::

ارجع إلى شاشة Microsoft Defender لنقطة النهاية الإلحاق، وحدد **"السماح**"، وسيتم إعادة توجيهك إلى شاشة لوحة المعلومات.

## <a name="send-in-app-feedback"></a>إرسال ملاحظات داخل التطبيق

إذا واجه مستخدم مشكلة لم تتم معالجتها بالفعل في الأقسام أعلاه أو تعذر عليه حلها باستخدام الخطوات المدرجة، يمكن للمستخدم تقديم **ملاحظات داخل التطبيق** إلى جانب **البيانات التشخيصية**. يمكن لفريقنا بعد ذلك التحقق من السجلات لتوفير الحل الصحيح. يمكن للمستخدمين اتباع هذه الخطوات للقيام بنفس الشيء:

1. افتح **تطبيق MDE** على جهازك وانقر فوق **أيقونة ملف التعريف** في الزاوية العلوية اليمنى.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="أيقونة ملف التعريف في مدخل Microsoft Defender لنقطة النهاية" lightbox="images/select-profile-icon-1.jpg":::

2. حدد "تعليمات & الملاحظات".

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="الخيار &quot;تعليمات & الملاحظات&quot; الذي يمكن تحديده في مدخل Microsoft Defender لنقطة النهاية" lightbox="images/selecthelpandfeedback2.png":::

3. حدد "إرسال ملاحظات إلى Microsoft".

    :::image type="content" alt-text="تحديد إرسال ملاحظات إلى Microsoft" source="images/send-feedback-to-microsoft-3.jpg":::

4. اختر من الخيارات المحددة. للإبلاغ عن مشكلة، حدد "أريد الإبلاغ عن مشكلة".

    :::image type="content" source="images/report-issue-4.jpg" alt-text="الخيار &quot;أريد الإبلاغ عن مشكلة&quot;" lightbox="images/report-issue-4.jpg":::

5. قم بتوفير تفاصيل المشكلة التي تواجهها وتحقق من "إرسال البيانات التشخيصية". نوصي بالتحقق من "تضمين عنوان بريدك الإلكتروني" حتى يتمكن الفريق من الوصول إليك مرة أخرى باستخدام حل أو متابعة.

    :::image type="content" source="images/finalsubmit5.png" alt-text="الجزء الذي يمكنك فيه إضافة التفاصيل وإرفاق البيانات التشخيصية" lightbox="images/finalsubmit5.png":::

6. انقر فوق "إرسال" لإرسال الملاحظات بنجاح.

