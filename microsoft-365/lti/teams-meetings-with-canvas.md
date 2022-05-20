---
title: استخدام اجتماعات Microsoft Teams مع Canvas
ms.author: danismith
author: DaniEASmith
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
description: دمج اجتماعات Microsoft Teams مع Canvas
ms.openlocfilehash: a81b8c7da014ba4ded9e4a2e3cfd6b38509ae2db
ms.sourcegitcommit: b5529afa84f7dde0a89b1e08aeaf6a3a15cd7679
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/20/2022
ms.locfileid: "65599602"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>استخدام اجتماعات Microsoft Teams مع Canvas

Microsoft Teams الاجتماعات هو تطبيق Learning أدوات التشغيل التفاعلي (LTI) الذي يساعد المعلمين والطلاب على التنقل بسهولة بين نظام إدارة Learning (LMS) Teams. يمكن للمستخدمين الوصول إلى فرق الصفوف المرتبطة بدورتهم التدريبية مباشرة من داخل LMS الخاصة بهم.

## <a name="prerequisites-before-deployment"></a>المتطلبات الأساسية قبل النشر

> [!NOTE]
> يدعم LTI للاجتماعات Teams الحالي فقط مزامنة مستخدمي Canvas مع Microsoft Azure Active Directory (AAD) في نطاق محدود.
>
> - يجب أن يكون لدى المستأجر ترخيص Microsoft Education.
> - يمكن استخدام مستأجر Microsoft واحد فقط لتعيين المستخدمين بين Canvas وMicrosoft.
> - سيتعين عليك إيقاف تشغيل مزامنة بيانات المؤسسة التعليمية (SDS) قبل استخدام الفئة Teams LTI لتجنب تكرار المجموعات.

## <a name="microsoft-office-365-admin"></a>مسؤول Microsoft Office 365

قبل إدارة تكامل Microsoft Teams داخل Instructure Canvas، من المهم أن تتم الموافقة على تطبيق **Microsoft-Teams-Sync-for-Canvas** Azure من قبل مسؤول Microsoft Office 365 في مؤسستك في مستأجر Microsoft Azure قبل إكمال إعداد مسؤول Canvas.

1. سجل الدخول إلى Canvas.

2. حدد ارتباط **المسؤول** في التنقل العمومي، ثم حدد حسابك.

3. في تنقل المسؤول، حدد الارتباط **الإعدادات**، ثم علامة التبويب **Integrations**.

   ![لوحة Teams مزامنة png محدثة.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. أدخل اسم مستأجر Microsoft وسمة تسجيل الدخول ولاحقة المجال وسمة بحث AAD. سيتم استخدام هذه الحقول لمطابقة المستخدمين في Canvas مع المستخدمين في Microsoft Azure Active Directory.
   - سمة تسجيل الدخول هي سمة مستخدم Canvas المستخدمة للمطابقة.
   - حقل اللاحقة اختياري ويسمح لك بتحديد مجال عندما لا يكون هناك تعيين دقيق بين سمات Canvas وحقول Microsoft AAD. على سبيل المثال، إذا كان البريد الإلكتروني للوحة 'name@example.edu' بينما UPN في Microsoft AAD هو 'name'، يمكنك مطابقة المستخدمين عن طريق إدخال 'example.edu' في حقل اللاحقة.
   - سمة البحث ل Active Directory هي الحقل الموجود على جانب Microsoft الذي يتم مطابقة سمات Canvas به. حدد ما بين UPN أو عنوان البريد الإلكتروني الأساسي أو الاسم المستعار للبريد الإلكتروني.

5. حدد **"تحديث الإعدادات**" بمجرد الانتهاء.

6. للموافقة على الوصول إلى تطبيق **Microsoft-Teams-Sync-for-Canvas** Azure من Canvas، حدد ارتباط **منح حق الوصول للمستأجر**. ستتم إعادة توجيهك إلى نقطة نهاية موافقة مسؤول Microsoft Identity Platform.

   ![اذونات.](media/permissions.png)

7. حدد **"قبول**".

   > [!NOTE]
   > المزامنة هي وظيفة يديرها شريك LMS وتستخدم لمزامنة العضوية على مستوى الدورة التدريبية مع فريق Teams باستخدام واجهات برمجة تطبيقات الرسم البياني من Microsoft. هذه هي في المقام الأول وظيفة يقوم المعلم بتشغيلها على أنها صحيحة على مستوى الدورة التدريبية. بعد ذلك، يظهر أي تغيير في العضوية يتم إجراؤه على LMS من أجل إضافة الأعضاء أو حذفهم باستخدام المزامنة التي ينفذها شريك LMS. حتى قبل تمكين هذه العملية لمعلم، يسمح مسؤول مؤسسة التعليم M365 للمعلمين بالوصول إلى المزامنة باستخدام نموذج إذن المزامنة الموجود أدناه. يتم منح هذه الأذونات إلى شريك LMS لتمكين المعلمين من مزامنة العضوية بين دورة LMS وفرق الصفوف Teams.

8. تمكين مزامنة Microsoft Teams عن طريق تشغيل التبديل.

   ![مزامنة الفرق.](media/teams-sync.png)

## <a name="canvas-admin"></a>مسؤول اللوحة

إعداد تكامل Microsoft Teams LTI 1.3.

بصفتك مسؤول اللوحة، ستحتاج إلى إضافة تطبيق LTI للاجتماعات Microsoft Teams داخل بيئتك. دون ملاحظة عن معرف عميل LTI للتطبيق.

 - اجتماعات Microsoft Teams - 170000000000703

1. Access **Admin settingsApps** > .

2. حدد **+ App** لإضافة تطبيقات LTI Teams.

   ![التطبيقات الخارجية.](media/external-apps.png)

3. حدد **حسب معرف العميل** لنوع التكوين.

   ![إضافة تطبيق.](media/add-app.png)

4. أدخل معرف العميل المتوفر، ثم حدد **"إرسال**".

   ستلاحظ Microsoft Teams اسم تطبيق LTI للاجتماعات لمعرف العميل للتأكيد.

5. حدد **تثبيت**.

   ستتم إضافة تطبيق LTI للاجتماعات Microsoft Teams إلى قائمة التطبيقات الخارجية.

6. قم بتمكين التطبيق من خلال الانتقال إلى مفاتيح المطور في حساب مسؤول Canvas، وتحديد موروث، وتشغيل التبديل "تشغيل" للاجتماعات Microsoft Teams.

## <a name="enable-for-canvas-courses"></a>تمكين دورات Canvas التدريبية

لاستخدام LTI ضمن دورة تدريبية، يجب أن يقوم معلم الدورة التدريبية Canvas بتمكين مزامنة عمليات التكامل. يجب تمكين كل دورة تدريبية من قبل مدرب لإنشاء Teams مقابل؛ لا توجد آلية عمومية لإنشاء Teams. تم تصميم ذلك بحذر لمنع إنشاء Teams غير المرغوب فيها.

الرجاء الرجوع إلى [وثائق المعلم](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) لتمكين LTI لكل دورة تدريبية وإنهاء إعداد التكامل.
