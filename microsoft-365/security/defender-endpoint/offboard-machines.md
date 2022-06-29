---
title: إيقاف تشغيل الأجهزة من خدمة Microsoft Defender لنقطة النهاية
description: إلحاق أجهزة Windows والخوادم والأجهزة غير التابعة ل Windows من خدمة Microsoft Defender لنقطة النهاية
keywords: الإلحاق، Microsoft Defender لنقطة النهاية الإلحاق، الإلحاق
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 3fec93e45fbdced0cc6c4106d24a29eb13087d02
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66531001"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>إيقاف تشغيل الأجهزة من خدمة Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**الأنظمة الأساسية**
- ماك
- ينكس
- Windows Server 2012 R2
- Windows Server 2016‏

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

اتبع الإرشادات المقابلة استنادا إلى أسلوب النشر المفضل لديك.

> [!NOTE]
> سيتم تبديل حالة الجهاز إلى ["غير نشط"](fix-unhealthy-sensors.md#inactive-devices) بعد 7 أيام من إيقاف الإلحاق.
>
> ستبقى بيانات الأجهزة غير الملحقة (مثل الخط الزمني والتنبيهات والثغرات الأمنية وما إلى ذلك) في المدخل حتى تنتهي [فترة الاستبقاء](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) التي تم تكوينها.
>
> سيظل ملف تعريف الجهاز (بدون بيانات) في ["قائمة الأجهزة](machines-view-overview.md) " لمدة لا تزيد عن 180 يوما.
>
> بالإضافة إلى ذلك، لا يتم احتساب الأجهزة غير النشطة في آخر 30 يوما في البيانات التي تعكس [درجة التعرض](tvm-exposure-score.md) إدارة المخاطر والثغرات الأمنية لمؤسستك وMicrosoft Secure Score للأجهزة.
>
> لعرض الأجهزة النشطة فقط، يمكنك التصفية حسب [حالة حماية جهاز الاستشعار](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views) أو [علامات الجهاز](machine-tags.md) أو [مجموعات الأجهزة](machine-groups.md).

## <a name="offboard-windows-devices"></a>إيقاف تشغيل أجهزة Windows

- [إيقاف تشغيل الأجهزة باستخدام برنامج نصي محلي](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [إيقاف تشغيل الأجهزة باستخدام نهج المجموعة](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [إيقاف تشغيل الأجهزة باستخدام أدوات إدارة الجهاز الأجهزة المحمولة](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>إيقاف تشغيل الخوادم

- [إيقاف تشغيل الخوادم](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>إيقاف تشغيل الأجهزة غير التي تعمل بنظام Windows

- [إيقاف تشغيل الأجهزة غير التي تعمل بنظام Windows](configure-endpoints-non-windows.md#offboard-non-windows-devices)
