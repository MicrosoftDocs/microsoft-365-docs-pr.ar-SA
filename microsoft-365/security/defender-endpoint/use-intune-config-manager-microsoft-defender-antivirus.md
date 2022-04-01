---
title: تكوين برنامج الحماية من الفيروسات من Microsoft Defender باستخدام إدارة نقاط النهاية من Microsoft
description: استخدم إدارة نقاط النهاية من Microsoft Microsoft Intune لتكوين برنامج الحماية من الفيروسات من Microsoft Defender Endpoint Protection
keywords: scep، intune، حماية نقطة النهاية، تكوين
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
ms.openlocfilehash: 1eb126481cc9872c42906e0311d1c771da44c693
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 12/17/2021
ms.locfileid: "63579549"
---
# <a name="use-microsoft-endpoint-manager-to-configure-and-manage-microsoft-defender-antivirus"></a>استخدم إدارة نقاط النهاية من Microsoft لتكوين وإدارة برنامج الحماية من الفيروسات من Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

يمكنك [استخدام إدارة نقاط النهاية من Microsoft لتكوين](/mem/endpoint-manager-overview) برنامج الحماية من الفيروسات من Microsoft Defender المسح الضوئي. [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) [إدارة التكوين](/mem/configmgr/core/understand/introduction) الآن جزءا من إدارة نقاط النهاية.

## <a name="configure-microsoft-defender-antivirus-scans-in-endpoint-manager"></a>تكوين عمليات برنامج الحماية من الفيروسات من Microsoft Defender في إدارة نقاط النهاية

1. انتقل إلى إدارة نقاط النهاية من Microsoft إدارة ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))، ثم سجل الدخول.

2. انتقل إلى **أمان نقطة النهاية**.

3. ضمن **إدارة**، اختر **برنامج الحماية من الفيروسات**.

4. حدد نهج برنامج الحماية من الفيروسات من Microsoft Defender الخاص بك.

5. ضمن **إدارة**، اختر **خصائص**.

6. إلى بجانب **إعدادات التكوين،** اختر **تحرير**.

   > [!IMPORTANT]
   > يتم إهمال إعدادات الحماية من الفيروسات ل AllowOnAccessProtection و AllowIntrusionPreventionSystem بشكل رسمي، ولا يمكن تكوينها على هذا النحو. 

7. قم بتوسيع **المقطع مسح** ضوئي ومراجعة إعدادات الفحص أو تحريرها.

8. اختر **مراجعة + حفظ**.

> [!TIP]
> هل تحتاج إلى مساعدة؟ راجع [إدارة أمان نقطة النهاية في Microsoft Intune](/mem/intune/protect/endpoint-security).

## <a name="related-articles"></a>المقالات ذات الصلة

- [المقالات المرجعية الخاصة بأدوات الإدارة والتكوين](configuration-management-reference-microsoft-defender-antivirus.md)
- [برنامج الحماية من الفيروسات من Microsoft Defender في Windows 10](microsoft-defender-antivirus-in-windows-10.md)
