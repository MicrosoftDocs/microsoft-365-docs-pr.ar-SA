---
title: التحقق من أحداث الاتصال التي تحدث خلف نيات إعادة توجيه
description: تعرف على كيفية استخدام مراقبة مستوى HTTP المتقدمة من خلال حماية الشبكة في Microsoft Defender ل Endpoint، مما يؤدي إلى سطوح هدف حقيقي بدلا من وكيل.
keywords: الوكيل، حماية الشبكة، الوكيل إعادة توجيه، أحداث الشبكة، التدقيق، الحظر، أسماء المجالات، المجال
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c0a2bdab641f0289975f1d8475627d3066ecf1f8
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 01/12/2022
ms.locfileid: "63572356"
---
# <a name="investigate-connection-events-that-occur-behind-forward-proxies"></a>التحقق من أحداث الاتصال التي تحدث خلف نيات إعادة توجيه

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

يدعم Defender ل Endpoint مراقبة اتصال الشبكة من مستويات مختلفة من مكدس الشبكة. من الصعب جدا أن تستخدم الشبكة وكيلا للأمام كبوابة إلى الإنترنت.

يعمل الوكيل كما لو كان نقطة النهاية الهدف. في هذه الحالات، ستدقق أجهزة عرض اتصال الشبكة البسيطة في الاتصالات بالوكيل الصحيح ولكن له قيمة تحقيق أقل.

يدعم Defender for Endpoint مراقبة مستوى HTTP المتقدمة من خلال حماية الشبكة. عند تشغيل الحدث، يتم عرض نوع جديد من الأحداث يعرض أسماء المجالات الهدف الحقيقية.

## <a name="use-network-protection-to-monitor-network-connection-behind-a-firewall"></a>استخدام حماية الشبكة لمراقبة اتصال الشبكة خلف جدار حماية

يمكن مراقبة اتصال الشبكة خلف وكيل إعادة توجيه بسبب أحداث الشبكة الأخرى التي تنشأ من حماية الشبكة. لمشاهدتها على مخطط زمني للجهاز، قم تشغيل حماية الشبكة (كحد أدنى في وضع التدقيق).

يمكن التحكم في حماية الشبكة باستخدام الأوضاع التالية:

- **الحظر**: سيتم حظر المستخدمين أو التطبيقات من الاتصال والمجالات الخطيرة. وستتمكن من رؤية هذا النشاط في Microsoft 365 Defender.
- **التدقيق**: لن يتم حظر المستخدمين أو التطبيقات من الاتصال والمجالات الخطيرة. ومع ذلك، ستشاهد هذا النشاط في Microsoft 365 Defender.


إذا قمت إيقاف تشغيل حماية الشبكة، لن يتم حظر المستخدمين أو التطبيقات من الاتصال والمجالات الخطيرة. لن ترى أي نشاط شبكة في Microsoft 365 Defender.

إذا لم تكن قد قمت بتكوينه، سيتم إيقاف تشغيل حظر الشبكة بشكل افتراضي.

لمزيد من المعلومات، راجع [تمكين حماية الشبكة](enable-network-protection.md).

## <a name="investigation-impact"></a>تأثير التحقيق

عند تشغيل حماية الشبكة، سترى أنه على المخطط الزمني لجهاز ما، سيبقى عنوان IP يمثل الوكيل، بينما يظهر العنوان الهدف الحقيقي.

![صورة أحداث الشبكة على المخطط الزمني للجهاز.](images/atp-proxy-investigation.png)

تتوفر الآن الأحداث الأخرى التي يتم تشغيلها بواسطة طبقة حماية الشبكة لسطح أسماء المجالات الحقيقية حتى خلف وكيل.

معلومات الحدث:

![صورة حدث شبكة واحد.](images/atp-proxy-investigation-event.png)

## <a name="hunt-for-connection-events-using-advanced-hunting"></a>البحث عن أحداث الاتصال باستخدام الصيد المتقدم

تتوفر لك كل أحداث الاتصال الجديدة للصيد من خلال الصيد المتقدم أيضا. بما أن هذه الأحداث هي أحداث اتصال، يمكنك العثور عليها ضمن الجدول DeviceNetworkEvents ضمن `ConnecionSuccess` نوع الإجراء.

سيعرض لك استخدام هذا الاستعلام البسيط كل الأحداث ذات الصلة:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| take 10
```

![صورة استعلام بحث متقدم.](images/atp-proxy-investigation-ah.png)

يمكنك أيضا تصفية الأحداث المرتبطة بالاتصال بالوكيل نفسه.

استخدم الاستعلام التالي لتصفية الاتصالات بالوكيل:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" and RemoteIP != "ProxyIP"
| take 10
```

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تطبيق حماية الشبكة باستخدام GP - نهج CSP](/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)
