---
title: نظرة عامة Microsoft 365 Defender واجهات برمجة التطبيقات
description: تعرف على واجهات برمجة التطبيقات المتوفرة في Microsoft 365 Defender
keywords: apis، apis، نظرة عامة، حادث، أحداث، البحث عن تهديدات، microsoft 365 defender
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
ms.openlocfilehash: ec4a497fd0ee428fbc664ae064ec95f74fcdce85
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63570582"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>نظرة عامة Microsoft 365 Defender واجهات برمجة التطبيقات

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالمنتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل طرحه تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المتوفرة هنا.

Microsoft 365 Defender على أعلى النظام الأساسي الجاهز للتكامل.

استخدم Microsoft 365 Defender برمجة التطبيقات لأتمتة مهام سير العمل استنادا إلى الحادث المشترك وجداول الصيد المتقدمة.

- **[قائمة انتظار الأحداث المدمجة](api-incident.md)** - ركز على ما هو هام من خلال تجميع نطاق الهجوم الكامل وكل الأصول التي تم التأثير عليها معا ضمن API للحادث.

- **[مكافحة](api-advanced-hunting.md)** التهديدات عبر المنتجات - يمكنك الاستفادة من المعرفة التنظيمية لفريق الأمان للبحث عن علامات اختراق، عن طريق إنشاء الاستعلامات المخصصة الخاصة بك لتعقب البيانات الخام التي يتم تجميعها عبر منتجات الحماية المتعددة.

- **[API لتدفق الأحداث](streaming-api.md)** - قم بشحن الأحداث والتنبيهات في الوقت الحقيقي في دفق بيانات واحد عند حدوثها.

إلى جانب Microsoft 365 Defender واجهات برمجة التطبيقات الخاصة بكل واحد من منتجات الأمان الأخرى لدينا، تعرض واجهات [](api-articles.md) برمجة التطبيقات الإضافية لمساعدتك على الاستفادة من إمكاناتها الفريدة.

> [!NOTE]
> يجب ألا يؤثر الانتقال إلى المدخل الموحد على لوحات معلومات PowerBi استنادا إلى Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية. يمكنك الاستمرار في العمل باستخدام واجهات برمجة التطبيقات الموجودة بغض النظر عن انتقال المدخل التفاعلي.

## <a name="learn-more"></a>التعرف على المزيد

| **فهم كيفية الوصول إلى واجهات برمجة التطبيقات** |
|-|
| [التعرف على الحصص النسبية ل API والترخيص](api-terms.md) |
| [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md) |
| **إنشاء التطبيقات** |
| [إنشاء تطبيق 'Hello world'](api-hello-world.md) |
| [إنشاء تطبيق للوصول Microsoft 365 Defender واجهات برمجة التطبيقات بالنيابة عن المستخدم](api-create-app-user-context.md) |
| [إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم](api-create-app-web.md) |
| [إنشاء تطبيق مع وصول شريك متعدد المستأجرين إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-partner-access.md) |
| **استكشاف الأخطاء وإصلاحها والمحافظة على تطبيقاتك** |
| [فهم رموز خطأ API](api-error-codes.md) |
| [إدارة أسرار تطبيقاتك باستخدام مخزن مفاتيح Azure](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [تنفيذ تخويل OAuth 2.0 ل تسجيل الدخول من قبل المستخدم](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
