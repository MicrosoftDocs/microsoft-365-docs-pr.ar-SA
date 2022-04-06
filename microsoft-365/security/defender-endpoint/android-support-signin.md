---
title: استكشاف الأخطاء وإصلاحها على Microsoft Defender لنقطة النهاية على نظام التشغيل Android
description: استكشاف المشاكل وإصلاحها ل Microsoft Defender لنقطة النهاية على نظام التشغيل Android
keywords: microsoft، defender، Microsoft Defender ل Endpoint، mde، android، السحابة، الاتصال، الاتصال
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
ms.openlocfilehash: 9d08994d0a69ba1985e69845b3a22abd40c753fd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63583129"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>استكشاف الأخطاء وإصلاحها على Microsoft Defender لنقطة النهاية على نظام التشغيل Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

عند تشغيل جهاز، قد ترى مشاكل تسجيل الدخول بعد تثبيت التطبيق.

أثناء التركيب، قد تواجه مشاكل في تسجيل الدخول بعد تثبيت التطبيق على جهازك.

توفر هذه المقالة حلولا للمساعدة في معالجة مشاكل تسجيل الدخول.

## <a name="sign-in-failed---unexpected-error"></a>فشل تسجيل الدخول - خطأ غير متوقع

**فشل تسجيل الدخول:** *خطأ غير متوقع، حاول لاحقا*

:::image type="content" alt-text="صورة لخطأ فشل تسجيل الدخول خطأ غير متوقع." source="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**الرسالة:**

خطأ غير متوقع، حاول لاحقا

**السبب:**

لديك إصدار قديم من تطبيق "Microsoft Authenticator" مثبت على جهازك.

**الحل:**

قم بتثبيت أحدث [إصدار Microsoft Authenticator من](https://play.google.com/store/apps/details?id=com.azure.authenticator) متجر Google Play وحاول مرة أخرى.

## <a name="sign-in-failed---invalid-license"></a>فشل تسجيل الدخول - ترخيص غير صالح

**فشل تسجيل الدخول:** *ترخيص غير صالح، يرجى الاتصال بالمسؤول*

:::image type="content" alt-text="صورة فشل تسجيل الدخول يرجى الاتصال بالمسؤول." source="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**رسالة:** *ترخيص غير صالح، يرجى الاتصال بالمسؤول*

**السبب:**

ليس لديك Microsoft 365 تعيين ترخيص، أو لا تملك مؤسستك ترخيصا للاشتراك Microsoft 365 Enterprise الاشتراك.

**الحل:**

اتصل بالمسؤول للحصول على المساعدة.

## <a name="report-unsafe-site"></a>الإبلاغ عن موقع غير آمن

تقوم مواقع التصيد الاحتيالي على الويب بانتحال مواقع الويب الموثوق بها بغرض الحصول على معلوماتك الشخصية أو المالية. تفضل بزيارة [صفحة تقديم ملاحظات](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) حول حماية الشبكة إذا كنت تريد الإبلاغ عن موقع ويب قد يكون موقع تصيد احتيالي.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>لا يتم حظر صفحات التصيد الاحتيالي على بعض أجهزة OEM

**ينطبق على:** OEMs محددة فقط

- **Xiaomi**

لا يتم حظر التصيد الاحتيالي وتهديدات الويب الضارة التي يكشف عنها Defender for Endpoint for Android على بعض أجهزة Xiaomi. لا تعمل الوظائف التالية على هذه الأجهزة.

![صورة موقع تم إعلامه بأنه غير آمن.](images/0c04975c74746a5cdb085e1d9386e713.png)

**السبب:**

تتضمن أجهزة Xiaomi نموذج أذونات جديد. يمنع ذلك Defender for Endpoint for Android من عرض النوافذ المنبثقة أثناء تشغيله في الخلفية.

إذن أجهزة Xiaomi: "عرض النوافذ المنبثقة أثناء التشغيل في الخلفية".

![صورة لإعداد منبثق.](images/6e48e7b29daf50afddcc6c8c7d59fd64.png)

**الحل:**

تمكين الإذن المطلوب على أجهزة Xiaomi.

- عرض النوافذ المنبثقة أثناء التشغيل في الخلفية.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>تعذر السماح بإذن "الحماية الدائمة" أثناء التكائم على بعض أجهزة OEM

**ينطبق على:** أجهزة معينة خاصة ب OEM فقط.

- **Xiaomi مع Android 11**

يطلب تطبيق Defender إذن تحسين البطارية/الحماية الدائمة على الأجهزة كجزء من تهيئة التطبيق، ويرجع تحديد السماح خطأ بأنه لا  يمكن تعيين الإذن. يؤثر ذلك فقط على الإذن الأخير المسمى "الحماية الدائمة". 

**السبب:**

غيرت Xiaomi أذونات تحسين البطارية في Android 11. لا يسمح ل Defender for Endpoint بتكوين هذا الإعداد لتجاهل تحسينات البطارية.

**الحل:**

نحن نعمل مع OEM للعثور على حل لتمكين هذا الإذن من شاشة تشغيل التطبيق. سنقوم بتحديث الوثائق عند حل هذه المشكلة.
يمكن للمستخدمين اتباع هذه الخطوات لتمكين الأذونات نفسها من إعدادات الجهاز: 

1. انتقل إلى **الإعدادات** على جهازك.

2. ابحث عن تحسين **البطارية وحدده**.

   ![ابحث عن "تحسين طاقة البطارية" وحدده.](images/search-battery-optimisation.png)

3. في **الوصول إلى التطبيق الخاص**، حدد **تحسين البطارية**.

   ![في الوصول إلى التطبيق الخاص، حدد "تحسين طاقة البطارية".](images/special-app-access.png)

4. غير "المنسدلة" لإظهار **جميع التطبيقات**.

   ![الخطوة الأولى لتغيير المنسدلة لإظهار "جميع التطبيقات".](images/show-all-apps-2.png)

   ![الخطوة الثانية لتغيير المنسدلة لإظهار "جميع التطبيقات".](images/show-all-apps-1.png)

5. حدد موقع "Microsoft Defender لنقطة النهاية" وحدد **عدم التحسين**.

   ![حدد موقع "Microsoft Defender لنقطة النهاية" وحدد "عدم التحسين".](images/select-dont-optimise.png)

ارجع إلى شاشة تعيين نقطة النهاية ل Microsoft Defender، وحدد السماح، وستعاد توجيهك إلى شاشة لوحة المعلومات.

## <a name="send-in-app-feedback"></a>إرسال ملاحظات داخل التطبيق

إذا كان المستخدم يواجه مشكلة لم يتم معالجتها بالفعل في المقاطع أعلاه أو تعذر عليه حلها باستخدام الخطوات المدرجة، يمكن للمستخدم تقديم ملاحظات داخل التطبيق إلى جانب البيانات **التشخيصية**. بعد ذلك، يمكن لفريقنا التحقق من السجلات لتوفير الحل المناسب. يمكن للمستخدمين اتباع هذه الخطوات للقيام بالشيء نفسه:

1.  افتح **تطبيق MDE** على جهازك وانقر فوق أيقونة **ملف التعريف** في الزاوية العلوية اليمنى.

    :::image type="content" alt-text="انقر فوق أيقونة ملف التعريف." source="images/select-profile-icon-1.jpg":::

2.  حدد "تعليمات & الملاحظات".

    :::image type="content" alt-text="حدد تعليمات وملاحظات." source="images/selecthelpandfeedback2.png":::

3.  حدد "إرسال ملاحظات إلى Microsoft".

    :::image type="content" alt-text="حدد إرسال ملاحظات إلى Microsoft." source="images/send-feedback-to-microsoft-3.jpg":::

4.  اختر من الخيارات المتوفرة. الإبلاغ عن مشكلة، حدد "أريد الإبلاغ عن مشكلة".

    :::image type="content" alt-text="الإبلاغ عن مشكلة." source="images/report-issue-4.jpg":::

5.  قم بتوفير تفاصيل المشكلة التي تواجهها وتحقق من "إرسال بيانات تشخيصية". نوصي بالتحقق من "تضمين عنوان بريدك الإلكتروني" بحيث يمكن للفريق التواصل معك من خلال حل أو متابعة.

    :::image type="content" alt-text="أضف التفاصيل وأرفق البيانات التشخيصية." source="images/finalsubmit5.png":::

6.  انقر فوق "إرسال" لإرسال الملاحظات بنجاح.
