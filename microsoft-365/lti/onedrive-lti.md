---
title: دمج Microsoft OneDrive LTI مع Canvas
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: إنشاء الواجبات ووضع الدرجات عليها، وإنشاء محتوى الدورة التدريبية وتنسيقه، والتعاون في العمل على الملفات في الوقت الحقيقي باستخدام تطبيق التشغيل التفاعلي الجديد لأدوات Microsoft OneDrive Learning ل Canvas.
ms.openlocfilehash: 5de027c9d7606ebe546a8dc8e087b91da7f0400e
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824553"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>دمج Microsoft OneDrive LTI مع Canvas

يعد دمج Microsoft OneDrive LTI مع Canvas عملية على خطوتين. تمكن الخطوة الأولى Microsoft OneDrive في Canvas، والخطوة الثانية تجعل Microsoft OneDrive LTI متوفرة ضمن دورات Canvas التدريبية.

## <a name="recommended-browser-settings"></a>إعدادات المستعرض الموصى بها

- يجب تمكين ملفات تعريف الارتباط Microsoft OneDrive.
- يجب عدم حظر العناصر المنبثقة Microsoft OneDrive.

> [!NOTE]
>
> - لا يتم تمكين ملفات تعريف الارتباط بشكل افتراضي في وضع التصفح المتخفي لمستعرض Chrome، وستحتاج إلى تمكينها.
> - يعمل Microsoft OneDrive LTI في الوضع الخاص في مستعرض Microsoft Edge. تأكد من عدم حظر ملفات تعريف الارتباط (التي يتم تمكينها بشكل افتراضي).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>تمكين Microsoft OneDrive LTI في Canvas

> [!IMPORTANT]
> يجب أن يكون الشخص الذي يقوم بهذا التكامل مسؤولا عن Canvas ومسؤولا عن مستأجر Microsoft 365.

1. تسجيل الدخول إلى <a href="https://onedrivelti.microsoft.com/admin" target="_blank">مدخل تسجيل Microsoft OneDrive LTI</a>
2. حدد الزر " **موافقة المسؤول** " واقبل الأذونات.

   > [!CAUTION]
   > إذا لم يتم تنفيذ هذه الخطوة، فإن الخطوة التالية ستعطيك خطأ، ولن تتمكن من اتخاذ هذه الخطوة لمدة ساعة بمجرد حصولك على الخطأ.

3. حدد الزر **"إنشاء مستأجر LTI جديد** ". في صفحة تسجيل LTI، حدد **Canvas** في القائمة المنسدلة وأدخل عنوان URL الأساسي لمثيل Canvas.

   > [!NOTE]
   > إذا كان مثيل Canvas الخاص بك، على سبيل المثال، `https://contoso.test.instructure.com`يجب إدخال عنوان URL الكامل.

   :::image type="content" source="media/OneDrive-LTI-07.png" alt-text="صفحة إدارة مستأجر LTI، مع حقل منسدلة لاختيار النظام الأساسي للمستهلك LTI وحقل نص URL.":::

4. انسخ JSON عن طريق تحديد الزر **"نسخ** " (أيقونة على اليمين تعرض صفحتين فوق بعضهما البعض). سيتم استخدام هذا لإنشاء المفتاح في Canvas.

   :::image type="content" source="media/OneDrive-LTI-08.png" alt-text="صورة تعرض زر النسخ الذي سيقوم بنسخ نص JSON المعروض وإتاحته لإنشاء المفتاح في Canvas.":::

5. سجل الدخول إلى مثيل Canvas كمسؤول وحدد **"مفاتيح المطور"** من القائمة الموجودة على الجانب الأيمن من الصفحة. من القائمة المنسدلة، قم بإنشاء مفتاح مطور عن طريق اختيار **مفتاح LTI** من القائمة المنسدلة في أعلى يمين الصفحة.

   :::image type="content" source="media/OneDrive-LTI-14.png" alt-text="لقطة شاشة تعرض شريط التنقل الأيسر مع تحديد &quot;Developer Keys&quot;، وتحديد إدخال مفتاح LTI من القائمة المنسدلة على يمين الصفحة.":::

6. في صفحة "Configure"، في القائمة المنسدلة " **Method** "، حدد **"لصق JSON** " كأسلوب والصق نص JSON الذي نسخته في الخطوة 4 في حقل النص الذي يظهر.

    > [!TIP]
    > **الخطوة الاختيارية:** إذا كان معلمو مدرستك يرغبون في التحكم بأنفسهم في الارتباطات التي تظهر في التنقل في دوراتهم التدريبية، يمكنك تعديل المعلمة ``default`` في JSON المنسوخ. ``default`` يتم تعيين المعلمة إلى ``enabled`` تلقائيا؛ ومع ذلك، يتم تغيير ``default`` المعلمة لسمح للمعلمين ``disabled`` باختيار التنقل في الدورات التدريبية الخاصة بهم.
    >
    > لمزيد من المعلومات حول كيفية تعديل المعلمين لارتباطات التنقل للدورة التدريبية الخاصة بهم، راجع [كيف أعمل إدارة ارتباطات التنقل للدورة التدريبية؟](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. احفظ المفتاح، ويصبح متوفرا في Canvas في حالة **إيقاف التشغيل** . قم **بتشغيل** المفتاح وانسخ المفتاح المعطى في عمود **"التفاصيل** " لاستخدامه في الخطوة التالية.

   :::image type="content" source="media/OneDrive-LTI-19.png" alt-text="صفحة Canvas مع تعيين المفتاح في حالة إيقاف التشغيل. يجب تشغيل المفتاح وسيحتاج إلى نسخه من عمود التفاصيل في هذه الصفحة.":::

8. ارجع إلى مدخل تسجيل Microsoft OneDrive LTI والصق المفتاح في حقل **معرف عميل Canvas**. حدد **"التالي** " عندما تصبح جاهزا.

   :::image type="content" source="media/OneDrive-LTI-20.png" alt-text="صفحة تسجيل مستأجر LTI، التي تعرض نص JSON ومربع النص الذي يجب نسخ المفتاح إليه.":::

9. راجع التغييرات واحفظها. سيتم عرض رسالة عند التسجيل الناجح.
10. يمكن أيضا مراجعة تفاصيل التسجيل عن طريق تحديد الزر **View LTI Tenants** على الصفحة الرئيسية.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>تمكين Microsoft OneDrive LTI في دورات Canvas التدريبية

يمكن لمسؤول Canvas تمكين Microsoft OneDrive LTI لجميع الدورات التدريبية. إذا كانت هناك حاجة Microsoft OneDrive LTI في دورة محددة (وليس جميع الدورات التدريبية)، يحتاج معلم الدورة التدريبية إلى اتباع نفس الخطوات ضمن إعدادات الدورة التدريبية.

1. سجل دخولك كمسؤول وانتقل إلى قسم **الإعدادات**.
2. انتقل إلى قسم **"التطبيقات** " وحدد الزر **"عرض تكوينات التطبيقات** ".
3. حدد الزر **"إضافة تطبيق** ".
4. في القائمة المنسدلة **"نوع التكوين** "، اختر الخيار **"حسب معرف العميل** ".
5. الصق قيمة مفتاح المطور الذي تم إنشاؤه مسبقا في حقل **"معرف العميل"** ، وحدد الزر **"إرسال** ".

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="صفحة إضافة تطبيق، تعرض الخيار &quot;حسب معرف العميل&quot; ضمن القائمة المنسدلة لنوع التكوين.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>الإعدادات التعاون ل Microsoft OneDrive LTI في دورات Canvas التدريبية

> [!NOTE]
> لكي يعمل التعاون للمعلمين والطلاب، يجب عدم تمكين إعداد التعاون. للتأكد من عدم تمكين الإعداد، اتبع الخطوات أدناه.

1. سجل دخولك كمسؤول وانتقل إلى قسم **الإعدادات**.
1. انتقل إلى قسم **"خيارات الميزات** "، ثم انتقل إلى قسم **الدورة التدريبية** .
1. قم بتعيين ميزة " **أداة التعاون الخارجي** " لكي لا يتم تمكينها.

> [!NOTE]
> يمكن تعيين التعاون للطلاب الفرديين ومجموعات الطلاب. يعمل التعيين للطلاب الفرديين بشكل افتراضي. لكي تتمكن من تعيين التعاون لمجموعة من الطلاب، اتبع الخطوات التالية:

1. تسجيل الدخول كمسؤول والانتقال إلى قسم **"مفاتيح المطور** ".
1. ابحث عن المفتاح ذي القيمة 170000000000710 وقم بتعيينه إلى **"تشغيل**".
