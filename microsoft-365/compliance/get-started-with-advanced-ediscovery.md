---
title: إعداد Advanced eDiscovery في Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: تصف هذه المقالة كيفية إعداد Advanced eDiscovery بحيث يمكنك بدء إنشاء الحالات وإدارتها. كما يصف أيضا اشتراكات Microsoft والترخيص المطلوبين. بعد إكمال بضع خطوات سريعة، Advanced eDiscovery الأداة جاهزة للاستخدام.
ms.openlocfilehash: cf2d7c6bc770dd6125777c895771b3b61c8ee593
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/04/2021
ms.locfileid: "63567810"
---
# <a name="set-up-microsoft-365-advanced-ediscovery"></a>إعداد Microsoft 365 Advanced eDiscovery

Advanced eDiscovery في Microsoft 365 سير عمل شامل للمحافظة على البيانات المستجيبة والاستعراضات الداخلية والخارجية في مؤسستك وجمعها ومراجعتها وتحليلها وتصديرها. لا حاجة إلى نشر Advanced eDiscovery، ولكن هناك بعض المهام الأساسية التي يجب على مسؤول المعلومات ومدير eDiscovery إكمالها قبل أن تتمكن مؤسستك من بدء إنشاء حالات Advanced eDiscovery واستخدامها لإدارة عمليات البحث.

تناقش هذه المقالة الخطوات التالية الضرورية لإعداد Advanced eDiscovery.

![خطوات لإعداد Advanced eDiscovery.](../media/set-up-advanced-ediscovery.png)

يشمل ذلك ضمان الترخيص المناسب المطلوب للوصول إلى Advanced eDiscovery وإضافه وكلاء إلى الحالات، وتعيين الأذونات إلى فريق التحقيق القانوني لكي يتمكنوا من الوصول إلى الحالات وإدارتها.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>الخطوة 1: التحقق من التراخيص المناسبة وتعيينها

يتطلب ترخيص Advanced eDiscovery اشتراك المؤسسة المناسب والترخيص لكل مستخدم. للحصول على قائمة بمتطلبات الترخيص Advanced eDiscovery، راجع [الاشتراكات والترخيص](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>الخطوة 2: تعيين أذونات eDiscovery

للوصول إلى Advanced eDiscovery أو إضافته كعضو في Advanced eDiscovery، يجب تعيين الأذونات المناسبة للمستخدم. بشكل خاص، يجب إضافة مستخدم كعضو في مجموعة دور مدير eDiscovery في مركز التوافق في Microsoft 365. يمكن لأعضاء مجموعة الدور هذه إنشاء Advanced eDiscovery الحالات وإدارتها. ويمكنهم إضافة الأعضاء وإزالته، وحجز مواقع المحتويات والمدبرات، وإدارة إعلامات الاحتجاز القانوني، وإنشاء عمليات البحث المقترنة في حالة ما وتحريرها، وإضافة نتائج البحث إلى مجموعة مراجعة، وتحليل البيانات في مجموعة مراجعات، وتصديرها وتنزيلها من Advanced eDiscovery أخرى.

أكمل الخطوات التالية لإضافة مستخدمين إلى مجموعة دور eDiscovery Manager:

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">مركز التوافق في Microsoft 365</a> تسجيل الدخول باستخدام بيانات الاعتماد لحساب مسؤول في Microsoft 365 مؤسستك.

2. في صفحة **الأذونات** ، حدد مجموعة الدور **eDiscovery Manager** .

3. في صفحة منتدي eDiscovery Manager، انقر  فوق تحرير بجانب **القسم eDiscovery Manager**.

4. في الصفحة **اختيار eDiscovery Manager** في معالج مجموعة تحرير الدور، انقر **فوق اختيار إدارة eDiscovery**.

5. انقر **فوق** إضافة ثم حدد خانة الاختيار لكل المستخدمين الذين تريد إضافتهم إلى مجموعة الدور.

6. انقر **فوق** إضافة لإضافة المستخدمين المحددين، ثم انقر فوق **تم**.

7. انقر **فوق** حفظ لإضافة المستخدمين إلى مجموعة الدور، ثم انقر فوق **إغلاق** لإكمال الخطوة.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>مزيد من المعلومات حول مجموعة دور eDiscovery Manager

توجد مجموعتان فرعتان في مجموعة دور eDiscovery Manager. يستند الفرق بين هذه المجموعات الفرعية إلى النطاق.

- **eDiscovery Manager**: يمكنه عرض وإدارة Advanced eDiscovery التي أنشأها أو هي عضو فيها. إذا أنشأ مدير eDiscovery آخر حالة ولكنه لم يضيف eDiscovery Manager ثان كعضو في هذه الحالة، فلن يتمكن مدير eDiscovery الثاني من عرض الحالة أو فتحها على صفحة Advanced eDiscovery في مركز التوافق. بشكل عام، يمكن إضافة معظم الأشخاص في مؤسستك إلى المجموعة الفرعية eDiscovery Manager.

- **مسؤول eDiscovery**: يمكنه تنفيذ كل مهام إدارة الحالات التي يمكن لمدير eDiscovery تنفيذها. بالإضافة إلى ذلك، يمكن لمسؤول eDiscovery:

  - عرض كل الحالات المدرجة في Advanced eDiscovery الصفحة.
  
  - يمكنك إدارة أي حالة في المؤسسة بعد إضافتها كعضو في الدعوى.

  - الوصول إلى بيانات حالة الاتصال وتصديرها لأي حالة في المؤسسة.

  نظرا لنطاق الوصول الواسع، يجب أن يكون لدى المؤسسة عدد قليل من المسؤولين الأعضاء في مجموعة مسؤولي eDiscovery الفرعية.

لمزيد من المعلومات حول أذونات eDiscovery ووصفا لكل دور تم تعيينه إلى مجموعة دور eDiscovery Manager، راجع تعيين أذونات [eDiscovery](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>الخطوة 3: تكوين الإعدادات Advanced eDiscovery

الخطوة الأخيرة التي يجب إكمالها قبل أن يبدأ الأشخاص في مؤسستك بإنشاء حالات واستخدامها هي تكوين الإعدادات العالمية التي تنطبق على كل الحالات في مؤسستك. في الوقت نفسه، يكون الإعداد العام الوحيد هو الكشف عن امتيازات المحامي *والعميل* (سيتوفر المزيد من الإعدادات العامة في المستقبل). يمكن هذا الإعداد نموذج امتياز المحامي والعميل من التشغيل عند تحليل البيانات في مجموعة مراجعة. يستخدم النموذج التعلم الآلي لتحديد احتمال احتواء المستند على محتوى قانوني بطبيعته. كما تقارن أيضا بين المشاركين في المستندات وقائمة المحامي (التي ترسلها عند إعداد النموذج) لتحديد ما إذا كان هناك مشارك واحد على الأقل في المستند كمحام.

لمزيد من المعلومات حول إعداد نموذج الكشف عن امتيازات المحامي والعميل واستخدامه، راجع إعداد الكشف عن امتيازات المحامي [والعميل في](attorney-privilege-detection.md) Advanced eDiscovery.

> [!NOTE]
> هذه خطوة اختيارية يمكنك تنفيذها في أي وقت. لا يمنعك عدم تنفيذ نموذج الكشف عن امتيازات المحامي والعميل من إنشاء Advanced eDiscovery الحالات.

## <a name="next-steps"></a>الخطوات التالية

بعد إعداد Advanced eDiscovery، تكون جاهزا [لإنشاء حالة.](create-and-manage-advanced-ediscoveryv2-case.md)