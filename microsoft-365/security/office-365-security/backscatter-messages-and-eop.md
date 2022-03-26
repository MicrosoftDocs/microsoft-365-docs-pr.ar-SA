---
title: Backscatter في EOP
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
description: في هذه المقالة، ستتعرف على Backscatter Microsoft Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79a6dd1be6c33bdbfc3d87b834f231de7cd08a0c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 10/06/2021
ms.locfileid: "63568571"
---
# <a name="backscatter-in-eop"></a>Backscatter في EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**ينطبق على**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender Office 365 الخطة 1 الخطة 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*إن الرسالة المرتد* هي تقارير بعدم التسليم (تعرف أيضا بالتقارير بعدم التسليم أو رسائل البريد المرتد) التي تتلقاها للرسائل التي لم ترسلها. يحدث الخطأ Backscatter بسبب مرسلي البريد العشوائي الذين يغرون (ينتحلون) عنوان من ( `5322.From` المعروف أيضا باسم عنوان أو P2) في رسائلهم. غالبا ما يستخدم مرسلو البريد العشوائي عناوين البريد الإلكتروني الحقيقية كعنوان "من" لإعارة المصداقية لرسائلهم. عندما يتم إرسال البريد العشوائي إلى مستلم غير موجود، يتم خداع خادم البريد الإلكتروني الوجهة بشكل أساسي لإرجاع الرسالة غير القابلة للرسالة في عدم التسليم إلى المرسل المزيف في العنوان من.

في Microsoft 365 المؤسسات التي بها علب بريد في Exchange Online أو مؤسسات Exchange Online Protection (EOP) مستقلة بدون علب بريد Exchange Online، تبذل EOP كل جهدها لتحديد الرسائل وإسقاطها بصمت من مصادر مشكوك فيها من دون إنشاء NDR. ولكن استنادا إلى كمية البريد الإلكتروني التي تتدفق عبر الخدمة، هناك دائما إمكانية قيام EOP بإرسال رسالة بريد إلكتروني غير مقصودة.

Backscatterer.org على قائمة حظر (تعرف أيضا باسم قائمة حظر DNS أو DNSBL) من خوادم البريد الإلكتروني التي كانت مسؤولة عن إرسال البريد المرجع، وقد تظهر خوادم EOP في هذه القائمة. ولكننا لا نحاول إزالة أنفسنا من قائمة حظر البريد Backscatterer.org لأن قائمتهم (من خلال إقرارهم الخاص) ليست قائمة بمرسلي البريد العشوائي.

> [!TIP]
> يوصي Backscatterer.org ويب (<http://www.backscatterer.org/?target=usage>) باستخدام خدمته في وضع خزينة بدلا من وضع الرفض، لأن خدمات البريد الإلكتروني الكبيرة ترسل دائما بعض رسائل البريد المرجع.
