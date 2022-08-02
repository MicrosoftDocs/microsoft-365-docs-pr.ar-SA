---
title: Microsoft Defender لنقطة النهاية Device Control Removable Storage Protection
description: فهم 'القدرات التي تساعد على منع المستخدم أو الجهاز أو كليهما من استخدام وسائط التخزين القابلة للإزالة غير المصرح بها
keywords: وسائط التخزين القابلة للإزالة
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
ms.date: 08/01/2022
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: a0225c12521812dc3888aac6c0179019dfa0ea72
ms.sourcegitcommit: adc4e5707aa074fc4aa0cb9e8c2986fc8b88813c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 08/01/2022
ms.locfileid: "67112516"
---
# <a name="microsoft-defender-for-endpoint-device-control-removable-storage-protection"></a>Microsoft Defender لنقطة النهاية Device Control Removable Storage Protection


**ينطبق على:**
- [الخطة 1 من Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!INCLUDE [Prerelease](../includes/prerelease.md)]

تمنع حماية التخزين القابلة للإزالة للتحكم في الجهاز في Microsoft Defender لنقطة النهاية المستخدمين أو نقاط النهاية أو كليهما من استخدام وسائط تخزين غير مصرح بها قابلة للإزالة.

## <a name="protection-policies"></a>نهج الحماية

### <a name="removable-storage-access-control"></a>التحكم في الوصول إلى التخزين القابل للإزالة

**قدرات**

- *مراجعه الحسابات* الوصول للقراءة أو الكتابة أو التنفيذ إلى التخزين القابل للإزالة استنادا إلى خصائص الجهاز المختلفة، مع استثناء أو بدونه.
- *منع* الوصول للقراءة أو الكتابة أو التنفيذ مع استثناء أو بدونه - السماح بجهاز معين استنادا إلى خصائص الجهاز المختلفة.

لإدارة التخزين الخارجي، استخدم التحكم في الوصول إلى التخزين القابل للإزالة بدلا من [تثبيت الجهاز](#device-installation).

**تفاصيل دعم Windows 10 والدعم Windows 11**:

- يتم تطبيقه على مستوى الجهاز، على مستوى المستخدم. أو كليهما. السماح فقط لأشخاص معينين يقومون بإجراء الوصول للقراءة/الكتابة/التنفيذ إلى تخزين معين قابل للإزالة على جهاز معين.
- دعم MEM OMA-URI وGPO.
- بالنسبة إلى أجهزة Windows، راجع [التحكم في الوصول إلى التخزين القابل للإزالة](device-control-removable-storage-access-control.md).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

**تفاصيل دعم macOS**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله.
- للحصول على معلومات محددة حول macOS، راجع [عنصر تحكم الجهاز لنظام التشغيل macOS](mac-device-control-overview.md).

**النظام الأساسي المدعوم** - macOS Catalina 10.15.4+ (مع تمكين ملحقات النظام)


### <a name="device-installation"></a>تثبيت الجهاز

**الإمكانات** - منع التثبيت مع أو بدون استثناء استنادا إلى خصائص الجهاز المختلفة.

**تفاصيل دعم Windows 10 والدعم Windows 11**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله.
- يدعم Microsoft إدارة نقاط النهاية وكائنات نهج المجموعة.
- لمزيد من المعلومات حول Windows، راجع [كيفية التحكم في أجهزة USB والوسائط الأخرى القابلة للإزالة باستخدام Microsoft Defender لنقطة النهاية](control-usb-devices-using-intune.md).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

**تفاصيل دعم macOS**:

- مطبق على مستوى الجهاز: ينطبق النهج نفسه على أي مستخدم تم تسجيل دخوله
- للحصول على معلومات محددة حول macOS، راجع [عنصر تحكم الجهاز لنظام التشغيل macOS](mac-device-control-overview.md).

**النظام الأساسي المدعوم** - macOS Catalina 10.15.4+ (مع تمكين ملحقات النظام) أو أحدث

### <a name="endpoint-dlp-removable-storage"></a>تخزين DLP القابل للإزالة لنقطة النهاية

**الإمكانات** - تدقيق المستخدم أو تحذيره أو منعه من نسخ عنصر أو معلومات إلى وسائط قابلة للإزالة أو جهاز USB.

**الوصف** - لمزيد من المعلومات حول Windows، راجع [التعرف على منع فقدان بيانات نقطة النهاية](../../compliance/endpoint-dlp-learn-about.md).

**النظام الأساسي المدعوم** - Windows 10، Windows 11

### <a name="bitlocker"></a>BitLocker

**القدرات**:

- حظر البيانات المطلوب كتابتها إلى محركات الأقراص القابلة للإزالة غير المحمية ب BitLocker.
- حظر الوصول إلى محركات الأقراص القابلة للإزالة ما لم تكن مشفرة على كمبيوتر تملكه مؤسستك

**الوصف** - لمزيد من المعلومات حول Windows، راجع [BitLocker - إعدادات محرك الأقراص القابلة للإزالة](/mem/intune/protect/endpoint-security-disk-encryption-profile-settings).

**النظام الأساسي المدعوم** - Windows 10، Windows 11
