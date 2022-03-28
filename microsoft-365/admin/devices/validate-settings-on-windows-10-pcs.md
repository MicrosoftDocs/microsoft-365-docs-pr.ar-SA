---
title: التحقق من صحة إعدادات حماية التطبيقات Windows 10 الكمبيوتر الشخصي
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
description: تعرف على كيفية التحقق من أن Microsoft 365 حماية تطبيقات الأعمال قد تم تطبيقها على أجهزة Windows 10 الخاصة بك.
ms.openlocfilehash: be25acb8414705c48a8763a0530ec2a70565de83
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63575056"
---
# <a name="validate-device-protection-settings-for-windows-10-pcs"></a>التحقق من صحة إعدادات حماية الجهاز Windows 10 الكمبيوتر الشخصي

> [!NOTE]
> يتم طرح Microsoft Defender for Business Microsoft 365 Business Premium العملاء، بدءا من 1 مارس 2022. يوفر هذا العرض ميزات أمان إضافية للأجهزة. [تعرف على المزيد حول Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="verify-that-windows-10-device-policies-are-set"></a>التحقق من Windows 10 تعيين سياسات الأجهزة

بعد [إعداد نهج الجهاز](protection-settings-for-windows-10-pcs.md)، قد يستغرق الأمر بضع ساعات حتى يتم تطبيق النهج على أجهزة المستخدمين. يمكنك تأكيد أن هذه السياسات قد تم تطبيقها من خلال Windows الإعدادات الشاشات على أجهزة المستخدمين. نظرا لعدم تمكن المستخدمين من تعديل Windows وتحديث برنامج الحماية من الفيروسات من Microsoft Defender على أجهزتهم Windows 10، سيتم وضع العديد من الخيارات باللون الرمادي.
  
1. انتقل **إلى الإعدادات** \> **تحديث الأمان Windows &amp;** \> **تحديث** \> خيارات إعادة التشغيل وتأكد من أن كل الإعدادات باللون الرمادي. 
    
    ![كل خيارات إعادة التشغيل باللون الرمادي.](../../media/31308da9-18b0-47c5-bbf6-d5fa6747c376.png)
  
2. انتقل **إلى الإعدادات** \> **تحديث Windows &amp;** \>  \> خيارات التحديث المتقدمة وتأكد من أن كل الإعدادات باللون الرمادي. 
    
    ![Windows خيارات التحديثات المتقدمة باللون الرمادي.](../../media/049cf281-d503-4be9-898b-c0a3286c7fc2.png)
  
3. انتقل إلى **الإعدادات** \> **تحديث الأمان Windows &amp;** \>  \> **خيارات التحديث المتقدمة** \> **اختر كيفية تسليم التحديثات**.
    
    تأكد من أنه يمكنك رؤية الرسالة (باللون الأحمر) بأن بعض الإعدادات مخفية أو مدارة بواسطة مؤسستك، وأن كل الخيارات تظهر باللون الرمادي.
    
    ![اختر كيفية تسليم التحديثات صفحة تشير إلى أن الإعدادات مخفية أو مدارة بواسطة مؤسستك.](../../media/6b3e37c5-da41-4afd-9983-b4f406216b59.png)
  
4. لفتح مركز Windows Defender،  \> **&amp;** \> انتقل إلى الإعدادات تحديث الأمان Windows **Defender** \> انقر فوق فتح Windows حماية مؤشر ترابط الفيروسات في **مركز** \> **&amp;** \> **&amp; حماية حماية الفيروسات من الفيروسات**. 
    
5. تحقق من أن كل الخيارات باللون الرمادي. 
    
    ![يتم وضع إعدادات الحماية من الفيروسات والتهديدات باللون الرمادي.](../../media/9ca68d40-a5d9-49d7-92a4-c581688b5926.png)
  
## <a name="related-content"></a>المحتوى ذي الصلة

[Microsoft 365 ووثائق الأعمال ومواردها](/admin)\
[تعيين تكوينات الأجهزة Windows 10 PCsTop](protection-settings-for-windows-10-pcs.md)
 [10 لتأمين Microsoft 365 لخطط الأعمال](../security-and-compliance/secure-your-business-data.md)