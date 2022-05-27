---
title: نظرة عامة على واجهات برمجة تطبيقات Microsoft 365 Defender
description: تعرف على واجهات برمجة التطبيقات المتوفرة في Microsoft 365 Defender
keywords: api, apis, overview, incident, incidents, threat hunting, microsoft 365 defender
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
ms.openlocfilehash: c2a340c2ad147e32082a50e326a2e0c7e11718c2
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739594"
---
# <a name="overview-of-microsoft-365-defender-apis"></a>نظرة عامة على واجهات برمجة تطبيقات Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**ينطبق على:**

- Microsoft 365 Defender

> [!IMPORTANT]
> تتعلق بعض المعلومات بالناتج الذي تم إصداره مسبقا والذي قد يتم تعديله بشكل كبير قبل إصداره تجاريا. لا تقدم Microsoft أي ضمانات، صريحة أو ضمنية، فيما يتعلق بالمعلومات المقدمة هنا.

Microsoft 365 Defender مبني على نظام أساسي جاهز للتكامل.

استخدم واجهات برمجة التطبيقات Microsoft 365 Defender لأتمتة مهام سير العمل استنادا إلى الحدث المشترك وجداول التتبع المتقدمة.

- **[قائمة انتظار الحوادث المجمعة](api-incident.md)** - ركز على ما هو مهم من خلال تجميع نطاق الهجوم الكامل وجميع الأصول المتأثرة معا ضمن واجهة برمجة تطبيقات الحدث.

- **[تتبع التهديدات عبر المنتجات](api-advanced-hunting.md)** - الاستفادة من المعرفة التنظيمية لفريق الأمان للبحث عن علامات التسوية، عن طريق إنشاء استعلامات مخصصة خاصة بك لتدقيق البيانات الأولية التي تم جمعها عبر منتجات حماية متعددة.

- **[واجهة برمجة تطبيقات تدفق الأحداث](streaming-api.md)** - شحن الأحداث والتنبيهات في الوقت الحقيقي في دفق بيانات واحد عند حدوثها.

إلى جانب واجهات برمجة التطبيقات الخاصة Microsoft 365 Defender هذه، تكشف كل من منتجاتنا الأمنية الأخرى [واجهات برمجة التطبيقات الإضافية](api-articles.md) لمساعدتك على الاستفادة من إمكاناتها الفريدة.

> [!NOTE]
> يجب ألا يؤثر الانتقال إلى المدخل الموحد على لوحات معلومات PowerBi استنادا إلى واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية. يمكنك الاستمرار في العمل مع واجهات برمجة التطبيقات الموجودة بغض النظر عن انتقال المدخل التفاعلي.

شاهد هذا الفيديو القصير لمعرفة كيفية استخدام Microsoft 365 Defender لأتمتة مهام سير العمل ودمج التطبيقات.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4d73M?rel=0]

## <a name="learn-more"></a>التعرف على المزيد

| **فهم كيفية الوصول إلى واجهات برمجة التطبيقات** |
|-|
| [التعرف على الحصص النسبية لواجهة برمجة التطبيقات والترخيص](api-terms.md) |
| [الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-access.md) |
| **إنشاء تطبيقات** |
| [إنشاء تطبيق 'Hello world'](api-hello-world.md) |
| [إنشاء تطبيق للوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender نيابة عن مستخدم](api-create-app-user-context.md) |
| [إنشاء تطبيق للوصول إلى Microsoft 365 Defender بدون مستخدم](api-create-app-web.md) |
| [إنشاء تطبيق مع وصول شريك متعدد المستأجرين إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-partner-access.md) |
| **استكشاف أخطاء تطبيقاتك وصيانتها وإصلاحها** |
| [فهم رموز أخطاء واجهة برمجة التطبيقات](api-error-codes.md) |
| [إدارة البيانات السرية في تطبيقاتك باستخدام Azure Key Vault](/learn/modules/manage-secrets-with-azure-key-vault/) |
| [تنفيذ تخويل OAuth 2.0 لتسجيل دخول المستخدم](/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |
