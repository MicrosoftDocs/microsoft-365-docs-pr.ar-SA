---
title: أجهزة غير Windows إلى خدمة Microsoft Defender for Endpoint
description: قم بتكوين أجهزة Windows بحيث يمكنها إرسال بيانات المستشعر إلى خدمة Microsoft Defender لنقطة النهاية.
keywords: أجهزة غير Windows، macos، linux، إدارة الأجهزة، تكوين Microsoft Defender للأجهزة Endpoint
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
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 4573e7002454e9e72648df42352104abaa4c22d6
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63571409"
---
# <a name="onboard-non-windows-devices"></a>الأجهزة غير المجهزة Windows

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**الأنظمة الأساسية**
- macOS
- Linux

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-nonwindows-abovefoldlink)

يوفر Defender for Endpoint تجربة عمليات أمان مركزية Windows الأنظمة Windows الأساسية. ستكون قادرا على رؤية التنبيهات من أنظمة التشغيل المدعمة المختلفة (OS) في Microsoft 365 Defender وحماية شبكة مؤسستك بشكل أفضل.

ستحتاج إلى معرفة إصدارات Linux و macOS الدقيقة المتوافقة مع Defender for Endpoint لكي يعمل التكامل. لمزيد من المعلومات، اطلع على:

- [متطلبات النظام ل Microsoft Defender for Endpoint على Linux](microsoft-defender-endpoint-linux.md#system-requirements)
- [Microsoft Defender ل Endpoint على متطلبات نظام macOS](microsoft-defender-endpoint-mac.md#system-requirements).

## <a name="onboarding-non-windows-devices"></a>اجهزه غير Windows

ستحتاج إلى اتخاذ الخطوات التالية لترك الأجهزة غير Windows:

1. حدد الطريقة المفضلة لديك للتك الجديدة:

   - بالنسبة إلى أجهزة macOS، يمكنك اختيار ال متن الطائرة من خلال Microsoft Defender ل Endpoint أو من خلال حل جهة خارجية. لمزيد من المعلومات، راجع [Microsoft Defender ل Endpoint على Mac](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint-mac).

   - بالنسبة للأجهزة الأخرى غير Windows، اختر أجهزة غير Windows من خلال **تكامل جهة خارجية**.
    1. في جزء التنقل، حدد **الشركاء وتطبيقات شركاء واجهات** \> برمجة **التطبيقات** . تأكد من إدراج حل  جهة خارجية.
    2. في صفحة **تطبيقات** الشركاء، حدد الشريك الذي يدعم أجهزتك غير Windows.
    3. انقر **فوق** عرض لفتح صفحة الشريك. اتبع الإرشادات المتوفرة على الصفحة.
    4. بعد إنشاء حساب أو الاشتراك في حل الشريك، يجب أن تحصل على مرحلة يطلب فيها من المسؤول العام للمستأجر في مؤسستك قبول طلب إذن من تطبيق الشريك. اقرأ طلب الإذن بعناية للتأكد من محاذاته مع الخدمة التي تحتاج إليها.

2. تشغيل اختبار الكشف باتباع إرشادات حل  جهة خارجية.

## <a name="offboard-non-windows-devices"></a>إيقاف تشغيل الأجهزة غير Windows

بالنسبة إلى أجهزة macOS و Linux، يمكنك اختيار إيقاف التشغيل من خلال Microsoft Defender ل Endpoint. في جزء التنقل **، حدد الإعدادات** \> **إيقاف** \> التشغيل حدد **نظام التشغيل لبدء عملية إيقاف التشغيل**.

يمكنك أيضا إيقاف تشغيل الأجهزة غير Windows عن طريق تعطيل التكامل مع جهة خارجية. تمكين تغطية الأجهزة التي تعمل Windows من خلال [دمج حلول الأطراف الخارجية](https://security.microsoft.com/interoperability/partners).

## <a name="related-topics"></a>المواضيع ذات الصلة
- [أجهزة Windows](configure-endpoints.md)
- [خوادم على اللوحة](configure-server-endpoints.md)
- [تكوين إعدادات الوكيل والاتصال بالإنترنت](configure-proxy-internet.md)
- [استكشاف مشاكل تشغيل نقطة النهاية وإصلاحها في Microsoft Defender](troubleshoot-onboarding.md)
