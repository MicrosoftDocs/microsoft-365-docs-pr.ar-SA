---
title: استكشاف مشاكل ملحقات kernel وإصلاحها في Microsoft Defender لنقطة النهاية على macOS
description: استكشاف المشاكل المتعلقة بملحقات kernel وإصلاحها في Microsoft Defender لنقطة النهاية على macOS.
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، kernel، ملحق
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
ms.openlocfilehash: 72d1aab8be071b5f4ec66988b35655571625b409
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477270"
---
# <a name="troubleshoot-kernel-extension-issues-in-microsoft-defender-for-endpoint-on-macos"></a>استكشاف مشاكل ملحقات kernel وإصلاحها في Microsoft Defender لنقطة النهاية على macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**

- [Microsoft Defender لنقطة النهاية على macOS](microsoft-defender-endpoint-mac.md)
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Microsoft Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

توفر هذه المقالة معلومات حول كيفية استكشاف المشاكل وإصلاحها باستخدام ملحق kernel المثبت كجزء من Microsoft Defender لنقطة النهاية على macOS.

بدءا من macOS High Sierra (10.13)، يتطلب macOS الموافقة على جميع ملحقات kernel بشكل صريح قبل السماح بتشغيلها على الجهاز.

إذا لم توافق على ملحق kernel أثناء نشر/تثبيت Microsoft Defender لنقطة النهاية على macOS، يعرض التطبيق شعارا يطالبك بتمكينه:

:::image type="content" source="images/mdatp-32-main-app-fix.png" alt-text="تم تعطيل RTP" lightbox="images/mdatp-32-main-app-fix.png":::

يمكنك أيضا تشغيل ```mdatp health```. وهو يقدم تقارير حول ما إذا كانت الحماية في الوقت الحقيقي تم تمكينها ولكنها غير متوفرة. يشير ذلك إلى أن ملحق kernel غير معتمد للتشغيل على جهازك.

```bash
mdatp health
```
```Output
...
real_time_protection_enabled                : false
real_time_protection_available              : true
...
```

توفر الأقسام التالية إرشادات حول كيفية معالجة هذه المشكلة، استنادا إلى الأسلوب الذي استخدمته لنشر Microsoft Defender لنقطة النهاية macOS.

## <a name="managed-deployment"></a>النشر المدار

راجع الإرشادات المطابقة لأداة الإدارة التي استخدمتها لنشر المنتج:

- [النشر المستند إلى JAMF](mac-install-with-jamf.md)
- [Microsoft Intune يستند إلى](mac-install-with-intune.md#create-system-configuration-profiles)

## <a name="manual-deployment"></a>النشر اليدوي

إذا مرت أقل من 30  \> دقيقة منذ تثبيت المنتج، فانتقل إلى أمان تفضيلات النظام **& الخصوصية**، حيث يجب السماح برامج النظام من المطورين "Microsoft Corporation".

إذا لم تشاهد هذه المطالبة، فهذا يعني مرور 30 دقيقة أو أكثر، ومع ذلك لم يتم الموافقة على تشغيل ملحق kernel على جهازك:

:::image type="content" source="images/mdatp-33-securityprivacysettings-noprompt.png" alt-text="نافذة الأمان والخصوصية بعد انتهاء صلاحية المطالبة" lightbox="images/mdatp-33-securityprivacysettings-noprompt.png":::

في هذه الحالة، تحتاج إلى تنفيذ الخطوات التالية لتحريك تدفق الموافقة مرة أخرى.

1. في المحطة الطرفية، حاول تثبيت برنامج التشغيل. ستفشل العملية التالية، لأنه لم يتم الموافقة على تشغيل ملحق kernel على الجهاز. ومع ذلك، سيتم تشغيل تدفق الموافقة مرة أخرى.

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    ```Output
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Kext rejected due to system policy: <OSKext 0x7fc34d528390 [0x7fffa74aa8e0]> { URL = "file:///Library/StagedExtensions/Library/Extensions/wdavkext.kext/", ID = "com.microsoft.wdavkext" }
    Diagnostics for /Library/Extensions/wdavkext.kext:
    ```

2. افتح **أمان تفضيلات** \> **النظام & الخصوصية** من القائمة. (أغلقه أولا، إذا تم فتحه.)

3. **السماح** للبرامج النظامية من المطورين "Microsoft Corporation"

4. في المحطة الطرفية، ثبت برنامج التشغيل مرة أخرى. في هذه المرة، ستنجح العملية:

    ```bash
    sudo kextutil /Library/Extensions/wdavkext.kext
    ```

    يجب أن يختفي الشعار من تطبيق Defender، ```mdatp health``` ويجب أن يقدم الآن تقريرا بأن الحماية في الوقت الحقيقي متوفرة وممكنة:

    ```bash
    mdatp health
    ```

    ```Output
    ...
    real_time_protection_enabled                : true
    real_time_protection_available              : true
    ...
    ```
