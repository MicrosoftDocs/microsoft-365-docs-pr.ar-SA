---
title: استكشاف مشاكل ترخيص Microsoft Defender for Endpoint على Mac وإصلاحها
description: استكشاف مشاكل الترخيص وإصلاحها في Microsoft Defender ل Endpoint على Mac.
keywords: microsoft، defender، Microsoft Defender for Endpoint، mac، الأداء
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b0a328ffeee6ee5796cb92f00b8491b257e88a65
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570146"
---
# <a name="troubleshoot-license-issues-for-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشاكل ترخيص Microsoft Defender ل Endpoint على macOS وإصلاحها

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md)
 [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
 [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

أثناء المرور عبر [Microsoft Defender ل Endpoint على macOS](microsoft-defender-endpoint-mac.md) واختبار [النشر اليدوي أو](mac-install-manually.md) إثبات المبدأ (PoC)، قد تحصل على الخطأ التالي:

![صورة لخطأ الترخيص.](images/no-license-found.png)

**الرسالة:** 

لم يتم العثور على أي ترخيص

يبدو أن مؤسستك لا تملك ترخيصا Microsoft 365 Enterprise الاشتراك.

اتصل بالمسؤول للحصول على المساعدة.

**السبب:** 

قمت بنشر Microsoft Defender ل Endpoint و/أو تثبيته على حزمة macOS ("تنزيل حزمة التثبيت")، ولكن ربما لم تكن قد قمت بتشغيل برنامج التكوين النصي ("تنزيل حزمة التهيئة")، أو لم يتم تعيين ترخيص للمستخدم.

يمكنك أيضا مواجهة هذا الخطأ عندما لا يكون وكيل Microsoft Defender for Endpoint على macOS منتهي الصلاحية. 


**الحل:**

اتبع الإرشادات MicrosoftDefenderATPOnboardingMacOs.py الموثقة هنا: [تكوين العميل](mac-install-manually.md#client-configuration)

بالنسبة إلى السيناريوهات التي لا يكون فيها Microsoft Defender for Endpoint على macOS محدثا، ستحتاج إلى تحديث الوكيل. 
