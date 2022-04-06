---
title: نظرة عامة على الإدارة و واجهات برمجة التطبيقات
ms.reviewer: ''
description: تعرف على أدوات الإدارة وفئات API في Microsoft Defender لنقطة النهاية
keywords: التكامل، api، siem، rbac، الوصول، المدخل، التكامل، التحقيق، الاستجابة، الوحدات، الكيان، سياق المستخدم، سياق التطبيق، النقل المتدفق
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
MS.technology: mde
ms.custom: api
ms.openlocfilehash: cc73531540222791eb39eeca74570f34ff78a1b7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469768"
---
# <a name="overview-of-management-and-apis"></a>نظرة عامة على الإدارة و واجهات برمجة التطبيقات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mgt-apis-abovefoldlink)


يدعم Defender for Endpoint مجموعة واسعة من الخيارات لضمان أن العملاء يمكنهم بسهولة اعتماد النظام الأساسي.

مع التسليم بأن بيئات العملاء وبنىهم قد تختلف، تم إنشاء Defender for Endpoint بمرونة وتحكم كبير لاحتواء متطلبات العملاء المختلفة.

## <a name="endpoint-onboarding-and-portal-access"></a>الوصول إلى نقطة النهاية والوصول إلى المدخل

يتم دمج تهيئة الأجهزة بشكل كامل في إدارة نقاط النهاية من Microsoft و Microsoft Intune للأجهزة العميلة و Microsoft Defender للأجهزة الخادمة، مما يوفر تجربة كاملة من النهاية إلى النهاية من التكوين والنشر والمراقبة. بالإضافة إلى ذلك، Microsoft Defender لنقطة النهاية هذه نهج المجموعة أدوات أخرى تستخدمها جهة خارجية لإدارة الأجهزة.

يوفر Defender for Endpoint إمكانية التحكم الدقيقة في ما يمكن للمستخدمين الذين لديهم حق الوصول إلى المدخل رؤيته وفعله من خلال مرونة التحكم بالوصول المستند إلى الدور (RBAC). يدعم نموذج RBAC كل أنواع بنية فرق الأمان:

- المؤسسات وفرق الأمان الموزعة عالميا
- فرق عمليات أمان النماذج ذات المستويات
- التقسيمات المنفصلة بالكامل مع فرق عمليات أمان عالمية مركزية واحدة

## <a name="available-apis"></a>واجهات برمجة التطبيقات المتوفرة

لقد Microsoft Defender لنقطة النهاية هذا الحل على أعلى النظام الأساسي الجاهز للتكامل.

يعرض Defender for Endpoint الكثير من بياناته والإجراءات الخاصة به من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. ستمكنك واجهات برمجة التطبيقات هذه من أتمتة مهام سير العمل وابتعازها استنادا إلى قدرات Defender لنقطة النهاية.

:::image type="content" source="images/mdatp-apis.png" alt-text="API المتوفرة والتكامل في Microsoft Defender لنقطة النهاية" lightbox="images/mdatp-apis.png":::

يمكن تجميع واجهات برمجة التطبيقات ل Defender for Endpoint في ثلاثة:

- Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات
- API لتدفق البيانات الخام
- تكامل SIEM

## <a name="microsoft-defender-for-endpoint-apis"></a>Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات

يوفر Defender for Endpoint نموذج API الطبقات يعرض البيانات والإمكانات في نموذج منظم وواضح وسهل الاستخدام، يتم عرضه من خلال نموذج تخويل ومصادقة قياسي مستند إلى Azure AD يسمح بالوصول في سياق المستخدمين أو تطبيقات SaaS. تم تصميم نموذج API لكشف الكيانات والإمكانات في نموذج متناسق.

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول Defender ل واجهات برمجة التطبيقات في Endpoint.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

تعرض  واجهة برمجة التطبيق "التحقيق" ثراء Defender لنقطة النهاية - مما يعرض الكيانات المحسوبة أو "ملف التعريف" (على سبيل المثال، الجهاز والمستخدم والملف) والأحداث منفصلة (على سبيل المثال، إنشاء العملية وإنشاء الملفات) التي تصف عادة سلوكا مرتبطا بكيان ما، مما يمكن الوصول إلى البيانات عبر واجهات التحقيق التي تسمح بالوصول إلى البيانات استنادا إلى استعلام. لمزيد من المعلومات، راجع [واجهات برمجة التطبيقات المعتمدة](exposed-apis-list.md).

تعرض **API** للاستجابة القدرة على اتخاذ إجراءات في الخدمة وعلى الأجهزة، مما يمكن العملاء من استخدام المؤشرات وإدارة الإعدادات، حالة التنبيه، بالإضافة إلى اتخاذ إجراءات الاستجابة على الأجهزة برمجيا مثل عزل الأجهزة من الشبكة وملفات الفحص وغيرها.

## <a name="raw-data-streaming-api"></a>API لتدفق البيانات الخام

يوفر Defender ل API لتدفق البيانات الخام لنقطة النهاية القدرة للعملاء على شحن الأحداث والتنبيهات في الوقت الحقيقي من مثيلاتهم عند حدوثها ضمن دفق بيانات واحد، مما يوفر زمن نقل منخفض وآلية تسليم معدل نقل عال.

يتم دفع معلومات حدث Defender for Endpoint مباشرة إلى تخزين Azure للاحتفاظ بالبيانات على المدى الطويل، أو إلى مراكز أحداث Azure للاستهلاك بواسطة خدمات المرئيات أو محركات معالجة البيانات الإضافية.

لمزيد من المعلومات، راجع [API لتدفق البيانات الخام](raw-data-export.md).

تتضمن الأداة Microsoft 365 Defender API للدفق أحداث البريد الإلكتروني والتنبيهات بالإضافة إلى أحداث الجهاز.
لمزيد من المعلومات، راجع Microsoft 365 Defender [API المتدفقة](../defender/streaming-api.md).

## <a name="siem-api"></a>SIEM API

عند تمكين تكامل معلومات الأمان وإدارة الأحداث (SIEM)، فإنه يسمح لك بسحب عمليات الكشف من Microsoft 365 Defender باستخدام حل SIEM الخاص بك أو عن طريق الاتصال مباشرة باكتشافات REST API. هذا الأمر ينشط قسم تفاصيل الوصول إلى موصل SIEM مع قيم معبأه مسبقا، كما يتم إنشاء تطبيق ضمن مستأجر Azure Active Directory (Azure AD). 

## <a name="related-topics"></a>المواضيع ذات الصلة

- [الوصول إلى Microsoft Defender لنقطة النهاية برمجة التطبيقات](apis-intro.md)
- [واجهات برمجة التطبيقات المعتمدة](exposed-apis-list.md)
- [فرص الشريك التقني](partner-integration.md)
