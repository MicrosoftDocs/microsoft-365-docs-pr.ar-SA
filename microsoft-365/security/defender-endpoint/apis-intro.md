---
title: الوصول إلى واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية
ms.reviewer: ''
description: تعرف على كيفية استخدام واجهات برمجة التطبيقات لأتمتة مهام سير العمل وابتعازها استنادا إلى قدرات نقطة النهاية ل Microsoft Defender
keywords: apis، api، wdatp، فتح api، microsoft defender ل api نقطة النهاية، microsoft defender atp، api العامة، apis المعتمدة، التنبيهات، الجهاز، المستخدم، المجال، ip، ملف، البحث المتقدم، الاستعلام
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
ms.openlocfilehash: a73df39c6d26bdfd44a7f4f629e148e7f0afabb2
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/03/2021
ms.locfileid: "63583125"
---
# <a name="access-the-microsoft-defender-for-endpoint-apis"></a>الوصول إلى واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يعرض Defender for Endpoint الكثير من بياناته والإجراءات الخاصة به من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. ستمكنك واجهات برمجة التطبيقات هذه من أتمتة مهام سير العمل وابتعازها استنادا إلى قدرات Defender لنقطة النهاية. يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

شاهد هذا الفيديو للحصول على نظرة عامة سريعة حول Defender ل واجهات برمجة التطبيقات في Endpoint.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء AAD (دليل Azure النشط) [جديد](/microsoft-365/security/defender-endpoint/exposed-apis-create-app-nativeapp)
- الحصول على رمز وصول مميز باستخدام هذا التطبيق
- استخدام الرمز المميز للوصول إلى Defender for Endpoint API

يمكنك الوصول إلى Defender for Endpoint API باستخدام **سياق التطبيق** أو **سياق المستخدم**.

- **سياق التطبيق: (مستحسن)**

  يتم استخدامها بواسطة التطبيقات التي يتم تشغيلها بدون تقديم مستخدم تم تسجيل الدخول له. على سبيل المثال، التطبيقات التي يتم تشغيلها كالخدمات الخلفية أو daemons.

  الخطوات التي يجب اتخاذها للوصول إلى Defender for Endpoint API مع سياق التطبيق:

  1. إنشاء AAD (دليل Azure النشط) Web-Application.
  2. قم بتعيين الإذن المطلوب للتطبيق، على سبيل المثال، "تنبيهات القراءة"، "أجهزة عزل".
  3. إنشاء مفتاح لهذا التطبيق.
  4. احصل على الرمز المميز باستخدام التطبيق باستخدام مفتاحه.
  5. استخدام الرمز المميز للوصول إلى Microsoft Defender ل API لنقطة النهاية

     لمزيد من المعلومات، راجع [الوصول باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md).

- **سياق المستخدم:**

  يستخدم لتنفيذ إجراءات في واجهة برمجة المستخدم بالنيابة عن المستخدم.

  الخطوات التي يجب اتخاذها للوصول إلى Defender for Endpoint API مع سياق المستخدم:

  1. إنشاء AAD (دليل Azure النشط) Native-Application.
  2. قم بتعيين الإذن المطلوب للتطبيق، على سبيل المثال "تنبيهات القراءة" أو "أجهزة عزل" إلخ.
  3. احصل على رمز مميز باستخدام التطبيق مع بيانات اعتماد المستخدم.
  4. استخدام الرمز المميز للوصول إلى Microsoft Defender ل API لنقطة النهاية

     لمزيد من المعلومات، راجع [الوصول باستخدام سياق المستخدم](exposed-apis-create-app-nativeapp.md).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](exposed-apis-list.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md)
- [الوصول إلى Microsoft Defender لنقطة النهاية باستخدام سياق المستخدم](exposed-apis-create-app-nativeapp.md)
