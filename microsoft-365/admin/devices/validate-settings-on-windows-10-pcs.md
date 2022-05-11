---
title: التحقق من صحة إعدادات حماية التطبيقات لأجهزة الكمبيوتر Windows 10
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
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
description: تعرف على كيفية التحقق من أن إعدادات حماية تطبيق Microsoft 365 للأعمال قد تم تفعيلها على أجهزة Windows 10 للمستخدمين.
ms.openlocfilehash: cbb26461da9fcc73f57d219c36ef04d97e7fc209
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317542"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>التحقق من صحة إعدادات حماية الجهاز لأجهزة الكمبيوتر Windows 10

> [!NOTE]
> يتم طرح Microsoft Defender for Business للعملاء Microsoft 365 Business Premium، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>تحقق من تعيين نهج الجهاز Windows 10

بعد [إعداد نهج الجهاز](../../business-premium/m365bp-protection-settings-for-windows-10-pcs.md)، قد يستغرق تطبيق النهج على أجهزة المستخدمين ما يصل إلى بضع ساعات. يمكنك التأكد من أن النهج قد تم تفعيلها من خلال النظر إلى مختلف شاشات Windows الإعدادات على أجهزة المستخدمين. نظرا لأن المستخدمين لن يتمكنوا من تعديل الإعدادات Windows Update وإعدادات برنامج الحماية من الفيروسات من Microsoft Defender على أجهزة Windows 10 الخاصة بهم، فستظهر العديد من الخيارات باللون الرمادي.
  
1. انتقل إلى **الإعدادات** \> **خيارات "تحديث &amp; الأمان** \> **" Windows Update** \> **"إعادة التشغيل**" وتأكد من أن كافة الإعدادات باللون الرمادي.

    ![تظهر كل خيارات إعادة التشغيل باللون الرمادي.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. انتقل إلى **الإعدادات** \> **تحديث &amp; الأمان** \> **Windows Update** \> **خيارات متقدمة** وتأكد من أن كافة الإعدادات باللون الرمادي.

    ![Windows خيارات التحديثات المتقدمة كلها باللون الرمادي.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. انتقل إلى **الإعدادات** \> **تحديث &amp; الأمان** \> **Windows Update** \> **خيارات** \> متقدمة **اختر كيفية تسليم التحديثات**.

    تأكد من أنه يمكنك رؤية الرسالة (باللون الأحمر) التي تفيد بأن بعض الإعدادات مخفية أو مدارة من قبل مؤسستك، وأن جميع الخيارات باللون الرمادي.

    ![اختر كيفية تسليم التحديثات للصفحة التي تشير إلى أن الإعدادات مخفية أو مدارة من قبل مؤسستك.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. لفتح مركز أمان Windows Defender، انتقل إلى **الإعدادات** \> **تحديث &amp; الأمان** \> **Windows** انقر فوق "فتح \> **Windows مركز** \> حماية **فيروسات &amp;** Defender" **ضمن إعدادات الحماية من تهديدات الفيروسات&amp;**.\>

5. تحقق من أن جميع الخيارات باللون الرمادي.

    ![تظهر إعدادات الحماية من الفيروسات والتهديدات باللون الرمادي.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>المحتويات ذات الصلة

[Microsoft 365 لوثائق وموارد الأعمال](/admin)

[تعيين تكوينات الجهاز لممارسات Windows 10 PCsBest](../../business-premium/m365bp-protection-settings-for-windows-10-devices.md)
 [لتأمين Microsoft 365 لخطط الأعمال](../../admin/security-and-compliance/secure-your-business-data.md)
