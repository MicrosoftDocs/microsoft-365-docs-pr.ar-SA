---
title: الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها باستخدام Microsoft Defender لنقطة النهاية على Linux
description: الكشف عن التطبيقات غير المرغوب فيها (PUA) ومنعها باستخدام Microsoft Defender لنقطة النهاية على Linux.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، linux، pua، pus
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
ms.openlocfilehash: 004a9d7af09e8a2abb656c29db558d797173edcd
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663591"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها باستخدام Microsoft Defender لنقطة النهاية على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Defender for Endpoint الخطة 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على إصدار تجريبي مجاني.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يمكن لميزة حماية التطبيق (PUA) غير المرغوب فيها في Defender لنقطة النهاية على Linux اكتشاف ملفات PUA ومنعها على نقاط النهاية في شبكتك.

لا تعتبر هذه التطبيقات فيروسات أو برامج ضارة أو أنواعا أخرى من التهديدات، ولكنها قد تنفذ إجراءات على نقاط النهاية التي تؤثر سلبا على أدائها أو استخدامها. يمكن أن يشير PUA أيضا إلى التطبيقات التي تعتبر ذات سمعة سيئة.

يمكن أن تزيد هذه التطبيقات من خطر إصابة شبكتك بالبرامج الضارة، وتتسبب في صعوبة التعرف على عدوى البرامج الضارة، ويمكن أن تهدر موارد تكنولوجيا المعلومات في تنظيف التطبيقات.

## <a name="how-it-works"></a>كيفية عملها

يمكن ل Defender لنقطة النهاية على Linux اكتشاف ملفات PUA والإبلاغ عنها. عند تكوينها في وضع الحظر، يتم نقل ملفات PUA إلى العزل.

عند اكتشاف PUA على نقطة نهاية، يحتفظ Defender لنقطة النهاية على Linux بسجل للعدوى في تاريخ التهديد. يمكن تصور المحفوظات من مدخل Microsoft 365 Defender أو من خلال `mdatp` أداة سطر الأوامر. سيحتوي اسم التهديد على كلمة "Application".

## <a name="configure-pua-protection"></a>تكوين حماية PUA

يمكن تكوين حماية PUA في Defender لنقطة النهاية على Linux بإحدى الطرق التالية:

- **إيقاف التشغيل**: تم تعطيل حماية PUA.
- **التدقيق**: يتم الإبلاغ عن ملفات PUA في سجلات المنتجات، ولكن ليس في Microsoft 365 Defender. لا يتم تخزين أي سجل للعدوى في محفوظات التهديدات ولا يتخذ المنتج أي إجراء.
- **الكتلة**: يتم الإبلاغ عن ملفات PUA في سجلات المنتجات وفي Microsoft 365 Defender. يتم تخزين سجل العدوى في محفوظات التهديدات ويتم اتخاذ الإجراء من قبل المنتج.

> [!WARNING]
> بشكل افتراضي، يتم تكوين حماية PUA في وضع **التدقيق** .

يمكنك تكوين كيفية معالجة ملفات PUA من سطر الأوامر أو من وحدة تحكم الإدارة.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>استخدم أداة سطر الأوامر لتكوين حماية PUA:

في Terminal، نفذ الأمر التالي لتكوين حماية PUA:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>استخدم وحدة تحكم الإدارة لتكوين حماية PUA:

في مؤسستك، يمكنك تكوين حماية PUA من وحدة تحكم إدارة، مثل Puppet أو Ansible، بطريقة مماثلة لكيفية تكوين إعدادات المنتج الأخرى. لمزيد من المعلومات، راجع قسم [إعدادات نوع التهديد](linux-preferences.md#threat-type-settings) في [تعيين تفضيلات Defender لنقطة النهاية على مقالة Linux](linux-preferences.md) .

## <a name="related-articles"></a>المقالات ذات الصلة

- [تعيين التفضيلات ل Defender لنقطة النهاية على Linux](linux-preferences.md)
