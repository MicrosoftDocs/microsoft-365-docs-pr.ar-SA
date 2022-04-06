---
title: استخدام Microsoft Teams الاجتماعات مع اللوحة
ms.author: v-cichur
author: cichur
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: دمج Microsoft Teams الاجتماعات مع اللوحة
ms.openlocfilehash: 529cc27b6b63fca76d47487f26bd6deda7478640
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569568"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>استخدام Microsoft Teams الاجتماعات مع اللوحة

Microsoft Teams الاجتماعات هي Learning أدوات التشغيل التفاعلي (LTI) الذي يساعد المعلمين والطلاب على التنقل بسهولة بين نظام إدارة Learning (LMS) Teams. يمكن للمستخدمين الوصول إلى فرق الصف المقترنة بمهمتهم التدريبية مباشرة من داخل LMS.

## <a name="prerequisites-before-deployment"></a>المتطلبات الأساسية قبل النشر

> [!NOTE]
> تدعم Teams اجتماعات LTI فقط مزامنة مستخدمي اللوحة مع Microsoft Azure Active Directory (AAD (دليل Azure النشط)) في نطاق محدود.
>
> - يجب أن يكون لدى المستأجر ترخيص Microsoft Education.
> - يمكن استخدام مستأجر Microsoft واحد فقط لتعيين المستخدمين بين Canvas و Microsoft.
> - يجب إيقاف تشغيل مزامنة بيانات المؤسسة التعليمية (SDS) قبل استخدام الفئة Teams LTI لتجنب تكرار المجموعات.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 المسؤول

قبل إدارة تكامل Microsoft Teams ضمن لوحة Instructure، من المهم أن يكون تطبيق **Microsoft-Teams-Sync-for-Canvas** Azure الخاص ب Canvas معتمدا من قبل مسؤول Microsoft Office 365 في مؤسستك في مستأجر Microsoft Azure قبل إكمال إعداد مسؤول اللوحة.

1. سجل الدخول إلى اللوحة القماشية.

2. حدد ارتباط **المسؤول** في التنقل العام، ثم حدد حسابك.

3. في شريط تنقل المسؤول، **حدد الارتباط الإعدادات** ثم علامة **التبويب عمليات** التكامل.

   ![لوحة Teams مزامنة محدثة png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. أدخل اسم مستأجر Microsoft وسمة تسجيل الدخول و لاحقة المجال AAD (دليل Azure النشط) البحث. سيتم استخدام هذه الحقول لمطابقة المستخدمين في Canvas مع المستخدمين في Microsoft Azure Active Directory.
   - السمة Login (تسجيل الدخول) هي سمة مستخدم Canvas المستخدمة للمطابقة.
   - يعد حقل لاحقة اختياريا ويسمح لك بتحديد مجال عند عدم وجود تعيين دقيق بين سمات اللوحة AAD (دليل Azure النشط) Microsoft. على سبيل المثال، إذا كان بريدك الإلكتروني في Canvas "name@example.edu" بينما UPN في Microsoft AAD (دليل Azure النشط) هو "الاسم"، يمكنك مطابقة المستخدمين عن طريق إدخال "example.edu" في حقل اللاحقة.
   - إن السمة "البحث في Active Directory" هي الحقل على جانب Microsoft الذي تتطابق سمات اللوحة به. حدد بين UPN أو عنوان البريد الإلكتروني الأساسي أو الاسم المستعار للبريد الإلكتروني.

5. حدد **تحديث الإعدادات** مرة واحدة.

6. للموافقة على الوصول إلى تطبيق **Microsoft-Teams-Sync-for-Canvas** Azure الخاص ب Canvas، حدد الارتباط **منح وصول المستأجر**. سيتم إعادة توجيهك إلى نقطة نهاية موافقة مسؤول النظام الأساسي ل Microsoft Identity.

   ![الأذونات.](media/permissions.png)

7. حدد **قبول**.

   > [!NOTE]
   > المزامنة هي وظيفة يديرها شريك LMS وتستخدم لمزامنة العضوية على مستوى الدورة التدريبية مع فريق Teams باستخدام واجهات برمجة تطبيقات رسم Microsoft. هذه في المقام الأول وظيفة يقوم المعلم بتبديلها ك true على مستوى الدورة التدريبية. بعد ذلك، سينعكس أي تغيير في العضوية تم على جانب LMS من أجل إضافة الأعضاء أو حذفهم باستخدام مزامنة التي ينفذها شريك LMS. حتى قبل تمكين هذه العملية لمعلم، يسمح مسؤول المؤسسة التعليمية M365 للمعلمين بالوصول إلى المزامنة باستخدام مشروط إذن المزامنة المعثر عليه أدناه. يتم منح هذه الأذونات لشريك LMS لتمكين المعلمين من مزامنة العضوية بين الدورة التدريبية ل LMS Teams للصف.

8. قم بتمكين Microsoft Teams من خلال تشغيل تبديل.

   ![teams-sync.](media/teams-sync.png)

## <a name="canvas-admin"></a>مسؤول اللوحة

قم بإعداد Microsoft Teams LTI 1.3.

كمسؤول لوحة قماشية، ستحتاج إلى إضافة Microsoft Teams LTI للاجتماعات داخل بيئتك. دون "معر ى عميل LTI" للتطبيق.

 - Microsoft Teams الاجتماعات - 170000000000703

1. إعدادات **مسؤول** **AccessApps** > .

2. حدد **+ تطبيق** لإضافة Teams LTI.

   ![التطبيقات الخارجية.](media/external-apps.png)

3. حدد **حسب "الم ID العميل** " لنوع التكوين.

   ![إضافة تطبيق.](media/add-app.png)

4. أدخل "الموفر لمعر العميل"، ثم حدد **إرسال**.

   ستلاحظ اسم Microsoft Teams LTI للاجتماعات لمعرف العميل للتأكيد.

5. حدد **تثبيت**.

   وستضاف Microsoft Teams LTI للاجتماعات إلى قائمة التطبيقات الخارجية.

6. قم بتمكين التطبيق من خلال الانتقال إلى مفاتيح المطور في حساب مسؤول اللوحة، وتحديد موروث، وتحويل مفتاح تبديل "تشغيل" Microsoft Teams الاجتماعات.

## <a name="enable-for-canvas-courses"></a>تمكين الدورات التدريبية للوحة

لاستخدام LTI ضمن دورة تدريبية، يجب أن يقوم معلم الدورة التدريبية Canvas بتمكين مزامنة عمليات التكامل. يجب تمكين كل دورة تدريبية من قبل معلم لإنشاء Teams، ولا توجد آلية Teams إنشاء الدورة التدريبية. تم تصميم هذا لمنع إنشاء Teams غير المرغوب فيها.

الرجاء إحالة المعلمين إلى [وثائق المعلمين](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) لتمكين LTI لكل دورة تدريبية والانتهاء من إعداد التكامل.
