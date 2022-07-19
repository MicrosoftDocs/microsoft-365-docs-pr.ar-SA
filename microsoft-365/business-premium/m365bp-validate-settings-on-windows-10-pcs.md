---
title: التحقق من صحة إعدادات حماية التطبيقات لأجهزة الكمبيوتر Windows 10
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: fae8819d-7235-495f-9f07-d016f545887f
description: تعرف على كيفية التحقق من أن إعدادات حماية التطبيقات Microsoft 365 Business Premium سارية على أجهزة Windows 10 الخاصة بالمستخدمين.
ms.openlocfilehash: fe91d0b1588d860ee510f2542bc3f11a8cf2812a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 06/29/2022
ms.locfileid: "66857427"
---
# <a name="validate-device-protection-settings-for-windows-10-or-11-pcs"></a>التحقق من صحة إعدادات حماية الجهاز لأجهزة Windows 10 أو 11 جهاز كمبيوتر

## <a name="verify-that-windows-10-or-11-device-policies-are-set"></a>تحقق من تعيين Windows 10 أو 11 نهج جهاز

بعد [إعداد نهج الجهاز](../business-premium/m365bp-protection-settings-for-windows-10-devices.md)، قد يستغرق تطبيق النهج على أجهزة المستخدمين ما يصل إلى بضع ساعات. يمكنك التأكد من أن النهج قد تم تفعيلها من خلال النظر إلى شاشات إعدادات Windows المختلفة على أجهزة المستخدمين. نظرا لأن المستخدمين لن يتمكنوا من تعديل إعدادات Windows Update وMicrosoft Defender Antivirus على Windows 10 أو 11 جهازا، فستظهر العديد من الخيارات باللون الرمادي.
  
1. انتقل إلى أمان \> "**تحديث &amp;** **الإعدادات**\>" **Windows Update** \> **خيارات "إعادة التشغيل**" وتأكد من أن كافة الإعدادات باللون الرمادي.

    ![تظهر كل خيارات إعادة التشغيل باللون الرمادي.](../business-premium/media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. انتقل إلى أمان \> "**تحديث &amp;** **الإعدادات**\>" **Windows Update** \> **الخيارات المتقدمة** وتأكد من أن كافة الإعدادات باللون الرمادي.

    ![تظهر جميع خيارات التحديثات المتقدمة في Windows باللون الرمادي.](../business-premium/media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. انتقل إلى أمان \> "**تحديث &amp;** **الإعدادات**\>" **Windows Update** \> خيارات **متقدمة** \> **اختر كيفية تسليم التحديثات**.

    تأكد من أنه يمكنك رؤية الرسالة (باللون الأحمر) التي تفيد بأن بعض الإعدادات مخفية أو مدارة من قبل مؤسستك، وأن جميع الخيارات باللون الرمادي.

    ![اختر كيفية تسليم التحديثات للصفحة التي تشير إلى أن الإعدادات مخفية أو مدارة من قبل مؤسستك.](../business-premium/media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. لفتح مركز أمان Windows Defender، انتقل إلى **أمان "تحديث &amp;** **الإعدادات**\>" **Windows Defender** \> انقر فوق "**فتح Windows Defender** **إعدادات الحماية من تهديدات فيروسات &amp;****&amp; مؤشر ترابط** مركز \> الأمان".\> \>

5. تحقق من أن جميع الخيارات باللون الرمادي.

    ![تظهر إعدادات الحماية من الفيروسات والتهديدات باللون الرمادي.](../business-premium/media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>المحتويات ذات الصلة

[وثائق وموارد Microsoft 365 للأعمال](/admin)

[تعيين تكوينات الجهاز لأفضل ممارسات أجهزة الكمبيوتر](../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 Windows 10[لتأمين خطط Microsoft 365 للأعمال](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>الهدف التالي

[مراجعة نهج الحماية وتحريرها](m365bp-view-edit-create-mdb-policies.md)
