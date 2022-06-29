---
title: ادمج أدوات إدارة معلومات الأمان والأحداث مع Microsoft 365 Defender
description: تعرف على كيفية استخدام واجهة برمجة تطبيقات REST وتكوين أدوات إدارة معلومات الأمان والأحداث المدعومة لتلقي عمليات الكشف وسحبها.
keywords: تكوين siem، وأدوات إدارة معلومات الأمان والأحداث، وsplunk، و arcsight، والمؤشرات المخصصة، وواجهة برمجة تطبيقات rest، وتعريمات التنبيه، ومؤشرات التسوية
search.product: eADQiWindows 10XVcnh
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
ms.openlocfilehash: 3e2772fd458c60e48f78c0d4b816cdac8ca25940
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66530291"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>ادمج أدوات إدارة معلومات الأمان والأحداث مع Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>سحب Microsoft 365 Defender الأحداث وبيانات الأحداث المتدفقة باستخدام أدوات إدارة معلومات الأمان والأحداث (SIEM)

> [!NOTE]
>
> - [تتكون Microsoft 365 Defender Incidents](incident-queue.md) من مجموعات من التنبيهات المرتبطة وأدلةها.
> - [Microsoft 365 Defender دفق واجهة برمجة التطبيقات دفق](streaming-api.md) بيانات الأحداث من Microsoft 365 Defender إلى مراكز الأحداث أو حسابات تخزين Azure.

يدعم Microsoft 365 Defender أدوات إدارة معلومات الأمان والأحداث (SIEM) لاستيعاب المعلومات من مستأجر المؤسسة في Azure Active Directory (AAD) باستخدام بروتوكول مصادقة OAuth 2.0 لتطبيق AAD مسجل يمثل حل SIEM المحدد أو الموصل المثبت في بيئتك. 

لمزيد من المعلومات، اطلع على:

- [ترخيص واجهات برمجة التطبيقات Microsoft 365 Defender وشروط الاستخدام](api-terms.md)
- [الوصول إلى واجهات برمجة التطبيقات Microsoft 365 Defender](api-access.md)
- [مثال "مرحباً بالعالم"](api-hello-world.md)
- [الوصول باستخدام سياق التطبيق](api-create-app-web.md)

هناك نموذجان أساسيان لاستيعاب معلومات الأمان: 

1.  استيعاب أحداث Microsoft 365 Defender والتنبيهات التي تحتوي عليها من واجهة برمجة تطبيقات REST في Azure. 

2.  استيعاب بيانات الحدث المتدفقة إما من خلال Azure Event Hubs أو حسابات Azure Storage. 

يدعم Microsoft 365 Defender حاليا تكاملات حلول SIEM التالية: 

- [استيعاب الحوادث من واجهة برمجة تطبيقات REST للأحداث](#ingesting-incidents-from-the-incidents-rest-api)
- [استيعاب بيانات الحدث المتدفقة عبر Event Hub](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>استيعاب الحوادث من واجهة برمجة تطبيقات REST للأحداث

### <a name="incident-schema"></a>مخطط الحادث
لمزيد من المعلومات حول خصائص الحادث Microsoft 365 Defender بما في ذلك بيانات تعريف كيانات التنبيه والأدلة المضمنة، راجع [تعيين المخطط](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

استخدام وظيفة Splunk الإضافية الجديدة المدعومة بالكامل ل Microsoft Security التي تدعم:

- استيعاب الحوادث التي تحتوي على تنبيهات من المنتجات التالية، والتي تم تعيينها على نموذج المعلومات العامة ل Splunk (CIM):

  - Microsoft 365 Defender
  - Microsoft Defender for Endpoint
  - Microsoft Defender for Identity وAzure Active Directory Identity Protection
  - Microsoft Defender for Cloud Apps

- استيعاب تنبيهات Defender لنقطة النهاية (من نقطة نهاية Azure ل Defender لنقطة النهاية) وتحديث هذه التنبيهات

- تم نقل دعم تحديث Microsoft 365 Defender Incidents و/أو Microsoft Defender لنقطة النهاية Alerts ولوحات المعلومات المعنية إلى تطبيق Microsoft 365 ل Splunk. 

لمزيد من المعلومات حول:

- الوظيفة الإضافية Splunk لأمان Microsoft، راجع [الوظيفة الإضافية لأمان Microsoft على Splunkbase](https://splunkbase.splunk.com/app/6207/#/overview)

- تطبيق Microsoft 365 ل Splunk، راجع [تطبيق Microsoft 365 على Splunkbase](https://splunkbase.splunk.com/app/3786/)

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

يقوم SmartConnector الجديد Microsoft 365 Defender استيعاب الحوادث في ArcSight وتعيينها إلى إطار الحدث المشترك (CEF).

لمزيد من المعلومات حول ArcSight SmartConnector الجديد Microsoft 365 Defender، راجع [وثائق منتجات ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

يستبدل SmartConnector FlexConnector السابق Microsoft Defender لنقطة النهاية التي تم إهمالها.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>استيعاب بيانات الحدث المتدفقة عبر مراكز الأحداث

تحتاج أولا إلى دفق الأحداث من مستأجر AAD إلى Event Hubs أو Azure Storage Account. لمزيد من المعلومات، راجع [Streaming API](../defender/streaming-api.md).

لمزيد من المعلومات حول أنواع الأحداث التي تدعمها واجهة برمجة تطبيقات الدفق، راجع [أنواع أحداث الدفق المعتمدة](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk

استخدم الوظيفة الإضافية Splunk ل Microsoft Cloud Services لاستيعاب الأحداث من Azure Event Hubs.  

لمزيد من المعلومات حول الوظيفة الإضافية Splunk ل Microsoft Cloud Services، راجع [الوظيفة الإضافية Microsoft Cloud Services على Splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>استخدم وحدة دعم الأجهزة Microsoft 365 Defender IBM QRadar الجديدة التي تستدعي [Microsoft 365 Defender Streaming API](streaming-api.md) التي تسمح لاستيعاب بيانات الحدث المتدفقة من منتجات Microsoft 365 Defender عبر Event Hubs أو Azure Storage Account. لمزيد من المعلومات حول أنواع الأحداث المعتمدة، راجع [أنواع الأحداث المعتمدة](supported-event-types.md).
