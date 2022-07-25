---
title: دمج فئات Microsoft Teams واجتماعات تطبيقات LTI مع Desire2Learn Brightspace LMS
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-modern-desktop
- m365initiative-edu
ms.localizationpriority: medium
description: إنشاء وإدارة فصول Teams والاجتماعات باستخدام إمكانية التشغيل التفاعلي ل Microsoft Learning Tools (LTI) ل Desire2Learn (D2L) Brightspace LMS.
ms.openlocfilehash: c3d551fcdc866c08437564addb1cd3cb9b144a75
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/21/2022
ms.locfileid: "66988345"
---
# <a name="integrate-microsoft-teams-classes-and-meetings-lti-apps-within-desire2learn-brightspace-lms"></a>دمج فئات Microsoft Teams والاجتماعات في تطبيقات LTI ضمن Desire2Learn Brightspace LMS

يوفر هذا الدليل خطوات مسؤول تكنولوجيا المعلومات لتسجيل كل من Teams Classes وتطبيقات Teams Meetings LTI ل Desire2Learn (D2L) Brightspace LMS.

للحصول على تفاصيل حول إدارة جميع تطبيقات LTI لأي LMS، راجع [إدارة بوابة Microsoft LMS لأي LMS](manage-microsoft-one-lti.md).

الخطوات الأساسية لدمج تطبيقات Teams LTI و Brightspace هي:

1. [المتطلبات الأساسية قبل التكامل](#prerequisites-before-integration).
1. [تسجيل Microsoft LTI للاستخدام في Brightspace](#register-microsoft-teams-lti-for-use-in-brightspace).
1. [نشر تطبيقات Microsoft LTI إلى Brightspace](#deploy-the-microsoft-lti-apps-to-brightspace).
1. [إضافة ارتباطات تطبيق Teams LTI إلى Brightspace للمعلمين](#add-teams-lti-app-links-to-educators-brightspace).

## <a name="prerequisites-before-integration"></a>المتطلبات الأساسية قبل التكامل

لكي يعمل التكامل بين D2L Brightspace وTeams بشكل صحيح، يجب إعداد Brightspace وTeams للتواصل مع بعضهما البعض.

1. لكي تعمل فصول Teams، تحتاج إلى تثبيت **Brightspace Course Connector** وتكوينه بشكل صحيح. اتبع [هذه الخطوات لتثبيت الموصل على حساب Brightspace الخاص بك](https://community.brightspace.com/s/article/Getting-started-with-Brightspace-Course-Connector-for-Microsoft-Teams).

   > [!NOTE]
   > حدد **"فريق الفصل"** **لنوع التكامل** عند إعداد الموصل لضمان التوافق مع أدوات Teams LTI.

2. ستعمل اجتماعات Teams بدون موصل الدورة التدريبية. ومع ذلك، لن تتوفر بعض الميزات مثل **إضافة فئة بأكملها** . نوصي بتثبيت **Brightspace Course Connector** لتطبيق Teams Meetings LTI.

## <a name="register-microsoft-teams-lti-for-use-in-brightspace"></a>تسجيل Microsoft Teams LTI للاستخدام في Brightspace

1. تفضل بزيارة [بوابة Microsoft LMS](https://lti.microsoft.com/) وحدد زر **"Go to Registration Portal** ".

2. سجل الدخول باستخدام *حساب مسؤول Microsoft 365*.

3. بعد تسجيل الدخول، حدد **"إضافة تسجيل جديد**".

4. حدد إما **LTI لاجتماعات Teams** أو **LTI لصفوف Teams** للتسجيل ثم حدد **"التالي**".

5. أدخل اسم **تسجيل** يمكن التعرف عليه بسهولة وحدد **D2L Brightspace** كمنصة LMS. حدد **التالي**.

6. سيتم منحك قائمة المفاتيح التي تحتاج إلى إضافتها إلى موقع Brightspace LMS.

7. افتح موقع Brightspace في علامة تبويب أخرى. لا تغلق علامة تبويب بوابة Microsoft LMS.

8. في موقع Brightspace، انتقل إلى **إمكانية توسعة مسؤول** >  **Manage** وحدد **LTI Advantage** ثم **تسجيل الأداة**.

9. حدد **التسجيل القياسي** وانسخ المفاتيح من **مفاتيح Microsoft LTI** إلى إدخالات الأداة المقابلة.
    1. ينتقل مفتاح **URL للارتباط الهدف** من Microsoft إلى حقل **URI للارتباط الهدف** ل Brightspace.
    1. ينتقل مفتاح **URL لاتصال معرف Open ID** من Microsoft إلى حقل **عنوان URL لتسجيل الدخول إلى OpenID Connect** في Brightspace.
    1. ينتقل مفتاح **عنوان URL لإعادة توجيه** Microsoft إلى حقل عناوين **URL لإعادة توجيه** Brightspace.

10. في الحقل **Domain** ، أدخل `https://teams.microsoft.com`.

11. حدد الزر **"تسجيل** ".

12. سيعرض نموذج تفاصيل تسجيل Brightspace. يجب إضافة هذه القيم على بوابة Microsoft LMS.

13. في علامة تبويب **بوابة Microsoft LMS** ، حدد **مفاتيح التسجيل المتوفرة في LMS**.

14. انسخ القيم والصقها من تفاصيل تكوين Brightspace إلى خطوة **مفاتيح التسجيل المتوفرة في Microsoft LMS** .

    الصق القيم كما يلي:

    | على Brightspace                         | على مدخل تسجيل Microsoft LTI |
    | -------------------------------------- | ------------------------------------ |
    | المصدر                                 | URL معرف المصدر                        |
    | معرف العميل                              | معرف العميل                            |
    | عنوان URL لمجموعة مفاتيح Brightspace                 | URL مجموعة المفاتيح                           |
    | نقطة نهاية مصادقة OpenID Connect | URL مصادقة النظام الأساسي          |

    حدد **التالي**.

15. راجع صفحة **المراجعة والإضافة** . إذا لم تكن هناك أخطاء، فحدد **"حفظ" و"إنهاء**". يجب أن تشاهد رسالة تشير إلى التسجيل الناجح.

لقد أكملت تسجيل إما تطبيق LTI لصفوف Teams أو اجتماعات Teams.

إذا كنت ترغب في إضافة التطبيق الآخر أيضا، فكرر الخطوات المذكورة أعلاه، وحدد تطبيق Teams LTI الآخر في الخطوة 4.

## <a name="deploy-the-microsoft-lti-apps-to-brightspace"></a>نشر تطبيقات Microsoft LTI إلى Brightspace

بعد تسجيل تطبيقات Microsoft LTI، تحتاج إلى نشر التطبيقات على موقع Brightspace.

إليك الإجراء لإنشاء نشر جديد:

1. في موقع Brightspace، حدد الأداة التي قمت بإنشائها.
2. أدخل اسم نشر.
3. حدد كافة إعدادات الأمان باستثناء **Classlist** و **Anonymous**.
4. لا تقم بتعيين إعدادات التكوين.
5. حدد **"Create Deployment**".

اختر **"وحدات المؤسسة"** التي ترغب في استخدام تطبيق LTI الجديد. حدد **المؤسسة الجذر** أو حدد توابع وحدة المؤسسة الفردية.

## <a name="add-teams-lti-app-links-to-educators-brightspace"></a>إضافة ارتباطات تطبيق Teams LTI إلى Brightspace للمعلمين

بعد إنشاء عملية نشر، ستقوم بإنشاء ارتباط جديد. سيضيف هذا الارتباط تطبيق Microsoft LTI إلى تجربة Brightspace للمعلمين.

1. في موقع Brightspace، حدد التوزيع الذي أنشأته.
2. قم بالتمرير لأسفل وحدد **"عرض الارتباطات**".
3. حدد **ارتباط جديد**.
4. املأ هذه التفاصيل المطلوبة:
    1. الصق **عنوان URL لإعادة التوجيه** من *بوابة Microsoft LMS* في حقل **URL** . يمكن الوصول إلى عنوان URL هذا عن طريق عرض التسجيل على البوابة.
    1. تعيين النوع إلى **"التشغيل الأساسي**".
5. حدد **"حفظ وإغلاق**".

يمكن للمعلم الآن إضافة تطبيق Microsoft LTI عن طريق تحديده في القائمة المنسدلة " **المحتوى الموجود** في Brightspace".
