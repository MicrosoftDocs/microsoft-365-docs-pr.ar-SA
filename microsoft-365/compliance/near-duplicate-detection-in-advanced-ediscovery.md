---
title: الكشف شبه المكرر في eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: استخدم الكشف شبه المكرر لتجميع المستندات المتشابهة نصيا عند تحليل بيانات الحالة في eDiscovery (Premium).
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e22444845005f4cf155340e13856722976715d91
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/20/2022
ms.locfileid: "64997593"
---
# <a name="near-duplicate-detection-in-ediscovery-premium"></a>الكشف شبه المكرر في eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

خذ بعين الاعتبار مجموعة من المستندات التي يجب مراجعتها حيث تستند مجموعة فرعية إلى نفس القالب ولها في الغالب نفس اللغة المتداولة، مع بعض الاختلافات هنا وهناك. إذا تمكن المراجع من تحديد هذه المجموعة الفرعية، ومراجعة إحداها بدقة، ومراجعة الاختلافات للبقية، فلن يفوتهم أي معلومات فريدة مع أخذ جزء صغير فقط من الوقت الذي كان سيستغرقه لقراءة جميع المستندات التي تغطيها. بالقرب من مجموعات الكشف المكررة، يتم تجميع مستندات متشابهة نصيا معا لمساعدتك على جعل عملية المراجعة أكثر كفاءة.

## <a name="how-does-it-work"></a>كيف يعمل؟

عند تشغيل الكشف عن التكرار القريب، يقوم النظام لتحليل كل مستند باستخدام النص. ثم يقارن كل مستند مع الآخر لتحديد ما إذا كان تشابهها أكبر من الحد المعين. إذا كان الأمر كذلك، يتم تجميع المستندات معا. بمجرد مقارنة جميع المستندات وتجميعها، يتم وضع علامة "محوري" على مستند من كل مجموعة؛ عند مراجعة المستندات، يمكنك مراجعة محور أولا ومراجعة المستندات الأخرى في نفس المجموعة شبه المكررة، مع التركيز على الفرق بين المحور والمستند قيد المراجعة.
