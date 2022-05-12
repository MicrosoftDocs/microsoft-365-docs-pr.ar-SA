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
ms.openlocfilehash: 629d475c160d5836d155ca0374630ad64b0928b4
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372010"
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
> يتوفر التكامل في برنامج Corelight Sensor v25 والإي وقت لاحق.
> 
> ستحتاج إلى اتصال بالإنترنت لأداة الاستشعار الخاصة بك للوصول إلى كل من خدمات السحابة Defender و Corelight لكي يعمل الحل.

#### <a name="enable-the-integration-in-the-corelight-web-interface"></a>تمكين التكامل في واجهة ويب Corelight

1. في واجهة الويب Corelight، انتقل إلى **Sensor** \> **Export**.

   :::image type="content" source="images/exporttodefender.png" alt-text="تصدير kafka" lightbox="images/exporttodefender.png":::

2. تمكين **التصدير إلى Microsoft Defender**.
3. أدخل معرف مستأجر Microsoft 356 Defender.
4. اختياريا، يمكنك:
    - تعيين **سجلات Zeek إلى Exclude**. الحد الأدنى من مجموعة السجلات التي يجب تضمينها هي: dns، conn، files، http، ssl، ssh، x509، snmp، smtp، ftp، sip، dhcp، والإشعار.
    - اختر إنشاء **عامل تصفية سجل Microsoft Defender**.
5. حدد **تطبيق التغييرات**.

#### <a name="enable-the-integration-in-the-corelight-client"></a>تمكين التكامل في corelight-client

1. تمكين **التصدير إلى Microsoft Defender** باستخدام الأمر التالي في corelight-client:

    ``` command
    corelight-client configuration update \
    --bro.export.defender.enable True
    ```

2. تعيين معرف المستأجر

3. بشكل اختياري، يمكنك استخدام الأمر التالي لاستبعاد سجلات معينة أو لإنشاء عامل تصفية سجل Microsoft Defender. الحد الأدنى من مجموعة السجلات التي يجب تضمينها هي: dns، conn، files، http، ssl، ssh، x509، snmp، smtp، ftp، sip، dhcp، والإشعار.

   ``` command
     corelight-client configuration update \
    --bro.export.defender.exclude=<logs_to_exclude> \
    --bro.export.defender.filter=<logs_to_filter>
   ```

## <a name="see-also"></a>راجع أيضًا

- [الأسئلة الشائعة حول اكتشاف الجهاز](device-discovery-faq.md)
