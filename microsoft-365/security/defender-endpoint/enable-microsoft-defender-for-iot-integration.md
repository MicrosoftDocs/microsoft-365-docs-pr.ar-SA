---
title: تمكين تكامل Microsoft Defender for IoT في Microsoft Defender لنقطة النهاية
description: تمكين تكامل Microsoft Defender for IoT للحصول على الرؤية التي تركز على أجهزة IoT/OT في مناطق الشبكة حيث لا يتم نشر MDE
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
ms.openlocfilehash: 70d8586cb8f8babcdc709a67632f32103e9420ce
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/07/2021
ms.locfileid: "63583763"
---
# <a name="enable-microsoft-defender-for-iot-integration"></a>تمكين تكامل Microsoft Defender for IoT

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**

- [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

يمكن أن يتكامل Microsoft Defender for Endpoint الآن مع Microsoft Defender for IoT. يعمل هذا التكامل على توسيع إمكانات اكتشاف جهازك باستخدام إمكانات المراقبة بدون وكيل التي يوفرها Microsoft Defender for IoT. سيساعد ذلك على تأمين أجهزة IoT الخاصة بالمؤسسات والمتصلة بشبكة IT، مثل أجهزة Voice عبر بروتوكول الإنترنت (VoIP) والطابعات والكاميرات. وهو يسمح ل المؤسسات ب الاستفادة من حل متكامل واحد يعمل على تأمين جميع البنية الأساسية ل IoT والتقنية التشغيلية (OT). لمزيد من المعلومات، راجع [حماية شبكة Enterprise IoT](/azure/defender-for-iot/organizations/overview-eiot).

مع تمكين هذا التكامل، سيتمكن Microsoft Defender لنقطة النهاية من زيادة مستوى الرؤية للمساعدة في تحديد موقع أجهزة IoT في شبكتك وتحديدها وتأمينها. سيتم مزامنة أجهزة IoT التي اكتشفها Microsoft Defender for IoT أو Microsoft Defender ل Endpoint تلقائيا عبر المدخلين. سيمنحك ذلك طريقة عرض موحدة واحدة لمخزون OT/IoT الكامل إلى جانب باقي أجهزة IT (محطات العمل، الخوادم، والأجهزة المحمولة).

يتضمن Microsoft Defender for IoT أيضا مستشعر شبكة قابلا للنشر يوفر مصدر بيانات إضافي. يوفر لك إعداد مستشعر الشبكة كجزء من تكاملك طريقة العرض الأكثر اكتمالا لأجهزتك التي تعمل ب IoT وOT، خاصة بالنسبة إلى أجزاء الشبكة حيث لا يكون Microsoft Defender حساس نقاط النهاية موجودا، وعندما يصل الموظفون إلى المعلومات عن بعد.

## <a name="prerequisites"></a>المتطلبات الأساسية

لتمكين Microsoft Defender for IoT، يجب أن يكون للمستخدم الأدوار التالية:

- المسؤول العام للمستأجر في Azure Active Directory
- مسؤول الأمان لاشتراك Azure الذي سيتم استخدامه لتكامل Microsoft Defender for IoT

## <a name="enabling-the-microsoft-defender-for-iot-integration"></a>تمكين تكامل Microsoft Defender for IoT

1. في جزء التنقل من [https://security.microsoft.com](https://security.microsoft.com/) المدخل **، حدد الإعدادات** \> **اكتشاف** \> **جهاز Microsoft Defender ل IoT**.

    ![صورة لإعداد تكامل IoT.](images/enable-defender-for-iot.png)

2. **حدد اشتراك Azure** من القائمة المنسدلة للاشتراكات المتوفرة في مستأجر Azure Active Directory وحدد **حفظ**.

## <a name="set-up-a-network-sensor"></a>إعداد مستشعر الشبكة

باستخدام اشتراك Azure المحدد، يمكنك إضافة مستشعر الشبكة.

لإضافة مستشعر شبكة، ضمن **إعداد أدوات استشعار الشبكة** ، اختر **ارتباط Microsoft Defender for IoT** . سيعيدك ذلك إلى عملية إعداد مستشعر Onboard في مدخل Azure. لمزيد من المعلومات، راجع [إدارة أدوات الاستشعار باستخدام Defender for IoT في مدخل Azure](/azure/defender-for-iot/organizations/how-to-manage-sensors-on-the-cloud).

## <a name="turn-off-subscription-integration"></a>إيقاف تشغيل تكامل الاشتراك

يمكنك إيقاف تشغيل تكامل اشتراك Azure من صفحة إعدادات Microsoft Defender for IoT في [https://security.microsoft.com](https://security.microsoft.com/) المدخل. بمجرد إيقاف تشغيل الاشتراك، لن ترى أجهزة IoT التي اكتشفها Microsoft Defender for IoT في مخزون أجهزة Microsoft Defender for Endpoint.

## <a name="see-also"></a>راجع أيضًا

- [نظرة عامة على اكتشاف الجهاز](configure-device-discovery.md)
- [الأسئلة الشائعة حول اكتشاف الجهاز](device-discovery-faq.md)
