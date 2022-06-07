---
title: استخدام Microsoft Teams Classes مع Blackboard Learn Ultra
ms.author: danismith
author: cichur
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
description: استخدام Microsoft Teams Classes مع Blackboard Learn Ultra
ms.openlocfilehash: f5e53c54db893a184a5b2afe86b61c823b62f5a6
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923051"
---
# <a name="use-microsoft-teams-classes-with-blackboard-learn-ultra"></a>استخدام Microsoft Teams Classes مع Blackboard Learn Ultra

العمل الجماعي هو جوهر كل مؤسسة حديثة. من خلال تعزيز التعاون، إنها سمة محددة لكل مؤسسة ناجحة. يمكنك تحسين جميع إمكانيات وميزات Blackboard Learn Ultra عن طريق إقرانها بصفوف Microsoft Teams.

قد تتضمن الصفوف محادثات في الوقت الحقيقي أو اجتماعات فيديو أو تفاعلات غير متزامنة. يمكنك إضافة تجارب مشاركة الملفات والتكوين المشترك لطلابك، كل ذلك في مكان واحد. تعيد فصول Microsoft Teams مع Learn Ultra تعريف ديناميكيات التدريس وما يعنيه التعلم الفعال.

> [!IMPORTANT]
> تأكد من إعداد حقل "البريد الإلكتروني للمؤسسة" بنجاح في [نظام معلومات الطلاب (SIS)](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Student_Information_System/SIS_Planning)
>
>يعتمد تكامل فئات Microsoft Teams على حقل البريد الإلكتروني للمؤسسة في SIS الخاص بك لتعيين [اسم مبدأ المستخدم (UPN](/azure/active-directory/hybrid/howto-troubleshoot-upn-changes)) الصحيح ل Microsoft Azure Active Directory. إذا لم يتم توفير أي بريد إلكتروني للمؤسسة، فسيتم تعيين هذا بشكل افتراضي إلى البريد الإلكتروني الموجود. يوصى بتعيين هذا الحقل لكل مستخدم لضمان مزامنة بياناته بشكل صحيح وعدم وجود تعارض في بيانات البريد الإلكتروني بين AAD و Blackboard Learn Ultra.
>
> إذا لم تقم بتعيين هذا الحقل بشكل مناسب في تعيين SIS، فسيستمر التكامل في العمل، ولكن قد لا يظهر المستخدمون في فئات Teams التي تم إنشاؤها، وقد تحدث أخطاء.

## <a name="supporting-institutional-data-mapping--institution-email-sis-field"></a>دعم تعيين البيانات المؤسسية – حقل SIS للبريد الإلكتروني للمؤسسة

كجزء من التطور مع عمليات تكامل موفر السحابة، أنشأ Blackboard Learn Ultra حقل **بريد إلكتروني جديد للمؤسسة** ، في كل من تكامل إطار عمل نظام معلومات الطلاب وواجهات برمجة تطبيقات REST العامة، ما يسمح للمؤسسات بإدارة عملية مزامنة البيانات بشكل فعال بين Blackboard Learn Ultra وAD.

### <a name="what-does-the-institution-email-mean-and-what-does-it-support"></a>ماذا يعني البريد الإلكتروني للمؤسسة وما الذي يدعمه؟

يسمح حقل **"البريد الإلكتروني للمؤسسة** " بتعيينات الحقول المخصصة بين مصادر البيانات المدعومة خارجيا للعميل و Blackboard Learn Ultra. إذا كانت مصادر البيانات عبارة عن موفري سحابة، مثل Microsoft، فإن اسم مبدأ المستخدم (UPN) هو معرف فريد أساسي لكل مستخدم يتكون من بادئة UPN (اسم حساب المستخدم) ولاحقة UPN (اسم مجال DNS) مقترنة برمز @. يؤدي ذلك إلى إنشاء عنوان بريد إلكتروني فريد لكل مستخدم معين داخل Microsoft Azure Active Directory.

لضمان دقة البيانات وتحقيق التسجيلات أو العضويات بين فصول Blackboard Learn Ultra وMicrosoft Teams بشكل صحيح، يجب أن يتطابق عنوان البريد الإلكتروني للمستخدم بين كلا النظامين. في Blackboard Learn Ultra، يمكن للمستخدمين تغيير عنوان البريد الإلكتروني الموجود أو تجاوزه في واجهة المستخدم، مما قد يؤدي إلى حدوث أخطاء في المزامنة وعدم إضافة المستخدم بشكل صحيح إلى فريق الصفوف. يضمن تعيين حقل **"البريد الإلكتروني للمؤسسة** " إمكانية إدارة هذا المستوى من التحقق من الأمان والتحقق من الصحة بشكل صحيح، بغض النظر عما إذا قام المستخدمون بتغيير بريدهم الإلكتروني داخل Blackboard Learn Ultra أم لا.

 عندما يكون عنوانا البريد الإلكتروني مختلفين، إما:

- يجب اتخاذ قرار بشأن المصدر الذي له الأسبقية وسيتم اتخاذه كرسائل بريد إلكتروني للشخص والمؤسسة.
  او
- يمكن للمؤسسة تعيين حقل مخصص في البريد الإلكتروني للمؤسسة، والذي يمكن أن يحل تعارضا محتملا.

يتوفر الآن تعيين حقل **"البريد الإلكتروني للمؤسسة** " لكافة أنواع تكامل SIS الموجودة في **Advanced Configuration Settings** > **Users Learn Object Type** > **Mapping**.

> [!NOTE]
> من المهم ملاحظة أنه بشكل افتراضي، يتم تعيين **البريد الإلكتروني للمؤسسة** إلى **"البريد الإلكتروني** للشخص" لكافة تنسيقات SIS ويجب أن يكون فريدا لكل شخص. ستوضع كافة عمليات التكامل الموجودة التي تم إعدادها وتشغيلها تعيين البيانات هذا في مكانها، حيث سيفشل SIS في استيراد المستخدمين إذا تم تكرار بريدهم الإلكتروني. إذا كانت المؤسسة تتطلب القدرة على تغيير البريد الإلكتروني للمؤسسة إلى **مخصص**، فستحتاج إلى إدارة هذا من خلال **إعدادات التكوين المتقدمة** في SIS.

## <a name="requirements"></a>الاحتياجات

يتوفر تكامل فئات Microsoft Teams **لدورات Ultra Course View فقط**. تحتاج مؤسستك إلى إكمال هذه المتطلبات لاستخدامها:

- تمكين Blackboard Learn Ultra Learn SaaS مع تمكين Ultra Base Navigation

  ![مثال على الميزة ممكن في الدورات التدريبية.](media/feature-availability.png)

- تمكين LTI للاستخدام في الدورات التدريبية.

  أ. انتقل إلى **موفري أدوات LTI** **للوحة** >  المسؤول **الذين يديرون الخصائص العمومية** > .

  ب. حدد **LTI Enabled in Courses**، واختياريا، حدد **Enabled in Organizations**.

  ج. حدد **"إرسال**".

- يجب تكوين LTI

- إضافة Blackboard Learn Ultra Teams Classes LTI Integration

- إضافة أداة LTI 1.3 لصفوف Microsoft Teams

- إضافة أداة واجهة برمجة تطبيقات REST ومشاركة الموارد عبر المنشأ

- تكوين تكامل فئات Microsoft Teams والموافقة عليه

## <a name="add-the-blackboard-learn-ultra-teams-classes-lti-13-tool"></a>إضافة أداة Blackboard Learn Ultra Teams Classes LTI 1.3

1. من **لوحة المسؤول**، حدد **موفري أدوات LTI**.

2. حدد **تسجيل أداة LTI 1.3**.

3. في حقل **"معرف العميل** "، اكتب هذا المعرف أو انسخه والصقه:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. راجع كافة الإعدادات التي تم ملؤها مسبقا وفي **حالة الأداة**، ثم حدد **ممكن**.

5. في **نهج المؤسسة**، حدد **"الدور" في الدورة التدريبية والاسم** **وعنوان البريد الإلكتروني**، ثم حدد **"نعم** " لكليهما.

6. حدد **السماح بالوصول إلى خدمة الدرجات** **والسماح بالوصول إلى خدمة العضوية**.

## <a name="add-the-microsoft-teams-classes-lti-13-tool"></a>إضافة أداة LTI 1.3 لصفوف Microsoft Teams

1. من **لوحة المسؤول**، حدد **موفري أدوات LTI**.

2. حدد **تسجيل أداة LTI 1.3**.

3. في حقل **"معرف العميل** "، اكتب هذا المعرف أو انسخه والصقه:

   `027328b7-c2e3-4c9e-aaa1-07802dae6c89`

4. راجع كافة الإعدادات التي تم ملؤها مسبقا وفي *حالة الأداة* وحدد *ممكن.*

5. في **نهج المؤسسة**، حدد **الدور في الدورة التدريبية والاسم** **وعنوان البريد الإلكتروني**. حدد **"نعم** " لكليهما.

6. حدد **السماح بالوصول إلى خدمة الدرجات** **والسماح بالوصول إلى خدمة العضوية**.

## <a name="add-the-rest-api-tool"></a>إضافة أداة واجهة برمجة تطبيقات REST

1. من **لوحة المسؤول**، انتقل إلى **عمليات التكامل** وحدد **تكاملات Rest API**.

2. حدد **إنشاء تكامل**.

3. في حقل **"معرف التطبيق** "، اكتب هذا المعرف أو انسخه والصقه:

   `f1561daa-1b21-4693-ba90-6c55f1a0eb41`

4. اكتب مستخدما لهذا التكامل.

   سيكون هذا المستخدم هو المستخدم الذي له حق الوصول إلى واجهة برمجة تطبيقات المنزل الذي يرتبط منه التطبيق.

5. حدد **"إرسال**".

## <a name="add-the-cross-origin-resource-sharing"></a>إضافة مشاركة الموارد عبر المنشأ

1. من **لوحة المسؤول**، انتقل إلى **عمليات التكامل** وحدد **Cross-origin Resource Sharing*.

2. حدد **Create Configuration**.

3. في حقل **"الأصل** "، نوع نسخ عنوان URL هذا ولصقه:

   `https://bb-ms-teams-ultra-ext.api.blackboard.com`

4. في الحقل **"الرؤوس المسموح بها** "، اكتب **التخويل**.

5. تعيين **متوفر** إلى **"نعم**".

6. حدد **"إرسال**".

## <a name="configure-and-approve-microsoft-teams-classes-integration"></a>تكوين تكامل فئات Microsoft Teams والموافقة عليه

لدمج مثيل Blackboard Learn Ultra بنجاح مع فئات Microsoft Teams، ستحتاج إلى التأكد من الموافقة على تطبيق Blackboard Learn Ultra للوصول داخل مستأجر Microsoft Azure. هذه عملية يجب إكمالها من قبل مسؤول Microsoft 365 العام في مؤسستك.

يمكن إجراء هذه العملية إما قبل أو بعد تكوين تطبيقات LTI في Blackboard Learn Ultra Instance.

### <a name="before-configuring-the-lti-applications"></a>قبل تكوين تطبيقات LTI

إذا اخترت الموافقة على تطبيق Blackboard Learn Ultra Teams Classes Azure قبل تكوين عمليات تكامل LTI، فستحتاج إلى إعادة التوجيه إلى **نقطة نهاية موافقة مسؤول Microsoft Identity Platform**. يتم عرض عنوان URL:

`https://login.microsoftonline.com/{tenant}/adminconsent?client\_id=2d94989f-457a-47c1-a637-e75acdb11568`

> [!NOTE]
> ستستبدل **{Tenant}** بمعرف مستأجر Microsoft Azure المؤسسي المحدد.

سترى نافذة أذونات توضح أنك تمنح الإذن ل Blackboard Learn Ultra للوصول إلى Microsoft Teams.

![نافذة الأذونات ل Microsoft و Blackboard.](media/permissions1.png)

### <a name="after-configuring-the-lti-applications"></a>بعد تكوين تطبيقات LTI

1. في **لوحة المسؤول**، انتقل إلى **الأدوات والأدوات المساعدة** وحدد **مسؤول تكامل Microsoft Teams**.

2. حدد **تمكين Microsoft Teams**.

3. أضف **معرف مستأجر Microsoft** إلى حقل النص المتوفر.

4. اختر أحد الخيارات التالية:

   - إذا كان التطبيق لديه موافقة مسبقة، فسيظهر علامة اختيار صغيرة. إذا ظهرت علامة الاختيار، فحدد **"إرسال**".

   - إذا لم تتم الموافقة على الموافقة، فاتبع الخطوات الموضحة لإنشاء عنوان URL للموافقة وإرساله إلى مسؤول Microsoft 365 العام للموافقة عليه.

5. بمجرد تأكيد الموافقة، حدد **"إعادة المحاولة** " للتأكيد، ثم حدد **"إرسال**".
