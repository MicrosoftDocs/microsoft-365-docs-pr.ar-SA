---
title: تمكين تكامل Corelight في Microsoft Defender لنقطة النهاية
description: تمكين تكامل Corelight للحصول على رؤية تركز على أجهزة IoT/OT في مناطق من الشبكة حيث لا يتم نشر MDE
keywords: تمكين siem connector و siem و connector ومعلومات الأمان والأحداث
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
ms.openlocfilehash: bf3095b9178b4ff2e71d4ee5f652d9316f233746
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664579"
---
# <a name="enable-corelight-data-integration"></a>تمكين تكامل بيانات Corelight

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

اشتركت Microsoft مع [Corelight](https://corelight.com/integrations/iot-security)، موفر النظام الأساسي الرائد للكشف عن الشبكات المفتوحة والاستجابة لها (NDR) في الصناعة، لمساعدتك على اكتشاف أجهزة IoT/OT عبر مؤسستك. باستخدام البيانات المرسلة من أجهزة شبكة Corelight، Microsoft 365 Defender زيادة الرؤية في أنشطة الشبكة للأجهزة غير المدارة، بما في ذلك الاتصال بالأجهزة الأخرى غير المدارة أو الشبكات الخارجية.

مع تمكين مصدر البيانات هذا، يتم إرسال جميع الأحداث من أجهزة شبكة Corelight إلى Microsoft 365 Defender. يمكنك عرض هذه الأنشطة في المخطط الزمني للأجهزة غير المدارة، والمتوفر في مخزون جهاز Microsoft Defender لنقطة النهاية. لمزيد من المعلومات، راجع [اكتشاف الجهاز](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>تمكين تكامل Corelight

لتمكين تكامل Corelight، ستحتاج إلى اتخاذ الخطوات التالية:

[الخطوة 1: تشغيل Corelight كمصدر بيانات](#step-1-turn-on-corelight-as-a-data-source)<br>
[الخطوة 2: توفير إذن ل Corelight لإرسال الأحداث إلى Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[الخطوة 3: تكوين جهاز Corelight لإرسال البيانات إلى Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>الخطوة 1: تشغيل Corelight كمصدر بيانات

1. في جزء التنقل من [https://security.microsoft.com](https://security.microsoft.com/) المدخل، حدد **الإعدادات** \> **Device discovery** \> **Data sources**.

   :::image type="content" source="images/enable-corelight.png" alt-text="صفحة مصادر البيانات في مدخل Microsoft 365 Defender" lightbox="images/enable-corelight.png":::

2. حدد **إرسال بيانات Corelight إلى M365D** وحدد **Save**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>الخطوة 2: توفير إذن ل Corelight لإرسال الأحداث إلى Microsoft 365 Defender

> [!NOTE]
> يجب أن تكون مسؤولا عاما لمنح Corelight الإذن للوصول إلى الموارد في مؤسستك.

1. كمسؤول عام للمستأجر، انتقل إلى هذا [الارتباط](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) لمنح الإذن.
2. انتقل إلى [https://security.microsoft.com](https://security.microsoft.com/) المدخل، وحدد **الإعدادات** \> **Microsoft 365 Defender**، ولاحظ **معرف المستأجر**. ستحتاج إلى هذه المعلومات عند تكوين جهاز Corelight.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>الخطوة 3: تكوين جهاز Corelight لإرسال البيانات إلى Microsoft 365 Defender

> [!NOTE]
>  سيكون التكامل عاما في برنامج Corelight Sensor v24 والإي وقت لاحق. 

للمعاينة في v23 أو v22.1 يجب عليك التنفيذ `corelight-client configuration update --enable.adfiot 1` لتمكين مقطع التكوين في واجهة المستخدم الرسومية.

بالإضافة إلى ذلك، يتطلب التحقق من صحة واجهة المستخدم الرسومية تكوين وسيط في قسم التكوين على جميع إصدارات v23.  الوسيط الذي توفره مطلوب ولكن لن يتم استخدامه بالفعل. أدخل `127.0.0.1:1234` في حقل _وسيط kafka_ لضمان التحقق من الصحة بنجاح قبل اتباع الخطوات أدناه لتمكين إرسال البيانات إلى Microsoft 365 Defender.

> [!NOTE]
> ستحتاج إلى اتصال بالإنترنت لأداة الاستشعار الخاصة بك للوصول إلى كل من خدمات السحابة Defender و Corelight لكي يعمل الحل.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>التمكين في واجهة المستخدم الرسومية لأداة استشعار Corelight

1. في قسم تكوين واجهة المستخدم الرسومية لأداة استشعار Corelight، حدد **"تصدير جهاز الاستشعار**\>".
2. من القائمة، انتقل إلى **EXPORT TO KAFKA** وحدد مفتاح التبديل لتشغيله.

   :::image type="content" source="images/exporttokafka.png" alt-text="تصدير kafka" lightbox="images/exporttokafka.png":::

3. بعد ذلك، قم بتشغيل **EXPORT TO AZURE DEFENDER FOR IOT** وأدخل معرف المستأجر الخاص بك، المذكور في الخطوة 1، في حقل معرف المستأجر.

   :::image type="content" source="images/exporttodiot.png" alt-text="تصدير iot" lightbox="images/exporttodiot.png":::

4. حدد **تطبيق التغييرات**.

   :::image type="content" source="images/corelightapply.png" alt-text="أيقونة تطبيق التغييرات" lightbox="images/corelightapply.png":::

> [!NOTE]
> يجب عدم تغيير خيارات التكوين في Kafka (باستثناء استثناء السجل وعوامل التصفية). سيتم تجاهل أي تغييرات تم إجراؤها.

#### <a name="enabling-in-the-corelight-client"></a>التمكين في corelight-client

يمكنك تشغيل **EXPORT TO KAFKA** و **EXPORT إلى AZURE DEFENDER FOR IOT** باستخدام الأمر التالي في corelight-client:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> إذا كنت تستخدم بالفعل تصدير Kafka، فاتصل بدعم Corelight لتكوين بديل.

لتكوين إرسال الحد الأدنى من السجلات فقط:

1. في واجهة المستخدم الرسومية لأداة استشعار Corelight، انتقل إلى قسم Kafka
2. انتقل إلى **سجلات Zeek لاستبعادها**
3. تحديد **الكل**
4. ثم حدد **x** بجانب السجلات التالية للتأكد من استمرار تدفقها إلى Microsoft:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. تحديد **تطبيق التغييرات**

قد تتوسع قائمة السجلات التي تتدفق إلى Microsoft بمرور الوقت.

## <a name="see-also"></a>راجع أيضًا

- [الأسئلة الشائعة حول اكتشاف الجهاز](device-discovery-faq.md)
