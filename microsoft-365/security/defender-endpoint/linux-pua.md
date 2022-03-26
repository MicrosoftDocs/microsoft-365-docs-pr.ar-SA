---
title: الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها باستخدام Microsoft Defender for Endpoint على Linux
description: كشف التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA) وحظرها باستخدام Microsoft Defender ل Endpoint على Linux.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، pua، pus
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
ms.openlocfilehash: 03c6f64e7272706262ef622a173e58260468e01b
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570467"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-linux"></a>الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها باستخدام Microsoft Defender for Endpoint على Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يمكن لميزاة حماية التطبيق (PUA) غير المرغوب فيها في Defender for Endpoint على Linux الكشف عن ملفات PUA وحظرها على نقاط النهاية في شبكتك.

لا تعتبر هذه التطبيقات فيروسات أو برامج ضارة أو أنواعا أخرى من التهديدات، ولكنها قد تقوم بتنفيذ إجراءات على نقاط النهاية تؤثر سلبا على أدائها أو استخدامها. يمكن أن يشير PUA أيضا إلى التطبيقات التي تعتبر سيئة السمعة.

يمكن أن تزيد هذه التطبيقات من خطر إصابة شبكتك بالبرامج الضارة، وتتسبب في صعوبة التعرف على البرامج الضارة، كما أنها قد تهدر موارد المعلومات في تنظيف التطبيقات.

## <a name="how-it-works"></a>كيفية عمل ذلك

يمكن ل Defender ل Endpoint على Linux الكشف عن ملفات PUA وإبلاغاها. عند تكوينها في وضع الحظر، يتم نقل ملفات PUA إلى الفحص.

عند اكتشاف PUA في نقطة نهاية، يحتفظ Defender for Endpoint على Linux بسجل عن الإصابة في محفوظات التهديدات. يمكن عرض المحفوظات من مدخل Microsoft 365 Defender أو من خلال `mdatp` أداة سطر الأوامر. سيحتوي اسم التهديد على الكلمة "تطبيق".

## <a name="configure-pua-protection"></a>تكوين حماية PUA

يمكن تكوين حماية PUA في Defender for Endpoint على Linux باستخدام إحدى الطرق التالية:

- **إيقاف** التشغيل: تم تعطيل حماية PUA.
- **التدقيق**: يتم تسجيل ملفات PUA في سجلات المنتجات، ولكن ليس في Microsoft 365 Defender. لا يتم تخزين أي سجل إصابة في محفوظات التهديدات ولا يتم اتخاذ أي إجراء من قبل المنتج.
- **الحظر**: يتم تسجيل ملفات PUA في سجلات المنتجات وفي Microsoft 365 Defender. يتم تخزين سجل إصابة في محفوظات التهديدات ويتخذ المنتج الإجراء اللازم.

> [!WARNING]
> بشكل افتراضي، يتم تكوين حماية PUA في **وضع** التدقيق.

يمكنك تكوين كيفية معالجة ملفات PUA من سطر الأوامر أو من وحدة تحكم الإدارة.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>استخدم أداة سطر الأوامر لتكوين حماية PUA:

في المحطة الطرفية، قم بتنفيذ الأمر التالي لتكوين حماية PUA:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>استخدم وحدة تحكم الإدارة لتكوين حماية PUA:

في المؤسسة، يمكنك تكوين حماية PUA من وحدة تحكم إدارة، مثل "مهى" أو "غير قابل للطي"، بطريقة مماثلة لكيفية تكوين إعدادات المنتج الأخرى. لمزيد من المعلومات، راجع القسم [إعدادات](linux-preferences.md#threat-type-settings) نوع التهديدات من المقالة تعيين تفضيلات [ل Defender for Endpoint على Linux](linux-preferences.md) .

## <a name="related-articles"></a>المقالات ذات الصلة

- [تعيين تفضيلات ل Defender for Endpoint على Linux](linux-preferences.md)
