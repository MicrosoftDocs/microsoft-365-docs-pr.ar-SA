---
title: ادمج أدوات SIEM مع Microsoft Defender لنقطة النهاية
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
ms.openlocfilehash: ed88048b506ecfcddb8394667e7d800927fc1d83
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634900"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>ادمج أدوات SIEM مع Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>تنبيهات استخدام معلومات الأمان وأدوات إدارة الأحداث (SIEM)

> [!NOTE]
>
> [Microsoft Defender لنقطة النهاية تنبيه](alerts.md) من حدث واحد أو أكثر من الأحداث المريبة أو الضارة التي وقعت على الجهاز وتفاصيلها ذات الصلة. إن Microsoft Defender لنقطة النهاية API للتنبيه هي أحدث API لاستهلاك التنبيه وتحتوي على قائمة مفصلة بدلليل ذي صلة لكل تنبيه. لمزيد من المعلومات، راجع [أساليب التنبيه وخصائصه](alerts.md) [وتنبيهات القائمة](get-alerts.md).

يدعم Microsoft Defender لنقطة النهاية معلومات الأمان وأدوات إدارة الأحداث (SIEM) التي تستخدم المعلومات من مستأجر المؤسسة في Azure Active Directory (AAD (دليل Azure النشط)) باستخدام بروتوكول مصادقة OAuth 2.0 لمستأجر AAD (دليل Azure النشط)  تطبيق يمثل حل SIEM المحدد أو الموصل المثبت في بيئتك.

لمزيد من المعلومات، اطلع على:

- [Microsoft Defender لنقطة النهاية واجهات برمجة التطبيقات شروط الاستخدام وترخيصها](api-terms-of-use.md) 
- [الوصول إلى Microsoft Defender لنقطة النهاية برمجة التطبيقات](apis-intro.md)
- [مرحبًا بالعالم المثال (يصف كيفية تسجيل تطبيق في Azure Active Directory)](api-hello-world.md)
- [الوصول باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md)


Microsoft Defender لنقطة النهاية حاليا عمليات تكامل حل SIEM التالية: 

- [أحداث وتنبيهات من Microsoft 365 Defender وتنبيهات Microsoft Defender لنقطة النهاية وتنبيهات REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [تحديد Microsoft Defender لنقطة النهاية الأحداث من Microsoft 365 Defender تدفق API](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>أحداث وتنبيهات من Microsoft 365 Defender وتنبيهات Microsoft Defender لنقطة النهاية وتنبيهات REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>أحداث الاحتكاء من Microsoft 365 Defender REST API

لمزيد من المعلومات حول Microsoft 365 Defender أحداث API، راجع [أساليب الأحداث وخصائصها](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>تنبيهات الاحتيام من تنبيهات Microsoft Defender لنقطة النهاية REST API

لمزيد من المعلومات حول Microsoft Defender لنقطة النهاية تنبيهات التنبيهات، راجع [أساليب التنبيهات وخصائصها](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>تكامل أداة SIEM مع Microsoft Defender لنقطة النهاية

### <a name="splunk"></a>Splunk

استخدام Microsoft 365 Defender الإضافية ل Splunk التي تدعم:

- محاولة Microsoft Defender لنقطة النهاية تنبيهات
- تحديث التنبيهات في Microsoft Defender لنقطة النهاية من داخل Splunk

لمزيد من المعلومات حول Microsoft 365 Defender الإضافية ل Splunk، راجع [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

SmartConnector الجديد Microsoft 365 Defender الأحداث التي تحتوي على تنبيهات من جميع منتجات Microsoft 365 Defender - بما في ذلك من Microsoft Defender لنقطة النهاية - إلى ArcSight وي خرائط هذه إلى Common Event Framework (CEF).

لمزيد من المعلومات حول ArcSight SmartConnector الجديد Microsoft 365 Defender، راجع وثائق [منتج ArcSight](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

يحل SmartConnector محل FlexConnector السابق Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>يتم الآن دعم تكامل IBM QRadar مع Microsoft 365 Defender التي تتضمن Microsoft Defender لنقطة النهاية بواسطة وحدة دعم Microsoft 365 Defender الجديدة (DSM) [التي تستدعي Microsoft 365 Defender برمجة](../defender/streaming-api.md) تطبيقات النقل المتدفق التي تسمح باحتواء بيانات حدث النقل المتدفق من Microsoft 365 Defender، بما في ذلك Microsoft Defender لنقطة النهاية. لمزيد من المعلومات حول خدمة QRadar Microsoft 365 Defender DSM، راجع [وثائق منتج QRadar ل IBM](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender)، لمزيد من المعلومات حول أنواع الأحداث المعتمدة ل API المتدفقة، راجع أنواع الأحداث [المعتمدة](../defender/supported-event-types.md).

لم يعد العملاء الجدد قيد التشغيل باستخدام وحدة دعم جهاز QRadar Microsoft Defender ATP السابقة (DSM)، كما يتم تشجيع العملاء الحاليين على اعتماد DSM Microsoft 365 Defender الجديد كنقطة واحدة للتكامل مع جميع منتجات Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>تحديد Microsoft Defender لنقطة النهاية الأحداث من Microsoft 365 Defender تدفق API

Microsoft 365 Defender بيانات الأحداث المتدفقة تنبيهات والأحداث الأخرى من Microsoft Defender لنقطة النهاية ومنتجات Microsoft Defender الأخرى. قد يتم دفق هذه الأحداث إلى حساب تخزين Azure أو إلى مراكز أحداث Azure. يتم حاليا دعم نموذج التكامل عبر مراكز الأحداث بواسطة Splunk وIBM QRadar.

لمزيد من المعلومات، [راجع Microsoft 365 Defender SIEM](../defender/configure-siem-defender.md).
