---
title: الأسئلة المتداولة عند تشغيل Microsoft 365 Defender
description: احصل على إجابات للأسئلة الأكثر شيوعا حول الترخيص والأذونات والإعدادات الأولية والمنتجات والخدمات الأخرى المتعلقة بتمكين Microsoft 365 Defender
keywords: الأسئلة المتداولة، الأسئلة المتداولة، سحابة القطاع الحكومي، البدء، تمكين Microsoft 365 Defender، Microsoft 365 Defender، M365، الأمان، موقع البيانات، الأذونات المطلوبة، أهلية الترخيص، صفحة الإعدادات
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 73dddcfc1389eb5bb0b0115f0666c413dc7d2a01
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663193"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>الأسئلة المتداولة عند تشغيل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

اقرأ الإجابات على الأسئلة الأكثر شيوعا حول تشغيل [Microsoft 365 Defender](microsoft-365-defender.md)، بما في ذلك التراخيص والأذونات المطلوبة ونشر خدمات الدعم والإعدادات الأولية.

للحصول على إرشادات حول كيفية تشغيل الخدمة، [اقرأ تشغيل Microsoft 365 Defender](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>ليس لدي ترخيص Microsoft 365 E5. هل يمكنني الاستمرار في استخدام Microsoft 365 Defender؟

يمكن للعملاء الذين لديهم التراخيص غير E5 التالية استخدام Microsoft 365 Defender:

- Microsoft Defender for Endpoint
- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Defender لـ Office 365 (الخطة 2)

للحصول على قائمة كاملة بالتراخيص [المدعومة، اقرأ متطلبات الترخيص](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>هل أحتاج إلى تثبيت أي شيء أو نشره لبدء استخدام Microsoft 365 Defender؟

لا، Microsoft 365 Defender دمج البيانات من خدمات الأمان Microsoft 365 التي قمت بتوزيعها بالفعل. بمجرد تشغيلها، ستبدأ تجارب الحوادث والأتمتة والتتبع في العمل ضمن نطاق المنتجات المنشورة. إذا لم يتم نشر أي من هذه المنتجات بشكل صحيح، فلن يعرض Microsoft 365 Defender أي بيانات ولن يتمكن من اتخاذ أي إجراء.

لتحسين تجاربك Microsoft 365 Defender، نوصي بنشر *جميع* [منتجات وخدمات الأمان Microsoft 365 المدعومة](deploy-supported-services.md).

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>أين Microsoft 365 Defender معالجة البيانات وتخزينها؟

Microsoft 365 Defender يحدد تلقائيا الموقع الأمثل لمركز البيانات حيث تتم معالجة البيانات المجمعة وتخزينها. إذا كان لديك Microsoft Defender لنقطة النهاية، فإنه يحدد نفس الموقع الذي يستخدمه Defender لنقطة النهاية.

>[!NOTE]
>Microsoft Defender لنقطة النهاية التوفير تلقائيا في مراكز بيانات الاتحاد الأوروبي (EU) عند تشغيلها من خلال Microsoft Defender for Cloud. سيتم توفير Microsoft 365 Defender تلقائيا في نفس مركز بيانات الاتحاد الأوروبي للعملاء الذين قاموا بتوفير Microsoft Defender لنقطة النهاية بهذه الطريقة.

يظهر موقع مركز البيانات قبل وبعد توفير الخدمة في صفحة الإعدادات Microsoft 365 Defender (**الإعدادات > Microsoft 365 Defender**). إذا كنت تفضل استخدام موقع مركز بيانات آخر، فحدد **"هل تحتاج إلى مساعدة"؟** في مدخل Microsoft 365 Defender للاتصال بدعم Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>أين يمكنني الوصول إلى Microsoft 365 Defender؟

يتوفر Microsoft 365 Defender في: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>ما هي الأذونات التي أحتاجها للوصول إلى Microsoft 365 Defender؟

يمكن للحسابات المعينة لأدوار Azure Active Directory (Azure AD) التالية الوصول إلى وظائف وبيانات Microsoft 365 Defender:

- المسؤول العام
- مسؤول الأمان
- عامل تشغيل الأمان
- القارئ العمومي
- قارئ الأمان
- مسؤول التوافق
- مسؤول بيانات التوافق
- مسؤول التطبيق
- مسؤول تطبيق السحابة


> [!NOTE]
> تؤثر إعدادات التحكم في الوصول المستندة إلى الدور في Microsoft Defender لنقطة النهاية على الوصول إلى البيانات. لمزيد من المعلومات، اقرأ حول [إدارة الوصول إلى Microsoft 365 Defender](m365d-permissions.md).

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>ما هي المنطقة الزمنية التي Microsoft 365 Defender افتراضيا إليها؟

بشكل افتراضي، يعرض Microsoft 365 Defender معلومات الوقت في المنطقة الزمنية UTC. يمكنك تغيير هذا الإعداد لاستخدام المنطقة الزمنية المحلية. [التعرف على تعيين المنطقة الزمنية](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>كيف يمكنني التعرف على ميزات Microsoft 365 Defender الجديدة وتحديثات واجهة المستخدم؟

توفر Microsoft المعلومات بانتظام من خلال القنوات المختلفة، بما في ذلك:

- [مركز الرسائل](../../admin/manage/message-center.md) في مركز مسؤولي Microsoft 365
- Blogposts في [Microsoft 365 الأمان & مجتمع التكنولوجيا للامتثال](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

احصل على أحدث التجارب المتاحة للجمهور من خلال تشغيل [ميزات المعاينة](preview.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [نظرة عامة على Microsoft 365 Defender](microsoft-365-defender.md)
- [تشغيل Microsoft 365 Defender](m365d-enable.md).
- [متطلبات الترخيص والمتطلبات الأساسية الأخرى](prerequisites.md)
- [نشر الخدمات المعتمدة](deploy-supported-services.md)
- [تشغيل ميزات المعاينة](preview.md)
