---
author: LanaChin
ms.author: v-lanachin
ms.date: 03/31/2022
ms.topic: include
audience: admin
ms.service: msteams
ms.openlocfilehash: ab375a876eb62e5f41e5dd7cda3743d4010b95ff
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823624"
---
قبل البدء، تأكد من أن لديك المتطلبات الأساسية التالية:

- Blue Yonder WFM الإصدار 2020.3 أو 2021.1 أو 2021.2.

    > [!NOTE]
    > إذا كان لديك Blue Yonder WFM 2020.3 أو 2021.1، فطبق التصحيح 2020.3.0.4 أو 2021.1.0.3. يعمل هذا التصحيح على إصلاح مشكلة تلقي المستخدمين رسالة خطأ مستمرة في Shifts. كما أنه يصلح مشكلة تمنع المستخدمين من تحديث توفرهم في Shifts.

- اسم حساب خدمة Blue Yonder WFM وكلمة المرور وعناوين URL للخدمة:

    - URL المصادقة الموحدة
    - URL مصادقة ملف تعريف الارتباط
    - URL الخدمة الذاتية للموظف
    - عنوان URL لواجهة برمجة تطبيقات الويب للبيع بالتجزئة
    - URL واجهة برمجة تطبيقات إدارة الموقع
    - عنوان URL لواجهة برمجة تطبيقات الإدارة

    إذا لم تكن لديك هذه المعلومات، فاتصل بدعم Blue Yonder. يتم إنشاء الحساب على مستوى المؤسسة الجذر بواسطة مسؤول مؤسسة Blue Yonder. يجب أن يكون لديه الوصول إلى واجهة برمجة التطبيقات مسؤول العميل والوصول إلى Store Manager. الحساب وكلمة المرور مطلوبان لإنشاء اتصال.
- يتم تمكين مصادقة SSO المتحدة في بيئة WFM Blue Yonder. اتصل بدعم Blue Yonder للتأكد من تمكين تسجيل الدخول الأحادي الموحد. سيحتاجون إلى المعلومات التالية:

    - federatedSSOValidationService: `https://wfmconnector.teams.microsoft.com/api/v1/fedauth/{tenantId}/6A51B888-FF44-4FEA-82E1-839401E9CD74/authorize` حيث {tenantId} هو tenantId الخاص بك
     - proxyHeader: X-MS-AuthToken

- تم إعداد فريق واحد على الأقل في Teams.
- لقد أضفت حساب نظام Microsoft 365 الخاص بك كمالك فريق إلى جميع الفرق التي تريد تعيينها.</br> [أنشئ هذا الحساب في Microsoft 365](/microsoft-365/admin/add-users/add-users) وقم بتعيين ترخيص Microsoft 365 له. بعد ذلك، أضف الحساب كمالك الفريق إلى جميع الفرق التي تريد تعيينها. يستخدم موصل Shifts هذا الحساب عند مزامنة تغييرات Shifts من WFM Blue Yonder.

    نوصي بإنشاء حساب لهذا الغرض تحديدا وعدم استخدام حساب المستخدم الخاص بك.