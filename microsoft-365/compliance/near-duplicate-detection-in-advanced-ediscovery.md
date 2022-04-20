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
ms.openlocfilehash: f7976f5fdf023c30f7f96264ecc2b744656e9091
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: ar-SA
ms.lasthandoff: 04/19/2022
ms.locfileid: "64949400"
---
# <a name="near-duplicate-detection-in-ediscovery-premium"></a>الكشف شبه المكرر في eDiscovery (Premium)

خذ بعين الاعتبار مجموعة من المستندات التي يجب مراجعتها حيث تستند مجموعة فرعية إلى نفس القالب ولها في الغالب نفس اللغة المتداولة، مع بعض الاختلافات هنا وهناك. إذا تمكن المراجع من تحديد هذه المجموعة الفرعية، ومراجعة إحداها بدقة، ومراجعة الاختلافات للبقية، فلن يفوتهم أي معلومات فريدة مع أخذ جزء صغير فقط من الوقت الذي كان سيستغرقه لقراءة جميع المستندات التي تغطيها. بالقرب من مجموعات الكشف المكررة، يتم تجميع مستندات متشابهة نصيا معا لمساعدتك على جعل عملية المراجعة أكثر كفاءة.

## <a name="how-does-it-work"></a>كيف يعمل؟

عند تشغيل الكشف عن التكرار القريب، يقوم النظام لتحليل كل مستند باستخدام النص. ثم يقارن كل مستند مع الآخر لتحديد ما إذا كان تشابهها أكبر من الحد المعين. إذا كان الأمر كذلك، يتم تجميع المستندات معا. بمجرد مقارنة جميع المستندات وتجميعها، يتم وضع علامة "محوري" على مستند من كل مجموعة؛ عند مراجعة المستندات، يمكنك مراجعة محور أولا ومراجعة المستندات الأخرى في نفس المجموعة شبه المكررة، مع التركيز على الفرق بين المحور والمستند قيد المراجعة.
