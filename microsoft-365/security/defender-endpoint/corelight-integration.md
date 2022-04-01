---
title: تمكين تكامل Corelight في Microsoft Defender لنقطة النهاية
description: تمكين تكامل Corelight للحصول على الرؤية التي تركز على أجهزة IoT/OT في مناطق الشبكة حيث لا يتم نشر MDE
keywords: تمكين موصل siem، siem، الموصل، معلومات الأمان والأحداث
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 3a7a4b7ab842baaadb276e60037451e8eb919bf9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465441"
---
# <a name="enable-corelight-data-integration"></a>تمكين تكامل بيانات Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

لقد قامت Microsoft ب شراكة مع [Corelight](https://corelight.com/integrations/iot-security)، موفر النظام الأساسي المفتوح للكشف عن الشبكة والاستجابة (NDR) في المجال، لمساعدتك على اكتشاف أجهزة IoT/OT عبر مؤسستك. باستخدام البيانات، المرسلة من أجهزة شبكة Corelight، Microsoft 365 Defender رؤية أكثر في أنشطة الشبكة للأجهزة غير المراقبة، بما في ذلك الاتصال بأجهزة أخرى غير مستخدمة أو شبكات خارجية.

مع تمكين مصدر البيانات هذا، يتم إرسال كل الأحداث من أجهزة شبكة Corelight إلى Microsoft 365 Defender. يمكنك عرض هذه الأنشطة في المخطط الزمني للأجهزة غير التي يتم إدارةها، والمتوفر في Microsoft Defender لنقطة النهاية الأجهزة. لمزيد من المعلومات، راجع [اكتشاف الجهاز](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>تمكين تكامل Corelight

لتمكين تكامل Corelight، ستحتاج إلى اتخاذ الخطوات التالية:

[الخطوة 1: تشغيل Corelight كمصدر بيانات](#step-1-turn-on-corelight-as-a-data-source)<br>
[الخطوة 2: توفير إذن ل Corelight لإرسال الأحداث إلى Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[الخطوة 3: تكوين جهاز Corelight لإرسال البيانات إلى Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>الخطوة 1: تشغيل Corelight كمصدر بيانات

1. في جزء التنقل من [https://security.microsoft.com](https://security.microsoft.com/) المدخل **، حدد الإعدادات** \> **بيانات** \> اكتشاف **الجهاز**.

   :::image type="content" source="images/enable-corelight.png" alt-text="صفحة مصادر البيانات في مدخل Microsoft 365 Defender" lightbox="images/enable-corelight.png":::

2. حدد **إرسال بيانات Corelight إلى M365D** وحدد **حفظ**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>الخطوة 2: توفير إذن ل Corelight لإرسال الأحداث إلى Microsoft 365 Defender

> [!NOTE]
> يجب أن تكون المسؤول العام لمنح إذن Corelight للوصول إلى الموارد في مؤسستك.

1. كمسؤول عام للمستأجر، انتقل إلى هذا [الارتباط](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) لمنح الإذن.
2. انتقل إلى [https://security.microsoft.com](https://security.microsoft.com/) المدخل، **وحدد** \> الإعدادات **Microsoft 365 Defender**، ثم دون "بطاقة **المستأجر**". ستحتاج إلى هذه المعلومات عند تكوين جهاز Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>الخطوة 3: تكوين جهاز Corelight لإرسال البيانات إلى Microsoft 365 Defender

> [!NOTE]
>  سيكون التكامل عاما في برنامج Corelight Sensor v24 واللاحقة. 

للمعاينة في الإصدار 23 أو v22.1، `corelight-client configuration update --enable.adfiot 1` يجب تنفيذ لتمكين مقطع التكوين في واجهة المستخدم (GUI).

بالإضافة إلى ذلك، يتطلب التحقق من صحة واجهة المستخدم (GUI) تكوين وسيط في مقطع التكوين على كل إصدارات v23.  الوسيط الذي توفره مطلوب ولكن لن يتم استخدامه فعليا. أدخل `127.0.0.1:1234` في حقل _وسيط kafka_ لضمان نجاح عملية التحقق من الصحة قبل اتباع الخطوات أدناه لتمكين إرسال البيانات إلى Microsoft 365 Defender.

> [!NOTE]
> ستحتاج إلى اتصال بالإنترنت حتى يصل المستشعر إلى كل من خدمات السحابة Defender و Corelight حتى يعمل الحل.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>التمكين في واجهة GUI لمستشعر Corelight

1. في المقطع تكوين واجهة GUI لمستشعر Corelight، حدد **تصدير المستشعر**\>.
2. من القائمة، انتقل إلى **تصدير إلى KAFKA** وحدد مفتاح التبديل لكي يتم تشغيلها.

   :::image type="content" source="images/exporttokafka.png" alt-text="تصدير kafka" lightbox="images/exporttokafka.png":::

3. بعد ذلك، قم بتصدير **إلى AZURE DEFENDER ل IOT** وأدخل "الم IOT" الخاص بك للمستأجر، كما هو ملاحظ في الخطوة 1، في حقل "الم ID المستأجر".

   :::image type="content" source="images/exporttodiot.png" alt-text="تصدير iot" lightbox="images/exporttodiot.png":::

4. حدد **تطبيق التغييرات**.

   :::image type="content" source="images/corelightapply.png" alt-text="الأيقونة &quot;تطبيق التغييرات&quot;" lightbox="images/corelightapply.png":::

> [!NOTE]
> يجب عدم تغيير خيارات التكوين في كافكا (باستثناء استبعاد السجل و عوامل التصفية). سيتم تجاهل أي تغييرات تم إدخالها.

#### <a name="enabling-in-the-corelight-client"></a>التمكين في corelight-client

يمكنك تشغيل تصدير إلى **KAFKA** وتصدير إلى **AZURE DEFENDER ل IOT** باستخدام الأمر التالي في corelight-client:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> إذا كنت تستخدم تصدير كافكا بالفعل، فاتصل ب دعم Corelight للحصول على تكوين بديل.

لتكوين إرسال مجموعة السجلات الدنيا فقط:

1. في واجهة GUI لمستشعر Corelight، انتقل إلى مقطع Kafka
2. الانتقال إلى **سجلات Zeek لاستبعادها**
3. تحديد **الكل**
4. ثم حدد **x** بجانب السجلات التالية للتأكد من استمرار تدفقها إلى Microsoft:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. حدد **تطبيق التغييرات**

قد يتم توسيع قائمة السجلات التي تتدفق إلى Microsoft مع مرور الوقت.

## <a name="see-also"></a>راجع أيضًا

- [الأسئلة الشائعة حول اكتشاف الجهاز](device-discovery-faq.md)
