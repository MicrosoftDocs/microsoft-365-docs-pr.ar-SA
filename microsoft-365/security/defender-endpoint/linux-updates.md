---
title: نشر تحديثات ل Microsoft Defender ل Endpoint على Linux
ms.reviewer: ''
description: يصف كيفية نشر التحديثات ل Microsoft Defender ل Endpoint على Linux في بيئات المؤسسات.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، التحديثات، النشر
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
ms.openlocfilehash: 71c689143feca3d8c87d219a55c4ea42b4f9d950
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63573270"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>نشر تحديثات ل Microsoft Defender ل Endpoint على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

تنشر Microsoft تحديثات البرامج بشكل منتظم لتحسين الأداء والأمان وتقديم ميزات جديدة.

> [!WARNING]
> يحتوي كل إصدار من إصدار Defender for Endpoint على Linux على تاريخ انتهاء صلاحية، ولن يستمر بعد ذلك في حماية جهازك. يجب تحديث المنتج قبل هذا التاريخ. للتحقق من تاريخ انتهاء الصلاحية، قم بتشغيل الأمر التالي:
> ```bash
> mdatp health --field product_expiration
> ```


تكون إمكانيات Microsoft Defender لنقطة النهاية المتوفرة بشكل عام مكافئة بغض النظر عن قناة التحديث المستخدمة للنشر (Beta (Insider) ومعاينة (خارجي) و Current (الإنتاج)).


لتحديث Defender for Endpoint على Linux يدويا، نفذ أحد الأوامر التالية:

## <a name="rhel-and-variants-centos-and-oracle-linux"></a>RHEL والمتغيرات (CentOS و Oracle Linux)

```bash
sudo yum update mdatp
```

## <a name="sles-and-variants"></a>SLES والمتغيرات

```bash
sudo zypper update mdatp
```

## <a name="ubuntu-and-debian-systems"></a>أنظمة Ubuntu و Debian

```bash
sudo apt-get install --only-upgrade mdatp
```

> [!IMPORTANT]
> عند دمج Microsoft Defender ل Endpoint و Defender for Cloud، سيتلقى وكيل mdatp التحديثات تلقائيا بشكل افتراضي.
