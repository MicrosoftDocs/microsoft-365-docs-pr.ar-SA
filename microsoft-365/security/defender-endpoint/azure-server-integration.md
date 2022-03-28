---
title: التكامل مع Microsoft Defender for Cloud
description: تعرف على تكامل Microsoft Defender for Endpoint مع Microsoft Defender for Cloud
keywords: التكامل، الخادم، azure، 2012r2، 2016، 2019، تهيئة الخادم، إدارة الأجهزة، تكوين Microsoft Defender للخوادم Endpoint، تهيئة Microsoft Defender للخوادم Endpoint، تهيئة Microsoft Defender للخوادم Endpoint
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2ed9d25336cd7e8162849aa5d1d1a3e3382063fc
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63575094"
---
# <a name="integration-with-microsoft-defender-for-cloud"></a>التكامل مع Microsoft Defender for Cloud

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender for Cloud

يمكن ل Microsoft Defender ل Endpoint التكامل مع Microsoft Defender for Cloud لتوفير حل شامل Windows حماية الخادم. من خلال هذا التكامل، يمكن ل Microsoft Defender for Cloud استخدام قوة Defender for Endpoint لتوفير اكتشاف محسن للتهديدات Windows الخادمة.

يتم تضمين الإمكانات التالية في هذا التكامل:

- التشغيل التلقائي - يتم تمكين مستشعر Defender لنقطة النهاية تلقائيا على Windows الخوادم التي تم تشغيلها في Microsoft Defender for Cloud. لمزيد من المعلومات حول Microsoft Defender لدمج السحابة، راجع [استخدام ترخيص نقطة النهاية المتكامل ل Microsoft Defender](/azure/security-center/security-center-wdatp).

    > [!NOTE]
    > تم توسيع التكامل بين Microsoft Defender للخوادم و Microsoft Defender لنقطة النهاية لدعم Windows [Server 2019 Windows Virtual Desktop (WVD)](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview) .

- Windows الخوادم التي يراقبها Microsoft Defender for Cloud أيضا في Defender for Endpoint - يتصل Microsoft Defender for Cloud بسلاسة بمستأجر Defender for Endpoint، مما يوفر طريقة عرض واحدة عبر العملاء الخوادم.  بالإضافة إلى ذلك، ستتوفر تنبيهات Defender لنقطة النهاية في وحدة تحكم Microsoft Defender for Cloud.
- تحقيق الخادم - يمكن لعملاء Microsoft Defender for Cloud الوصول إلى مدخل Microsoft 365 Defender لإجراء تحقيق مفصل للكشف عن نطاق الانتهاك المحتمل.

> [!IMPORTANT]
> - عند استخدام Microsoft Defender for Cloud لمراقبة الخوادم، يتم تلقائيا إنشاء مستأجر Defender for Endpoint (في الولايات المتحدة للمستخدمين الأميركيين، في الاتحاد الأوروبي للمستخدمين الأوروبيين والمملكة المتحدة).<br>
يتم تخزين البيانات التي يقوم Defender for Endpoint بتجميعها في الموقع الجغرافي للمستأجر كما هو محدد أثناء توفيرها.
> - إذا كنت تستخدم Defender ل Endpoint قبل استخدام Microsoft Defender for Cloud، سيتم تخزين بياناتك في الموقع الذي حددته عند إنشاء المستأجر الخاص بك حتى لو قمت بالدمج مع Microsoft Defender for Cloud في وقت لاحق.
> - بمجرد تكوينها، لا يمكنك تغيير الموقع الذي تم تخزين البيانات فيه. إذا كنت بحاجة إلى نقل بياناتك إلى موقع آخر، يجب الاتصال بدعم Microsoft لإعادة تعيين المستأجر. <br>
تم تعطيل مراقبة نقطة نهاية الخادم باستخدام هذا التكامل Office 365 سحابة القطاع الحكومي العملاء.



## <a name="related-topics"></a>المواضيع ذات الصلة
- [الإصدارات السابقة من Windows](onboard-downlevel.md)
- [الإصدار Windows Server 2012 R2 و2016 وSAC الإصدار 1803 و2019](configure-server-endpoints.md)
