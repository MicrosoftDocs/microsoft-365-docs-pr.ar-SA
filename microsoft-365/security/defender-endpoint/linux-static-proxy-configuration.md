---
title: اكتشاف الوكيل الثابت ل Microsoft Defender ل Endpoint على Linux
ms.reviewer: ''
description: يصف كيفية تكوين Microsoft Defender ل Endpoint على Linux، لاكتشاف الوكيل الثابت.
keywords: microsoft، defender، Microsoft Defender ل Endpoint، linux، التثبيت، الوكيل
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
ms.openlocfilehash: 3b5061f0230a9704cb0fb9b80752c4d38954ad12
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63570466"
---
# <a name="configure-microsoft-defender-for-endpoint-on-linux-for-static-proxy-discovery"></a>تكوين Microsoft Defender ل Endpoint على Linux لاكتشاف الوكيل الثابت

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

يمكن ل Microsoft Defender ل Endpoint اكتشاف خادم وكيل باستخدام متغير `HTTPS_PROXY` البيئة. يجب تكوين هذا الإعداد **في** وقت التثبيت وبعد تثبيت المنتج.

## <a name="installation-time-configuration"></a>تكوين وقت التثبيت

أثناء التثبيت، يجب `HTTPS_PROXY` تمرير متغير البيئة إلى مدير الحزمة. يمكن لمدير الحزمة قراءة هذا المتغير بأي من الطرق التالية:

- يتم `HTTPS_PROXY` تعريف المتغير في `/etc/environment` باستخدام السطر التالي:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

- يتم `HTTPS_PROXY` تعريف المتغير في التكوين العمومي لمدير الحزمة. على سبيل المثال، في Ubuntu 18.04، يمكنك إضافة السطر التالي إلى `/etc/apt/apt.conf.d/proxy.conf`:

  ```bash
  Acquire::https::Proxy "http://proxy.server:port/";
  ```

  > [!CAUTION]
  > تجدر الإشارة إلى أن هناك طريقتين أعلاه يمكن أن تحددا الوكيل الذي يجب استخدامه للتطبيقات الأخرى على النظام. استخدم هذا الأسلوب بحذر، أو فقط إذا كان المقصود منه أن يكون تكوينا عموميا بشكل عام.

- يتم `HTTPS_PROXY` تثبيت المتغير مسبقا لأوامر التثبيت أو إزالة التثبيت. على سبيل المثال، باستخدام إدارة حزمة APT، قم بتثبيت المتغير كما يلي عند تثبيت Microsoft Defender لنقطة النهاية:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/" apt install mdatp
  ```

  > [!NOTE]
  > لا تضيف sudo بين تعريف متغير البيئة والابتعاد، وإلا لن يتم نشر المتغير.

قد `HTTPS_PROXY` يتم تعريف متغير البيئة بطريقة مماثلة أثناء إزالة التثبيت.

لاحظ أن التثبيت و إلغاء التثبيت لن يفشل بالضرورة إذا كان الوكيل مطلوبا ولكن لم يتم تكوينه. على الرغم من ذلك، لن يتم إرسال بيانات التكليف، وقد تستغرق العملية وقتا أطول نظرا لمهات الشبكة.

## <a name="post-installation-configuration"></a>نشر تكوين التثبيت

بعد التثبيت، يجب `HTTPS_PROXY` تعريف متغير البيئة في ملف خدمة Defender for Endpoint. للقيام بذلك، يمكنك تشغيل `sudo systemctl edit --full mdatp.service`.
يمكنك بعد ذلك نشر المتغير للخدمة بوا واحدة من طريقتين:

- قم ب إلغاء اربط السطر `#Environment="HTTPS_PROXY=http://address:port"` وحدد عنوان الوكيل الثابت.

- أضف سطرا `EnvironmentFile=/path/to/env/file`. يمكن أن يشير هذا المسار `/etc/environment` إلى ملف مخصص أو يحتاج أي منهما إلى إضافة السطر التالي:

  ```bash
  HTTPS_PROXY="http://proxy.server:port/"
  ```

بعد التعديل ، `mdatp.service`احفظ الملف ثم أعد تشغيل الخدمة حتى يمكن تطبيق التغييرات باستخدام الأوامر التالية:

```bash
sudo systemctl daemon-reload; sudo systemctl restart mdatp
```
