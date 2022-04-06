---
title: حظر حلقة الملاحظات
description: الحظر الحلقي للملاحظات، ويسمى أيضا الحماية السريعة، هو جزء من قدرات الحظر والاحتواء السلوكية في Microsoft Defender لنقطة النهاية
keywords: حظر السلوك والحماية السريعة وحظر الملاحظات و Microsoft Defender لنقطة النهاية
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 82d5fb32a9535a5b341bca8e5bee989d88ad8232
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 11/24/2021
ms.locfileid: "63583198"
---
# <a name="feedback-loop-blocking"></a>حظر حلقة الملاحظات

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**ينطبق على:**
- [خطة Microsoft Defender لنقطة النهاية 2](https://go.microsoft.com/fwlink/?linkid=2154037)

## <a name="overview"></a>نظرة عامة

إن حظر تكرار الملاحظات، ويشار إليه أيضا بالحماية السريعة، هو أحد مكونات قدرات الحظر [](/microsoft-365/security/defender-endpoint/behavioral-blocking-containment) والاحتواء السلوكية في [Microsoft Defender لنقطة النهاية](/windows/security/threat-protection/). مع حظر تكرار الملاحظات، تكون الأجهزة عبر مؤسستك محمية بشكل أفضل من الهجمات. 

## <a name="how-feedback-loop-blocking-works"></a>كيفية عمل حظر تكرار الملاحظات

عند اكتشاف سلوك مريب أو ملف، على برنامج الحماية من الفيروسات من Microsoft Defender، يتم إرسال [](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)معلومات حول هذه الأداة إلى تصنيفات متعددة. يفحص مشغل حلقة الحماية السريعة المعلومات ويربطها مع إشارات أخرى للوصول إلى قرار بشأن ما إذا كنت تريد حظر ملف أم لا. يتم التحقق من التحف وتصنيفها بسرعة. يؤدي ذلك إلى الحظر السريع للبرامج الضارة التي تم تأكيدها، كما يؤدي إلى تعزيز الحماية عبر النظام البيئي بأكمله. 

عند وضع الحماية السريعة في مكانها، يمكن إيقاف الهجوم على جهاز وأجهزة أخرى في المؤسسة وأجهزة أخرى في مؤسسات أخرى، حيث يحاول الهجوم توسيع موطئ قدمه.


## <a name="configuring-feedback-loop-blocking"></a>تكوين حظر تكرار تكرار الملاحظات

إذا كانت مؤسستك تستخدم Defender for Endpoint، يتم تمكين حظر حلقة الملاحظات بشكل افتراضي. ومع ذلك، تحدث الحماية السريعة من خلال مجموعة من قدرات Defender لنقطة النهاية وميزات حماية التعلم الآلي ومشاركة الإشارات عبر خدمات الأمان من Microsoft. تأكد من تمكين الميزات التالية وإمكانيات Defender لنقطة النهاية وتكوينها:

- [أساسيات Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)

- [الأجهزة المجهزة في Microsoft Defender لنقطة النهاية](/microsoft-365/security/defender-endpoint/onboard-configure)

- [الكشف التلقائي والاستجابة على النقط النهائية في وضع الحظر](/microsoft-365/security/defender-endpoint/edr-in-block-mode)

- [الحد من سطح الهجوم](/microsoft-365/security/defender-endpoint/attack-surface-reduction)

- [حماية الجيل التالي](/windows/security/threat-protection/microsoft-defender-antivirus/configure-microsoft-defender-antivirus-features) (antivirus)

## <a name="related-articles"></a>المقالات ذات الصلة

- [الحظر السلوكي والاحتواء](behavioral-blocking-containment.md)

- [(Blog) الحظر السلوكي والاحتواء: تحويل البصريات إلى حماية](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection/)

- [موارد Microsoft Defender مفيدة لنقطة النهاية](/microsoft-365/security/defender-endpoint/helpful-resources)
