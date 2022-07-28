---
title: مقارنة إعدادات نهج توافق الجهاز في Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية مقارنة إعدادات نهج توافق الجهاز.
ms.openlocfilehash: 9640fcb1438de70c6283c177e64c12fb6da57349
ms.sourcegitcommit: 23a53b5c5e372a2a7ad5e175850224d3d464f6dd
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/28/2022
ms.locfileid: "67056581"
---
# <a name="compare-device-compliance-policy-settings-in-microsoft-365-lighthouse"></a>مقارنة إعدادات نهج توافق الجهاز في Microsoft 365 Lighthouse

يتيح لك Microsoft 365 Lighthouse عرض نهج التوافق عبر المستأجرين في طريقة عرض واحدة. يمكنك دفع الأمان والتوحيد القياسي عبر المستأجرين من خلال مقارنة النهج. يمكنك تصفية طرق العرض للاطلاع على الإعدادات التي تم تكوينها (مقابل الإعدادات التي لم يتم تكوينها) أو الإعدادات التي تختلف في تكويناتها أو الإعدادات التي تتطابق. يمكنك أيضا البحث عن إعدادات معينة لمعرفة كيفية مقارنتها عبر النهج.

## <a name="before-you-begin"></a>قبل البدء

تأكد من أن الأجهزة لديها ترخيص Microsoft Intune ومن أنها مسجلة في Microsoft Endpoint Manager (MEM).

## <a name="compare-policy-settings"></a>مقارنة إعدادات النهج

1. في جزء التنقل الأيمن في Lighthouse، حدد **توافق الأجهزة** > .

2. حدد علامة التبويب **"النهج** ".

3. من القائمة المنسدلة **عوامل التصفية** ، حدد نظام تشغيل أو نظام أساسي.

   > [!NOTE]
   > يمكنك فقط مقارنة النهج مع نفس نظام التشغيل أو النظام الأساسي.

4. من القائمة التي تمت تصفيتها، حدد ما يصل إلى ثلاثة نهج تريد مقارنتها.

5. حدد **"مقارنة**".

يمكنك تصفية النتائج للاطلاع على **الإعدادات التي تختلف** أو **الإعدادات المتطابقة** أو **الإعدادات المكونة**.

## <a name="configure-a-policy-setting"></a>تكوين إعداد نهج

1. في جزء التنقل الأيمن في Lighthouse، حدد **توافق الأجهزة** > .

2. حدد علامة التبويب **"النهج** ".

3. من قائمة النهج، حدد النهج الذي تريد عرضه.

4. في جزء تفاصيل النهج، حدد **عرض هذا النهج في Microsoft Endpoint Manager**.

5. في MEM، قم بتحرير إعدادات النهج حسب الحاجة.

## <a name="next-steps"></a>الخطوات التالية

أثناء إجراء تعديلات على النهج، تأكد من تقييم تغييراتك مقابل إعدادات الأساس الحالية. لمزيد من المعلومات، راجع [نظرة عامة حول استخدام الخطوط الأساسية لنشر تكوينات المستأجر القياسية](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[ما هو تسجيل الجهاز في Intune؟](/mem/intune/enrollment/device-enrollment) (مقالة)  
[استخدام نهج التوافق لتعيين قواعد للأجهزة التي تديرها باستخدام Intune](/mem/intune/protect/device-compliance-get-started) (مقالة)  
[نظرة عامة حول استخدام أساسيات Microsoft 365 Lighthouse لنشر تكوينات المستأجر القياسية](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (المقالة)
