---
title: تحميل بيانات غير Microsoft 365 إلى مجموعة مراجعة
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: تعرف على كيفية استيراد بيانات غير Microsoft 365 إلى مجموعة مراجعة لتحليلها في Advanced eDiscovery أخرى.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39f91846e42bb2403c2b1faf7fd98ff3e7759182
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63566118"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>تحميل بيانات غير Microsoft 365 إلى مجموعة مراجعة

لا توجد كل المستندات التي تحتاج إلى تحليلها في Advanced eDiscovery في Microsoft 365. باستخدام ميزة استيراد البيانات غير Microsoft 365 في Advanced eDiscovery، يمكنك تحميل المستندات غير الموجودة في Microsoft 365 إلى مجموعة مراجعة. توضح لك هذه المقالة كيفية إحضار المستندات غير Microsoft 365 إلى Advanced eDiscovery لتحليلها.

## <a name="requirements-to-upload-non-office-365-content"></a>متطلبات تحميل محتوى Office 365 غير محتوي

يتطلب استخدام ميزة Microsoft 365 غير الموضحة في هذه المقالة أن يكون لديك ما يلي:

- يجب أن يتم تعيين الترخيص المناسب لجميع المشركين الذين تريد إقران Microsoft 365 غير المستخدمين. لمزيد من المعلومات، راجع [بدء استخدام Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- حالة موجودة Advanced eDiscovery حالة.

- يجب إضافة التغذية إلى الحالة قبل أن تتمكن من تحميل البيانات غير Microsoft 365 وإقرانها بها.

- يجب أن Microsoft 365 البيانات غير المعتمدة من نوع ملف معتمد بواسطة Advanced eDiscovery. لمزيد من المعلومات، راجع [أنواع الملفات المعتمدة في Advanced eDiscovery](supported-filetypes-ediscovery20.md).

- يجب أن تكون كل الملفات التي يتم تحميلها إلى مجموعة مراجعة موجودة في مجلدات، حيث يقترن كل مجلد بمحافظ معين. يجب أن تستخدم أسماء هذه المجلدات تنسيق التسمية *التالي: alias@domainname*. يجب alias@domainname أن تكون اسم المستخدم Microsoft 365 ومجاله. يمكنك تجميع كل alias@domainname المجلدات في مجلد الجذر. يمكن أن يحتوي المجلد الجذر على المجلدات alias@domainname فقط. الملفات الفضفضة في المجلد الجذر غير معتمدة.

   تكون بنية المجلد للبيانات غير Microsoft 365 التي تريد تحميلها مماثلة للمثال التالي:

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   حيث abraham.mcmahon@contoso.com jewell.gordon@contoso.com و staci.gonzalez@contoso.com هي عناوين SMTP للمشتركين في هذه الحالة.

   ![بنية مجلد تحميل Microsoft 365 البيانات غير الأساسية.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- حساب تم تعيينه إلى مجموعة دور eDiscovery Manager (وإضافته كمسؤول eDiscovery).

- تم تثبيت أداة AzCopy v8.1 على كمبيوتر لديه حق الوصول إلى بنية مجلد المحتوى Microsoft 365 غير المثبت. لتثبيت AzCopy، راجع نقل [البيانات باستخدام AzCopy v8.1 على Windows](/previous-versions/azure/storage/storage-use-azcopy). تأكد من تثبيت AzCopy في الموقع الافتراضي، وهو **٪ProgramFiles(x86)٪\Microsoft SDKs\Azure\AzCopy**. يجب استخدام AzCopy v8.1. قد لا تعمل الإصدارات الأخرى من AzCopy عند تحميل بيانات غير Microsoft 365 في Advanced eDiscovery.


## <a name="upload-non-microsoft-365-content-into-advanced-ediscovery"></a>Upload محتوى غير Microsoft 365 في Advanced eDiscovery

1. كمدير eDiscovery أو مسؤول eDiscovery، افتح Advanced eDiscovery واذهب إلى حالة تحميل البيانات غير Microsoft 365 إلى.  

2. انقر **فوق مراجعة المجموعات**، ثم حدد مجموعة المراجعة لتحميل البيانات غير Microsoft 365 إلى.  إذا لم يكن لديك مجموعة مراجعة، يمكنك إنشاء واحدة. 
 
3. افتح مجموعة المراجعة إما بالنقر فوقها أو تحديدها والنقر فوق **فتح مجموعة المراجعة**.

4. في مجموعة المراجعة، انقر فوق **إدارة** مجموعة المراجعة (السهم لأسفل مباشرة بعد الخيار إجراءات)، ثم انقر فوق الخيار بيانات **غير Office 365 البيانات**.

5. انقر **Upload الملفات** لبدء تشغيل معالج استيراد البيانات.

   ![Upload الملفات.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   تقوم الخطوة الأولى في المعالج بإعداد موقع تخزين Azure آمن توفره Microsoft لتحميل الملفات عليه.  عند اكتمال الإعداد، يصبح الزر التالي **: Upload** الملفات نشطا.

   ![استيراد غير Microsoft 365: تحضير.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. انقر **فوق التالي: Upload الملفات**.

6. في صفحة **Upload** الملفات، يمكنك القيام بما يلي:

   ![استيراد غير Microsoft 365: Upload الملفات.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   أ. في **المربع مسار** إلى موقع الملفات، تحقق من موقع المجلد الجذر الذي قمت بتخزين البيانات غير المخزنة فيه Microsoft 365 التي تريد تحميلها أو اكتبه. على سبيل المثال، بالنسبة إلى موقع أمثلة الملفات المعروضة في المقطع قبل البدء، يمكنك كتابة **٪USERPROFILE\downloads\nonO365**. يضمن توفير الموقع الصحيح تحديث أمر AzCopy المعروض في أسفل المسار بشكل صحيح.

   ب. انقر **فوق نسخ إلى الحافظة** لنسخ الأمر المعروض في المربع.

7. ابدأ Windows موجه الأوامر، وألصق الأمر الذي نسخته في الخطوة السابقة، ثم اضغط على **Enter** لبدء الأمر AzCopy.  بعد بدء الأمر، سيتم تحميل الملفات غير Microsoft 365 إلى موقع تخزين Azure الذي تم إعداده في الخطوة 4.

   ![استيراد غير Microsoft 365: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > كما ذكر سابقا، يجب استخدام AzCopy v8.1 لاستخدام الأمر الذي تم توفيره على صفحة ملفات **Upload بنجاح.** إذا فشل الأمر AzCopy الذي تم توفيره، فالرجاء الاطلاع على استكشاف الأخطاء في [AzCopy وإصلاحها في](troubleshooting-azcopy.md) Advanced eDiscovery.

8. ارجع إلى مركز التوافق في Microsoft 365، وانقر فوق **التالي: معالجة الملفات** في المعالج.  هذا الأمر يبدأ في معالجة الملفات غير Microsoft 365 التي تم تحميلها إلى موقع تخزين Azure واستخراج النص وفهرستها.  

9. تعقب تقدم معالجة الملفات على الصفحة معالجة الملفات أو على  علامة التبويب المهام من خلال عرض  مهمة تسمى إضافة بيانات غير Microsoft 365 إلى **مجموعة مراجعة**.  بعد انتهاء المهمة، ستتوفر الملفات الجديدة في مجموعة المراجعة.

   ![استيراد غير Microsoft 365: معالجة الملفات.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. بعد الانتهاء من المعالجة، يمكنك إغلاق المعالج.
