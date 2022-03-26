---
title: الأسئلة التي يتم طرحها بشكل متكرر عند تشغيل Microsoft 365 Defender
description: احصل على إجابات على الأسئلة الأكثر شيوعا حول الترخيص والأذونات والإعدادات الأولية والمنتجات والخدمات الأخرى ذات الصلة بتمكين Microsoft 365 Defender
keywords: الأسئلة الشائعة، الأسئلة الشائعة، سحابة القطاع الحكومي، بدء استخدام، تمكين Microsoft 365 Defender، Microsoft 365 Defender، M365، الأمان، موقع البيانات، الأذونات المطلوبة، أهلية الترخيص، صفحة الإعدادات
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
ms.openlocfilehash: e5ed41f400c24a2522ea49f2524d0fe629bdbb9f
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/09/2021
ms.locfileid: "63573854"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>الأسئلة التي يتم طرحها بشكل متكرر عند تشغيل Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**ينطبق على:**
- Microsoft 365 Defender

اقرأ الردود على الأسئلة الأكثر شيوعا حول تشغيل Microsoft 365 Defender، بما في ذلك الأذونات والتراخيص المطلوبة ونشر خدمات الدعم والإعدادات الأولية.[](microsoft-365-defender.md)

للحصول على إرشادات حول كيفية تشغيل الخدمة، [اقرأ تشغيل Microsoft 365 Defender](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>ليس لدي ترخيص Microsoft 365 E5. هل يمكنني استخدام Microsoft 365 Defender؟

يمكن للعملاء الذين يستخدمون التراخيص التالية غير E5 استخدام Microsoft 365 Defender:

- Microsoft Defender لنقطة النهاية
- Microsoft Defender for Identity
- Microsoft Defender لتطبيقات السحابة
- Defender for Office 365 (الخطة 2)

للحصول على قائمة كاملة بالتراخيص المعتمدة، [اقرأ متطلبات الترخيص](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>هل أحتاج إلى تثبيت أي شيء أو نشره لبدء استخدام Microsoft 365 Defender؟

لا، Microsoft 365 Defender دمج البيانات من Microsoft 365 الأمان التي قمت بنشرها بالفعل. بمجرد تشغيلها، ستبدأ تجارب الحوادث والأتمتة والصيد في العمل ضمن نطاق المنتجات التي تم نشرها. إذا لم يتم نشر أي من هذه المنتجات بشكل صحيح، Microsoft 365 Defender عرض أي بيانات ويبقى غير قادر على اتخاذ أي إجراء.

لتحسين تجاربك Microsoft 365 Defender، نوصي بنشر جميع المنتجات والخدمات Microsoft 365 [الأمان المعتمدة](deploy-supported-services.md).

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>أين Microsoft 365 Defender البيانات وتخزينها؟

Microsoft 365 Defender تحديد موقع مثالي لمركز البيانات حيث تتم معالجة البيانات المجمعة وتخزينها. إذا كان لديك Microsoft Defender لنقطة النهاية، فيحدد الموقع نفسه الذي يستخدمه Defender لنقطة النهاية.

>[!NOTE]
>توفر Microsoft Defender ل Endpoint تلقائيا في مراكز بيانات الاتحاد الأوروبي (EU) عند تشغيلها من خلال Microsoft Defender for Cloud. Microsoft 365 Defender تلقائيا في مركز بيانات الاتحاد الأوروبي نفسه للعملاء الذين قاموا بتوفير Microsoft Defender ل Endpoint بهذه الطريقة.

يتم عرض موقع مركز البيانات قبل وبعد توفير الخدمة في صفحة الإعدادات Microsoft 365 Defender (**الإعدادات > Microsoft 365 Defender**). إذا كنت تفضل استخدام موقع مركز بيانات آخر، فحدد **هل** تحتاج إلى مساعدة؟ في مدخل Microsoft 365 Defender للاتصال بدعم Microsoft.

## <a name="where-can-i-access-microsoft-365-defender"></a>أين يمكنني الوصول إلى Microsoft 365 Defender؟

Microsoft 365 Defender على: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>ما هي الأذونات التي أحتاج إليها للوصول إلى Microsoft 365 Defender؟

يمكن للحسابات المعينة أدوار Azure Active Directory (Azure AD) التالية الوصول Microsoft 365 Defender الوظائف والبيانات:

- المسؤول العام
- مسؤول الأمان
- عامل تشغيل الأمان
- القارئ العام
- قارئ الأمان
- مسؤول التوافق
- مسؤول بيانات التوافق
- مسؤول التطبيق
- مسؤول تطبيق السحابة


> [!NOTE]
> تؤثر إعدادات التحكم بالوصول المستند إلى الدور في Microsoft Defender لنقطة النهاية على الوصول إلى البيانات. لمزيد من المعلومات، اقرأ حول [إدارة الوصول إلى](m365d-permissions.md) Microsoft 365 Defender.

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>ما هي المنطقة الزمنية التي Microsoft 365 Defender الإعداد الافتراضي لها؟

بشكل افتراضي، Microsoft 365 Defender عرض معلومات الوقت في المنطقة الزمنية UTC. يمكنك تغيير هذا الإعداد لاستخدام المنطقة الزمنية المحلية. [تعرف على كيفية تعيين المنطقة الزمنية](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>كيف يمكنني التعرف على الميزات Microsoft 365 Defender الجديدة وتحديثات واجهة المستخدم؟

توفر Microsoft المعلومات بشكل منتظم من خلال القنوات المختلفة، بما في ذلك:

- مركز [الرسائل في](../../admin/manage/message-center.md) مركز مسؤولي Microsoft 365
- منشورات المدونة في مجتمع Microsoft 365 [الأمان & التوافق](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance)

احصل على أحدث التجارب المتوفرة بشكل عام من خلال تشغيل [ميزات المعاينة](preview.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [Microsoft 365 Defender عامة](microsoft-365-defender.md)
- [قم Microsoft 365 Defender](m365d-enable.md).
- [متطلبات الترخيص والمتطلبات الأساسية الأخرى](prerequisites.md)
- [نشر الخدمات المعتمدة](deploy-supported-services.md)
- [تشغيل ميزات المعاينة](preview.md)
