---
title: الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات
description: تعرف على كيفية الوصول إلى واجهات Microsoft 365 Defender برمجة التطبيقات
keywords: الوصول، apis، سياق التطبيق، سياق المستخدم، تطبيق aad، رمز الوصول المميز
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: a8406c0ec27c238615b25f60b988efbb50a8d7d7
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63569904"
---
# <a name="access-the-microsoft-365-defender-apis"></a>الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

Microsoft 365 Defender البيانات والإجراءات من خلال مجموعة من واجهات برمجة التطبيقات البرنامجية. تساعدك واجهات برمجة التطبيقات هذه على أتمتة مهام سير العمل واستخدام إمكانات Microsoft 365 Defender بالكامل.

بشكل عام، ستحتاج إلى اتخاذ الخطوات التالية لاستخدام واجهات برمجة التطبيقات:

- إنشاء تطبيق Azure Active Directory
- الحصول على رمز وصول مميز باستخدام هذا التطبيق
- استخدام الرمز المميز للوصول إلى Microsoft 365 Defender API

> [!NOTE]
> يتطلب الوصول إلى API مصادقة OAuth2.0. لمزيد من المعلومات، راجع [رمز التخويل ل OAuth 2.0 Flow](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

بعد تنفيذ هذه الخطوات، تكون جاهزا للوصول إلى Microsoft 365 Defender API باستخدام سياق معين.

## <a name="application-context-recommended"></a>سياق التطبيق (مستحسن)

استخدم هذا السياق للتطبيقات التي يتم تشغيلها بدون تقديم مستخدم تم تسجيل الدخول له، مثل خدمات الخلفية أو daemons.

1. إنشاء تطبيق ويب Azure Active Directory.
2. تعيين الأذونات المطلوبة للتطبيق.
3. إنشاء مفتاح للتطبيق.
4. احصل على رمز أمان مميز باستخدام التطبيق ومفتاحه.
5. استخدم الرمز المميز للوصول إلى Microsoft 365 Defender API.

لمزيد من المعلومات، راجع إنشاء تطبيق للوصول **[إلى Microsoft 365 Defender بدون مستخدم](api-create-app-web.md)**.

## <a name="user-context"></a>سياق المستخدم

استخدم هذا السياق لتنفيذ إجراءات بالنيابة عن مستخدم واحد.

1. إنشاء تطبيق Azure Active Directory الأصلي.
2. تعيين الإذن المطلوب للتطبيق.
3. احصل على رمز أمان مميز باستخدام بيانات اعتماد المستخدم للتطبيق.
4. استخدم الرمز المميز للوصول إلى Microsoft 365 Defender API.

لمزيد من المعلومات، راجع إنشاء تطبيق للوصول **[Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم](api-create-app-user-context.md)**.

## <a name="partner-context"></a>سياق الشريك

استخدم هذا السياق عندما تحتاج إلى توفير تطبيق للعديد من المستخدمين عبر [مستأجرين متعددين](/azure/active-directory/develop/single-and-multi-tenant-apps).

1. إنشاء تطبيق Azure Active Directory متعدد المستأجرين.
2. تعيين الإذن المطلوب للتطبيق.
3. احصل [على موافقة المسؤول](/azure/active-directory/develop/v2-permissions-and-consent#requesting-consent-for-an-entire-tenant) للتطبيق من كل مستأجر.
4. احصل على رمز أمان مميز باستخدام بيانات اعتماد المستخدم استنادا إلى اسم المستأجر الخاص للعميل.
5. استخدم الرمز المميز للوصول إلى Microsoft 365 Defender API.

لمزيد من المعلومات، راجع **[إنشاء تطبيق مع وصول الشريك Microsoft 365 Defender واجهات برمجة التطبيقات](api-partner-access.md)**.

## <a name="related-articles"></a>المقالات ذات الصلة

- [Microsoft 365 Defender نظرة عامة على واجهات برمجة التطبيقات](api-overview.md)
- [تخويل OAuth 2.0 تسجيل دخول المستخدم والوصول إلى API](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)
- [إدارة أسرار تطبيقات الخادم باستخدام مخزن مفاتيح Azure](/learn/modules/manage-secrets-with-azure-key-vault/)
- [إنشاء تطبيق 'Hello world' الذي Microsoft 365 واجهات برمجة التطبيقات](api-hello-world.md)
