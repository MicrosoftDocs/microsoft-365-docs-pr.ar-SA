---
title: التحقق من موقع تخزين البيانات وتحديث إعدادات استبقاء البيانات
description: التحقق من موقع تخزين البيانات وتحديث إعدادات استبقاء البيانات ل Microsoft Defender لنقطة النهاية
keywords: البيانات والتخزين والإعدادات والاستبقاء والتحديث
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
ms.openlocfilehash: fb27a097f2f9dfd26e1b611c56be6d078ecadc52
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/29/2021
ms.locfileid: "63571528"
---
# <a name="verify-data-storage-location-and-update-data-retention-settings-for-microsoft-defender-for-endpoint"></a>التحقق من موقع تخزين البيانات وتحديث إعدادات استبقاء البيانات ل Microsoft Defender لنقطة النهاية

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-gensettings-abovefoldlink)

أثناء عملية الضبط، يتولى المعالج نقلك عبر إعدادات تخزين البيانات والاحتفاظ بها في Defender لنقطة النهاية. 

بعد إكمال الضبط، يمكنك التحقق من التحديد في صفحة إعدادات استبقاء البيانات.

## <a name="verify-data-storage-location"></a>التحقق من موقع تخزين البيانات
أثناء [مرحلة "إعداد"](production-deployment.md)، كنت ستحدد الموقع الذي تريد تخزين البيانات فيه. 


يمكنك التحقق من موقع البيانات  \> من خلال الانتقال إلى الإعدادات **نقاط** \> النهاية **استبقاء** البيانات (ضمن **عام**).


## <a name="update-data-retention-settings"></a>تحديث إعدادات استبقاء البيانات

يمكنك تحديث إعدادات استبقاء البيانات. بشكل افتراضي، تكون فترة الاستبقاء 180 يوما. 

1. في جزء التنقل **، حدد الإعدادات** \> **نقاط** \> النهاية **استبقاء البيانات** (ضمن **عام**).

2. حدد مدة استبقاء البيانات من القائمة المنسدل.

    > [!NOTE]
    > الإعدادات الأخرى غير قابلة للتحرير.

3. انقر **فوق حفظ التفضيلات**.

## <a name="related-topics"></a>المواضيع ذات الصلة
- [تحديث إعدادات استبقاء البيانات](data-retention-settings.md)
- [تكوين إعلامات التنبيهات في Defender لنقطة النهاية](configure-email-notifications.md)
- [تكوين الميزات المتقدمة](advanced-features.md)
