---
title: تمكين الوظيفة الإضافية "رسالة التقرير" أو الوظائف الإضافية "تصيد التقرير"
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: تعرف على كيفية تمكين الوظائف الإضافية "رسالة التقرير" أو "التصيد الاحتيالي للتقرير" Outlook Outlook على ويب أو للمستخدمين الفرديين أو لمؤسستك بأكملها.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a4166b36888c96b12a8aa410848c392c2afdaeb5
ms.sourcegitcommit: 58ec09f1fd66af9717dc2743585d06d358ec7360
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/30/2022
ms.locfileid: "65144828"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>تمكين الوظيفة الإضافية "رسالة التقرير" أو الوظائف الإضافية "تصيد التقرير"

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> إذا كنت مسؤولا في مؤسسة Microsoft 365 مع علب بريد Exchange Online، نوصي باستخدام صفحة **عمليات الإرسال** في مدخل Microsoft 365 Defender. لمزيد من المعلومات، راجع ["استخدام إرسال المسؤول" لإرسال رسائل البريد العشوائي والتصيد الاحتيالي وعناوين URL والملفات المشتبه بها إلى Microsoft](admin-submission.md).

تسهل وظائف التصيد الاحتيالي ل "رسالة التقرير" و"الإبلاغ عن التصيد الاحتيالي" Outlook Outlook على ويب (المعروف سابقا باسم Outlook Web App) الإبلاغ عن الإيجابيات الخاطئة (البريد الإلكتروني الجيد الذي تم وضع علامة عليه على أنه سيئ) أو السلبيات الخاطئة (تم السماح بالبريد الإلكتروني غير الصحيح) إلى Microsoft والشركات التابعة لها للتحليل.

تستخدم Microsoft عمليات الإرسال هذه لتحسين فعالية تقنيات حماية البريد الإلكتروني. على سبيل المثال، افترض أن الأشخاص يبلغون عن العديد من الرسائل باستخدام الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي". تظهر هذه المعلومات في لوحة معلومات الأمان والتقارير الأخرى. يمكن لفريق الأمان في مؤسستك استخدام هذه المعلومات كإشارة إلى أنه قد يلزم تحديث نهج مكافحة التصيد الاحتيالي.

يمكنك تثبيت إما "رسالة التقرير" أو الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي". إذا كنت تريد أن يقوم المستخدمون بالإبلاغ عن رسائل البريد العشوائي والتصيد الاحتيالي، فنشر الوظيفة الإضافية "رسالة التقرير" في مؤسستك.

توفر الوظيفة الإضافية "رسالة التقرير" خيار الإبلاغ عن رسائل البريد العشوائي والتصيد الاحتيالي. يمكن للمسؤولين تمكين الوظيفة الإضافية "رسالة التقرير" للمؤسسة، ويمكن للمستخدمين الفرديين تثبيتها لأنفسهم.

توفر الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" خيار الإبلاغ عن رسائل التصيد الاحتيالي فقط. يمكن للمسؤولين تمكين الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" للمؤسسة، ويمكن للمستخدمين الفرديين تثبيتها لأنفسهم.

إذا كنت مستخدما فرديا، يمكنك تمكين كل من الوظائف الإضافية لنفسك.

إذا كنت مسؤولا عاما أو مسؤول Exchange Online، وتم تكوين Exchange لاستخدام مصادقة OAuth، يمكنك تمكين الوظيفة الإضافية "رسالة التقرير" والوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" لمؤسستك. تتوفر كلتا الوضيفتين الإضافيتين الآن من خلال [النشر المركزي](../../admin/manage/centralized-deployment-of-add-ins.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- تعمل كل من الوظيفة الإضافية "رسالة التقرير" والوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" مع معظم اشتراكات Microsoft 365 والمنتجات التالية:
  - Outlook على ويب
  - Outlook 2013 SP1 أو إصدار أحدث
  - Outlook 2016 for Mac
  - Outlook مضمنة مع تطبيقات Microsoft 365 ل Enterprise
  - تطبيق Outlook لنظامي التشغيل iOS وAndroid

- لا تتوفر كلتا الوضيفتين الإضافيتين لعلب البريد المشتركة.

- لا تتوفر كلتا الوضيفتين الإضافيتين لعلب بريد Exchange المحلية.

- يجب أن يعمل مستعرض الويب الموجود لديك مع كل من الوظائف الإضافية "رسالة التقرير" و"الإبلاغ عن التصيد الاحتيالي". ولكن، إذا لاحظت أن الوظيفة الإضافية غير متوفرة أو لا تعمل كما هو متوقع، فجرب مستعرضا آخر.

- بالنسبة إلى التثبيتات التنظيمية، يجب تكوين المؤسسة لاستخدام مصادقة OAuth. لمزيد من المعلومات، راجع [تحديد ما إذا كان النشر المركزي للوظائف الإضافية يعمل لمؤسستك](../../admin/manage/centralized-deployment-of-add-ins.md).

- يجب أن يكون المسؤولون عضوا في مجموعة دور المسؤولين العموميين. لمزيد من المعلومات، راجع [الأذونات في مدخل Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- لمزيد من المعلومات حول كيفية الإبلاغ عن رسالة باستخدام ميزة "رسالة التقرير"، راجع ["الإبلاغ عن الإيجابيات الخاطئة والسلبيات الخاطئة" في Outlook](report-false-positives-and-false-negatives.md).

- يجب أن يكون لدى المؤسسات التي لديها تصفية URL أو حل أمان (مثل وكيل و/أو جدار حماية) في مكانها، ipagave.azurewebsites.net ونقاط نهاية outlook.office.com مسموح بالوصول إليها على بروتوكول HTTPS.

## <a name="get-the-report-message-add-in"></a>الحصول على الوظيفة الإضافية "رسالة التقرير"

### <a name="get-the-report-message-add-in-for-yourself"></a>الحصول على الوظيفة الإضافية "رسالة التقرير" لنفسك

1. انتقل إلى Microsoft AppSource <https://appsource.microsoft.com/marketplace/apps> وابحث عن الوظيفة الإضافية "رسالة التقرير". للانتقال مباشرة إلى الوظيفة الإضافية "رسالة التقرير"، انتقل إلى <https://appsource.microsoft.com/product/office/wa104381180>.

2. انقر فوق **GET IT NOW**.

   :::image type="content" source="../../media/ReportMessageGETITNOW.png" alt-text="رسالة تقرير Get It Now." lightbox="../../media/ReportMessageGETITNOW.png":::

3. في مربع الحوار الذي يظهر، راجع شروط الاستخدام ونهج الخصوصية، ثم انقر فوق **"متابعة**".

4. سجل الدخول باستخدام حساب العمل أو المؤسسة التعليمية (لاستخدام العمل) أو حساب Microsoft (للاستخدام الشخصي).

بعد تثبيت الوظيفة الإضافية وتمكينها، سترى الأيقونات التالية:

- في Outlook، تبدو الأيقونة كما يلي:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/OutlookReportMessageIcon.png" alt-text="أيقونة الوظيفة الإضافية &quot;رسالة التقرير&quot; ل Outlook." lightbox="../../media/OutlookReportMessageIcon.png":::

- في Outlook على ويب، تبدو الأيقونة كما يلي:

    > [!div class="mx-imgBorder"]
    > ![Outlook على ويب أيقونة الوظيفة الإضافية لرسالة التقرير.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>الحصول على الوظيفة الإضافية "رسالة التقرير" لمؤسستك

> [!NOTE]
> قد يستغرق ظهور الوظيفة الإضافية في مؤسستك ما يصل إلى 12 ساعة.

1. في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com/AdminPortal/Home?#/homepage)، انتقل إلى **الإعدادات** \> **التطبيقات المتكاملة**. انقر فوق **"الحصول على التطبيقات**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="تطبيقات مركز مسؤولي Microsoft 365 المتكاملة." lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. في صفحة **Microsoft 365 Apps** التي تظهر، انقر في المربع **"بحث**"، وأدخل **"رسالة التقرير**"، ثم انقر فوق أيقونة **"البحث** ![في البحث".](../../media/search-icon.png) في قائمة النتائج، ابحث عن **"رسالة التقرير"** وحددها.

3. يتم فتح صفحة تفاصيل التطبيق. حدد **Get It Now**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message.png" alt-text="الوظيفة الإضافية &quot;رسالة التقرير&quot;." lightbox="../../media/microsoft-365-admin-center-report-message.png":::

4. أكمل معلومات ملف التعريف الأساسية، ثم انقر فوق **"متابعة**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-profile-info.png" alt-text="إعداد ملف تعريف الوظيفة الإضافية لرسالة التقرير." lightbox="../../media/microsoft-365-admin-center-profile-info.png":::

5. يتم فتح القائمة المنبثقة **"نشر تطبيق جديد** ". تكوين الإعدادات التالية. انقر فوق **"التالي** " للانتقال إلى الصفحة التالية لإكمال الإعداد.

   - **إضافة مستخدمين**: حدد إحدى القيم التالية:
     - **أنا فقط**
     - **المؤسسة بأكملها**
     - **مستخدمون /مجموعات معينة**

   - **النشر**:
     - **قبول طلبات الأذونات**: اقرأ أذونات التطبيق وإمكانياته بعناية قبل الانتقال إلى الصفحة التالية.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deploy-new-app.png" alt-text="صفحة طلبات قبول الأذونات." lightbox="../../media/microsoft-365-admin-center-deploy-new-app.png":::

     - **إنهاء النشر**: مراجعة نشر الوظيفة الإضافية والانتهاء منها.
     - **اكتمل التوزيع**: حدد **"تم** " لإكمال الإعداد.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deployment-complete.png" alt-text="اكتملت رسالة الإعلام الخاصة بالنشر." lightbox="../../media/microsoft-365-admin-center-deployment-complete.png":::

## <a name="edit-settings-for-the-report-message-add-in"></a>تحرير الإعدادات للوظيفة الإضافية "رسالة التقرير"

1. في مركز مسؤولي Microsoft 365، انتقل إلى **الإعدادات** \> **التطبيقات المتكاملة** \. ثم ابحث عن الوظيفة الإضافية **"رسالة التقرير"** وحددها.

2. في القائمة المنبثقة التي تظهر، حدد **"تحرير المستخدمين"** لتحرير إعدادات المستخدم.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message-edit.png" alt-text="القائمة المنبثقة لرسالة التقرير." lightbox="../../media/microsoft-365-admin-center-report-message-edit.png":::

3. لإزالة الوظيفة الإضافية، حدد **"إزالة التطبيق** " ضمن **"الإجراءات"** في القائمة المنبثقة نفسها.

## <a name="get-the-report-phishing-add-in"></a>الحصول على الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي"

### <a name="get-the-report-phishing-add-in-for-yourself"></a>الحصول على الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" لنفسك

1. انتقل إلى Microsoft AppSource <https://appsource.microsoft.com/marketplace/apps> وابحث عن الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي".

2. انقر فوق **GET IT NOW**.

3. في مربع الحوار الذي يظهر، راجع شروط الاستخدام ونهج الخصوصية، ثم انقر فوق **"متابعة**".

4. سجل الدخول باستخدام حساب العمل أو المؤسسة التعليمية (لاستخدام العمل) أو حساب Microsoft (للاستخدام الشخصي).

بعد تثبيت الوظيفة الإضافية وتمكينها، سترى الأيقونات التالية:

- في Outlook، تبدو الأيقونة كما يلي:

  ![أيقونة الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" Outlook.](../../media/Outlook-ReportPhishing.png)

- في Outlook على ويب، تبدو الأيقونة كما يلي:

    > [!div class="mx-imgBorder"]
    > ![Outlook على ويب أيقونة الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي".](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>الحصول على الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي" لمؤسستك

> [!NOTE]
> قد يستغرق ظهور الوظيفة الإضافية في مؤسستك ما يصل إلى 12 ساعة.

1. في [مركز مسؤولي Microsoft 365](https://admin.microsoft.com/AdminPortal/Home?#/homepage)، انتقل إلى **الإعدادات** \> **التطبيقات المتكاملة**. انقر فوق **"الحصول على التطبيقات**".

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="تطبيقات مركز مسؤولي Microsoft 365 المتكاملة." lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. في صفحة **Microsoft 365 Apps** التي تظهر، انقر في المربع **"بحث**"، وأدخل **"الإبلاغ عن التصيد الاحتيالي**"، ثم انقر فوق أيقونة **البحث**![.](../../media/search-icon.png) في قائمة النتائج، ابحث عن **"التصيد الاحتيالي للتقرير" وحدده**.

3. يتم فتح صفحة تفاصيل التطبيق. حدد **Get It Now**.

4. أكمل معلومات ملف التعريف الأساسية، ثم انقر فوق **"متابعة**".

5. يتم فتح القائمة المنبثقة **"نشر تطبيق جديد** ". اتبع الخطوات [الموضحة أعلاه](enable-the-report-message-add-in.md#get-the-report-message-add-in-for-your-organization) لإكمال الإعداد.

## <a name="edit-settings-for-the-report-phishing-add-in"></a>تحرير إعدادات الوظيفة الإضافية "الإبلاغ عن التصيد الاحتيالي"

1. في مركز مسؤولي Microsoft 365، انتقل إلى **الإعدادات** \> **التطبيقات المتكاملة** \. ثم ابحث عن الوظيفة **الإضافية "الإبلاغ عن التصيد الاحتيالي** " وحددها.

2. في القائمة المنبثقة التي تظهر، حدد **"تحرير المستخدمين"** لتحرير إعدادات المستخدم.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-phishing-edit.png" alt-text="القائمة المنبثقة &quot;الإبلاغ عن التصيد الاحتيالي&quot;." lightbox="../../media/microsoft-365-admin-center-report-phishing-edit.png":::

3. لإزالة الوظيفة الإضافية، حدد **"إزالة التطبيق** " ضمن **"الإجراءات"** في القائمة المنبثقة نفسها.
