---
title: إعداد eDiscovery (Premium) في Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: تصف هذه المقالة كيفية إعداد eDiscovery (Premium) حتى تتمكن من البدء في إنشاء الحالات وإدارتها. كما يصف اشتراكات Microsoft المطلوبة والترخيص. بعد إكمال بعض الخطوات السريعة، تصبح أداة eDiscovery (Premium) جاهزة للاستخدام.
ms.openlocfilehash: b23203d374b7ecf2f447c2f6b906345537ec6cf4
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092404"
---
# <a name="set-up-microsoft-purview-ediscovery-premium"></a>إعداد Microsoft Purview eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

يوفر Microsoft Purview eDiscovery (Premium) سير عمل شامل للاحتفاظ بالبيانات التي تستجيب للتحقيقات الداخلية والخارجية لمؤسستك وجمعها ومراجعتها وتحليلها وتصديرها. لا توجد حاجة لنشر eDiscovery (Premium)، ولكن هناك بعض المهام الأساسية التي يجب على مسؤول تكنولوجيا المعلومات ومدير eDiscovery إكمالها قبل أن تتمكن مؤسستك من البدء في إنشاء حالات eDiscovery (Premium) واستخدامها لإدارة التحقيقات الخاصة بك.

تناقش هذه المقالة الخطوات التالية اللازمة لإعداد eDiscovery (Premium).

![خطوات لإعداد eDiscovery (Premium).](../media/set-up-advanced-ediscovery.png)

يشمل ذلك ضمان الترخيص المناسب المطلوب للوصول إلى eDiscovery (Premium) وإضافة أمناء إلى الحالات، وتعيين أذونات لفريق التحقيق والشؤون القانونية حتى يتمكنوا من الوصول إلى الحالات وإدارتها.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>الخطوة 1: التحقق من التراخيص المناسبة وتعيينها

يتطلب ترخيص eDiscovery (Premium) اشتراك المؤسسة المناسب والترخيص لكل مستخدم. للحصول على قائمة بمتطلبات الترخيص ل eDiscovery (Premium)، راجع [الاشتراكات والترخيص](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>الخطوة 2: تعيين أذونات eDiscovery

للوصول إلى eDiscovery (Premium) أو إضافته كعضو في حالة eDiscovery (Premium)، يجب تعيين الأذونات المناسبة للمستخدم. على وجه التحديد، يجب إضافة مستخدم كعضو في مجموعة دور eDiscovery Manager في مدخل توافق Microsoft Purview. يمكن لأعضاء مجموعة الأدوار هذه إنشاء حالات eDiscovery (Premium) وإدارتها. يمكنهم إضافة الأعضاء وإزالتها، ووضع أمناء الاحتجاز ومواقع المحتوى قيد الاحتجاز، وإدارة إعلامات الاحتجاز القانوني، وإنشاء عمليات البحث المقترنة في حالة ما وتحريرها، وإضافة نتائج البحث إلى مجموعة مراجعة، وتحليل البيانات في مجموعة مراجعة، والتصدير والتنزيل من حالة eDiscovery (Premium).

أكمل الخطوات التالية لإضافة مستخدمين إلى مجموعة أدوار eDiscovery Manager:

1. انتقل إلى <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">مدخل التوافق</a> وسجل الدخول باستخدام بيانات الاعتماد لحساب مسؤول في مؤسستك Microsoft 365.

2. في صفحة **الأذونات** ، حدد مجموعة أدوار **eDiscovery Manager** .

3. في صفحة القائمة المنبثقة eDiscovery Manager، انقر فوق **"تحرير"** إلى جانب قسم **eDiscovery Manager** .

4. في الصفحة **"اختيار eDiscovery Manager"** في معالج تحرير مجموعة الأدوار، انقر فوق **"اختيار eDiscovery Manager**".

5. انقر فوق **"إضافة** "، ثم حدد خانة الاختيار لكافة المستخدمين الذين تريد إضافتهم إلى مجموعة الأدوار.

6. انقر فوق **"إضافة"** لإضافة المستخدمين المحددين، ثم انقر فوق **"تم**".

7. انقر فوق **"حفظ"** لإضافة المستخدمين إلى مجموعة الأدوار، ثم انقر فوق **"إغلاق"** لإكمال الخطوة.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>مزيد من المعلومات حول مجموعة أدوار eDiscovery Manager

هناك مجموعتان فرعيتان في مجموعة دور eDiscovery Manager. ويستند الفرق بين هذه المجموعات الفرعية إلى النطاق.

- **eDiscovery Manager**: يمكنه عرض وإدارة حالات eDiscovery (Premium) التي يقومون بإنشائها أو عضو فيها. إذا أنشأت إدارة eDiscovery أخرى حالة ولكنها لا تضيف eDiscovery Manager ثانية كعضو في هذه الحالة، فلن تتمكن إدارة eDiscovery الثانية من عرض الحالة أو فتحها على صفحة eDiscovery (Premium) في مركز الامتثال. بشكل عام، يمكن إضافة معظم الأشخاص في مؤسستك إلى المجموعة الفرعية eDiscovery Manager.

- **مسؤول eDiscovery**: يمكنه تنفيذ جميع مهام إدارة الحالة التي يمكن أن يقوم بها مدير eDiscovery. بالإضافة إلى ذلك، يمكن لمسؤول eDiscovery:

  - عرض كافة الحالات المدرجة في صفحة eDiscovery (Premium).
  
  - إدارة أي حالة في المؤسسة بعد أن يضيفوا أنفسهم كعضو في الحالة.

  - الوصول إلى بيانات الحالة وتصديرها لأي حالة في المؤسسة.

  نظرا للنطاق الواسع للوصول، يجب أن يكون لدى المؤسسة عدد قليل من المسؤولين الذين هم أعضاء في المجموعة الفرعية لمسؤولي eDiscovery.

لمزيد من المعلومات حول أذونات eDiscovery ووصف لكل دور تم تعيينه إلى مجموعة أدوار eDiscovery Manager، راجع [تعيين أذونات eDiscovery](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-ediscovery-premium"></a>الخطوة 3: تكوين الإعدادات العمومية ل eDiscovery (Premium)

الخطوة الأخيرة التي يجب إكمالها قبل أن يبدأ الأشخاص في مؤسستك في إنشاء الحالات واستخدامها هي تكوين الإعدادات العمومية التي تنطبق على جميع الحالات في مؤسستك. في هذا الوقت، يكون الإعداد العمومي الوحيد هو *الكشف عن امتيازات الوكيل والعميل* (ستتوفر المزيد من الإعدادات العمومية في المستقبل). يمكن هذا الإعداد نموذج امتياز الوكيل والعميل من التشغيل عند تحليل البيانات في مجموعة مراجعة. يستخدم النموذج التعلم الآلي لتحديد احتمال احتواء المستند على محتوى قانوني بطبيعته. كما يقارن المشاركين في المستندات بقائمة الوكلاء (التي ترسلها عند إعداد النموذج) لتحديد ما إذا كان للمستند مشارك واحد على الأقل وهو وكيل.

لمزيد من المعلومات حول إعداد نموذج الكشف عن امتيازات الوكيل والعميل واستخدامه، راجع [إعداد الكشف عن امتيازات الوكيل والعميل في eDiscovery (Premium).](attorney-privilege-detection.md)

> [!NOTE]
> هذه خطوة اختيارية يمكنك تنفيذها في أي وقت. لا يمنعك عدم تنفيذ نموذج الكشف عن امتيازات الوكيل والعميل من إنشاء حالات eDiscovery (Premium) واستخدامها.

## <a name="next-steps"></a>الخطوات التالية

بعد إعداد eDiscovery (Premium)، تصبح جاهزا [لإنشاء حالة](create-and-manage-advanced-ediscoveryv2-case.md).