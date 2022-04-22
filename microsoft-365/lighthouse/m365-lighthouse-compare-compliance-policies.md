---
title: مقارنة إعدادات نهج توافق الجهاز في Microsoft 365 Lighthouse
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
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية مقارنة إعدادات نهج توافق الجهاز.
ms.openlocfilehash: 1ea7a278a58cd6d864c32ab7b25569ae463658f9
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022746"
---
# <a name="compare-device-compliance-policy-settings-in-microsoft-365-lighthouse"></a>مقارنة إعدادات نهج توافق الجهاز في Microsoft 365 Lighthouse

يتيح لك Microsoft 365 Lighthouse عرض نهج التوافق عبر المستأجرين في طريقة عرض واحدة. يمكنك دفع الأمان والتوحيد القياسي عبر المستأجرين من خلال مقارنة النهج. يمكنك تصفية طرق العرض للاطلاع على الإعدادات التي تم تكوينها (مقابل الإعدادات التي لم يتم تكوينها) أو الإعدادات التي تختلف في تكويناتها أو الإعدادات التي تتطابق. يمكنك أيضا البحث عن إعدادات معينة لمعرفة كيفية مقارنتها عبر النهج.

## <a name="before-you-begin"></a>قبل البدء

تأكد من أن الأجهزة لديها ترخيص Microsoft Intune ومن أنها مسجلة في إدارة نقاط النهاية من Microsoft (MEM).

## <a name="compare-policy-settings"></a>مقارنة إعدادات النهج

1. في جزء التنقل الأيمن في Lighthouse، حدد **الأجهزة**.

2. حدد علامة التبويب **"النهج** ".

3. من القائمة المنسدلة **عوامل التصفية** ، حدد نظام تشغيل أو نظام أساسي.

   > [!NOTE]
   > يمكنك فقط مقارنة النهج مع نفس نظام التشغيل أو النظام الأساسي.

4. من القائمة التي تمت تصفيتها، حدد ما يصل إلى ثلاثة نهج تريد مقارنتها.

5. حدد **"مقارنة**".

يمكنك تصفية النتائج للاطلاع **على الإعدادات التي تختلف** أو **الإعدادات التي تتطابق** مع **الإعدادات أو التي تم تكوينها**.

## <a name="configure-a-policy-setting"></a>تكوين إعداد نهج

1. في جزء التنقل الأيمن في Lighthouse، حدد **الأجهزة**.

2. حدد علامة التبويب **"النهج** ".

3. من القائمة، حدد اسم نهج.

4. من جزء تفاصيل النهج، حدد **عرض هذا النهج في إدارة نقاط النهاية من Microsoft**.

5. في MEM، قم بتحرير إعدادات النهج حسب الحاجة.

## <a name="next-steps"></a>الخطوات التالية

أثناء إجراء تعديلات على النهج، تأكد من تقييم تغييراتك مقابل إعدادات الأساس الحالية. لمزيد من المعلومات، راجع [نظرة عامة حول استخدام الخطوط الأساسية لنشر تكوينات المستأجر القياسية](m365-lighthouse-deploy-standard-tenant-configurations-overview.md).

## <a name="related-content"></a>المحتويات ذات الصلة

[ما هو تسجيل الجهاز في Intune؟](/mem/intune/enrollment/device-enrollment) (مقالة)  
[استخدام نهج التوافق لتعيين قواعد للأجهزة التي تديرها باستخدام Intune](/mem/intune/protect/device-compliance-get-started) (مقالة)  
[نظرة عامة حول استخدام Microsoft 365 أساسيات Lighthouse لنشر تكوينات المستأجر القياسية](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (المقالة)
