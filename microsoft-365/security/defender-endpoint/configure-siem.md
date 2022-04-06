---
title: دمج أدوات SIEM مع Microsoft Defender لنقطة النهاية
description: تعرف على كيفية استيعاب الحوادث والتنبيهات، ودمج أدوات SIEM.
keywords: تكوين siem، وأدوات إدارة معلومات الأمان والأحداث، وsplunk، و arcsight، والمؤشرات المخصصة، وواجهة برمجة تطبيقات rest، وتعريمات التنبيه، ومؤشرات التسوية
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
ms.openlocfilehash: d679ac0d01a7e922e49b72b574a43e6f684179f9
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664491"
---
# <a name="integrate-your-siem-tools-with-microsoft-defender-for-endpoint"></a>دمج أدوات SIEM مع Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


## <a name="ingest-alerts-using-security-information-and-events-management-siem-tools"></a>استيعاب التنبيهات باستخدام أدوات إدارة معلومات الأمان والأحداث (SIEM)

> [!NOTE]
>
> [Microsoft Defender لنقطة النهاية يتكون التنبيه](alerts.md) من حدث أو أكثر من الأحداث المشبوهة أو الضارة التي حدثت على الجهاز وتفاصيلها ذات الصلة. واجهة برمجة تطبيقات التنبيه Microsoft Defender لنقطة النهاية هي أحدث واجهة برمجة تطبيقات لاستهلاك التنبيه وتحتوي على قائمة مفصلة بالأدلة ذات الصلة لكل تنبيه. لمزيد من المعلومات، راجع [أساليب التنبيه وخصائصه](alerts.md) [وتنبيهات القائمة](get-alerts.md).

يدعم Microsoft Defender لنقطة النهاية أدوات إدارة معلومات الأمان والأحداث (SIEM) لاستيعاب المعلومات من مستأجر المؤسسة في Azure Active Directory (AAD (دليل Azure النشط)) باستخدام بروتوكول مصادقة OAuth 2.0 AAD (دليل Azure النشط)  تطبيق يمثل حل أو موصل SIEM المحدد المثبت في بيئتك.

لمزيد من المعلومات، اطلع على:

- [ترخيص واجهات برمجة التطبيقات Microsoft Defender لنقطة النهاية وشروط الاستخدام](api-terms-of-use.md) 
- [الوصول إلى Microsoft Defender لنقطة النهاية برمجة التطبيقات](apis-intro.md)
- [مثال مرحبًا بالعالم (يصف كيفية تسجيل تطبيق في Azure Active Directory)](api-hello-world.md)
- [الوصول باستخدام سياق التطبيق](exposed-apis-create-app-webapp.md)


يدعم Microsoft Defender لنقطة النهاية حاليا تكاملات حلول SIEM التالية: 

- [استيعاب الحوادث والتنبيهات من Microsoft 365 Defender وحوادث MICROSOFT DEFENDER لنقطة النهاية وتنبيهات واجهات برمجة تطبيقات REST](#ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis)
- [استيعاب أحداث Microsoft Defender لنقطة النهاية من واجهة برمجة تطبيقات دفق الأحداث Microsoft 365 Defender](#ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api)

## <a name="ingesting-incidents-and-alerts-from-the-microsoft-365-defender-and-microsoft-defender-for-endpoint-incidents-and-alerts-rest-apis"></a>استيعاب الحوادث والتنبيهات من Microsoft 365 Defender وحوادث MICROSOFT DEFENDER لنقطة النهاية وتنبيهات واجهات برمجة تطبيقات REST

### <a name="ingesting-incidents-from-the-microsoft-365-defender-incidents-rest-api"></a>استيعاب الحوادث من واجهة برمجة تطبيقات REST لحوادث Microsoft 365 Defender

لمزيد من المعلومات حول واجهة برمجة تطبيقات أحداث Microsoft 365 Defender، راجع [أساليب وخصائص الحوادث](../defender/api-incident.md).

### <a name="ingesting-alerts-from-the-microsoft-defender-for-endpoint-alerts-rest-api"></a>استيعاب التنبيهات من واجهة برمجة تطبيقات REST للتنبيهات Microsoft Defender لنقطة النهاية

لمزيد من المعلومات حول واجهة برمجة تطبيقات تنبيهات Microsoft Defender لنقطة النهاية، راجع [أساليب التنبيهات وخصائصها](alerts.md).

## <a name="siem-tool-integration-with-microsoft-defender-for-endpoint"></a>تكامل أداة SIEM مع Microsoft Defender لنقطة النهاية

### <a name="splunk"></a>Splunk

استخدام الوظيفة الإضافية Microsoft 365 Defender ل Splunk التي تدعم:

- استيعاب تنبيهات Microsoft Defender لنقطة النهاية
- تحديث التنبيهات في Microsoft Defender لنقطة النهاية من داخل Splunk

لمزيد من المعلومات حول الوظيفة الإضافية Microsoft 365 Defender ل Splunk، راجع [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

يستوعب SmartConnector الجديد لحوادث Microsoft 365 Defender التي تحتوي على تنبيهات من جميع منتجات Microsoft 365 Defender - بما في ذلك من Microsoft Defender لنقطة النهاية - إلى ArcSight ويعيدها إلى إطار الحدث المشترك (CEF).

لمزيد من المعلومات حول ArcSight SmartConnector الجديد Microsoft 365 Defender، راجع [وثائق ArcSight Product](https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/microsoft-365-defender/index.html).

يستبدل SmartConnector FlexConnector السابق ل Microsoft 365 Defender.

### <a name="ibm-qradar"></a>IBM QRadar

>[!NOTE]
>يدعم تكامل IBM QRadar مع Microsoft 365 Defender، والتي تتضمن Microsoft Defender لنقطة النهاية الآن وحدة دعم الأجهزة Microsoft 365 Defender الجديدة (DSM) التي تستدعي [ Microsoft 365 Defender Streaming API](../defender/streaming-api.md) التي تسمح لاستيعاب بيانات الحدث المتدفقة من منتجات Microsoft 365 Defender، بما في ذلك Microsoft Defender لنقطة النهاية. لمزيد من المعلومات حول QRadar الجديد Microsoft 365 Defender DSM، راجع [وثائق منتج IBM QRadar](https://www.ibm.com/docs/en/dsm?topic=microsoft-365-defender)، ولمزيد من المعلومات حول أنواع الأحداث المدعومة من واجهة برمجة التطبيقات المتدفقة، راجع [أنواع الأحداث المدعومة](../defender/supported-event-types.md).

لم يعد يتم إلحاق العملاء الجدد باستخدام وحدة دعم أجهزة QRadar Microsoft Defender ATP السابقة (DSM)، ويتم تشجيع العملاء الحاليين على اعتماد Microsoft 365 Defender DSM الجديدة كنقطة تكامل واحدة مع جميع منتجات Microsoft 365 Defender.

## <a name="ingesting-microsoft-defender-for-endpoint-events-from-the-microsoft-365-defender-event-streaming-api"></a>استيعاب أحداث Microsoft Defender لنقطة النهاية من واجهة برمجة تطبيقات دفق الأحداث Microsoft 365 Defender

تتضمن Microsoft 365 Defender بيانات الحدث المتدفقة تنبيهات وأحداث أخرى من Microsoft Defender لنقطة النهاية ومنتجات Microsoft Defender الأخرى. قد يتم بث هذه الأحداث إلى حساب تخزين Azure أو إلى Azure Event Hubs. نموذج التكامل عبر مراكز الأحداث مدعوم حاليا من قبل Splunk و IBM QRadar.

لمزيد من المعلومات، راجع [Microsoft 365 Defender تكامل SIEM](../defender/configure-siem-defender.md).
