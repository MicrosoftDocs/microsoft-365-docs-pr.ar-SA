---
title: جرب Microsoft 365 Defender قدرات الاستجابة للحوادث في بيئة تجريبية
description: جرب قدرات الاستجابة للحوادث في Microsoft 365 Defender لتحديد أولويات الحوادث وإدارتها، وأتمتة التحقيقات، واستخدام التتبع المتقدم في الكشف عن التهديدات.
keywords: Microsoft 365 Defender التجربة، جرب Microsoft 365 Defender، وتقييم Microsoft 365 Defender، Microsoft 365 Defender معمل التقييم، Microsoft 365 Defender  الإصدار التجريبي، والأمان السيبراني، والتهديدات المستمرة المتقدمة، وأمان المؤسسة، والأجهزة، والجهاز، والهوية، والمستخدمين، والبيانات، والتطبيقات، والحوادث، والتحقيق التلقائي والمعالجة، والتتبع المتقدم
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 01a263569da09807c96160c32fda719bd2575994
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748464"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>جرب Microsoft 365 Defender قدرات الاستجابة للحوادث في بيئة تجريبية

**ينطبق على:**
- Microsoft 365 Defender

هذه المقالة هي [الخطوة 2 من 2](eval-defender-investigate-respond.md) في عملية إجراء تحقيق والاستجابة لحادث في Microsoft 365 Defender باستخدام بيئة تجريبية. لمزيد من المعلومات حول هذه العملية، راجع مقالة [النظرة العامة](eval-defender-investigate-respond.md) .

بمجرد إجراء [استجابة للحوادث لهجوم محاكاة](eval-defender-investigate-respond-simulate-attack.md)، إليك بعض Microsoft 365 Defender القدرات لاستكشاف:

|القدره |الوصف |
|:-------|:-----|
| [تحديد أولويات الحوادث](#prioritize-incidents) | استخدم تصفية قائمة انتظار الأحداث وفرزها لتحديد الحوادث التي يجب معالجتها بعد ذلك. |
| [إدارة الحوادث](#manage-incidents) | تعديل خصائص الحدث لضمان التعيين الصحيح، وإضافة علامات وتعليقات، وحل حدث. |
| [التحقيق التلقائي والاستجابة (AIR)](#examine-automated-investigation-and-response-with-the-action-center) | استخدم قدرات التحقيق والاستجابة التلقائية (AIR) لمساعدة فريق عمليات الأمان على معالجة التهديدات بشكل أكثر كفاءة وفعالية. مركز الصيانة هو تجربة "جزء واحد من الزجاج" لمهام الحدث والتنبيه مثل الموافقة على إجراءات المعالجة المعلقة. |
| [الصيد المتقدم](#use-advanced-hunting) | استخدم الاستعلامات لفحص الأحداث في شبكتك بشكل استباقي وتحديد مؤشرات التهديد والكيانات. يمكنك أيضا استخدام التتبع المتقدم أثناء التحقيق في الحادث ومعالجتها. |


## <a name="prioritize-incidents"></a>تحديد أولوية الأحداث

يمكنك الوصول إلى قائمة انتظار الحوادث من **تنبيهات & الحوادث > الحوادث** على الإطلاق السريع <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">لمدخل Microsoft 365 Defender</a>. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="قسم تنبيهات & الحوادث في مدخل Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::


يعرض قسم **التنبيهات والحوادث الأحدث** رسما بيانيا لعدد التنبيهات المستلمة والحوادث التي تم إنشاؤها في آخر 24 ساعة.

لفحص قائمة الحوادث وتحديد أولويات أهميتها للتعيين والتحقيق، يمكنك: 

- تكوين أعمدة قابلة للتخصيص (حدد **اختيار الأعمدة**) لمنحك رؤية في خصائص مختلفة للحادث أو الكيانات المتأثرة. يساعدك هذا على اتخاذ قرار مستنير فيما يتعلق بتحديد أولويات الحوادث للتحليل.

- استخدم التصفية للتركيز على سيناريو أو تهديد معين. يمكن أن يساعد تطبيق عوامل التصفية في قائمة انتظار الحدث في تحديد الحوادث التي تتطلب انتباها فوريا. 

من قائمة انتظار الأحداث الافتراضية، حدد **عوامل التصفية** لمشاهدة جزء **عوامل التصفية** ، الذي يمكنك من خلاله تحديد مجموعة معينة من الحوادث. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="جزء عوامل التصفية من قسم التنبيهات & الحوادث في مدخل Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

لمزيد من المعلومات، راجع [تحديد أولويات الحوادث](incident-queue.md).

## <a name="manage-incidents"></a>إدارة الأحداث

يمكنك إدارة الحوادث من جزء **إدارة الحوادث** لحدث ما. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="جزء إدارة الحوادث في قسم تنبيهات & الحوادث في مدخل Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

يمكنك عرض هذا الجزء من ارتباط **إدارة الحدث** على:

- جزء الخصائص لحدث في قائمة انتظار الحدث.
- صفحة **ملخص** لحادث.

فيما يلي الطرق التي يمكنك من خلالها إدارة الحوادث:

- تحرير اسم الحدث

  قم بتغيير الاسم المعين تلقائيا استنادا إلى أفضل ممارسات فريق الأمان.
  
- إضافة علامات الحادث

  أضف العلامات التي يستخدمها فريق الأمان لتصنيف الحوادث، والتي يمكن تصفيتها لاحقا.
  
- تعيين الحدث

  قم بتعيينه إلى اسم حساب مستخدم، والذي يمكن تصفيته لاحقا.
  
- حل حدث

  أغلق الحدث بعد إصلاحه.
  
- تعيين تصنيفه وتحديده

  قم بتصنيف نوع التهديد وتحديده عند حل حدث.
  
- إضافة تعليقات

  استخدم التعليقات للتقدم أو الملاحظات أو معلومات أخرى استنادا إلى أفضل ممارسات فريق الأمان. تتوفر محفوظات التعليقات الكاملة من خيار **التعليقات والمحفوظات** في صفحة تفاصيل الحادث.

لمزيد من المعلومات، راجع [إدارة الحوادث](manage-incidents.md).

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>فحص التحقيق التلقائي والاستجابة باستخدام مركز الصيانة

اعتمادا على كيفية تكوين قدرات التحقيق والاستجابة التلقائية لمؤسستك، يتم اتخاذ إجراءات المعالجة تلقائيا أو فقط بناء على موافقة فريق عمليات الأمان. يتم سرد جميع الإجراءات، سواء كانت معلقة أو مكتملة، في [مركز الصيانة](m365d-action-center.md)، الذي يسرد إجراءات المعالجة المعلقة والمكتملة لأجهزتك والبريد الإلكتروني & محتوى التعاون والهويات في موقع واحد.

فيما يلي مثال على ذلك.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="مركز الإجراءات الموحدة في مدخل Microsoft 365 Defender" lightbox="../../media/m3d-action-center-unified.png":::

من مركز الصيانة، يمكنك تحديد الإجراءات المعلقة ثم الموافقة عليها أو رفضها في جزء القائمة المنبثقة. فيما يلي مثال على ذلك.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="يعرض الجزء خيارات الموافقة على إجراء أو رفضه في مدخل Microsoft 365 Defender" lightbox="../../media/air-actioncenter-itemselected.png":::


الموافقة على (أو رفض) الإجراءات المعلقة في أقرب وقت ممكن بحيث يمكن متابعة التحقيقات التلقائية وإكمالها في الوقت المناسب.

لمزيد من المعلومات، راجع [التحقيق التلقائي والاستجابة](m365d-autoir.md) [ومركز الصيانة](m365d-action-center.md).

## <a name="use-advanced-hunting"></a>استخدام التتبع المتقدم

> [!NOTE]
> قبل أن نرشدك خلال محاكاة التتبع المتقدمة، شاهد الفيديو التالي لفهم مفاهيم التتبع المتقدمة، ومعرفة أين يمكنك العثور عليها في المدخل، ومعرفة كيف يمكن أن تساعدك في عمليات الأمان الخاصة بك.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


إذا كانت [محاكاة هجوم PowerShell الاختيارية بلا ملف](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) عبارة عن هجوم حقيقي وصل بالفعل إلى مرحلة الوصول إلى بيانات الاعتماد، يمكنك استخدام التتبع المتقدم في أي نقطة في التحقيق للبحث بشكل استباقي من خلال الأحداث والسجلات في الشبكة باستخدام ما تعرفه بالفعل من التنبيهات التي تم إنشاؤها والكيانات المتأثرة. 

على سبيل المثال، استنادا إلى المعلومات في تنبيه [استكشاف عنوان IP والمستخدم (SMB)،](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity) يمكنك استخدام `IdentityDirectoryEvents` الجدول للعثور على جميع أحداث تعداد جلسة SMB، أو العثور على المزيد من أنشطة الاكتشاف في بروتوكولات أخرى مختلفة في بيانات Microsoft Defender for Identity باستخدام `IdentityQueryEvents` الجدول.


### <a name="hunting-environment-requirements"></a>متطلبات بيئة التتبع

هناك علبة بريد وجهاز داخلي واحد مطلوب لهذه المحاكاة. ستحتاج أيضا إلى حساب بريد إلكتروني خارجي لإرسال رسالة الاختبار.

1. تحقق من [تمكين المستأجر الخاص بك Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. تحديد علبة بريد هدف لاستخدامها لتلقي البريد الإلكتروني.

   - يجب مراقبة علبة البريد هذه بواسطة Microsoft Defender لـ Office 365

   - يحتاج الجهاز من المتطلب 3 إلى الوصول إلى علبة البريد هذه

3. تكوين جهاز اختبار:

    أ. تأكد من أنك تستخدم الإصدار Windows 10 1903 أو الإصدار الأحدث.

    ب. انضم إلى جهاز الاختبار إلى مجال الاختبار.

    ج. [تشغيل برنامج الحماية من الفيروسات لـ Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). إذا كنت تواجه مشكلة في تمكين برنامج الحماية من الفيروسات لـ Windows Defender، فراجع [هذا الموضوع لاستكشاف الأخطاء وإصلاحها](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

    د. [إلحاق Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>تشغيل المحاكاة

1. من حساب بريد إلكتروني خارجي، أرسل بريدا إلكترونيا إلى علبة البريد المحددة في الخطوة 2 من قسم متطلبات بيئة التتبع. قم بتضمين مرفق سيتم السماح به من خلال أي نهج عامل تصفية بريد إلكتروني موجودة. لا يلزم أن يكون هذا الملف ضارا أو قابلا للتنفيذ. أنواع الملفات المقترحة <i> هي.pdf</i><i> أو.exe</i> (إذا كان مسموحا به) أو نوع مستند Office مثل ملف Word.

2. افتح البريد الإلكتروني المرسل من الجهاز الذي تم تكوينه كما هو محدد في الخطوة 3 من قسم متطلبات بيئة التتبع. افتح المرفق أو احفظ الملف على الجهاز.

#### <a name="go-hunting"></a>الانتقال إلى التتبع

1. افتح مدخل <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>.

2. من جزء التنقل، حدد **التتبع > التتبع المتقدم**.

3. إنشاء استعلام يبدأ بجمع أحداث البريد الإلكتروني.

   1. حدد **استعلام > جديد**.

   1. في مجموعات **البريد الإلكتروني** ضمن **التتبع المتقدم**، انقر نقرا مزدوجا فوق **EmailEvents**. يجب أن تشاهد هذا في نافذة الاستعلام.

      ```console
      EmailEvents
      ```

   1. تغيير الإطار الزمني للاستعلام إلى آخر 24 ساعة. بافتراض أن البريد الإلكتروني الذي أرسلته عند تشغيل المحاكاة أعلاه كان في ال 24 ساعة الماضية، وإلا فقم بتغيير الإطار الزمني حسب الحاجة.

   1. حدد **تشغيل الاستعلام**. قد تكون لديك نتائج مختلفة اعتمادا على بيئة الإصدار التجريبي.

      > [!NOTE]
      > راجع الخطوة التالية لخيارات التصفية للحد من إرجاع البيانات.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-1.png" alt-text="صفحة Advanced Hunting في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-1.png":::

        > [!NOTE]
        > يعرض التتبع المتقدم نتائج الاستعلام كبيانات جدولية. يمكنك أيضا اختيار عرض البيانات في أنواع تنسيقات أخرى مثل المخططات.

   1. انظر إلى النتائج وشاهد ما إذا كان يمكنك تحديد البريد الإلكتروني الذي فتحته. قد يستغرق ظهور الرسالة في التتبع المتقدم ما يصل إلى ساعتين. لتضييق نطاق النتائج، يمكنك إضافة شرط **المكان** إلى الاستعلام للبحث فقط عن رسائل البريد الإلكتروني التي تحتوي على "yahoo.com" ك SenderMailFromDomain الخاصة بها. فيما يلي مثال على ذلك.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. انقر فوق الصفوف الناتجة من الاستعلام حتى تتمكن من فحص السجل.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-2.png" alt-text="قسم فحص السجل من صفحة التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-2.png":::

4. الآن بعد أن تحققت من إمكانية رؤية البريد الإلكتروني، أضف عامل تصفية للمرفقات. ركز على كل رسائل البريد الإلكتروني التي تحتوي على مرفقات في البيئة. بالنسبة إلى هذه المحاكاة، ركز على رسائل البريد الإلكتروني الواردة، وليس تلك التي يتم إرسالها من بيئتك. قم بإزالة أي عوامل تصفية أضفتها لتحديد موقع رسالتك وإضافة "| حيث **> AttachmentCount 0** و **EmailDirection** == **"Inbound""**

   سيعرض لك الاستعلام التالي النتيجة بقائمة أقصر من الاستعلام الأولي لكافة أحداث البريد الإلكتروني:

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. بعد ذلك، قم بتضمين المعلومات حول المرفق (مثل: اسم الملف، تجزئة) إلى مجموعة النتائج. للقيام بذلك، انضم إلى جدول **EmailAttachmentInfo** . الحقول الشائعة التي يجب استخدامها للانضمام، في هذه الحالة هي **NetworkMessageId** و **RecipientObjectId**.

   يتضمن الاستعلام التالي أيضا سطرا إضافيا "| **أعد تسمية المشروع EmailTimestamp=Timestamp**" التي ستساعد في تحديد الطابع الزمني الذي كان مرتبطا بالبريد الإلكتروني مقابل الطوابع الزمنية المتعلقة بإجراءات الملفات التي ستضيفها في الخطوة التالية.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. بعد ذلك، استخدم قيمة **SHA256** من جدول **EmailAttachmentInfo** للعثور على **DeviceFileEvents** (إجراءات الملف التي حدثت على نقطة النهاية) لهذا التجزئة. سيكون الحقل الشائع هنا هو تجزئة SHA256 للمرفق.

   يتضمن الجدول الناتج الآن تفاصيل من نقطة النهاية (Microsoft Defender لنقطة النهاية) مثل اسم الجهاز، وما الإجراء الذي تم تنفيذه (في هذه الحالة، تمت تصفيته لتضمين أحداث FileCreated فقط)، والمكان الذي تم تخزين الملف فيه. سيتم أيضا تضمين اسم الحساب المقترن بالعملية.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   لقد قمت الآن بإنشاء استعلام يحدد جميع رسائل البريد الإلكتروني الواردة حيث قام المستخدم بفتح المرفق أو حفظه. يمكنك أيضا تحسين هذا الاستعلام لتصفية مجالات معينة للمرسلين وأحجام الملفات وأنواع الملفات وما إلى ذلك.

7. الوظائف هي نوع خاص من الصلة، والتي تتيح لك سحب المزيد من بيانات TI حول ملف مثل انتشاره، الموقع ومعلومات المصدر، وما إلى ذلك. للحصول على مزيد من التفاصيل حول الملف، استخدم إثراء الدالة **FileProfile()** :

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>إنشاء الكشف

بمجرد إنشاء استعلام يحدد المعلومات التي تريد **أن يتم تنبيهك** حولها إذا حدثت في المستقبل، يمكنك إنشاء الكشف المخصص من الاستعلام.

ستقوم عمليات الكشف المخصصة بتشغيل الاستعلام وفقا للتكرار الذي قمت بتعيينه، وستنشئ نتائج الاستعلامات تنبيهات أمان، استنادا إلى الأصول المتأثرة التي تختارها. وستربط هذه التنبيهات بالحوادث ويمكن فرزها كأي تنبيه أمني آخر تم إنشاؤه بواسطة أحد المنتجات.

1. في صفحة الاستعلام، قم بإزالة الأسطر 7 و8 التي تمت إضافتها في الخطوة 7 من إرشادات التتبع Go وانقر فوق **إنشاء قاعدة الكشف**.

   :::image type="content" source="../../media/advanced-hunting-incident-response-try-3.png" alt-text="قسم تحرير الاستعلام في صفحة التتبع المتقدم في مدخل Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-3.png":::

   > [!NOTE]
   > إذا نقرت فوق **"إنشاء قاعدة الكشف** " وكان لديك أخطاء في بناء الجملة في الاستعلام، فلن يتم حفظ قاعدة الكشف. تحقق مرة أخرى من الاستعلام للتأكد من عدم وجود أخطاء.

2. املأ الحقول المطلوبة بالمعلومات التي ستسمح لفريق الأمان بفهم التنبيه، ولماذا تم إنشاؤه، والإجراءات التي تتوقع منهم اتخاذها.

   :::image type="content" source="../../media/mtp/fig23.png" alt-text="صفحة تفاصيل التنبيه في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig23.png":::

   تأكد من تعبئة الحقول بوضوح للمساعدة في منح المستخدم التالي قرارا مستنيرا حول تنبيه قاعدة الكشف هذا

3. حدد الكيانات المتأثرة في هذا التنبيه. في هذه الحالة، حدد **الجهاز** **وعلبة البريد**.

   :::image type="content" source="../../media/mtp/fig24.png" alt-text="صفحة تفاصيل الكيانات المتأثرة في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig24.png":::

4. تحديد الإجراءات التي يجب اتخاذها إذا تم تشغيل التنبيه. في هذه الحالة، قم بتشغيل فحص مكافحة الفيروسات، على الرغم من إمكانية اتخاذ إجراءات أخرى.

   :::image type="content" source="../../media/mtp/fig25.png" alt-text="صفحة الإجراءات في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig25.png":::

5. حدد نطاق قاعدة التنبيه. نظرا لأن هذا الاستعلام يتضمن أجهزة، فإن مجموعات الأجهزة ذات صلة بهذا الكشف المخصص وفقا لسياق Microsoft Defender لنقطة النهاية. عند إنشاء الكشف المخصص الذي لا يتضمن الأجهزة ككيانات متأثرة، لا ينطبق النطاق.

   :::image type="content" source="../../media/mtp/fig26.png" alt-text="صفحة النطاق في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig26.png":::


   بالنسبة لهذا الإصدار التجريبي، قد تحتاج إلى تحديد هذه القاعدة إلى مجموعة فرعية من أجهزة الاختبار في بيئة الإنتاج الخاصة بك.

6. حدد **"إنشاء**". ثم حدد **قواعد الكشف المخصصة** من لوحة التنقل.

   :::image type="content" source="../../media/mtp/fig27a.png" alt-text="خيار قواعد الكشف المخصصة في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig27a.png":::

   :::image type="content" source="../../media/mtp/fig27b.png" alt-text="الصفحة التي تعرض قواعد الكشف وتفاصيل التنفيذ في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig27b.png":::

   من هذه الصفحة، يمكنك تحديد قاعدة الكشف، والتي ستفتح صفحة تفاصيل.

   :::image type="content" source="../../media/mtp/fig28.png" alt-text="الصفحة التي تعرض تفاصيل التنبيهات التي تم تشغيلها في مدخل Microsoft 365 Defender" lightbox="../../media/mtp/fig28.png":::


### <a name="expert-training-on-advanced-hunting"></a>تدريب الخبراء على التتبع المتقدم

**تتبع الخصم** هو سلسلة بث ويب لمحللين أمنيين جدد ومتتبعي التهديدات المحنكين. فهو يرشدك من خلال أساسيات التتبع المتقدم وصولا إلى إنشاء استعلاماتك المتطورة الخاصة. 

راجع [الحصول على تدريب الخبراء على التتبع المتقدم](advanced-hunting-expert-training.md) للبدء.

### <a name="navigation-you-may-need"></a>التنقل الذي قد تحتاج إليه

[إنشاء بيئة تقييم Microsoft 365 Defender](eval-create-eval-environment.md)
