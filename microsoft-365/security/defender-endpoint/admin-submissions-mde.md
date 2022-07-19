---
title: إرسال الملفات في Microsoft Defender لنقطة النهاية
description: تعرف على كيفية استخدام ميزة عمليات الإرسال الموحدة في Microsoft 365 Defender لإرسال رسائل البريد الإلكتروني وعناوين URL ومرفقات البريد الإلكتروني والملفات المريبة إلى Microsoft للمسح الضوئي.
keywords: مكافحة الفيروسات، والبريد العشوائي، والتصيد الاحتيالي، والملف، والتنبيه، Microsoft Defender لنقطة النهاية، الإيجابية الخاطئة، السلبية الخاطئة، الملف المحظور، url المحظور، الإرسال، الإرسال، التقرير
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.date: 06/15/2021
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
manager: dansimp
localization_priority: Normal
audience: ITPro
ms.topic: how-to
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: FPFN
ms.openlocfilehash: 0d445050ea667d54b8a73eb2f040c8114e1dfcfb
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66857491"
---
# <a name="submit-files-in-microsoft-defender-for-endpoint"></a>إرسال الملفات في Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على**

- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2146806)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-usewdatp-abovefoldlink).

في Microsoft Defender لنقطة النهاية، يمكن للمسؤولين استخدام ميزة عمليات الإرسال الموحدة لإرسال الملفات وتجزئة الملفات (SHAs) إلى Microsoft للمراجعة. تجربة عمليات الإرسال الموحدة هي محطة واحدة لإرسال رسائل البريد الإلكتروني وعناوين URL ومرفقات البريد الإلكتروني والملفات في تجربة إرسال واحدة سهلة الاستخدام. يمكن للمسؤولين استخدام مدخل Microsoft 365 Defender أو صفحة التنبيه Microsoft Defender لنقطة النهاية لإرسال الملفات المشبوهة.

## <a name="what-do-you-need-to-know-before-you-begin"></a>ما الذي تحتاج إلى معرفته قبل البدء؟

- تتوفر تجربة عمليات الإرسال الموحدة الجديدة فقط في الاشتراكات التي تتضمن Microsoft 365 Defender أو Microsoft Defender لنقطة النهاية الخطة 2 أو Microsoft Defender ل Office Plan 2.

- لإرسال الملفات إلى Microsoft، يجب أن تكون عضوا في إحدى مجموعات الأدوار التالية:

  - **إدارة المؤسسة** أو **مسؤول الأمان** أو **قارئ الأمان** في [مدخل Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-security-center.md).

- لمزيد من المعلومات حول كيفية إرسال البريد العشوائي والتصيد الاحتيالي وعناوين URL ومرفقات البريد الإلكتروني إلى Microsoft، راجع [تقارير الرسائل والملفات إلى Microsoft](../office-365-security/report-junk-email-messages-to-microsoft.md).

## <a name="report-items-to-microsoft-from-the-portal"></a>الإبلاغ عن العناصر إلى Microsoft من المدخل

إذا كان لديك ملف تشك في أنه قد يكون برنامجا ضارا أو تم اكتشافه بشكل غير صحيح (إيجابي خطأ)، يمكنك إرساله إلى Microsoft لتحليله باستخدام مدخل Microsoft 365 Defender في https://security.microsoft.com/.

### <a name="submit-a-file-or-file-hash"></a>إرسال تجزئة ملف أو ملف

1. افتح Microsoft 365 Defender، <https://security.microsoft.com/>وانقر فوق **"إجراءات" & عمليات الإرسال**، وانقر فوق **"عمليات الإرسال**"، وانتقل إلى علامة التبويب **"ملفات**"، ثم حدد **"إضافة عمليات إرسال جديدة**".

    > [!div class="mx-imgBorder"]
    > ![إضافة عمليات إرسال جديدة](../../media/unified-admin-submission-new.png)

2. استخدم **"إرسال العناصر إلى Microsoft" لمراجعة** القائمة المنبثقة التي تظهر لإرسال  **تجزئة الملف أو الملف**.

3. في المربع **"تحديد نوع الإرسال** "، حدد **"ملف"** أو **"تجزئة ملف"** من القائمة المنسدلة.

4. عند إرسال ملف، انقر فوق **"استعراض الملفات**". في مربع الحوار الذي يتم فتحه، ابحث عن الملف وحدده، ثم انقر فوق **"فتح**". لاحظ أنه بالنسبة إلى عمليات إرسال **تجزئة الملف** ، سيتعين عليك إما نسخ تجزئة الملف أو كتابتها.

5. في **هذا الملف يجب أن يكون قد تم تصنيفه كمقطع** ، اختر إما **البرامج الضارة** (سلبي خطأ)، أو **البرامج غير المرغوب فيها**، أو **Clean** (false positive).

6. بعد ذلك، **اختر الأولوية**. لاحظ أنه بالنسبة إلى عمليات إرسال **تجزئة الملف** ، فإن **إرسال تجزئة الملف المجمع أو الملف المنخفض** هو الخيار الوحيد، ويتم تحديده تلقائيا.

    > [!div class="mx-imgBorder"]
    > ![إرسال العناصر إلى Microsoft للمراجعة](../../media/unified-admin-submission-file.png)

7. انقر فوق **"إرسال**".

   إذا كنت تريد عرض تفاصيل عمليات الإرسال، فحدد عمليات الإرسال من قائمة **أسماء عمليات الإرسال** لفتح القائمة **المنبثقة لتفاصيل النتيجة** .

## <a name="report-items-to-microsoft-from-the-alerts-page"></a>الإبلاغ عن العناصر إلى Microsoft من صفحة التنبيهات

يمكنك أيضا إرسال تجزئة ملف أو ملف مباشرة من قائمة التنبيهات على صفحة **التنبيهات** .

1. افتح Microsoft 365 Defender في <https://security.microsoft.com/>**التنبيهات & الحوادث**، ثم انقر فوق **"تنبيهات**" لعرض قائمة التنبيهات.

2. حدد التنبيه الذي تريد الإبلاغ به. لاحظ أنك ترسل ملفا متداخلا داخل التنبيه.

3. انقر فوق علامات الحذف الموجودة بجانب **"إدارة التنبيه** " للاطلاع على خيارات إضافية. حدد **"إرسال العناصر إلى Microsoft" للمراجعة**.

    > [!div class="mx-imgBorder"]
    > ![إرسال العناصر من قائمة انتظار التنبيهات](../../media/unified-admin-submission-alerts-queue.png)

4. في القائمة المنبثقة التالية التي تفتح، حدد نوع الإرسال.

    > [!div class="mx-imgBorder"]
    > ![إكمال الحقول المطلوبة](../../media/unified-admin-submission-alert-queue-flyout.png)

    إذا قمت بتحديد **"ملف"** كنوع الإرسال، فحمل الملف، وقم بتصنيف عمليات الإرسال، واختر الأولوية.

    إذا قمت بتحديد **"تجزئة الملف"** كنوع الإرسال، فاختر تجزئة الملف المتوفرة من القائمة المنسدلة. يمكنك تحديد تجزئة ملفات متعددة.

5. انقر فوق **"إرسال**".

## <a name="related-information"></a>المعلومات ذات الصلة

- [Microsoft Defender لنقطة النهاية في Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md)
- [معالجة الإيجابيات/السلبيات الخاطئة](defender-endpoint-false-positives-negatives.md)
- [عرض قائمة انتظار التنبيهات وتنظيمها في Microsoft Defender لنقطة النهاية](alerts-queue.md)
