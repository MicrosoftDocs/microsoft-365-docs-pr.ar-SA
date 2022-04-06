---
title: تكامل Microsoft OneDrive LTI مع Blackboard
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
description: يمكنك إنشاء تعيينات الدرجات وإنشاء محتوى الدورة التدريبية وتكليفها والتعاون في العمل على الملفات في الوقت الحقيقي باستخدام Microsoft OneDrive Learning أدوات التشغيل التفاعلي ل Blackboard.
ms.openlocfilehash: 94e77181244bbf02115bd706e86751a9382b906b
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/09/2022
ms.locfileid: "63705293"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>تكامل Microsoft OneDrive LTI مع Blackboard

تكامل Microsoft OneDrive LTI مع Blackboard عملية من خطوتين. توفر الخطوة الأولى Microsoft OneDrive LTI في دورات Blackboard التدريبية، والخطوة الثانية Microsoft OneDrive ل Blackboard.

> [!IMPORTANT]
> يجب أن يكون الشخص الذي ينفذ هذا التكامل مسؤولا عن Blackboard ومسؤولا عن Microsoft 365 المستأجر.

## <a name="recommended-browser-settings"></a>إعدادات المستعرض المستحسنة

- يجب السماح ب ملفات تعريف الارتباط Microsoft OneDrive.
- يجب عدم حظر النوافذ المنبثقة Microsoft OneDrive.

> [!NOTE]
>
> - لا يسمح بملفات تعريف الارتباط بشكل افتراضي في وضع التصفح المتخفي في مستعرض Chrome، وستحتاج إلى السماح بها.
> - Microsoft OneDrive LTI في الوضع الخاص في Microsoft Edge المستعرض. تأكد من أنك لم تقم بحظر ملفات تعريف الارتباط (المسموح بها بشكل افتراضي).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>تسجيل أداة OneDrive LTI 1.3 في Blackboard

1. من لوحة المسؤول في Blackboard، حدد  **موفرو أدواتLTI**.
2. حدد  **أداة تسجيل LTI 1.3**.
3. في الحقل "الم ID العميل"، اكتب هذا الملصق أو انسخه واللصق فيه: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

  > [!NOTE]
  > ستكوين إضافة "معر ة العميل" هذه موضعين مختلفين في Blackboard: واحد يسمح بالوصول إلى الأداة من سوق المحتويات والكتب والأدوات ومحرر النص Rich، وآخر يسمح بالوصول إلى الأداة من القائمة إضافة محتوى في الدورة التدريبية عبر الإنترنت الخاصة بال الدورات التدريبية ل Ultra.

4. حدد **إرسال**.
5. راجع كل الإعدادات التي تم ملءها مسبقا في "عرض  **حالةTool** "، وتأكد من أن الزر "حالة الأداة" المحدد تم  **رفضه**.
6.  **InInstitution Policies**, select the **Role in course** and the **Name checkboxes** in the user fields to send. كل حقول المستخدمين الأخرى اختيارية، ولكن من المستحسن تركها في إثبات OneDrive تثبيتك.
7. **السماح بالوصول إلى خدمة الدرجات**  كما  **أن إمكانية الوصول إلى خدمة** العضوية هي أيضا اختيارية في الوقت نفسه ولكنها قد تكون مطلوبة للتحديثات المستقبلية لأداة LTI.
8. انسخ **"معر ة النشر**". ستحتاج إليها لتكوين أداة Microsoft LTI.
9. حدد الزر **إرسال** للانتهاء.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>تكوين أداة Microsoft LTI للعمل مع Blackboard

1. سجل دخولك إلى Microsoft OneDrive [تسجيل LTI](https://onedrivelti.microsoft.com/admin).
2. حدد زر **موافقة المسؤول** واقبل الأذونات.

> [!CAUTION]
> إذا لم يتم تنفيذ هذه الخطوة، ستعرض لك الخطوة التالية رسالة خطأ، ولن تتمكن من تنفيذ هذه الخطوة لمدة ساعة واحدة بمجرد أن تحصل على الخطأ.

3. حدد الزر **إنشاء مستأجر LTI** جديد.
4. في صفحة تسجيل LTI، اختر **Blackboard** من القائمة المنسدلة النظام الأساسي للمستهلكين ل LTI، ثم حدد **الزر التالي** .
5. قم **بلصق "اسم النشر"** الذي نسخته أثناء تسجيل الأداة في Blackboard وحدد **التالي**.
6. راجع التغييرات واحفظها. سيتم عرض رسالة عند التسجيل بنجاح.
7. يمكن أيضا مراجعة تفاصيل التسجيل عن طريق تحديد الزر عرض **مستأجري LTI** على الصفحة الرئيسية.

بعد إكمال هذه الخطوات، سيكون المعلمون قادرين على فتح المستندات من OneDrive عند استخدامهم قائمة "علامة ضافة" في صفحة محتوى الدورة التدريبية.

## <a name="recommended-content"></a>المحتوى المستحسن

[عمليات تكامل Microsoft ل Blackboard](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[Microsoft Teams الفئات](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
