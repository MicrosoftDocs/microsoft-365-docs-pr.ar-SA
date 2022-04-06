---
title: تسجيل Microsoft Defender لنقطة النهاية على أجهزة macOS في Jamf Pro
description: تسجيل Microsoft Defender لنقطة النهاية على أجهزة macOS في Jamf Pro
keywords: microsoft، defender، Microsoft Defender لنقطة النهاية، mac، التثبيت، النشر، إلغاء التثبيت، intune، jamfpro، macos، catalina، mojave، high sierra
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
ms.openlocfilehash: 6189b61826cd56e2a8652032998c3b2df8f980ce
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468644"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>تسجيل Microsoft Defender لنقطة النهاية على أجهزة macOS في Jamf Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [Microsoft Defender لنقطة النهاية 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> هل تريد تجربة Defender لنقطة النهاية؟ [التسجيل للحصول على تجربة مجانية.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="enroll-macos-devices"></a>تسجيل أجهزة macOS

هناك طرق متعددة للتسجيل في JamF.

سترشدك هذه المقالة على طريقتين:

- [الطريقة 1: دعوات التسجيل](#enrollment-method-1-enrollment-invitations)
- [الطريقة 2: تسجيلات ما قبل الإعداد](#enrollment-method-2-prestage-enrollments)

للحصول على قائمة كاملة، راجع [حول تسجيل الكمبيوتر](https://docs.jamf.com/9.9/casper-suite/administrator-guide/About_Computer_Enrollment.html).

## <a name="enrollment-method-1-enrollment-invitations"></a>طريقة التسجيل 1: دعوات التسجيل

1. في لوحة معلومات Pro Jamf، انتقل إلى **دعوات التسجيل**.

   :::image type="content" source="images/a347307458d6a9bbfa88df7dbe15398f.png" alt-text="إعدادات التكوين1" lightbox="images/a347307458d6a9bbfa88df7dbe15398f.png":::

2. حدد **+ جديد**.

   :::image type="content" source="images/b6c7ad56d50f497c38fc14c1e315456c.png" alt-text="إغلاق وصف الشعار الذي يتم إنشاؤه تلقائيا" lightbox="images/b6c7ad56d50f497c38fc14c1e315456c.png":::

3. في **تحديد المستلمين لدعوة >** **ضمن عناوين** البريد الإلكتروني أدخل عنوان (عناوين) البريد الإلكتروني للمستلمين.

    :::image type="content" source="images/718b9d609f9f77c8b13ba88c4c0abe5d.png" alt-text="إعدادات التكوين2" lightbox="images/718b9d609f9f77c8b13ba88c4c0abe5d.png":::

    :::image type="content" source="images/ae3597247b6bc7c5347cf56ab1e820c0.png" alt-text="إعدادات التكوين3" lightbox="images/ae3597247b6bc7c5347cf56ab1e820c0.png":::

    على سبيل المثال: janedoe@contoso.com

    :::image type="content" source="images/4922c0fcdde4c7f73242b13bf5e35c19.png" alt-text="إعدادات التكوين4" lightbox="images/4922c0fcdde4c7f73242b13bf5e35c19.png":::

4. تكوين الرسالة للدعوة.

   :::image type="content" source="images/ce580aec080512d44a37ff8e82e5c2ac.png" alt-text="إعدادات التكوين5" lightbox="images/ce580aec080512d44a37ff8e82e5c2ac.png":::

   :::image type="content" source="images/5856b765a6ce677caacb130ca36b1a62.png" alt-text="إعدادات التكوين6" lightbox="images/5856b765a6ce677caacb130ca36b1a62.png":::

   :::image type="content" source="images/3ced5383a6be788486d89d407d042f28.png" alt-text="إعدادات التكوين7" lightbox="images/3ced5383a6be788486d89d407d042f28.png":::

   :::image type="content" source="images/54be9c6ed5b24cebe628dc3cd9ca4089.png" alt-text="إعدادات التكوين8" lightbox="images/54be9c6ed5b24cebe628dc3cd9ca4089.png":::

## <a name="enrollment-method-2-prestage-enrollments"></a>طريقة التسجيل 2: تسجيلات ما قبل الإعداد

1. في لوحة معلومات Pro Jamf، انتقل إلى **تسجيلات Prestage**.

   :::image type="content" source="images/6fd0cb2bbb0e60a623829c91fd0826ab.png" alt-text="إعدادات التكوين9" lightbox="images/6fd0cb2bbb0e60a623829c91fd0826ab.png":::

2. اتبع الإرشادات الواردة [في "التسجيلات المسبقة من الكمبيوتر](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html)".

## <a name="enroll-macos-device"></a>تسجيل جهاز macOS

1. حدد **متابعة** وثبت شهادة CA من **نافذة تفضيلات** النظام.

   :::image type="content" source="images/jamfpro-ca-certificate.png" alt-text="تسجيل Pro Jamf1" lightbox="images/jamfpro-ca-certificate.png":::

2. بمجرد تثبيت شهادة المرجع المرجع، ارجع إلى نافذة المستعرض **وحدد** متابعة ملف تعريف MDM وتثبيته.

   :::image type="content" source="images/jamfpro-install-mdm-profile.png" alt-text="تسجيل Pro Jamf2" lightbox="images/jamfpro-install-mdm-profile.png":::

3. حدد **السماح** للتنزيل من JAMF.

   :::image type="content" source="images/jamfpro-download.png" alt-text="تسجيل Pro Jamf3" lightbox="images/jamfpro-download.png":::

4. حدد **متابعة** للمتابعة مع تثبيت ملف تعريف MDM.

   :::image type="content" source="images/jamfpro-install-mdm.png" alt-text="تسجيل Pro Jamf4" lightbox="images/jamfpro-install-mdm.png":::

5. حدد **متابعة** لتثبيت ملف تعريف MDM.

   :::image type="content" source="images/jamfpro-mdm-unverified.png" alt-text="تسجيل Pro Jamf5" lightbox="images/jamfpro-mdm-unverified.png":::

6. حدد **متابعة**  لإكمال التكوين.

   :::image type="content" source="images/jamfpro-mdm-profile.png" alt-text="تسجيل Pro Jamf6" lightbox="images/jamfpro-mdm-profile.png":::
