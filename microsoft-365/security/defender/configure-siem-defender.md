---
title: ادمج أدوات SIEM مع Microsoft 365 Defender
description: تعرف على كيفية استخدام REST API وتكوين أدوات إدارة أحداث ومعلومات الأمان المعتمدة لتلقي الكشف وسحبه.
keywords: تكوين siem ومعلومات الأمان وأدوات إدارة الأحداث، وslunk، وقوس النظر، والمؤشرات المخصصة، وبرمجة التطبيقات، وتعريفات التنبيهات، ومؤشرات اختراق
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
ms.openlocfilehash: 210705bd3392e4aeeadd815ed8c1840e772f6ad9
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/19/2021
ms.locfileid: "63575140"
---
# <a name="integrate-your-siem-tools-with-microsoft-365-defender"></a>ادمج أدوات SIEM مع Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="pull-microsoft-365-defender-incidents-and-streaming-event-data-using-security-information-and-events-management-siem-tools"></a>سحب Microsoft 365 Defender البيانات وتدفق بيانات الأحداث باستخدام أدوات إدارة أحداث ومعلومات الأمان (SIEM)

> [!NOTE]
>
> - [Microsoft 365 Defender الأحداث](incident-queue.md) على مجموعات من التنبيهات المرتبطة ودلليلها.
> - [Microsoft 365 Defender تدفق API](streaming-api.md) إلى دفق بيانات الحدث من Microsoft 365 Defender إلى مراكز الأحداث أو حسابات تخزين Azure.

يدعم Microsoft 365 Defender معلومات الأمان وأدوات إدارة الأحداث (SIEM) التي تستخدم المعلومات من مستأجر المؤسسة في Azure Active Directory (AAD (دليل Azure النشط)) باستخدام بروتوكول مصادقة OAuth 2.0 لمستأجر AAD (دليل Azure النشط)  تطبيق يمثل حل SIEM المحدد أو الموصل المثبت في بيئتك. 

لمزيد من المعلومات، اطلع على:

- [Microsoft 365 Defender واجهات برمجة التطبيقات شروط الاستخدام وترخيصها](api-terms.md)
- [الوصول إلى Microsoft 365 Defender واجهات برمجة التطبيقات](api-access.md)
- [مثال Hello World](api-hello-world.md)
- [الوصول باستخدام سياق التطبيق](api-create-app-web.md)

هناك نموذجان أساسيان لأهم معلومات الأمان: 

1.  يتم Microsoft 365 Defender الأحداث وتنبيهاتها المضمنة من API REST في Azure. 

2.  استخدام بيانات حدث النقل المتدفق إما من خلال Azure Event Hubs أو حسابات تخزين Azure. 

Microsoft 365 Defender حاليا عمليات تكامل حل SIEM التالية: 

- [أحداث الاحتكاء من الأحداث REST API](#ingesting-incidents-from-the-incidents-rest-api)
- [استخدام بيانات حدث النقل المتدفق عبر مركز الأحداث](#ingesting-streaming-event-data-via-event-hubs)

## <a name="ingesting-incidents-from-the-incidents-rest-api"></a>أحداث الاحتكاء من الأحداث REST API

### <a name="incident-schema"></a>مخطط حادث
لمزيد من المعلومات حول خصائص Microsoft 365 Defender بما في ذلك بيانات تعريف كيانات التنبيهات والدليل المضمنة، راجع [تعيين المخطط](../defender/api-list-incidents.md#schema-mapping).

### <a name="splunk"></a>Splunk

استخدام Microsoft 365 Defender الإضافية ل Splunk التي تدعم:

- أحداث الاقتصاص التي تحتوي على تنبيهات من المنتجات التالية، والتي تم تعيينها إلى نموذج المعلومات الشائع (CIM) الخاص ب Splunk):

  - Microsoft 365 Defender
  - Microsoft Defender لنقطة النهاية
  - حماية هوية Microsoft Defender for Identity و Azure Active Directory
  - Microsoft Defender لتطبيقات السحابة

- تحديث الأحداث في Microsoft 365 Defender من داخل Splunk

- Ingesting Defender لتنبيهات نقطة النهاية (من نقطة نهاية Azure ل Defender for Endpoint) وتحديث هذه التنبيهات

لمزيد من المعلومات حول Microsoft 365 Defender الإضافية ل Splunk، راجع [splunkbase](https://splunkbase.splunk.com/app/4959/).

### <a name="micro-focus-arcsight"></a>Micro Focus ArcSight

يعمل SmartConnector الجديد Microsoft 365 Defender الأحداث إلى ArcSight ويدخلها في إطار الحدث المشترك (CEF).

لمزيد من المعلومات حول ArcSight SmartConnector الجديد Microsoft 365 Defender، راجع [وثائق منتج ArcSight](https://community.microfocus.com/cyberres/productdocs/w/connector-documentation/39246/smartconnector-for-microsoft-365-defender).

يحل SmartConnector محل FlexConnector السابق ل Microsoft Defender لنقطة النهاية.
  

## <a name="ingesting-streaming-event-data-via-event-hubs"></a>استخدام بيانات حدث النقل المتدفق عبر "مراكز الأحداث"

ستحتاج أولا إلى دفق الأحداث من AAD (دليل Azure النشط) المستأجر إلى مركز الأحداث أو حساب تخزين Azure. لمزيد من المعلومات، راجع [تدفق API](../defender/streaming-api.md).

لمزيد من المعلومات حول أنواع الأحداث المعتمدة بواسطة API للدفق، راجع [أنواع أحداث النقل المتدفق المعتمدة](../defender/supported-event-types.md).

### <a name="splunk"></a>Splunk
استخدم "الوظائف الإضافية ل Splunk" ل Microsoft Cloud Services لالتدراج الأحداث من Azure Event Hubs.  


لمزيد من المعلومات حول الوظائف الإضافية Splunk ل Microsoft Cloud Services، راجع [splunkbase](https://splunkbase.splunk.com/app/3110/).
  

### <a name="ibm-qradar"></a>IBM QRadar
>استخدم وحدة IBM QRadar الجديدة Microsoft 365 Defender دعم الأجهزة (DSM) التي تستدعي [Microsoft 365 Defender API](streaming-api.md) المتدفقة التي تسمح باحتواء بيانات حدث النقل المتدفق من Microsoft 365 Defender البيانات. لمزيد من المعلومات حول أنواع الأحداث المعتمدة، راجع [أنواع الأحداث المعتمدة](supported-event-types.md).
