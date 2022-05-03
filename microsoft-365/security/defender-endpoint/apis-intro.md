---
title: الوصول إلى Microsoft Defender لنقطة النهاية برمجة التطبيقات
ms.reviewer: ''
description: تعرف على كيفية استخدام واجهات برمجة التطبيقات لأتمتة مهام سير العمل والابتكار استنادا إلى قدرات Microsoft Defender لنقطة النهاية
keywords: واجهة برمجة التطبيقات، واجهة برمجة التطبيقات، wdatp، واجهة برمجة التطبيقات المفتوحة، microsoft Defender لواجهة برمجة تطبيقات نقطة النهاية، microsoft defender atp، واجهة برمجة التطبيقات العامة، واجهة برمجة التطبيقات المدعومة، التنبيهات، الجهاز، المستخدم، المجال، ip، ملف، تتبع متقدم، استعلام
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
ms.openlocfilehash: 3638357d2c1440604858fabfa42e5df32569aed3
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172256"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>الوصول إلى Microsoft Defender لنقطة النهاية برمجة التطبيقات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Business](../defender-business/index.yml)

> [!IMPORTANT]
> لا يتم تضمين قدرات التتبع المتقدمة في Defender for Business. راجع [مقارنة Microsoft Defender for Business بالخطط Microsoft Defender لنقطة النهاية 1 و2](../defender-business/compare-mdb-m365-plans.md#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2).

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يكشف Defender لنقطة النهاية الكثير من بياناته وإجراءاته من خلال مجموعة من واجهات برمجة التطبيقات البرمجية. ستمكنك واجهات برمجة التطبيقات هذه من أتمتة مهام سير العمل والابتكار استنادا إلى قدرات Defender لنقطة النهاية. يتطلب الوصول إلى واجهة برمجة التطبيقات مصادقة OAuth2.0. لمزيد من المعلومات، راجع [التعليمة البرمجية للتخويل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

شاهد هذا الفيديو للحصول على نظرة عامة سريعة على واجهات برمجة تطبيقات Defender لنقطة النهاية.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء [تطبيق AAD (دليل Azure النشط)](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- الحصول على رمز مميز للوصول باستخدام هذا التطبيق
- استخدام الرمز المميز للوصول إلى Defender لواجهة برمجة تطبيقات نقطة النهاية

يمكنك الوصول إلى Defender لواجهة برمجة تطبيقات نقطة النهاية باستخدام **سياق التطبيق** أو **سياق المستخدم**.

- **سياق التطبيق: (مستحسن)**

  يستخدم من قبل التطبيقات التي تعمل دون وجود مستخدم قام بتسجيل الدخول. على سبيل المثال، التطبيقات التي تعمل كخدمات خلفية أو برامج خفية.

  الخطوات التي يجب اتخاذها للوصول إلى Defender لواجهة برمجة تطبيقات نقطة النهاية مع سياق التطبيق:

  1. إنشاء تطبيق ويب AAD (دليل Azure النشط).
  2. عين الإذن المطلوب للتطبيق، على سبيل المثال، "قراءة التنبيهات"، "عزل الأجهزة".
  3. إنشاء مفتاح لهذا التطبيق.
  4. احصل على الرمز المميز باستخدام التطبيق مع مفتاحه.
  5. استخدام الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية

     لمزيد من المعلومات، راجع [الحصول على الوصول باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md).

- **سياق المستخدم:**

  يستخدم لتنفيذ إجراءات في واجهة برمجة التطبيقات نيابة عن مستخدم.

  الخطوات التي يجب اتخاذها للوصول إلى Defender لواجهة برمجة تطبيقات نقطة النهاية مع سياق المستخدم:

  1. إنشاء تطبيق أصلي AAD (دليل Azure النشط).
  2. قم بتعيين الإذن المطلوب للتطبيق، على سبيل المثال "قراءة التنبيهات" و"عزل الأجهزة" وما إلى ذلك.
  3. احصل على الرمز المميز باستخدام التطبيق مع بيانات اعتماد المستخدم.
  4. استخدام الرمز المميز للوصول إلى واجهة برمجة تطبيقات Microsoft Defender لنقطة النهاية

     لمزيد من المعلومات، راجع ["الحصول على حق الوصول باستخدام سياق المستخدم](exposed-apis-create-app-nativeapp.md)".

## <a name="related-topics"></a>المواضيع ذات الصلة

- [واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية](exposed-apis-list.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية مع سياق التطبيق](exposed-apis-create-app-webapp.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية مع سياق المستخدم](exposed-apis-create-app-nativeapp.md)
