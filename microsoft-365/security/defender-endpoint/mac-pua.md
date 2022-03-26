---
title: الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها باستخدام Microsoft Defender لنقطة النهاية على Mac
description: كشف التطبيقات التي يحتمل أن تكون غير مرغوب فيها (PUA) وحظرها باستخدام Microsoft Defender ل Endpoint على macOS.
keywords: microsoft، defender، Microsoft Defender for Endpoint، mac، pua، pus
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
ms.openlocfilehash: a0fb8e19dd573da67936892c81cd515b463a7cba
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 02/12/2022
ms.locfileid: "63570617"
---
# <a name="detect-and-block-potentially-unwanted-applications-with-microsoft-defender-for-endpoint-on-macos"></a>الكشف عن التطبيقات التي يحتمل أن تكون غير مرغوب فيها وحظرها باستخدام Microsoft Defender for Endpoint على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

يمكن لميزاة حماية التطبيق (PUA) غير المرغوب فيها في Microsoft Defender ل Endpoint على macOS الكشف عن ملفات PUA وحظرها على نقاط النهاية في شبكتك.

لا تعتبر هذه التطبيقات فيروسات أو برامج ضارة أو أنواعا أخرى من التهديدات، ولكنها قد تقوم بتنفيذ إجراءات على نقاط النهاية تؤثر سلبا على أدائها أو استخدامها. يمكن أن يشير PUA أيضا إلى التطبيقات التي تعتبر سيئة السمعة.

يمكن أن تزيد هذه التطبيقات من خطر إصابة شبكتك بالبرامج الضارة، وتتسبب في صعوبة التعرف على البرامج الضارة، كما أنها قد تهدر موارد المعلومات في تنظيف التطبيقات.

## <a name="how-it-works"></a>كيفية عمل ذلك

يمكن ل Microsoft Defender ل Endpoint على macOS الكشف عن ملفات PUA وإبلا عنها. عند تكوينها في وضع الحظر، يتم نقل ملفات PUA إلى الفحص.

عند اكتشاف PUA في نقطة نهاية، يقدم Microsoft Defender ل Endpoint على macOS إعلاما للمستخدم، ما لم يتم تعطيل الإعلامات. سيحتوي اسم التهديد على الكلمة "تطبيق".

## <a name="configure-pua-protection"></a>تكوين حماية PUA

يمكن تكوين حماية PUA في Microsoft Defender ل Endpoint على macOS بوا واحدة من الطرق التالية:

- **إيقاف** التشغيل: تم تعطيل حماية PUA.
- **التدقيق**: يتم تسجيل ملفات PUA في سجلات المنتجات، ولكن ليس في Microsoft 365 Defender المدخل. لا يتم تقديم أي إعلام للمستخدم ولا يتم اتخاذ أي إجراء من قبل المنتج.
- **الحظر**: يتم تسجيل ملفات PUA في سجلات المنتجات Microsoft 365 Defender المدخل. يتم تقديم إعلام للمستخدم ويتخذ المنتج الإجراء اللازم.

> [!WARNING]
> بشكل افتراضي، يتم تكوين حماية PUA في **وضع** التدقيق.

يمكنك تكوين كيفية معالجة ملفات PUA من سطر الأوامر أو من وحدة تحكم الإدارة.

### <a name="use-the-command-line-tool-to-configure-pua-protection"></a>استخدم أداة سطر الأوامر لتكوين حماية PUA:

في المحطة الطرفية، قم بتنفيذ الأمر التالي لتكوين حماية PUA:

```bash
mdatp threat policy set --type potentially_unwanted_application --action [off|audit|block]
```

### <a name="use-the-management-console-to-configure-pua-protection"></a>استخدم وحدة تحكم الإدارة لتكوين حماية PUA:

في المؤسسة، يمكنك تكوين حماية PUA من وحدة تحكم الإدارة، مثل JAMF أو Intune، بطريقة مماثلة لكيفية تكوين إعدادات المنتج الأخرى. لمزيد من المعلومات، راجع القسم [إعدادات](mac-preferences.md#threat-type-settings) نوع التهديدات من الموضوع تعيين تفضيلات [ل Microsoft Defender ل Endpoint على macOS](mac-preferences.md) .

## <a name="related-topics"></a>المواضيع ذات الصلة

- [تعيين تفضيلات ل Microsoft Defender ل Endpoint على macOS](mac-preferences.md)
