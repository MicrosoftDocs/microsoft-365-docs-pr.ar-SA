---
title: Defender لنقطة النهاية لإلحاق Windows Server
description: إلحاق Windows Server Microsoft Defender لنقطة النهاية.
keywords: الإلحاق، Microsoft Defender لنقطة النهاية الإلحاق، sccm، نهج المجموعة، mdm، البرنامج النصي المحلي، اختبار الكشف
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b25d60be243dd5d375fb6ed0f795e4a901a504b2
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857465"
---
# <a name="defender-for-endpoint-onboarding-windows-server"></a>Defender لنقطة النهاية لإلحاق Windows Server

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- Windows Server 2012 R2
- Windows Server 2016‏
- Windows Server Semi-Annual قناة المؤسسة
- Windows Server 2019 والإطارات الأحدث
- إصدار Windows Server 2019 الأساسي
- Windows Server 2022
- [مشكلات الأداء في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https:%2F%2Faka.ms%2FMDEp2OpenTrial)

ستحتاج إلى الانتقال من خلال قسم الإلحاق في مدخل Defender لنقطة النهاية لإلحاق أي من الأجهزة المدعومة. اعتمادا على الجهاز، سيتم إرشادك بالخطوات المناسبة وتوفير خيارات أداة الإدارة والتوزيع المناسبة للجهاز.

يقوم Defender لنقطة النهاية بتوسيع الدعم ليشمل أيضا نظام التشغيل Windows Server. يوفر هذا الدعم قدرات متقدمة للكشف عن الهجمات والتحقيق فيها بسلاسة من خلال وحدة التحكم Microsoft 365 Defender. يوفر دعم Windows Server رؤية أعمق لأنشطة الخادم، وتغطية الكشف عن هجمات النواة والذاكرة، وتمكين إجراءات الاستجابة.

يصف هذا الموضوع كيفية إلحاق خوادم Windows معينة Microsoft Defender لنقطة النهاية.

للحصول على إرشادات حول كيفية تنزيل أمن Windows الأساسات لخوادم Windows واستخدامها، راجع [أمن Windows الأساسات.](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-baselines)

## <a name="windows-server-onboarding-overview"></a>نظرة عامة على إلحاق Windows Server

ستحتاج إلى إكمال الخطوات العامة التالية لإلحاق الخوادم 2008 R2، 2012 R2، 2016، 2019، 2022 بنجاح.

:::image type="content" source="images/server-onboarding.png" alt-text="إلحاق الخادم" lightbox="images/server-onboarding.png":::

> [!NOTE]
> يتم إلحاق الخوادم باستخدام GPs فقط.

### <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 وWindows Server 2016
- تنزيل حزم التثبيت والإلحاق.
- تطبيق حزمة التثبيت.
- اتبع خطوات الإلحاق للأداة المقابلة.

### <a name="windows-server-semi-annual-enterprise-channel-and-windows-server-2019"></a>Windows Server Semi-Annual Enterprise Channel وWindows Server 2019
- قم بتنزيل حزمة الإلحاق.
- اتبع خطوات الإلحاق للأداة المقابلة.

> [!IMPORTANT]
> لكي تكون مؤهلا لشراء Microsoft Defender لنقطة النهاية Server SKU، يجب أن تكون قد اشتريت بالفعل ما لا يقل عن أي مما يلي، Windows E5/A5 أو Microsoft 365 E5/A5 أو الأمان في Microsoft 365 E5 تراخيص الاشتراك. لمزيد من المعلومات حول الترخيص، راجع [شروط المنتج](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).

## <a name="offboard-windows-servers"></a>إيقاف تشغيل خوادم Windows

يمكنك إلغاء تشغيل Windows Server 2012 R2 وWindows Server 2016 وWindows Server (SAC) وWindows Server 2019 وإصدار Windows Server 2019 Core بنفس الطريقة المتوفرة لأجهزة العميل Windows 10.

- [إيقاف تشغيل الأجهزة باستخدام Configuration Manager](/microsoft-365/security/defender-endpoint/configure-endpoints-sccm#offboard-devices-using-configuration-manager)
- [إيقاف تشغيل الأجهزة ومراقبتها باستخدام أدوات 裝置管理 الأجهزة المحمولة](/microsoft-365/security/defender-endpoint/configure-endpoints-mdm#offboard-and-monitor-devices-using-mobile-device-management-tools)
- [إيقاف تشغيل الأجهزة باستخدام نهج المجموعة](/microsoft-365/security/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy)
- [إيقاف تشغيل الأجهزة باستخدام برنامج نصي محلي](/microsoft-365/security/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script)

بعد إلغاء الإلحاق، يمكنك المتابعة لإلغاء تثبيت حزمة الحلول الموحدة على Windows Server 2012 R2 وWindows Server 2016.

بالنسبة إلى إصدارات خادم Windows الأخرى، لديك خياران لإلغاء تشغيل خوادم Windows من الخدمة:
- إلغاء تثبيت عامل MMA
- إزالة تكوين مساحة عمل Defender لنقطة النهاية

> [!NOTE]
> تنطبق إرشادات إلغاء الإلحاق هذه لإصدارات خادم Windows الأخرى أيضا إذا كنت تقوم بتشغيل Microsoft Defender لنقطة النهاية السابقة ل Windows Server 2016 وWindows Server 2012 R2 التي تتطلب MMA. توجد إرشادات الترحيل إلى الحل الموحد الجديد في [سيناريوهات ترحيل الخادم في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>المواضيع ذات الصلة

- [أجهزة Windows التي تستخدم Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [أجهزة Windows باستخدام نهج المجموعة](configure-endpoints-gp.md)
- [أجهزة البنية الأساسية لسطح المكتب الظاهري (VDI) غير الثابتة](configure-endpoints-vdi.md)
