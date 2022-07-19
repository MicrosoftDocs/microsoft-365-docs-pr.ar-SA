---
title: نظرة عامة على الرسائل المعزولة في Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw
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
description: بالنسبة لموفري الخدمات المدارة (MSPs) الذين يستخدمون Microsoft 365 Lighthouse، تعرف على كيفية إدارة الرسائل المعزولة.
ms.openlocfilehash: 3a295802ba806c48f01f6f64c8b148169fe28102
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 07/01/2022
ms.locfileid: "66857489"
---
# <a name="overview-of-quarantined-messages-in-microsoft-365-lighthouse"></a>نظرة عامة على الرسائل المعزولة في Microsoft 365 Lighthouse

يتيح لك Microsoft 365 Lighthouse الاطلاع على رؤى ومعلومات حول رسائل البريد الإلكتروني المعزولة عبر جميع مستأجري العملاء. من طريقة عرض واحدة، يمكنك فرز رسائل البريد الإلكتروني المعزولة واتخاذ الإجراءات المناسبة. تتوفر البيانات إذا قام المستأجر بتنفيذ Exchange Online Protection (EOP) وMicrosoft Defender للخطة 1 من Office365 (MDO).

يمكنك الوصول إلى المعلومات عن طريق تحديد **"حماية البيانات"** من جزء التنقل الأيمن أو الصفحة **الرئيسية** .

## <a name="quarantined-messages-page"></a>صفحة الرسائل المعزولة

من هذه الصفحة، يمكنك عرض الإحصائيات الموحدة عبر مستأجري العملاء، والبيانات المتداولة لنوع وحجم بيانات العزل، والمعلومات المتعلقة بقوائم انتظار العزل في مستأجري العملاء الفرديين.

يوفر قسم **حالة الرسائل** طريقة عرض موحدة عبر المستأجرين المؤهلين الملحقين حاليا إلى Lighthouse. تتضمن طريقة العرض

- إجمالي الرسائل في العزل
- إجمالي الرسائل التي تنتظر المراجعة
- الرسائل التي تقترب حاليا من حد العزل الافتراضي وهو 30 يوما والتي على وشك إزالتها تلقائيا (تنتهي صلاحيتها)
- الرسائل التي تم إصدارها من العزل
- العدد الإجمالي لعلب البريد المتأثرة عبر جميع المستأجرين

تعكس البيانات آخر 30 يوما؛ ومع ذلك، يمكنك استخدام عامل تصفية **النطاق الزمني** لتعديل طريقة العرض.

يحتوي مخطط **سبب** **العزل** على تصنيف تفصيلي لعدد العزل حسب نوع نهج Exchange Online Protection (EOP) وMicrosoft Defender لنهج الخطة 1 من Office365 (MDO). تتضمن هذه الأنواع

- البرامج الضاره
- التصيّد الاحتيالي
- التصيد الاحتيالي عالي الثقة
- البريد المزعج
- البريد الإلكتروني المجمع

قائمة العزل هي طريقة عرض قابلة للفرز لمعلومات العزل حسب المستأجر. ضمن طريقة العرض هذه، يمكنك التصفية حسب المعلومات التالية:

- **سبب العزل:** أي، برامج ضارة، تصيد احتيالي، تصيد احتيالي عالي الثقة، بريد عشوائي، بريد إلكتروني مجمع
- **نوع النهج:** أي، مكافحة البرامج الضارة، مكافحة التصيد الاحتيالي، مكافحة البريد العشوائي، المرفقات الآمنة، قاعدة النقل، غير معروف
- **على وشك الانتهاء:** أي، اليوم، في غضون يومين، في غضون سبعة أيام

يمكنك أيضا ضبط الأعمدة وفرز البيانات استنادا إلى المستأجر وحالة الرسالة وتواريخ انتهاء الصلاحية.

:::image type="content" source="../media/m365-lighthouse-data-protection/quarantine-email-page.png" alt-text="صفحة رسائل العزل في Microsoft 365 Lighthouse" lightbox="../media/m365-lighthouse-data-protection/quarantine-email-page.png":::

يوفر خيار **نسخ الارتباط إلى الرسائل في Microsoft** **365 Defender** ارتباطا إلى مدخل Microsoft 365 Defender حيث يمكنك الوصول إلى قائمة انتظار عزل البريد الإلكتروني للمستأجر وإدارتها. يجب عليك المصادقة قبل أن تتمكن من اتخاذ أي إجراء.

## <a name="related-content"></a>المحتويات ذات الصلة

[رسائل البريد الإلكتروني المعزولة](../security/office-365-security/quarantine-email-messages.md) (مقالة)\
[توصيات Microsoft لإعدادات أمان EOP و Defender لـ Office 365](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (مقالة)\
[نظرة عامة على Exchange Online Protection (EOP)](../security/office-365-security/exchange-online-protection-overview.md) (مقالة)
