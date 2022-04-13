---
title: دمج Microsoft OneDrive LTI مع Blackboard
ms.author: danismith
author: DaniEASmith
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
description: إنشاء الواجبات ووضع الدرجات عليها، وإنشاء محتوى الدورة التدريبية وتنسيقه، والتعاون في العمل على الملفات في الوقت الحقيقي باستخدام إمكانية التشغيل التفاعلي لأدوات Microsoft OneDrive Learning الجديدة ل Blackboard.
ms.openlocfilehash: 7e43ff51a069db55be06236fb0318aa4453d8feb
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824641"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>دمج Microsoft OneDrive LTI مع Blackboard

دمج Microsoft OneDrive LTI مع Blackboard هو عملية من خطوتين. تجعل الخطوة الأولى Microsoft OneDrive LTI متوفرة ضمن دورات Blackboard التدريبية، وتدور الخطوة الثانية على Microsoft OneDrive ل Blackboard.

> [!IMPORTANT]
> يجب أن يكون الشخص الذي ينفذ هذا التكامل مسؤولا عن Blackboard ومسؤولا عن مستأجر Microsoft 365.

## <a name="recommended-browser-settings"></a>إعدادات المستعرض الموصى بها

- يجب السماح لملفات تعريف الارتباط Microsoft OneDrive.
- لا ينبغي حظر العناصر المنبثقة Microsoft OneDrive.

> [!NOTE]
>
> - لا يسمح بملفات تعريف الارتباط بشكل افتراضي في وضع التصفح المتخفي لمستعرض Chrome وستحتاج إلى السماح بها.
> - يعمل Microsoft OneDrive LTI في الوضع الخاص في مستعرض Microsoft Edge. تأكد من أنك لم تقم بحظر ملفات تعريف الارتباط (المسموح بها بشكل افتراضي).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>تسجيل أداة OneDrive LTI 1.3 في Blackboard

1. من لوحة المسؤول في Blackboard، حدد **موفري أدوات LTI**.
2. حدد **Register LTI 1.3 Tool**.
3. في حقل "معرف العميل"، اكتب هذا المعرف أو انسخه والصقه: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

   > [!NOTE]
   > ستؤدي إضافة معرف العميل هذا إلى تكوين موضعين مختلفين في Blackboard: واحد يسمح بالوصول إلى الأداة من سوق المحتوى والكتب والأدوات ومحرر النص المنسق، وآخر يسمح بالوصول إلى الأداة من القائمة "إضافة محتوى" في الدورة التدريبية عبر الإنترنت للدورات التدريبية الفائقة.

4. حدد **"إرسال**".
5. راجع كافة الإعدادات التي تم ملؤها مسبقا في طريقة عرض **"حالة الأداة**"، وتأكد من أن الزر "تمت **الموافقة****" على "حالة الأداة**" المحدد.
6. في **نهج المؤسسة**، حدد **الدور في الدورة التدريبية** وعلب اختيار **الاسم** في حقول المستخدم لإرسالها. تعد جميع حقول المستخدمين الأخرى اختيارية، ولكن يوصى بتركها للتحقق من تثبيت OneDrive في المستقبل.
7. **السماح بالوصول إلى خدمة الدرجات** **والسماح بالوصول إلى خدمة العضوية** اختياري أيضا في هذا الوقت ولكن قد يكون مطلوبا للتحديثات المستقبلية لأداة LTI.
8. نسخ **معرف النشر**. ستحتاج إليها لتكوين أداة Microsoft LTI.
9. حدد الزر **"إرسال** " للإنهاء.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>تكوين أداة Microsoft LTI للعمل مع Blackboard

1. سجل الدخول إلى [مدخل تسجيل Microsoft OneDrive LTI](https://onedrivelti.microsoft.com/admin).
2. حدد الزر " **موافقة المسؤول** " واقبل الأذونات.

> [!CAUTION]
> إذا لم يتم تنفيذ هذه الخطوة، فإن الخطوة التالية ستعطيك خطأ، ولن تتمكن من اتخاذ هذه الخطوة لمدة ساعة بمجرد حصولك على الخطأ.

3. حدد الزر **"إنشاء مستأجر LTI جديد** ".
4. في صفحة تسجيل LTI، اختر **Blackboard** من القائمة المنسدلة LTI Consumer Platform، ثم حدد الزر **"التالي** ".
5. الصق **معرف النشر** الذي نسخته أثناء تسجيل الأداة في Blackboard وحدد **"التالي**".
6. راجع التغييرات واحفظها. سيتم عرض رسالة عند التسجيل الناجح.
7. يمكن أيضا مراجعة تفاصيل التسجيل عن طريق تحديد الزر **View LTI Tenants** على الصفحة الرئيسية.

بعد إكمال هذه الخطوات، سيتمكن المعلمون من فتح المستندات من OneDrive عند استخدامهم قائمة "علامة الجمع" في صفحة "محتوى الدورة التدريبية".

## <a name="recommended-content"></a>المحتوى الموصى به

[تكاملات Microsoft ل Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[تكامل فئات Microsoft Teams](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
