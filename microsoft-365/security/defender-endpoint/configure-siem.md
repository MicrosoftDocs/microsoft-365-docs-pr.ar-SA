---
title: دمج أدوات SIEM مع Microsoft Defender لنقطة النهاية
description: تعرف على كيفية استخدام الأحداث والتنبيهات ودمج أدوات SIEM.
keywords: تكوين siem ومعلومات الأمان وأدوات إدارة الأحداث، وslunk، وقوس النظر، والمؤشرات المخصصة، وبرمجة التطبيقات، وتعريفات التنبيهات، ومؤشرات اختراق
search.appverid: met150
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4c0462bcfae77677fca05132aaf0895b897bf788
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/24/2022
ms.locfileid: "63572292"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>دمج أدوات SIEM مع Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>تنبيهات استخدام معلومات الأمان وأدوات إدارة الأحداث (SIEM)

> [!NOTE]
>
> [يتم إنشاء تنبيه Microsoft Defender لنقطة](alerts.md) النهاية من حدث واحد أو أكثر من الأحداث المريبة أو الضارة التي وقعت على الجهاز وتفاصيلها ذات الصلة. إن API لتنبيهات نقطة النهاية من Microsoft Defender هي أحدث API لاستهلاك التنبيه وتحتوي على قائمة مفصلة بدلليل ذي صلة لكل تنبيه. لمزيد من المعلومات، راجع [أساليب التنبيه وخصائصه](alerts.md) [وتنبيهات القائمة](get-alerts.md).

يدعم Microsoft Defender ل Endpoint أدوات استخدام معلومات الأمان وإدارة الأحداث (SIEM) من مستأجر المؤسسة في Azure Active Directory (AAD (دليل Azure النشط)) باستخدام بروتوكول مصادقة OAuth 2.0 لتطبيق AAD (دليل Azure النشط) مسجل يمثل حل SIEM المحدد أو الموصل المثبت في بيئتك.

لمزيد من المعلومات، اطلع على:

- [ترخيص Microsoft Defender ل واجهات برمجة تطبيقات نقطة النهاية و شروط الاستخدام](api-terms-of-use.md) 
- [الوصول إلى واجهات برمجة تطبيقات Microsoft Defender لنقطة النهاية](apis-intro.md)
- [مثال Hello World (يصف كيفية تسجيل تطبيق في Azure Active Directory)](api-hello-world.md)
- [الوصول باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md)


يدعم Microsoft Defender ل Endpoint حاليا عمليات تكامل حل SIEM التالية: 

- [أحداث وتنبيهات حول محاولة Microsoft 365 Defender و Microsoft Defender لحوادث نقطة النهاية والتنبيهات الخاصة ب "واجهات برمجة تطبيقات REST"](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [الاحتيام إلى أحداث Microsoft Defender لنقطة النهاية من Microsoft 365 Defender تدفق API للحدث](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>أحداث وتنبيهات حول محاولة Microsoft 365 Defender و Microsoft Defender لحوادث نقطة النهاية والتنبيهات الخاصة ب "واجهات برمجة تطبيقات REST"

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>أحداث الاحتكاء من Microsoft 365 Defender REST API

لمزيد من المعلومات حول Microsoft 365 Defender أحداث API، راجع [أساليب الأحداث وخصائصها](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>تنبيهات الإبراق من تنبيهات Microsoft Defender لنقطة النهاية REST API

لمزيد من المعلومات حول API لتنبيهات نقطة النهاية ل Microsoft Defender، راجع [أساليب التنبيهات وخصائصها](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>تكامل أداة SIEM مع Microsoft Defender ل Endpoint

### <a name="splunk"></a>Splunk

استخدام Microsoft 365 Defender الإضافية ل Splunk التي تدعم:

- محاولة Microsoft Defender لتنبيهات نقطة النهاية
- تحديث التنبيهات في Microsoft Defender لنقطة النهاية من داخل Splunk

لمزيد من المعلومات حول Microsoft 365 Defender الإضافية ل Splunk، راجع [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

SmartConnector الجديد لحوادث Microsoft 365 Defender التي تحتوي على تنبيهات من جميع منتجات Microsoft 365 Defender - بما في ذلك من Microsoft Defender ل Endpoint - إلى ArcSight وي تعيينها إلى Common Event Framework (CEF).

لمزيد من المعلومات حول ArcSight SmartConnector الجديد Microsoft 365 Defender، راجع وثائق [منتج ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

يحل SmartConnector محل FlexConnector السابق Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>يتم الآن دعم تكامل IBM QRadar مع Microsoft 365 Defender، الذي يتضمن Microsoft Defender لنقطة النهاية بواسطة الوحدة النمطية الجديدة لدعم جهاز Microsoft 365 Defender (DSM) التي تستدعي [API ل Microsoft 365 Defender](../defender/streaming-api.md) المتدفقة التي تسمح باحتواء بيانات حدث النقل المتدفق من Microsoft 365 Defender، بما في ذلك Microsoft Defender لنقطة النهاية. لمزيد من المعلومات حول خدمة QRadar Microsoft 365 Defender DSM، راجع [وثائق منتج QRadar ل IBM](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender)، لمزيد من المعلومات حول أنواع الأحداث المعتمدة ل API المتدفقة، راجع أنواع الأحداث [المعتمدة](../defender/supported-event-types.md).

لم يعد العملاء الجدد قيد التشغيل باستخدام وحدة دعم جهاز QRadar Microsoft Defender ATP السابقة (DSM)، كما يتم تشجيع العملاء الحاليين على اعتماد DSM Microsoft 365 Defender الجديد كنقطة واحدة للتكامل مع جميع منتجات Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>الاحتيام إلى أحداث Microsoft Defender لنقطة النهاية من Microsoft 365 Defender تدفق API للحدث

Microsoft 365 Defender بيانات الأحداث المتدفقة تنبيهات والأحداث الأخرى من Microsoft Defender ل Endpoint ومنتجات Microsoft Defender الأخرى. قد يتم دفق هذه الأحداث إلى حساب تخزين Azure أو إلى مراكز أحداث Azure. يتم حاليا دعم نموذج التكامل عبر مراكز الأحداث بواسطة Splunk وIBM QRadar.

لمزيد من المعلومات، [راجع Microsoft 365 Defender SIEM](../defender/configure-siem-defender.md).
