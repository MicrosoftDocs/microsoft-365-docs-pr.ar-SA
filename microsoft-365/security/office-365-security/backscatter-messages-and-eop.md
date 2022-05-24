---
title: البريد الاحتياطي في EOP
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: في هذه المقالة، ستتعرف على Backscatter والحماية Microsoft Exchange Online (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d132ed56c02989987da9e0ce32e7d4593e85e651
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648206"
---
# <a name="backscatter-in-eop"></a>البريد الاحتياطي في EOP

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [خطة 1 وخطة 2 من Microsoft Defender لـ Office 365](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*إن Backscatter* عبارة عن تقارير بعدم التسليم (تعرف أيضا بتقارير بعدم التسليم أو رسائل البريد المرتد) التي تتلقاها للرسائل التي لم ترسلها. يحدث الانتحال الخلفي بسبب مرسلي البريد العشوائي الذين يستنسخون (ينتحلون) عنوان "من" (المعروف أيضا باسم `5322.From` العنوان أو P2) في رسائلهم. غالبا ما يستخدم مرسلي البريد العشوائي عناوين البريد الإلكتروني الحقيقية كعنوان "من" لإضفاء مصداقية على رسائلهم. عند إرسال البريد العشوائي إلى مستلم غير موجود، يتم خداع خادم البريد الإلكتروني الوجهة بشكل أساسي لإرجاع الرسالة غير القابلة للتسليم في التقرير بعدم التسليم إلى المرسل المخادع في عنوان "من".

في المؤسسات Microsoft 365 التي تحتوي على علب بريد في Exchange Online أو مؤسسات Exchange Online Protection مستقلة (EOP) بدون علب بريد Exchange Online، تبذل EOP كل جهد لتحديد الرسائل وإفلاتها بصمت من مصادر مريبة دون إنشاء التقرير بعدم التسليم( NDR). ولكن، استنادا إلى البريد الإلكتروني المجمع المتدفق عبر الخدمة، هناك دائما احتمال أن يرسل EOP رسالة بريد إلكتروني عن غير قصد.

يحتفظ Backscatterer.org بقائمة حظر (تعرف أيضا بقائمة حظر DNS أو DNSBL) لخوادم البريد الإلكتروني المسؤولة عن إرسال البريد الاحتياطي، وقد تظهر خوادم EOP في هذه القائمة. ولكننا لا نحاول إزالة أنفسنا من قائمة الحظر Backscatterer.org لأن قائمتهم (من خلال دخولهم الخاص) ليست قائمة بمرسلي البريد العشوائي.

> [!TIP]
> يوصي موقع ويب Backscatterer.org (<http://www.backscatterer.org/?target=usage>) باستخدام خدمته في وضع خزينة بدلا من وضع الرفض، لأن خدمات البريد الإلكتروني الكبيرة ترسل دائما بعض رسائل البريد الاحتياطي.
