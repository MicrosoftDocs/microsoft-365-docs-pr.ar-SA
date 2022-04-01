---
title: مقارنة إعدادات نهج توافق الجهاز
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: بالنسبة إلى موفري الخدمات المدارة (MSPs) Microsoft 365 المنارة، تعرف على كيفية مقارنة إعدادات نهج توافق الأجهزة.
ms.openlocfilehash: 30645ef4d59fcdee0d994ae709ff9bb45fc21b09
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 03/08/2022
ms.locfileid: "63579219"
---
# <a name="compare-device-compliance-policy-settings"></a>مقارنة إعدادات نهج توافق الجهاز

Microsoft 365 "المنارة" عرض سياسات التوافق عبر المستأجرين في طريقة عرض واحدة. يمكنك تعزيز الأمان والتقيس عبر المستأجرين من خلال مقارنة السياسات. يمكنك تصفية طرق العرض لرؤية الإعدادات التي تم تكوينها (مقابل الإعدادات التي لم يتم تكوينها) أو الإعدادات التي تختلف في تكويناتها أو الإعدادات التي تتطابق. يمكنك أيضا البحث عن إعدادات معينة لمعرفة كيفية مقارنتها عبر السياسات.

## <a name="before-you-begin"></a>قبل البدء

تأكد من أن الأجهزة تملك Microsoft Intune تسجيل في إدارة نقاط النهاية من Microsoft (MEM).

## <a name="compare-policy-settings"></a>مقارنة إعدادات النهج

1. في جزء التنقل الأيسر في المنارة، حدد **الأجهزة**.

2. حدد علامة **التبويب "سياسات** ".

3. من القائمة **المنسدل** عوامل التصفية، حدد نظام تشغيل أو نظام أساسي.

   > [!NOTE]
   > يمكنك فقط مقارنة السياسات مع نظام التشغيل أو النظام الأساسي نفسه.

4. من القائمة التي تمت تصفيتها، حدد ما يصل إلى ثلاثة سياسات تريد مقارنتها.

5. حدد **مقارنة**.

يمكنك تصفية النتائج لرؤية الإعدادات **التي تختلف** أو الإعدادات **التي تتطابق** أو **إعدادات مكونة**.

## <a name="configure-a-policy-setting"></a>تكوين إعداد نهج

1. في جزء التنقل الأيسر في المنارة، حدد **الأجهزة**.

2. حدد علامة **التبويب "سياسات** ".

3. من القائمة، حدد اسم نهج.

4. من جزء تفاصيل النهج، حدد **عرض هذا النهج في** إدارة نقاط النهاية من Microsoft.

5. في MEM، قم بتحرير إعدادات النهج حسب الحاجة.

## <a name="next-steps"></a>الخطوات التالية

عند إجراء تعديلات على النهج، تأكد من تقييم تغييراتك مقابل إعدادات الأساس الحالية. لمزيد من المعلومات، راجع [نظرة عامة حول استخدام الأساسات لنشر تكوينات المستأجر القياسية](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>المحتوى ذي الصلة

[ما هو تسجيل الجهاز في Intune؟](/mem/intune/enrollment/device-enrollment) (article)  
[استخدام سياسات التوافق لتعيين قواعد للأجهزة التي تديرها باستخدام Intune](/mem/intune/protect/device-compliance-get-started) (مقالة)  
[نظرة عامة حول استخدام الأساسات لنشر تكوينات المستأجر القياسية](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (مقالة)
