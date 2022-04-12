---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام إدارة نقاط النهاية من Microsoft
description: استخدم إدارة نقاط النهاية من Microsoft Microsoft Intune لتكوين برنامج الحماية من الفيروسات من Microsoft Defender Endpoint Protection
keywords: scep، intune، حماية نقطة النهاية، التكوين
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 12/16/2021
ms.reviewer: phuijbr, oogunrinde
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: b25e57ee28ae0ef3f219a9adda1ff3f860d063db
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789283"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدام إدارة نقاط النهاية من Microsoft لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية الخطة 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية الخطة 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- برنامج الحماية من الفيروسات من Microsoft Defender

**منصات**
- بالنسبة لنظام التشغيل

يمكنك استخدام [إدارة نقاط النهاية من Microsoft](/mem/endpoint-manager-overview) لتكوين عمليات المسح الضوئي برنامج الحماية من الفيروسات من Microsoft Defender. [أصبحت Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [Configuration Manager الآن](/mem/configmgr/core/understand/introduction) جزءا من إدارة نقاط النهاية.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>تكوين عمليات فحص برنامج الحماية من الفيروسات من Microsoft Defender في إدارة نقاط النهاية

1. انتقل إلى مركز إدارة إدارة نقاط النهاية من Microsoft ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))، وسجل الدخول.

2. انتقل إلى **أمان نقطة النهاية**.

3. ضمن **"إدارة"**، اختر **"الحماية من الفيروسات**".

4. حدد نهج برنامج الحماية من الفيروسات من Microsoft Defender.

5. ضمن **"إدارة"**، اختر **"خصائص**".

6. إلى جانب **إعدادات التكوين**، اختر **"تحرير**".

   > [!IMPORTANT]
   > يتم إهمال إعدادات الحماية من الفيروسات AllowOnAccessProtection و AllowIntrusionPreventionSystem رسميا ولا يمكن تكوينها على هذا النحو. 

7. قم بتوسيع قسم **المسح** الضوئي، ومراجعة إعدادات المسح أو تحريرها.

8. اختر **Review + save**.

> [!TIP]
> هل تحتاج إلى مساعدة؟ راجع [إدارة أمان نقطة النهاية في Microsoft Intune](/mem/intune/protect/endpoint-security).

> [!TIP]
> إذا كنت تبحث عن معلومات متعلقة بالحماية من الفيروسات للأنظمة الأساسية الأخرى، فراجع:
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على macOS](mac-preferences.md)
> - [Microsoft Defender لنقطة النهاية على Mac](microsoft-defender-endpoint-mac.md)
> - [إعدادات نهج الحماية من الفيروسات في macOS ل برنامج الحماية من الفيروسات من Microsoft Defender ل Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [تعيين تفضيلات Microsoft Defender لنقطة النهاية على Linux](linux-preferences.md)
> - [مشكلات الأداء في Microsoft Defender لنقطة النهاية على Linux](microsoft-defender-endpoint-linux.md)
> - [تكوين Defender لنقطة النهاية على ميزات Android](android-configure.md)
> - [تكوين Microsoft Defender لنقطة النهاية على ميزات iOS](ios-configure-features.md)

## <a name="related-articles"></a>المقالات ذات الصلة

- [المقالات المرجعية لأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
