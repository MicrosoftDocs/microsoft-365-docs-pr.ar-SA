---
title: أجهزة إيقاف التشغيل من خدمة Microsoft Defender لنقطة النهاية
description: أجهزة Windows أو خوادم أو أجهزة Windows من خدمة Microsoft Defender لنقطة النهاية
keywords: إيقاف التشغيل، Microsoft Defender ل offboarding Endpoint، إيقاف التشغيل
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
ms.openlocfilehash: c2ec837ebc9fef0aabd2810dbd22db24597c52da
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63572247"
---
# <a name="offboard-devices-from-the-microsoft-defender-for-endpoint-service"></a>أجهزة إيقاف التشغيل من خدمة Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

**الأنظمة الأساسية**
- macOS
- Linux
- Windows Server 2012 R2
- Windows Server 2016‏

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-offboarddevices-abovefoldlink)

اتبع الإرشادات المطابقة وفقا لطريقة النشر المفضلة لديك.

> [!NOTE]
> سيتم تبديل حالة الجهاز إلى [غير](fix-unhealthy-sensors.md#inactive-devices) نشط بعد 7 أيام من إيقاف التشغيل.
>
> ستبقى بيانات الأجهزة غير المجهزة (مثل المخطط الزمني والتنبيهات ونقاط الضعف وغيرها) في المدخل حتى تنتهي صلاحية فترة الاستبقاء [التي](data-storage-privacy.md#how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy) تم تكوينها.
>
> سيظل ملف تعريف الجهاز (بدون بيانات) [في قائمة الأجهزة](machines-view-overview.md) لمدة لا يزيد عددها عن 180 يوما.
>
> بالإضافة إلى ذلك، لا يتم حساب الأجهزة غير النشطة في آخر 30 يوما في البيانات التي تعكس درجة التعرض للضوء في مؤسستك إدارة المخاطر والثغرات الأمنية و Microsoft Secure Score للأجهزة. [](tvm-exposure-score.md)
>
> لعرض الأجهزة النشطة فقط، يمكنك التصفية حسب حالة [أدوات](machines-view-overview.md#use-filters-to-customize-the-device-inventory-views) الاستشعار أو علامات [الجهاز](machine-tags.md) أو [مجموعات الأجهزة](machine-groups.md).

## <a name="offboard-windows-devices"></a>إيقاف Windows الأجهزة

- [أجهزة إيقاف التشغيل باستخدام برنامج نصي محلي](configure-endpoints-script.md#offboard-devices-using-a-local-script)
- [أجهزة إيقاف التشغيل باستخدام "نهج المجموعة"](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [أجهزة إيقاف التشغيل باستخدام أدوات إدارة أجهزة المحمول](configure-endpoints-mdm.md#offboard-and-monitor-devices-using-mobile-device-management-tools)

## <a name="offboard-servers"></a>Offboard Servers

- [خوادم إيقاف التشغيل](configure-server-endpoints.md#offboard-windows-servers)

## <a name="offboard-non-windows-devices"></a>إيقاف تشغيل الأجهزة غير Windows

- [إيقاف تشغيل الأجهزة غير Windows](configure-endpoints-non-windows.md#offboard-non-windows-devices)
