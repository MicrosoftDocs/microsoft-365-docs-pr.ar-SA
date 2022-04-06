---
title: أساليب وخصائص مكتبة الاستجابة المباشرة
description: تعرف على كيفية استخدام خصائص وأساليب مكتبة الاستجابة المباشرة.
keywords: apis، api الخاصة بالرسم البياني، apis المعتمدة، الحصول، الأجهزة
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: reference
ms.technology: m365d
ms.openlocfilehash: c9eb1de08be8905a41b172a19a33db58dbdc19b9
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705493"
---
#  <a name="live-response-library-methods-and-properties"></a>أساليب وخصائص مكتبة الاستجابة المباشرة

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:** [Microsoft Defender لنقطة النهاية](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

- هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink) 

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


## <a name="methods"></a>الأساليب

| **الأسلوب**          | **نوع الإرجاع**         | **الوصف**                         |
|---------------------|-------------------------|-----------------------------------------|
| ملفات مكتبة القائمة  | مجموعة ملفات المكتبة | كيانات ملفات مكتبة القائمة              |
| Upload مكتبة   | كيان ملف المكتبة     | Upload ملف إلى مكتبة استجابة مباشرة |
| حذف من المكتبة | بلا محتوى              | حذف كيان ملف المكتبة              |

## <a name="properties"></a>الخصائص

| **الخاصية** | **النوع**                         | **الوصف**                                        |
|--------------|----------------------------------|--------------------------------------------------------|
| الأوامر     | مجموعة أوامر الاستجابة المباشرة | صفيف من عناصر الأمر. راجع [أوامر الاستجابة المباشرة](live-response.md#live-response-commands). |

