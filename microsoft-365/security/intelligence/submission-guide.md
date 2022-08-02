---
title: إرسال الملفات للتحليل بواسطة Microsoft
description: تعرف على كيفية إرسال الملفات إلى Microsoft لتحليل البرامج الضارة، وكيفية تعقب عمليات الإرسال، واكتشافات النزاعات.
ms.reviewer: ''
keywords: الأمان، عينة تعليمات الإرسال، ملف البرامج الضارة، ملف الفيروسات، ملف أحصنة طروادة، إرسال، إرسال إلى Microsoft، إرسال عينة، فيروس، أحصنة طروادة، فيروسات، فيروسات غير مكتشفة، لا تكتشف، البريد الإلكتروني microsoft، البرامج الضارة، أعتقد أن هذا برنامج ضار، أعتقد أنه فيروس، أين يمكنني إرسال فيروس، هل هذا فيروس، MSE، لا يكشف، لا توقيع، لا اكتشاف، ملف مشبوه،  MMPC، مركز الحماية من البرامج الضارة لـ Microsoft، والباحثين، والمحلل، وWDSI، والذكاء الأمني
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 28dfb21cb918ca5f0b99579304f3135664e11533
ms.sourcegitcommit: adc4e5707aa074fc4aa0cb9e8c2986fc8b88813c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67112032"
---
# <a name="submit-files-for-analysis"></a>إرسال الملفات لتحليلها

إذا كان لديك ملف تشك في أنه قد يكون برنامجا ضارا أو تم اكتشافه بشكل غير صحيح، يمكنك إرساله إلينا للتحليل. تحتوي هذه الصفحة على إجابات لبعض الأسئلة الشائعة حول إرسال ملف للتحليل.

## <a name="how-do-i-submit-a-file-to-microsoft-for-analysis"></a>كيف أعمل إرسال ملف إلى Microsoft للتحليل؟

### <a name="send-a-malware-file"></a>إرسال ملف برامج ضارة

يمكنك إرسال الملفات التي تعتقد أنها برامج ضارة أو ملفات تم اكتشافها بشكل غير صحيح من خلال [مدخل إرسال العينة](https://www.microsoft.com/wdsi/filesubmission).

يمكنك إكمال تحليل سريع من خلال توفير معلومات مفصلة حول المنتج الذي كنت تستخدمه وما كنت تفعله عند العثور على الملف.

بعد تسجيل الدخول، ستتمكن من تعقب عمليات الإرسال.

> [!NOTE]
>
> يمكنك استخدام ميزة إرسال WDSI حتى إذا لم يكن لديك Microsoft Defender لنقطة النهاية الخطة 2 أو Microsoft Defender لخطة Office 2.

### <a name="submit-a-suspected-email-attachment"></a>إرسال مرفق بريد إلكتروني مشتبه به

استخدم [مدخل Microsoft 365 Defender](https://security.microsoft.com/) لإرسال مرفقات البريد الإلكتروني المشتبه بها إلى Microsoft للمراجعة. لمزيد من المعلومات، راجع [إرسال مرفق بريد إلكتروني مشتبه به إلى Microsoft](../office-365-security/admin-submission.md).

### <a name="submit-a-file-or-file-hash"></a>إرسال تجزئة ملف أو ملف

استخدم ميزة عمليات الإرسال الموحدة في Microsoft Defender لنقطة النهاية لإرسال الملفات وتجزئة الملفات إلى Microsoft لمراجعتها. لمزيد من المعلومات، راجع ["إرسال الملفات" في Microsoft Defender لنقطة النهاية](../defender-endpoint/admin-submissions-mde.md).

## <a name="can-i-send-a-sample-by-email"></a>هل يمكنني إرسال عينة بالبريد الإلكتروني؟

لا، نحن نقبل فقط عمليات الإرسال من خلال [نموذج مدخل الإرسال](https://www.microsoft.com/wdsi/filesubmission) الخاص بنا.

## <a name="can-i-submit-a-sample-without-signing-in"></a>هل يمكنني إرسال نموذج دون تسجيل الدخول؟

لا. إذا كنت عميل مؤسسة، فستحتاج إلى تسجيل الدخول حتى نتمكن من تحديد أولويات عمليات الإرسال بشكل مناسب. إذا كنت تواجه حاليا انتشار فيروس أو حادث متعلق بالأمان، فيجب عليك الاتصال باحترافية دعم Microsoft المعينة أو الانتقال إلى [دعم Microsoft](https://support.microsoft.com/) للحصول على مساعدة فورية.

## <a name="what-is-the-software-assurance-id-said"></a>ما هو معرف ضمان البرنامج (SAID)؟

معرف [ضمان البرامج (SAID)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) هو لعملاء المؤسسات لتتبع استحقاقات الدعم. يقبل مدخل الإرسال معلومات SAID ويحتفظ بها ويسمح للعملاء الذين يعانون من معرفات SAID صالحة بتقديم عمليات إرسال ذات أولوية أعلى.

### <a name="how-do-i-dispute-the-detection-of-my-program"></a>كيف أعمل في اكتشاف برنامجي؟

[أرسل الملف](https://www.microsoft.com/wdsi/filesubmission) المعني كمطور برامج. انتظر حتى يتم تحديد الإرسال النهائي.

إذا لم تكن راضيا عن تحديد عمليات الإرسال، فاستخدم نموذج جهة اتصال المطور المتوفر مع نتائج الإرسال للوصول إلى Microsoft. سنستخدم المعلومات التي تقدمها لمزيد من التحقيق إذا لزم الأمر.

نحن نشجع جميع موردي البرامج والمطورين على القراءة حول [كيفية تعريف Microsoft للبرامج الضارة والبرامج غير المرغوب فيها](criteria.md).

## <a name="how-do-i-track-or-view-past-sample-submissions"></a>كيف أعمل تعقب عمليات الإرسال النموذجية السابقة أو عرضها؟

يمكنك تعقب عمليات الإرسال من خلال [صفحة محفوظات الإرسال](https://www.microsoft.com/wdsi/submissionhistory).

## <a name="what-does-the-submission-status-mean"></a>ماذا تعني حالة الإرسال؟

يظهر كل عملية إرسال في أحد أنواع الحالة التالية:

* تم الإرسال — تم تلقي الملف

* قيد التقدم - بدأ محلل في التحقق من الملف

* مغلق - تم تحديد نهائي من قبل محلل

يمكنك الاطلاع على حالة أي ملفات ترسلها إلينا في [صفحة محفوظات الإرسال](https://www.microsoft.com/wdsi/submissionhistory).

## <a name="how-does-microsoft-prioritize-submissions"></a>كيف تحدد Microsoft أولويات عمليات الإرسال

تأخذ معالجة عمليات الإرسال مورد محلل مخصص. ولأننا نتلقى بانتظام عددا كبيرا من عمليات الإرسال، فإننا نتعامل معها بناء على الأولوية. تؤثر العوامل التالية على كيفية تحديد أولويات عمليات الإرسال:

* يتم تحديد أولويات الملفات الشائعة التي يحتمل أن تؤثر على أعداد كبيرة من أجهزة الكمبيوتر.

* يتم إعطاء العملاء المصادق عليهم، خاصة عملاء المؤسسات الذين يستخدمون [معرفات ضمان البرامج (SAIDs)](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default.aspx) الصالحة، الأولوية.

* يتم إعطاء عمليات الإرسال التي تم وضع علامة عليها على أنها ذات أولوية عالية من قبل أصحاب SAID اهتماما فوريا.

يتم فحص عمليات الإرسال الخاصة بك على الفور بواسطة أنظمتنا لمنحك أحدث قرار حتى قبل أن يبدأ المحلل في معالجة حالتك. لاحظ أن الملف نفسه قد تمت معالجته بالفعل من قبل محلل. للتحقق من وجود تحديثات للتحديد، حدد rescan في صفحة تفاصيل الإرسال.
