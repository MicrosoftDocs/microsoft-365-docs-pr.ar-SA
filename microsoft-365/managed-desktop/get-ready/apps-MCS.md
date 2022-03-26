---
title: العمل مع Microsoft Consulting Services
description: التحضير والخطوات التي يجب اتباعها للعمل مع MCS لحزم تطبيقاتك
keywords: سطح المكتب المدار من Microsoft، Microsoft 365، الخدمة، الوثائق
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 5dd6bf62625d6b22a0585645abbeb24dabd6c9fd
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/10/2022
ms.locfileid: "63566693"
---
# <a name="working-with-microsoft-consulting-services"></a>العمل مع Microsoft Consulting Services

يمكنك التفاعل مع Microsoft Consulting Services (MCS) للحصول على حزم تطبيقاتك لاستخدامها مع Microsoft Managed Desktop. لمزيد من المعلومات، اعمل مع ممثل حسابك للاتصال ب MCS لمراجعة مشروع حزم التطبيق المحدد.

## <a name="roles-and-responsibilities"></a>الأدوار والمسؤوليات

| الدور | المسؤولية |
| ------ | ------ |
| يمكنك | للعمل باستخدام حزم تطبيق MCS **، يجب توفير العناصر التالية**: <ul><li> ملفات المثبت المصدر (على سبيل المثال، setup.exe أو .msi).</li><li>إرشادات التثبيت التي تحدد تفاصيل حول كيفية مظهر التثبيت النهائي. على سبيل المثال، هل يجب أن يكون هناك اختصار سطح المكتب للتطبيق؟ ما الذي يجب أن تكون عليه رؤية التطبيق؟ هل يجب أن يتصل التطبيق بخادم وإذا كان الأمر كذلك، فما هو التطبيق؟ لمزيد من المعلومات، راجع [قالب طلب حزم التطبيق](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/app-packaging-template.docx).</li><li>يجب إجراء اختبار القبول الخاص بك للتحقق من عمل التطبيق كما هو متوقع في بيئتك.</li><ul> |
| Microsoft Consulting Services (MCS) | **سيتولى MCS الإجراءات التالية:** <ul><li>تحقق مما إذا كان التطبيق محظورا أو مقيدا في بيئة سطح المكتب المدار من Microsoft.</li><li>اختبر تثبيت التطبيق وبدءه و إلغاء تثبيته لضمان التوافق مع Windows 10. إذا اكتشف MCS مشكلة توافق، سيرسل التطبيق إلى [برنامج App Assure](/fasttrack/products-and-capabilities#app-assure) ل الإصلاح.</li><li>يمكنك وضع التطبيق في حزمة حسب المواصفات واختبار نشر التطبيق باستخدام Microsoft Intune.</li><ul>

## <a name="app-delivery-schedule"></a>جدول تسليم التطبيق

ابدأ عملية التعبئة عن طريق تحميل معلومات التطبيق إلى مدخل Microsoft Managed Desktop. يراجع فريق الحزم عمليات الإرسال الجديدة كل خميس. بعد المراجعة والتعبئة، يتم تسليم التطبيقات التي تم حزمها في يوم الجمعة التالي. يمكن حزم ما يصل إلى خمسة تطبيقات في الأسبوع للبدء، ولكن يمكن للخدمة أن تكبر لتلبية احتياجاتك.

![يعرض التقويم تدفق التطبيق في يوم الخميس (21 في هذا المثال)، والتحقق من صحة الوسائط في اليوم التالي، والتغليف في يوم الاثنين التالي (الخامس والعشرين)، وتسليم التطبيق في يوم الجمعة التالي (التاسع والعشرين).](../../media/MCS-cal.png)

سيتم إعلامك بمجرد تسليم التطبيق. في هذه المرحلة، لديك 21 يوما لإجراء اختبار القبول والموافقة على العمل في مدخل Microsoft Managed Desktop. إذا اكتشفت مشكلة في التطبيق أثناء اختبار القبول، فارفض التطبيق في مدخل Microsoft Managed Desktop. سيتم توصيلك عبر البريد الإلكتروني باستخدام حزمة خدمات Microsoft الاستشارية (MCS) لفهم المشكلة وحلها.

## <a name="testing-accounts-and-environment"></a>اختبار الحسابات والبيئة

لكي يكمل فريق الحزم عملية الترحيل إلى Microsoft Intune، نوصي بتوفير أذونات معينة:

- الوصول إلى Microsoft Intune 'نشر التطبيقات' الخاصة بحزم الحزم لإضافة التطبيق وتعيينه.
- اختبار المجموعات وحسابات المستخدمين والتراخيص لمحزمات الحزم لكي تتمكن من اختبار التطبيقات.

سيستخدم MCS هذه الأذونات لتنفيذ الإجراءات التالية:

- تأكد من عمل التطبيق على جهاز ظاهري تم تكوينه لسطح المكتب المدار من Microsoft.
- Upload التطبيق Microsoft Intune لنشره للمستخدمين.

من دون هذه الأذونات، يمكن ل MCS التقدم للأمام، ولكن لن يتمكن من تحميل التطبيقات إلى بيئتك.
