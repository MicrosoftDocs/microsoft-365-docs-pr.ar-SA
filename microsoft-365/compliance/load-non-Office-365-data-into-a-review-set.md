---
title: تحميل البيانات غير Microsoft 365 في مجموعة مراجعة
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: تعرف على كيفية استيراد بيانات غير Microsoft 365 إلى مجموعة مراجعة للتحليل في حالة eDiscovery (Premium).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 41ba0a3d9f1989cff2bdffdab38f7eee020d7b5d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095807"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>تحميل البيانات غير Microsoft 365 في مجموعة مراجعة

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

لا توجد كل المستندات التي تحتاج إلى تحليلها في Microsoft Purview eDiscovery (Premium) في Microsoft 365. باستخدام ميزة استيراد البيانات غير Microsoft 365 في eDiscovery (Premium)، يمكنك تحميل المستندات غير الموجودة في Microsoft 365 إلى مجموعة مراجعة. توضح لك هذه المقالة كيفية إحضار المستندات غير Microsoft 365 إلى eDiscovery (Premium) للتحليل.

## <a name="requirements-to-upload-non-office-365-content"></a>متطلبات تحميل محتوى غير Office 365

يتطلب استخدام ميزة التحميل غير Microsoft 365 الموضحة في هذه المقالة أن يكون لديك ما يلي:

- يجب تعيين الترخيص المناسب لجميع أمناء الحفظ الذين تريد إقران المحتوى غير Microsoft 365 بهم. لمزيد من المعلومات، راجع [بدء استخدام eDiscovery (Premium).](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses)

- حالة eDiscovery (Premium) موجودة.

- يجب إضافة أمناء الحفظ إلى الحالة قبل أن تتمكن من تحميل البيانات غير Microsoft 365 وإقرانها بهم.

- يجب أن تكون البيانات غير Microsoft 365 نوع ملف يدعمه eDiscovery (Premium). لمزيد من المعلومات، راجع [أنواع الملفات المعتمدة في eDiscovery (Premium).](supported-filetypes-ediscovery20.md)

- يجب أن تكون جميع الملفات التي يتم تحميلها إلى مجموعة مراجعة موجودة في مجلدات، حيث يقترن كل مجلد بوصي معين. يجب أن تستخدم أسماء هذه المجلدات تنسيق التسمية التالي: *alias@domainname*. يجب أن يكون alias@domainname اسم المستخدم المستعار Microsoft 365 والمجال. يمكنك تجميع كافة مجلدات alias@domainname في مجلد جذر. يمكن أن يحتوي المجلد الجذر على مجلدات alias@domainname فقط. الملفات غير المفككة في المجلد الجذر غير معتمدة.

   ستكون بنية المجلد للبيانات غير Microsoft 365 التي تريد تحميلها مشابهة للمثال التالي:

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   حيث abraham.mcmahon@contoso.com، jewell.gordon@contoso.com، staci.gonzalez@contoso.com هي عناوين SMTP للأمناء في هذه الحالة.

   ![بنية مجلد تحميل البيانات غير Microsoft 365.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- حساب تم تعيينه إلى مجموعة أدوار eDiscovery Manager (وإضافته كمسؤول eDiscovery).

- أداة AzCopy v8.1 المثبتة على كمبيوتر لديه حق الوصول إلى بنية مجلد المحتوى غير Microsoft 365. لتثبيت AzCopy، راجع [نقل البيانات باستخدام الإصدار 8.1 من AzCopy على Windows](/previous-versions/azure/storage/storage-use-azcopy). تأكد من تثبيت AzCopy في الموقع الافتراضي، وهو **٪ProgramFiles(x86)٪\Microsoft SDKs\Azure\AzCopy**. يجب استخدام AzCopy v8.1. قد لا تعمل الإصدارات الأخرى من AzCopy عند تحميل البيانات غير Microsoft 365 في eDiscovery (Premium).


## <a name="upload-non-microsoft-365-content-into-ediscovery-premium"></a>Upload المحتوى غير Microsoft 365 في eDiscovery (Premium)

1. بصفة مدير eDiscovery أو مسؤول eDiscovery، افتح eDiscovery (Premium)، وانتقل إلى الحالة التي سيتم تحميل البيانات غير Microsoft 365 إليها.  

2. انقر فوق **مجموعات المراجعة**، ثم حدد مجموعة المراجعة لتحميل البيانات غير Microsoft 365 إليها.  إذا لم يكن لديك مجموعة مراجعة، يمكنك إنشاء واحدة. 
 
3. افتح مجموعة المراجعة إما بالنقر فوقها أو تحديدها والنقر فوق **"فتح مجموعة المراجعة**".

4. في مجموعة المراجعة، انقر فوق **"إدارة مجموعة المراجعة**" (السهم لأسفل بعد خيار **"الإجراءات**")، ثم انقر فوق خيار **البيانات "غير Office 365**".

5. انقر فوق **Upload الملفات** لبدء معالج استيراد البيانات.

   ![Upload الملفات.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   تقوم الخطوة الأولى في المعالج بإعداد موقع تخزين Azure آمن توفره Microsoft لتحميل الملفات إليه.  عند اكتمال الإعداد، يصبح الزر **"التالي:Upload files**" نشطا.

   ![استيراد غير Microsoft 365: إعداد.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. انقر فوق **"التالي": Upload الملفات**.

6. في صفحة **ملفات Upload**، قم بما يلي:

   ![استيراد غير Microsoft 365: Upload الملفات.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   أ. في المربع **"مسار إلى موقع الملفات**"، تحقق من موقع المجلد الجذر الذي قمت بتخزين البيانات غير Microsoft 365 التي تريد تحميلها أو اكتبه. على سبيل المثال، لموقع الملفات المثال المعروضة في **المقطع "قبل البدء**"، يمكنك كتابة **٪USERPROFILE\Downloads\nonO365**. يضمن توفير الموقع الصحيح تحديث أمر AzCopy المعروض في المربع أسفل المسار بشكل صحيح.

   ب. انقر فوق **"نسخ إلى الحافظة** " لنسخ الأمر المعروض في المربع.

7. ابدأ موجه أوامر Windows، والصق الأمر الذي نسخته في الخطوة السابقة، ثم اضغط على **مفتاح الإدخال Enter** لبدء تشغيل الأمر AzCopy.  بعد بدء الأمر، سيتم تحميل الملفات غير Microsoft 365 إلى موقع تخزين Azure الذي تم إعداده في الخطوة 4.

   ![استيراد غير Microsoft 365: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > كما ذكر سابقا، يجب عليك استخدام الإصدار 8.1 من AzCopy لاستخدام الأمر المتوفر على صفحة **ملفات Upload** بنجاح. إذا فشل أمر AzCopy المتوفر، فالرجاء مراجعة [استكشاف أخطاء AzCopy وإصلاحها في eDiscovery (Premium)](troubleshooting-azcopy.md).

8. ارجع إلى مدخل توافق Microsoft Purview، وانقر فوق **"التالي": معالجة الملفات** في المعالج.  يؤدي ذلك إلى بدء معالجة واستخراج النص وفهرسة الملفات غير Microsoft 365 التي تم تحميلها إلى موقع تخزين Azure.  

9. تعقب تقدم معالجة الملفات على صفحة **"معالجة الملفات**" أو على علامة التبويب **"المهام**" من خلال عرض مهمة تسمى **"إضافة بيانات غير Microsoft 365" إلى مجموعة مراجعة**.  بعد انتهاء المهمة، ستتوفر الملفات الجديدة في مجموعة المراجعة.

   ![استيراد غير Microsoft 365: معالجة الملفات.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. بعد الانتهاء من المعالجة، يمكنك إغلاق المعالج.
