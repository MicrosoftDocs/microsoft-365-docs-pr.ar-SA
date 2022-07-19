---
title: دمج فصول Microsoft Teams واجتماعاته مع Moodle
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
description: إنشاء فصول واجتماعات Teams وإدارتها باستخدام إمكانية التشغيل التفاعلي لأدوات التعلم من Microsoft OneDrive ل Moodle.
ms.openlocfilehash: da65874516dcf196ac91ecea1acc75e3cb719f58
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/13/2022
ms.locfileid: "66857400"
---
# <a name="integrate-microsoft-teams-classes-and-meetings-within-moodle"></a>دمج فصول Microsoft Teams واجتماعاته داخل Moodle

يوفر هذا الدليل خطوات مسؤول تكنولوجيا المعلومات لتسجيل كل من تطبيقات Teams Classes وTeams Meetings LTI على Moodle.

للحصول على تفاصيل حول إدارة جميع تطبيقات LTI لأي LMS، راجع [إدارة بوابة Microsoft LMS لأي LMS](manage-microsoft-one-lti.md).

## <a name="prerequisites-before-set-up"></a>المتطلبات الأساسية قبل الإعداد

لكي يعمل التكامل بين Moodle وTeams بشكل صحيح، يجب إعداد Moodle وTeams للتواصل مع بعضهما البعض.

اتبع [الإرشادات لتثبيت المكون الإضافي Moodle وتكوينه](moodle-plugin-configuration.md).

## <a name="register-microsoft-teams-lti-for-use-in-moodle"></a>تسجيل Microsoft Teams LTI للاستخدام في Moodle

> [!IMPORTANT]
> يجب أن يكون الشخص الذي يقوم بهذا التكامل مسؤول Moodle ومسؤول مستأجر Microsoft 365.

1. تفضل بزيارة [بوابة Microsoft LMS](https://lti.microsoft.com/) وحدد زر **مدخل التسجيل Go إلى** .

2. سجل الدخول باستخدام حساب مسؤول Microsoft 365.

3. بعد تسجيل الدخول، حدد **"إضافة تسجيل جديد**".

4. حدد إما **LTI لاجتماعات Teams** أو **LTI لصفوف Teams** للتسجيل ثم حدد **"التالي**".

5. أدخل اسم **تسجيل** يمكن التعرف عليه بسهولة وحدد **Moodle** كمنصة LMS. حدد **التالي**.

6. سيتم منحك قائمة المفاتيح التي تحتاج إلى إضافتها إلى موقع Moodle الخاص بك.

7. افتح Moodle في علامة تبويب أخرى. لا تغلق علامة تبويب بوابة Microsoft LMS.

8. في Moodle، انتقل إلى **وحدات** >  نشاط نشاط إدارة **الموقع** >  >  للأدوات  >  الخارجية **التي تدير الأدوات**.

9. في صفحة **إدارة الأدوات** ، حدد **تكوين أداة يدويا**.

10. ضمن **إعدادات الأداة**، أدخل **اسم أداة** مثل **فئات Microsoft Teams**. بالنسبة **لإصدار LTI**، حدد **LTI 1.3**. بالنسبة **لنوع المفتاح العام**، حدد **عنوان URL لمجموعة المفاتيح**.

11. بعد ذلك، انسخ المفاتيح من **مفاتيح Microsoft LTI** إلى إدخالات الأدوات المقابلة.
    1. ينتقل مفتاح **URL للارتباط الهدف** من Microsoft إلى حقل URL الخاص **بأداة** Moodle.
    1. ينتقل مفتاح **URL لاتصال معرف Open ID** من Microsoft إلى حقل **URL لتسجيل الدخول إلى** Moodle.
    1. ينتقل مفتاح **URL لإعادة توجيه** Microsoft إلى حقل **(URI) لإعادة التوجيه في** Moodle.

12. حدد **"حفظ التغييرات**".

13. يجب أن تظهر الأداة الجديدة الآن في قسم **الأدوات** في صفحة **أدوات إدارة** Moodle. حدد أيقونة القائمة لعرض **تفاصيل تكوين الأداة**.

14. Go back إلى علامة تبويب بوابة Microsoft LMS. حدد **"التالي**" للانتقال إلى خطوة **مفاتيح التسجيل المتوفرة في LMS**.

15. انسخ القيم والصقها من **تفاصيل تكوين أداة** Moodle إلى خطوة **مفاتيح التسجيل المقدمة من Microsoft LMS** .

  الصق القيم كما يلي:

  | في موديل | على مدخل تسجيل Microsoft LTI |
  | --------- | ------------------------------------ |
  | معرف النظام الأساسي | URL معرف المصدر |
  | معرف العميل | معرف العميل |
  | معرف النشر | معرف النشر |
  | URL مجموعة المفاتيح العامة | URL مجموعة المفاتيح |
  | URL الرمز المميز للوصول | URL الرمز المميز للوصول |
  | URL طلب المصادقة | URL مصادقة النظام الأساسي |

  حدد **التالي**.

16. راجع صفحة **المراجعة والإضافة** . إذا لم تكن هناك أخطاء، فحدد **"حفظ" و"إنهاء**". يجب أن تشاهد رسالة تشير إلى التسجيل الناجح.

لقد أكملت تسجيل إما تطبيق LTI لصفوف Teams أو اجتماعات Teams.

إذا كنت ترغب في إضافة التطبيق الآخر أيضا، فكرر الخطوات المذكورة أعلاه، وحدد تطبيق Teams LTI الآخر في الخطوة 4.

### <a name="add-teams-lti-apps-to-educators-moodle-courses"></a>إضافة تطبيقات Teams LTI إلى دورات Moodle للمعلمين

بعد تسجيل تطبيقات Teams LTI، يمكن للمعلمين إضافة تطبيق Teams Classes وتطبيق اجتماعات Teams إلى دوراتهم التدريبية في Moodle.

- [إرشادات المعلم حول إضافة تطبيق Teams Classes](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-ac6a1e34-32f7-45e6-b83e-094185a1e78a).
- [إرشادات المعلم حول إضافة تطبيق اجتماعات Teams](https://support.microsoft.com/topic/use-microsoft-teams-meetings-in-your-lms-11b6095d-f90b-42b9-ab77-4dcff2bb3b76).

## <a name="technical-requirements-to-launch-teams-lti-apps"></a>المتطلبات التقنية لتشغيل تطبيقات Teams LTI

لبدء تشغيل تطبيقات Teams LTI داخل Moodle، هناك بعض المتطلبات التقنية التي يجب تلبيتها.

> [!NOTE]
> يمكن لمسؤولي تكنولوجيا المعلومات والمعلمين تسجيل تطبيقات LTI على مدخل تسجيل تطبيقات LTI.

### <a name="it-admin-technical-requirements"></a>المتطلبات التقنية لمسؤول تكنولوجيا المعلومات

- استخدم إصدار Moodle 3.10 أو أعلى.
- قم بتنزيل أحدث مكون إضافي من Microsoft O365 لإصدار Moodle 3.10 أو إصدار أحدث.
- الوصول إلى مدخل تسجيل تطبيقات LTI لتسجيل تطبيقات LTI.
  - يجب أن يكون التسجيل قيد الانتهاء على جهاز سطح المكتب.
- قم بتنزيل أحدث إصدار من Microsoft Edge أو Google Chrome أو Safari أو Mozilla Firefox.

### <a name="educator-technical-requirements"></a>المتطلبات التقنية للمعلم

- الوصول إلى مدخل تسجيل تطبيقات LTI لتسجيل تطبيقات LTI، إذا لم يقم مسؤول تكنولوجيا المعلومات بتسجيل التطبيقات.
  - يجب أن يكون التسجيل قيد الانتهاء على جهاز سطح المكتب.
- قم بتنزيل أحدث إصدار من Microsoft Edge أو Google Chrome أو Safari أو Mozilla Firefox.
- [تطبيقات Teams LTI للصفوف والاجتماعات في Moodle](#add-teams-lti-apps-to-educators-moodle-courses).

### <a name="student-technical-requirements"></a>المتطلبات التقنية للطالب

- تطبيقات Teams LTI للصفوف والاجتماعات في Moodle.
  - لا يحتاج الطلاب إلى اتخاذ أي إجراءات لإضافة تطبيقات LTI لصفوف Teams أو اجتماعاتها.
